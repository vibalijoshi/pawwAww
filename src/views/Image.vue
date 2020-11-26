<template>
<div>
  <h1>Image goes here</h1>
  <img :src="imageUrl" alt="image">
</div>


</template>

// <script>
// import { ipcRenderer } from 'electron';
// export default {
//   created() {
//     ipcRenderer.on('image', (event, arg) => {
//       this.imageUrl = arg
//     })
//   },
//   data() {
//     return {
//       imageUrl: ''
//     }
//   }
// }
// </script>

