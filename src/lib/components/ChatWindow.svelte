<script>
  import { afterUpdate } from 'svelte';
  import { writable } from 'svelte/store';
  import { chatVisible } from '$lib/store';

  const messages = writable([]);

  let messageText = "";
  let chatContentElement; // Reference to the chat content div

  function toggleChat() {
    chatVisible.update(n => !n);
  }

  function sendMessage() {
    if (messageText.trim() !== "") {
      messages.update(currentMessages => [...currentMessages, { text: messageText, timestamp: new Date() }]);
      messageText = ""; // Clear input after sending
    }
  }

  function handleKeydown(event) {
    if (event.key === 'Enter' && !event.shiftKey) {
      event.preventDefault(); // Prevent the default action to avoid line breaks in input
      sendMessage();
    }
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
    <div class="h-80 bg-white overflow-y-auto p-4" bind:this={chatContentElement}>
      {#each $messages as message}
        <div class="break-words p-2 bg-gray-200 my-2 rounded">
          {message.text}
        </div>
      {/each}
    </div>
    <div class="p-2 bg-gray-200">
      <input class="w-full p-2 rounded-lg border border-gray-300 focus:outline-none focus:ring-2 focus:ring-blue-500"
             type="text"
             bind:value={messageText}
             placeholder="Type your message here..."
             on:keydown={handleKeydown}>
    </div>
  {/if}
</div>
