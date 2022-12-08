<template>
<form @submit.prevent="Done">
  <input  type="text" v-model="search" placeholder="Create a new todo">
</form>
<div class="icon" v-for="(image,index) in database" :key="index">
  <h1 class="data"><span>{{image.name}}</span></h1>
 <button @click="Remove(index)"><span class="x">X</span></button>
</div>
<p class="items-left">{{database.length}} items left</p>
</template>

<script>

export default {
  data() {
    return {

      search:'',
      database: []
    }
  },
  methods: {
    Done() {
      if(this.search != ''){
        this.database.unshift({name : this.search});
        this.search = ''
      }
    },
    Remove(index) {
    this.database = this.database.filter((image,i) => i != index)
    }
  }
}

</script>

<style >
.icon .data {
 width: 45%;
   margin-top: 30px;
   border: 1px solid grey;
}
.icon {
  margin-left: 30%;
}
#app {
  text-align: center;
  margin-top: 60px;
}
input {
  padding: 15px 10px;
  width:50%;
}
button {
  outline: none;
  border: none;
  background-color: white;
  transform: translateY(-20px);
    font-size: 20px;
}
h1{
  font-size: 20px;
}
.items-left {
  text-align: center;
  margin-right: 46%;
}
* {
  overflow-x: hidden;
}
</style>
