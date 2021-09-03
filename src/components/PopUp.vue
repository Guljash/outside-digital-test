<template>
  <div class="popup">
    <div class="popup-inner">
      <button @click="$emit('closePopUp')" class="popup-close" />
      <slot />
    </div>
  </div>
</template>

<script>
export default {
  name: "PopUp",
};
</script>

<style scoped>
.popup {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 100;
  background-color: darkgray;
  display: flex;
  align-items: center;
  justify-content: center;
}

.popup-close {
  position: absolute;
  right: 25px;
  top: 25px;
  background-color: rgba(0, 0, 0, 0);
  border: none;
  background-image: url("../assets/Close.svg");
  background-size: cover;
  width: 18px;
  height: 18px;
  cursor: pointer;
}

.popup-inner {
  position: relative;
  background-color: rgb(255, 255, 255);
  border-radius: 30px;
  width: 552px;
  padding: 30px;
}

@media screen and (max-width: 375px) {
  .popup {
    background-color: rgb(255, 255, 255);
    align-items: flex-start;
    justify-content: center;
  }
  .popup-inner {
    background-color: rgb(255, 255, 255);
    padding: 0 30px 0 30px;
    border-radius: 0px;
    width: 100%;
    height: auto;
    margin-top: 30px;
  }
  .popup-close {
    right: 25px;
    top: 0px;
  }
}
</style>
