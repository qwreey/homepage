{#if (window.navigator.userAgent.match(/[Vv]ersion\/[\.\d]+ *[Ss]afari\/[\.\d]+$/)!==null)}
  <div>
    <p>사파리는 CSS 렌더링이 다른점이 많아 페이지가 온전하게 보이지 않을 수 있습니다. 더 나은 경험을 위해 Chrome, Firefox 계열 브라우저를 이용해주세요.</p>
  </div>
{/if}

<style lang="scss">
  div {
    top: 20px;
    position: sticky;
    backdrop-filter: blur(8px) brightness(50%);
    -webkit-backdrop-filter: blur(8px) brightness(50%);
    margin: 22px;
    padding: 0 22px;
    border-radius: 16px;
  }
</style>
