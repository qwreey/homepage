<script lang="ts">
</script>

<main>

  <div class="trail-effect">
    {#each {length: 5} as _}
      <p>Qwreey</p>
    {/each}
  </div>
  <div class="subtitle-holder">
    {#each ['이것','저것\xa0','뭐든\xa0','만듭','니다.'] as text}
      <p>{text}</p>
    {/each}
  </div>
  <div class="stars"><div/><div/><div/></div>

</main>

<style lang="scss">

  @use "starEffect";
  @use "shadowTrailEffect";
  @use "trailEffect";

  main {
    display: flex;
    flex-direction: column;
  }

  .stars {
    >:nth-child(1) {
      @include starEffect.use(100,2000,2);
    }
  }

  // 서브타이틀
  .subtitle-holder {
    display: flex;
    flex-direction: row;
    p { font-size: 2em; }
    @for $nth from 1 through 5 {
      >:nth-child(#{$nth}) {
        @include shadowTrailEffect.use(#{0.1 * $nth}s);
      }
    }
  }

  // 타이틀
  .trail-effect {
    font-size: 3em;
    @include trailEffect.use(0s);
  }

</style>
