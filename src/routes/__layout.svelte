<script lang="ts">
  import '../sass/minireset.sass';
  import '../sass/global.sass';
</script>

<div class="container">
  <slot />
</div>

<style lang="sass">
  .container
    display: flex
    flex-direction: column
    gap: 4rem
    max-width: 1440px
    height: 100%
    margin: 0 auto
    padding: 2rem 0

  @media screen and (max-width: 1440px)
    .container
      max-width: 1080px
      padding: 2rem
      gap: 3rem

  @media screen and (max-width: 768px)
    .container
      padding: 1rem
</style>
