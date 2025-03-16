<script>
  export let header = "CO2-footprint";
  export const img = "/logo.webp"; 
 

</script>

<header>
  <img src="{img}" alt="Logo">
  <h1>{header}</h1>


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

</style>
