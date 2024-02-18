<!-- SignIn page when user choose to login using Email -->
<script>
  import Input from "../../components/Input.svelte";
  import Button from "../../components/button.svelte";
  import InputPass from "../../components/InputPass.svelte";
  import { goto } from "$app/navigation";

  // All this data must be submitted to the back-end depends on the API requirements
  // Some of it can just stay in the front-end like "agreeToTerms" since the user will need it
  // only once in order to sign-up
  let email = "";
  let password = "";
  let ConfirmPassword = "";
  let passwordSubmitted = false;
  let validated = false;
  let submittedData = false;
  let message = "";
  let agreeToTerms = false;
  let BeginAccountSetup = false;
  let condingSkillSubmit = false;
  let Description = "";
  let CodingSkills = 0;
  let Greetings = false;
  let invalidEmail = false;
  let reason = "";
  let invalidPassword = false;

  const validateEmail = () => {
    const re = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
    if (!re.test(email)) {
      validated = false;
      invalidEmail = true;
    } else {
      validated = true;
      invalidEmail = false;
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

  // first password submission
  const submitPassword = () => {
    if (password.length >= 8){
      if(password.match(/[a-z]/i)){
        if(password.match(/\d/)){
          passwordSubmitted = true;
          invalidPassword = false;
        } else {
          invalidPassword = true;
          reason = "Password must contain at least 1 number"
        }
      } else {
        invalidPassword = true;
        reason = "Password must contain at least 1 letter"
      }

    } else {
      invalidPassword = true;
      reason = "Password must contain at least 8 charicters"
    }
  };
  // checking for
  const checkPassword = () => {
    console.log(password, ConfirmPassword);
    if (password === ConfirmPassword && ConfirmPassword !== "") {
        message = "";
      submittedData = true;
    }
    else {
        message = "Passwords do not match";
    }
  };

  $: if (Greetings) {
    setTimeout(() => goto("/"), 3000);
  }
</script>

<!-- Passowrd Input should only be displayed when the User enter a correct and existing Email -->
{#if !submittedData}
  <div class="submit-form">
    <!-- Email submission should be visible first -->
    {#if !email || !validated}
      <div style="animation: fadeIn 1s ease-in-out forwards;">
        <h1 style="font-weight: 900; font-size: 72px;">What's your Email?</h1>
        <Input
          bind:value={email}
          label="Email"
          labelFontSize="2.3em"
          width="80%"
          height="90px"
          fontSize="2em"
          on:blur={validateEmail}
        />
        <div style="margin-top: 50px;">
          <Button
            text="Next"
            backgroundColor="#FFE37F"
            width="130px"
            height="70px"
            border="1px solid black"
            fontSize="1.6em"
            on:click={validateEmail}
          />
          {#if invalidEmail == true}
          <div style="display: flex; flex-direction:row; gap: 30px; margin-top: 3%">
            <div style="width: 10px; height: 70px; background-color: #F00000; border-radius: 20px"></div>
            <h2 style="margin-top: 1.5%; color : #F00000; font-weight:400;">Invalid email format.</h2>
            </div>
          {/if}
        </div>
      </div>
    {/if}

    {#if email && validated && !passwordSubmitted}
      <!-- After Email submission, User must submit passowrd too -->
      <div style="animation: fadeIn 1s ease-in-out forwards;">
        <h1 style="font-weight: 900; font-size: 72px;">
          Set a secure password
        </h1>
        <p style="font-weight: 600; font-size: 32px; margin-top: -20px;">
          Choose a safe password that you'll remember
        </p>
        <InputPass
          bind:value={password}
          label="Password"
          labelFontSize="2.3em"
          width="80%"
          height="90px"
          fontSize="2em"
          on:blur={validatePassword}
        />
        <div style="margin-top: 50px;">
          <Button
            text="Proceed"
            backgroundColor="#FFE37F"
            width="140px"
            height="70px"
            border="1.2px solid black"
            fontSize="1.6em"
            on:click={submitPassword}
          />
          {#if invalidPassword == true}
          <div style="display: flex; flex-direction:row; gap: 30px; margin-top: 3%">
            <div style="width: 10px; height: 70px; background-color: #F00000; border-radius: 20px"></div>
            {#if invalidPassword == true}
              <h2 style="margin-top: 1.5%; color : #F00000; font-weight:400;">{reason}</h2>
            {/if}
            </div>
          {/if}
        </div>
      </div>

    {/if}

    {#if password && passwordSubmitted}
      <div style="animation: fadeIn 1s ease-in-out forwards;">
        <h1 style="font-weight: 900; font-size: 72px;">Repeat that password</h1>
        <p style="font-weight: 600; font-size: 32px; margin-top: -20px;">
          Repeat the same password from before
        </p>
        <InputPass
          bind:value={ConfirmPassword}
          label="Confirm Password"
          labelFontSize="2.3em"
          width="80%"
          height="90px"
          fontSize="2em"
        />
        <div style="margin-top: 50px; margin-bottom: 20px;">
          <Button
            text="Next"
            backgroundColor="#FFE37F"
            width="130px"
            height="70px"
            border="1.2px solid black"
            fontSize="1.6em"
            on:click={checkPassword}
          />
        </div>
        <Button
          text="I forgot it"
          backgroundColor="#FFABAB"
          width="150px"
          height="70px"
          border="1.2px solid black"
          fontSize="1.6em"
          on:click={() => {
            password = "";
            passwordSubmitted = false;
            ConfirmPassword = "";
          }}
        />
      </div>
      {#if message !== ""}
      <div style="display: flex; flex-direction:row; gap: 30px; margin-top: 3%">
        <div style="width: 10px; height: 70px; background-color: #F00000; border-radius: 20px"></div>
        <h2 style="margin-top: 1.5%; color : #F00000; font-weight:400;">Passwords do not match</h2>
        </div>
      {/if}
    {/if}
  </div>
{/if}
{#if submittedData && !agreeToTerms}
  <div class="legal_notice">
    <h1>Legal notices</h1>
    <p style="font-weight: 600;">
      By clicking “I agree”, you are agreeing to our <a
        style="color: #0067E0;"
        href="/Legal/Terms"
        target="_blank">terms of use</a
      >, and our <a style="color: #0067E0;"target="_blank" href="/Legal/Privacy">privacy policy</a>.
    </p>
    <Button
      text="I agree"
      backgroundColor="#FFE37F"
      width="130px"
      height="70px"
      border="1.2px solid black"
      fontSize="1.6em"
      on:click={() => {
        agreeToTerms = true;
      }}
    />
  </div>
{/if}

{#if agreeToTerms && !BeginAccountSetup}
  <div class="account-settings">
    <h1>Account Setup</h1>
    <p>
      This won’t take long and it helps us customize your learning experience.
    </p>
    <Button
      text="Begin"
      backgroundColor="#FFE37F"
      width="130px"
      height="70px"
      border="1.2px solid black"
      fontSize="1.6em"
      on:click={() => {
        agreeToTerms = true;
        BeginAccountSetup = true;
      }}
    />
  </div>
{/if}

{#if BeginAccountSetup && !condingSkillSubmit}
  <div class="Coding-Skills">
    <h1>Rate your coding skills.</h1>
    <div class="Flex-Numbers">
      <div style="display: flex; gap: 30px; width: 100%; margin-top: 2em">
        <Button
          text="1"
          backgroundColor={CodingSkills === 1 ? "#C4C4C4" : "#FFFFFF"}
          width="113px"
          height="113px"
          border="2px solid black"
          fontSize="4em"
          on:click={() => {
            CodingSkills = 1;
          }}
        />
        <Button
          text="2"
          backgroundColor={CodingSkills === 2 ? "#C4C4C4" : "#FFFFFF"}
          width="113px"
          height="113px"
          border="2px solid black"
          fontSize="4em"
          on:click={() => {
            CodingSkills = 2;
          }}
        />
        <Button
          text="3"
          backgroundColor={CodingSkills === 3 ? "#C4C4C4" : "#FFFFFF"}
          width="113px"
          height="113px"
          border="2px solid black"
          fontSize="4em"
          on:click={() => {
            CodingSkills = 3;
          }}
        />
        <Button
          text="4"
          backgroundColor={CodingSkills === 4 ? "#C4C4C4" : "#FFFFFF"}
          width="113px"
          height="113px"
          border="2px solid black"
          fontSize="4em"
          on:click={() => {
            CodingSkills = 4;
          }}
        />
        <Button
          text="5"
          backgroundColor={CodingSkills === 5 ? "#C4C4C4" : "#FFFFFF"}
          width="113px"
          height="113px"
          border="2px solid black"
          fontSize="4em"
          on:click={() => {
            CodingSkills = 5;
          }}
        />
      </div>
      <div style="display: flex; justify-content: space-between;">
        <p style="font-size: 24px; font-weight: 600;">Low</p>
        <p style="font-size: 24px; font-weight: 600;">High</p>
      </div>
    </div>
    <Button
      text="Next"
      backgroundColor="#FFE37F"
      width="115px"
      height="70px"
      border="1.2px solid black"
      fontSize="1.6em"
      on:click={() => {
        condingSkillSubmit = true;
      }}
    />
  </div>
{/if}

{#if condingSkillSubmit && !Greetings}
  <div class="account-settings" style="margin-top: 5%;">
    <h1>What do you know in coding?</h1>
    <p style="margin-top: 0%;">
      Explain in detail. Our AI will decode your answer
    </p>
    <textarea
      name="CodingKnowledge"
      id="CodingKnowledge"
      cols="30"
      rows="10"
      bind:value={Description}
    ></textarea>
    <Button
      text="Next"
      backgroundColor="#FFE37F"
      width="115px"
      height="70px"
      border="1.2px solid black"
      fontSize="1.6em"
      on:click={() => {
        Greetings = true;
      }}
    />
  </div>
{/if}

{#if Greetings}
  <div
    class="account-settings"
    style="display:flex; justify-content: center; align-items:center; text-align:center; width: 100%; height: 100%; margin-left:0%; margin-right:0%; margin-bottom:0%;  margin-top : 10%"
  >
    <h1>Welcome</h1>
  </div>
{/if}

<style>
  .submit-form {
    margin-top: 10%;
    margin-left: 15%;
    display: flex;
    flex-direction: column;
    gap: 5px;
    font-family: Inter;
    animation: fadeIn 1s ease-in-out forwards;
  }

  .legal_notice {
    margin-top: 8%;
    margin-left: 12%;
    display: flex;
    flex-direction: column;
    gap: 5px;
    font-family: Inter;
    animation: fadeIn 1s ease-in-out forwards;
  }

  .legal_notice h1 {
    font-weight: 900;
    font-size: 60px;
  }

  .legal_notice p {
    line-height: 60px;
    font-weight: 600;
    font-size: 24px;
    width: 550px;
    margin-bottom: 5rem;
  }

  .account-settings {
    margin-top: 10%;
    margin-left: 15%;
    display: flex;
    flex-direction: column;
    font-family: Inter;
    animation: fadeIn 1s ease-in-out forwards;
  }

  .account-settings h1 {
    font-weight: 900;
    font-size: 64px;
  }

  .account-settings p {
    line-height: 45px;
    font-weight: 600;
    font-size: 32px;
    width: 750px;
    margin-bottom: 3rem;
  }

  .account-settings textarea {
    width: 80%;
    height: 200px;
    font-size: 2.5em;
    font-family: Inter;
    padding: 20px;
    border: 2px solid black;
    border-radius: 10px;
    margin-bottom: 5rem;
  }

  .Coding-Skills {
    margin-top: 5%;
    margin-left: 15%;
    display: flex;
    flex-direction: column;
    font-family: Inter;
    animation: fadeIn 1s ease-in-out forwards;
  }

  .Coding-Skills h1 {
    font-weight: 900;
    font-size: 64px;
  }

  .Flex-Numbers {
    display: flex;
    flex-direction: column;
    gap: 10px;
    width: 50%;
    margin-bottom: 5%;
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
