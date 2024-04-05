<div class="hero">
    <h1 class="title">
       Data Synth
    </h1>
    <h2 class="subtitle">
        Precisely formatted, compliant data on demand.
    </h2>
</div>
<div class="stat">
    <div class="info">
        <h1 class="title"> Differentially Private </h1>
        <h2 class="subtitle">
            Create anonymous, synthetic data in compliance with privacy regulations.
        </h2>
    </div>
    <div class="card">
        <div class="contents">
        </div>
    </div>
</div>
<div class="stat">
    <div class="card">
        <div class="contents left">
        </div>
    </div>
    <div class="info" style="text-align: right;">
        <h1 class="title"> Completely Custom</h1>
        <h2 class="subtitle">
            Use a flexible, powerful data suite to design, format, and label new data.
        </h2>
    </div>
</div>
<div class="stat">
    <div class="info">
        <h1 class="title"> GAN Powered </h1>
        <h2 class="subtitle">
            Leverage state of the art AI to expand existing datasets in minutes. 
        </h2>
    </div>
    <div class="card">
        <div class="contents">
        </div>
    </div>
</div>

<style>
    .hero {
        width: 100vw;
        height: 100vh;
        margin-bottom: 10vh;

        display: flex;
        flex-direction: column;
        align-items: center;
        background-image: radial-gradient(var(--background-color) 15%, transparent 50%, var(--background-color) 75%),
            radial-gradient(var(--border-color) 0%, var(--elevated-color) 20%, var(--background-color) 40%);
        background-size: 100% 100%, 4vh 4vh;
    }
    .title {
        margin-top: 38vh;
        margin-bottom: 0;
        font-size: 5rem;
        font-weight: 500;
        /* soft gradient */
        color: transparent;
        background: linear-gradient(180deg, var(--primary-color) 0%, var(--secondary-color) 50%);
        background-clip: text;
        
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;

        /* soft glow */
        text-shadow: none;
        animation: startGlowing 3s forwards;
    }
    @keyframes startGlowing {
        15% {
            text-shadow: 0 0 5px var(--secondary-color);
        }
        100% {
            text-shadow: 0 0 50px var(--secondary-color);
        }
    }
    .subtitle {
        color: var(--secondary-color);
        margin-top: 2rem;
        margin-bottom: 0;
        font-size: 1.5rem;
        font-weight: 400;
    }
    .stat {
        display: flex;
        justify-content: space-between;
        width: 90vw;
        padding: 0 5vw;
        margin-bottom: 15vh;
    }
    .contents {
        padding: 10vh 10vw;
        height: 80vh;
        width: 25vw;
        padding: 25px 50px;
        display: flex;
        flex-direction: column;
        justify-content: space-between; 
        border-radius: inherit;
        background-image: radial-gradient(circle, var(--background-color) 10%, var(--elevated-color) 80%);
        background-size: 200%;

    }
    .contents.left {
        background-position: -100%;
    }
    .card {
        z-index: 2;
        margin: 0 auto;
        border-radius: 10px;
        background: linear-gradient(180deg, var(--border-color), var(--elevated-color));
        display:flex;
        justify-content: center;
        align-items: center;
        width: fit-content;
        height: fit-content;

        padding: 1px;
        transition: all 0.3s;
    }
    .card:hover {
        transform: scale(1.05);
    }
</style>