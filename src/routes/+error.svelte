<script>
    import Button from "../components/button.svelte";
</script>


<style>
    .error_container {
    margin-top: 10%;
    margin-left: 15%;
    display: flex;
    flex-direction: column;
    font-family: Inter;
    animation: fadeIn 1s ease-in-out forwards;
  }

  .error_container h1 {
    font-weight: 900;
    font-size: 64px;
    text-align: left;
    margin-left: -0.2%;
    margin-bottom: 0%;
  }

  .error_container p {
    line-height: 45px;
    font-weight: 600;
    font-size: 32px;
    width: 100%;
    margin-bottom: 3rem;
  }

  .buttons-container {
    display: flex;
    flex-direction: column;
    gap: 40px;
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


    <div class="error_container">
        <h1>Error 404</h1>
        <p>
            We looked all over and couldn’t find that page! We’re deeply sorry for the inconvenience
        </p>

        <div class="buttons-container">
            <Button
            text="Go home"
            backgroundColor="#FFE37F"
            width="130px"
            height="60px"
            border="1.2px solid black"
            fontSize="1.6em"
            boxShadow="0px 10px 20px rgba(0, 0, 0, 0.25)"
            on:click={() => {
                window.location.href = "/";
            }}
            />
            <Button
            text="Report incident"
            backgroundColor="#FFABAB"
            width="250px"
            height="70px"
            border="1.2px solid black"
            fontSize="1.6em"
            boxShadow="0px 10px 20px rgba(0, 0, 0, 0.25)"
            />
        </div>
    </div>