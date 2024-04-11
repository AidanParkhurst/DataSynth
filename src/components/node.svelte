<script>
    export let node = { id: 0, x: 0, y: 0 };

    $: nodeStyle = `
        top: calc(${node.y}px - 50px);
        left: calc(${node.x}px - 50px);
    `;
</script>

<div class="node" style="{nodeStyle}">
    <h1>{node.id}</h1>
</div>

<style>
    .node {
        position: absolute;

        display: flex;
        justify-content: center;
        align-items: center;

        width: 100px;
        height: 400px;

        background-color: var(--elevated-color);
        border-radius: 10px;
        border: 1px solid var(--border-color); 

        transition: all 0.5s;
        animation: pressDown 0.5s;
    }
    
    .node:hover {
        transform: scale(1.1);
    }

    @keyframes pressDown {
        0% {
            transform: scale(1.1);
        }
        100% {
            transform: scale(1);
        }
    }
</style>