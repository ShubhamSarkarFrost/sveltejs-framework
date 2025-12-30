<script>
  import ContactCard from './ContactCard.svelte';
  let name = 'Max';
  let title = '';
  let image = ''; // will hold data URL from upload
  let description = '';
  let formState = 'empty';
  let createdContacts = [];

  let files; // for bind:files

  function handleImageChange() {
    if (!files || !files[0]) {
      image = '';
      return;
    }
    const file = files[0];
    const reader = new FileReader();
    reader.onload = (e) => {
      image = e.target.result; // data URL
    };
    reader.readAsDataURL(file);
  }

  function addContact() {
    if (
      name.trim().length == 0 ||
      title.trim().length == 0 ||
      image.trim().length == 0 ||
      description.trim().length == 0
    ) {
      formState = 'invalid';
      return;
    }

    // Add to contacts array immediately
    createdContacts = [
      ...createdContacts,
      {
        id: Math.random(),
        name: name,
        title: title,
        image: image,
        description: description,
      },
    ];

    // Reset form for next entry
    name = '';
    title = '';
    image = '';
    description = '';
    files = null;
    formState = 'empty';
  }
</script>

<div class="page">
  <div id="form-wrapper">
    <div id="form">
      <div class="form-control">
        <label for="userName">User Name</label>
        <input type="text" bind:value={name} id="userName" />
      </div>

      <div class="form-control">
        <label for="jobTitle">Job Title</label>
        <input type="text" bind:value={title} id="jobTitle" />
      </div>

      <!-- file upload instead of URL -->
      <div class="form-control">
        <label for="imageUpload">Image Upload</label>
        <input
          id="imageUpload"
          type="file"
          accept="image/*"
          bind:files
          on:change={handleImageChange}
        />
      </div>

      <div class="form-control">
        <label for="desc">Description</label>
        <textarea rows="3" bind:value={description} id="desc"></textarea>
      </div>

      <button class="primary" on:click={addContact}>Add Contact Card</button>
    </div>
  </div>

  {#if formState === 'invalid'}
    <p class="error">Please fill out all fields.</p>
  {:else if createdContacts.length === 0}
    <p class="instruction">Please enter some data and click Add Contact Card</p>
  {/if}

  <div class="contacts-grid">
    {#each createdContacts as contact, i (contact.id)}
      <h2>#{i + 1}</h2>
      <ContactCard
        userName={contact.name}
        jobTitle={contact.title}
        userImage={contact.image}
        description={contact.description}
      />
    {/each}
  </div>
</div>

<style>
  .page {
    min-height: 100vh;
    padding: 2rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 2rem;
  }

  #form-wrapper {
    background-color: #e6ddff;
    padding: 2rem;
    border-radius: 0.75rem;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  #form {
    width: 30rem;
    max-width: 100%;
  }

  .form-control {
    margin-bottom: 0.75rem;
    display: flex;
    flex-direction: column;
  }

  label {
    margin-bottom: 0.25rem;
    font-weight: 600;
  }

  input,
  textarea {
    padding: 0.4rem 0.6rem;
    border-radius: 0.25rem;
    border: 1px solid #ccc;
  }

  .primary {
    margin-top: 0.5rem;
    padding: 0.5rem 1.25rem;
    background-color: #4b0082;
    color: white;
    border: none;
    border-radius: 0.4rem;
    cursor: pointer;
    transition: background-color 0.2s ease;
    width: 100%;
  }

  .primary:hover {
    background-color: #b19cd9;
  }

  .error,
  .instruction {
    margin-top: 0.5rem;
    text-align: center;
  }

  .error {
    color: #b00020;
  }

  .instruction {
    color: #666;
    font-style: italic;
  }

  .contacts-grid {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    width: 100%;
    max-width: 40rem;
  }
</style>
