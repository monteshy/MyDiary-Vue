<template>
  <transition name="fade">
    <div v-show="isModalShow">
      <div class="mask"
           @click="isModalShow=!isModalShow"></div>
      <div class="modal">
        <p>是否确定删除</p>
        <button @click="yes">确定</button>
        <button @click="no">取消</button>
      </div>
    </div>
  </transition>
</template>
<script>
import { mapGetters } from 'vuex'
import axios from 'axios';
const pinyin = require('pinyin');
export default {
  data() {
    return {
      isModalShow: false,
      contact: '',
      number: '',
      initial: ''
    }
  },
  watch: {
  },
  computed: mapGetters({
    currentFolder: 'getCurrentFolder'
  }),
  methods: {
    yes() {
      this.$parent.deleteItem()
      this.isModalShow = !this.isModalShow
    },
    no() {
      this.isModalShow = !this.isModalShow
    }
  }
}
</script>
<style lang="less" scoped>
@import '../less/common.less';
.mask {
  position: absolute;
  left: 0;
  top: 0;
  background-color: #000;
  opacity: .3;
  height: 100vh;
  width: 100vw;
}

.modal {
  position: absolute;
  box-sizing: border-box;
  padding: 0 20px;
  top: 50%;
  left: 50%;
  margin-left: -140px;
  margin-top: -80px;
  width: 280px;
  height: 160px;
  background-color: #fff;
  color: @maincolor;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  border-radius: 5px;
  input,
  button {
    height: 30px;
    line-height: 30px;
    margin: 2px;
    border: 1px solid @maincolor;
    border-radius: 5px;
  }
  input {
    width: 180px;
    padding: 0 20px;
    color: @maincolor;
  }
  button {
    width: 90px;
    background-color: @maincolor;
    color: #fff;
  }
}
</style>