<script >
import { createApp } from 'vue';
import HelloWorld from './components/HelloWorld.vue'
import Product from './components/Product.vue'

export default {
  components: {
    HelloWorld,
    Product
  },
  data() {
    return {
      tagline : 'Chez Papà tout est moins cher !!!',
      inActive : true,
      products : [],
      title: "",
      price: 0,
      description: "",
      image: "",
      oldProducts: 3,
    }
  },
  methods : {
    handleClick : function() {
      console.log("click detecté");
      this.inActive  ? this.inActive = false : this.inActive = true ;
    },
    addProduct: function(e) {
      console.log(e)
      this.products.push({
        title: this.title,
        description: this.description,
        price: this.price,
        image: this.image
      })
    },
    async getProducts() {
      await fetch('https://fakestoreapi.com/products')
          .then((response) => {
            if (response.ok) {
                return response.json();
            } else {
                throw 'Error getting products list'
            }
          })
          .then((data) => {
            console.log(data);
            this.products = data
          })
          .catch((error) => {

          })
    }
  },
  watch: {
    'products.length'(newProducts, oldProducts) {
      console.log(newProducts)
      console.log(oldProducts)
    }, 
  },
  mounted() {
      this.getProducts()
  }
}
</script>

<template>
  <HelloWorld msg="Votre Panier" />
  <p>{{ tagline }}</p>
  <br>
  <input type="text" v-model="tagline"  />
  <br>
  <button v-on:click="handleClick">Afficher Cours</button>
  <div class="container">
    <div class="containerForm">
      <form v-on:submit.prevent="addProduct">
          <label for="title">titre : </label>
          <input type="text" name="title" v-model="title"/>
          <br>
          <label for="price">prix :</label>
          <input type="number" name="price" v-model="price"/>
          <br>
          <label for="description">Description :</label>
          <input type="text" name="description" v-model="description" />
          <br>
          <label for="url">Lien Image :</label>
          <input type="text" name="url" v-model="image" />
          <br>
          <button>Submit</button>
      </form>
      <div>
          <p>Nouveau Titre : {{ title }}</p>
          <p>Description : {{ description }}</p>
          <p>Prix : {{ price }}</p>
          <p>Lien Image : {{ image }}</p>
      </div>
    </div>
    <div v-if="inActive">
      <Product 
        v-for = "(product, index) in products"
        :key = index
        :title="product.title"
        :price="product.price"
        :description="product.description"
        :image="product.image"
      />
    </div>
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

.inActive {
  display: none;
}

.container {
  display: flex;
  flex-direction: row;
}

.containerForm {
  display: flex;
  flex-direction: column;
}



</style>
