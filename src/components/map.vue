<template>
  <div>
    <div style="margin-bottom: 20px;">
      <label for="mapWidth">Ширина карты: </label>
      <input type="number" name="mapWidth" id="mapWidth" v-model.number="mapWidth">
      <label for="mapHeight">Высота карты: </label>
      <input type="number" name="mapHeight" id="mapHeight" v-model.number="mapHeight">
    </div>
    <div>
      <div v-for="y in mapHeight" :key="y" class="row">
        <div v-for="x in mapWidth" :key="x" class="cell" @click="changeLocation(x,y)">
          <span class="cellindex">{{x}},{{y}}</span>
          <div class="player" v-if="player.location[0] == x && player.location[1] == y">
            <img src="../assets/def_avatar.jpg" alt="" class="avatar">
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'mapApp',
  data(){
    return{
      mapWidth: 7,
      mapHeight: 7,
      player: {
        location:[4,3]
      }
    }
  },
  methods:{
    changeLocation(x,y){
      this.player.location = [x,y];
    }
  }
}
</script>
<style scoped>
.row{
  display: flex; 
  width: 100%; 
  justify-content: center;
}
.cell{
  border: 1px solid black;
  width: 100px;
  height: 100px;
  position: relative;
  display: flex;
  justify-content: center;
}
.cell:hover{
  background-color: antiquewhite;
}
.player{
  border: 2px solid red;
  border-radius: 50%;
  width: 70px;
  height: 70px;
  align-self: center;
}
.player:hover{
  width: 75px;
  height: 75px;
}
.avatar{
  border-radius: 50%;
  width: 70px;
  height: 70px;
}
.avatar:hover{
  width: 75px;
  height: 75px;
}
.cellindex{
  position: absolute;
  bottom: 0px;
  right: 0px;
  color: gray;
}
</style>