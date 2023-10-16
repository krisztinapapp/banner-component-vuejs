<script setup>
import BannerComponent from "./components/BannerComponent.vue"
</script>

<template>
  <main>
    <banner-component
      mode="square"
      carousel-on-mobile="false"
      items='[
        {
          "type": "image",
          "aspectRatio": "square",
          "src": "https://picsum.photos/400",
          "link": "https://example.com/link1"
        },
        {
          "type": "cta",
          "title": "CTA Title",
          "button": "CTA Button",
          "link": "https://example.com/link2"
        },
        {
          "type": "image",
          "aspectRatio": "square",
          "src": "https://picsum.photos/400",
          "link": "https://example.com/link3"
        }
      ]'
    >
    </banner-component>

    <banner-component
      mode="square"
      carousel-on-mobile="true"
      items='[
        {
          "type": "cta",
          "title": "CTA Title",
          "button": "CTA Button",
          "link": "https://example.com/link1"
        },
        {
          "type": "image",
          "aspectRatio": "square",
          "src": "https://picsum.photos/400",
          "link": "https://example.com/link2"
        },
        {
          "type": "image",
          "aspectRatio": "square",
          "src": "https://picsum.photos/400",
          "link": "https://example.com/link3"
        },
        {
          "type": "image",
          "aspectRatio": "square",
          "src": "https://picsum.photos/400",
          "link": "https://example.com/link3"
        },
        {
          "type": "image",
          "aspectRatio": "square",
          "src": "https://picsum.photos/400",
          "link": "https://example.com/link3"
        },
        {
          "type": "image",
          "aspectRatio": "square",
          "src": "https://picsum.photos/400",
          "link": "https://example.com/link3"
        }
      ]'
    >
    </banner-component>

    <banner-component
      mode="rectangle"
      carousel-on-mobile="false"
      items='[
        {
          "type": "image",
          "aspectRatio": "rectangle",
          "src": "https://picsum.photos/1200/400",
          "link": "https://example.com/link1"
        },
        {
          "type": "image",
          "aspectRatio": "square",
          "src": "https://picsum.photos/400",
          "link": "https://example.com/link1"
        },
        {
          "type": "cta",
          "title": "CTA Title",
          "button": "CTA Button",
          "link": "https://example.com/link1"
        }
      ]'
    >
    </banner-component>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
