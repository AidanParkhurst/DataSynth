<div class="hero">
    <h1 class="title">
        Model Neural Networks
    </h1>
    <h2 class="subtitle">
        Visually, intuitively, and faster than ever before.
    </h2>
</div>
<div class="stat">
    <div class="card">
        <div class="contents">
            <h2>Conceptualize Machine Learning </h2>
            <h1>Get the Big Picture</h1>
        </div>
    </div>
</div>
<div class="full stat">
    <h2>Locally or in the Cloud<h2>
    <h1>Own Your Code. Test Your Results.</h1>
</div>
<div class="stat">
    <div class="card left">
        <div class="contents left">
            <h2>Custom networks in minutes</h2>
            <h1>Build Models Fast</h1>
        </div>
    </div>
</div>
<div class="full stat">
    <h2>Knowledge to the people<h2>
    <h1>Artificial Intelligence, Democratized.</h1>
</div>
<style>
    .hero {
        width: 100vw;
        height: 100vh;
        margin-bottom: 10vh;

        display: flex;
        flex-direction: column;
        align-items: center;
        background-size: 100% 100%, 32vh 32vh;
        background-position: center, center;

        opacity: 0;
        animation: appear 1s forwards, expand 1s forwards;
    }
    @keyframes expand {
        0% {
            background-size: 100% 100%, 1vh 1vh;
        }
        100% {
            background-size: 100% 100%, 4vh 4vh;
        }
    }
    .title {
        margin-top: 38vh;
        margin-bottom: 0;
        font-size: 5rem;
        font-weight: 500;
        /* soft gradient */
        color: transparent;
        background: linear-gradient(180deg, var(--primary-color) 0%, var(--secondary-color) 80%);
        background-clip: text;
        
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;

        animation: appear 1s ease forwards;
        
    }
    .subtitle {
        color: var(--secondary-color);
        margin-top: 2rem;
        margin-bottom: 0;
        font-size: 1.5rem;
        font-weight: 400;

        opacity: 0;
        animation: appear ease forwards;
        animation-duration: 1s;
        animation-delay: 1s;
    }
    .stat {
        display: flex;
        justify-content: space-between;
        width: 90vw;
        height: 100vh;
        padding: 0 5vw;
        margin-bottom: 10vh;
    }
    .stat.full {
        justify-content: center;
    }
    .contents {
        padding: 10vh 10vw;
        height: 80vh;
        width: 70vw;
        padding: 25px 50px;
        display: flex;
        flex-direction: column;
        border-radius: inherit;
        background-image: radial-gradient(circle, var(--background-color) 10%, var(--elevated-color) 80%);
        background-size: 200%;
        background-position: 100%;

    }
    .contents.left {
        background-position: 0%;
        text-align: right;
    }
    .card {
        z-index: 2;
        margin: 0 auto;
        border-radius: 10px;
        background: linear-gradient(270deg, var(--border-color), var(--elevated-color));
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
    h1 {
        margin-top: 1vh;
        font-size: 4rem;
        color: var(--primary-color);
        font-weight: 500;
    }
    .card.left {
        background: linear-gradient(90deg, var(--border-color), var(--elevated-color)); 
    }
    
    @keyframes appear {
        0% {
            opacity: 0;
        }
        100% {
            opacity: 1;
        }
    }
    @keyframes ripple {
        0% {
            text-shadow: 0 0 0px var(--secondary-color);
        }
        100% {
            text-shadow: 0 0 40px var(--secondary-color);
        }
    }
</style>