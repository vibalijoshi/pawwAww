<template>
<v-app>
  <span class="bg"></span>
  <v-layout row >
    <v-flex class="flat">
      <v-card>
        <v-toolbar color="red" dark>
          <v-toolbar-items class="head" >r/aww</v-toolbar-items>

          <v-spacer></v-spacer>
        </v-toolbar>

        <v-list two-line class="hoo" >
     
          <template v-for="(post, index) in posts">

            <v-divider
              v-if="true"
              :key="index"
              :inset="true"
            ></v-divider>
            <v-layout row :key="post.data.url" @click="openImage(post.data.permalink)">
              <v-list-item-avatar class="avta" size= 150  :key="post.data.url">
                <img :src="post.data.thumbnail">                
              </v-list-item-avatar>

             <v-list-item-content :key="post.data.awards">
                <v-list-item-title class="titlee" v-html="post.data.title"></v-list-item-title>
                <!-- <v-btn @click="openImage(post.data.preview.images[0].source.url)">click me</v-btn> -->
              </v-list-item-content>
             

            </v-layout>
            
          </template>
        </v-list>
      </v-card>
    </v-flex>
  </v-layout>
  </v-app>
</template>

<script>
const axios = require("axios");

  export default {
    name: 'HelloWorld',
    data (){
      return{
        posts: [],
      }

    },
    created(){
      axios.get("https://reddit.com/r/aww.json")
      .then(response=> {
        this.posts = response.data.data.children
      })
      .catch(error=> {
        console.log(error)
      })
    },
    methods: {
      openImage(image){
        window.open('https://www.reddit.com/'+image, "_blank");
        //post.data.preview.images[0].source.url
      }
    }

    
  }
</script>
<style scoped>
.head{
  font-size: 3rem;
  font-family: 'Courier New', Courier, monospace;
}
.flat{
  padding: 0 10%;
}
.avta{
  padding: 10%;
}
img {
  border: 5px solid #ff0000;
}
.titlee{
  font-size: 100%;
  font-family: Arial, Helvetica, sans-serif;
}
.bg{
  
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    background: url( 'https://wallpaperaccess.com/full/2222650.jpg') no-repeat center center;
    background-size: cover;
    background-color: red;
    transform: scale(1.1);
  }
  .hoo{
    cursor: pointer;
  }
  .hoo :hover{
    background-color:#454a46;
  }

</style>
