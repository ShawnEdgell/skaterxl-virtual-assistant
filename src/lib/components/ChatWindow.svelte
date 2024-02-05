<script>
  import { afterUpdate } from 'svelte';
  import { chatVisible } from '$lib/store';

  let chatContentElement; // Reference to the chat content div

  function toggleChat() {
    chatVisible.update(n => !n);
  }

  // Automatically scroll to the bottom after the DOM updates
  afterUpdate(() => {
    if (chatContentElement) {
      chatContentElement.scrollTo(0, chatContentElement.scrollHeight);
    }
  });
</script>

<div class="fixed bottom-0 right-0 mb-4 mr-4 w-72 bg-gray-100 border border-gray-300 rounded-t-lg z-50 transition-all duration-300">
  <button on:click={toggleChat} 
          class="w-full text-left bg-blue-500 text-white cursor-pointer px-4 py-2 rounded-t-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
          type="button">
    XL Virtual Assistant
  </button>
  
  {#if $chatVisible}
    <div class="h-96 bg-white overflow-y-auto" bind:this={chatContentElement}>
      <!-- Replace this iframe with your Dialogflow chatbot -->
      <iframe
        allow="microphone;"
        src="https://console.dialogflow.com/api-client/demo/embedded/b14fb721-e239-4b30-8b20-817940aa5995"
        class="chatbot-iframe"
        style="border: none; width: 100%; height: 100%;">
      </iframe>
    </div>
  {/if}
</div>
