<script>
    import { createEventDispatcher } from "svelte";
    let dispatch = createEventDispatcher();

    export let menu = {
        x: 0,
        y: 0,
        visible: false
    };
    $: menuStyle = `
        top:${menu.y}px;
        left:${menu.x}px;
        height: ${menu.visible ? "30vh":"0"};
        opacity: ${menu.visible ? "1":"0"};
        pointer-events:${menu.visible ? "auto":"none"};`;

    let addNode = () => {
        dispatch('add', menu);
        hideMenu();
    };

    let hideMenu = () => {
        menu.visible = false;
    };
</script>

<div class="actions" style={menuStyle}
    on:mouseleave={hideMenu} role="menu" tabindex="0">
    <button on:click={addNode}>Data Source</button>
    <button on:click={addNode}>Dense Layer</button>
    <button on:click={addNode}>Recurrent Layer</button>
    <button on:click={addNode}>Convolutional Layer</button>
</div>

<style>
    .actions {
        position: absolute;
        top: 0;
        left: 0;
        width: 10vw;

        display: flex;
        flex-direction: column;
        align-items: center;

        background: radial-gradient(circle, var(--elevated-color) 0%, transparent 100%);
        backdrop-filter: blur(10px);
        border-radius: 10px;
        border: 1px solid var(--border-color);

        opacity: 1;
        height: 0;
        transition: height 0.2s, opacity 0.2s;
    }

    .actions button {
        background: none;
        border: none;
        color: var(--secondary-color);
        width: 100%;
        height: 20%;
        padding: 5px 10px;
        border-radius: 10px;
        transition: all 0.5s;
        border: 1px solid transparent;
    }
    .actions button:hover {
        border: 1px solid var(--border-color);
        color: var(--primary-color);
    }
</style>