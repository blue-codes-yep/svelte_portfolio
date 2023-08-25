<script>
  import ThemeToggle from "./ThemeToggle.svelte";
</script>

<nav class="navbar">
  <a href="/">Home</a>
  <a href="#about">About</a>
  <a href="#project">Projects</a>
  <a href="#contact">Contact</a>
  <ThemeToggle />
</nav>

<style>
  .navbar {
    display: flex;
    justify-content: center; 
    align-items: center; 
    flex-wrap: nowrap; 
    padding-bottom: 20px;

  }

  .navbar a {
    margin: 0 15px; 
    text-decoration: none;
    color: var(--text-color);
  }

  .navbar a:hover {
    text-decoration: underline;
  }
</style>
