<!-- This is a button that takes 4 arguments -->

<script>
    export let text = "Button";
    export let color = "blue";
    export let border = "black";
    export let boxShadow = "none";
</script>

<!-- button class that takes the argument and implement it in the design-->
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
    /**
    * Hover effect when the mouse is over the button
    */
    .button:hover {
        opacity: 0.8;
    }
    /**
    * Media query for mobile devices
    */
    @media (max-width: 600px) {
        .button {
            font-size: 0.8em;
        }
    }
</style>

<!-- Define the Button element with its arguments-->
<button class="button" style="--color: {color}; --border: {border}; --boxShadow: {boxShadow};">{text}</button>