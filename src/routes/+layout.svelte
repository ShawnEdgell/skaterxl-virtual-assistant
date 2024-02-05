<script>
    import '../app.css'; // Adjust the path if your structure is different
    import ChatButton from '$lib/components/ChatButton.svelte';
    import ChatWindow from '$lib/components/ChatWindow.svelte';
  </script>
  
  <div class="app-layout">
    <slot />
    <!-- Here, the <slot /> tag is where the specific content of each page will be injected -->
  </div>
  
  <!-- Placing the ChatButton and ChatWindow at the end to ensure they overlay other content -->
  <ChatButton />
  <ChatWindow />
  
  <style>
    /* You can define global styles here, if needed */
  </style>
  