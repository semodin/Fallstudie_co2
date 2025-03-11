<script>
  export let header = "CO2-footprint";
  export const img = "/logo.webp"; 
 
  // Links für die Navigation
  export let navLinks = [
  { name: "Home", path: "/App.svelte" },
  { name: "Über uns", path: "/About.svelte" },
  { name: "Zusammenarbeit", path: "/collaboration" }
  ];
</script>

<header>
  <img src="{img}" alt="Logo">
  <h1>{header}</h1>

  <!-- Navigation -->
  <nav>
    <ul class="nav-list">
      {#each navLinks as link}
        <li><a href="{link.path}">{link.name}</a></li>
      {/each}
    </ul>
  </nav>
</header>

<style>
header {
  position: sticky;
  top: 0;
  left: 0;
  width: 100%;
  padding: 10px;
  z-index: 1000;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  background-color: #d4eebe;
  display: flex;
  flex-direction: column; /* Stellt das Logo über h1 */
  justify-content: center;
  align-items: center;
  color: black;
  text-align: center;
}

img {
  max-width: 180px;
  height: auto;
  object-fit: cover;
  object-position: center top;
  border-radius: 100%;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  }
/* Navigation */
.nav-list {
  list-style: none;
  padding: 0;
  margin: 10px 0 0;
  display: flex;
  gap: 15px;
}

.nav-list li {
  display: inline;
}

.nav-list a {
  text-decoration: none;
  color: black;
  font-weight: bold;
  padding: 8px 12px;
  border-radius: 5px;
  transition: background 0.3s ease;
}

.nav-list a:hover {
  background: rgba(0, 0, 0, 0.1);
}
</style>