<script setup>
const name = "Vue dinamico";
const styleColor = "color:blue";
const arrayColores = ["blue", "red", "green"];
const activo = true;
//array para uso v-for
const arrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"];
//array de objetos para uso v-for
const arrayFrutas2 = [
  {
    name: "Manzana",
    price: "$1.00",
    description: "Una manzana",
  },
  {
    name: "Pera",
    price: "$2.00",
    description: "Una pera",
  },
  {
    name: "Naranja",
    price: "$3.00",
    description: "Una naranja",
  },
];
//objeto para uso v-for
const objetoFruta = {
  name: "Manzana",
  price: "$1.00",
  description: "Una manzana",
};
//array para uso v-for y v-if
const arrayFrutas3 = [
  {
    name: "Manzana",
    price: "$1.00",
    description: "Una manzana",
    stock: 0,
  },
  {
    name: "Pera",
    price: "$2.00",
    description: "Una pera",
    stock: 10,
  },
  {
    name: "Naranja",
    price: "$3.00",
    description: "Una naranja",
    stock: 20,
  },
];
//array para uso v-for anidado
const users = [
  {
    id: 1,
    name: "Juan",
    posts: [
      { id: 1, title: "Mi primer post" },
      { id: 2, title: "Mi segundo post" },
    ],
  },
  {
    id: 2,
    name: "Maria",
    posts: [
      { id: 3, title: "Mi tercer post" },
      { id: 4, title: "Mi cuarto post" },
    ],
  },
];
//metodo - methods
const handleClick = (message = 'nada') => {
  console.log(message);
};
</script>

<template>
  <h1>Hola {{ name.toUpperCase() }}</h1>
  <h2>{{ arrayColores }}</h2>
  <h2 :style="styleColor">soy azul</h2>
  <h2 :style="`color: ${arrayColores[0]}`">soy azul</h2>
  <h2>
    {{ activo ? "Estoy Activo" : "Estoy Inactivo" }}
  </h2>
  <!-- uso v-for en array-->
  <ul>
    <li v-for="(name, index) in arrayFrutas" :key="index">
      {{ name }}
    </li>
  </ul>
  <!-- uso v-for en array de objetos-->
  <ul>
    <li v-for="fruta in arrayFrutas2" :key="fruta.name">
      {{ fruta.name }} - {{ fruta.price }} - {{ fruta.description }}
    </li>
  </ul>
  <!-- uso v-for en objetos-->
  <ul>
    <li v-for="(value, propiedad, index) in objetoFruta" :key="index">
      {{ index }} - {{ propiedad }} : {{ value }}
    </li>
  </ul>
  <!-- uso v-for y v-if en arreglo-->
  <ul>
    <template v-for="item in arrayFrutas3" :key="item.name">
      <li v-if="item.stock > 0">{{ item.name }} - {{ item.price }}</li>
    </template>
  </ul>
  <!-- uso v-for anidado en arreglo-->
  <div>
    <h2>Lista de usuarios:</h2>
    <ul>
      <template v-for="(user, index) in users" :key="user.id">
        <li>
          <h3>{{ user.name }}</h3>
          <ul>
            <template v-for="(post, index) in user.posts" :key="post.id">
              <li>{{ post.title }}</li>
            </template>
          </ul>
        </li>
      </template>
    </ul>
  </div>
  <!-- Boton con evento sin parametros-->
  <button v-on:click="handleClick()">Activame 1</button>
  <button @click="handleClick()">Activame 2</button>
  <!-- Boton con evento con parametros-->
  <button v-on:click="handleClick('Texto 1')">Activame 1</button>
  <button @click="handleClick('Texto 2')">Activame 2</button>
</template>

<style>
h1 {
  color: red;
}
</style>
