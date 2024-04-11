<script>
    import { createEventDispatcher } from "svelte";
    let dispatch = createEventDispatcher();

    export let node = { id: 0, x: 0, y: 0 };
    
    let deleteNode = () => {
        dispatch('delete', node.id);
    };

    $: nodeStyle = `
        top: calc(${node.y}px - 50px);
        left: calc(${node.x}px - 50px);
    `;

    let dragStartX, dragStartY;
    let handleDragStart = (e) => {
      dragStartX = e.clientX;
      dragStartY = e.clientY;
    };
    let handleDrag = (e) => {
      if (e.clientX === 0 && e.clientY === 0) return; // Ignore the drag event that fires with 0,0 when the drag ends
      node.x += e.clientX - dragStartX;
      node.y += e.clientY - dragStartY;
      dragStartX = e.clientX;
      dragStartY = e.clientY;
    };
    let handleDragEnd = (e) => {
      node.x += e.clientX - dragStartX;
      node.y += e.clientY - dragStartY;
    };
</script>

<div class="layer" style="{nodeStyle}"
    draggable="true"
    on:drag={handleDrag}
    on:dragend={handleDragEnd}
    on:dragstart={handleDragStart}
    role="button"
    tabindex="0"
    >
    <div class="node">
        <div class="info">
            <h2>Layer {node.id}</h2>
            <div class="stat">
                <h4>Type</h4>
                <h3>Recurrent</h3>
            </div>
            <div class="stat">
                <h4>Scale</h4>
                <h3>10</h3>
            </div>
            <div class="stat">
                <h4>Transform</h4>
                <h3>Sigmoid</h3>
            </div>
        </div>
        <div class="buttons">
            <button class="delete" on:click={deleteNode}>
                <!--SVG X Icon-->
                <svg xmlns="http://www.w3.org/2000/svg" class="icon"
                    stroke="var(--secondary-color)"
                    fill="none"
                    viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round"
                        stroke-width="2"
                        d="M6 18L18 6M6 6l12 12">
                    </path>
                </svg>
            </button>
            <button class="config">
                <!--SVG Hamburger Icon-->
                <svg xmlns="http://www.w3.org/2000/svg" class="icon"
                    stroke="var(--secondary-color)"
                    fill="none"
                    viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round"
                        stroke-width="2"
                        d="M4 6h16M4 12h16m-7 6h7">
                    </path>
                </svg>
            </button>
        </div>
    </div>
</div>

<style>
    .layer {
        position: absolute;
        display: flex;
        flex-direction: column;
        cursor: pointer;

        transition: all 0.5s;
        animation: pressDown 0.5s;
    }
    .info {
        padding: 0 20px;
        margin-right: 10px;
        margin-bottom: 2rem;
    }

    h2 {
        margin-bottom: 2rem;
    }
    h3 {
        margin-top: 0;
    }

    h4 {
        color: var(--secondary-color);
        margin-bottom: .5rem;
        margin-top: 0;
    }

    .buttons {
        display: flex;
        justify-content: space-between;
        flex-direction: row;
        padding: 0 5px;
    }
    button {
        padding: 0;
        margin: 0;
        background: none;
        border: none;
    }
    .icon {
        padding: 10px;
        border-radius: 5px;
        width: 25px;
        cursor: pointer;
        transition: 0.5s all;
    }
    .icon:hover {
        stroke: var(--primary-color); 
        background-color: var(--elevated-color);
    }
    .node {
        display: flex;
        justify-content: space-between;
        flex-direction: column;
        height: fit-content;

        background-color: var(--elevated-color);
        background-image: linear-gradient(0deg, var(--background-color) 0%, var(--elevated-color) 30%);
        border-radius: 10px;
        border: 1px solid var(--border-color); 
        
        color: var(--primary-color);
        transition: all 0.5s;
    }
    
    .node:hover {
        border-color: var(--secondary-color)
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