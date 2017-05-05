<template>

<div class="two">

<div class="ui top attached tabular menu">
          <a class="item" data-tab="first/a"><font><font>食材搜菜</font></font></a>
          <a class="item" data-tab="first/b"><font><font>做法搜菜</font></font></a>
          <a class="item" data-tab="first/c"><font><font>功能开发中</font></font></a>
        </div>
        <div class="ui bottom attached active tab segment" data-tab="first/a"><font><font>
       
        <!-------------------------- 搜索栏 -------------------->
        
              <div class="ui search">
              <div class="ui icon input" >
                <input id="caiName" placeholder="请输入想要做的菜" type="text">
                <button class="ui inverted green button" v-on:click="search">搜索</button>
              </div>
              <div id="results" >
              
                <div v-for="todo in json" style="border:1px solid #bbb;margin:4px;">
               <!--  <p>{{todo}}</p> -->
                  <h2>菜名:{{todo.name}}</h2>
                  <h3>准备时间:{{todo.peoplenum}}</h3>
                  <h3>烹饪时间:{{todo.cookingtime}}</h3>
                  <h4>介绍:{{todo.content}}</h4>
                  <h4>标签:{{todo.tag}}</h4>
                  <span>参考图：<img :src="todo.pic" /></span>
                  <div>
                  <p><b>材料：</b></p>
                     <ul>
                       <li v-for="cailiao in todo.material">{{cailiao.mname}},{{cailiao.amount}}</li>
                     </ul>
                  </div>
                  <div>
                    步骤:
                    <ul>
                      <li v-for="buzou in todo.process" style="border:1px solid #bbb;margin:2px;">
                        <span>{{buzou.pcontent}}</span>
                        <img :src="buzou.pic" alt="">
                      </li>
                    </ul>
                  </div>
                </div>
              </div>
            </div> 
        </font></font></div>
        <div class="ui bottom attached tab segment" data-tab="first/b"><font><font>
        	<div class="ui icon input">

                <input id="caiZF" placeholder="请输入做法(炖煮蒸炒炸)" type="text">
                <button class="ui inverted green button" v-on:click="searchzf">搜索</button>
              </div>
              <div id="results">
              
                <div v-for="todo in zfs" style="border:1px solid #ccc;margin:4px;">
               <!--  <p>{{todo}}</p> -->
                  <h2>菜名:{{todo.name}}</h2>
                  <p>准备时间:{{todo.peoplenum}}</p>
                  <p>烹饪时间:{{todo.cookingtime}}</p>
                  <p>介绍:{{todo.content}}</p>
                  <p>标签:{{todo.tag}}</p>
                  <span>图片：<img :src="todo.pic" /></span>
                  <div>材料：
                     <ul>
                       <li v-for="cailiao in todo.material">{{cailiao.mname}},{{cailiao.amount}}</li>
                     </ul>
                  </div>
                  <div>
                    步骤:
                    <ul>
                      <li v-for="buzou in todo.process">
                        <span>{{buzou.pcontent}}</span>
                        <img :src="buzou.pic" alt="">
                      </li>
                    </ul>
                  </div>
                </div>
              </div>
        </font></font></div>
        <div class="ui bottom attached tab segment" data-tab="first/c"><font><font>功能暂未开放，敬请期待！</font></font></div>

</div>

</template>




<script>
var homeUrl = "http://api.jisuapi.com/recipe/"
var searchUrl = "search?keyword="
var souUrl = ""
var keyUrl = "&num=10&appkey=468713f9d26b3e56"


export default {
name: 'two',
data(){return {
    json:[],
    zfs:[],
    }
  },
  mounted(){
   
  $('#context1 .menu .item')
    .tab({
      context: $('#context1')
    })
  $('#context2 .menu .item')
    .tab({
      // special keyword works same as above
      context: 'parent'
    })
  },
  methods:{
  	search(){
        var _this = this;
      //alert(this.json)
      // console.log(this.json)
      // console.log(_this.json[0].name)
      souUrl = caiName.value
      $.ajax({
        url: homeUrl + searchUrl + souUrl + keyUrl,
        type: 'GET',
        dataType: 'jsonp',
      })
      .done(function(data) {
         data = data.result.list;
        _this.json = data;
        
      })
      .fail(function() {
        alert("信息未获取到");
      })
      
    
     },
     searchzf(){
        var _this = this;
      //alert(this.json)
      // console.log(this.json)
      // console.log(_this.json[0].name)
      souUrl = caiZF.value
      $.ajax({
        url: homeUrl + searchUrl + souUrl + keyUrl,
        type: 'GET',
        dataType: 'jsonp',
      })
      .done(function(data) {
         data = data.result.list;
        _this.zfs = data;
        
      })
      .fail(function() {
        alert("信息未获取到");
      })
      
    
     }
  },

}


</script>









<style>
	div{
		border-radius: 3px;
	}
</style>














