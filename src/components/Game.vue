<template>
    <div class="container">
        <div class="box" :class="{boxSel:num===1}" @click='event1(1)'>
        </div>
        <div class="box" :class="{boxSel:num===2}" @click='event1(2)'>
        </div>
        <div class="box" :class="{boxSel:num===3}" @click='event1(3)'>
        </div>
    </div>
    <div class="container">
        <div class="box" :class="{boxSel:num===4}" @click='event1(4)'>
        </div>
        <div class="box" :class="{boxSel:num===5}" @click='event1(5)'>
        </div>
        <div class="box" :class="{boxSel:num===6}" @click='event1(6)'>
        </div>
    </div>
    <div class="container">
        <div class="box" :class="{boxSel:num===7}" @click='event1(7)'>
        </div>
        <div class="box" :class="{boxSel:num===8}" @click='event1(8)'>
        </div>
        <div class="box" :class="{boxSel:num===9}" @click='event1(9)'>
        </div>
    </div>
</template>
<script>




export default {
  
  data()
  {
    return{
        num: Math.floor(Math.random() * 9) + 1
    }
  },
  methods:
  {
    event1(x)
    {
       if(x===this.num)
        {
            this.$emit('stop')
        }
    }

  }
  
  
  
}
</script>

<style>

.container
{
    display: flex;
    justify-content: space-around;
    margin: 20px;
}
.box
{
    height:200px;
    width:30%;
    background-color: rgb(255, 255, 255);
}
.boxSel
{
    height:200px;
    width:30%;
    background-color: rgb(130, 243, 149);
}
</style>