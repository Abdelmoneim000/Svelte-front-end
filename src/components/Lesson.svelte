<!-- Lesson component to show a short describtion -->
<script>
    import Button from "./button.svelte";
  export let title = "";
  export let description = "";
  export let showButton = false;
  export let buttonText = "Begin";
</script>

<style>
    .lesson {
        width: 55%;
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        border: 3px solid #000000;
        border-radius: 10px;
        padding: 30px;
    }

    .Typo {
        display: flex;
        flex-direction: column;
        justify-content: center;
        width: 80%;
    }

    .Typo h1 {
        margin: 0;
    }

    .Typo p {
        font-size: 24px;
        width: 80%;
        font-weight: 500;
    }

</style>


<div class="lesson">
    <div class="Typo" style={showButton ? "" : "margin-right: 120px;"}>
        <h1>{title}</h1>
        <p>{description}</p>
    </div>
    {#if showButton}
        <Button
        text={buttonText}
        backgroundColor="#FFE37F"
        width="120px"
        height="60px"
        border="1.2px solid black"
        fontSize="27px"
        />
    {/if}
</div>