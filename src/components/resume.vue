<!--
 * @Author: zn 610039061@qq.com
 * @Date: 2020-04-11 18:05:14
 * @LastEditTime: 2020-04-21 17:10:29
 * @Description: 简历
 -->
<template>
  <div class="page-resume" id="pageResume">
    <!-- 左侧个人信息 -->
    <div class="resume-aside">
      <div class="aside-content">
          <img src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1587472653390&di=a4e1c8d8ba5c8dd1d8e87d527d2cc5a6&imgtype=0&src=http%3A%2F%2Fimg.jk51.com%2Fimg_jk51%2F353045950.jpeg" class="aside-portrait">
          <div class="personal-desc">
              <p>娜娜aa</p>
              <p> Web前端开发工程师 </p>
              <p> 女 / 1992.05 </p>
              <span class="work-year">3年工作经验</span>
          </div>
          <div class="aside-preview">
              <p>
                  <span>邮箱:</span>
                  <a href="mailto:610039061@qq.com">610039061@qq.com</a>
              </p>
              <p>
                  <span>电话:</span>
                  <a href="tel:13711504803">13711504803</a>
              </p>
              <p>
                  <i></i>
                  <!-- <a onclick="window.open('https://zengnaxianlin.github.io')">https://zengnaxianlin.github.io</a> -->
              </p>
              <p>
                  <p>到岗时间: 一周内</p>
                  <p>期望薪资: 12k</p>
              </p>
          </div>
          <div class="black-item mt16">
              <div class="header-title">
                  <p>教育经验</p>
              </div>
              <p>宜春学院<br/>数学与计算机学院</p>
              <p>2012.09 - 2016.06</p>
              <p>计算机科学与技术 - 本科</p>
              <p>英语四级, 励志奖学金, 学习委员</p>
          </div>
          <div class="black-item" v-if="workExperience">
              <div class="header-title">
                  <p>工作经验</p>
              </div>
              <div class="work-exp" v-for="(item,index) in workExperience" :key="index">
                <p class="work-exp-company">{{item.companyName}}</p>
                <p class="work-time">{{item.time}}</p>
                <p class="work-exp-main">主要职责: {{item.mainWork}}</p>
              </div>
          </div>
          <div class="black-item" v-if="personalEvaluation1">
              <div class="header-title">
                  <p>技术栈</p>
              </div>
              <ul class="person-introduction">
                  <li v-for="(item,index) in personalEvaluation1" :key="index" v-html="item"></li>
              </ul>
          </div>
          <div class="black-item" v-if="personalEvaluation">
              <div class="header-title">
                  <p>个人评价</p>
              </div>
              <ul class="person-introduction">
                  <li v-for="(item,index) in personalEvaluation" :key="index" v-html="item"></li>
              </ul>
          </div>
      </div>
    </div>
    <!-- 右侧个人内容 -->
    <div class="resume-content">
      <div>
        <div class="black-item" v-if="projects">
            <div class="header-title">
                <p>项目经验</p>
            </div>
            <div v-for="(item,index) in projects" :key="index" class="project">
              <p class="pro-name">
                {{ item.projectName }}
                <span class="pro-time">{{ item.time }}</span>
              </p>
              <p><span class="pro-title">主要技术: </span><span v-html="item.mainSkills"></span></p>
              <p class="pro-production"><span class="pro-title">项目描述: </span>{{ item.production }}</p>
              <p class="pro-modules"><span class="pro-title">主要模块: </span>{{ item.modules }}</p>
              <p class="pro-modules" v-if="item.works"><span class="pro-title">主要职责: </span>{{item.works}}</p>
              <p v-if="item.addr"><span class="pro-title">项目地址: </span><a :href="item.addr" target="_blank">{{ item.addr }}</a></p>
            </div>
        </div>
      </div>
    </div>
    <!-- 下载简历 -->
    <div class="pdf-btn" @click="getLoad">
        <a class="down" href="" download="downImg">下载简历</a>
    </div>
  </div>
