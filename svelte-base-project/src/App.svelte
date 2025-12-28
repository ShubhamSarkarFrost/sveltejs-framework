<script>
  import ContactCard from './ContactCard.svelte';

  let name = 'Max';
  let title = 'Senior Developer';
  let description = 'Passionate about building fast and accessible web applications.';
  let age = 30;
  let imageSrc = ''; // data URL or object URL of the uploaded image

  $: uppercaseName = name.toUpperCase();
  $: console.log(name);
  $: if (name === 'Maximilian') {
    console.log('It runs!');
    age = 31;
  }

  function incrementAge() {
    age += 1;
  }

  function handleImageChange(event) {
    const [file] = event.target.files;
    if (!file) return;

    const reader = new FileReader();
    reader.onload = e => {
      imageSrc = e.target.result;
    };
    reader.readAsDataURL(file);
  }
</script>

<div class="page">
  <h1>Hello {uppercaseName}, my age is {age}!</h1>

  <div class="controls">
    <button on:click={incrementAge}>Change Age</button>
  </div>

  <div class="form">
    <label>
      Name
      <input type="text" bind:value={name} />
    </label>

    <label>
      Title
      <input type="text" bind:value={title} />
    </label>

    <label>
      Short description
      <textarea rows="3" bind:value={description}></textarea>
    </label>

    <label class="file-label">
      Photo
      <input
        type="file"
        accept="image/*"
        on:change={handleImageChange}
      />
    </label>

    {#if imageSrc}
      <div class="preview">
        <img src={imageSrc} alt={`Photo of ${name}`} />
      </div>
    {/if}
  </div>

  <ContactCard
    userName={uppercaseName}
    title={title}
    description={description}
    imageSrc={imageSrc}
  />
</div>

<style>
  .page {
    max-width: 640px;
    margin: 2rem auto;
    padding: 1.5rem;
    background: #faf5ff;
    border-radius: 12px;
    box-shadow: 0 8px 18px rgba(0, 0, 0, 0.06);
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  }

  h1 {
    color: purple;
    margin-bottom: 1rem;
    font-size: 1.8rem;
  }

  .controls {
    margin-bottom: 1.5rem;
  }

  button {
    padding: 0.5rem 1rem;
    border-radius: 999px;
    border: none;
    background: #7c3aed;
    color: white;
    cursor: pointer;
    font-weight: 600;
    transition: background 0.2s ease, transform 0.1s ease;
  }

  button:hover {
    background: #5b21b6;
    transform: translateY(-1px);
  }

  .form {
    display: grid;
    gap: 0.75rem;
    margin-bottom: 1.5rem;
  }

  label {
    display: flex;
    flex-direction: column;
    font-size: 0.9rem;
    color: #4b5563;
    gap: 0.25rem;
  }

  .file-label input[type="file"] {
    padding: 0.25rem 0;
  }

  input,
  textarea {
    padding: 0.5rem 0.75rem;
    border-radius: 8px;
    border: 1px solid #d1d5db;
    font-size: 0.95rem;
    outline: none;
    transition: border-color 0.15s ease, box-shadow 0.15s ease;
  }

  input:focus,
  textarea:focus {
    border-color: #7c3aed;
    box-shadow: 0 0 0 3px rgba(124, 58, 237, 0.18);
  }

  .preview {
    margin-top: 0.5rem;
  }

  .preview img {
    width: 96px;
    height: 96px;
    object-fit: cover;
    border-radius: 999px;
    border: 2px solid #7c3aed;
  }
</style>
