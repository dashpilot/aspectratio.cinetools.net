
<template>
<div class="wrap">
  <main id="main">


    <div class="wdgt wdgt-main">
      <div class="wdgt-toolbar">
        Filmkit Aspect Ratio Calculator
      </div>

      <div class="wdgt-content p-3">

        <label>Original Width</label>
        <input type="text" class="form-control" v-model="orig_w" @keyup="calculate($event, 'w')">

        <label>Original Height</label>
        <input type="text" class="form-control" v-model="orig_h" @keyup="calculate($event, 'h')">

        <label>New Width</label>
        <input type="text" class="form-control" v-model="new_w" @keyup="calculate($event, 'w')">

        <label>New Height</label>
        <input type="text" class="form-control" v-model="new_h" @keyup="calculate($event, 'h')">

      </div>



    </div>








    <div class="text-center wdgt-footer">Made by <a href="https://www.filmkit.net">Filmkit</a></div>





  </main>
</div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      orig_w: 1920,
      orig_h: 1080,
      new_w: null,
      new_h: null
    }
  },
  methods: {
    calculate($event, trigger) {

      let keyCode = ($event.keyCode ? $event.keyCode : $event.which);
      if (keyCode < 48 || keyCode > 57) { // 46 is dot
        $event.preventDefault();
      }

      let ratio = this.orig_h / this.orig_w;
      console.log(ratio)
      console.log(this.new_w)

      if (trigger == "w") {
        this.new_h = Math.round(this.new_w * ratio);
      } else {
        this.new_w = Math.round(this.new_h * ratio);
      }


    }
  }
}
</script>
