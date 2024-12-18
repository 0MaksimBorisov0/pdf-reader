<script setup>
import { ref } from 'vue'
import { VuePDF, usePDF } from '@tato30/vue-pdf'
import file from "@/weihnachtsmaerkte.pdf"

const page = ref(1)
const { pdf, pages } = usePDF(file)

</script>

<template>
  <div class="wrapper">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <button class="navButton" @click="page = page > 1 ? page - 1 : page">
      <svg fill="#ffffff" height="18px" width="18px" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
           viewBox="0 0 330 330" xml:space="preserve">
<path id="XMLID_92_" d="M111.213,165.004L250.607,25.607c5.858-5.858,5.858-15.355,0-21.213c-5.858-5.858-15.355-5.858-21.213,0.001
	l-150,150.004C76.58,157.211,75,161.026,75,165.004c0,3.979,1.581,7.794,4.394,10.607l150,149.996
	C232.322,328.536,236.161,330,240,330s7.678-1.464,10.607-4.394c5.858-5.858,5.858-15.355,0-21.213L111.213,165.004z"/>
</svg>
    </button>
    <div class="mainContainer">

      <VuePDF :pdf="pdf" :page="page" fit-parent/>

    </div>
    <button class="navButton" @click="page = page < pages ? page + 1 : page">
      <svg fill="#ffffff" height="18px" width="18px" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
           viewBox="0 0 330.002 330.002" xml:space="preserve">
<path id="XMLID_103_" d="M233.252,155.997L120.752,6.001c-4.972-6.628-14.372-7.97-21-3c-6.628,4.971-7.971,14.373-3,21
	l105.75,140.997L96.752,306.001c-4.971,6.627-3.627,16.03,3,21c2.698,2.024,5.856,3.001,8.988,3.001
	c4.561,0,9.065-2.072,12.012-6.001l112.5-150.004C237.252,168.664,237.252,161.33,233.252,155.997z"/>
</svg>
    </button>
  </div>
</template>

<style>
*{
  padding:0;
  margin:0;
}

.navButton {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  background-color: #B92A2A;
  color: white;
  width: 42px;
  height: 42px;
  border-radius: 50px;
  border: none;
}
.wrapper{
  width:100vw;
  display:flex;
  justify-content:center;
  align-items: center;

}
.navButton:hover {
  background-color: #821C1C;
}

.mainContainer {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: row;;
  width:90%;
}

@media only screen and (max-width: 480px) {
  .navButton {
    background-color: #B92A2A;
    color: white;
    border: none;
  }
  .mainContainer{
    width:85%;
    height:100%;
  }
  .wrapper{
    height:100vh
  }
}
</style>