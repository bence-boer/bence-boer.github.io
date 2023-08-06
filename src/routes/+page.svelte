<script>
  let mode = "dark-mode";
</script>

<div class="main-container {mode}">
  <a href="/gallery" class="tile gallery" tabindex="0">
    <h2>Gallery</h2>
  </a>
  <a href="/projects" class="tile projects" tabindex="0">
    <h2>Projects</h2>
  </a>
  <a href="/about" class="tile about" tabindex="0">
    <h2>About</h2>
  </a>
  <a href="/contacts" class="tile contacts" tabindex="0">
    <h2>Contacts</h2>
  </a>
</div>

<style lang="scss">
  @use "$lib/styles/colors" as colors;
  @use "$lib/styles/sizes" as sizes;


  .main-container {
    height: 100%;

    display: grid;
    grid-template-areas:
        ".       projects projects contacts"
        "gallery about    .        contacts"
        ".       about    .        .       ";
    grid-template-rows: 1fr 1fr 1fr;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    gap: 1em;
  }

  .tile {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0.5em;

    background-color: colors.$accent;

    font-size: 1.5rem;
    text-transform: uppercase;
    word-break: break-all;

    transition: background-color 0.2s;
    border-radius: sizes.$border-radius;
  }

  .tile:hover {
    background-color: colors.$neutral-light;
    color: colors.$neutral-dark;
  }

  .tile h2 {
    margin: 0;
    font-size: 2.5em;
    font-weight: 200;
  }

  .gallery {
    grid-area: gallery;
  }

  .projects {
    grid-area: projects;
  }

  .about {
    grid-area: about;
  }

  .contacts {
    grid-area: contacts;
  }
</style>