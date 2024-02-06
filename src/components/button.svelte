<script>
    export let text = "Button";
    export let color = "black"; // This will be the color of the button text
    export let backgroundColor = "blue"; // This will be the color of the button background
    export let border = "black";
    export let boxShadow = "none";
    export let width = "20%";
    export let height = "53px";
</script>

<style>
    .button {
        width: var(--width);
        height: 53px !important;
        background-color: var(--backgroundColor);
        color: var(--color);
        border: 2px solid var(--border);
        border-radius: 10px;
        font-size: 1.2em;
        font-weight: 750;
        cursor: pointer;
        transition: all 0.3s ease;
        box-shadow: var(--boxShadow);
    }
    .button:hover {
        opacity: 0.8;
    }

    /* Responsive styles for 1024px and less */
    @media (max-width: 1024px) {
        .button {
            height: 140%;
            width: 18%;
        }
    }

    /* Responsive styles for 768px and less */
    @media (max-width: 768px) {
        .button {
            font-size: 1.1em;
            height: 20%;
            width: 20%;
        }
    }
    /* Responsive styles for 600px and less */
    @media (max-width: 600px) {
        .button {
            font-size: 1em;
            width: 23%;
        }
    }
    /* Responsive styles for 480px and less */
    @media (max-width: 480px) {
        .button {
            margin-top: 3%;
            width: 100px;
            height: 40px;
            font-size: 1em;
        }
    }

    /* Responsive styles for 320px and less */
    @media (max-width: 320px) {
        .button {
            margin-top: 1%;
            width: 40%;
            font-size: 1em;
        }
    }
</style>

<!-- Button component with on:click Event to be customized -->
<button class="button" style="--color: {color}; --backgroundColor: {backgroundColor}; --border: {border}; --boxShadow: {boxShadow}; --width: {width}; --height: {height};" on:click>{text}</button>
