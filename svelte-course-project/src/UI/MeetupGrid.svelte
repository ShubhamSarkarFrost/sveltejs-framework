<script>
  import MeetupItem from './MeetupItem.svelte';
  export let meetups;
</script>

<section id="meetups">
  {#each meetups as meetup}
    <MeetupItem
      title={meetup.title}
      subtitle={meetup.subtitle}
      description={meetup.description}
      imageUrl={meetup.imageUrl}
      email={meetup.contactEmail}
      address={meetup.address}
    />
  {/each}
</section>

<style>
  section {
    width: 100%;
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    padding: 2rem 1rem;
    background-color: #FFE4EF;
  }
</style>
