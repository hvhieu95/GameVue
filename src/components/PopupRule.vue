<template>
  <div class="wraper-popup " v-bind:class="getClassPopup">
    <div class="rule">
      <h3>luat choi</h3>
      <p>
        xxxxxxxxxxxxxxxxxxx
      </p>
      <button v-on:click="confirm" class="confirm">da hieu</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "popup-rule",
  props: {
    isOpenPopup: { type: Boolean, default: false },
  },
  data() {
    return {};
  },
  computed: {
    getClassPopup: function() {
      return {
        "open-popup": this.isOpenPopup,
      };
    },
  },
  methods: {
    confirm() {
      this.$emit("handleConfirm");
    },
  },
};
</script>

<style>
.wraper-popup {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(black 0, 0, 0, 0.4);
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
}
.wraper-popup.open-popup {
  opacity: 1;
  visibility: visible;
}
.rule {
  width: 350px;
  padding: 20px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%) scale(1, 2);
  background-color: aliceblue;
  position: absolute;
  font-family: Arial, Helvetica, sans-serif;
  transition: all 0.3s ease;
}
.open-popup .rule {
  transform: translate(-50%, -50%) scale(1);
}
.rule h3 {
  margin-bottom: 10px;
}
.rule .confirm {
  border: 2px solid #333;
  background-color: #fff;
  cursor: pointer;
  margin-top: 20px;
  transition: all 0.3s ease;
  padding: 8px 15px;
}
.rule .confirm:hover {
  color: #fff;
  background-color: #333;
}
</style>
