<script>
  import settings from "../../../assets/settings.svg";
  import crown from "../../../assets/crown.svg";
  import arrowDown from "../../../assets/arrowDown.svg";
  import Button from "../../../components/button.svelte";
  import Lesson from "../../../components/Lesson.svelte";
  import Course from "../../../components/Course.svelte";

  let navText = ["Learn", "Catalog"];
  let drop = false; // for the dropdown profile options
  /**
   * selectOptions...
   * Array to check if the option button (EASY, MEDIUM, HARD) is selecter
   * and based on that, the text color and backround color of the option
   * should change.
   */
   let selectedOptions = [];

   function setSelected(item) {
    const index = selectedOptions.indexOf(item);
    if (index !== -1) {
        // Remove the element if found
        selectedOptions.splice(index, 1);
    } else {
        selectedOptions.push(item);
    }
    // Reassign selectedOptions to itself to trigger reactivity
    selectedOptions = selectedOptions.slice();
    }


  let selected = navText[0];
  const selectItem = (item) => {
    selected = item;
  };
</script>

<!--Navigation bar-->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div class="HomeBody">
  <nav class="Menu">
    {#each navText as text (text)}
      <!-- svelte-ignore a11y-click-events-have-key-events -->
      <!-- svelte-ignore a11y-no-static-element-interactions -->
      <div class:selected={selected === text} on:click={() => selectItem(text)}>
        {text}
      </div>
    {/each}
  </nav>
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <div
    class="profile"
    on:click={() => {
      drop = !drop;
    }}
  >
    P
  </div>
</div>

{#if drop}
  <div></div>
  <div class="dropDown">
    <div>
      <a style="width: 100%;" href="/settings">Settings</a>
      <img src={settings} alt="settings" />
    </div>
    <div>
      <a style="width: 100%;" href="/upgrade">Upgrade</a>
      <img src={crown} alt="crown" />
    </div>
  </div>
{/if}

{#if selected === "Learn"}
  <div class="container" style="justify-self: center;">
    <div class="nav-buttons">
        <div>
          <p>Python</p>
          <img src={arrowDown} alt="arrowDown">
        </div>
        <Button
            backgroundColor="#FFABAB"
            width="120px"
            border="0.78px solid black" 
            borderRadius="9.6px"
            text="Abandon"
        />
    </div>
    <Lesson
      title="Lesson 1"
      description="This lesson will go over what python is, and how it’s actually used. We’ll also take a dive into Python syntax and fundamentals."
      showButton={true}
      buttonText="Begin"
    />
    <Lesson
      title="Lesson 2"
      description="This lesson will go over what python is, and how it’s actually used. We’ll also take a dive into Python syntax and fundamentals."
      showButton={false}
    />
  </div>
{/if}

{#if selected === "Catalog"}
  <div class="container" >
    <div class="catalog_head">
      <h1>
        Course Catalog
      </h1>
      <!-- Options for selecting a Course HERE -->
      <!-- svelte-ignore a11y-no-static-element-interactions -->
      <!-- svelte-ignore a11y-click-events-have-key-events -->
      <div class="options">
        <div 
        class:selected={selectedOptions.includes("Easy")} 
        on:click={() => {setSelected("Easy")}}
        >
            <h3>Easy</h3>
        </div>
        <div 
        class:selected={selectedOptions.includes("Medium")} 
        on:click={() => {setSelected("Medium")}}
        >
            <h3>Medium</h3>
        </div>
        <div 
        class:selected={selectedOptions.includes("Hard")} 
        on:click={() => {setSelected("Hard")}}
        >
            <h3>Hard</h3>
        </div>
    </div>
    </div>
    <div class="cards_view">
      <Course
      course="Python"
      difficulty="Easy"
      description="Python is a user friendly, high-level programming language popular for its readability"
    />
    <Course
      course="Web Trio"
      difficulty="Easy"
      description="The top 3 web trio, HTML,CSS, & JS all combined into one simple course"
    />
    </div>
  </div>
{/if}


<style>
  :global(body) {
    background-color: #f7f7f7;
    font-family: "Inter";
  }

  .HomeBody {
    width: 100%;
    height: fit-content;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 70px;
  }
  .Menu {
    margin-top: 5%;
    display: flex;
    justify-content: center;
    gap: 3px;
  }

  .Menu div {
    background-color: white;
    width: 250px;
    height: 53px;
    font-weight: 700;
    font-size: 20px;
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

  .profile {
    position: relative; /* Add this line */
    margin-top: 75px;
    width: 55px;
    height: 55px;
    background-color: white;
    border-radius: 50%;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 33px;
    color: #66e07c;
    font-weight: 700;
  }

  .dropDown {
    position: absolute;
    top: 160px; /* Set this to the height of the profile element plus any margin or padding */
    right: 375px;
    background-color: white;
    width: 200px;
    border-radius: 5px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 10px;
    background-color: black;
    padding: 13px;
    animation: fadeIn 0.5s ease-in-out;
  }

  .dropDown::before {
    content: "";
    position: absolute;
    top: -10px; /* Adjust as needed */
    left: 50%;
    transform: translateX(-50%);
    border-left: 10px solid transparent;
    border-right: 10px solid transparent;
    border-bottom: 10px solid black;
  }

  .dropDown div {
    padding: 10px;
    height: 20px;
    border-radius: 5px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #484848;
  }

  .dropDown div a {
    color: white;
    text-decoration: none;
    font-size: 13px;
    font-weight: 700;
  }

  .container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    gap: 30px;
    margin-top: 100px;
    margin-bottom: 10%;
    animation: fadeIn 1s ease-in-out;
  }

  .catalog_head {
    display: flex;
    flex-direction: column;
    padding-right: 20%;
  }

  .catalog_head h1 {
    font-size: 58px;
    font-weight: 900;
    margin-top: 0%;
  }

  .options {
    display: flex;
    flex-direction: row;
    gap: 50px;
  }

  .cards_view {
    display: flex;
    flex-direction: row;
    justify-content: center;
    gap: 50px;
  }


  .nav-buttons {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 32%;
  }

  .nav-buttons div {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    width: 250px;
    height: 30px;
    border: 2.6px solid #D9D9D9;
    border-radius: 8.8px;
    padding: 13.2px 24px 13.2px 17.6px;
    cursor: pointer;
  }

  .nav-buttons div p {
    font-size: 23px;
    font-weight: 700;
  }

  .nav-buttons div img {
    width: 25px;
    height: 25px;
  }

  .options {
    margin-bottom: 5%;
    gap: 10px;
  }

  .options div {
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #EBEBF0;
    width: 120px;
    height: 40px;
    border-radius: 20px;
    cursor: pointer;
  }
  
  .options div.selected {
    background-color: black;
    color: white;
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
