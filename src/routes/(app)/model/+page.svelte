<script>
    import Node from "../../../components/node.svelte";

    let nodes = [];
    
    let addNode = (e) => {
        let x = e.clientX - e.target.getBoundingClientRect().left;
        let y = e.clientY - e.target.getBoundingClientRect().top;
        nodes = [...nodes, { id: nodes.length, x: x, y: y}];
    }
    
    let handleKey = (e) => {
        // TODO: Keyboard shortcuts
        return;
    }

    let deleteNode = (event) => {
        nodes = nodes.filter(node => node.id !== event.detail);
    };
</script>

<div class="workspace">
    <div role="button" tabindex=0 on:keydown={handleKey} on:click={addNode} class="background">
    </div>
    {#each nodes as node}
    <Node {node} on:delete={deleteNode}/>
    {/each}
</div>

<style>
    .workspace {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        color: var(--primary-color);
    }

    .background {
        position: relative;
        height: 100%;
        width: 100%;

        display: flex;
        flex-wrap: wrap;
        gap: 1rem;
    }
</style>