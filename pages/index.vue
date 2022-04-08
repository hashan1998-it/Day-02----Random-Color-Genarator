<template>
  <div
    class="wrapper d-flex justify-content-center align-items-center"
    :style="cssVarWrapper"
  >
    <div class="base-container text-center">
      <h1>Random Hex</h1>

      <span class="hex-code" :style="cssSpanVar">
      <span v-if="colorCode == '' " style="fontSize:1.5rem; color:aqua; transition: all 0.5s ease-in;">Press the button to get random colors</span>
      <span v-else style="-webkit-text-stroke: 0.2px black;">#</span>
      <span class="color-text">{{ colorCode }}</span>
      </span>

      <hr :style="{ backgroundColor: cssSpanVar.color }" />
      <button class="btn btn-primary" @click="flip">Genarate</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      colorCode: '',
    }
  },
  computed: {
    cssVarWrapper() {
      return {
        background: '#' + this.colorCode,
      }
    },
    cssSpanVar() {
      return {
        color: '#' + this.colorCode,
      }
    },
  },
  methods: {
    flip() {
        this.colorCode = Math.random().toString(16).substring(2, 8)
        console.log('#' + this.colorCode)
      }
  },
}
</script>
<style scoped>
:root {
  --primary: #6200ee;
  --secondary: #018786;
  --buttonWidth: 100px;
}
.wrapper {
  width: 100%;
  height: 100vh;
  transition: background-color 0.5s ease-in;
}
.wrapper .base-container {
  /* From https://css.glass */
background: rgba(255, 255, 255, 0.42);
border-radius: 16px;
box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
backdrop-filter: blur(15.8px);
-webkit-backdrop-filter: blur(15.8px);
border: 1px solid rgba(255, 255, 255, 0.36);
  max-width: 900px;
  padding: 30px;
  border-radius: 5px;
  ;
}
.wrapper .base-container > * {
  margin-bottom: 20px;
  transition: all 0.2s
}
.wrapper .base-container span {
  font-size: 4rem;
}
.wrapper .base-container h1 {
  margin-bottom: 40px;
  color: #fff;
  font-size: 2rem;
 
}
.wrapper .base-container .color-text{
  transition: color 0.3s ease-in;
   -webkit-text-stroke: 0.2px black;
}

.wrapper .base-container button {
  background: var(--secondary);
  width: 110px;
}

@media screen and (max-width: 590px){
  h1 , span{
    font-size:1.5rem !important;

  }

}

</style>
