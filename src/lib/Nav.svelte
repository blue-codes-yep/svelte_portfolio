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
    justify-content: center; /* Center items horizontally */
    align-items: center; /* Center items vertically */
    flex-wrap: nowrap; /* Keep items in a single row */
    padding: 10px;
    background-color: var(--background-color);
  }

  .navbar a {
    margin: 0 15px; /* Space between links */
    text-decoration: none;
    color: var(--text-color);
  }

  .navbar a:hover {
    text-decoration: underline;
  }
</style>
