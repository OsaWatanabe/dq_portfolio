<template>
  <section>
    <div class="tools-menu">
      <div class="tools-menu-list">
        <ul>
          <li
            v-for="(tool, index) in toolsList"
            v-on:mouseleave="toolsMouseleave(index)"
            v-on:mouseover="toolsMouseover(index)"
            :key="tool.name+index"
          >
            <a class="tool-cursor" v-if="toolsChoice==index">▶</a>
            {{tool.name}}
          </li>
        </ul>
      </div>
    </div>
    <div class="tools-details" @click="toolClick">
      <div class="tools-details-list">
        <ul>
          <li
            v-for="detail in toolsList[toolsChoice].details"
            :key="toolsList[toolsChoice].name+detail.name"
          >
            <a :href="detail.link" target="_blank" v-if="detail.link!=='#'">{{detail.name}}</a>
            <span v-else>{{detail.name}}</span>
          </li>
        </ul>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  components: {},
  data: function() {
    return {
      toolsContent: "ぷろふぃーる",
      toolsChoice: 0,
      toolsList: [
        {
          name: "ぶき",
          details: [
            {
              name: "VS Code",
              link: "#"
            },
            {
              name: "Amazon Web Services",
              link: "#"
            },
            {
              name: "Git/GitLab/GitHub",
              link: "#"
            },
            {
              name: "Docker",
              link: "#"
            },
            {
              name: "Terraform",
              link: "#"
            },
            {
              name: "GitKraken",
              link: "#"
            },
            {
              name: "Netlify",
              link: "#"
            },
            {
              name: "Adobe XD",
              link: "#"
            }
          ]
        },
        {
          name: "しごとべや",
          details: [
            {
              name: "MacBook Pro 13inch",
              link: "#"
            },
            {
              name: "LG 32インチ/4K モニタ",
              link: "https://www.lg.com/jp/monitor/lg-32UK550-B"
            },
            {
              name: "iPhone 11 pro",
              link: "#"
            },
            {
              name: "iPad Pro 11inch",
              link: "#"
            },
            {
              name: "NAS Synology DS218+",
              link: "https://www.amazon.co.jp/gp/product/B075N1BYWX"
            },
            {
              name: "Raspberry Pi",
              link:
                "https://www.amazon.co.jp/RASPBERRY-PI-TSI-PI018-Clear-Raspberry-Pi3-Model/dp/B01D1FR29M"
            },
            {
              name: "Nature Remo",
              link: "https://nature.global/jp/nature-remo-mini"
            },
            {
              name: "Amazon Echo",
              link: "#"
            },
            {
              name: "Google Home mini",
              link: "#"
            },
            {
              name: "Switch Bot",
              link: "https://www.switchbot.jp/bot"
            },
            {
              name: "かなでもの杉無垢デスク",
              link: "https://kanademono.design/collections/for-dining/products/tbl-k01-bk"
            },
            {
              name: "6歳児",
              link: "#"
            },
            {
              name: "3歳児",
              link: "#"
            }
          ]
        },
        {
          name: "じれい",
          details: [
            {
              name: "このアプリのソース",
              link: "https://github.com/OsaWatanabe/dq_portfolio"
            },
            {
              name: "婚活握手会システム開発",
              link: "https://emira-t.jp/special/10485/"
            },
            {
              name: "WonderJack",
              link:
                "https://pc.watch.impress.co.jp/docs/column/gyokai/1132020.html"
            },
            {
              name: "カイゼンスイッチ",
              link:
                "https://monoist.atmarkit.co.jp/mn/articles/2002/13/news051.html"
            }
          ]
        }
      ]
    };
  },
  mounted: function() {
    this.$store.commit("pageChange", 5);
  },
  methods: {
    toolClick: function() {
      this.$store.commit("setToolDisplay", false);
    },
    toolsMouseover: function(i) {
      //this.toolsList[i].name = '▶' + this.skillsList[i].name
      this.toolsChoice = i;
    },
    toolsMouseleave: function(i) {
      //this.toolsList[i].name = this.skillsList[i].name.slice(1)
    }
  }
};
</script>

<style>
a:link {
  text-decoration: none;
  color: white;
}

a:visited {
  text-decoration: none;
  color: white;
}

.tool-cursor {
  text-align: left;
  font-family: "メイリオ", Meiryo, "ヒラギノ角ゴ Pro W3",
    "HIragino Kaku Gothic Pro W3", "HIragino Kaku Gothic Pro", Osaka,
    "ＭＳ Ｐゴシック", "MS P Gothic", sans-serif;
}

.tools-menu {
  position: absolute;
  top: 0px;
  left: 0px;
  width: 130px;
  height: 115px;
  padding: 10px;
  margin-bottom: 10px;
  border: 2px solid #fff;
  border-radius: 10px;
  background-color: #000;
}

.tools-menu::before {
  background-color: #000;
  color: #fff;
  content: "ぷろふぃーる";
  position: relative;
  left: 23px;
  top: -23px;
}

.tools-menu-list {
  position: relative;
  top: -23px;
  text-align: center;
  background-color: #000;
}

.tools-details {
  position: absolute;
  top: 0px;
  left: 170px;
  width: 190px;
  height: 350px;
  padding: 10px;
  margin-bottom: 10px;
  border: 2px solid #fff;
  border-radius: 10px;
  background-color: #000;
}

.tools-details-list {
  text-align: right;
}
</style>
