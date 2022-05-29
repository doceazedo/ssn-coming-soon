<script lang="ts">
  import { fade, scale } from 'svelte/transition';
  import { quintOut } from 'svelte/easing';
  import { CloseIcon, DiscordIcon, TwitterIcon } from '$lib/components/icons';

  export let isOpen: boolean, success: boolean;

  const successTitle = 'Tudo certo! 🤩';
  const successParagraph = 'Sua conta foi adicionada à lista de espera.';

  const errorTitle = 'Algo deu errado... 😭';
  const errorParagraph =
    'Ocorreu um erro no envio, relaxe e tente novamente mais tarde.';

  const closeModal = () => (isOpen = false);
</script>

{#if isOpen}
  <div class="modal" transition:fade={{ duration: 200 }}>
    <div class="modal-background" on:click={closeModal} />
    <div
      class="modal-content"
      transition:scale={{
        duration: 200,
        opacity: 0,
        start: 0.75,
        easing: quintOut,
      }}
    >
      <div class="modal-card">
        <h1 class="modal-card-title">
          {success ? successTitle : errorTitle}
          <span class="close" on:click={closeModal}>
            <CloseIcon />
          </span>
        </h1>
        <div class="modal-card-content">
          <p>{success ? successParagraph : errorParagraph}</p>
          <p>
            Por enquanto, fique à vontade para fazer parte do nosso novo grupo
            no Discord, todas as novidades do ssn.gg, inclusive a data de
            reabertura serão noticiadas por lá e também pelo Twitter.
          </p>
          <p>
            Note que não há necessidade de cadastrar outras contas na lista de
            espera, apenas uma por jogador é o suficiente. Você poderá jogar com
            quantas contas alternativas quiser.
          </p>
          <p>– DoceAzedo</p>
          <div class="buttons">
            <a
              href="https://discord.gg/DChTnVTuKp"
              target="_blank"
              class="button discord"
            >
              <DiscordIcon /> Junte-se ao Discord
            </a>
            <a
              href="https://twitter.com/servidorsemnome"
              target="_blank"
              class="button twitter"
            >
              <TwitterIcon /> Seguir no Twitter
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
{/if}

<style lang="sass">
  @import '../../../sass/mixins'

  .modal
    position: fixed
    top: 0
    left: 0
    display: flex
    justify-content: center
    align-items: center
    width: 100%
    height: 100%

    &-background    
      position: absolute
      top: 0
      left: 0
      width: 100%
      height: 100%
      background-color: rgba(#f4ffaa, .75)

    &-content
      position: relative
      width: 40rem
      max-width: calc(100% - 1rem)
      max-height: 100%
      overflow-y: auto

    &-card
      background-color: #fff
      @include neubrutalist-shadow
      overflow: hidden

      &-title
        display: flex
        align-items: center
        justify-content: space-between
        height: 2.75rem
        padding-left: 1rem
        font-family: 'Space Grotesk', sans-serif
        font-weight: 700
        font-size: 1.25rem
        background-color: #8668d7
        border-bottom: 1px solid #000

        .close
          display: flex
          justify-content: center
          align-items: center
          height: 2.75rem
          width: 2.75rem
          cursor: pointer

          :global(svg)
            width: 1.5rem
            height: 1.5rem

      &-content
        display: flex
        flex-direction: column
        gap: .75rem
        padding: 1rem

  .buttons
    display: flex
    gap: .75rem

  .button
    display: flex
    align-items: center
    gap: .75rem
    width: fit-content
    height: 3rem
    padding: 0 1rem
    margin-top: .5rem
    color: #fff
    text-decoration: none
    cursor: pointer
    @include neubrutalist-shadow

    &.discord
      background-color: #5865F2

    &.twitter
      background-color: #1d9bf0

    :global(svg)
      height: 1.5rem
      width: 1.5rem

  @media screen and (max-width: 768px)
    .buttons
      flex-direction: column
      gap: .25rem
</style>
