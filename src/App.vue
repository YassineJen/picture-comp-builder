<template>
  <div id="app">
    <div class="bgcolor container-fluid g-0">
      <div class="row g-0 h-100">
        <div class="col md-auto g-0 h-100">
          <picture-component 
            @updateData="updateData($event)"
            v-on:isFocused="getClickedElm($event)"
            :pictureElements="options.pictureElements"></picture-component>
    
        </div>
        <div class="col-lg-3 g-0 h-100">
          <picture-configurator 
            :pictureElements="options.pictureElements"
            :selectedId="options.clickedElm">
            </picture-configurator>
         
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import PictureComponent from "./components/PictureComponent.vue";
import PictureConfigurator from "./components/PictureConfigurator.vue";

export default {
  name: "App",
  components: {
    
    PictureComponent,
    PictureConfigurator
},

  data() {
    return {
      options:{
     
      clickedElm: 0,
      pictureElements: [
        {
          id: 0,
          txt: "This is a Title",
          underlineBool: false,
          boldBool: false,
          italicBool: false,
          strikeThroughBool: false,
          startBool: false,
          centerBool: true,
          endBool: false,
          txtcolor: "#FFFFFF",
          bgcolor: "#FFFFFF",
          fontSize: "fs-2",
          isHighlited:false
        },
        {
          id: 1,
          txt: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam semper facilisis ligula a euismod. Proin egestas sodales mi et tempus. Proin non dui pellentesque, pretium ante ut, feugiat sem. Morbi pellentesque nunc sed magna iaculis, id aliquet magna finibus. Ut arcu justo, auctor vitae lorem non, gravida ultricies ex. Morbi id urna nec lacus iaculis pellentesque eget sit amet metus. Ut id facilisis felis. Nulla tempus dui quam, eget ullamcorper leo rhoncus ac. Suspendisse a hendrerit nisi. Aenean et purus consequat, volutpat eros quis, imperdiet purus. Aenean vitae orci elementum, mattis tortor eleifend, bibendum est. Nulla congue hendrerit sapien at suscipit. Donec in nisi at sem tempor posuere. Vivamus eget ipsum sit amet enim posuere tristique.",
          underlineBool: false,
          boldBool: false,
          italicBool: false,
          strikeThroughBool: false,
          startBool: false,
          centerBool: true,
          endBool: false,
          txtcolor: "#FFFFFF",
          bgcolor: "",
          fontSize: "fs-5",
          lineHeight:"lh-base",
          isHighlited:false
        },
        {
          id:2,
          color:"#FFFFFF",
          opacity:1,
          selectedShape:0,
          isTop:false,
          waveStyle :[
        {
          id:0,
          shape:"M0,192L21.8,176C43.6,160,87,128,131,144C174.5,160,218,224,262,245.3C305.5,267,349,245,393,229.3C436.4,213,480,203,524,192C567.3,181,611,171,655,154.7C698.2,139,742,117,785,133.3C829.1,149,873,203,916,229.3C960,256,1004,256,1047,240C1090.9,224,1135,192,1178,192C1221.8,192,1265,224,1309,240C1352.7,256,1396,256,1418,256L1440,256L1440,320L1418.2,320C1396.4,320,1353,320,1309,320C1265.5,320,1222,320,1178,320C1134.5,320,1091,320,1047,320C1003.6,320,960,320,916,320C872.7,320,829,320,785,320C741.8,320,698,320,655,320C610.9,320,567,320,524,320C480,320,436,320,393,320C349.1,320,305,320,262,320C218.2,320,175,320,131,320C87.3,320,44,320,22,320L0,320Z"
        },
        {
          id:1,
          shape:"M0,192L0,0L1440,0L1440,320L0,320L0,320Z"
        },
        {
          id:2,
          shape:"M0,320L1440,0L1440,320L0,320Z"
        },
        {
          id:3,
          shape:"M0,96L1440,256L1440,320L0,320Z"
        },
        {
          id:4,
          shape:"M0,224L30,234.7C60,245,120,267,180,261.3C240,256,300,224,360,192C420,160,480,128,540,106.7C600,85,660,75,720,80C780,85,840,107,900,138.7C960,171,1020,213,1080,234.7C1140,256,1200,256,1260,250.7C1320,245,1380,235,1410,229.3L1440,224L1440,320L1410,320C1380,320,1320,320,1260,320C1200,320,1140,320,1080,320C1020,320,960,320,900,320C840,320,780,320,720,320C660,320,600,320,540,320C480,320,420,320,360,320C300,320,240,320,180,320C120,320,60,320,30,320L0,320Z"
        },
        {
          id:5,
          shape:"M0,64L48,58.7C96,53,192,43,288,42.7C384,43,480,53,576,80C672,107,768,149,864,160C960,171,1056,149,1152,149.3C1248,149,1344,171,1392,181.3L1440,192L1440,320L1392,320C1344,320,1248,320,1152,320C1056,320,960,320,864,320C768,320,672,320,576,320C480,320,384,320,288,320C192,320,96,320,48,320L0,320Z"
        }
      ]
        },
        {
          id:3,
          choosedSide: "to right",
          choosedColor1: "#651A6A",
          choosedColor2: "#D31B3D",
        },
        {
          id:4,
          buttons: [
            {
              btnText: 'Read More',
              btnLink: './more.html',
              btnTextColor: '#9f1b53',
              btnBgColor: "#FFFFFF"
            }
          ]
        },
        {
          id:5,
          imgAlt:"",
          imgShape:"sha-0",
          imgUrl:"https://www.immigrationfrancophone.ca/wp-content/uploads/2022/01/PNG-11.png"
        }
      ],


    }};
  },

  methods: {
    getClickedElm(IdValue) {
      this.options.clickedElm = IdValue;
    },
   
  },
};
</script>

<style>

.bgcolor{
  background: #3E3E46;
;
}
body{
  overflow: hidden;
  color:white;
}

</style>
