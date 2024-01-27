<script>
    import Input from "../../components/Input.svelte";
    import Button from "../../components/button.svelte";
</script>

<style>
    .container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        font-family: Inter;
        width: 100%;
        height: 100vh;
    }

    .container h1 {
        font-weight: 900px;
        font-size: 55px;
    }

    .container p {
        font-style: normal;
        font-weight: 600px;
        font-size: 20px;
    }

    .txt {
        width: 60%;
    }

    .submit-form {
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        width: 70%;
        height: 6%;
        margin-top: 50px;
        margin-left: 10%;
    }

    /* Responsive styles */
    @media (max-width: 768px) {
        .container h1 {
            font-size: 40px;
        }

        .container p {
            font-size: 18px;
        }

        .txt {
            width: 80%;
            margin-bottom: 10%;
        }

        .submit-form {
            flex-direction: column;
            width: 80%;
            margin-left: 0;
        }
    }

    @media (max-width: 480px) {
        .container h1 {
            font-size: 30px;
        }

        .submit-form{
            display: flex;
            flex-direction: column;
        }

        .container p {
            font-size: 16px;
        }

        .txt {
            width: 90%;
        }

        .submit-form {
            width: 90%;
        }
    }
</style>
  
<div class="container">
    <div class="txt">
        <h1>PolyLabs is coming.</h1>
        <p>Wanna be the first to know when the next generation of learning programming releases?</p>
    </div>
    <div class="submit-form">
        <Input label="Email" labelFontSize="1.2em"/>
        <Button text="Submit" backgroundColor="#FFE37F" width="15%" height="100%" />
    </div>
</div>