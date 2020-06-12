<template>
  <div @click="setActive()" class="item" :class="{ active: active }">
    <div class="inner" :ref="'ref' + _uid">
      <div class="single" :ref="'single' + _uid">
        <div class="title heading">{{ item.name }}</div>
        <img :src="item.image" :alt="item.name" />
        <span v-if="active" @click.stop="closeActive">close</span>
        <span class="price">{{ item.value }}</span>
      </div>
      <div class="details">
        Some detasils
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      active: false,
      activeleft: 0,
      activetop: 0
    }
  },
  props: {
    item: Object
  },
  methods: {
    setActive () {
      const that = this
      this.active = true
      this.activeleft = this.$refs['ref' + this._uid].getBoundingClientRect().left
      this.activetop = this.$refs['ref' + this._uid].getBoundingClientRect().top

      this.$refs['ref' + this._uid].style.position = 'fixed'
      this.$refs['ref' + this._uid].style.left = this.activeleft + 'px'
      this.$refs['ref' + this._uid].style.top = this.activetop + 'px'
      setTimeout(function() {
        that.$refs['ref' + that._uid].style.left = '0'
        that.$refs['ref' + that._uid].style.top = '0'
        that.$refs['ref' + that._uid].style.bottom = '0px'
        that.$refs['ref' + that._uid].style.height = '100%'
        that.$refs['single' + that._uid].style.borderRadius = '0'
        that.$refs['ref' + that._uid].style.width = '100%'

      }, 1)
      setTimeout(function() {
      }, 500)

    },
    closeActive () {
      const that = this
      console.log(this.$refs)
      console.log(this.$refs['ref' + this._uid])
      console.log( this.activeleft + 'px')
      this.$refs['ref' + this._uid].style.left = this.activeleft + 'px'
      this.$refs['ref' + this._uid].style.top = this.activetop + 'px'
      this.$refs['ref' + that._uid].style.width = '320px'
      this.$refs['ref' + that._uid].style.height = '400px'
      this.$refs['single' + that._uid].style.borderRadius = '25px'

      setTimeout(function() {
        that.active = false
        that.$refs['ref' + that._uid].style.position = 'unset'
      }, 500)
    }
  }
}
</script>
<style lang="scss">
  .item {
    margin: 20px;
    box-shadow: 0 0 10px rgba(0,0,0,0.01);
    text-align: center;
    border-radius: 25px;
    transition: 0.5s all;
    background: #f7f7f7;
    display: flex;
    width: 320px;
    height: 400px;
    margin: 20px;
    img {
      width: 100%;
      max-width: 200px;
      height: auto;
    }
    .inner {
      transition: 0.5s all;
      display: flex;
    }
    .details {
      width:0;
      overflow: hidden;
      display: none;
      transition: 0.5s all;
    }
    .heading {
      font-weight: bold;
      font-size: 20px;
      margin: 15px 0;
    }
    .single {
      width: 320px;
      height: 400px;
      padding: 20px;
      border-radius: 25px;
      position: relative;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      align-items: center;
    }
    &:hover, &.active {
      .inner {
      .single {
        background: linear-gradient(#3f4870, #524a6d);
        color: white;
        .title {
          color: white;
        }
      }
      }
    }
    &.active {
      z-index: 2;
      .details {
        width: auto;
        flex: 1;
        background: #f5f5f5;
        padding: 20px;
        text-align: left;
        display: flex;
      }
      .single {
        height: 100%;
        z-index: 3;
      }

    }
  }
</style>