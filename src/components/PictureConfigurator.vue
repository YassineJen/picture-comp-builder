<template>
  <div>
        <div class="settings text-center" >
            <div class="settings-title">
                <i class="fa-solid fa-sliders"></i> Settings
            </div>
            <div class="settings-panel">
              <text-panel-component v-if="selectedId === 0 || selectedId === 1"  :pictureElements="pictureElements"
            :selectedId="selectedId"></text-panel-component>
                        <image-panel-component :pictureElements="pictureElements" v-if="selectedId === 3"></image-panel-component>

            <bg-panel-component :pictureElements="pictureElements"  ></bg-panel-component>
            <button-panel-component :pictureElements="pictureElements" ></button-panel-component>
            </div>
        </div>
            </div>
  
</template>

<script>
import BgPanelComponent from './PictureConfiguratorComponents/BgPanelComponent.vue';
import ButtonPanelComponent from './PictureConfiguratorComponents/ButtonPanelComponent.vue';
import TextPanelComponent from "./PictureConfiguratorComponents/TextPanelComponent.vue";
import ImagePanelComponent from "./PictureConfiguratorComponents/ImagePanelComponent.vue";

export default {
  components: {
    TextPanelComponent,
    BgPanelComponent,
    ButtonPanelComponent,
    ImagePanelComponent,
  
  },

  props: {
    pictureElements: Array,
    selectedId:Number,
  },
  mounted() {
    this.pictureElementsCopy = this.pictureElements;
  },
  data() {
    return {
      pictureElementsCopy: 1,
    };
  },
};
</script>

<style>
.settings {
    height: 100vh;
    background: #2b2b33;
    text-align: left;
    color: white;
    overflow-y:auto;
}
.settings-title {
  background: #141217;
  text-transform: uppercase;
  padding: 4px;
  font-weight: bold;
  text-align: center;
  font-size: 16px;
  letter-spacing: 1px;
  border-bottom: 1px solid black;
}

.settings-panel {
  padding: 3px;
}



</style>