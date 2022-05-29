<header class="header">
  <h1 class="title">ssn.gg <small class="emoji">😋🍉🍋</small></h1>
  <p class="subtitle">
    A quarta e definitiva iteração da autêntica experiência anarquista.
  </p>
</header>

<style lang="sass">
  .header
    display: flex
    flex-direction: column
    gap: .5rem

    .title
      display: flex
      align-items: center
      justify-content: space-between
      font-family: 'Space Grotesk', sans-serif
      font-size: 6rem
      font-weight: 700
      letter-spacing: -.25rem

      .emoji
        font-size: 4rem

    .subtitle
      font-size: 1.5rem
      font-weight: 500

  @media screen and (max-width: 1440px)
    .header
      .title
        font-size: 4rem

        .emoji
          font-size: 3rem

      .subtitle
        font-size: 1.2rem

  @media screen and (max-width: 768px)
    .header .title .emoji
      font-size: 2rem
</style>
