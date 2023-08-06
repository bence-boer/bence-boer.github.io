<script>
  import { onMount } from "svelte";

  /** @type {string[]} */
  export let media = [];

  /** @type {number} */
  $: item_count = media.length;

  /** @type {boolean} */
  export let thumbnails_visible = true;

  /** @type {HTMLElement} */
  let carousel;

  /** @type {number} */
  let carousel_width;

  /** @type {number} */
  let current_item_index = 0;

  onMount(() => {
    adjust_sizes();
    window.addEventListener("resize", adjust_sizes);
  });

  function adjust_sizes() {
    carousel_width = carousel.offsetWidth;
  }

  function next() {
    let target_index = current_item_index = (current_item_index + 1) % item_count;
    scroll_to(target_index);
  }

  function previous() {
    let target_index = current_item_index = (item_count + current_item_index - 1) % item_count;
    scroll_to(target_index);
  }

  /**
   * @function
   * @param {number} index - Index of element to scroll to
   * @returns
   */
  function scroll_to(index) {
    carousel.scroll((index) * carousel_width, 0);
    current_item_index = index;
  }
</script>

<div class="container">
  {#if item_count > 1 && thumbnails_visible}
    <div class="thumbnail-container">
      {#each media as _, index}
        <div class="thumbail"
             class:highlighted={index === current_item_index}
             on:click={() => scroll_to(index)}
        ></div>
      {/each}
    </div>
  {/if}

  <div class="carousel" bind:this={carousel}>
    {#each media as src}
      <div class="carousel-item">
        <img class="media-element" {src} alt="" />
      </div>
    {/each}
  </div>

  <div class="side-shadow"></div>
  <button on:click={previous} class="previous">
    <span class="material-symbols-rounded">navigate_before</span>
  </button>
  <button on:click={next} class="next">
    <span class="material-symbols-rounded">navigate_next</span>
  </button>
</div>

<style lang="scss">
  @use "$lib/styles/sizes" as sizes;
  @use "$lib/styles/colors" as colors;

  :root {
    --width: min(100%, (90vh - #{sizes.$navbar-height}) * 16 / 9);
  }

  .container {
    position: relative;
    width: var(--width);
    aspect-ratio: 16 / 9;
    overflow: hidden;

    background-color: #111111;
    border-radius: sizes.$border-radius;
  }

  .side-shadow {
    position: absolute;
    top: 0;
    bottom: 0;
    width: 100%;
    // gradient on both sides
    background: linear-gradient(to right, rgba(0, 0, 0, 0.5), transparent 10%),
                linear-gradient(to left, rgba(0, 0, 0, 0.5), transparent 10%);
    pointer-events: none;
  }

  button {
    position: absolute;
    top: 0;

    height: 100%;
    padding: 1em;
    margin: 0;

    border: none;
    background: none;
    outline: none;
    cursor: pointer;

    color: colors.$neutral-light;
    -webkit-tap-highlight-color: transparent;

    &.previous {
      left: 0;
    }

    &.next {
      right: 0;
    }
  }

  .carousel {
    width: var(--width);
    aspect-ratio: 16 / 9;

    position: relative;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: flex-end;
    gap: 2rem;

    overflow-y: auto;
    overscroll-behavior-x: contain;
    scroll-snap-type: x mandatory;
    scroll-behavior: smooth;

    border-radius: sizes.$border-radius;

    &::-webkit-scrollbar {
      display: none;
    }

    .carousel-item {
      position: relative;
      scroll-snap-align: center;
      scroll-snap-stop: always;

      min-width: var(--width);
      max-width: var(--width);
      height: 100%;
      overflow: clip;

      display: flex;
      align-items: center;
      justify-content: center;

      .media-element {
        max-width: 100%;
        max-height: 100%;
      }
    }

    /*
    &::before, &::after {
      position: fixed;
      top: sizes.$navbar-height;
      bottom: sizes.$footer-height;
      z-index: 1;
      width: sizes.$page-padding;
      content: "";
    }

    &::before {
      left: 0;
      background-image: linear-gradient(to right, colors.$primary 20%, transparent 100%);
    }

    &::after {
      right: 0;
      background-image: linear-gradient(to left, colors.$primary 20%, transparent 100%);
    }
     */

    &.full-screen {
      position: fixed;
      top: 0;
      left: 0;
      z-index: 1000;

      width: 100vw;
      height: 100vh;
      height: 100svh;
      padding: 5vmin;

      backdrop-filter: brightness(0.2);
    }
  }

  .thumbnail-container {
    position: absolute;
    bottom: 0;
    left: 0;
    min-width: 100%;
    max-width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: center;

    margin-bottom: 8px;
    gap: 6px;
  }

  .thumbnail {
    width: 8px;
    height: 8px;
    cursor: pointer;
    background: #aaa;
    border-radius: 100%;

    transition: 0.2s ease-out;

    &:hover {
      scale: 1.2;
    }
  }

  .thumbnail.highlighted {
    background-color: colors.$accent;
  }

  @media (max-width: sizes.$phone-view-breakpoint) {
    :host {
      aspect-ratio: 3 / 4;
    }

    .carousel {
      max-width: 90vw;
    }
  }
</style>