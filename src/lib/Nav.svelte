<script>
  import ThemeToggle from "./ThemeToggle.svelte";
</script>

<nav class="navbar">
  <a href="/" class="$page.path === '/' ? 'active' : ''">
    <div class="home-svg">
    <svg
      viewBox="0 0 24 24"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
      style="stroke: var(--home-svg-stroke);"
      width="27"
      height="30"
      ><g id="SVGRepo_bgCarrier" stroke-width="0" /><g
        id="SVGRepo_tracerCarrier"
        stroke-linecap="round"
        stroke-linejoin="round"
      /><g id="SVGRepo_iconCarrier">
        <path
          d="M2.36407 12.9579C1.98463 10.3208 1.79491 9.00229 2.33537 7.87495C2.87583 6.7476 4.02619 6.06234 6.32691 4.69181L7.71175 3.86687C9.80104 2.62229 10.8457 2 12 2C13.1543 2 14.199 2.62229 16.2882 3.86687L17.6731 4.69181C19.9738 6.06234 21.1242 6.7476 21.6646 7.87495C22.2051 9.00229 22.0154 10.3208 21.6359 12.9579L21.3572 14.8952C20.8697 18.2827 20.626 19.9764 19.451 20.9882C18.2759 22 16.5526 22 13.1061 22H10.8939C7.44737 22 5.72409 22 4.54903 20.9882C3.37396 19.9764 3.13025 18.2827 2.64284 14.8952L2.36407 12.9579Z"
          style="stroke: var(--home-svg-stroke);"
          stroke-width="1.5"
        />
        <path
          d="M15 18H9"
          style="stroke: var(--home-svg-stroke);"
          stroke-width="1.5"
          stroke-linecap="round"
        />
      </g></svg
    ></div>
  </a>
  <div class="nav-about"><a href="#about" class="$page.path === '/#about' ? 'active' : ''">About</a></div>
  <div class="nav-projects"><a href="#project" class="$page.path === '/#project' ? 'active' : ''">Projects</a></div>
  <div class="nav-contact"><a href="#contact" class="$page.path === '/#contact' ? 'active' : ''">Contact</a></div>
  <ThemeToggle />
</nav>

<style>
.navbar {
  display: grid;
  grid-template-columns: 1fr 5fr 5fr 1fr; 
  grid-template-areas: 
    "home about projects contact toggle";
}

.home-svg {
  position: fixed;
  grid-area: home;
  z-index: 1;
  margin-left: 5px;
}

.nav-about {
  grid-area: about;
}

.nav-projects {
  grid-area: projects;
}

.nav-contact {
  grid-area: contact;
}

.navbar a {
  text-decoration: none;
  color: var(--text-color);
  font-size: 1.5rem;
  font-weight: 500;

  transition: all 0.2s ease-in-out;
}
</style>
