<template>
  <div>
    <h1 class="titulo">
      Tienda virtual de ciclismo <a href="#" class="bx bxs-cart"></a>
    </h1>
    <div class="container-sm">
      <header class="header">
        <div class="logo" ><h1 class="titulo" Tienda virtual de ciclismo  href="#" ></h1></div>
      </header>
      <div class="container-sm1">
        <div class="content1">
          <h2 class="buscador">¿Qué deseas buscar?</h2>
          <input
            type="text"
            class="input"
            placeholder="busca cualquier accesorio"
          />
        </div>
      </div>
      <div class="container-sm11">
        <div class="iconos"></div>
      </div>
    </div>

    <div class="contenedor">
      <h1>Tienda virtual de ciclismo</h1>
      <div class="box-contaier">
        <div v-for="(producto, index) in listaProductos" :key="index" class="box">
          <div class="imagen">
            <img :src="producto.imagenSrc" alt="" />
          </div>
          <div class="content">
            <div class="estrellas">
              <i
                class="bx bxs-star"
                v-for="star in producto.estrellas"
                :key="star"
              ></i>
              <i class="bx bxs-star-half"></i>
            </div>
            <h3>{{ producto.nombre }}</h3>
            <p>{{ producto.descripcion }}</p>
            <span>{{ producto.precio }}</span>
          </div>
          <a href="#" class="btn-pe" @click="abrirModal(producto)">Agregar</a>
        </div>
      </div>
      <div class="modal" v-if="modalActivo">
        <div class="modal-contenido">
          <i class="bx bx-check-circle"></i>
          <p>Producto agregado al carrito</p>
          <a href="#" class="btn-modal" @click="cerrarModal">Continuar comprando</a>
          <a href="#" class="btn-pe">Agregar</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

import "boxicons/css/boxicons.min.css";
export default {
  data() {
    return {
      listaProductos: [
        {
          imagenSrc:
            "https://spirobicycles.com/cdn/shop/products/FredoomLtwoo11Velocidades_4_39c777fb-68a8-4c21-9819-c1818878319e.jpg?v=1681935457",
          estrellas: [1, 2, 3, 4],
          nombre: "bicicleta",
          descripcion: "despues coloco",
          precio: "$5.000.000",
        },
        {
          imagenSrc:
            "https://www.ciclismoafondo.es/uploads/s1/12/20/44/1/5c7d4b950de6941e51349429-casco-specialized-s-works-evade-w-angi-prueba.jpeg",
          estrellas: [1, 2, 3],
          nombre: "Producto 2",
          descripcion: "Descripción del Producto 2",
          precio: "$1.000.000",
        },
        {
          imagenSrc:
            "https://exitocol.vtexassets.com/arquivos/ids/724406-800-auto?v=637042878212430000&width=800&height=auto&aspect=true",
          estrellas: [1, 2, 3, 4],
          nombre: "Producto 3",
          descripcion: "Descripción del Producto 3",
          precio: "$20.000",
        },
        {
          imagenSrc:
            "https://http2.mlstatic.com/D_NQ_NP_775657-MCO69546633165_052023-O.webp",
          estrellas: [1, 2, 3, 4],
          nombre: "Producto 3",
          descripcion: "Descripción del Producto 3",
          precio: "$500.000",
        },
        {
          imagenSrc:
            "https://deportivosnomadas.com/3017-large_default/jersey-ciclismo-colombia-olimpico-azul.jpg",
          estrellas: [1, 2, 3, 4],
          nombre: "Producto 3",
          descripcion: "Descripción del Producto 3",
          precio: "$15.99",
        },
        {
          imagenSrc:
            "https://noticiclismo.com/wp-content/uploads/2020/06/Zapatillas-S-Work-Vent-3.jpg",
          estrellas: [1, 2, 3, 4],
          nombre: "Producto 3",
          descripcion: "Descripción del Producto 3",
          precio: "$15.99",
        },
        {
          imagenSrc:
            "https://megabikes.co/1393-large_megabikes/pedales-shimano-ultegra-pd-r8000.jpg",
          estrellas: [1, 2, 3, 4],
          nombre: "Producto 3",
          descripcion: "Descripción del Producto 3",
          precio: "$15.99",
        },
        {
          imagenSrc:
            "https://i.ebayimg.com/thumbs/images/g/jkkAAOSwIWFkhpW0/s-l640.jpg",
          estrellas: [1, 2, 3, 4],
          nombre: "Producto 3",
          descripcion: "Descripción del Producto 3",
          precio: "$15.99",
        },
        {
          imagenSrc:
            "https://ciclospecial.com/wp-content/uploads/2022/02/CARAMA%C3%91OLA-FLY.jpg",
          estrellas: [1, 2, 3, 4],
          nombre: "Producto 3",
          descripcion: "Descripción del Producto 3",
          precio: "$15.99",
        },
        {
          imagenSrc:
            "https://www.tradeinn.com/f/13775/137754966/campagnolo-par-ruedas-carretera-bora-wto-60-2-way-fit-carbon-disc-tubeless.jpg",
          estrellas: [1, 2, 3, 4],
          nombre: "Producto 3",
          descripcion: "Descripción del Producto 3",
          precio: "$15.99",
        },
        {
          imagenSrc:
            "https://img.redbull.com/images/c_limit,w_1500,h_1000,f_auto,q_auto/redbullcom/2021/5/27/vyj8s9gzsshtgrlptqtj/cross-country-racing-mountain-bike",
          estrellas: [1, 2, 3, 4],
          nombre: "Producto 3",
          descripcion: "Descripción del Producto 3",
          precio: "$15.99",
        },
        {
          imagenSrc:
            "https://savabike.co/images/virtuemart/product/coraza-continental-ultrasport-ii-23c-25c-28c-ruta.jpg",
          estrellas: [1, 2, 3, 4],
          nombre: "Producto 3",
          descripcion: "Descripción del Producto 3",
          precio: "$15.99",
        },
      ],
      modalActivo: false,
    };
  },
  methods: {
    abrirModal(producto) {
      this.modalActivo = true;
    },
    cerrarModal() {
      this.modalActivo = false;
    },
  },
};
</script>
  
  <style>
