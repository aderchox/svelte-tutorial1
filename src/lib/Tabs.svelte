<script>
    export let data;
    export let activeTitle;
</script>

<div>
    <slot name="titles" titles={data.map(item => item.title)} />
    {#each data as item}
        {#if item.title === activeTitle}
            <slot name="heading" heading={item.heading} />
            <slot name="content" content={item.content} />
        {/if}
    {/each}
</div>

<style>
    div :global(.titles) {
        padding: 0;
        display: flex;
        gap: 20px;
    }
    div :global(.title) {
        user-select: none;
        cursor: pointer;
    }
    div :global(.title.active) {
        color: red;
    }
    div :global(.title:hover) {
        color: rgb(245, 125, 125);
    }
    div :global(.heading) {
        padding: 20px;
        border: 1px solid red;
    }
    div :global(.tabPage) {
        padding: 20px;
    }
</style>