<script lang="ts">
  export let theme:string
  export let username:string
  export let repo:string

  const url = `/api/pin?username=${username}&amp;repo=${repo}`



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
