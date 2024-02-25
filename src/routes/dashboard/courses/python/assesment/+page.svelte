<script>
    import CodeEditor from "../../../../../components/CodeEditor.svelte";
    import Button from "../../../../../components/button.svelte";
</script>

<main>
    <div class="Test-question">
        <h1>Question 1</h1>
        <p>Write a function that takes in a string and returns the string in reverse</p>
    </div>
    <div class="card-container">
        <div>
            <CodeEditor />
        </div>
        <div>
            <Button text="Submit" backgroundColor="#FFE37F" />
        </div>
    </div>
</main>