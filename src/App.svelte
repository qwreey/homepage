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

<!--
SUGGEST: 바텀바 vs 탑바 vs 사이드바 (모바일 / pc 여부에 따라 사이드/ 바텀 유무?)
TODO: 바텀바에 repo, 게시글, 정보 페이지로 각각 스크롤하는 버튼넣기 (아이콘도. 마우스 올리면 위에 툴팁도 뜸)
TODO: '아래로 스크롤하세요' 텍스트 & 아이콘 만들어서 아래쪽에 오버레이 해놓기
TODO: 리포 부분에는 스크롤 안에 스크롤 들어가는식으로 만들기 (스크롤 끝까지 하면 다음페이지 넘어가지는)
TODO: 바텀바 아이콘에 지금위치 가르키는 인디케이터 넣기 (애니메이션과 함깨!)
-->

<style lang="scss">

  @use "common";
  @use "starEffect";
  @use "shadowTrailEffect";
  @use "trailEffect";

  // 변수
  $bottom-bar-size: 2em;

  main {
    background: radial-gradient(ellipse at bottom, #1d1a3b 0%, #0b0911 100%);
    width: 100vw; height: 100vh;
    display: flex;
    flex-direction: column;
  }

  // 바텀바 (메뉴바)
  // .bottom-bar {}

  // 페이지 스크롤 (스넵 스크롤)
  .page-holder {
    scroll-behavior: smooth;
    scroll-snap-type: y mandatory;
    overflow: scroll;
    width: 100vw; height: calc(100vh - $bottom-bar-size);
    // 내부 페이지
    .page {
      width: 100vw; height: calc(100vh - $bottom-bar-size);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
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
