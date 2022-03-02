<template>
  <section v-show="ResumeContent.show">
    <header class="section-head">
      <h2 class="section-title">{{ ResumeContent.head.title }}
        &nbsp;<span v-show="ResumeContent.head.subtitle!=null">|</span>&nbsp;
        <small class="section-subtitle">{{ ResumeContent.head.subtitle }}</small></h2>
    </header>
    <div class="section-content" v-show="ResumeContent.contents!=null">
      <div class="section-item" v-for="item of ResumeContent.contents" :key="item.name">
        <header class="item-head">
          <h3 class="item-name">{{ item.name }}
            &nbsp;<span v-show="item.subtitle!=null">|</span>&nbsp;
            <small class="section-subtitle">{{ item.subtitle }}</small></h3>
          <span class="item-time">{{ item.time }}</span>
        </header>
        <div class="item-content">
          <div class="item-sentence" v-for="sentence of item.sentences" :key="sentence">
            {{ sentence }}
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
defineProps<{
  ResumeContent: {}
}>()

</script>

<style lang="less" scoped>
@import "/src/assets/css/comment";

section {
  padding: 13px 50px;
  overflow: hidden;

  .section-head {
    position: relative;
    height: 30px;
    margin: 10px auto 8px;
    overflow: hidden;
    border-bottom: 1.5px solid darken(@color-main, 2%);

    .section-title {
      position: relative;
      min-width: 100px;
      margin: 0 auto;
      font-size: @main-heading-font-size;
      line-height: @main-heading-font-size;
      font-weight: bolder;
      text-align: center;
    }

  }

  .section-subtitle {
    font-size: @subtitle-font-size;
    line-height: @subtitle-font-size;
  }

  .section-content {
    overflow: hidden;

    + .section-content {
      margin-top: 2px;
    }
  }

  .section-content {
    line-height: 25px;
    text-align: justify;
    word-break: break-all;
    margin-bottom: 2px;
  }
}

.item-head {
  position: relative;
  padding: 3px 0;
  font-weight: bold;
  line-height: 22px;
  overflow: hidden;

  .iconfont {
    color: @color-main;
  }

  .item-time {
    float: right;
    font-size: @date-font-size;
    @media screen and (max-width: 720px) {
      width: 100%;
      margin-bottom: 5px;
    }
  }

  .item-name {
    float: left;
    font-size: @title-font-size;
    font-weight: bold;
  }
}

.item-content {
  margin-bottom: 6px;
}


</style>
