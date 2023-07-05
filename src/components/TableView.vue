
<template>
  <div class="export">
    <button @click="exportCSV($event)">CSV</button>
    <button>Excel</button>
    <button>Print</button>
    <button>PDF</button>
  </div>

  <input  class="search" v-model="filters['global'].value"  placeholder="Search" />
  <br><br>
  <div class="card">
      <DataTable v-model:filters="filters" :value="customers" ref="dt" paginator :rows="5" :rowsPerPageOptions="[5, 10, 20, 50]" tableStyle="min-width: 50rem" 
             :globalFilterFields="['company']">
          <Column field="name" header="Name" style="width: 25%"></Column>
          <Column field="country.name" header="Country" style="width: 25%"></Column>
          <Column field="company" filterField="company" header="Company" style="width: 25%"></Column>
          <Column field="representative.name" header="Representative" style="width: 25%"></Column>
      </DataTable>
  </div>
</template>

<script>
import Button from 'primevue/button';
import { FilterMatchMode } from 'primevue/api';
import { CustomerService } from './CustomerService';

export default {
  components: {
        Button,
    },
  data() {
      return {
          customers: null,
          filters: {
                global: { value: null, matchMode: FilterMatchMode.CONTAINS },
                company: { value: null, matchMode: FilterMatchMode.STARTS_WITH },
            },
      };
  },
  mounted() {
      CustomerService.getCustomersMedium().then((data) => (this.customers = data));
  },
  methods: {
        exportCSV() {
            this.$refs.dt.exportCSV();
        }
    }
  
};
</script>

<style>
.export {
  margin-left: 20px;
}
  button {
    background-color: skyblue;
    border: none;
    color: white;
    padding: 10px 20px;
    text-align: center;
    text-decoration: none;
    float :left;
    font-size: 15px;
    margin: 0px 15px;
    cursor: pointer;
    -webkit-transition-duration: 0.4s;
    transition-duration: 0.4s;
  }
  button:hover {
    box-shadow: 0 12px 16px 0 rgba(0,0,0,0.24), 0 17px 50px 0 rgba(0,0,0,0.19);
  }
  .search {
    float: right;
    margin-right: 40px;
    margin-top: 15px;
  }
  .p-datatable-table{
    width: 100%;
    height: 400px;
  }
  
  .card {
    background: var(--surface-card);
  }
</style>