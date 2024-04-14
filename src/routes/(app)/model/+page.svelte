<script>
    import Node from "../../../components/node.svelte";
    import Toolbar from "../../../components/toolbar.svelte";
    import ActionMenu from "../../../components/menu.svelte";

    let nodes = [];
    let menu = {x: 0, y: 0, visible: false};
    let selected = null; 

    let handleKey = (e) => {
        // TODO: Keyboard shortcuts
        return;
    }

    let openMenu = (e) => {
        let x = e.clientX - e.target.getBoundingClientRect().left - 99;
        let y = e.clientY - e.target.getBoundingClientRect().top - 5;
        
        menu = {x: x, y: y, visible: true};
    }

    let addNode = (e) => {
        let x = e.detail.x;
        let y = e.detail.y;
        nodes = [...nodes, {
                id: nodes.length,
                x: x, y: y,
                type: "Dense",
                scale: Math.floor(Math.random() * 10 + 1),
                transform: "Sigmoid"}];
    }
    let deleteNode = (event) => {
        nodes = nodes.filter(node => node.id !== event.detail);
        if(selected !== null && selected.id === event.detail) selected = null;
    }
    let selectNode = (event) => {
        selected = nodes.find(node => node.id === event.detail);
    }

    /* TODO: Make zoom function better, rn the clickable area shrinks on zoom out*/
    let zoomOut = () => {
        /* Reduce the scale of the workspace, */
        let workspace = document.querySelector('.workspace');
        let scale = parseFloat(getComputedStyle(workspace).getPropertyValue('--scale'));
        scale = Math.max(0.5, scale - 0.1);
        workspace.style.setProperty('--scale', scale);
    }
    let zoomIn = () => {
        /* Increase the scale of the workspace, */
        let workspace = document.querySelector('.workspace');
        let scale = parseFloat(getComputedStyle(workspace).getPropertyValue('--scale'));
        scale = Math.min(2, scale + 0.1);
        workspace.style.setProperty('--scale', scale);
    }
</script>

<Toolbar {selected}/>
<div class="container">
    <div class="workspace">
        <div role="button" tabindex=0 on:keydown={handleKey} on:click={openMenu} class="background">
        </div>
        {#each nodes as node}
        <Node {node} on:delete={deleteNode} on:select={selectNode}/>
        {/each}
    </div>
    <ActionMenu {menu} on:add={addNode}/>
    <div class="zoomControls">
        <button class="plus icon" on:click={zoomIn}>
            <!--SVG Plus Icon-->
            <svg xmlns="http://www.w3.org/2000/svg" 
                viewBox="0 0 24 24" stroke="var(--secondary-color)" fill="none" width="24" height="24">
                <path stroke-linecap="round" stroke-linejoin="round"
                    stroke-width="2"
                    d="M12 6v6m0 0v6m0-6h6m-6 0H6"/>
            </svg>
        </button>
        <button class="minus icon" on:click={zoomOut}>
            <!--SVG Minus Icon-->
            <svg xmlns="http://www.w3.org/2000/svg" 
                viewBox="0 0 24 24" stroke="var(--secondary-color)" fill="none" width="24" height="24">
                <path stroke-linecap="round" stroke-linejoin="round"
                    stroke-width="2"
                    d="M19 13H5v-2h14v2z"/>
            </svg>
        </button>
    </div>
</div>

<style>
    .container {
        width: 100vw;
        height: 100vh;

        padding: 0;
        margin: 0;
        overflow: scroll;
        overflow-x: scroll;

        color: var(--primary-color);
        transform: scale(var(--scale));
    }

    .workspace {
        --scale: 1;
        
        margin: 0;
        padding: 0;

        transform: scale(var(--scale));
        width: calc(100% / var(--scale));
        height: calc(100% / var(--scale));
        
        transition: all 0.5s;
    }

    .background {
        position: relative;
        height: 100%;
        width: 100%;

        display: flex;
        flex-wrap: wrap;
        gap: 1rem;
    }

    .zoomControls {
        position: fixed;
        bottom: 1rem;
        right: 1rem;
        display: flex;
        gap: 0.2rem;
    }

    button.icon {
        background: none;
        border: 1px solid var(--border-color);
        border-radius: 10px;
        padding: 0.5rem;
        cursor: pointer;
        transition: all 0.5s;
    }
    button.plus {
        border-radius: 15px 5px 5px 15px
    }
    button.minus {
        border-radius: 5px 15px 15px 5px
    }

    button.icon:hover {
        background: var(--elevated-color);
        box-shadow: 0 0 20px var(--border-color);
    }
    svg {
        transition: all 0.5s;
    }
    button.icon:hover svg {
        stroke: var(--primary-color);
    }
</style>