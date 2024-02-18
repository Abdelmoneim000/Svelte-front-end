<!-- SignIn page when user choose to login using Email -->
<script>
    import Input from "../../components/Input.svelte";
    import InputPass from "../../components/InputPass.svelte";
    import Button from "../../components/button.svelte";

    let email = "";
    let password = "";
    let validated = false;
    let message = "";


    const validateEmail = () => {
        
        const re = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
        if (!re.test(email)) {
            message = 'Invalid email address. Please try again.';
            validated = false;
        } else {
            validated = true;
        }
    };

        // Check password for 8 characters, 1 letter, and 1 number.
        const validatePassword = () => {
        const re = /^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d]{8,}$/;
        if (!re.test(password)) {
            passwordSubmitted = false;
        } else {
            passwordSubmitted = true;
        }
    };
</script>

<style>
.submit-form {
    margin-top: 13%;
    margin-left: 15%;
    display: flex;
    flex-direction: column;
    gap: 5px;
    font-family: Inter;
    animation: fadeIn 1s ease-in-out forwards;
}

@keyframes fadeIn {
        0% {
            opacity: 0;
            transform: translateY(20px);
        }
        100% {
            opacity: 1;
            transform: translateY(0);
        }
    }
</style>


<!-- Passowrd Input should only be displayed when the User enter a correct and existing Email -->

<div class="submit-form">
    <!-- Email submission should be visible first -->
    {#if !email || !validated}
        <h1 style="font-weight: 900; font-size: 72px;">What's your Email?</h1>
        <Input bind:value={email} label="Email" labelFontSize="2.3em" width="80%" height="90px" fontSize="2em" />
        <div style="margin-top: 50px;">
            <Button text="Next" backgroundColor="#FFE37F" width="130px" height="70px" border="1px solid black" fontSize="1.6em" on:click={validateEmail} />
        </div>
        {#if message !== ""}
        <div style="display: flex; flex-direction:row; gap: 30px; margin-top: 3%">
          <div style="width: 10px; height: 60px; background-color: #F00000; border-radius: 20px"></div>
          <p style="margin-top: 1.5%; color : #F00000;">{message}</p>
          </div>
        {/if}
    {/if}
    <!-- After Email submission, User must submit passowrd too -->
    {#if email && validated}
        <h1 style="font-weight: 900; font-size: 72px;">What's your Password?</h1>
        <InputPass bind:value={password} label="Password" labelFontSize="2.3em" width="80%" height="90px" fontSize="3em" on:click={validatePassword} />
        <div style="margin-top: 50px;">
            <!-- TODO: back-end should link a submit event to the button and send the data of both email and password to the back-end -->
            <Button text="Login" backgroundColor="#FFE37F" width="130px" height="70px" border="1px solid black" fontSize="1.6em" />
        </div>
    {/if}
</div>