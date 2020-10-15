# vue-html2canvas
Vue mixin for Html2Canvas to remove the white spaces.

### Install

```
npm install vue-html2canvas
```
**Or**
```
yarn add vue-html2canvas
```

### Usage

**main.js**

```javascript
import Vue from 'vue';
import VueHtml2Canvas from 'vue-html2canvas';

Vue.use(VueHtml2Canvas);
```

**component**

```html
<template>
  <div>
    <!-- SOURCE -->
    <div ref="printMe" style="padding: 10px; background: #f5da55">
      <h1 style="color: #000; ">Print me!</h1>
    </div>
    <!-- OUTPUT -->
    <img :src="output">
  </div>
</template>

<script>
export default {
  data() {
    return {
      output: null
    }
  },
  methods: {
    async print() {
      const el = this.$refs.printMe;
      // add option type to get the image version
      // if not provided the promise will return 
      // the canvas.
      const options = {
        type: 'dataURL'
      }
      this.output = await this.$html2canvas(el, options);
    }
  },
  mounted() {
    this.print()
  }
}
</script>
```

Made with ❤️ by Jofferson Ramirez Tiquez
