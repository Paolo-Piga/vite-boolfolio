<template>
    <div v-if="progetto">
      <h1>{{ progetto.name }}</h1>
      <p><strong>Tipo:</strong> {{ progetto.type }}</p>
      <p><strong>Tecnologie:</strong> {{ progetto.technologies.join(', ') }}</p>
      <p><strong>Descrizione:</strong> {{ progetto.description }}</p>
    </div>
    <div v-else>
      <p>Progetto non trovato!</p>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ProgettiDetailsView',
    data() {
      return {
        progetto: null
      };
    },
    created() {
      const projectId = this.$route.params.id;
  
      // Simuliamo una chiamata API per ottenere il progetto in base all'id
      fetch('https://jsonplaceholder.typicode.com/posts/' + projectId)
        .then(response => response.json())
        .then(data => {
          // Simulazione di un progetto specifico
          this.progetto = {
            id: data.id,
            name: `Progetto ${data.id}`,
            type: data.id % 2 === 0 ? 'Web App' : 'Mobile App',
            technologies: data.id % 2 === 0 ? ['Vue.js', 'Node.js'] : ['React Native', 'Firebase'],
            description: `Descrizione del progetto ${data.id}`
          };
        })
        .catch(error => {
          console.error("Errore nel recupero del progetto: ", error);
        });
    }
  };
  </script>