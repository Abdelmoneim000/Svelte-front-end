<!-- Home page -->
<script>
    import Button from "../components/button.svelte";
    import { onMount } from 'svelte';
  
    let selected = "Home"; // Default selected nav item works as a state.
    const navText = ["Home", "Sign In", "Sign Up"];
  
    const selectItem = (item) => {
        selected = item;
    };
  
    onMount(() => {
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                // Use the 'isIntersecting' property to check if the entry is in view
                if(entry.isIntersecting) {
                    entry.target.classList.add('fadeIn');
                } else {
                    // Optional: Remove the class if you want the animation to trigger every time the section comes into view
                    // entry.target.classList.remove('fadeIn');
                }
            });
        }, { threshold: 0.1 }); // Adjust the threshold as needed
  
        // Observe the '.Intro' section
        const introSection = document.querySelector('.Intro');
        if (introSection) {
            observer.observe(introSection);
        }
    });
</script>

<style>
    :global(body) {
        background-color: #F7F7F7;
        font-family: 'Inter';
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

<!--Elements and sections go here-->

<!--Navigation bar-->
<div class="HomeBody">
    <nav class="Menu">
        {#each navText as text (text)}
            <div class:selected={selected === text} on:click={() => selectItem(text)}>{text}</div>
        {/each}
    </nav>
</div>

<!-- Main Header -->

<header class="Intro" style="">
    <h1 style="font-size: 55px;">Learn Coding Fast.</h1>
    <p style="font-weight: 600; font-size: 22px; margin-bottom: 3%">PolyLabs is a platform to quickly and efficiently learn programming.</p>
    <Button
        width="10%"
        height="50px"
        text="Learn more"
        border= "1px solid #000000"
        backgroundColor="#FFE37F"
        boxShadow="0px 4px 20px 0px #00000033"
        borderRadius="5px"
    />
</header>
<section>
    <h1>Meet "Kernel"</h1>
</section>