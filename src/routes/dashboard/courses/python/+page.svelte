<script>
    import Button from "../../../../components/button.svelte";
</script>


<div class="container">
    <div class="course_info">
        <div class="typo">
            <h1>Python</h1>
            <p>
                Python is a user friendly, high-level programming language popular for its readability
            </p>
        </div>
        <div class="difficulty">
            <h3>Easy</h3>
        </div>
    </div>
    <Button
        backgroundColor="#FFE37F"
        width="120px"
        border="1.5px solid black"
        borderRadius="9.6px"
        text="Enroll"
    />
</div>


<style>
    .container {
        display: flex;
        flex-direction: column;
        justify-self: center;
        margin-left: 350px;
        margin-top: 200px;
        font-family: "Inter";
        gap: 50px;
    }

    .course_info {
        width: 65%;
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        border: 3px solid #000000;
        border-radius: 16px;
        padding: 40px;
    }

    .course_info p {
        font-size: 24px;
        color: #52525C;
        width: 70%;
        font-weight: 500;
    }
    .course_info h1 {
        font-weight: 900;
        margin: 0;
        font-size: 55px;
    }
    .difficulty {
        display: flex;
        align-items: center;
        justify-content: center;
        width : 120px;
        height: 60px;
        margin-bottom: -220px;
        margin-right: -43px;
        border: 3px solid black;
        border-top-left-radius: 16px;
        border-bottom-right-radius: 16px;
        text-align: center;
        color: #449108;
    }
</style>
