<script>
  import { chatVisible } from '$lib/store';
  
  function toggleChat() {
    chatVisible.update(n => !n);
  }
</script>

<div class="text-center mt-4">
  <button 
    on:click={toggleChat}
    class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-full transition duration-150 ease-in-out">
    Chat with us!
  </button>
</div>
