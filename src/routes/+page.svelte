<!-- Home page -->
<script>
// Imports and modules go here...
    const navText = ["Home", "Sign In", "Sing Up"];
</script>

<style>
    .HomeBody {
        width: 100%;
        height: fit-content;
        font-family: Inter;
        background-color: #ffff;
    }
    .Menu {
        margin-top: 5%;
        display: flex;
        justify-content: center;
        gap: 1px;
    }

    .Menu div {
        background-color: antiquewhite;
        width: 9%;
        height: 40px;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
    }

    .Menu > div {
        border-radius: 5px;
    }

</style>

<!--Elements and sections go here-->

<div class="HomeBody">
    <nav class="Menu">
        <div><span>Home</span></div>
        <div>Sign In</div>
        <div>Sign Up</div>
    </nav>
</div>