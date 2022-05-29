<script lang="ts">
  import { NotifyFormModal } from '.';
  import { SpinnerIcon } from '$lib/components/icons';

  const to = 'wl@doceazedo.com';
  let value = '';
  let isLoading = false;
  let isModalOpen = false;
  let success = true;

  const handleSubmit = async () => {
    if (isLoading || !value.length) return;
    isLoading = true;

    try {
      const resp = await fetch(`https://formsubmit.co/ajax/${to}`, {
        method: 'POST',
        headers: {
          Accept: 'application/json',
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          nickname: value,
        }),
      });
      const data = await resp.json();
      success = data?.success == 'true';
    } catch (error) {
      success = false;
    }

    isLoading = false;
    isModalOpen = true;
  };
</script>

<form class="form" on:submit|preventDefault={handleSubmit}>
  <div class="username">
    <input
      class="input"
      type="text"
      spellcheck="false"
      placeholder="Nickname"
      bind:value
    />
    <img class="head" src="https://mc-heads.net/head/{value}" alt="" />
  </div>
  <button type="submit" class="button" class:is-loading={isLoading}>
    Entrar na lista de espera
    <span class="loading">
      <SpinnerIcon />
    </span>
  </button>
</form>

<NotifyFormModal bind:isOpen={isModalOpen} {success} />

<style lang="sass">
  @import '../../../sass/mixins'

  .form
    display: flex
    gap: .75rem

    .username
      position: relative

      .head
        position: absolute
        left: -.75rem
        top: -.75rem
        height: 2rem
        pointer-events: none
        user-select: none

    .input
      height: 3rem
      padding: 0 1rem
      width: 16rem
      outline: none
      @include neubrutalist-shadow

    .button
      position: relative
      height: 3rem
      padding: 0 1rem
      background-color: #feca01
      outline: none
      cursor: pointer
      @include neubrutalist-shadow

      .loading
        position: absolute
        top: 0
        left: 0
        display: flex
        justify-content: center
        align-items: center
        width: 100%
        height: 100%
        background-color: #feca01
        transition: all .2s ease

        :global(svg)
          width: 2rem
          height: 2rem

      &:not(.is-loading) .loading
        opacity: 0
        pointer-events: none

  @media screen and (max-width: 768px)
    .form
      .username
        flex-grow: 1

      .input
        width: 100%

      .button
        flex-shrink: 0
</style>
