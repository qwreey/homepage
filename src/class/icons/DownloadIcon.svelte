<script lang="ts">
  export let theme:string
  export let width:string
  export let height:string

  let stroke:string
  switch (theme) {
    case "dark":
    case "Dark":
      stroke = "white"
      break
    case "light":
    case "Light":
      stroke = "black"
      break
  }
</script>

<svg width="{width}" height="{height}" viewBox="0 0 23 23" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M4 19L19 19" stroke="{stroke}" stroke-width="1.8" stroke-linecap="round"/>
  <path d="M19 15V19" stroke="{stroke}" stroke-width="1.8" stroke-linecap="round"/>
  <path d="M11.5 14L11.5 4" stroke="{stroke}" stroke-width="1.8" stroke-linecap="round"/>
  <path d="M11.5 14L6.55025 9.05025" stroke="{stroke}" stroke-width="1.8" stroke-linecap="round"/>
  <path d="M11.5 14L16.4497 9.05025" stroke="{stroke}" stroke-width="1.8" stroke-linecap="round"/>
  <path d="M4 19V15" stroke="{stroke}" stroke-width="1.8" stroke-linecap="round"/>
</svg>
