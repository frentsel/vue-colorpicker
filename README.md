# vue-colorpicker2

## [LiveDemo](https://caohenghu.github.io/vue-colorpicker2/)

![preview](https://raw.githubusercontent.com/caohenghu/vue-colorpicker2/master/src/img/preview.jpg)

## Install

```bash
$ yarn add vue-colorpicker2
```

## Example

```html
<template>
    <div :style="{background: color}">
        <color-picker
            :color="color"
            :sucker-hide="false"
            :sucker-canvas="suckerCanvas"
            :sucker-area="suckerArea"
            @change="change"
            @openSucker="openSucker"
        />
    </div>
</template>

<script>
    import colorPicker from 'vue-colorpicker2'

    export default {
        components: {
            colorPicker
        },
        data() {
            return {
                color: '#59c7f9',
                suckerCanvas: null,
                suckerArea: [],
                isSucking: false
            }
        },
        methods: {
            change(color) {
                const {rgba: {r, g, b, a}} = color
                this.color = `rgba(${r, g, b, a})`
            },
            openSucker(isOpen) {
                if (isOpen) {
                    // ... canvas be created
                    // this.suckerCanvas = canvas
                    // this.suckerArea = [x1, y1, x2, y2]
                } else {
                    // this.suckerCanvas && this.suckerCanvas.remove
                }
            }
        }
    }
</script>
```

## Options

name | type | default | desc
---|---|---|---
color | String | `#000000` | `rgba` or `hex`
colors-default | Array | `['#000000', '#FFFFFF', '#FF1900', '#F47365', '#FFB243', '#FFE623', '#6EFF2A', '#1BC7B1', '#00BEFF', '#2E81FF', '#5D61FF', '#FF89CF', '#FC3CAD', '#BF3DCE', '#8E00A7', 'rgba(0,0,0,0)']` | like `['#ff00ff', '#0f0f0f', ...]`
colors-history-key | String | `vue-colorpicker2-history` | 
sucker-hide | Boolean | `true` | `true` or `false`
sucker-canvas | HTMLCanvasElement | `null` | like `document.createElement('canvas')`
sucker-area | Array | `[]` | like `[x1, y1, x2, y2]`


> color is one-way data flow, so you can't use v-model. why? because you'll listen change event do more things, so i think it's not necessary here.

## Events

name | type | emit args | desc
---|---|---|---
changeColor | Function | color | `{ rgba: {}, hsv: {}}`
openSucker | Function | isOpen | `true` or `false`

> if you want use sucker, then `openSucker`, `sucker-hide`, `sucker-canvas`, `sucker-area` is necessary.