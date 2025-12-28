<script>
  export let userName;
  export let title;
  export let description;
  export let imageSrc = ''; // optional, default empty
</script>

<article class="card">
  <div class="avatar">
    {#if imageSrc}
      <img src={imageSrc} alt={`Avatar of ${userName}`} />
    {:else}
      <div class="placeholder">{userName?.[0] ?? '?'}</div>
    {/if}
  </div>
  <div class="info">
    <h2>{userName}</h2>
    <p class="title">{title}</p>
    <p class="description">{description}</p>
  </div>
</article>

<style>
  .card {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 1rem 1.25rem;
    background: white;
    border-radius: 12px;
    box-shadow: 0 6px 14px rgba(0, 0, 0, 0.04);
  }

  .avatar {
    width: 72px;
    height: 72px;
    border-radius: 999px;
    overflow: hidden;
    background: #ede9fe;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .avatar img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .placeholder {
    font-size: 1.8rem;
    font-weight: 700;
    color: #5b21b6;
  }

  .info h2 {
    margin: 0;
    font-size: 1.2rem;
    color: #111827;
  }

  .title {
    margin: 0.1rem 0;
    font-size: 0.9rem;
    color: #6b7280;
    font-weight: 500;
  }

  .description {
    margin: 0;
    font-size: 0.9rem;
    color: #4b5563;
  }
</style>
