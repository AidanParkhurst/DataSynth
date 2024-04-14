<script>
    import { fade } from "svelte/transition";

    export let selected = null;
    $: toolbarWidth = (selected == null) ? "10vw" : "30vw";

</script>
<div class="toolbar" style="width: {toolbarWidth};">
    {#if selected !== null}
    <div class="selected" transition:fade={{duration: 200}}>
        <h1>Layer {selected.id}</h1>
        <div class="stat">
            <h3>Type</h3>
            <h2>{selected.type}</h2>
        </div>
        <div class="stat">
            <h3>Scale</h3>
            <h2>{selected.scale}</h2>
        </div>
        <div class="stat">
            <h3>Transform</h3>
            <h2>{selected.transform}</h2>
        </div>
    </div>
    {/if}
</div>

<style>
    .toolbar {
        position: fixed;
        top: 0;
        left: 0;
        width: 30vw;
        height: 100%;
        z-index: 100;
        /* soft glassy blur background */
        backdrop-filter: blur(5px);
        background-image: radial-gradient(circle, var(--elevated-color) 0%, transparent 100%);

        /* soft shadow to the right */
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 1);
        transition: 0.5s all;
    }
    .toolbar:after {
        content: "";
        display: block;
        position: absolute;
        top: 0;
        left: 100%;
        width: 1px;
        height: 100%;
        background-image: radial-gradient(circle, var(--border-color) 0%, transparent 100%);
        z-index: -1;
    }
    .selected {
        padding: 10vh 5vw
    }
    .selected h1 {
        margin-bottom: 3rem;
    }
    .selected h3 {
        margin-top: 0;
        margin-bottom: 0.5rem;
    }
    .selected h2 {
        margin-top: 0;
        margin-bottom: 2rem;
    }
</style>