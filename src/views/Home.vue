<template>
  <div>
    <h2>Ats API Getterss</h2>
    <div v-for="(p, id) in lista" :key="id">
      <p>{{p.name}}</p>
      <p>{{p.email}}</p>
      <!-- <p>{{p.body}}</p> -->
    </div>
     
  </div>
</template>
<script>

const axios = require('axios');

export default {
  name: "Home",
  data: function () {
    return {
      lista: {
        id: '',
        name: '',
        email: '',
        body: ''
      },     
    };
  },
  mounted() {
    this.getLista();
  },
  methods: {
    async getLista() {      
      const response = await axios.get('https://jsonplaceholder.typicode.com/posts/1/comments')
      if (response.status == 200) {
        this.lista = response.data;        
      }
      else {
       console.error('err');
        alert('DEU RUIM');
      }
    } 
  }  
};
</script>
