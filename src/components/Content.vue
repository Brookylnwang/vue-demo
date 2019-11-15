//src/components/Content.vue
<template>
  <b-container>
    <button>sdsdsd</button>
    <!--v-life是导入的子组件Life-->
    <v-life :title="title" :homemsg='msg' :run='run' ref='life_child' />
    <button @click="flag=!flag">点击挂载及卸载组件</button>
    <button @click="getData()">请求数据</button>
    <button @click="getChildData()">主动获取子组件</button>
    <ul>
      <li v-for="items in list">
        {{ items.title }}
      </li>
    </ul>
    <b-card
      overlay
      img-src="https://picsum.photos/900/250/?image=3"
      img-alt="Card Image"
      text-variant="white"
      title="Image Overlay"
      sub-title="Subtitle"
      v-if="flag"
    >
      <b-card-text>
        Some quick example text to build on the card and make up the bulk of the card's content.
      </b-card-text>
    </b-card>
  </b-container>
</template>
<script>
  //导入Life组件
  import Life from './Life.vue';
  import VueEvent from '../model/VueEvent.js';
  import axios from "axios";
  export default {
    data() {
      return {
        msg: '我是一个组件',
        list: [],
        title: '这是父组件title',
        flag: true
      };
    },
    methods: {
      run() {
        alert("这是Content组件的方法")
      },
      getChildData() {
        alert(this.$refs.life_child.msg)
      },
      getData() {
        /*var api = 'http://www.phonegap100.com/appapi.php?a=getPortalList&catid=20&page=1';
        this.$http.get(api).then((response)=>{
          console.log(response)
          this.list = response.body.result;
        },function(err){
          console.log(err)
        })*/
        /*axios传值*/
        axios
          .get("http://www.phonegap100.com/appapi.php?a=getPortalList&catid=20&page=1")
          .then(response => {
          //this.meals = response.data.categories;
          console.log(response)
          this.list = response.data.result;
        })
          .catch(err => {
          console.log(err);
        })
      }
    },
    components: {
      'v-life': Life
    },
    mounted() {
      VueEvent.$on('to-content', function(data){
        console.log(data);
        //this.flag = data;
      })
    }
  };
</script>