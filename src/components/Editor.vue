<template>
  <div class="editor">
    <nav>
      <ol>
        <li
          v-for="i in [0, 1, 2, 3, 4, 5]"
          v-bind:class="{ active: currentTab === i }"
          v-on:click="currentTab = i"
        >
          <svg class="icon">
            <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
          </svg>
        </li>
        <!-- <li v-bind:class="{ active: currentTab === 1 }" v-on:click="(currentTab = 1)">
          <svg class="icon">
            <use xlink:href="#icon-gongzuobao"></use>
          </svg>
        </li>-->
      </ol>
    </nav>
    <ol class="panes">
      <!--      <li v-for="i in [0,1,2,3,4,5]" v-bind:class="{active:currentTab === i}">
        Tab{{i+1}}
      </li> -->
      <li v-bind:class="{ active: currentTab === 0 }">
        <ProfileEditor :profile="resume.profile" />
      </li>
      <li v-bind:class="{ active: currentTab === 1 }">
        <ArrayEditor
          :items="resume.workHistory"
          :labels="{ company: '公司', content: '工作内容' }"
          :title="'工作经历'"
        />
      </li>
      <li v-bind:class="{ active: currentTab === 2 }">
        <h2>学习经历</h2>
        <ArrayEditor
          :items="resume.studyHistory"
          :labels="{ school: '学校', duration: '毕业时间', degree: '学历' }"
        />
      </li>
      <li v-bind:class="{ active: currentTab === 3 }">
        <h2>项目经历</h2>
        <ArrayEditor
          :items="resume.projects"
          :labels="{ name: '项目名称', content: '项目内容' }"
        />
      </li>
      <li v-bind:class="{ active: currentTab === 4 }">
        <h2>获奖情况</h2>
        <ArrayEditor
          :items="resume.trophyHistory"
          :labels="{ trophyName: '获奖名称', trophyTime: '获奖时间' }"
        />
      </li>
      <li v-bind:class="{ active: currentTab === 5 }">
        <h2>联系方式</h2>
        <el-form>
          <el-form-item label="qq">
            <el-input v-model="resume.contacts.qq"></el-input>
          </el-form-item>
          <el-form-item label="微信">
            <el-input v-model="resume.contacts.wchat"></el-input>
          </el-form-item>
          <el-form-item label="邮箱">
            <el-input v-model="resume.contacts.email"></el-input>
          </el-form-item>
          <el-form-item label="电话">
            <el-input v-model="resume.contacts.phone"></el-input>
          </el-form-item>
        </el-form>
      </li>
    </ol>
  </div>
</template>

<script>
import ProfileEditor from "./ProfileEditor";
import ArrayEditor from "./ArrayEditor";

export default {
  components: {
    ProfileEditor,
    ArrayEditor,
  },
  props:['resume'],
  data() {
    return {
      currentTab: 0,
      icons: [
        "credentials_icon",
        "gongzuobao",
        "book",
        "shoucang",
        "trophy",
        "icon_dianhua",
      ],
    };
  },
  created() {},
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
  > .panes {
    flex: 1;
    .container {
      position: relative;
      .el-icon-error {
        position: absolute;
        right: 0;
        top: 0;
      }
    }
    > li {
      display: none;
      padding: 32px;
      height: 100%;
      overflow: auto;
      &.active {
        display: block;
      }
    }
  }
}
</style>
