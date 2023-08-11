<style>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    padding: 20px;
    box-sizing: border-box;
    width: 80%; 
    margin: 0 auto; 
  }
</style>

<script>
  import Nav from "$lib/Nav.svelte";
  import Footer from "$lib/Footer.svelte";
</script>

<Nav />
<div class="container">
  <slot />
</div>
<Footer />

