<script>
export default {
  data() {
    return {
      output: "",
      rem: 26,
      letter_available: true,
    };
  },
  methods: {
    next_letter() {
      if (cur.length > 1) {
        const tar = Math.floor(cur.length * Math.random());
        this.output = cur[tar];
        cur.splice(tar, 1);
      } else if (cur.length == 1) {
        this.output = cur[0];
        cur = [];
      } else {
        this.letter_available = false;
        alert("thats all the letters");
      }
      this.rem = cur.length + 1;
    },
    next_game() {
      
      if(confirm('are you sure you want to restart ')){

        cur = selection.split("");
        this.rem = cur.length;
        this.output = "";
        this.letter_available = true;
      }
    },
  },
};
const selection = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
let cur = selection.split("");
</script>

<template>
  <div v-if="letter_available">
    <button type="button" class="btn" @click="next_letter()">
      next letter
    </button>
  </div>
  <button @click="next_game()">restart</button>
  <h1>{{ output }}</h1>
  <h3>letters remaining {{ rem }}</h3>
</template>

<style scoped></style>
