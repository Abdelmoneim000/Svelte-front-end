<!-- Logo page for coming soon page -->
<script>
    import logo from '../../assets/logo.svg';
</script>

<style>
    :global(body) {
        margin : 0;
    }
    .full-page {
        font-family: Rubik;
        color: white;
        background-color: #FFE37F;
        width: 100%;
        height: 100vh;
        overflow: hidden;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    h1 {
        -webkit-text-stroke: 1.5px black;
        -webkit-text-fill-color: white;
        font-size: 5rem;
        font-weight: 900px;
        text-shadow: 5px 3px 0px #00000040;
    }

    h2 {
        -webkit-text-stroke: 0.8px black;
        font-size: 2rem;
        text-shadow: 3px 3px 0px #00000040;
    }

    img {
        width: 30%;
        height: 30%;
    }

    .two-words-row {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
        gap: 30px;
    }

    .colored {
        text-align: center;
        border-radius: 10px;
        background-color: black;
        width: auto; /* Adjust the width to fit the content */
        height: 35px; /* Adjust the height to fit the content */
        padding: 10px; /* Add some padding to resemble a button */
    }

    .colored h2 {
        margin: 0;
    }

    /* Responsive styles for 1024px and less */
    @media (max-width: 1024px) {
        img {
            width: 45%;
            height: 45%;
        }

        h1 {
            margin: -10px 0 0 0;
            font-size: 3rem;
        }
    }

    @media (max-width: 720) {
        h1 {

            margin: 0 0 0 0;
        }
    }

    @media (max-width: 320px) {

        h1 {
            font-size: 2.5rem;
        }
    }


</style>

<div class="full-page">
    <img src={logo} alt="PolyLabs logo">
    <h1>PolyLabs AI</h1>
    <h2>Learn Coding Better</h2>
    <br/>
    <div class="two-words-row">
        <h2 style="color: #9EFF62">Coming</h2>       
        <div class="colored">
            <h2 style="color: #9EFF62">2024</h2>
        </div>
    </div>
</div>