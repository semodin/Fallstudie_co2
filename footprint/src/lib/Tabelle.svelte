// svelte-ignore options_renamed_ssr_dom
<script>
    import { onMount } from "svelte";
    import { writable } from "svelte/store";
    import { tableData } from "./tableData.js";
    //export const someProp; // Add any props if needed
  
    let sortedData = tableData;

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


    //Filtering


</script>

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
        overflow-y: auto;
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
    }

    th {
        background-color: #f2f2f2;
        text-transform: uppercase;
        cursor: pointer;
    }

    .higlighted {
        color: hsl(50, 100%, 45%)
    
    }

    th:hover {
        cursor: pointer;
    }

    tr:nth-child(even) {
        background-color: #f2f2f2;
    }
</style>