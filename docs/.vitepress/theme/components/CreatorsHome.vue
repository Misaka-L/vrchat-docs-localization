<template>
  <Banner
    title="成为一名 VRChat 创作者"
    subtitle="利用我们的工具和文档来学习，创作，分享。"
  />

  <div class="links-group">
    <HomeLinkButton
      text="开始入门"
      link="/creators.vrchat.com/getting-started"
      description="我们鼓励创作与分享。欢迎您的到来！"
      icon="/assets/getting-started.png"
    />
    <HomeLinkButton
      text="世界"
      link="/creators.vrchat.com/worlds/"
      description="风景，故事，玩法，由您决定！"
      icon="/assets/worlds.png"
    />
    <HomeLinkButton
      text="虚拟形象"
      link="/creators.vrchat.com/avatars/"
      description="挥洒个性，打造您专属的虚拟形象！"
      icon="/assets/avatars.png"
    />
  </div>
</template>

<script setup lang="ts">
import Banner from './Banner.vue'
import HomeLinkButton from './HomeLinkButton.vue';
</script>

<style scoped>
.links-group {
    display: flex;
    justify-items: center;
    flex-wrap: wrap;

    margin: 0 1rem;
}

@media screen and (min-width: 500px) {
    .links-group .button-container {
        flex: 0 0 33.33333%;
    }
}

@media screen and (min-width: 800px) {
    .links-group {
        margin: 0 5rem;
    }
}

@media screen and (min-width: 1200px) {
    .links-group {
        margin: 0 15rem;
    }
}
</style>