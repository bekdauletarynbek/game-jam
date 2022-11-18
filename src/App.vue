<template>
  <div style="position: relative; width: 600px; height: 600px; margin: auto;">
    <img class="user"
         style="position: absolute;
         width: 100px;
         height: 100px;"
         :src="pos"
         :style="[`top: ${top}px`, `left: ${left}px`, `transform: ${mirror ? 'scale(-1, 1);' : ''}`]"/>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      top: 0,
      left: 0,
      mirror: false
    }
  },
  computed: {
    pos() {
      return this.left % 2 === 0 ? require('@/assets/person.png') : require('@/assets/person-1.png')
    }
  },
  created() {
    window.addEventListener('keydown', this.toBottom)
    // window.addEventListener('mousemove', (e) => {
    //   console.log(e)
    // })
  },
  methods: {
    toBottom($event) {
      if($event.key === 'ArrowDown') {
        this.top += 10;
      }
      if($event.key === 'ArrowUp') {
        this.top -= 10;
      }
      if($event.key === 'ArrowLeft') {
        this.left -= 7;
        this.mirror = true;
      }
      if($event.key === 'ArrowRight') {
        this.left += 7;
        this.mirror = false;
      }
      console.log('to bottom', $event);
    },
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
}
body{
  background-image: url('https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQuoEVzkj_WJ4R3Gw7QmW5tgI615PhI_m_OkA&usqp=CAU');
  background-repeat: no-repeat;
  background-position: top;
  background-size: cover;
  width: 100vw;
  height: 100vh;
  margin: 0;
  padding: 0;
  overflow: hidden;
}
</style>
