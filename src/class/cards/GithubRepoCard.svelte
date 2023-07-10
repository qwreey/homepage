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
  let description:string = "..."
  let color:string = "transparent"
  let overlayColor:string = "transparent"
  let lang

  fetch(`https://api.github.com/repos/${username}/${repo}`).then(async response=>{
    if (!response.ok) {
      console.log(response.statusText)
    } else {
      let result = await response.json()
      forks = ""+result.forks_count
      stars = ""+result.stargazers_count
      description = ""+result.description
      lang = ""+result.language
      if (langcolor[lang]) {
        color = langcolor[lang]
        overlayColor = `linear-gradient(135deg, ${color}1d, #00000000 70%)`
      }
    }
  })
</script>

<div
  id="main"
  style:--overlay-color={overlayColor}
  class:dark={theme == "dark"}
  class:light={theme == "light"}>
  <div id="wrapper">
    <div id="frame">
      <div id="icon">
      </div>
      <div id="content">
        <p id="title"><span id="username">{username}</span>/<span id="repo">{repo}</span></p>
        <p id="description">{description}</p>
      </div>
    </div>
    <div id="icons">
      <StarIcon height="24" width="24" theme={theme}/>
      <p>{stars}</p>
      <ForkIcon height="24" width="24" theme={theme}/>
      <p>{forks}</p>
      <div id="langdot" style:background-color={color}></div>
      <p>{lang}</p>
    </div>
    <div id="footer">
      <GithubIcon height="22" width="22" theme={theme}/>
      <p>Source codes on GitHub</p>
    </div>
  </div>
</div>

<style lang="scss">
  @use "card_base";
  #main { @include card_base.use; }
  #wrapper { background: var(--overlay-color); }
</style>