.box-contaier {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(28rem, 1fr));
  gap: 1.5rem;
}

.box-contaier .box {
  padding: 2.5rem;
  background: #b3b5b4;
  border-radius: 0.5rem;
  border: 0.1rem solid rgb(0, 0, 0, 0.2);
  box-shadow: var(--box-shadow);
  position: relative;
  overflow: hidden;
  text-align: center;
}

.box-contaier .box .bxs-heart:hover,
.box-contaier .box .bxs-show:hover {
  background: var(--green);
  color: #fff;
}

.box-contaier .box .bxs-heart,
.box-contaier .box .bxs-show {
  position: relative;
  top: 1.5rem;
  background: #000000;
  border-radius: 50%;
  height: 5rem;
  width: 5rem;
  line-height: 5rem;
  font-size: 2rem;
  color: var(--black);
}

.header i {
  color: white;
  font-size: 25px;
  margin-right: 150px;
}

.container-sm1 {
  position: relative;
  height: 600px;
  overflow: hidden;
}

.bxs-cart {
  z-index: 1;
  position: fixed;
  background-color: #7b7b7b;
}


.titulo{
  color: #b80000;
  position: fixed;
  z-index: 1;
}

.container-sm1::before {
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
  background-image: url("https://www.santandercycling.com/cdn/shop/files/la_mejor_ruta_de_santander_1.gif?v=1683680293&width=3840");
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  z-index: -1;
}
.content1 {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: flex;
  flex-direction: column;
  align-items: center;
}

.iconos {
  background-image: url("imagenes/bike.png");
}

.buscador {
  color: white;
  margin-bottom: 10px;
}

.input {
  width: 80%;
  padding: 10px;
}

.catalogo {
  text-align: center;
}
.btn-pe {
  display: inline-block;
  padding: 11px 130px;
  font-size: 16px;
  text-align: center;
  text-decoration: none;
  background-color: transparent;
  color: rgb(0, 0, 0);
  border: 2px solid #b80000;
  border-radius: 6px;
  cursor: pointer;
  margin-bottom: 5px;
}

h1 {
  font-size: 2.5rem;
  text-align: center;
  margin-top: 0rem;
  color: #b80000;
}

.box-contaier .box .bxs-heart {
  right: -15rem;
}

.box-contaier .box .bxs-show {
  left: -15rem;
}

.box-contaier .box img {
  height: 17rem;
  margin: 1rem 0;
}

.box-contaier .box h3 {
  color: var(--black);
  font-size: 2.5rem;
}

.box-contaier .box .strellas {
  padding: 1rem;
  color: rgb(205, 0, 0);
}

.box-contaier .box .strellas i {
  font-size: 1.5rem;
  color: var(--green);
}

.box-contaier .box span {
  color: var(--green);
  font-weight: bolder;
  margin-right: 1rem;
  font-size: 2.5rem;
}

.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal-contenido {
  background-color: white;
  padding: 2rem;
  border-radius: 10px;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.btn-modal {
  margin-top: 1rem;
  padding: 10px 20px;
  font-size: 16px;
  text-align: center;
  text-decoration: none;
  background-color: rgb(255, 0, 0);
  color: white;
  border-radius: 6px;
  cursor: pointer;
}
</style>