</template>
<script>
export default {
  name: 'resume',
  data () {
     return {
      personalEvaluation: [
          '本人有3年工作经验，有带领实习生经验，积极向上，有良好的人际沟通能力，良好的工作协调能力，踏实肯干的工作精神，不断学习新技术，对知识有强烈的求知欲，良好的前端编程能力和编程习惯，致力于代码的整体结构规范及优化',
      ],
      personalEvaluation1: [
          '具备良好的编程风格，代码简洁整齐，能熟练编写符合 <em>W3C</em> 标准的高效率代码',
          '熟悉<em>Div+Css</em>网页布局与样式，对html语义化有深刻的理解',
          '熟悉使用<em>HTML5、CSS3、Flex</em> 响应式移动网站开发',
          '熟悉使用 <em>Ajax</em>、<em>Axios</em>技术与后台交互开发',
          '熟悉使用预处理器<em>Sass</em>、<em>Less</em> 的编写，对其自动化编译成<em>Css</em>',
          '熟悉使用 <em>JavaScript</em>、<em>Vue</em>、<em>UniApp</em>、<em>Es6</em> 框架进行开发',
          '熟悉使用 <em>Node Express</em> 开发，使用基于 <em>node</em> 的各种前端构建工具 <em>gulp</em>、<em>grunt</em> 等',
          '熟悉使用<em>Photoshop</em>等设计软件',
      ],
      workExperience:[
        {
          'companyName':'深圳市盛欣德科技有限公司',
          'time':'2019-09 至 2020-04',
          'mainWork':'负责还原 UI高保真设计图,负责 PC 端、小程序的前端开发工作，设计和完成通用业务组件库的搭建工作；负责与产品、UI 和后端做良好的沟通，对产品能够提供持续的体验优化'
        },
        {
          'companyName':'广州市零空信息技术有限公司',
          'time':'2016-03 至 2018-06',
          'mainWork':'负责 Web前端开发;负责交互设计核对并实现; 配合后台完成数据交互;项目开发完成后，测试并修改BUG，优化产品性能;负责项目后期维护更新，并且不断优化。'
        }
      ],
      projects:[
      {
          'projectName':'壹优食微信小程序',
          'time':'2020-02 至 2020-04',
          'mainSkills':'<em>小程序</em>、<em>Uniapp</em> 、<em>vue</em> 、<em>Sass </em> 、<em>ES6/ES7</em>',
          'production':'壹优食小程序为用户提供菜品预订，下单及配送一整套服务，提供预订整周菜品并赠送优惠券，为用户带来美味美食的同时提供优质的服务',
          'modules':'首页菜品展示，购物车模块，配送地址、优惠券、用户周报、订单、支付等；',
          'works':'(1)选用Uniapp和vue搭建小程序框架 (2)负责还原 UI高保真设计图(3)配合后台完成所有接口请求数据(4)配合产品完成小程序项目的优化'
        },
        {
          'projectName':'壹优食后台管理系统',
          'time':'2019-11 至 2020-01',
          'mainSkills':'<em>JavaScript </em> 、<em>jQuery</em> 、<em>Layui</em>、<em>Echarts</em>、<em>less</em>',
          'production':'壹优食管理后台是配合小程序的一个管理系统，方便管理员发布最新的菜品、发布公告以及对用户订单进行处理等一系列配套的管理',
          'modules':'公告资讯、菜单管理、菜品管理、用户管理、优惠券管理、订单管理、配送地址等',
          'addr':'https://deng.jcjiaoyu.top/'
        },
        {
          'projectName':'毅起付-商家智慧助手',
          'time':'2017-06 至 2018-06',
          'mainSkills':'<em>Vue</em> 、<em>Router</em> 、<em>Vuex</em> 、<em>ElementUI</em> 、<em>Axios</em> 、<em>Webpack</em>',
          'production':'毅起付商家智慧助手是一款为线下商户提供智慧支付及营销解决方案的聚合支付产品。支持微信、支付宝、银行卡多种账户类型，灵活满足付款需求。对接多种智能收银硬件，pos机、扫码盒子、扫码枪、云喇叭等',
          'modules':'登录注册模块、会员管理、签约管理、服务商管理、商户管理、门店管理、权限管理系统、佣金管理、广告联盟等',
          'addr':'https://sjzs.hydosky.com'
        },
        {
          'projectName':'达瑞后台管理系统',
          'time':'2017-02 至 2017-06',
          'mainSkills':'<em>Vue</em> 、<em>Router</em> 、<em>Vuex</em> 、<em>ElementUI</em> 、<em>Axios</em> 、<em>Webpack</em>',
          'production':'达瑞后台管理系统提供串联质谱生物分析管理，方便管理员统一进行用户的信息录入、数据统计、异常数据、综合分析等操作',
          'modules':'登录注册模块、信息录入、数据统计、检测报告、系统设置、模板设置等',
          'addr':''
        },
        {
          'projectName':'pony马术俱乐部后台管理系统及公众号',
          'time':'2016-10 至 2017-01',
          'mainSkills':'<em>JavaScript</em>、<em>jQuery</em>、<em>hui</em>、<em>less </em>',
          'production':'宝骊国际马术俱乐部提供微信预约功能，可以预约相应的马术课程，后台管理系统方便管理员进行操作',
          'modules':'登录注册模块、会员中心、课程管理、公告管理、预约管理、订单管理',
          'addr':''
        },
        {
          'projectName':'魔法隧道官网及桌面应用',
          'time':'2016-06 至 2016-09',
          'mainSkills':'<em>Election</em>、<em>jquery</em> 、<em>bootstrap</em>',
          'production':'魔法隧道提供免费的智能网络穿透，通过自主研发的穿透技术，可供多线路支持运行，让用户无需公网IP、无需路由端口映射、不用机房托管便可轻轻松松实现家中建站、远程桌面、游戏服务器、ERP互联等功能',
          'modules':'登录注册模块、个人中心、隧道控制中心',
          'addr':'http://www.mofasuidao.cn'
        },
        {
          'projectName':'零云',
          'time':'2016-03 至 2016-06',
          'mainSkills':'<em>nodejs</em> 、<em>Express</em>、<em>ejs</em>、<em>gulp</em>、<em>mongodb</em>',
          'production':'零云的特点是能够将本地的服务进行网络穿透发布出去。即程序员可以在本地主机譬如自己的电脑上开发应用，不管是开发过程中还是开发完成后，只要通过零云和网络工具“魔法隧道”就可以随时随地将应用发布到外网,免去了配置公网IP烦恼。并且在该服务访问量增大，本机不足以支撑时，在零云上还进行自由的弹性伸缩，以保障服务的正常访问和资源有效配置，弹性、便捷又节能。',
          'modules':'登录注册、服务中心、服务编排、容器服务、镜像广场、代码构建、控制台、社区等',
          'addr':''
        },
      ]
    };
  },
  methods:{
    getLoad(){
      html2canvas(document.querySelector('#pageResume')).then(function (canvas) {
          var imgUri = canvas.toDataURL("image/png").replace("image/png", "image/octet-stream"); // 获取生成的图片的url
          window.location.href = imgUri; // 下载图片
      });
    }
  }
}
</script>

