<!-- Dashboard should only be viewed when the user logs in -->
<script>
    import Course from "../../components/Course.svelte";
    import Button from "../../components/button.svelte";

    let selectedCourse = "";
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
    }

    .card-container > div:last-child {
        position: relative;
        left: 23.5%;
        margin-top: 3em;
    }
</style>

<h1>Choose a course to enroll in.</h1>
<div class="card-container">
    <div class="card_view">
        <Course
        course="Python"
        difficulty="Easy"
        description="Python is a user friendly, high-level programming language popular for its readability"
        />
        <Course
        course="Web Trio"
        difficulty="Easy"
        description="HTML, CSS, and JavaScript are the building blocks of the web"
        />
    </div>
    <div>
        <Button
        backgroundColor="#FFE37F"
        width="100px"
        border="1.2px solid black"
        borderRadius="9.6px"
        text="Next" />
    </div>
</div>




