<!-- Course card component to display for each course -->
<script>
  export let course = "";
  export let difficulty = "";
  export let description = "";
  let clicked = false;

    const handleClick = () => {
        clicked = !clicked;
    };
</script>


<style>
    .card {
        font-family: "Inter";
        width: 20%;
        height: 350px;
        border: 3px solid black;
        border-radius: 20px;
        padding: 30px;
        margin: 10px;
        cursor: pointer;
    }
    .title {
        display: flex;
        justify-content: space-between;
        padding-left: 10px;
        padding-right: 10px;
    }

    .title div {
        display: flex;
        align-items: center;
        justify-content: center;
        width: calc(100% - 150px);
        height: 40px;
        margin-top: 10px;
        background-color: #EBEBF0;
        border-radius: 16px;
    }

    .title  h3 {
        font-size: 25px;
    }
    .description {
        margin-top: 10px;
        color: #52525C;
    }

    .description p {
        font-size: 32px;
        line-height: 40px;
    }
</style>


<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div class="card" style="background-color: {clicked ? '#ECECEC' : 'var(--background-color)'};" on:click={handleClick} on:click>
    <div class="title">
        <div style="border: {clicked ? '2px solid black' : 'none'};">
            <h3>{course}</h3>
        </div>
        <h3 style="color: #449108; margin-top: 10px;">{difficulty}</h3>
    </div>
    <div class="description">
        <p>{description}</p>
    </div>
</div>