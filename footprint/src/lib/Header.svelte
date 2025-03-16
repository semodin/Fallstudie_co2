<script>

  import { route } from "../store.js";

function navigateTo(page) {
  route.set(page); // Ändert die Route
}

export let header = "CO2-footprint"; 
export const img = "/logo.webp"; 
 
</script>

<header>
  <div class="header-container">
  <img src="/logo1.webp" alt="Logo">
  <h1>{header}</h1>
  </div>

  <nav>
    <ul class="nav-list">
      <button on:click={() => navigateTo('home')}>Home</button>
      <button on:click={() => navigateTo('about')}>Über uns</button>
      <button on:click={() => navigateTo('contact')}>Kontakt</button>

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
  flex-direction: column; /* Stellt sicher, dass Inhalte untereinander bleiben */
  justify-content: center;
  align-items: center;
  color: black;
  text-align: center;
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;
}

.header-container {
  display: flex;
  align-items: center; /* Bild und Text vertikal ausrichten */
  gap: 15px; /* Abstand zwischen Bild und Titel */
}

img {
  max-width: 100px;
  height: auto;
  object-fit: cover;
  object-position: center top;
  border-radius: 100%;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

/* Navigation */
.nav-list {
  padding: 0;
  margin: 10px 0 0 0;   display: flex;
  gap: 15px;
}

.nav-list button {
  background-color: #d4eebe;
}

.nav-list button:hover {
  background: rgba(0, 0, 0, 0.1);
}

</style>
