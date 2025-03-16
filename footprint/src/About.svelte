<script>

  
  export let message = "Über uns!";
</script>

<main>

  <section class="content">
    <h1>{message}</h1>
    <p>Willkommen auf der "Über uns"-Seite! Hier erfährst du mehr über unser Projekt.</p>
  </section>


</main>

<style>
main {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  padding: 20px;
}

.content {
  max-width: 800px;
}
</style>

