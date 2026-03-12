<script lang="ts" setup>
import { ElIcon } from 'element-plus'
import { Document, Files, MagicStick, Picture, DataAnalysis, Film } from '@element-plus/icons-vue'
const newsList = [
    "[2026-02-12] Personal homepage officially launched.",
    "[2026-02-10] Top 10 Outstanding Student Award, 2025, Institute of Big Data Science and Industry.",
  " [2026-01-26] 🎉🎉 1 paper has been accepted by ICLR 2026! 🎉🎉",
]


// 个人信息
const profile = {
  name: "Zizheng Jiu 酒子峥",
  photo: "./jiu.jpg", // 4:3比例头像
  bio: "Shanxi University | M.Sc.",
  contact: [
    { type: "Email", label: "Email", link: "mailto:jiu03699@gmail.com" },
    { type: "GitHub", label: "GitHub", link: "" },
    { type: "Bilibili", label: "Bilibili", link: "https://space.bilibili.com/441386401?spm_id_from=333.788.0.0" },
  ]
}

// 右侧导航菜单
const menuItems = [
  { name: "🔎 About Me", link: "#about",desc: "I am a 3rd-year Master’s student at the Institute of Big Data Science and Industry, Shanxi University, focusing on Image Clustering, Multi-Modal Foundation Models, and AI for Science (AI4Sports), supervised by Prof. Yuhua Qian and Assoc. Prof. Feijiang Li. I completed my undergraduate studies in Automation at Jiangsu University.\n" +
        "\n" +
        "I am passionate about sports, with football as my main discipline, and I also enjoy running, swimming, and fitness training. I emphasize scientific and functional training and am keen on applying my knowledge in computer science and AI to make sports training more effective and data-driven. I believe that technology is not something distant or unattainable—it should serve everyone, helping people achieve better performance and a healthier lifestyle."  },
  { name: "📢 News", link: "#news" },
  { name: "📝 Research", link: "#research" },
]
const researchList = [
  {
    title: "Spatial Structure and Selective Text Jointly Facilitate Image Clustering",
    authors: "Zizheng Jiu*, Feijiang Li*, Jieting Wang, Yuhua Qian✉️, Lu Chen",
    venue: "ICLR 2026",
    image: "./papers/SATC.jpg",   // 架构图小图
    paper: "https://arxiv.org/abs/xxxx",
    webpage: "https://zizhjiu.github.io/project-page",
    code: "https://github.com/zizhjiu/project"
  }
]

</script>

<template>
  <div class="container">
    <!-- 左侧个人信息 -->
    <div class="left-panel">
      <el-image :src="profile.photo" class="profile-photo" fit="cover" />
      <h2 class="profile-name">{{ profile.name }}</h2>
      <p class="profile-bio">{{ profile.bio }}</p>

      <div class="contact-row">
        <span class="contact-item">
          📍Taiyuan, China
        </span>

        <a
          v-for="c in profile.contact"
          :key="c.type"
          :href="c.link"
          target="_blank"
          class="contact-item"
        >
          <span v-if="c.type === 'Email'">✉️</span>
          <span v-if="c.type === 'GitHub'">🐙</span>
          <span v-if="c.type === 'Bilibili'">📺</span>
          {{ c.label }}
        </a>
      </div>
    </div>

    <!-- 右侧内容 -->
    <div class="right-panel">
      <ul class="menu-list">

        <!-- About -->
        <li id="about">
          <a href="#about">🔎 About Me</a>
          <p class="menu-desc">{{ menuItems[0].desc }}</p>
        </li>

        <!-- News -->
        <li id="news">
          <a href="#news">📢 News</a>
          <p
            v-for="(n, idx) in newsList"
            :key="idx"
            class="news-text"
          >
            {{ n }}
          </p>
        </li>

        <!-- Research -->
        <li id="research">
          <a href="#research">📝 Research</a>

          <div class="paper-list">
            <div
              v-for="(paper, idx) in researchList"
              :key="idx"
              class="paper-item"
            >
              <!-- 左侧架构图 -->
              <div class="paper-image">
                <el-image
                  :src="paper.image"
                  fit="contain"
                  class="paper-img"
                />
              </div>

              <!-- 右侧论文信息 -->
              <div class="paper-info">
                <div class="paper-title">
                  {{ paper.title }}
                </div>

                <div class="paper-authors">
                  {{ paper.authors }}
                </div>

                <div class="paper-venue">
                  {{ paper.venue }}
                </div>

                <div class="paper-links">
                  <a href="https://openreview.net/forum?id=3DOgmfZ2k6&referrer=%5BAuthor%20Console%5D(%2Fgroup%3Fid%3DICLR.cc%2F2026%2FConference%2FAuthors%23your-submissions)" target="_blank">📄 Paper</a>
                  <a :href="paper.webpage" target="_blank">🌐 Webpage</a>
                  <a :href="paper.code" target="_blank">💻 Code</a>
                </div>
              </div>
            </div>
          </div>
        </li>

      </ul>
    </div>
  </div>
