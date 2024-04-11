<title>ModelSynth Webapp</title>
<body>
    <div class="toolbar"></div>
    <slot></slot>
</body>

<style>
    body {
        position:absolute;
        width: 100%;
        height: 100%;
        margin: 0;
        top: 0;
        left: 0;
        background-color: var(--background-color);
        font-family: 'greycliff-cf', sans-serif;
        color: var(--secondary-color);
    }

    .toolbar {
        position: fixed;
        top: 0;
        left: 0;
        width: 10vw;
        height: 100%;
        background-color: var(--elevated-color);
        z-index: 100;
    }
</style>