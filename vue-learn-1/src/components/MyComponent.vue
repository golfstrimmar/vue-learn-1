<template>
<div class="root">

  <div class="fio">
    <h2

    >
      {{getAuterFoolName}}

    </h2>
    <ul >
      <li
          v-for="(value, key, index) in users[0]"
          :key="index"
      >
<!--        {{getFullName(user)}}-->

        {{value}}
      </li>
    </ul>



    <button
        type="button"
        @click="currentPage--"
    >Пред.</button>

    <button
        type="button"
        v-for="page in pages"
        :key="page"
        @click="currentPage = page"
    >
      {{page}}
    </button>


    <button
        type="button"
        @click="currentPage++"
    >След.</button>

<p>Страница {{currentPage}}из {{pages}}</p>
  </div>


 <label>
   Bведите email
   <input
       type="email"
       :value="email"
      @input="emailInput"
   />
   {{email}}
 </label>
  <label>
   Bведите пароль
   <input type="password" :value="pass"/>
    {{pass}}
 </label>

  <div class="minmax">
    <button class="dec" @click="decrMinmax">-</button>
    <input
        type="text"
        :value="minmax"
    >
    <button class="ink" @click="incMinmax">+</button>
  </div>

<!-- дз2-->
  <div class="dz">
    <h3>Я найду тебя!</h3>
    <input
        type="text"
        :value="name"
        @input="searchText = $event.target.value"
    >
    <span>Всего имен: {{names.length}}</span>
    <span>, совпадений: {{getFilteredNames.length}}</span>
    <ul>
    <li
        v-for="(name,index) in getFilteredNames"
        :key="index"
    >{{name}}</li>
    </ul>
  </div>
<!--/ дз2-->


<div class="logo">

<div class="img-wrapper"
style=""
     v-if="isCatVisible"
    :class="imgFilters"
>
  <img
      src="@/assets/logo.png"
      alt=""
      :class="imgFilters"
      :style="imgStyles"

  >
</div>

  <p v-else>кот скоро вернется</p>
  <div class="controls">
<h1>Шаверма кот</h1>
    <button
        type="button"
        @click="imgFilters.shadow =!imgFilters.shadow"
    >Тень блока</button>
    <label>
      {{imgSizez.currentWidth}}
    <input
        type="range"
        :value="imgSizez.currentWidth"
        @input="imgSizez.currentWidth = $event.target.value"
        :min="imgSizez.minWidth"
        :max ="imgSizez.maxWidth"
    >
    </label>
    <input
        type="range"
        :min="imgSizez.minHeight"
        :max ="imgSizez.maxHeight"
    >


    <label >
      <span>угол поворота:</span>
      {{imgSizez.currentRotate}}
      <input
        type="range"
        :value="imgSizez.currentRotate"
        @input="imgSizez.currentRotate = $event.target.value"
        :min="imgSizez.minRotate "
        :max ="imgSizez.maxRotate"
      >
    </label>

    <button
    type="button"
    @click="isCatVisible=!isCatVisible, isSpanVisible=!isSpanVisible"

    >
      <span
      v-if="isSpanVisible"

      > Показать</span>
      <span
          v-if="!isSpanVisible"
      > Спрятать</span>

    </button>
  </div>
</div>

</div>
</template>

<script>
export default {
  name: "my-component",
  data(){
    return {
      email: 'exs@gmail.com',
      pass: "111111111",
      minmax: 1,
      firstName: 'victor',
      lastName: 'yushin',
      users:[
        {
          id: "1",
          firstName: "firstName-1",
        lastName: "lastName-1"
        },
        {
          id: "2",
          firstName: "firstName-2",
        lastName: "lastName-2"
        },
        {
          id: "3",
          firstName: "firstName-3",
        lastName: "lastName-3"
        },
      ],
      names:[
        'Василий',
        'Петр',
       'Данил',
        'Григорий'
      ],
      pages: 3,
      currentPage:3,
      coincidences: 4,
      searchText: '',
      isCatVisible: "true",
      imgFilters:{
        sepia: false,
        border: false,
        shadow: false
      },
      isSpanVisible: true,
      imgSizez:{
        maxWidth: 680,
        maxHeight: 480,
        currentWidth: 680,
        minRotate:0,
        maxRotate: 360,
        currentRotate: 0,
        currentHeight: 480
      },
      imgRotate: 0
    }
  },

  methods:{
    emailInput(event){
      this.email = event.target.value
    },
    decrMinmax(event){
      if(0<this.minmax ){
        this.minmax--
      }else{
        return
      }
    },
    incMinmax(event){
      if(this.minmax<=9){
        this.minmax++
      }else {
        return
      }
    },
    getFullName(user){
    return  user.id + " " + user.firstName + " " +user.lastName
    },
    loadUsers(page){
console.log(`Загрузка пользователей: страницы ${page}`);
    }
  },
  computed:{
    getAuterFoolName(){
    return  this.firstName.toUpperCase()+' '+ this.lastName.toUpperCase()
    },
    getFilteredNames(){
      return this.names.filter(name => name.toLowerCase().includes(this.searchText.toLowerCase()))
    },
    imgStyles(){
      return{
        width: `${this.imgSizez.currentWidth}px`,
        transform: `rotate(${this.imgSizez.currentRotate}deg)`
      }
    }
  },
  watch: {
    currentPage(page){
      this.loadUsers(page)
    }
  }
}
</script>

<style scoped>
.logo{
  justify-content: center;
  display: grid;
  grid-template-columns: 40% 1fr;
}
label{
  display:block;
}

.img-wrapper{
  background: burlywood;
  flex: 0 1 50%;
  box-sizing: border-box;
}

.shadow-span  {
  display: none;
}

.img-wrapper .shadow{
  box-shadow: 0 0 8px darkred;
}
</style>