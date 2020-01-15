<script>
  import Fetch from "./Fetch.svelte";
  import Form from "./Form.svelte";

  const props = {
    url: "https://jsonplaceholder.typicode.com/todos",
    title: "A list of todos"
  };
  let searchTerm;

  function handleSubmit() {
    console.log({ this: this });
    const { value } = this.elements.search;
    searchTerm = value;
  }
</script>

<Form {handleSubmit} />

<Fetch {searchTerm} let:data>
  <ul>
    {#each data as link}
      <li>
        <a href={link.url}>{link.title}</a>
      </li>
    {/each}
  </ul>
</Fetch>
