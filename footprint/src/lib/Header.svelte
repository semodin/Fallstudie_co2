

<script>
    export let header= "CO2-footprint";
    export const img = "/img/logo.webp";
  </script>
  
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
    /*display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 1rem;
    padding: 20px;
    
    color: black;
    padding: 1rem;
    text-align: center;*/
    }



    img {
    width: 180px;
    border-radius: 100%;
    }
  </style>
  
  <header>
    <img src="/img/logo.webp" alt="Logo">
    <h1>{header}</h1>
  </header>