<style lang="scss" scoped>
    //$theme: #ffb6b0;
    $theme: #fb8e85;
    $textColor:#666;

    @mixin themeBg ($opacity){
        //background-color: rgba(255,182,176, $opacity);
        background-color: rgba(251,142,133, $opacity);
    }

    .page-resume{
        width: 1024px;
        min-height: 500px;
        background-color: #fff;
        margin: 50px auto;
        box-shadow: 0 0 15px silver;
        color: $textColor;
        display: flex;

        .resume-aside{
            -webkit-box-flex: 3;
            -ms-flex: 3;
            flex: 3;
            display: -webkit-box;
            display: -ms-flexbox;
            display: flex;
            -webkit-box-direction: normal;
            -ms-flex-direction: column;
            flex-direction: column;
            padding: 40px;
            background-color: #FFFAF6;
            align-items: center;
            text-align: center;

            .aside-content{

                .aside-portrait{
                    width: 150px;
                    height: 150px;
                    border-radius: 50%;
                }

                .personal-desc{

                    .work-year{
                        color: #fff;
                        @include themeBg(1);
                        padding:6px 10px;
                        border-radius:20px;
                        font-size:14px;
                    }
                }

                .aside-preview{
                    p{
                        margin-bottom: 6px;
                    }

                    a{
                        color: $textColor;
                        cursor: pointer;
                        margin-left: 10px;
                        text-decoration:underline;

                        &:hover{
                            opacity: .7;
                        }
                    }
                }

                .person-introduction{
                  padding:0;
                  font-size:14px;
                  li{
                    text-align:left;
                    padding-bottom:10px;
                  }
                }

                .header-title{
                  color: #D246B2;
                  font-size: 22px;
                  font-weight: 700;
                }

                .work-exp{
                  margin-bottom:25px;
                  text-align:left;
                  .work-exp-company{
                    font-size: 16px;
                    font-weight: 700;
                    margin-bottom:6px;
                  }
                  .work-time{
                    font-size:12px;
                    font-weight:700;
                    margin:0;
                  }
                  .work-exp-main{
                    margin:0;
                  }
                }
            }
        }

        .resume-content{
            display: flex;
            flex: 6;
            padding: 40px 30px 30px;
            .black-item{
              .header-title{
                position:relative;
                p{
                  font-size: 22px;
                  font-weight: 700;
                  text-align:center;
                  width: 200px;
                  line-height: 1.8;
                  margin: 0 auto;
                  color: white;
                  border-radius: 30px;
                  @include themeBg(1);
                }
                &:before,&:after{
                  position: absolute;
                  display: block;
                  top: 19px;
                  content: "";
                  background: $theme;
                  height: 2px;
                  width: calc(50% - 120px);
                }
                &:before{
                  left:0;
                }
                &:after{
                  right:0;
                }
              }
            }
            .project{
              font-size:14px;
              margin-top:50px;
              .pro-name{
                font-size:20px;
                font-weight:600;
                margin:0;
                .pro-time{
                  font-size:14px;
                  color:$textColor;
                  font-weight:bold;
                }
              }
              .pro-title{
                font-weight: 700;
              }
            }
            a{
                color: #333;
                cursor: pointer;
                text-decoration:underline;

                &:hover{
                    opacity: .7;
                }
            }

        }

        .black-item{
            color: #555;
            .header-title{
                p{
                    color: $theme;
                    position:relative;
                    &:before,&:after{
                      position: absolute;
                      display: block;
                      top: 16px;
                      content: "";
                      background: $theme;
                      height: 2px;
                      width: calc(50% - 60px);
                    }
                    &:before{
                      left:0;
                    }
                    &:after{
                      right:0;
                    }
                }
            }
        }

        .pdf-btn{
            line-height: 3;
            font-size: 14px;
            border-radius: 50px;
            background-color: $theme;
            position: fixed;
            right: 40px;
            bottom: 40px;
            box-shadow: 0 0 15px silver;
            cursor: pointer;

            a{
                display: block;
                padding: 0 20px;
                color: #fff;
                text-decoration:none;
                &:hover{
                  color: $theme;
                }
            }

            &:hover{
                background-color: #fff;
            }
        }
    }
    .mt16{
      margin-top:16px;
    }

    @media screen and (max-width: 1049px){
      .page-resume{
        margin:0;
        width: 100%;
        display:block;

      }
      .resume-aside{
        padding-top:80px;
      }
    }


</style>
