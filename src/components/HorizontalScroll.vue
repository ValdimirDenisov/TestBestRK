<template>
  <div class="_horizontal-scroll horizontal-scroll">
    <div class="outer">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    const content = this.$el;
    if(content.addEventListener){
      content.addEventListener('DOMMouseScroll', function(e){
        content.scrollBy(-e.wheelDelta, 0);
      }, false);
    }
    if(content.attachEvent){
      content.attachEvent('onmousewheel', function(e){
        content.scrollBy(-e.wheelDelta, 0);
      });
    }
    content.onmousewheel = function(e){
      content.scrollBy(-e.wheelDelta, 0);
    }
  }
}
</script>

<style scoped>
._horizontal-scroll {
  box-sizing: border-box;
  overflow-x: scroll;
  overflow-y: hidden;
  text-align: left;
  white-space: nowrap;
}

._horizontal-scroll::-webkit-scrollbar {
  height: 3px;
}

.outer {
  display: flex;
  flex: 1;
  width: auto;
  height: 100%;
  padding: 0 20px;
  flex-flow: row nowrap;
  align-items: center;
}
.horizontal-scroll {
  display: flex;
  width: 400px;
  /*overflow-x:hidden;*/
}

.horizontal-scroll::after {
  display: block;
  content: '';
  height: 100%;
  width: 10px;
}
</style>
