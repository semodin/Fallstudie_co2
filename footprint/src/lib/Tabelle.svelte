<script>
  import { onMount } from "svelte";
  import { writable } from "svelte/store";
  import { tableData } from "./tableData.js";


  let sortedData = tableData;
  let searchQuery = ""; // Suchfeld für Filterung
  let filteredData = tableData; // Neue gefilterte Daten
 
  //Get the headers of the table
  const tableHeaders = Object.keys(tableData[0]);
  let selectedHeader = "id";
  let ascendingOrder = true; 

  //Number sorting
  const sortByNumber = (tableHeaders) => {
    sortedData = sortedData.sort((obj1, obj2) => {
      return ascendingOrder ? obj1[tableHeaders] - obj2[tableHeaders] : obj2[tableHeaders] - obj1[tableHeaders];
    });
      selectedHeader = tableHeaders;
  };

  //String sorting
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

<!-- Suchfeld für die Filterung -->
<div class="filter-container">
  <input 
    type="text" 
    placeholder="Suchen..." 
    bind:value={searchQuery} 
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
          {@html ascendingOrder ? "&#9661;" : "&#9651;"}
      </button>
      {/if}
    
      </th>
      {/each}
          </tr>
  </thead>
  <tbody>

      {#each sortedData as footprint}
    <tr>
      <td>{footprint.id}</td>
      <td>{footprint.country}</td>
      <td>{footprint.company}</td>
      <td>{footprint.footprint}</td>
    </tr>
      {/each}

  </tbody>
</table>
</div>

<style>
.table-container {
    max-height: 400px;
    min-height: 400px;
    overflow-y: auto;
    min-width: 700px;
    max-width: 700px;
  }

  table {
      border-spacing: 0;
      width: 100%;
      border: 1px solid #ddd;
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
  }

  .higlighted {
      color: hsl(118, 100%, 45%)
  
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
</style>