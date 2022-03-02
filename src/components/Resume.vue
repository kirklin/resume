<script setup lang="ts">
import ResumeHeader from "./ResumeItem/ResumeHeader.vue";
import ResumeFooter from "./ResumeItem/ResumeFooter.vue";
import ResumeContent from "./ResumeItem/ResumeContent.vue";
import {reactive, watch} from "vue";

const initData = {
  Setting: {},
  Resume: {
    ResumeHeader: {
      name: {
        ChineseName: "林**",
        EnglishName: "Kirk Lin"
      },
      job: {
        name: "Java后端工程师",
        location: "上海"
      },
      info: {
        sex: "男",
        birthday: "2001.10",
        phone: "159********",
        email: "linkirk@163.com",
        website: "https://github.com/kirklin",
        other: ["***大学 · 计算机应用技术 · 专业成绩前百分之1"]
      }
    },
    ResumeContent: [
      {
        show: false,
        head: {title: "实习经历"},
        contents: [
          {
            name: "某某某某某某有限公司",
            subtitle: "全栈工程师",
            time: "2021年11月 - 2022年01月",
            sentences: [
              "负责公司的某某某某某某项目架构设计及研发",
            ]
          }
        ]
      },
      {
        show: true,
        head: {title: "项目经历", subtitle: null},
        contents: [
          {
            name: "公共计算机实验室预约系统",
            subtitle: null,
            time: "2021年03月 - 2021年06月",
            sentences: [
              "预约系统可以快速查询到未来一段时期内计算机实验室的教学安排，学生可以根据自己对不同课程的实际掌握能力，自主选取相关模块参与学习",
              "本人独自负责项目的架构设计及研发，流程图及开发文档，用两个月的时间独立开发了初版的前后端分离系统，集成了预约模块、学生数据导入导出、数据统计、联动学校教务系统等功能。",
              "该项目成功部署至学校内网供全校师生使用, 通过Spring Boot、Vue、MySQL、Druid、Redis、作为主要技术选型。日均PV 1000+",
              "采用Spring Security进行安全认证服务, Druid进行线上SQL监控",
            ]
          }, {
            name: "KK商城",
            subtitle: null,
            time: "2021年07月 - 2021年10月",
            sentences: [
              "KK商城是一套电商微服务项目, 包括前台商城系统以及后台管理系统,系统包括：用户登录、注册、商品搜索、商品详情、购物车、下订单流程、秒杀活动等模块。",
              "基于 Spring Boot、 Spring Cloud Alibaba、Mybatis Plus、 Redis 实现, 采用 Docker 容器化部署。",
              "使用 Redis 分布式锁以及RabbitMQ消息队列对电商业务进行解耦",
              "通过本项目, 我认识到了基础的微服务项目搭建过程。"
            ]
          }
        ]
      }, {
        show: true,
        head: {title: "荣誉奖项"},
        contents: [
          {
            subtitle: "2021年 国家奖学金",
            time: "2021年12月"
          }, {
            subtitle: "2021年 全国大学生软件测试大赛全国总决赛特等奖",
            time: "2021年10月"
          }, {
            subtitle: "2021年 GPLT团体程序设计天梯赛全国总决赛铜奖",
            time: "2021年05月"
          }, {
            subtitle: "2021年 第十二届蓝桥杯全国软件和信息技术专业人才大赛C/C++程序设计赛项全国总决赛三等奖",
            time: "2021年05月"
          }, {
            subtitle: "2020年全国大学生软件测试大赛全国总决赛特等奖",
            time: "2020年10月"
          }, {
            subtitle: "2020年 第十一届蓝桥杯全国软件和信息技术专业人才大赛JAVA程序设计赛项全国总决赛三等奖",
            time: "2020年10月"
          }
        ]
      }, {
        show: true,
        head: {title: "专业技能"},
        contents: [{
          subtitle: "熟悉 Java基础语法, 集合, 多线程 等",
        }, {
          subtitle: "掌握 MySQL数据库的常用语法,了解主流开源 NoSQL (Redis)的使用",
        }, {
          subtitle: "掌握应用服务器软件 Tomcat, Nginx等容器配置和部署, 会使用Linux系统",
        }, {
          subtitle: "掌握 Spring、Spring MVC、Mybatis、Spring Boot、等主流框架。",
        }, {
          subtitle: "了解 Spring Cloud。",
        }, {
          subtitle: "熟练使用 Selenium 进行页面测试, 构建单元测试, 自动化测试",
        }, {
          subtitle: "掌握 TypeScript、Vue等主流前端技术, 对后端到前端的技术有一定的认识，熟悉网站开发流程。",
        }
        ]
      },

    ],
    ResumeFooter: {}
  }
};

let data = reactive(JSON.parse(<string>localStorage.getItem("ResumeData")) == null ? initData : JSON.parse(<string>localStorage.getItem("ResumeData")));

watch(data, (newValue, oldValue) => {
  console.log('data变化了', newValue.Resume.ResumeContent, oldValue.Resume.ResumeContent)
  localStorage.setItem("ResumeData", JSON.stringify(data))
})

</script>

<template>
  <div class="main">
    <ResumeHeader :ResumeHeader="data.Resume.ResumeHeader"/>
    <ResumeContent :ResumeContent=item v-for="item of data.Resume.ResumeContent"/>
    <ResumeFooter :ResumeFooter="data.Resume.ResumeFooter"/>
  </div>
</template>

<style lang="less">
@import "/src/assets/css/comment";

* {
  box-sizing: border-box;
}

body {
  position: relative;
  -webkit-font-smoothing: antialiased;
  -webkit-text-size-adjust: none;
  font-family: @font-family;
  font-size: @text-font-size;
  line-height: 22 / 14;
  color: @color-font-content;
  background-color: @color-background;
  padding-top: 5px;
  overflow: auto;
  @media screen and (max-width: 1024px) {
    padding-top: 0;
  }
}

.main {
  position: relative;
  width: 1024px;
  margin: 40px auto;
  background-color: #fff;
  border-radius: 5px;
  box-shadow: 0 0 15px #c0c0c0;
  overflow: hidden;
  transition: all .2s ease-in-out;
  opacity: 0;
  transform: translate3d(0, 50px, 0);
  animation: fadeUp 2s cubic-bezier(0.19, 1, 0.22, 1) forwards;
  @keyframes fadeUp {
    from {
      opacity: 0;
      transform: translate3d(0, 50px, 0);
    }
    to {
      opacity: 1;
      transform: translate3d(0, 0, 0);
    }
  }
  @media screen and (max-width: 1024px) {
    width: 100%;
    margin: 0;
    border-radius: 0;
  }
}
//控制打印样式
@media print {
  body {
    padding-top: 0;
  }

  .main {
    width: 1024px;
    height: 1450px; // A4 大小
    margin: 0 auto;
    border-radius: 0;
    box-shadow: none;
  }
}


</style>
