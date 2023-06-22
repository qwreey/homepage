<script lang="ts">
</script>

<main>

  <!-- 별 효과 -->
  <div class="stars"><div/><div/><div/></div>

  <div class="page-holder">

    <!-- 첫번째 페이지 -->
    <div class="page">
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
    </div>

  </div>

</main>

<style lang="scss">

  @use "common";
  @use "starEffect";
  @use "shadowTrailEffect";
  @use "trailEffect";

  main {
    background: radial-gradient(ellipse at bottom, #1d1a3b 0%, #0b0911 100%);
    width: 100vw; height: 100vh;
    display: flex;
    flex-direction: column;

    // 페이지 스크롤 (스넵 스크롤)
    .page-holder {
      scroll-behavior: smooth;
      scroll-snap-type: y mandatory;
      overflow: scroll;
      width: 100vw; height: 100vh;
      .page {
        width: 100vw; height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
      }
    }
  }

  // 별 효과
  .stars {
    position: absolute;
    top: 0; left: 0;
    width: 100vw; height: 100vh;
    margin: 0; padding: 0;
    overflow: hidden;
    // 작은별
    >:nth-child(1) {
      @include starEffect.use(
        $n: 200, $spread: 2000, $size: 2, $speed: 1, $color: rgb(180,180,180)
      );
    }
    // 큰별
    >:nth-child(2) {
      @include starEffect.use(
        $n: 80, $spread: 2000, $size: 5, $speed: 0.6, $color: rgb(180,180,180)
      );
    }
  }

  // 서브타이틀
  .subtitle-holder {
    display: flex;
    flex-direction: row;
    p {
      @include common.text-gradient(white, #ceb4ff);
      font-size: 2em;
    }
    @for $nth from 1 through 5 {
      >:nth-child(#{$nth}) {
        @include shadowTrailEffect.use(#{0.1 * $nth}s);
      }
    }
  }
  
  // 타이틀
  .trail-effect {
    p {
      color: #ddcbff;
      font-size: 3em;
    }
    @include trailEffect.use(0s);
  }

</style>
