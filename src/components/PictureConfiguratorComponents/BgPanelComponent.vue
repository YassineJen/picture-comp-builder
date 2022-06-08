<template>
    <div class="customize-panel">
        <div class="block-title">
            <i class="fa-solid fa-image"></i> Background
        </div>
        <div class="block-tools">
            <ul class="nav nav-tabs" id="myTab" role="tablist">
                <li class="nav-item" role="presentation">
                    <button class="nav-link active" id="wave-tab" data-bs-toggle="tab" data-bs-target="#wave-settings"
                        type="button" role="tab" aria-controls="home" aria-selected="true">Wave</button>
                </li>
                <li class="nav-item" role="presentation">
                    <button class="nav-link" id="bg-tab" data-bs-toggle="tab" data-bs-target="#bg-settings"
                        type="button" role="tab" aria-controls="profile" aria-selected="false">Background</button>
                </li>
            </ul>
            <div class="tab-content" id="myTabContent">
                <div class="tab-pane fade show active buttonsdiv" id="wave-settings" role="tabpanel"
                    aria-labelledby="wave-tab">
                    <table class="table table-sm table-bordered border-dark">
                        <tr>
                            <td>Color : {{ pictureElementsCopy[2].color }}</td>
                            <td style="text-align:center"><span class="color-picker">
                                    <input 
                                        v-model="pictureElementsCopy[2].color" type="color" id="colorPicker" />
                                </span></td>

                        </tr>
                        <tr>
                            <td>Opacity : {{pictureElementsCopy[2].opacity}} </td>
                            <td><input 
                                    v-model="pictureElementsCopy[2].opacity" width="auto" type="range"
                                    class="form-range" min="0" max="1" step="0.01" id="customRange3" /></td>
                        </tr>
                        <tr>
                            <td>Shape :</td>
                            <td>            
                                <select  style="background: #595964; color: white" v-model="pictureElementsCopy[2].selectedShape"
                                        class="form-select form-select-sm" aria-label=".form-select-sm example">
                                    <option value="0">Wave 1</option>
                                    <option value="1">Wave 2</option>
                                    <option value="2">Wave 3</option>
                                    <option value="3">Wave 4</option>
                                    <option value="4">Wave 5</option>
                                    <option value="5">Wave 6</option>
                                </select></td>
                        </tr>
                        <tr>
                            <td>Position :</td>
                            <td></td>
                        </tr>
                    </table>
                </div>
                <div class="tab-pane fade buttonsdiv" id="bg-settings" role="tabpanel" aria-labelledby="bg-tab">
                    <table class="table table-sm table-bordered border-dark">
                        <tr>
                            <td>Gradient Color :</td>
                            <td> <span class="color-picker">
                                    <input  v-model="pictureElementsCopy[3].choosedColor1" type="color" value="#1DB8CE" id="choosedColor1" />

                                </span>
                                <span class="color-picker">
                                    <input  v-model="pictureElementsCopy[3].choosedColor2" type="color" value="#1DB8CE" id="choosedColor2" />
                                </span>
                            </td>

                        </tr>
                        <tr>
                            <td>Direction :</td>
                            <td>
                                <select   style="background: #595964; color: white" v-model="pictureElementsCopy[3].choosedSide"
                                    class="form-select form-select-sm" aria-label=".form-select-sm example">
                                    <option selected value="to right">Left to right</option>
                                    <option value="to left">Right to left</option>
                                    <option value="180deg">Top to bottom</option>
                                </select>
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

.settings-panel input,
table td {
    background: #595964;
    color: white;
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