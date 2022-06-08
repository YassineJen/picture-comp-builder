<template>
                  <div class="customize-panel">
                    <div class="block-title">
                        <i class="fa-solid fa-highlighter"></i> Text
                    </div>
                    <div class="block-tools">
                        <div id="checkboxes" class="d-inline">
                            <input  v-model="pictureElementsCopy[selectedId].boldBool" type="checkbox" name="rGroup" value="1" id="r1" />
                            <label class="whatever" for="r1"><i class="fa-solid fa-bold"></i></label>
                            <input  v-model="pictureElementsCopy[selectedId].italicBool" type="checkbox" name="rGroup" value="2" id="r2" />
                            <label class="whatever" for="r2"><i class="fa-solid fa-italic"></i></label>
                            <input  v-model="pictureElementsCopy[selectedId].underlineBool" type="checkbox" name="rGroup" value="3" id="r3" />
                            <label class="whatever" for="r3"><i class="fa-solid fa-underline"></i></label>
                            <input  v-model="pictureElementsCopy[selectedId].strikeThroughBool" type="checkbox" name="rGroup" value="4" id="r4" />
                            <label class="whatever" for="r4"><i class="fa-solid fa-strikethrough"></i></label>
                        </div>
                        <div id="checkboxes" class="d-inline p-2">
                            <input  v-model="pictureElementsCopy[selectedId].startBool" type="checkbox" name="mGroup" value="1" id="p1" />
                            <label class="whatever" for="p1"><i class="fa-solid fa-align-left"></i></label>
                            <input  v-model="pictureElementsCopy[selectedId].centerBool" type="checkbox" name="mGroup" value="2" id="p2" />
                            <label class="whatever" for="p2"><i class="fa-solid fa-align-center"></i></label>
                            <input  v-model="pictureElementsCopy[selectedId].endBool" type="checkbox" name="mGroup" value="3" id="p3" />
                            <label class="whatever" for="p3"><i class="fa-solid fa-align-right"></i></label>
                        </div>
                                                    <div v-if="selectedId === 1" class="d-inline text-start ">
                                                    <label for="lineH"><i class="fa-solid fa-text-height pe-1"></i></label>
                                <select id="lineH"  class="custom-select" v-model="pictureElementsCopy[selectedId].lineHeight" aria-label=".form-select-sm example">
                                    <option value="lh-1">
                                        <label class="custom-select-option" for="r2">1</label>
                                    </option>
                                    <option value="lh-sm">
                                        <label class="custom-select-option" for="r2">1.25</label>
                                    </option>
                                    <option value="lh-base">
                                        <label class="custom-select-option" for="r2">1.5</label>
                                    </option>
                                    <option value="lh-lg">
                                        <label class="custom-select-option" for="r2">2</label>
                                    </option>
                                </select>
                            </div>

                        <div class="fontSettings">
                            <div class="d-inline text-start ">
                                <select  class="custom-select" v-model="pictureElementsCopy[selectedId].fontSize" aria-label=".form-select-sm example">
                                    pick ure size
                                    <option class="h1" value="fs-1">
                                        <label class="custom-select-option" for="r2">Display-1</label>
                                    </option>
                                    <option class="h2" value="fs-2">
                                        <label class="custom-select-option" for="r2">Display-2</label>
                                    </option>
                                    <option class="h3" value="fs-3">
                                        <label class="custom-select-option" for="r2">Display-3</label>
                                    </option>
                                    <option class="h4" value="fs-4">
                                        <label class="custom-select-option" for="r2">Display-4</label>
                                    </option>
                                    <option class="h5" value="fs-5">
                                        <label class="custom-select-option" for="r2">Display-5</label>
                                    </option>
                                </select>
                            </div>
                                                                        <div id="checkboxes" class="d-inline p-1">
                                <input type="checkbox" name="pppGroup" value="1" id="ppp1" disabled />
                                <label class="whatever" for="ppp1"><i class="fa-solid fa-paintbrush"></i>&nbsp;<input 
                                        v-model="pictureElementsCopy[selectedId].txtcolor" type="color" value="#1DB8CE" id="choosedCo1" />
                                </label>

                            </div>
                            <div id="checkboxes" class="d-inline ">
                                <input  v-model="pictureElementsCopy[selectedId].isHighlited" type="checkbox" name="fffGroup" value="1" id="n1" />
                                <label class="whatever" for="n1"><i class="fa-solid fa-highlighter"></i>&nbsp;<input 
                                        v-model="pictureElementsCopy[selectedId].bgcolor" type="color" value="#1DB8CE"
                                        id="choosedColonl1" /></label>

                            </div>
                </div>

            </div>
        </div>
</template>

<script>
export default {
  props: {
    pictureElements: Array,
    selectedId: Number,
  },
  mounted() {
    this.pictureElementsCopy = this.pictureElements;
  },
  data() {
    return {
      pictureElementsCopy: null,
    };
  },
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

<style scoped>

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

.whatever {
  background-color: #595964;
  color: #a6a6a8;
  vertical-align: middle;
  display: inline-block;
  width: 35px;
  height: auto;
  border: 1px solid #141217;
  text-align: center;
}

.fontSettings {
    padding-top: 2px;
    text-align: left;
}

#checkboxes input[type="checkbox"] {
  display: none;
}

#checkboxes {
  width: fit-content;
}

#checkboxes input[type="checkbox"]:checked+.whatever {
  background-color: #2b2b33;
  color: #fff;
}

#checkboxes input[type="checkbox"]:hover+.whatever {
  color: #fff;
}

.custom-select {
  background: #595964;
  color: white;
}

.custom-select-option:hover {
  background: #2b2b33;
}

.custom-select-option {
  max-width: 10px;
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