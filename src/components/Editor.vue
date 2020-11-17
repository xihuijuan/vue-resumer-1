<template>
  <div class="editor">
    <nav>
      <ol>
        <li v-for="i in [0,1,2,3,4,5]" 
        v-bind:class="{ active: currentTab === i }"  v-on:click="(currentTab = i)">
          <svg class="icon">
            <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
          </svg>
        </li>
        <!-- <li v-bind:class="{ active: currentTab === 1 }" v-on:click="(currentTab = 1)">
          <svg class="icon">
            <use xlink:href="#icon-gongzuobao"></use>
          </svg>
        </li>
        <li v-bind:class="{ active: currentTab === 2 }" v-on:click="(currentTab = 2)">
          <svg class="icon">
            <use xlink:href="#icon-book"></use>
          </svg>
        </li>
        <li v-bind:class="{ active: currentTab === 3 }" v-on:click="(currentTab = 3)">
          <svg class="icon">
            <use xlink:href="#icon-shoucang"></use>
          </svg>
        </li>
        <li v-bind:class="{ active: currentTab === 4 }"  v-on:click="(currentTab = 4)">
          <svg class="icon">
            <use xlink:href="#icon-trophy"></use>
          </svg>
        </li>
        <li v-bind:class="{ active: currentTab === 5 }"  v-on:click="(currentTab = 5)" >
          <svg class="icon">
            <use xlink:href="#icon-icon_dianhua"></use>
          </svg>
        </li> -->
      </ol>
    </nav>
    <ol class="panes">
      <li v-bind:class="{active:currentTab === 0}">tab 1</li>
      <li v-bind:class="{active:currentTab === 1}">tab 2</li>
      <li v-bind:class="{active:currentTab === 2}">tab 3</li>
      <li v-bind:class="{active:currentTab === 3}">tab 4</li>
      <li v-bind:class="{active:currentTab === 4}">tab 5</li>
      <li v-bind:class="{active:currentTab === 5}">tab 6</li>
    </ol>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentTab: 0,
      icons:['credentials_icon','gongzuobao','book','shoucang','trophy','icon_dianhua']
    };
  },
};
</script>

<style lang="scss">
.editor {
  min-height: 100px;
  display: flex;
  > nav {
    background: #000;
    width: 80px;
    > ol > li {
      padding: 16px 0px;
      text-align: center;
      > .icon {
        width: 32px;
        height: 32px;
        fill: #fff;
      }
      &.active {
        background: #fff;
        > .icon {
          fill: #000;
        }
      }
    }
  }
  > .panes{
      >li{
        display: none;
        &.active{
          display: block;
        }
      }
    }
}
</style>