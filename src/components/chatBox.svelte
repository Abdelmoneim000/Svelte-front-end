<!-- ChatBox.svelte -->
<script>
    export let messages;

    let newMessage = '';

    // Function to trim the message and add it to the messages array
    function sendMessage() {
        if (newMessage.trim() !== '') {
            messages.update(currentMessages => [...currentMessages, { text: newMessage, timestamp: new Date(), sender: 'user' }]);
            newMessage = '';
        }
    }

    // Enter key sends the message
    function handleKeydown(event) {
        if (event.key === 'Enter') {
            sendMessage();
            event.preventDefault(); // Prevent form submission or newline in textarea
        }
    }
</script>

<style>
    .chat-box {
        width: 100%;
        max-width: 600px; /* Adjust based on your preference */
        margin: auto;
        display: flex;
        flex-direction: column;
        border: 2px solid #ddd;
        border-radius: 8px;
        overflow: hidden;
        background-color: white; /* Ensure contrast with the global body background */
    }

    .messages {
        flex-grow: 1;
        padding: 10px;
        overflow-y: auto; /* Enable scroll */
        background-color: #f9f9f9; /* Light background for the message area */
        display: flex;
        flex-direction: column;
        gap: 8px; /* Space between messages */
    }

    .message {
        background-color: #e7e7e7; /* Slightly darker background for individual messages */
        padding: 5px 10px;
        border-radius: 4px;
        max-width: 70%;
        word-wrap: break-word; /* Ensure long words do not overflow */
        align-self: flex-end; /* Align messages to the right */
    }

    .input-area {
        display: flex;
        border-top: 2px solid #ddd;
    }

    .input-area input {
        flex-grow: 1;
        padding: 10px;
        border: none;
        outline: none;
    }

    .input-area button {
        padding: 10px 20px;
        border: none;
        background-color: #007bff;
        color: white;
        cursor: pointer;
    }

    .input-area button:hover {
        background-color: #0056b3;
    }
</style>

<div class="chat-box">
    <div class="messages">
        {#each $messages as {text, timestamp, sender} (timestamp.toISOString())}
            <div class="message">{text}</div>
        {/each}
    </div>
    <div class="input-area">
        <input
          placeholder="Type a message..."
          bind:value={newMessage}
          on:keydown={handleKeydown} />
        <button on:click={sendMessage}>Send</button>
    </div>
</div>
