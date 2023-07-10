<script lang="ts">
  export let theme:string;
  export let repo:string;

</script>

<div
  id="main"
  class:dark={theme == "dark"}
  class:light={theme == "light"}>

  <div id="frame">
    <div id="icon">

    </div>
    <div id="content">

    </div>
  </div>
  <div id="icons">

  </div>

</div>

<style lang="scss">
  #main {
    &.dark {
    }
    &.light {
    }

    #frame {
      display: flex;
    }
  }

</style>
