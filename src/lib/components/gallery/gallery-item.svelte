<script lang="ts">
  import { TopbarButtons } from '$lib/components/icons';

  export let image: string, position: 'left-sm' | 'left-xl' | 'top-xl';
</script>

<div
  class="gallery-item"
  class:left-sm={position == 'left-sm'}
  class:left-xl={position == 'left-xl'}
  class:top-xl={position == 'top-xl'}
>
  <div class="gallery-item-topbar">
    <TopbarButtons />
  </div>
  <figure class="gallery-item-image" style="background-image:url({image})" />
</div>

<style lang="sass">
  .gallery-item
    display: flex
    flex-direction: column
    width: 16rem
    height: 16rem
    background-color: rgba(#fff, .75)
    border: 1px solid #000
    border-radius: .25rem
    box-shadow: 3px 3px 0 0 #000
    overflow: hidden
    transition: all .2s ease

    &.left-sm
      margin-left: -1rem

      .gallery-item-topbar
        background-color: #57F287

    &.left-xl
      margin-left: -4rem

      .gallery-item-topbar
        background-color: #ED4245

    &.top-xl
      margin-top: 6rem

      .gallery-item-topbar
        background-color: #EB459E

    &:hover
      box-shadow: 5px 5px 0 0 #000

    &-topbar
      display: flex
      justify-content: flex-end
      padding: .5rem
      border-bottom: 1px solid #000

      :global(svg)
        height: .75rem

    &-image
      flex-grow: 1
      background-position: center
      background-repeat: no-repeat
      background-size: cover

  @media screen and (max-width: 768px)
    .gallery-item
      margin: 0 !important
</style>
