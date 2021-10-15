<template>
  <div class="product-card">
  <img
      :src="imgUrl"
      alt="img"
  >
  <div class="product-card__info">
    <h2>{{title}}</h2>
    <p>{{price}}</p>
    <p>Доступно для доставки: {{count}}</p>
    <button
    @click="addToBuscet"
    >Добавить в корзину</button>
  </div>
  </div>
</template>

<script>
export default {
  name: "product-card",
  props: {
    title: {
      type:String,
      validator(value){
        return value.length < 10
      }
    },
    price: Number,
    imgUrl: {
      type:String,
      default: "https://images.unsplash.com/photo-1632948106892-51f19b00fbcd?ixid=MnwxMjA3fDB8MHxlZGl0b3JpYWwtZmVlZHwzfHx8ZW58MHx8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60",
    },
    count:{
      type:Number,
      default: 0,
    },
},
  data(){

  },
  methods: {
    addToBuscet(){
      this.$emit("addToBuscet")
    }
  }
}
</script>

<style scoped>
.product-card{
  display: flex;
  flex-direction: column;
  margin: 50px 0 0 0;
  min-height: 500px;
  border: 1px solid midnightblue;
  padding: 20px;

}
.product-card__info{
  display: flex;
  flex-direction: column;
}
.product-card button{
  margin: auto 0 0 0;
}
.product-card img{
  max-height: 200px;
  width: 100%;
}
.product-card__info{
  flex: 1;
}
.product-card__info button{
  background: crimson;
  border-radius: 5px;
  min-height: 60px;
  text-transform: uppercase;
  font-size: 15px;
  font-weight: bold;
  color: white;
cursor: pointer;
  transition: all .2s ease-in-out;
}
.product-card__info button:hover{
  background: deeppink;
}
</style>