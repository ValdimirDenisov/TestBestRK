<template>
  <div class="main_container">
    <div class="nav_bar">
      <MyInput></MyInput>
      <div class="bar" ref="bar">
        <HorizontalScroll>
            <div class="inner-content_menu" v-for="item in [1, 2, 3, 4, 5, 6]" :key="item">content</div>
        </HorizontalScroll>
      </div>
    </div>
    <div class="content">
      <div class="menu_bar" >
        <div class="content_item_container" v-for="item in [1, 2, 3, 4, 5, 6, 7, 8, 9]" :key="item">
          <h1 class="head">Какое-то описание</h1>
          <HorizontalScroll>
            <div class="inner-content" v-for="item in [1, 2, 3, 4, 5, 6]" :key="item">content</div>
          </HorizontalScroll>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import MyInput from "./components/MyInput";
import HorizontalScroll from "./components/HorizontalScroll";

export default {
  name: 'App',
  components: {
    MyInput,
    HorizontalScroll,
  },
  created() {
    let prevScrollpos = window.pageYOffset;
    window.addEventListener('scroll',() => {
      let currentScrollPos = window.pageYOffset;
      if (currentScrollPos > 104) {
        if (prevScrollpos > currentScrollPos) {
          this.$refs.bar.classList.add('fixed')
          this.$refs.bar.classList.remove('hide-menu')
        } else {
          this.$refs.bar.classList.add('hide-menu')
        }
      } else {
        this.$refs.bar.classList.remove('fixed')
        this.$refs.bar.classList.remove('hide-menu')
      }
      prevScrollpos = currentScrollPos;
    })
  }
}
</script>

<style lang="scss">
  * {
    margin: 0;
    padding: 0;
  }
  .fixed {
    position: fixed;
    top: 0px;
    transition: all 0.5s cubic-bezier(0, 0, 0.8, 1.0);
  }

  .hide-menu {
    transform: translateY(-100%);
  }

  .main_container {
    width: 440px;
    margin: auto;
    border-left: 1px solid black;
    border-right: 1px solid black;
    //background-color: #ff7373;

    .nav_bar {
      width: 100%;
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
    }
    .bar {
      padding: 10px;
      //border: 2px solid red;
    }
  }

  .menu_bar {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    .content_item_container {
      margin-top: 15px;
    }
    .head {
      font-size: 20px;
    }
    .inner-content {
      display: flex;
      flex-shrink: 0;
      align-items: center;
      justify-content: center;
      width: 150px;
      height: 150px;
      border: solid 1px #2c3e50;
      border-radius: 5px;
    }

    .inner-content:not(:first-of-type) {
      margin-left: 10px;
    }

    .inner-content:first-of-type {
      margin-left: -15px;
    }
  }



  .inner-content_menu {
    display: flex;
    flex-shrink: 0;
    align-items: center;
    justify-content: center;
    width: 100px;
    height: 20px;
    border: solid 1px #2c3e50;
    border-radius: 5px;
  }
  .inner-content_menu:not(:first-of-type) {
    margin-left: 30px;
  }


</style>
