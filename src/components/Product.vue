<template>
    <ul>
        <li class="productContainer">
            <h3> {{ titleFormat }} </h3>
            <img class="imageWidth" :src="image">
            <p>Prix Ttc: {{  prixTtc }}€ TTC </p>
            <p> Description : {{ description }} </p>
        </li>
    </ul>
</template>

<script>

export default {
    name: "Product",
    props: {
        title: String,
        description: String,
        price: Number,
        image: String
    }, 

    computed: {
        prixTtc: function(){
            return this.price * 1.20
        },
        titleFormat: function() {
            return (this.title.charAt(0).toUpperCase() + this.title.toLowerCase().slice(1) + "©️")
        }


  }
}
</script>

<style scoped>
.imgProduct {
    width: 120px;
}

li{
    list-style: none;
}

.productContainer {
    border: thick double #32a1ce;
}

.imageWidth {
    width: 160px;
}
</style>