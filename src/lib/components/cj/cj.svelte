<div class="cj">
  <img src="/cj.png" alt="" />
</div>

<style lang="sass">
  .cj
    position: absolute
    bottom: 2rem
    right: 0
    display: flex    
    align-items: flex-end
    height: 16rem
    background-color: #8668d7
    border: 2px solid #000
    border-right: none
    border-top-left-radius: 24rem
    border-bottom-left-radius: 24rem
    z-index: -1

    img
      height: 24rem
      pointer-events: none
      user-select: none

  @media screen and (max-width: 1440px)
    .cj
      height: 14rem

      img
        height: 20rem

  @media screen and (max-width: 768px)
    .cj
      position: unset
      width: fit-content
      height: 10rem
      margin: 2rem -1rem 1rem auto

      img
        height: 16rem
</style>
