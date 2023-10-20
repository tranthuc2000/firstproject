
<script setup >
import { ref,computed,onMounted } from 'vue'
import Controls from './components/Controls.vue'
import Players from './components/Players.vue'
import Dices from './components/Dices.vue'
import PopupRule from './components/PopupRule.vue'
const isStart = ref(false)
const finalScore = ref(200)
const isWiner = ref(0)
const isActive = ref(true)
const diceScore = ref([0,0])
const playerScore = ref([0,0])
const current = ref(0)
const checkst = () => {
  isStart.value = !isStart.value
  reset()
}
const reset=() =>{
  isWiner.value = 0
  isActive.value = true
 diceScore.value = [0,0]
 playerScore.value = [0,0]
current.value = 0
}
const checkroll = () =>{

  if(isStart.value == false ){
    alert("Please click New Game")
    console.log(isStart)
  }

  if(isStart.value == true){
  let dice1 = Math.round(Math.random()*5)+1
  let dice2 = Math.round(Math.random()*5)+1
  console.log(dice1,dice2)
  diceScore.value[0] =dice1
  diceScore.value[1] =dice2
  if(dice1 == 1|| dice2== 1){
    setTimeout(() =>{
      alert("Rat tiec ban da bi mat luot ")
    },10)
    
    current.value = 0

    isActive.value = !isActive.value
  }
  else{
  
  current.value = dice1+dice2
  }
  }
}
const checkhold = () =>{
  if(isStart.value == false ){
    alert("Pls click New Game")
  }
  else{  
  let clone = [...playerScore.value]
  console.log(clone)
  if(isActive.value && isStart.value){
    clone[0] += current.value
  }
  if(!isActive.value){
    clone[1] +=current.value
  }
  console.log(clone)

  current.value = 0

  playerScore.value =[...clone]

  isActive.value = !isActive.value

  checkwin()
}
  }

const checkwin = () =>{
  if(playerScore.value[0] >=finalScore.value)
  {
    isWiner.value = 1;
    isStart.value = false;
  }
  else if(playerScore.value[1]>=finalScore.value){
    isWiner.value = 2;
    isStart.value = false
  }
}
</script>
<template>
  <div class="wrapper clearfix">
    <Players :playerScore="playerScore" :Current="current" :is-active="isActive" :is-winer="isWiner"/>

    <Controls @checkstart="checkst" :isStart="isStart" @checkroll="checkroll" @checkhold="checkhold" v-model:finalScore="finalScore" />{{ finalScore }}

    <Dices  :dice-score="diceScore"/>

    <PopupRule />
  </div>
</template>

