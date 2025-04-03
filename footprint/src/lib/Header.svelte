<script>

  import { route } from "../store.js";
  let menuOpen = false; // Zustand für das Menü

  // Sprachen, die von rechts nach links gelesen werden
  const rtlLanguages = ["ar", "he", "fa", "ur"];

  // Aktuelle Sprache des Users abrufen
  let userLang = navigator.language || (navigator.languages ? navigator.languages[0] : "en");


  // Prüfen, ob die Sprache von rechts nach links ist
  let isRTL = rtlLanguages.some(lang => userLang.startsWith(lang));

  function toggleMenu() {
    menuOpen = !menuOpen;
  }

function navigateTo(page) {
  route.set(page); // Ändert die Route
  menuOpen = false; // Schließt das Menü
}

export let header = "CO2-footprint"; 
export const img = "/Logo2_small.png"; 
 
</script>

<header>
  <div class="header-container">
    <img src="/Logo2_small.png" alt="Logo">
    <h1>{header}</h1>
  </div>

  <button class="{isRTL ? 'menu-button rtl' : 'menu-button'}" on:click={toggleMenu}>
    ☰
  </button>

  <!-- Navigationsmenü -->
  <nav class="{menuOpen ? 'open' : ''} {isRTL ? 'rtl' : ''}">
    <ul class="nav-list">
      <li><button on:click={() => navigateTo('home')}>Home</button></li>
      <li><button on:click={() => navigateTo('about')}>Über uns</button></li>
      <li><button on:click={() => navigateTo('contact')}>Kontakt</button></li>
    </ul>
  </nav>
</header>

<style>
header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  padding: 10px;
  z-index: 1000;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  background-color: #d4eebe;
  display: flex;
  flex-direction: column; /* Stellt sicher, dass Inhalte untereinander bleiben */
  align-items: center;
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

/* Menü-Button für Mobilgeräte */
.menu-button {
  display: block;
  background: none;
  border: none;
  font-size: 1.5em;
  cursor: pointer;
  padding: 10px;
  align-self: flex-start; /* Links oben */
}


/* Standardmäßig linksbündig für LTR */
nav {
  display: none;
  flex-direction: column;
  width: 100%;
  background-color: #d4eebe;
  padding: 10px 0;
  text-align: left;
  align-items: flex-start;
  justify-content: flex-start; /* Links ausrichten */
}

/* Wenn RTL aktiviert ist, rechtsbündig ausrichten */
nav.rtl {
  text-align: right;
  align-items: flex-end;
  justify-content: flex-end; /* Rechts ausrichten */
}

/* Navigation anzeigen, wenn `menuOpen` true ist */
nav.open {
  display: flex;
}

/* Standard-Navigation: links für LTR, rechts für RTL */
.nav-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  gap: 10px;
  flex-direction: row;
  justify-content: flex-start; /* Standard linksbündig */
  align-items: center;
  white-space: nowrap; /* Verhindert Zeilenumbrüche */
 }

/* Bei RTL rechtsbündig ausrichten */
nav.rtl .nav-list {
  align-items: flex-end;
  justify-content: flex-end;
}

@media screen and (min-width: 768px) {
  nav {
    display: flex !important;
    flex-direction: row;
    justify-content: flex-start;
  }
}

.nav-list {
    flex-direction: row;
    justify-content: flex-start; /* Standard: Links */
  }

    nav.rtl {
    justify-content: flex-end;
  }

  nav.rtl .nav-list {
    justify-content: flex-end;
  }

.nav-list li {
  width: 100%;
}

.nav-list button {
  background-color: #d4eebe;
  width: 100%;
  padding: 10px;
  border: none;
  cursor: pointer;
}

.nav-list button:hover {
  background: rgba(0, 0, 0, 0.1);
}

/* Ab 768px wieder normale Navigation anzeigen */
@media screen and (min-width: 768px) {
  .menu-button {
    display: none; /* Menü-Button ausblenden */
  }

  nav {
    display: flex !important;
    flex-direction: row;
    justify-content: center;
  }

  .nav-list {
    flex-direction: row;
  }

  nav.rtl .nav-list {
    flex-direction: row-reverse;
  }

}

</style>
