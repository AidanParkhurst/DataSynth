<script>
    import { writable } from 'svelte/store';

    let mouse = writable({ x: 0, y: 0 });

    function mouseMove(e) {
        const rect = e.currentTarget.getBoundingClientRect()
        mouse.set({ x: e.clientX - rect.x, y: e.clientY - rect.y });
        e.currentTarget.style.setProperty('--x', `calc(${$mouse.x}px - 50vw)`);
        e.currentTarget.style.setProperty('--y', `calc(${$mouse.y}px - 10vh)`);
    }
</script>

<title>ModelSynth</title>
<body>
    <div on:mousemove={mouseMove} class="header" role="presentation">
        <div class="logo">
            <h2>Logo</h2>
        </div>
        <div class="links">
            <a href="/">About</a>
            <a href="/demo">Demo</a>
            <a href="/team">Team</a>
            <a href="/contact">Contact</a>
        </div>
        <div class="login">
            <a href="/model">Start Modeling</a>
        </div>
    </div>
    <slot></slot>
    <div class="footer">
        <div class="logo">
            <h2>Logo</h2>
        </div>
        <div class="rights">
            <h3>DataSynth© 2024 All rights reserved</h3>
        </div>
        <div class="links">
            <a href="/">About</a>
            <a href="/demo">Demo</a>
            <a href="/team">Team</a>
            <a href="/contact">Contact</a>
        </div>
    </div>
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
        overflow-x: hidden;
    }

    .header {
        position: absolute;
        top: 0;
        left: 0;
        z-index: 2;
        
        width: 80vw;
        height: calc(10vh + 1px);
        padding: 0 10vw;

        display: flex;
        justify-content: space-between;
        align-items: center;
        overflow: hidden;

        --x: 0;
        --y: 0;
    }
    /* Soft glow which follows the mouse */
    .header:before {
        content: "";
        position:absolute;
        transition: opacity 0.5s; 

        top:0;
        left:0;
        height: 200%;
        width: 100%;
        opacity: 0;
        
        background: radial-gradient(circle, var(--border-color) 0%, transparent 10%);
        background-position-x: var(--x);
        background-position-y: var(--y);
        background-repeat: no-repeat;
        
        pointer-events: none;
        touch-action: none;
    }   
    .header:hover:before {
        opacity: 30%;
    }
    /* Gradient border at bottom */
    .header:after {
        position:absolute;
        top: 10vh;
        left: 0;
        content: "";
        width: 100%;
        height: 1px;
        background: radial-gradient(circle, var(--border-color) 0%, transparent 100%);
    }
    a {
        transition: all 0.5s;
    }
    .links {
        display: flex;
        justify-content: space-between;
        width: 50%;
    }
    .links a {
        text-decoration: none;
        color: var(--secondary-color);
        padding: 5px 10px;
    }
    .links a:hover {
        color: var(--primary-color);
    }

    .login a {
        position: relative;
        display: flex;
        justify-content: center;
        align-items: center;
        
        text-decoration: none;
        color: var(--secondary-color);
        padding: 10px 20px;
        border-radius: 10px;
        background-image: linear-gradient(180deg, var(--elevated-color) 0%, var(--background-color) 50%);
        border: 1px solid var(--border-color);
    }
    .login a:after {
        content: "";
        position:absolute;
        top: 0;
        left: 0;
        width: 80%;
        height: 1px;
        background: radial-gradient(circle, var(--secondary-color) 0%, transparent 100%);    
    }
    .login a:hover {
        color: var(--background-color);
        background: var(--secondary-color);
        /* slight glow */
        box-shadow: 0 0 15px var(--secondary-color);
    }
    .login a:active {
        background: var(--primary-color);
    }

    .footer {
        position: relative;
        width: 80vw;
        height: 20vh;
        z-index: 1;
        
        margin-top: 10vh;
        padding: 5vh 10vw;
        
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    .footer .links {
        display: flex;
        flex-direction: column;
        width: fit-content;
    }
    /* Outline border at top */
    .footer:before {
        content: "";
        position: absolute;
        top: -1px;
        left: 0;
        z-index: -2;

        width: 100%;
        height: 1px;
        margin: 0;
        background: radial-gradient(circle, var(--border-color) 0%, transparent 100%);
    }
</style>