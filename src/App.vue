<template>
  <form   action="" class="form">
    <input v-model="input" type="text"  class="masageContent" placeholder="Введите коментарий">
    <button type="button" @click="addComment" class="add">Добавить</button>
    <p v-if="errorMasage">Обяхательно для заполнения</p>
  </form>
  <div class="coments">
    <div class="coment" v-for="com in comment" :key="com" >
      
      <p class=" text">{{ com.masage }}</p>
      <button @click="deleteComment(key)" class="delate">Удалить</button>
    </div>
  </div>
  <div v-if="success" class="success">
    <p>коментарий успешно удалён</p>
    <button @click="success=false">ОК</button>
  </div>
</template>

<script>
export default{
  data(){
    return{
      comment:[{masage:"foo"}],
      input:'', 
      errorMasage:false,
      success:false,
  };
  },
  methods:{
    addComment(){
      if(this.input.length!=0){
        this.errorMasage=false
        this.comment.push({masage:this.input});
        this.input=''
      }
      else{
        this.errorMasage= true
      }
    },
    deleteComment(key){
      this.comment.splice(key, 1)
      this.success= true
    }
  } 
}
</script>

<style>
*{
  margin: 0px;
  padding: 0px;
}
.form{
  height: 150px;
  border: 1px solid #7edaac;
}
.masageContent{
  margin: 40px;
  height:30px;
  width: 40%;
}
.coments{
  margin: 50px;
  border: 1px solid #7edaac; 
}
.coment{
  display: flex;
  justify-content: space-between;
  margin: 50px;
  border: 1px solid black; 
  height: 80px;
}
.delate{
  color: black;
  background: white;
  border: 1px solid #7edaac;
  height: 30px;
  margin: 10px;
}
.success{
  position:absolute;
 top:40%;
 left:45%;
 text-align: center;
 height: 100px;
 width: 200px;
 color: white;
 background-color: rgba(41, 28, 41, 0.671);
 border: 3px solid  #7edaac;
 border-radius: 10px;
}
</style>
