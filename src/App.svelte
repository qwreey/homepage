<script lang="ts">
</script>

<main>
  <div class="title-animations">
    {#each {length: 5} as _}
      <p>머찐 애니메이션 효과를 연구해요</p>
    {/each}
  </div>
</main>

<style lang="scss">
  main {
    display: flex;
    flex-direction: column;
  }

  .title-animations {
    position: relative;
    >p:not(p:first-child) {
      position: absolute;
      top: 0;
    }
    p{
      margin: 0;
      font-size: 3em;
    }

    @for $nth from 1 through 5 {
      @keyframes title-animation-#{$nth} {
        0% {
          transform: translateY(#{0.6 * $nth}em);
          filter: blur(12px);
          @if $nth != 1 {
            opacity: #{(1 - $nth/6)/1.2};
          } @else { opacity: 1; }
        }
        100% {
          transform: none;
          filter: #{$nth and none or blur(6px)};
          @if $nth != 1 {
            opacity: #{(1 - $nth/6)/4};
          } @else { opacity: 1; }
        }
      }
      :nth-child(#{$nth}) {
        animation: title-animation-#{$nth} #{1.6 + $nth*0.06}s 1 cubic-bezier(0.19, 1, 0.22, 1);
        @if $nth != 1 {
          opacity: 0;
        }
      }
    }
  }
</style>
