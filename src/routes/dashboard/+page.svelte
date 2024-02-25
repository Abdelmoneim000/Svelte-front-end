<!-- Dashboard should only be viewed when the user logs in -->
<script>
    import Course from "../../components/Course.svelte";
    import Button from "../../components/button.svelte";
    import { goto } from "$app/navigation";

    let selectedCourse = "";
    let selected = false;
    let test = false;
    let confirm = false;
</script>

<style>
    h1 {
        font-family: "Inter";
        font-size: 48px;
        margin: 20px;
        text-align: center;
    }

    .card_view {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        gap: 50px;
        margin-top: 3em;
    }

    .card-container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        overflow: hidden;
    }

    .card-container > div:last-child {
        position: relative;
        left: 23.5%;
        margin-top: 3em;
    }

    .Test-question {
    margin-top: 10%;
    margin-left: 15%;
    display: flex;
    flex-direction: column;
    font-family: Inter;
    animation: fadeIn 1s ease-in-out forwards;
  }

  .Test-question h1 {
    font-weight: 900;
    font-size: 64px;
    text-align: left;
    margin-left: -0.2%;
  }

  .Test-question p {
    line-height: 45px;
    font-weight: 600;
    font-size: 32px;
    width: 750px;
    margin-bottom: 3rem;
  }

  .buttons-container {
    display: flex;
    flex-direction: column;
    gap: 20px;
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
{#if selected == false || selectedCourse === ""}
<h1>Choose a course to enroll in.</h1>
<div class="card-container">
    <div class="card_view">
        <Course
        course="Python"
        difficulty="Easy"
        description="Python is a user friendly, high-level programming language popular for its readability"
        on:click={() => selectedCourse = "Python"}
        />
        <Course
        course="Web Trio"
        difficulty="Easy"
        description="HTML, CSS, and JavaScript are the building blocks of the web"
        on:click={() => selectedCourse = "Web Trio"}
        />
    </div>
    <div>
        <Button
        backgroundColor="#FFE37F"
        width="100px"
        border="1.2px solid black"
        borderRadius="9.6px"
        text="Next" 
        on:click={() => {
            selected = true;
            }}
        />
    </div>
</div>
{/if}

{#if selected && selectedCourse && confirm === false}
<div class="Test-question">
    <h1>Do you Know {selectedCourse}?</h1>
    <p>
        Be honest with your response
    </p>

    <div class="buttons-container">
        <Button
        text="Yes"
        backgroundColor="#FFE37F"
        width="110px"
        height="70px"
        border="1.2px solid black"
        fontSize="1.6em"
        on:click={() => {
            confirm = true;
        }}
        />
        <Button
        text="No"
        backgroundColor="#FFABAB"
        width="100px"
        height="70px"
        border="1.2px solid black"
        fontSize="1.6em"
        on:click={() => {
            confirm = false;
        }}
        />
    </div>
  </div>
{/if}

{#if confirm && test == false}
    <div class="Test-question">
        <h1>Let’s test you</h1>
        <p>
            This is a casual test just to place you in the right spot of our program. AI will be disabled.
        </p>

        <div class="buttons-container">
            <Button
            text="Start"
            backgroundColor="#FFE37F"
            width="110px"
            height="70px"
            border="1.2px solid black"
            fontSize="1.6em"
            on:click={() => {
                window.location.href = "/dashboard/courses/python/assesment";
            }}
            />
            <Button
            text={`I don’t know ${selectedCourse}`}
            backgroundColor="#FFABAB"
            width="300px"
            height="70px"
            border="1.2px solid black"
            fontSize="1.6em"
            on:click={() => {
                window.location.href = "/dashboard";
            }}
            />
        </div>
  </div>
{/if}


