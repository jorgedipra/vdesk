<template>
  <div id="barra">
    <span id="contenedor_menu">
      <img
        id="menu"
        srcset="@/static/Pack/logo32.png"
        alt="menu"
        title="menu"
      />
    </span>
    <span id="hora">
      {{hora}}
    </span>
    
    
  </div>
</template>



<script>
export default {
  data() {
    return {
       hora: "-",
    };
  },
  head() {
    let time = this;
    time._time();
    setInterval(function(){ time._time(); }, 60000);
   
  },
  methods:{
    _time: function () {
      let hora = this.hora;
      const d = new Date();
      let h = "";
      let m = "";

      function addZero(i) {
        if (i < 10) {
          i = "0" + i;
        }
        return i;
      }

      h = addZero(d.getHours());
      m = addZero(d.getMinutes());
      h = (h > 12) ? (h-12 + ':' + m +' PM') : (h + ':' + m +' AM');
      this.hora=h;
    }
  }
};
</script>

<style>
:root {
  --main-bg-color: #1d1d27;
  --main-bg-color-hover: #383841;
  --main-txt-color: rgb(223, 207, 207);
}
#barra {
  background-color: var(--main-bg-color);
  position: fixed;
  bottom: 0;
  left: 0;
  height: 40px;
  width: 100%;
}
#contenedor_menu {
  background: var(--main-bg-color);
  border: solid 5px var(--main-bg-color);
  position: absolute;
  margin: -7px px;
  width: 40px;
  height: 40px;
  z-index: 4;
}
#contenedor_menu:hover {
  background: var(--main-bg-color-hover);
  border: solid 5px var(--main-bg-color-hover);
}
img#menu {
  display: block;
  margin: 2px auto;
  height: 25px;
  width: 25px;
}
#hora{
  color:var(--main-txt-color);
  position: absolute;
  right: 25px;
  bottom: 12px;
}
</style>