<template lang="">

<div class="w-screen h-screen flex flex-col justify-center items-center bg-black text-white">
  <div class="text-[64px] font-[600]">
    {{`${message} ${username}`}}
  </div>

  <button @click="changeName" class="bg-blue-800 px-5 py-3 rounded active:scale-95 duration-200 hover:opacity-75">Change name</button>
</div>

</template>
<script>
export default {
  data() {
    return {
      username: "Tom",
      message: `Hello`,
      arrayOfNames: []
    }
  },

  methods: {
    changeName(){
      let newUserName = this.arrayOfNames[Math.floor(Math.random() * this.arrayOfNames.length)]

      if(newUserName == this.username){
        newUserName = this.arrayOfNames[Math.floor(Math.random() * this.arrayOfNames.length)]
      }

      this.username = newUserName
    }
  },

  mounted(){
    fetch('src/assets/names.json')
    .then((response)=>{return response.text()})
    .then((data) => {this.arrayOfNames = JSON.parse(data)})
  }
}
</script>
<style scoped>
  
</style>