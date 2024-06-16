<template>
  <h1 v-if="!gameOn">
    Test Your Reaction Time: Be On Your guard. Click the first green rectangle you see
  </h1>
  <button @click='toggleGame' v-if="!gameOn"> Start Game</button>
  <game v-if="gameOn && !endScreen" @stop='stopTimer'/>
  <div v-if="endScreen">
    <h1>{{finalText}}</h1>
    <p>Your reaction time: {{interval}} milliseconds</p>
    </div>
</template>

<script>
import Game from './components/Game'

export default {
  
  name: 'App',
  components: {Game},
  data()
  {
    return{
      gameOn: false,
      startTime: Date.now(),
      stopTime: Date.now(),
      interval: 0,
      endScreen: false,
      finalText:"default"
    }
  },
  methods:
  {
    toggleGame()
    {
      this.gameOn=!this.gameOn
      this.startTime=Date.now()
    },
    stopTimer()
    {
      this.stopTime=Date.now()
      this.interval=this.stopTime-this.startTime
      this.endScreen=!this.endScreen
      if(this.interval<250)
      {
        this.finalText="You've gone supersonic"
      }
      if(this.interval<500&&this.interval>=250)
      {
        this.finalText="You have Cat like reflexes"
      }
      if(this.interval<750&&this.interval>=500)
      {
        this.finalText="that's fast"
      }
      if(this.interval<1000&&this.interval>=750)
      {
        this.finalText="Meh..."
      }
      if(this.interval>=1000)
      {
        this.finalText="Too slow...Snails pace"
      }
    }
  }
  
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.box1 
{
  top: 50%;
  left: 50%;
  height: 30%;
  width:30%;
  background: rgb(0, 238, 255);
}
.box2
{
  top: 0%;
  left: 0%;
  height: 30%;
  width:30%;
  background: rgb(0, 238, 255);
}
</style>
