<template>
    <div>
      <h1>Progetti</h1>
      <ul>
        <li v-for="progetto in progettiView" :key="progetto.id">
          {{ progetto.name }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ProgettiView',
    data() {
      return {
        progettiView: []
      };
    },
    created() {
      // Chiamata API per i progetti
      fetch('https://jsonplaceholder.typicode.com/posts')
        .then(response => response.json())
        .then(data => {
          // Simuliamo che ogni progetto abbia un id e un nome
          this.progetti = data.map(item => ({
            id: item.id,
            name: item.title
          }));
        })
        .catch(error => {
          console.error("Errore durante il recupero dei progetti: ", error);
        });
    }
  };
  </script>