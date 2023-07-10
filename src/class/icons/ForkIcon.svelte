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
  <circle cx="6.5" cy="5.5" r="2.1" stroke="{stroke}" stroke-width="1.8"/>
  <circle cx="16.5" cy="5.5" r="2.1" stroke="{stroke}" stroke-width="1.8"/>
  <path d="M6.5 12H16.5" stroke="{stroke}" stroke-width="1.8" stroke-linecap="round"/>
  <path d="M16.5 8V12" stroke="{stroke}" stroke-width="1.8" stroke-linecap="round"/>
  <path d="M6.5 12V8" stroke="{stroke}" stroke-width="1.8" stroke-linecap="round"/>
  <circle cx="11.5" cy="18.5" r="2.1" stroke="{stroke}" stroke-width="1.8"/>
  <path d="M11.5 12V16" stroke="{stroke}" stroke-width="1.8" stroke-linecap="round"/>
</svg>
