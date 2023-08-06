<nav>
  <ul>
    <li>
      <a href="/">
        <span class="material-symbols-rounded">home</span>Home
      </a>
    </li>
  </ul>
</nav>

<style lang="scss">
  @use "$lib/styles/colors" as colors;
  @use "$lib/styles/sizes" as sizes;

  nav {
    height: sizes.$navbar-height;
    border-bottom: 1px solid colors.$primary;
  }

  ul {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 100%;
    padding: 0 1rem;
    margin: 0;
    list-style: none;
  }

  a {
    display: flex;
    align-items: flex-end;
    justify-content: center;
    gap: 0.5rem;

    color: colors.$primary-inactive;
    font-size: 1.2rem;
    font-weight: 600;
    text-transform: uppercase;
    cursor: pointer;
    text-decoration: none;
  }
</style>