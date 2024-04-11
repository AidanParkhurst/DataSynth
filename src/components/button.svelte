<script>
    export let buttonText = "Default Text";
    export let href = "/";
    export let type = "button"; 
</script>

<a href={href} type={type}>
    <slot>{buttonText}</slot>
</a>
<style>
    a {
        transition: 1s all;
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
    a:after {
        content: "";
        position:absolute;
        top: 0;
        left: 0;
        width: 80%;
        height: 1px;
        background: radial-gradient(circle, var(--secondary-color) 0%, transparent 100%);    
    }
    a:hover {
        color: var(--background-color);
        background: var(--secondary-color);
        /* slight glow */
        box-shadow: 0 0 15px var(--border-color);
    }
    a:active {
        background: var(--primary-color);
    }
</style>