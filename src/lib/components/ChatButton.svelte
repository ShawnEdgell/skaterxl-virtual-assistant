<script>
    import { chatVisible } from '$lib/store';
    
    function toggleChat() {
      chatVisible.update(n => !n);
    }
  </script>
  
  <button on:click={toggleChat}>Chat with us!</button>
  