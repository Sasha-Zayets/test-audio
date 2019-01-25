<template>
  <div class="hostButton">
    <button type="button" name="button" class="audioButton audioButton_disable-true">
      <i class="fa fa-angle-left"></i>
      Назад
    </button>
    <button type="button" name="button" class="audioButton">
      Далее
      <i class="fa fa-angle-right"></i>
    </button>
  </div>
</template>

<script>
export default {
}
</script>

<style lang="scss">
.hostButton {
  text-align: center;
  padding: 0 10px 10px 10px;
  margin-top: 20px;
  .audioButton {
    box-shadow: 0px 3px 1px -2px rgba(0,0,0,0.2), 0px 2px 2px 0px rgba(0,0,0,0.14), 0px 1px 5px 0px rgba(0,0,0,0.12);
    border: none;
    padding: 10px 15px;
    background: #F5F5F5;
    color: black;
    text-transform: uppercase;
    font-weight: bold;
    outline: none;
    &:active, &:focus {
      outline: none;
    }
    &_disable-true {
      background-color: #DCDCDC;
      color: #ACACAC;
    }
    &:last-child {
      margin-left: 5px;
    }
    &:first-child {
      margin-right: 5px;
    }
  }
}
</style>
