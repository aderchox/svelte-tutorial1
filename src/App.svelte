<script>
  import Tabs from "./lib/Tabs.svelte";

  const tabsData = [
    {
      title: "AAA",
      content: "This is bare content. Lorem ipsum dolor sit amet consectetur adipisicing elit."
    },
    {
      title: "BBB",
      heading: "This is heading. Dolor amet consectetur",
      content: `
      <h3>This is structured content.</h3>
      <p>This is a whole test paragraph, still in the content.</p>
      `
    },
  ]
  let activeTitle = tabsData[0].title;
</script>

<main>
  <Tabs data={tabsData} {activeTitle}>
    <ul slot="titles" let:titles class="titles" role="list">
      {#each titles as title}
        <li
          class="title"
          class:active={activeTitle === title}
          on:click={e => activeTitle = title}
        >
          <h2>{title}</h2>
        </li>
      {/each}
    </ul>
    <h3 slot="heading" let:heading class={heading ? "heading" : ""}>
      {heading ?? ""}
    </h3>
    <div slot="content" let:content class="tabPage">
      <!-- XSS warning: Be careful to feed it yourself! -->
      {@html content}
    </div>
  </Tabs>
</main>

<style>
  /* Styling is possible from here too. */
  .tabPage {
    border: 1px solid #eee;
    margin-top: 10px;
  }
  main .tabPage > :global(h3) {
    margin: 0;
  }
</style>
