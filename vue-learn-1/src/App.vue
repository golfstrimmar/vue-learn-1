<template>
  <div id="app">
    <div class="container">

<sign-up></sign-up>

      <my-form></my-form>



      <my-component></my-component>



      <ul class="products">
      <li
          v-for="(product, index) in products"
          :key="index"
      >
  <product-card
  :title = "product.title"
  :price = "product.price"
  :imgUrl = "product.imgUrl"
  :count = "product.count"
  @addToBuscet="addToBuscet(index)"
  ></product-card>
      </li>
    </ul>

<!-- поиск-->
    <div class="top-information"></div>
    <h2>письменные столы</h2>
 <my-input
 v-model="searchText"
 />
    {{searchText}}
    <button>найти </button>
<!---------->
    <search @search="searchProduct">
    </search>
  </div>
  </div>
</template>

<script>
import  MyComponent from "@/components/MyComponent"
import  productCard from "@/components/productCard"
import  MyInput from "@/components/MyInput"
import  search from "@/components/search"
import  MyForm from "@/components/my-form"
import  SignUp from "@/components/SignUp"
export default {
  name: 'App',
  components: {
    MyComponent,
    productCard,
    MyInput,
    search,
    MyForm,
    SignUp
  },
  data(){
    return {
      searchText: '',
      products:[
        {
          title: 'Стол Jim',
          price: 19999,
          imgUrl: 'https://images.unsplash.com/photo-1632920663183-03c464fa58c8?ixid=MnwxMjA3fDB8MHxlZGl0b3JpYWwtZmVlZHw0fHx8ZW58MHx8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60',
          count: 20
        },
        {
          title: 'Стол Monako',
          price: 17778,
          imgUrl: 'https://images.unsplash.com/photo-1632884333982-e3b4f9fddd0e?ixid=MnwxMjA3fDB8MHxlZGl0b3JpYWwtZmVlZHw5fHx8ZW58MHx8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60',
          count: 25
        },
        {
          title: 'Стол с двумя ящиками',
          price: 10200,
          imgUrl: 'https://images.unsplash.com/photo-1497215728101-856f4ea42174?ixid=MnwxMjA3fDF8MHxlZGl0b3JpYWwtZmVlZHwxMXx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60',
          count: 23
        },
      ]
    }
  },
  methods:{
    addToBuscet(index){
    },
    searchProduct(searchText){
      console.log(searchText);
    }
  }
}
</script>

<style>
*{
  text-decoration: none;
  list-style: none;
}
ul,li{
  margin: 0 0 0 0;
  padding: 0 0 0 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.container{
  max-width: 1400px;
  border: 1px solid coral;
  margin: 0 auto;
}
.products{
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(346px, 1fr));
  justify-content: space-between;
  column-gap: 30px;
}
</style>
