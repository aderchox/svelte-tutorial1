<script>
  import Tabs from "./lib/Tabs.svelte";

  const tabsData = [
    {
      title: "AAA",
      content: "Lorem ipsum dolor sit amet consectetur adipisicing elit."
    },
    {
      title: "BBB",
      heading: "Dolor amet consectetur",
      content: `
      <h3>This is structured content.</h3>
      <p>This is a whole test paragraph, still in the content.</p>
      `
    },
  ]
</script>

<main>
  <!-- <input type="text" on:input={(e) => console.log(e.data)}> -->

  <Tabs data={tabsData}>
    <h2 slot="title" let:title class="title">
      {title}
    </h2>
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
  .tabPage {
    border: 1px solid #eee;
  }
</style>
