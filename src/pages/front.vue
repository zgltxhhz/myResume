<template>
  <div class="main-container" v-show="$parent.loading" style="display: none;">
    <div class="useful-link no-print">      
    </div>
    <section class="section section-header">
      <div class="section-bg section-header-bg"></div>
      <div class="section-bg section-content-bg"></div>
      <div class="container">
        <header class="header">
          <div class="header-box">
            <div class="avatar wow inShow no-print">
              <img src="../../public/img/logo.jpg" alt="logo" class="img-responsive">
            </div>
            <h1 class="name text-center wow inShow no-print">{{userInfo.nickname}}</h1>
            <h1 class="name text-center hide show-print-block">{{userInfo.name}}</h1>
          </div>
        </header>
        <div class="section-content">
          <div class="content-box">
            <div class="name-slogan">
              <h2 class="wow inShow no-print" data-wow-delay="0.1s">
                <span class="text-light">{{userInfo.lastName}}</span>&nbsp;{{userInfo.firstName}}
              </h2>
              <div class="description wow inShow" data-wow-delay="0.15s">{{userInfo.intention}}</div>
              <div class="description wow inShow" data-wow-delay="0.15s">{{userInfo.salary}}</div>
            </div>
            <div class="contact-info">
              <div class="row">
                <div class="col-md-6 col-lg-3">
                  <div class="item wow inShow" data-wow-delay="0.3s">
                    <h4>性别</h4>
                    <div class="info">{{userInfo.sex}}</div>
                  </div>
                </div>
                <div class="col-md-8 col-lg-3">
                  <div class="item wow inShow" data-wow-delay="0.45s">
                    <h4>年龄</h4>
                    <div class="info">{{calcDate(userInfo.birthday)}}</div>
                  </div>
                </div>
                <div class="col-md-6 col-lg-3">
                  <div class="item wow inShow" data-wow-delay="0.3s">
                    <h4>毕业学校</h4>
                    <div class="info">{{userInfo.school}}</div>
                  </div>
                </div>
                <div class="col-md-8 col-lg-3">
                  <div class="item wow inShow" data-wow-delay="0.5s" :href="'mailto:'+userInfo.email">
                    <h4>学历</h4>
                    <div class="info">{{userInfo.education}}</div>
                  </div>
                </div>
              </div>
              <div class="row">
              <div class="col-md-6 col-lg-3">
                  <a class="item wow inShow" data-wow-delay="0.55s">
                    <h4>专业</h4>
                    <div class="info">{{userInfo.major}}</div>
                  </a>
                </div>
                <div class="col-md-6 col-lg-3">
                  <a class="item wow inShow" data-wow-delay="0.55s">
                    <h4>经验</h4>
                    <div class="info">一年零两个月</div>
                  </a>
                </div>
                <div class="col-md-8 col-lg-3">
                  <div class="item wow inShow" data-wow-delay="0.6s">
                    <h4>电话</h4>
                    <address class="info">{{userInfo.phone}}</address>
                  </div>
                </div>
                <div class="col-md-6 col-lg-3">
                  <div class="item wow inShow" data-wow-delay="0.65s">
                    <h4>邮箱</h4>
                    <div class="info">{{userInfo.qq.email}}</div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section class="section">
      <div class="container">
        <div class="section-bg section-header-bg"></div>
        <div class="section-bg section-content-bg"></div>
        <header class="header">
          <div class="content-box">
            <h2 class="title">介绍&nbsp;/&nbsp;
              <small><i>Intro</i></small>
            </h2>
            <div class="description">介绍一些个人基本情况</div>
          </div>
        </header>
        <div class="section-content">
          <div class="intro">
            <p v-for="(intro,idx) in userInfo.intro.content" :key="idx" v-html="intro"></p>
          </div>
          <div class="technology">
            <ul class="inline">
              <li><b>{{userInfo.intro.technology.title}}</b></li>
              <li v-for="item in userInfo.intro.technology.content" :key="item">{{item}}</li>
            </ul>
          </div>
        </div>
      </div>
    </section>
    <section class="section">
      <div class="container">
        <div class="section-bg section-header-bg"></div>
        <div class="section-bg section-content-bg"></div>
        <header class="header">
          <div class="content-box">
            <h2 class="title">工作经验&nbsp;/&nbsp;
              <small><i>Experience</i></small>
            </h2>
            <div class="description">对之前的工作经历做一个介绍</div>
          </div>
        </header>
        <div class="section-content">
          <div class="experience">
            <div class="item" v-for="item in userInfo.experience" :key="item.title">
              <div class="row">
                <div class="col-md-5">
                  <div class="time">{{item.time}}</div>
                  <div class="title">{{item.title}}</div>
                  <div class="description">{{item.intro}}</div>
                </div>
                <div class="col-md-7">
                  <div class="content">{{item.description}}</div>
                  <div class="tips" v-for="tip in item.tips" :key="tip.title">
                    <b>{{tip.title}}</b>
                    <ul>
                      <li v-for="list in tip.content" :key="list">{{list}}</li>
                    </ul>
                  </div>
                  <div class="technology" v-for="tech in item.technology" :key="tech.title">
                    <b>{{tech.title}}</b>
                    <ul class="inline">
                      <li v-for="techItem in tech.content" :key="techItem">{{techItem}}</li>
                    </ul>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section class="section">
      <div class="container">
        <div class="section-bg section-header-bg"></div>
        <div class="section-bg section-content-bg"></div>
        <header class="header">
          <div class="content-box">
            <h2 class="title">技能&nbsp;/&nbsp;
              <small><i>Skills</i></small>
            </h2>
            <div class="description">我所掌握的工具和技术栈</div>
          </div>
        </header>
        <div class="section-content">
          <div class="row skill">
            <div class="col-md-6" v-for="skill in userInfo.skill" :key="skill.name">
              <div class="item">
                <div class="text-info">
                  <span class="num text-light">{{skill.percent}}</span>{{skill.name}}
                </div>
                <div class="progress">
                  <div class="progress-bar wow progressShow" :style="'width:'+skill.percent"></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section class="section">
      <div class="container">
        <div class="section-bg section-header-bg"></div>
        <div class="section-bg section-content-bg"></div>
        <header class="header">
          <div class="content-box">
            <h2 class="title">项目经验&nbsp;/&nbsp;
              <small><i>Experience</i></small>
            </h2>
            <div class="description">这展示了我的部分项目</div>
          </div>
        </header>
        <div class="section-content">
          <div class="experience">
            <div class="item" v-for="item in userInfo.project" :key="item.title">
              <div class="row">
                <div class="col-md-5">
                  <div class="time">{{item.time}}</div>
                  <div class="title">{{item.title}}</div>
                  <div class="description">{{item.intro}}</div>
                </div>
                <div class="col-md-7">
                  <div class="content">{{item.description}}</div>
                  <div class="tips" v-for="tip in item.tips" :key="tip.title">
                    <b>{{tip.title}}</b>
                    <ul>
                      <li v-for="list in tip.content" :key="list">{{list}}</li>
                    </ul>
                  </div>
                  <div class="technology" v-for="tech in item.technology" :key="tech.title">
                    <b>{{tech.title}}</b>
                    <ul class="inline">
                      <li v-for="(techItem,techItemIndex) in tech.content" :key="techItemIndex">{{techItem}}</li>
                    </ul>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section class="section">
      <div class="container">
        <div class="section-bg section-header-bg"></div>
        <div class="section-bg section-content-bg"></div>
        <header class="header">
          <div class="content-box">
            <h2 class="title">自我评价&nbsp;/&nbsp;
              <small><i>Evaluate</i></small>
            </h2>
            <div class="description">我对于我自己的一些看法</div>
          </div>
        </header>
        <div class="section-content">
          <div class="row usually">
            <div v-for="(item, index) in userInfo.evaluate" :key="index">
              {{item}}
            </div>
          </div>
        </div>
      </div>
    </section>
    <section class="section no-print">
      <div class="container">
        <div class="section-bg section-header-bg"></div>
        <div class="section-bg section-content-bg"></div>
        <header class="header">
          <div class="content-box">
            <h2 class="title">联系&nbsp;/&nbsp;
              <small><i>Contact</i></small>
            </h2>
            <div class="description">通过这些信息可以联系到我</div>
          </div>
        </header>
        <div class="section-content">
          <div class="contact">
            <div class="row">
              <div class="col-md-6 col-lg-3">
                <div class="item">
                  <h4>电话</h4>
                  <div class="info">{{userInfo.phone}}</div>
                </div>
              </div>
              <div class="col-md-6 col-lg-3">
                <div class="item">
                  <h4>QQ</h4>
                  <div class="info">{{userInfo.qq.number}}</div>
                </div>
              </div>
              <div class="col-md-6 col-lg-3">
                <div class="item">
                  <h4>微信</h4>
                  <div class="info">{{userInfo.location}}</div>
                </div>
              </div>
              <div class="col-md-6 col-lg-3">
                <div class="item">
                  <h4>Email</h4>
                  <div class="info">{{userInfo.qq.email}}</div>
                </div>
              </div>
            </div>
          </div>
          <div class="name-slogan">
            <h2 class="wow inShow">
            </h2>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
  export default {
    name: 'front',
    data() {
      return {
        userInfo: {
          exp:[],
          qq:{},
          intro:{
            content:[],
            technology:{
              title:'',
              content:[]
            }
          },
          experience:[{
            tips:{
              title:'',
              content:[],
            },
            technology:[],
          }],
          skill:[],
          project:[{
            tips:{
              title:'',
              content:[],
            },
            technology:[],
          }],
          usually:[],
        },
      }
    },
    created(){
      var self = this;
      this.$http.get('resume.json').then((res) =>{
        console.log(res.data)
        self.userInfo = res.data;
        this.$parent.loading = true;
      });
    },
    methods:{
      calcDate(birthday){
        let birthdayDate = new Date(birthday);
        let todyDate = new Date();
        return todyDate.getYear() - birthdayDate.getYear()
      }
    }
  }
</script>
