<template>
  <div>
    <!--<img src="./assets/logo.png">
    <h2>{{msg}}</h2>
    <br>
    这是一个根组件
    <p>{{obj.name}}</p>
    <ul v-bind:class="{'red':flag,'blue':!flag}">
      <li v-for='item in list1'>
        {{item.title}}
      </li>
    </ul>
    <br>
    <ul>
      <li v-for='items in list2'>
        {{items.name}}
        <ol>
          <li v-for='(news,index) in items.list':class="{'red':index==0,'blue':index==2}">
              index:{{index}}---{{news.title}}
          </li>
        </ol>
      </li>
    </ul>
    <br>
    <p>{{msgs}}</p>
    <div v-bind:title="titles">鼠标放上面</div>
    <img v-bind:src="url">
    <div>
      <h2>{{input_val}}</h2>
      <input type="text" v-model='input_val' />
      <button v-on:click="getMsg()">获取表单数据</button>
      <button v-on:click="setMsg()">设置表单数据</button>
      <br>
      <br>
      <input type="text" ref="userinfo" />
      <button v-on:click="getInputValue()">获取第二表单里的数据</button>
    </div>
    <div class="boxbox" ref='box'>{{boxbox}}</div>
    <div class="box1" v-bind:style="{width:boxwidth}"></div>
    <div>
      <button @click="run1_getMsg()">请求数据</button>
      <button @click="run2_setMsg()">执行第二种方法</button>
      <li v-for="item in origin_list">
        {{item}}
      </li>
      <button data-aid='123' @click="eventClick($event)">获取事件对象</button>
    </div>-->
  </div>
</template>

<script>
export default {
    name: 'dmeo',
    data () {
      return {
        msg: '你好',
        obj: {
          name: '张三'
        },
        list: ['123', '345', '567'],
        list1: [
          {'title': '123'},
          {'title': '123'},
          {'title': '123'},
          {'title': '123'}
        ],
        list2: [
          {
            'name': '国际新闻',
            'list': [
              {'title': '第一个国际新闻'},
              {'title': '第二个国际新闻'},
              {'title': '第三个国际新闻'}
            ]
          },
          {
            'name': '国外新闻',
            'list': [
              {'title': '第一个国外新闻'},
              {'title': '第二个国外新闻'},
              {'title': '第三个国外新闻'}
            ]
          }
        ],
        msgs: '你好，vue,我又来了',
        titles: '被你发现了',
        url: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1569686605242&di=3e247590ace023089ec78d29901f5ed3&imgtype=0&src=http%3A%2F%2Fphotocdn.sohu.com%2F20150924%2Fmp33243850_1443100816109_2.gif',
        h: '<h2>我是h2</h2>',
        flag: true,
        boxwidth: '300px',
        input_val: 'demo',
        afer_chang: '这是改变后的数据',
        boxbox: '这是一个box',
        origin_list: []
      }
    },
    methods: {
      getMsg() {
        alert("上图的url是：" + this.url)
      },
      setMsg() {
        this.input_val = this.afer_chang;
        alert(this.afer_chang)
      },
      getInputValue() {
        console.log(this.$refs.userinfo);
        this.$refs.box.style.background='orange';
        this.input_val = this.$refs.userinfo.value;
        this.boxbox = this.$refs.userinfo.value
      },
      run1_getMsg() {
        for(var i=0;i<10;i++){
          this.origin_list.push('我是第'+ i +'条数据')
        }
      },
      run2_setMsg() {
        alert('这是另一种方法');
      },
      eventClick(e) {
        console.log(e.srcElement.dataset.aid); /*获取自定义属性的值*/
        e.srcElement.style.background='red';
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
