<script>
  export let title;
  export let subtitle;
  export let imageUrl;
  export let description;
  export let address;
  export let email;
</script>

<article>
  <header>
    <div class="avatar">
      <img src={imageUrl} alt={title} />
    </div>
    <div class="header-text">
      <h1>{title}</h1>
      <h2>{subtitle}</h2>
      <p>{address}</p>
    </div>
  </header>
  
  <div class="content">
    <p>{description}</p>
  </div>
  
  <footer>
    <a href="mailto:{email}">Contact</a>
    <button>Show Details</button>
    <button>Favorite</button>
  </footer>
</article>

<style>
  article {
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    border-radius: 8px;
    background: white;
    margin: 1rem;
    overflow: hidden;
  }

  header,
  .content,
  footer {
    padding: 1rem;
  }

  header {
    display: flex;
    align-items: flex-start;
    gap: 1rem;
  }

  .avatar {
    width: 3.5rem;
    height: 3.5rem;
    border-radius: 50%;
    overflow: hidden;
    flex-shrink: 0;
    border: 3px solid rgba(255, 255, 255, 0.8);
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
    transition: all 0.2s ease;
    cursor: pointer;
  }

  .avatar:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(0, 0, 0, 0.25);
    border-color: rgba(255, 255, 255, 1);
  }

  .avatar:active {
    transform: translateY(0);
  }

  .avatar img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .header-text {
    flex: 1;
  }

  h1 {
    font-size: 1.25rem;
    margin: 0 0 0.25rem 0;
    font-family: 'Roboto Slab', sans-serif;
  }

  h1.is-favorite {
    background: #01a129;
    color: white;
    padding: 0 0.5rem;
    border-radius: 5px;
  }

  h2 {
    font-size: 1rem;
    color: #808080;
    margin: 0 0 0.25rem 0;
  }

  p {
    font-size: 1rem;
    margin: 0;
    color: #666;
  }

  footer {
    display: flex;
    justify-content: flex-end;
    gap: 0.5rem;
  }

  footer a,
  footer button {
    padding: 0.5rem 1rem;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    text-decoration: none;
    background: #f0f0f0;
    color: #333;
  }

  footer a:hover,
  footer button:hover {
    background: #e0e0e0;
  }
</style>
