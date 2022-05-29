<script lang="ts">
  import { GalleryItem } from '.';
</script>

<div class="gallery">
  <div class="gallery-column">
    <GalleryItem image="/gallery-1.webp" position="left-sm" />
    <GalleryItem image="/gallery-2.webp" position="left-xl" />
  </div>
  <div class="gallery-column">
    <GalleryItem image="/gallery-3.webp" position="top-xl" />
  </div>
</div>

<style lang="sass">
  .gallery
    display: flex
    gap: 2rem

    &-column
      display: flex
      flex-direction: column
      gap: 2rem

  
  @media screen and (max-width: 768px)
    .gallery
      padding: 0 1rem 5px
      margin-left: -1rem
      width: calc(100% + 2rem)
      overflow-x: scroll

      &-column
        flex-direction: row
</style>
