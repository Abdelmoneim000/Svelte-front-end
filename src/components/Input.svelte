<!-- Static svelte Input component -->
<style>
    /**
    * TODO: make it dynamic input component
    * Add the following features:
    * 1. Add media quary for moblies.
    * 2. Add the ability to change the input type.
    * 3. Add the ability to change the input placeholder.
    * 4. Add the ability to change the input label.
    * 5. Add the ability to change the input label color.
    * 6. Add the ability to change the input label font size.
    * 7. Add the ability to the width and height.
    */
    .container {
        width: 720px;
    }

    .entryarea {
        position: relative;
        height: 80px;
        line-height: 80px;
    }

    input {
        position: absolute;
        width: 100%;
        outline: none;
        font-size: 2.2em;
        padding: 0 30px;
        line-height: 80px;
        border-radius: 10px;
        border: 2px solid black;
        background-color: transparent;
        transition: 0.1 ease;
        z-index: 1111;
    }

    .labelline {
        position: absolute;
        font-size: 1.6em;
        color: #545454;
        padding: 0 25px;
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
</style>

<div class="container">
    <div class="entryarea">
        <input type="text" required>
        <div class="labelline">Enter your E-mail</div>
    </div>
</div>