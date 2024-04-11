<div class="container">
    <div class="blurb">
        <h1>Nice to meet you!</h1>
        <h2>We're ModelSynth,</h2>
    </div>
    <div class="contact">
        <form>
            <label for="name">What's your name?</label>
            <input type="text" id="name" name="name" required>
            <label for="email">Email?</label>
            <input type="email" id="email" name="email" required>
            <label for="message">Do you have a message?</label>
            <textarea id="message" name="message" required></textarea>
            <button type="submit">Send</button>
        </form>
    </div>
</div>

<style>
    * {
        transition: all 0.5s;
    }
    *:focus {
        outline: none;
        box-shadow: 0 0 10px var(--secondary-color);
    }
    .container {
        display: flex;
        padding: 10vh 10vw;
        justify-content: center;
        align-items: center;
        height: fit-content;
        gap: 5vw;
        color: var(--primary-color);
    }
    h1 {
        font-size: 4rem;
        margin-right: 5vw;
        font-weight: 500;
    }
    h2 {
        color: var(--secondary-color);
        font-size: 2rem;
        font-weight: 100;
    }
    .contact {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 50%;
    }

    form {
        display: flex;
        flex-direction: column;
        width: 100%;
    }

    label {
        margin-top: 5vh;
        font-size: 2rem;
    }

    input, textarea {
        margin-top: 0.5rem;
        padding: 0.5rem;
        font-size: 1.5rem;
        color: var(--primary-color);
        border: 1px solid var(--border-color);
        border-radius: 10px;
        background-color: var(--elevated-color);
    }

    button {
        display: flex;
        justify-content: center;
        align-items: center;
        
        text-decoration: none;
        background-color: transparent;
        font-size: 2rem;
        font-weight: 100;
        color: var(--secondary-color);
        margin-top: 5vh;
        padding: 10px 20px;
        border-radius: 10px;
        border: 1px solid var(--border-color);
    }
    button:hover {
        background: var(--border-color);
        box-shadow: 0 0 10px var(--border-color);
    }
    button:active {
        color: var(--background-color);
        background: var(--secondary-color);
    }

</style>