<template>
  <div id="app">
    <navbar />
    <div class="container">
      <div class=" card card-body">
        <h1> usuarios github</h1>
        <p class="lead">
          procure usuarios pelo nome  
        </p>
        <input @keyup="getUser" id="search" type="text" class="form-control" required/>
      </div>
      <div class="row" v-if="user.length !== 0">
        <div class=col-md-4>
          <folder :user="user"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import navbar from './components/navbar.vue';
import axios from 'axios';
import folder from './components/folder.vue'
  export default{
    name:'app',
    data(){
      return{
        github:{
          url:'https://api.github.com/users',
          client_id:'506f7f00eccefb966e50',
          client_secret:'9639ce0c38351ff784c1ef5527894c717a37dff2',
          count:7,
          sort: 'created: asc'
        },
        user: [],
        repos:[]
      };
    },
    components:{
      navbar,
      folder
    },
    methods:{
     getUser(e){
       const user = e.target.value;
       const {url, client_id, client_secret} = this.github;
       axios.get(
         `${url}/${user}?client_id=${client_id}&client_secret=${client_secret}` 
       ).then(({data}) => (this.user=data));
     } 
    }
  }

</script>
