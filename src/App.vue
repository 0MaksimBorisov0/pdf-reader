<script setup>
import { ref } from 'vue'
import { VuePDF, usePDF } from '@tato30/vue-pdf'
import file from "@/weihnachtsmaerkte.pdf"

const page = ref(1)
const { pdf, pages } = usePDF(file)

</script>

<template>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <div class="mainContainer">
    <VuePDF :pdf="pdf" :page="page" fit-parent/>
    <div class="buttonsContainer">
      <button class="navButton" @click="page = page > 1 ? page - 1 : page">
        Prev
      </button>
      <span class="pageNumbers">{{ page }} / {{ pages }}</span>
      <button class="navButton" @click="page = page < pages ? page + 1 : page">
        Next
      </button>
    </div>
  </div>
</template>

<style scoped>
.navButton {
  background-color: #B92A2A;
  color: white;
  width: 80px;
  height: 25px;
  border-radius: 8px;
  border: none;
}
.navButton:hover {
  box-shadow: 2px 2px 2px #821C1C;
}

.mainContainer {
  display: flex;
  align-items: center;
  flex-direction: column;
  background-color: #E1D4D4;

}
.buttonsContainer {
  margin-top: 20px;
  margin-bottom: 20px;
  display: flex;
  align-items: center;
  min-width: 230px;
  justify-content: space-between;
}

.pageNumbers {
  display: flex;
  align-items: center;
  flex-direction: column;
  color: #611515;
  font-weight: bold;
}

@media only screen and (max-width: 480px) {
  .navButton {
    background-color: #B92A2A;
    color: white;
    width: 100px;
    height: 42px;
    border-radius: 10px;
    border: none;
  }
  .buttonsContainer {

    display: flex;
    align-items: center;
    min-width: 320px;
    justify-content: space-between;
  }
}

</style>