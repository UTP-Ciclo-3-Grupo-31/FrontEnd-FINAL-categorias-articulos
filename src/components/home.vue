<template>
  <div>
    <div class="container-fluid servicioContenedor">
      <div class="d-flex justify-content-center mt-4">
        <h2>Nuestros Servicios</h2>
        </div>
      <div class="row mt-md-5 mt-sm-5 mt-xs-5 cuadroServicio">
        <div
          v-for="(art, indice) of datos"
          :key="art.id"
          class="col-lg-6 col-xs-12 border "
           v-if="art.categoriaId === 1"
        >
          <div v-if="art.estado === 1">
            <div class="d-flex justify-content-center align-items-center">
              <div class="p-2" style="text-align: center;">
                <img class="iconoServicio"  :src="art.urlIcono" alt="">
                <h4>{{ art.nombre }}</h4>
                <p>
                  {{ art.descripcionCorta}}
                </p>
              </div>
            </div>
            <div class="d-flex container-fluid justify-content-end pb-2 mt-n2">
              <!-- <button type="button" class="btn btn-outline-info"> Info</button>  -->
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="container-fluid casoExitoContenedor">
      <div class="d-flex justify-content-center mt-4 ">
        <h2>Casos de Éxito</h2>
        </div>
      <div class="row mt-md-5 mt-sm-5 mt-xs-5 ">
        <div
          v-for="(art, indice) of datos"
          :key="art.id"
          class="col-lg-6 col-xs-12 border " 
          v-if="art.categoriaId === 2"
        >
          <div>
            <div class="d-flex justify-content-center align-items-center ">
              <div class="p-2">
                <img class="imgCasoExito"  :src="art.urlIcono" alt="">
                <p>
                   "{{ art.descripcion }}"
                </p>
                <p class="casoExito" >
                  <i>{{ art.descripcionCorta }}<br></i>
                  <b>{{ art.nombre }}</b>
                </p>
              </div>
            </div>
            <div class="d-flex container-fluid justify-content-end pb-2 mt-n2">
              <!-- <button type="button" class="btn btn-outline-info"> Info</button>  -->
            </div>
          </div>
        </div>
      </div>
    </div>


    <div class="container-fluid">
      <div class="row justify-content-center mb-5">
        <div v-for="miembro in team" :key="miembro.codigo" class="col mt-5">
          <div class="card text-white bg-dark">
            <div class="d-flex justify-content-center p-2">
              <img :src="miembro.image" />
            </div>
            <div class="card-body">
                <h3 class="card-title">{{miembro.nombre}}</h3>
                <p class="card-text">{{miembro.descripcion}}</p>
                <p class="card-text"><span>Rol: </span>{{miembro.rol}}</p>
                <p class="card-text"><span>Codigo: </span>{{miembro.codigo}}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<style scoped>
.iconoServicio{
 width: 13%;
}
.imgCasoExito{
 margin-left: 20%;
 margin-bottom: 5%;
}
.servicioContenedor{
  max-width: 80%;
}
.casoExitoContenedor{
  max-width: 80%;
}
.casoExito{
  text-align: center;
}

.cuadroServicio{
  padding:10px;
}
</style>

<script>
import axios from "axios";
export default {
  data() {
    return {
      datos: null,
      team: [
        {
          codigo: 1,
          nombre: "Sergio Vargas",
          descripcion:
            "Programador,vive en Bogotá, le gusta Jugar con electrónica, volar drones y le apasionan las motos",
          rol: "Desarrollador backend",
          image: "./img/team/Avatar1.png",
        },
        {
          codigo: 2,
          nombre: "Diego Lipez",
          descripcion:
            "Ingeniero electricista de la Universidad Industrial de Santander, nacido en Bucaramanga actualmente vive en Bogotá, le gustan las caminatas por el campo y jugar minecraft con su hija.",
          rol: "Desarrollador backend",
          image: "./img/team/Avatar2.png",
        },
        {
          codigo: 5,
          nombre: "Engie Lorena Hernandez",
          descripcion:
            "Bogotana, tecnologa en gastronomia de la Universitaria Agustiniana, creativa, vive en busqueda constante de conocimiento, casada tiene una hija, apasionada por el arte, vive en la ciudad de Bogota y le gusta explorar rincones gastronomicos poco conocidos de esta ciudad.",
          rol: "Desarrollador frontend",
          image: "./img/team/Avatar5.png",
        },
        {
          codigo: 3,
          nombre: "Jose del Valle",
          descripcion:
            "Ingeniero de Control de la Universidad Nacional de Colombia, nacido en Itagüí vive actualmente en Medellín le gusta jugar vídeo juegos.",
          rol: "Desarrollador backend",
          image: "./img/team/Avatar4.png",
        },
        {
          codigo: 4,
          nombre: "Esteban Durán",
          descripcion:
            "Ingeniero Químico de la Universidad de Antioquia, vive en Medellín, le gusta hacer deporte, leer y el cine.",
          rol: "Desarrollador backend",
          image: "./img/team/Avatar3.png",
        },
      ],
    };
  },
  mounted() {
    axios.get("articulo/list").then((response) => (this.datos = response.data));
  },
};
</script>