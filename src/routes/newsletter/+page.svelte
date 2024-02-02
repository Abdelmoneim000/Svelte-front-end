<script>
    import Input from "../../components/Input.svelte";
    import Button from "../../components/button.svelte";

    // Email validator
    let email = '';
    let message = 'hello world!';
    let validated = true;

    const validateEmail = () => {
        
        const re = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
        if (!re.test(email)) {
            message = 'Email is incorrect';
        } else {
            message = '';

            // Send the email to the backend
            if (!validated) {
                message = 'There was an error submitting your email. Please try again.';
            } else {
                message = 'Email submitted successfully!';
            }
        }
    };
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
        font-weight: 600;
        font-size: 20px;
    }

    .txt {
        width: 60%;
    }

    .submit-form {
        display: flex;
        flex-direction: row;
        justify-content: left;
        align-items: center;
        width: 70%;
        height: 5%;
        margin-top: 50px;
        margin-left: 10%;
        gap: 50px;
    }

    .message {
        color: green;
        margin-top: 10%;
    }

    /* Responsive styles */
    @media (max-width: 1024px) {
        .container h1 {
            font-size: 50px;
        }

        .container p {
            font-size: 20px;
        }

        .txt {
            width: 70%;
        }

        .submit-form {
            width: 75%;
            height: 5%;
            margin-left: 3%;
        }
    }

    @media (max-width: 769px) {
        .container h1 {
            font-size: 40px;
        }

        .container p {
            font-size: 18px;
        }

        .txt {
            width: 80%;
            margin-bottom: 0%;
        }

        .submit-form {
            margin-top: 3%;
            flex-direction: column;
            justify-content: left;
            width: 80%;
            height: 30%;
            gap: 30px;
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

    @media (max-width: 320px) {
        .container h1 {
            font-size: 25px;
        }

        .container p {
            font-size: 14px;
        }

        .txt {
            width: 90%;
        }

        .submit-form {
            width: 100%;
            margin-left: 0;
        }
    }
</style>
  
<div class="container">
    <div class="txt">
        <h1>PolyLabs is coming.</h1>
        <p>Wanna be the first to know when the next generation of learning programming releases?</p>
    </div>
    <div class="submit-form">
        <Input bind:value={email} label="Email" labelFontSize="1em" width="60%" />
        <Button text="Submit" backgroundColor="#FFE37F" width="110px" height="50px" on:click={validateEmail} />
    </div>
    <p class="message">{message}</p>
</div>