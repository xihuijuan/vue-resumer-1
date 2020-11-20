<template>
  <div class="preview">
    <h1>{{ resume.profile.name || "请填写名字" }}</h1>
    <p>
      {{ resume.profile.city || "请填写居住地" }} |
      {{ resume.profile.birth || "请填写生日" }}
    </p>
    <!-- 工作经历 -->
    <section v-if="filter(resume.workHistory).length > 0">
      <hr />
      <h2>工作经历</h2>
      <ul>
        <li v-for="work in filter(resume.workHistory)">
          {{ work.company }}
          {{ work.content }}
        </li>
      </ul>
    </section>
    <!-- 学习经历 -->
    <section v-if="filter(resume.studyHistory).length > 0">
      <hr />
      <h2>学习经历</h2>
      <ul>
        <li v-for="study in filter(resume.studyHistory)">
          {{ study.school || "请填写学校" }}
          {{ study.duration || "请填写毕业时间" }}
          {{ study.degree || "请填写学历" }}
        </li>
      </ul>
    </section>
    <!-- 项目经历 -->
    <section v-if="filter(resume.projects).length > 0">
      <hr />
      <h2>项目经历</h2>
      <ul>
        <li v-for="project in filter(resume.projects)">
          {{ project.name }}
          {{ project.content }}
        </li>
      </ul>
    </section>
    <!-- 获奖历史 -->
    <section v-if="filter(resume.trophyHistory).length > 0">
      <hr />
      <h2>获奖历史</h2>
      <ul>
        <li v-for="trophy in filter(resume.trophyHistory)">
          {{ trophy.trophyName }}
          {{ trophy.trophyTime }}
        </li>
      </ul>
    </section>
    <!-- 联系方式 -->
    <hr />
    <h2>联系方式</h2>
    <ul>
      <li><h3>QQ：</h3>{{ resume.contacts.qq || "请填写QQ" }}</li>
      <li><h3>微信：</h3>{{ resume.contacts.wchat || "请填写微信" }}</li>
      <li><h3>邮箱：</h3>{{ resume.contacts.email || "请填写邮箱" }}</li>
      <li><h3>电话：</h3>{{ resume.contacts.phone || "请填写电话" }}</li>
    </ul>
  </div>
</template>
<script>
export default {
  props: ["resume"],
  methods: {
    filter(array) {
      //找出非空对象
      return array.filter((item) => !this.isEmpty(item));
    },
    isEmpty(object) {
      //只要有一个value不是false，就返回false
      let empty = true;
      for (let key in object) {
        if (object[key]) {
          empty = false;
          break;
        }
      }
      return empty;
    },
  },
};
</script>
<style>
.preview {
}
h3{
  display: inline;
}
</style>