<script>
    import { page } from '@sveltejs/kit';
  </script>
  
  <style>
    nav {
      display: flex;
      gap: 20px;
      padding: 15px;
      background: #333;
      color: white;
      position: sticky;
      top: 0;
      z-index: 1000;
    }
  
    a {
      text-decoration: none;
      color: white;
      font-weight: bold;
      transition: color 0.3s;
    }
  
    a:hover {
      color: #ffcc00;
    }
  
    .active {
      border-bottom: 2px solid #ffcc00;
    }
  </style>
  
  <nav>
    <a href="/" class={$page.url.pathname === "/" ? "active" : ""}>Homepage</a>
    <a href="/about" class={$page.url.pathname === "/about" ? "active" : ""}>Über uns</a>
    <a href="/collaboration" class={$page.url.pathname === "/collaboration" ? "active" : ""}>Zusammenarbeit</a>
  </nav>
  
  <slot /> <!-- Hier wird der Inhalt der Seiten eingefügt -->
  