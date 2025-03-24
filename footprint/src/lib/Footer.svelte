
<script>
    import { route } from "../store.js";

function navigateTo(page) {
  route.set(page); 
}
   export let footer = ""; 
  </script>
   
  <footer>
             
        <nav>
          <ul class="nav-list">
            <p>{footer}</p>
            <button on:click={() => navigateTo('impressum')}>Impressum</button>
            <button on:click={() => navigateTo('datenschutz')}>Datenschutz</button>
            
          </ul>
        </nav>

  </footer>

  <style>
    footer {
    position: fixed;
    bottom: 0%;
    left: 0;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 1rem;
    padding: 10px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    background-color: #ddd;
    color: black;
    text-align: center;
    height: 50px;
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
    margin: 0 0 0 0;
    
       }

    .nav-list {
      list-style: none;
      padding: 0;
      margin: 10px 0 0;
      display: flex;
      gap: 15px;
    }

    .nav-list button {
    display: inline;
    background-color: #ddd;
    color: black;}


    .nav-list button:hover {
    background: rgba(0, 0, 0, 0.1);
}

  </style>