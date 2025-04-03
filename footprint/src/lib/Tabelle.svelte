<script>

  import { tableData } from "./tableData.js";

  export let message = "Entdecken Sie die CO₂-Emissionen weltweit!";

  let sortedData = tableData;
  const sanitizeInput = (input) => input.replace(/</g, "&lt;").replace(/>/g, "&gt;");

  let searchQuery = ""; // Suchfeld für Filterung
  let filteredData = tableData; // Neue gefilterte Daten
 
  //Get the headers of the table
  const tableHeaders = Object.keys(tableData[0]);
  let selectedHeader = "id";
  let ascendingOrder = true; 

  //Nummer-sortierung
  const sortByNumber = (tableHeaders) => {
    sortedData = sortedData.sort((obj1, obj2) => {
      return ascendingOrder ? obj1[tableHeaders] - obj2[tableHeaders] : obj2[tableHeaders] - obj1[tableHeaders];
    });
      selectedHeader = tableHeaders;
  };

  //String-sorting
  const sortByString = (tableHeaders) => {
    sortedData = sortedData.sort((obj1, obj2) => {
      if (obj1[tableHeaders] < obj2[tableHeaders]) {
        return -1;
      } else if (obj1[tableHeaders] > obj2[tableHeaders]) {
        return 1;
      } else {
        return 0;
      }
    });
    if (!ascendingOrder) {
      sortedData = sortedData.reverse();
    }
    selectedHeader = tableHeaders;
  };


// **Filterfunktion**
 const filterData = () => {
    const query = searchQuery.toLowerCase();
    
    // Filterung auf Basis des Suchbegriffs
    filteredData = tableData.filter(row =>
      Object.values(row).some(value =>
        String(value).toLowerCase().includes(query)
      )
    );

    // Nach Filtern muss auch Sortierung neu angewendet werden
    sortedData = [...filteredData];
    if (selectedHeader) {
      if (selectedHeader === "id" || selectedHeader === "footprint") {
        sortByNumber(selectedHeader);
      } else {
        sortByString(selectedHeader);
      }
    }
  };

</script>

<main>

<div class="header-container">
  <h1>{message}</h1>

   <p>Hier finden Sie eine interaktive Übersicht über die jährlichen CO₂-Emissionen verschiedener Länder und Unternehmen. Nutzen Sie die Sortier- und Filterfunktionen, um gezielt nach Informationen zu suchen und wertvolle Einblicke in die Verteilung der Emissionen zu gewinnen.</p>
</div>

<!-- Suchfeld für die Filterung -->
<div class="filter-container">
  <input 
    type="text" 
    placeholder="Suchen..." 
    bind:value={searchQuery} on:input={() => searchQuery = sanitizeInput(searchQuery)} 
    on:input={filterData} 
    class="search-box"
  />
</div>

<div class="table-container">
<table id="myTable">
  <thead>
    <tr>
      {#each tableHeaders as header}
      <th class:higlighted={selectedHeader === header}
      on:click={() => (header === 'id' || header === 'footprint') ? sortByNumber(header) : sortByString(header)}>{header.replace("_", " ")}
      
      {#if header === selectedHeader}
      <button type="button" class="order-icon" on:click={() => ascendingOrder = !ascendingOrder} aria-label="Toggle sort order">
        {ascendingOrder ? "▼" : "▲"} 

      </button>
      {/if}
    
      </th>
      {/each}
          </tr>
  </thead>
  <tbody>

      {#each sortedData as footprint}
    <tr>
      <td class="id">{footprint.id}</td>
      <td class="country">{footprint.country}</td>
      <td class="company">{footprint.company}</td>
      <td class="footprint">{footprint.footprint}</td>
    </tr>
      {/each}

  </tbody>
</table>
</div>
</main>

<style>

.header-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      margin-top: 120px; /* Abstand vom Header */
      padding: 20px;
      
  }

.table-container {
      height: 400px;
      max-height: fit-content;
      min-height: 400px;
      max-width: 700px;
      overflow-y: auto;
      border: 2px solid #ddd;
      justify-content: center;
      margin: 10px auto;           
  }

  table {
      border-spacing: 0;
      width: 100%;
      border: 1px solid #ddd;
      border-collapse: collapse;
  }

  th, td {
      border: 1px solid #ddd;
      padding: 8px;
      text-align: left;
      column-width: 100px;
      
  }

  th {
      background-color: #f2f2f2;
      text-transform: uppercase;
      cursor: pointer;
      position: sticky;
      top: 0;
      z-index: 2;
  }

  .higlighted {
      font-weight: bold;
      background-color: rgb(202, 230, 243);
      
  }

  th:hover {
      cursor: pointer;
  }

  tr:nth-child(even) {
      background-color: #f2f2f2;
  }

  div.filter-container {
      display: flex;
      justify-content: center;
      margin-bottom: 1rem;
  }

  td.id {
      min-width: 70px;
  }

  td.country {
      width: 150px;
  }
  
  td.company {
      width: 150px;
  }

  td.footprint {
      width: 150px;
  }

  .search-box {
      width: 300px;
      padding: 10px;
      margin: 10px;
      border-radius: 10px;
      border: 1px solid #ddd;

  }

  .order-icon {
      background: none;
      border: none;
      color: black;
      font-size: 20px;
      cursor: pointer;
  }

  .order-icon:hover {
      color: black;
  }

</style>