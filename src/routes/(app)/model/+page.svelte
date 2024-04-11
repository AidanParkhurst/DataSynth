<script>
    import Node from "../../../components/node.svelte";

    let nodes = [];
    
    let addNode = (e) => {
        let x = e.clientX - e.target.getBoundingClientRect().left;
        let y = e.clientY - e.target.getBoundingClientRect().top;
        nodes = [...nodes, { id: nodes.length, x: x, y: y}];
        console.log(nodes);
    }
</script>

<div class="container">
    <div role="button" tabindex=0 on:keydown={addNode} on:click={addNode} class="workspace">
        {#each nodes as node}
        <Node {node}/>
        {/each}
    </div>
</div>

<style>
    .container {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        color: var(--primary-color);
    }
    .workspace {
        position: relative;
        height: 100%;
        width: 100%;

        display: flex;
        flex-wrap: wrap;
        gap: 1rem;
    }
</style>