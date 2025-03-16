<script>
  import { route } from "./store.js";
  import Header from "./lib/Header.svelte";
  import Footer from "./lib/Footer.svelte";
  import Tabelle from "./lib/Tabelle.svelte";
  import About from "./About.svelte";
  import Impressum from "./Impressum.svelte";
  import Contact from "./contact.svelte";

  let currentRoute;
  route.subscribe(value => currentRoute = value);
</script>
<Header/>
 
<main>
  <div class="container">
 

    {#if currentRoute === "home"}
    <Tabelle />
    {:else if currentRoute === "about"}
    <About />
    {:else if currentRoute === "contact"}
    <Contact />
    {:else if currentRoute === "impressum"}
    <Impressum />
    {/if} 


</main>
<Footer/>


<style>
  .container {
    display: flex;
    flex-direction: column;
    height:fit-content; /* Volle Bildschirmhöhe */
  }
</style>
