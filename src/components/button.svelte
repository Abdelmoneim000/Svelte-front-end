<script>
    export let text = "Button";
    export let color = "blue";
    export let border = "black";
    export let boxShadow = "none";
</script>

<style>
    .button {
        padding: 10px 20px;
        background-color: var(--color);
        color: black;
        border: 2px solid var(--border);
        border-radius: 10px;
        font-size: 1em;
        font-weight: bold;
        cursor: pointer;
        transition: all 0.3s ease;
        box-shadow: var(--boxShadow);
    }

    .button:hover {
        opacity: 0.8;
    }

    @media (max-width: 600px) {
        .button {
            font-size: 0.8em;
        }
    }
</style>

<button class="button" style="--color: {color}; --border: {border}; --boxShadow: {boxShadow};">{text}</button>