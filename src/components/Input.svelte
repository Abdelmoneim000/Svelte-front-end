<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

    export let label = "Label";
    export let labelColor = "#9d9d9d";
    export let labelFontSize = "1.6em";
    export let width = "60%";
    export let height = "50px";
    export let value = "";

    function handleChange(event) {
        value = event.target.value;
        dispatch('input', value);
    }
</script>

<style>
    .container {
        width: var(--width);
    }

    .entryarea {
        width: 100%;
        position: relative;
        height: var(--height);
        line-height: var(--height);
    }

    input {
        position: absolute;
        width: 90%;
        height: 100%;
        outline: none;
        font-size: 1.5em;
        padding: 0 30px;
        line-height: var(--height);
        border-radius: 10px;
        border: 2px solid black;
        background-color: transparent;
        transition: 0.1 ease;
        z-index: 1111;
    }

    .labelline {
        position: absolute;
        font-size: var(--labelFontSize);
        color: var(--labelColor);
        padding: 0 10px;
        margin: 0px 20px;
        transition: 0.2s ease;
    }

    input:focus, input:valid {
        border: 4px solid black;
    }

    input:focus + .labelline, input:valid + .labelline {
        height: 30px;
        line-height: 30px;
        padding: 0 12px;
        background-color: white;
        transform: translate(-15px, -15px) scale(0.8);
        font-size: 1.2em;
        color: black;
        z-index: 1111;
    }

    /* Responsive styles for 1024px and less */
    @media (max-width: 1024px) {
        .container {
            height: fit-content;
        }
        input {
            width: 100%;
            font-size: 1.8em;
            height: 47px;
        }

        .labelline {
            font-size: 1.4em;
        }
    }

    /* Responsive styles */
    @media (max-width: 768px) {
        input {
            width: 100%;
            font-size: 1.8em;
        }

        .labelline {
            font-size: 1.4em;
        }
    }

    @media (max-width: 480px) {
        input {
            width: 105%;
            font-size: 1.4em;
        }

        .labelline {
            font-size: 1.2em;
        }
    }

    @media (max-width: 320px) {
        input {
            width: 150px;
            font-size: 1em;
            font-weight: 600;
        }

        .labelline {
            font-size: 1em;
        }
    }
</style>

<div class="container" style="--width: {width}; --height: {height}; --labelFontSize: {labelFontSize}; --labelColor: {labelColor};">
    <div class="entryarea">
        <input type="text" required id="email" autocomplete="email" bind:value={value} on:input={handleChange}>
        <div class="labelline">{label}</div>
    </div>
</div>