<template>
                <div class="customize-panel">
                    <div class="block-title"><i class="fa-solid fa-computer-mouse"></i> Button<div @click="addBtn()"
                            class="plusBtn"><i class="fa-solid fa-circle-plus"></i></div>
                    </div>
                    <div class="block-tools">
                        <div class="text-center" v-if="pictureElementsCopy[4].buttons.length == 0"> Press the ADD button !</div>
                        <div v-for="(button, index) in pictureElementsCopy[4].buttons" :key="index" style="padding:6px">
                            <div class="buttonsdiv">
                                <div class="buttonsdiv-title text-center">Button {{ index + 1 }}
                                <div @click="deleteBtn(index)"
                                        class="deleteBtn" style="float:right"><i class="fa-solid fa-trash-can"></i>
                                </div>
                                </div>
                                <table class="table table-sm table-bordered border-dark text-center ">
                                    <tr>
                                        <td>Text</td>
                                        <td>
                                            <input  v-model="button.btnText" style="color:white;border:none" type="text" >
                                        </td>
                                        <td>
                                            <div > 
                                                <input  v-model="button.btnTextColor" type="color" value="#1DB8CE">
                                            </div>
                                        </td>
                                    </tr>
                                    <tr>
                                        <td >URL</td>
                                        <td>
                                            <input  v-model="button.btnLink" style="color:white;border:none" type="text" >
                                        </td>
                                        <td></td>
                                    </tr>
                                    <tr>
                                        <td style="color:#fff">Background</td>
                                        <td></td>
                                        <td>
                                            <div>
                                                <input  v-model="button.btnBgColor" type="color" value="#1DB8CE">
                                            </div>
                                        </td>
                                    </tr>
                                </table>

                            </div>
                        </div>
                    </div>
                </div>
</template>

<script>
export default {
  props: {
    pictureElements: Array,
  },
  mounted() {
    this.pictureElementsCopy = this.pictureElements;
  },
  data() {
    return {
      pictureElementsCopy: null,
    };
  },

  methods:{
        addBtn() {
            this.pictureElementsCopy[4].buttons.push({
                btnText: "ButtonTEXT",
                btnLink: "#",
                btnTextColor: "#9f1b53",
                btnBgColor:"#FFFFFF"
            })
        },
        deleteBtn(index) {
            this.pictureElementsCopy[4].buttons.splice(index, 1);
        },

  }

};
document.querySelectorAll("input[type=color]").forEach(function (picker) {
    //Target Point
    var targetLabel = document.querySelector('label[for="' + picker.id + '"]'),
        codeArea = document.createElement("span");

    codeArea.innerHTML = picker.value;
    targetLabel.appendChild(codeArea);

    //Now AddEventListener
    picker.addEventListener("change", function () {
        codeArea.innerHTML = picker.value;
        targetLabel.appendChild(codeArea);
    });
});
</script>

<style>

.customize-panel {
  padding-top: 1px;
  background: #3e3e46;
  border-top: 1px solid black;
  border-bottom: 1px solid black;
  margin-bottom: 3px;
}

.block-title {
  background: #2b2b33;
  text-align: left;
  text-transform: uppercase;
  font-weight: bold;
  font-size: 12px;
  letter-spacing: 1px;
  padding-left: 10px;
  border-bottom: 1px solid black;
}


.block-tools {
  text-align: left;
  padding: 5px;
}

.plusBtn {
    background: #595964;
    float: right;
    padding: 4px;
    border: 1px solid #141217;
}
.plusBtn:hover {
    background: #3e3e46;
}
table td{
    color:white;
}


.deleteBtn {
    background: #2b2b33;
    float: right;
    width: 25px;
}

.deleteBtn:hover {
    background: #3e3e46;
}

.buttonsdiv {
    background: #595964;

}

.buttonsdiv-title {
    background: #2b2b33;
    
    border: 1px solid #141217;
    height: 26px;
}

/* Color Picker */

[type="color"] {
    appearance: none;
    padding: 0;
    width: 15px;
    height: 15px;
    border: none;
}

[type="color"]::-webkit-color-swatch-wrapper {
    padding: 0;
}

[type="color"]::-webkit-color-swatch {
    border: none;
}

.color-picker {
    padding: 4px 7px;
    text-align: center;
    margin-left: 20px;
    margin-top: 2px;
}

.labelcolor {
    margin-bottom: 15px;
    display: inline-block;
    margin-top: 15px;
}

</style>