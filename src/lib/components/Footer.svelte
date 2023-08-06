<footer>© 2023 Bence Boér</footer>

<style lang="scss">
  @use "$lib/styles/colors" as colors;
  @use "$lib/styles/sizes" as sizes;

  footer {
    display: flex;
    justify-content: center;
    align-items: center;

    height: sizes.$footer-height;

    background-color: colors.$primary;
    color: colors.$neutral-light;
  }
</style>