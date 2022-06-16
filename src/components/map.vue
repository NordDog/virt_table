<template>
  <div>
    <div style="margin-bottom: 20px;">
      <label for="mapWidth">Ширина карты: </label>
      <input type="number" name="mapWidth" id="mapWidth" v-model.number="mapWidth">
      <label for="mapHeight">Высота карты: </label>
      <input type="number" name="mapHeight" id="mapHeight" v-model.number="mapHeight">
    </div>
    <div>
      <div v-for="(y, yIndex) in mapMatrix" :key="yIndex" class="row">
        <div v-for="(x, xIndex) in y" :key="xIndex" class="cell" :class="{ active_cell: x===1 }" @click="changeLocation(xIndex, yIndex)">
          <div class="cellbtns">
            <input type="button" :value="x" @click="changeCellActiveStatus(xIndex, yIndex)">
          </div>
          <span class="cellindex">{{xIndex}},{{yIndex}}</span>
          <div class="player" v-if="player.location[0] == xIndex && player.location[1] == yIndex">
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
      },
      mapMatrix:[
        [1,1,1,1,1,1,1],
        [1,1,1,1,1,1,1],
        [1,1,1,1,1,1,1],
        [1,1,1,1,1,1,1],
        [1,1,1,1,1,1,1],
        [1,1,1,1,1,1,1],
        [1,1,1,1,1,1,1],
      ]
    }
  },
  methods:{
    changeLocation(x,y){
      this.player.location = [x,y];
    },
    changeCellActiveStatus(x,y){
      this.mapMatrix[y][x] = this.mapMatrix[y][x] ? 0 : 1;
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
  border: 1px solid white;
  width: 98px;
  height: 98px;
  position: relative;
  display: flex;
  justify-content: center;
}
.active_cell{
  border: 1px solid black !important;
}
.active_cell:hover{
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
.cellbtns{
  position: absolute;
  right: 0px;
  top: 0px;
}
</style>