<script>
    import Input from "../../components/Input.svelte";
    import Button from "../../components/button.svelte";

    // NOTE!!!: This is a dummy email submission form. It does not submit the email to the backend.
    // email variable is updated using two-way binding inside the Input component.
    let email = '';
    let message = '';
    let validated = true;
    /**
     * Validate the email input field.
     * @returns {void}
     */
    const validateEmail = () => {
        
        const re = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
        if (!re.test(email)) {
            message = 'Invalid email address. Please try again.';
            validated = false;
        } else {
            message = '';
            validated = true;

            // Send the email to the backend
            if (!validated) {
                message = 'There was an error submitting your email. Please try again.';
            } else {
                message = 'You\'re on the list. We\'ll Email you soon.';
            }
        }
    };

</script>

<style>

    body {
        overflow-x: hidden !important;
        overflow-y: hidden !important;

    }
    .container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        font-family: Inter;
        width: 100%;
        height: 100vh;
        transform: scale(1.5);


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
        width: 60%;
        margin-top: 5%;
        display: flex;
        gap: 20px;
        justify-content: left;
        text-align: center;
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
            justify-content: space-around;
        }

        .message p {
            padding-top: 1%;
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

        .message p {
            padding-top: 2%;
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
/* Hide the message by default */
#unsupported-message {
    display: none;
}

/* Show the message on screens smaller than 768px */
@media screen and (max-width: 1000px) {
    #unsupported-message {
        display: block;
    }

    /* Hide other elements of the newsletter */
    /* Replace .newsletter with the actual class or id of your newsletter container */
    .container {
        display: none;
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
<body>
<div class="container">
    <div class="txt" id="unsupported-message">
        <p>Sorry, this newsletter is not supported on mobile or tablet devices.</p>
    </div>
    <div class="txt">
        <h1>PolyLabs is coming.</h1>
        <p>Wanna be the first to know when the next generation of learning programming releases?</p>
    </div>
    <div class="submit-form">
        <Input bind:value={email} label="Email" labelFontSize="1em" width="60%" />
        <Button text="Submit" backgroundColor="#FFE37F" width="110px" height="50px" on:click={validateEmail} />
    </div>
    <div class="message" >
        {#if validated && message === 'You\'re on the list. We\'ll Email you soon.'}

        <div style="width: 10px; height: 60px; background-color: #039700; border-radius: 20px; "></div>
        <p style="margin-top: 2%; color : #039700;">{message}</p>
   
        
        {:else if !validated && message === 'Invalid email address. Please try again.'}
       
        <div style="width: 10px; height: 60px; background-color: #F00000; border-radius: 20px"></div>
        <p style="margin-top: 2%; color : #F00000;">{message}</p>
        {/if}
    </div>
</div>
</body>