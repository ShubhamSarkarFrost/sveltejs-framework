<script>
  import Button from './UI/Button.svelte';
  import Header from './UI/Header.svelte';
  import MeetupGrid from './UI/MeetupGrid.svelte';
  import TextInput from './UI/TextInput.svelte';
  let title = '';
  let subtitle = '';
  let address = '';
  let email = '';
  let description = '';
  let imageUrl = '';
  let meetups = [
    {
      id: 'm1',
      title: 'Coding Bootcamp',
      subtitle: 'Learn to code in 2 hours',
      description: 'In this meetup, we will have some experts that teach you how to code!',
      imageUrl:
        'https://upload.wikimedia.org/wikipedia/commons/d/de/Afroyanga_Bootcamp_2.0_DAY2.jpg',
      address: '27th Nerd Road, 32523 New York',
      contactEmail: 'code@test.com',
    },
    {
      id: 'm2',
      title: 'Swim Together',
      subtitle: "Let's go for some swimming",
      description: 'We will simply swim some rounds!',
      imageUrl: 'https://upload.wikimedia.org/wikipedia/commons/6/6c/The_big_swimming_splash.jpg',
      address: '27th Nerd Road, 32523 New York',
      contactEmail: 'swim@test.com',
    },
  ];
  function addMeetup() {
    const newMeetup = {
      id: Math.random().toString(),
      title: title,
      subtitle: subtitle,
      description: description,
      imageUrl: imageUrl,
      contactEmail: email,
      address: address,
    }; // meetups.push(newMeetup); // DOES NOT WORK!
    meetups = [newMeetup, ...meetups];
  }
</script>

<Header />
<main>
  <form on:submit|preventDefault={addMeetup}>
    <TextInput
      id="title"
      label="Title"
      type="text"
      value={title}
      on:input={(event) => (title = event.target.value)}
    />
    <TextInput
      id="subtitle"
      label="Subtitle"
      type="text"
      value={subtitle}
      on:input={(event) => (subtitle = event.target.value)}
    />
    <TextInput
      id="address"
      label="Address"
      type="text"
      value={address}
      on:input={(event) => (address = event.target.value)}
    />
    <TextInput
      id="imageUrl"
      label="Image URL"
      type="text"
      value={imageUrl}
      on:input={(event) => (imageUrl = event.target.value)}
    />
    <TextInput
      id="email"
      label="E-Mail"
      type="email"
      value={email}
      on:input={(event) => (email = event.target.value)}
    />
    <TextInput
      id="description"
      label="Description"
      controlType="textarea"
      value={description}
      on:input={(event) => (description = event.target.value)}
    />
    <Button type="submit" caption="Save">Save</Button>
  </form>
  <MeetupGrid {meetups} />
</main>

<style>
  main {
    margin-top: 5rem;
  }
    form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>
