<template>
<div>
    <input v-model="searchQuery" placeholder="Cari sesuatu..." />
    <p>Hasil pencarian: {{ searchResult }}</p>
</div>
</template>

<script>
export default {
    name: 'TestWatch',
    data() {
        return {
        searchQuery: '',
        searchResult: ''
        };
    },
    watch: {
        searchQuery(newQuery) {
          // Simulasi pencarian dengan delay
          this.searchResult = newQuery !== "" ? `Hasil untuk "${newQuery}"` : "";
        }
    }
  }
</script>

<!-- <template>
    <div>
      <p>Pesan terbalik (dengan methods): {{ reverseMessage() }}</p>
    </div>
  </template>
  
  <script>
  export default {
    name: 'TestWatch',
    data() {
      return {
        message: 'Halo, Vue!'
      };
    },
    methods: {
      reverseMessage() {
        console.log('Dihitung ulang');
        return this.message.split('').reverse().join('');
      }
    }
  };
  </script> -->