<script lang="ts">
  import langcolor from "../../assets/langcolor.json"
  import ForkIcon from "../icons/ForkIcon.svelte"
  import StarIcon from "../icons/StarIcon.svelte"
  import GithubIcon from "../icons/GithubIcon.svelte"
  export let theme:string
  export let username:string
  export let repo:string

  let stars:string = "..."
  let forks:string = "..."

  fetch(`https://api.github.com/repos/${username}/${repo}`).then(async response=>{
    if (!response.ok) {
      console.log(response.statusText)
    } else {
      let result = await response.json()
      forks = ""+result.forks_count
      stars = ""+result.stargazers_count
    }
  })
</script>

<div
  id="main"
  class:dark={theme == "dark"}
  class:light={theme == "light"}>

  <div id="frame">
    <div id="icon">
    </div>
    <div id="content">
      <p id="title"><span id="username">{username}</span>/<span id="repo">{repo}</span></p>
    </div>
  </div>
  <div id="icons">
    <StarIcon height="24" width="24" theme="dark"/>
    <p>{stars}</p>
    <ForkIcon height="24" width="24" theme="dark"/>
    <p>{forks}</p>
  </div>
  <div id="footer">
    <GithubIcon height="22" width="22" theme="dark"/>
    <p>Source codes on GitHub</p>
  </div>

</div>

<style lang="scss">
  @use "card_base";
  #main { @include card_base.use; }
</style>
