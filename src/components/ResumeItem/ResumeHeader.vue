<template>
  <header class="head">
    <section class="title">
      <div class="resumeName">
        <h1>{{ ResumeHeader.name.ChineseName }}<small>{{ ResumeHeader.name.EnglishName }}</small></h1>
      </div>
      <div class="resumeJob">
        <h2>{{ ResumeHeader.job.name }}<small> | {{ ResumeHeader.job.location }}</small></h2>
      </div>
    </section>
    <section class="resumeInfo">
      <h2>电话:&nbsp;{{ ResumeHeader.info.phone }}&nbsp;&nbsp;|&nbsp;&nbsp;邮箱：{{ ResumeHeader.info.email }}</h2>
      <h3>{{ ResumeHeader.info.sex }}&nbsp;&nbsp;|&nbsp;&nbsp;{{ ResumeHeader.info.birthday }}</h3>
      <h3>{{ ResumeHeader.info.website }}</h3>
      <h3 v-for="item of ResumeHeader.info.other">{{ item }}</h3>
    </section>
    <!--    <section class="avatar">-->
    <!--      <img src="/src/assets/logo.png">-->
    <!--    </section>-->
  </header>
</template>

<script setup lang="ts">

defineProps<{
  ResumeHeader: {}
}>()

</script>

<style scoped lang="less">
@import "/src/assets/css/comment";

.head {
  padding: 30px 50px;
  color: @color-font-header;
  background-color: @color-main;
  overflow: hidden;
  @media screen and (max-width: 720px) {
    padding: 25px;
  }

  .title {
    padding-bottom: 5px;
    margin-bottom: 5px;
    border-bottom: 2px solid darken(@color-main, 3%);
    font-size: 52px;
    overflow: hidden;
  }

  .resumeName,
  .resumeJob,
  .resumeInfo,
  .contact {
    width: 50%;
    @media screen and (max-width: 720px) {
      width: 100%;
      text-align: center;
    }
  }

  .resumeName,
  .resumeInfo {
    float: left;
  }

  .resumeJob,
  .contact {
    float: right;
    text-align: right;
  }

  .resumeName {
    h1 {
      font-family: @font-family-title;
      font-weight: 500;
      letter-spacing: 5px;
      @media screen and (max-width: 720px) {
        margin-top: 10px;
        letter-spacing: 0;
        line-height: 1.25;
      }

      small {
        padding-left: 10px;
        font-size: 24px;
        font-weight: 400;
        letter-spacing: 0;
        @media screen and (max-width: 720px) {
          display: block;
          padding-left: 0;
          font-size: 20px;
          line-height: 1;
        }
      }
    }
  }

  .resumeJob {
    font-weight: 300;
    -webkit-font-smoothing: subpixel-antialiased;
    @media screen and (max-width: 720px) {
      text-align: center;
    }

    h2 {
      display: inline-block;
      font-size: 24px;
      @media screen and (max-width: 720px) {
        margin: 5px auto 0;
        padding: 10px;
        border-top: 1px solid darken(@color-main, 2%);
      }

      small {
        font-size: 14px;
      }
    }
  }

  .resumeInfo {
    padding-left: 5px;
    line-height: 30px;

    h2 {
      margin: 8px 0 4px;
      font-size: 18px;
    }

    h3 {
      font-size: 16px;
    }
  }

}
</style>
