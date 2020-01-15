<script>
  import { onMount } from "svelte";

  export let url = "https://academy.valentinog.com/api/link/";
  export let searchTerm = undefined;
  $: regex = new RegExp(searchTerm, "gi");

  let jsonResponse = [];

  $: data = searchTerm
    ? jsonResponse.filter(element => element.title.match(regex))
    : jsonResponse;

  onMount(async () => {
    const response = await fetch(url);
    const json = await response.json();
    jsonResponse = json;
  });
</script>

<slot {data} />
