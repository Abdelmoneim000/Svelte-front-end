<!-- Home page -->
<script>
  import Button from "../components/button.svelte";

    let selected = "Home"; // Default selected nav item works as a state.
    const navText = ["Home", "Sign In", "Sign Up"];

    const selectItem = (item) => {
        selected = item;
    };
</script>

<style>
    :global(body) {
        background-color: #F7F7F7;
        font-family: Inter;
    }
    .HomeBody {
        width: 100%;
        height: fit-content;
        font-family: Inter;
    }
    .Menu {
        margin-top: 5%;
        display: flex;
        justify-content: center;
        gap: 3px;
    }

    .Menu div {
        background-color: white;
        width: 9%;
        height: 40px;
        font-weight: 700;
        font-size: 15px;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
    }

    .Menu div:first-child {
        border-top-left-radius: 5px;
        border-bottom-left-radius: 5px;
    }

    .Menu div:last-child {
        border-bottom-right-radius: 5px;
        border-top-right-radius: 5px;
    }

    .Menu div.selected {
        background-color: #f0f0f0; /* Change to the desired color */
    }

    .Intro {
        text-align: center;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin-top: 3%;
    }

    @media (max-width: 320px) {
        .Menu div {
            width: 32%;
        }
    }

</style>

<!--Elements and sections go here-->

<!--Navigation bar-->
<div class="HomeBody">
    <nav class="Menu">
        {#each navText as text (text)}
            <div class:selected={selected === text} on:click={() => selectItem(text)}>{text}</div>
        {/each}
    </nav>
</div>

<!-- Main Header -->

<header class="Intro" style="">
    <h1 style="font-size: 55px;">Learn Coding Fast.</h1>
    <p style="font-weight: 600; font-size: 20px; margin-bottom: 3%">PolyLabs is a platform to quickly and efficiently learn programming.</p>
    <Button 
        width="8%"
        height="10%"
        text="Learn more"
        backgroundColor="#FFE37F"
        boxShadow="5px 3px 1px #000000"
    />
</header>