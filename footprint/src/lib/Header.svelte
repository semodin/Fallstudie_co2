<script>
  import { route } from "../store.js";
  let menuOpen = false;
  const rtlLanguages = ["ar", "he", "fa", "ur"];
  let userLang = navigator.language || (navigator.languages ? navigator.languages[0] : "en");
  let isRTL = rtlLanguages.some(lang => userLang.startsWith(lang));

  function toggleMenu() {
    menuOpen = !menuOpen;
  }

  function navigateTo(page) {
    route.set(page);
    menuOpen = false;
  }

  export let header = "CO2-footprint";
  export const img = "/Logo2_small.png";
 
</script>

<header>
  
  <div class="header-container">
    <img src="/Logo2_small.png" alt="Logo" />
    <h1>{header}</h1>
  </div>

  <button class="menu-button {isRTL ? 'rtl' : ''}" on:click={toggleMenu}>
    ☰
  </button>

  <!-- Mobiles Menü -->
  <nav class="mobile-nav {menuOpen ? 'open' : ''} {isRTL ? 'rtl' : ''}">
    <ul class="nav-list">
      <li><button on:click={() => navigateTo('home')}>Home</button></li>
      <li><button on:click={() => navigateTo('about')}>Über uns</button></li>
      <li><button on:click={() => navigateTo('contact')}>Kontakt</button></li>
    </ul>
  </nav>

  <!-- Desktop-Menü -->
  <nav class="desktop-nav {isRTL ? 'rtl' : ''}">
    <ul class="nav-list">
      <li><button on:click={() => navigateTo('home')}>Home</button></li>
      <li><button on:click={() => navigateTo('about')}>Über uns</button></li>
      <li><button on:click={() => navigateTo('contact')}>Kontakt</button></li>
    </ul>
  </nav>
</header>

<style>
/* === Header-Styling === */
header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  padding: 10px;
  z-index: 1000;
  background-color: #d4eebe;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;
}

.header-container {
  display: flex;
  align-items: center;
  gap: 15px;
}

img {
  max-width: 100px;
  height: auto;
  object-fit: cover;
  border-radius: 100%;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

/* === Menübutton === */
.menu-button {
  display: block;
  background: none;
  border: none;
  font-size: 1.5em;
  cursor: pointer;
  padding: 10px;
  align-self: flex-start;
}

/* === Navigation gemeinsam === */
nav {
  width: 100%;
  background-color: #d4eebe;
  padding: 10px 0;
 }

/* === MOBILE-NAV === */
.mobile-nav {
  display: none;
  flex-direction: column;
  position: absolute;
  top: 100%;
  left: 0;
  width: auto;
  background-color: #d4eebe;
  z-index: 999;
  padding: 10px;
  padding-block: 10px;
  padding-inline: 20px;
  text-align: left;
  align-items: flex-start;
}

.mobile-nav.open {
  display: flex;
}

/* Mobile Navigation RTL */
.mobile-nav.rtl {
  left: auto;
  right: 0;
  text-align: right;
  align-items: flex-end;
}

.mobile-nav.rtl .nav-list {
  flex-direction: column;
  align-items: flex-end;
  text-align: right;
}

.mobile-nav.rtl .nav-list li {
  width: auto; 
}

.mobile-nav.rtl .nav-list button {
  text-align: right;
  width: auto;
  align-self: flex-end;
}

/* === DESKTOP-NAV === */
.desktop-nav {
  display: none;
}

.desktop-nav.rtl .nav-list {
  flex-direction: row-reverse;
  justify-content: flex-end;
}

/* === Gemeinsame Navigationsliste === */
.nav-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: auto;
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
  text-align: inherit;
}

.nav-list button:hover {
  background: rgba(0, 0, 0, 0.1);
}

/* === MEDIA QUERY für Desktop === */
@media screen and (min-width: 768px) {
  .menu-button {
    display: none;
  }

  .mobile-nav {
    display: none !important;
  }

  .desktop-nav {
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    align-items: center;
  }

  .nav-list {
    flex-direction: row;
    justify-content: flex-start;
    width: auto;
  }

  .nav-list li {
    width: auto;
  }

  .nav-list button {
    width: auto;
  }

  .desktop-nav.rtl .nav-list {
    flex-direction: row-reverse;
    justify-content: flex-end;
  }
}
</style>
