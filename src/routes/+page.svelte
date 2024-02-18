<!-- Home page -->
<script>
  import Button from "../components/button.svelte";
  import chat from "../assets/Chat.svg";
  import Lessons from "../assets/Lessons.svg";
  import Github from "../assets/Github.svg";
  import email from "../assets/email.svg";
  import Twitter from "../assets/Twitter.svg";
  import Google from "../assets/Google.svg";
  import { goto } from "$app/navigation";

  let selected = "Home"; // Default selected nav item works as a state.
  const navText = ["Home", "Sign In", "Sign Up"]; // Navigation items

  const selectItem = (item) => {
    selected = item;
  };
</script>

<!--Elements and sections go here-->

<!--Navigation bar-->
<div class="HomeBody">
  <nav class="Menu">
    {#each navText as text (text)}
      <div class:selected={selected === text} on:click={() => selectItem(text)}>
        {text}
      </div>
    {/each}
  </nav>
</div>

<!-- Sign-in page -->
{#if selected === "Sign In"}
<header class="Intro">
  <h1 style="font-size: 55px;">Sign into PolyLabs</h1>
  <p
    style="font-weight: 600; font-size: 22px; margin-bottom: 3%; margin-top: -0.5%;"
  >
  Select your preferred method of authentication
  </p>
  <div style="display: flex; Justify-content:center; align-items:center; flex-wrap:wrap; width:60%; gap: 50px;">
    <div class="Sign-up-in-button">
      <img src={Github} alt="Google" />
      <p style="font-weight: 700; font-size: 28px;">Github</p>
    </div>
    <div class="Sign-up-in-button">
      <img src={Twitter} alt="Google"  />
      <p style="font-weight: 700; font-size: 28px;">Twitter</p>
    </div>
    <div class="Sign-up-in-button">
      <img src={Google} alt="Google" />
      <p style="font-weight: 700; font-size: 28px;">Google</p>
    </div>
    <div class="Sign-up-in-button" on:click={() => {goto("/SignIn")}}>
      <img src={email} alt="Google" />
      <p style="font-weight: 700; font-size: 28px;">Email</p>
    </div>
  </div>
</header>
{/if}

<!-- Sign Up page -->
{#if selected === "Sign Up"}
<header class="Intro">
  <h1 style="font-size: 55px;">Sign Up for PolyLabs</h1>
  <p
    style="font-weight: 600; font-size: 22px; margin-bottom: 3%; margin-top: -0.5%;"
  >
  Select your preferred method of authentication
  </p>
  <div style="display: flex; Justify-content:center; align-items:center; flex-wrap:wrap; width:60%; gap: 50px;">
    <div class="Sign-up-in-button">
      <img src={Github} alt="Google" />
      <p style="font-weight: 700; font-size: 28px;">Github</p>
    </div>
    <div class="Sign-up-in-button">
      <img src={Twitter} alt="Google"  />
      <p style="font-weight: 700; font-size: 28px;">Twitter</p>
    </div>
    <div class="Sign-up-in-button">
      <img src={Google} alt="Google" />
      <p style="font-weight: 700; font-size: 28px;">Google</p>
    </div>
    <div class="Sign-up-in-button" on:click={() => {goto("/SignUp")}}>
      <img src={email} alt="Google" />
      <p style="font-weight: 700; font-size: 28px;">Email</p>
    </div>
  </div>
</header>
{/if}

<!-- Main Header -->
{#if selected === "Home"}
<header class="Intro">
  <h1 style="font-size: 55px;">Learn Coding Fast.</h1>
  <p
    style="font-weight: 600; font-size: 22px; margin-bottom: 3%; margin-top: -0.5%;"
  >
    PolyLabs is a platform to quickly and efficiently learn programming.
  </p>
  <Button
    width="10%"
    height="50px"
    text="Learn more"
    border="1px solid #000000"
    backgroundColor="#FFE37F"
    boxShadow="0px 4px 20px 0px #00000033"
    borderRadius="5px"
  />
</header>
<section>
  <h1>
    Meet “<span style="font-size: 50px; font-family: IBM Plex Mono;"
      >Kernel</span
    >”
  </h1>
  <div class="container" style="margin-left: -10%; margin-top : -1%">
    <div style="display: flex; flex-direction: column; width: 40%; height: 40%;">
        <img src={chat} alt="Chat" style="width: 100%; height: 100%;" />
        <p style="font-weight: 400; margin-left : 17%; margin-top: -5%">*Polylabs base has 300 messages/day for free</p>
    </div>
    <p style="font-weight: 400; font-family : Inter;">
      Use our free AI powered chatbot to help assist you in your coding
      struggles*. Kernel has access to your learning prompt and your code, so it
      can fully help you.
    </p>
  </div>
</section>

<section style="margin-top: 10%;">
    <h1 style="font-size: 57px;">
        Customized Content
    </h1>
    <div class="container" style="margin-left: -10%; margin-top : -1%; flex-direction: row-reverse; height: fit-content;">
      <div class="features" >
        <h1>Lesson 1</h1>
        <div style="background-color: #C7C7C7; width: 100%; height: 5px; border-radius: 10px;"></div>
        <p>Let’s do a quick review of lessons 1 & 2</p>
        <h2>Thinking 💭</h2>
        <p>Look to the code, what do you <span style="font-weight: 900;">think</span> it does?</p>
        <h2>Test it 🧪</h2>
        <p>Prove yourself right or wrong by clicking run.</p>
    </div>
      <div style="display: flex; flex-direction:column; width: 40%; height: 100%;">
        <p style="font-weight: 400; font-family : Inter; font-size: 29px;">
            Polylabs customizes learning prompts using past experience to ensure that you absorb the most amount of content as possible.
          </p>
          <p style="font-weight: 400; font-family : Inter; font-size: 29px;">
            Polylabs is proud to say that our learning process is based to help you come to conclusions, instead of us blatantly telling you the answers.
          </p>
      </div>
    </div>
</section>

<section style="margin-top: 10%;">
    <h1 style="font-size: 57px; margin-bottom: 7%; font-weight: 800;">
        Better Courses
    </h1>
    <div class="container" style="margin-left: -7%; margin-top : -1%; flex-direction: row; height: fit-content;">
        <div class="features" style="height: fit-content; gap: 40px; width: 22%; border: 3px solid black;">
            <div style="border-radius: 30px; background-color: #EBEBF0; width: 35%; height: 50px; display: flex; justify-content: center; align-items:center;">
                <p style="font-weight: 700;">Python</p>
            </div>
            <p style="color: #52525C; width:270px;">
              Python is a user friendly, high-level programming language popular for its readability.
            </p>
      </div>
      <p style="font-weight: 400; font-size: 32px; margin-left: -5%">
        Polylabs prioritizes high quality courses. At our core, we ensure that courses are made to be easily understood and we only display courses that follow our strict standards.
      </p>
</section>

<section style="display: flex; justify-content:center; align-items:center; flex-direction:column;  gap: 60px; margin-left: -3%;">
  <h1 style="font-size: 54px; font-weight:800; text-align:center; width:80%;">
    “The journey of a thousand miles starts with a single step”
  </h1>
  <Button
    width="12%"
    height="60px"
    text="Take Step 1"
    border="2px solid #000000"
    backgroundColor="#FFE37F"
    boxShadow="0px 4px 20px 0px #00000033"
    borderRadius="12px"
    fontSize="22px"
  />
</section>

<footer>
  <div style="background-color: #C7C7C7; width: 50%; height: 5px; border-radius: 10px;"></div>
  <p style="font-size: 25px; font-weight: 600; text-align: center;">
    © 2024 PolyLabs. All rights reserved.
  </p>
  <div class="FooterLogo">
  </div>
</footer>
{/if}

<style>
  :global(body) {
    background-color: #f7f7f7;
    font-family: "Inter";
  }
  .HomeBody {
    width: 100%;
    height: fit-content;
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
    margin-top: 3%;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    height: 60vh;
    animation: fadeIn 1s ease-in-out forwards;
  }

  .Sign-up-in-button {
    width: 250px;
    height: 70px;
    border: 1.44px solid #000000;
    border-radius: 11.52px;
    display: flex;
    align-items: center;
    gap: 30px;
    padding-left: 50px;
    cursor: pointer;
  }

  .Sign-up-in-button:hover {
    background-color: #f0f0f0;
  }

  .Sign-up-in-button img {
    width: 50px;
    height: 50px;
  }

  section {
    margin-top: 10%;
    margin-left: 10%;
    animation: fadeIn 1s ease-in-out forwards;
  }

  section > h1 {
    font-size: 50px;
    font-family: "Inter";
    font-weight: 700;
    margin-bottom: 2%;
  }

  .container {
    display: flex;
    align-items: center;
    justify-content: space-around;
    width: 100%;
    gap: 50px;
  }

  .container > p {
    font-size: 24px;
    width: 40%;
    line-height: 35px;
    margin-bottom: 10%;
    font-weight: 200;
    font-family: "Inter";
  }

  .features {
    display: flex;
    flex-direction: column;
    padding: 2%;
    padding-left: 3%;
    justify-content: left;
    width: 30%;
    height: 85vh;
    border: 2px solid black;
    border-radius: 16px;
  }

  .features h1 {
    font-size: 45px;
  }

  .features h2 {
    font-size: 35px;
    font-weight: 700;
    margin-bottom: 0;
  }

  .features p {
    font-size: 25px;
    font-weight: 500;
  }

  footer {
    margin-top: 10%;
    margin-left: -1%;
    justify-content: center;
    align-items: center;
    display: flex;
    flex-direction: column;
  }

  .FooterLogo {
    margin-bottom: 1%;
    margin-left: -85%;
    margin-top: -60px;
    width: 70px;
    height: 70px;
    background-image: url("../assets/FooterLogo.svg");
    background-size: cover;
    background-repeat: no-repeat;
  }


  @media (max-width: 320px) {
    .Menu div {
      width: 32%;
    }
  }

  /**
    * Animation for the page.
    * making the page content move and appear when it is loaded.
    */
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
