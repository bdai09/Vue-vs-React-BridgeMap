<template>
<div id="bridge-info-wrapper">
  <div v-if="bridge" id="info-panel">
   <h2 v-html="bridge.nameEncoded"></h2>

   <div class="bridge-stats">
     <div>Year: {{bridge.year}} ({{age}} years)</div>
     <div> Width: {{bridge.width}}m</div>
     <div>Length: {{bridge.length}}m</div>
     </div>
  </div>

    <leaflet-map id="leaflet-map" :location="bridge" />
 </div>
</template>

<style scoped>
#bridge-info-wrapper {
  display: flex;
  flex-direction: column;
  height: 100%;
}

#leaflet-map {
  flex: 5;
  height: 100%;
}

#info-panel {
  flex: 1;
  height: 100%;
  padding: .5em;

  background-color: #A6CC8B;
  color: #686950;
  border-bottom: solid 2px #686950;

  display: flex;
  flex-direction: column;
  justify-content: space-around;
  text-align: center;
}

#info-panel h2 {
  margin: .5em;
}

.bridge-stats {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  font-size: 1.3em;
}
</style>

<script>
import LeafletMap from './LeafletMap.vue';

export default {
    name: 'BridgeInfo',
    components: {LeafletMap},
    props:['bridge'],
    computed:{
        age:function(){
            return (new Date).getFullYear()-this.bridge.year;
        }
    }
}
</script>