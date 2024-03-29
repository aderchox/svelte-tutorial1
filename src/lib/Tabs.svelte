<script>
    export let data;
</script>

<div>
    {#each data as item}
        <slot name="title" title={item.title} />
        <slot name="heading" heading={item.heading} />
        <slot name="content" content={item.content} />
    {/each}
</div>

<style>
    div :global(.title) {
        user-select: none;
        cursor: pointer;
    }
    div :global(.heading) {
        border: 1px solid red;
    }
</style>