</template>


<style scoped>
/* 整体容器，限制最大宽度为 A4 */
.container {
  display: flex;
  flex-direction: row;
  padding: 20px;
  min-height: auto;
  font-family: "Arial", sans-serif;

  max-width: 2000px;  /* A4纸宽度约 794px */
  margin: 0 auto;    /* 居中 */
}

/* 左侧个人信息 */
.left-panel {
  flex: 0.8;
  padding-right: 5px;  /* 缩小右侧间距 */
  text-align: center;
}

/* 头像，4:3比例 */
.profile-photo {
  width: 100%;
  max-width: 240px;  /* 限制最大宽度 */
  aspect-ratio: 3 / 4;
  border-radius: 8px;
  box-shadow: #ccc 0px 0px 6px 2px;
  margin-bottom: 20px;
}

/* 姓名 */
.profile-name {
  font-size: 24px;
  margin-bottom: 10px;
  font-weight: bold;
}

/* 简介 */
.profile-bio {
  font-size: 18px;
  margin-bottom: 20px;
  line-height: 1.5;
}

/* 联系方式 */
.contact-info p {
  font-size: 16px;
  margin-bottom: 6px;
}
.contact-info a {
  color: #42B883;
  text-decoration: none;
}
.contact-info a:hover {
  text-decoration: underline;
}

/* 右侧菜单 */
.right-panel {
  flex: 2;
  border-left: 2px solid #f0f0f0;
  padding-left: 50px; /* 缩小左侧间距 */
}
.menu-list {
  list-style: none;
  padding: 0;
  font-size: 30px;
}
.menu-list li {
  margin-bottom: 25px;
}
.menu-desc {
  font-size: 20px;
  color: #888;
  margin-top: 4px;
  max-width: 1400px;
  /* 两端对齐 */
  text-align: justify;
  text-align-last: left; /* 最后一行左对齐 */
  white-space: pre-line;
}
.menu-list a {
  text-decoration: none;
  color: #444;
  font-weight: bold;
  font-size: 28px;
}
.menu-list a:hover {
  color: #42B883;
}
.news-text {
  font-size: 20px;
  color: black;
  margin-top: 14px;
  font-weight: 600;
  line-height: 1.5;
}
.contact-row {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  gap: 18px;
  margin-top: 12px;
  font-size: 16px;
  color: #444;
}

.contact-item {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  text-decoration: none;
  color: inherit;
  font-weight: 500;
  transition: all 0.2s ease;
}

.contact-item:hover {
  color: #42B883;
  transform: translateY(-1px);
}
/* 论文列表 */
.paper-list {
  margin-top: 18px;
  display: flex;
  flex-direction: column;
  gap: 18px;
}

/* 单篇论文 */
.paper-item {
  display: flex;
  gap: 20px;
  padding: 16px 18px;
  border-radius: 12px;
  background: #fafafa;
  transition: all 0.25s ease;
}

.paper-item:hover {
  box-shadow: 0 6px 18px rgba(0,0,0,0.06);
  transform: translateY(-2px);
}

/* 左侧图片 */
.paper-image {
  flex: 0 0 200px;
}

.paper-img {
  width: 100%;
  height: 120px;
  object-fit: contain;
  border-radius: 8px;
  border: 1px solid #eee;
}

/* 右侧内容 */
.paper-info {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

/* 题目 */
.paper-title {
  font-size: 20px;
  font-weight: 700;
  line-height: 1.35;
  margin-bottom: 4px;
}

/* 作者 */
.paper-authors {
  font-size: 15px;
  color: #666;
}

/* 会议 */
.paper-venue {
  font-size: 15px;
  font-weight: 600;
  color: #42b883;
  margin: 4px 0 6px;
}

/* 按钮区域 */
.paper-links {
  display: flex;
  gap: 14px;
}

.paper-links a {
  font-size: 14px;
  font-weight: 600;
  color: #444;
  text-decoration: none;
  padding: 5px 12px;
  border-radius: 20px;
  border: 1px solid #ddd;
  transition: all 0.2s ease;
}

.paper-links a:hover {
  color: #42b883;
  border-color: #42b883;
  background: rgba(66,184,131,0.08);
}



/* 手机端自动换行 */
@media (max-width: 900px) {
  .container {
    flex-direction: column;
    max-width: 100%;
    padding: 10px;
  }
  .right-panel {
    border-left: none;
    border-top: 2px solid #f0f0f0;
    padding-left: 0;
    padding-top: 20px;
  }
}
</style>

