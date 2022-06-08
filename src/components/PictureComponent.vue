<template>
  <div>
    <div class="preview">
      <div :style="changeBackground(pictureElements[3].choosedSide, pictureElements[3].choosedColor1, pictureElements[3].choosedColor2)" class="pic-component">
        <div class="container">
          <div class="header-content">
            <div class="row g-0">
              <div class="col-lg-6">
                <div style="margin-top: 26%"></div>
                <div @click="$emit('isFocused', 0)" contenteditable="true">
                  <div>
                    <p
                      :style="
                        updateCSS(
                          pictureElements[0].txtcolor,
                          pictureElements[0].bgcolor,
                          pictureElements[0].isHighlited
                        )
                      "
                      :class="[
                        {
                          'text-decoration-underline':
                            pictureElements[0].underlineBool,
                          'fst-italic': pictureElements[0].italicBool,
                          'fw-bolder': pictureElements[0].boldBool,
                          'text-start': pictureElements[0].startBool,
                          'text-center': pictureElements[0].centerBool,
                          'text-end': pictureElements[0].endBool,
                          'text-decoration-line-through':
                            pictureElements[0].strikeThroughBool,
                        },
                        pictureElements[0].fontSize,
                      ]"
                    >
                      Make your day happier
                    </p>
                  </div>
                </div>
                <div @click="$emit('isFocused', 1)" contenteditable="true">
                  <div class="resizeable">
                    <p
                      :style="
                        updateCSS(
                          pictureElements[1].txtcolor,
                          pictureElements[1].bgcolor,
                          pictureElements[1].isHighlited
                        )
                      "
                      :class="[
                        {
                          'text-decoration-underline':
                            pictureElements[1].underlineBool,
                          'fst-italic': pictureElements[1].italicBool,
                          'fw-bolder': pictureElements[1].boldBool,
                          'text-start': pictureElements[1].startBool,
                          'text-center': pictureElements[1].centerBool,
                          'text-end': pictureElements[1].endBool,
                          'text-decoration-line-through':
                            pictureElements[1].strikeThroughBool,
                        },
                        pictureElements[1].fontSize,
                        pictureElements[1].lineHeight,
                      ]"
                    >
                      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam semper facilisis ligula a euismod. Proin egestas sodales mi et tempus.Etiam semper facilisis ligula a euismod. Proin egestas sodales mi et tempus.
                    </p>
                  </div>
                </div>
                <div class="text-center">
                  <a v-for="(button, index) in pictureElements[4].buttons" :key="index" :style="changeButton(button.btnTextColor,button.btnBgColor)" :href="button.btnLink"  class="theme-btn">{{ button.btnText }}</a>
                </div>
                </div>
              <div class="col-lg-6">
                <div style="margin-top: 12%"></div>
                <img
                  @click="$emit('isFocused', 3)"
                  :src="pictureElements[5].imgUrl"
                  :class="pictureElements[5].imgShape + ' img-fluid'"
                  :alt="pictureElements[5].imgAlt"
                />
              </div>
            </div>
          </div>
        </div>
        <svg
          class="wave"
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 1440 320"
        >
          <path 
            :fill="pictureElements[2].color"
            :fill-opacity="pictureElements[2].opacity"
            :d="pictureElements[2].waveStyle[pictureElements[2].selectedShape].shape"
          ></path>
        </svg>
      </div>
    </div>
    
  </div>
</template>

<script>
export default {
  props: {
    pictureElements: Array,
  },
  methods: {
    updateCSS(txtcolor, bgcolor, isHighlited) {
      let updatedCSS;
      if (isHighlited) {
        updatedCSS = "color:" + txtcolor + ";background:" + bgcolor + ";";
        return updatedCSS;
      } else {
        updatedCSS = "color:" + txtcolor + ";background:transparent;";
        return updatedCSS;
      }
    },
    changeBackground(choosedSide, choosedColor1, choosedColor2) {
            return (
                "background-image: linear-gradient(" +
                choosedSide +
                "," +
                choosedColor1 +
                "," +
                choosedColor2 +
                ");"
            );
        },

    changeButton(textcolor, bgcolor) {
            return (
                "background:" +
                bgcolor +
                ";color:" +
                textcolor 
            );
        },
  },
};
</script>

<style>
.preview {
  height: 100vh;
  overflow-y: auto;
  margin: 0px;
  color: blueviolet;
  background-color: #2b2b33;
}

.header-content {
  z-index: 1;
  position: relative;
}

.header-content h1 {
  font-size: 45px;
  font-weight: bold;
  text-transform: capitalize;
  color: white;
}

.header-content p {
  font-size: 20px;
  margin: 20px 0 25px;
  color: white;
  letter-spacing: 1px;
  font-weight: 300;
  text-transform: capitalize;
}

.theme-btn {
  border-radius: 50px;
  padding: 15px 30px;
  min-width: 170px;
  border: 2px solid white;
  font-size: 14px;
  text-transform: uppercase;
  margin-top: 13px;
  display: inline-block;
  text-align: center;
  margin-right: 12px;
  transition: all 0.5s ease-in;
  font-weight: bold;
}

.theme-btn:hover {
  text-decoration: none;
  background-color: #fff;
  color: #9f1b53;
}

.img-responsive {
  width: 100%;
  height: auto;
  max-width: 600px;
  max-height: 500px;
}

.sha-1{
    -webkit-mask: url(@/assets/shape1.svg) center/contain no-repeat;
    max-width: 100%
}

.sha-2{
    -webkit-mask: url(@/assets/shape2.svg) center/contain no-repeat;
    max-width: 100%
}
.sha-3{
    -webkit-mask: url(@/assets/shape2.svg) center/contain no-repeat;
    max-width: 100%
}
</style>
