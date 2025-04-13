<script>
  
    export let message = "Impressum";
  </script>
  
  <main>
  
    <section class="content">
      <h1>{message}</h1>
      <p>
        Willkommen auf der "Impressum"-Seite! Hier erfährst du mehr über unser Projekt.
      </p>

      <p>
        CO2-footprint Organisation <br>
        Grünstrasse 24 <br>
        12345 Musterstadt <br>
        Deutschland <br>
      </p>

      <p>
        Telefon: +49 123 456789 <br>
        Telefax: +49 123 456789 <br>
        E-Mail: info@footprint.org
      </p>

      <p>
        Geschäftsführer: Max Mustermann <br>
        Handelsregister: Musterstadt, HRB 123456 <br>
      </p>

      <p>
        Umsatzsteuer-ID: DE123456789 <br>
        Aufsichtsbehörde: Musterstadt <br>
        Verantwortlich für den Inhalt nach § 55 Abs. 2 RStV: Max Mustermann <br>
       </p>

       <h3>
        Hinweise zum Datenschutz: <br>
       </h3>
       <p>
        Diese Seite verwendet Cookies, um die Benutzererfahrung zu verbessern. <br>
        Durch die Nutzung dieser Seite stimmen Sie der Verwendung von Cookies zu. <br>
        Ihre Daten werden vertraulich behandelt und nicht an Dritte weitergegeben. <br>
       </p>

    </section>
  
  
  </main>

  <style>
    main {
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      padding: 20px;
      margin-top: 50px;
      margin-bottom: 30px;
      
    }
    
    .content {
      max-width: 100%;
    }
    </style>