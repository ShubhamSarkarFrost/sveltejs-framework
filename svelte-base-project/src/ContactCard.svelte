<script>
  export let userName;
  export let jobTitle;
  export let description;
  export let userImage;
</script>

<div class="contact-card">
  <header>
    <div class="thumb" class:thumb-placeholder={!userImage}>
      <img src={userImage} alt={userName} />
    </div>
    <div class="user-data">
      <h1>{userName}</h1>
      <h2>{jobTitle}</h2>
    </div>
  </header>
  <div class="description">
    <p>{description}</p>
  </div>
</div>

<style>
  .contact-card {
    background-color: #ebd6fb;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    max-width: 30rem;
    border-radius: 8px;
    padding: 1.5rem;
    margin: 1rem;
  }

  header {
    display: flex;
    align-items: center;
    gap: 1rem;
    margin-bottom: 1rem;
  }

  .thumb {
    width: 5rem;
    height: 5rem;
    flex-shrink: 0;
  }

  .thumb-placeholder {
    background: #ccc;
  }

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 50%; /* circular image */
  }

  .user-data {
    flex: 1;
    display: flex;
    flex-direction: column;
  }

  h1 {
    font-size: 1.25rem;
    font-family: 'Roboto Slab', sans-serif;
    margin: 0 0 0.25rem 0;
    color: #52357b;
  }

  h2 {
    font-size: 1rem;
    font-weight: normal;
    color: #52357b;
    margin: 0;
  }

  .description {
    border-top: 1px solid rgba(82, 53, 123, 0.2);
    padding-top: 1rem;
  }

  p {
    color: #52357b;
    margin: 0;
    line-height: 1.5;
  }
</style>
