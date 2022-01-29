<template>
  <div id="app">
    <nav class="navbar navbar-dark bg-primary">
      <a href="/" class="navbar-brand"> Preventas </a>
    </nav>
    <!-- Contenido Principal -->
    <div class = "container">
      <div class = "row mt-5">
        <div class = "col-sm-4">
          <div class = "card">
            <div class = "card-header">
              <h3>Agregar un Producto</h3>
            </div>
            <div class = "card-boy">
              <form action="index.html" method="post">

              </form>
            </div>
          </div>
        </div>
        <div class = "col-sm-8 text-center">
        <!--<img src="./assets/logo.png">-->
        <div class = "card">
          <div class = "card-header">
            <h3>Lista de productos</h3>
          </div>
          <div class = "card-body">
            <table class="table table-striped table-bordered">
              <thead>
                <tr>
                  <th>Producto</th>
                  <th>Marca</th>
                  <th>Tipo</th>
                  <th>Cantidad</th>
                  <th>Precio</th>
                </tr>
              </thead>
              <tbody>
                  {{productosX}}
              </tbody>
            </table>
          </div>   
        </div>
        </div>
      </div>
    </div>
    
  </div>
</template>
<script>
import { initializeApp } from 'firebase/app';
import { getDatabase , ref, onValue } from "firebase/database";
 import config from './config';
 const app = initializeApp(config);

// Get a reference to the database service
const database = getDatabase(app);
const starCountRef = ref(database, '/productos');
onValue(starCountRef, (snapshot) => {
  const data = snapshot.val();
  //console.log(data);
  //updateStarCount(postElement, data);
});

//  let app = Firebase.initializeApp(config);
//  let db = Firebase.database().ref("/productos");
 //let preventasRef = db;
 console.log(database);

//const dbref=firebase.database().ref().child('usuarios');
export default {
  name: 'App',
  // components: {
    
  // }
  // firebase:{
  //   productos: data
  // }, 
   data:()=>{
     return { 
        productosX: []
     }
   },
   methods: {
     obtenerProd(){
       console.log("asdads");
       onValue(starCountRef, (snapshot) => {
        this.productosX = snapshot.val();
      //const data = snapshot.val();
      //console.log(data);
      //updateStarCount(postElement, data);
      });
    },
    mounted(){
      this.obtenerProd();
    }
   }
}
</script>

<style>
/* #app {
  
} */
</style>
