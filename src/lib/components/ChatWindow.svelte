<script>
  import { chatVisible } from '$lib/store';

  // Function to toggle the chat window visibility
  function toggleChat() {
    chatVisible.update(n => !n);
  }
</script>

<div class="chat-container">
  <div class="chat-header" on:click={toggleChat}>
    Virtual Assistant
  </div>
  
  {#if $chatVisible}
    <div class="chat-content">
      <!-- Chat content goes here -->
    </div>
  {/if}
</div>

<style>
  .chat-container {
    position: fixed;
    bottom: 0;
    right: 0;
    width: 300px;
    background-color: #f0f0f0;
    border: 1px solid #ccc;
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
    z-index: 1000;
    transition: all 0.3s ease;
  }

  .chat-header {
    padding: 10px;
    background-color: #007bff;
    color: white;
    cursor: pointer;
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
  }

  .chat-content {
    height: 400px;
    background-color: white;
    overflow-y: auto;
  }
</style>
