<template>

<div class="three">
        <div class="ui top attached tabular menu">
          <a class="item" data-tab="third/a"><font><font>ID搜索 </font></font></a>
          <a class="item" data-tab="third/b"><font><font>口味搜索 </font></font></a>
          <a class="item" data-tab="third/c"><font><font>菜系搜索</font></font></a>
        </div>
        <div class="ui bottom attached tab segment" data-tab="third/a"><font><font>

       <p>请输入菜谱分类ID</p>
              <div class="ui icon input">
                <input id="fenleiid" placeholder="请输入分类ID" type="text">
                <button class="ui inverted green button" v-on:click="searchid">搜索</button>
              </div>
              <div v-for="fenl in flid" style="border:1px solid #ccc;margin:4px;">
                <h2>名称:{{fenl.name}}</h2>
                <h3>介绍:{{fenl.content}}</h3>
                <h4>分类:{{fenl.tag}}</h4>
                <span>图片:<img v-bind:src="fenl.pic" alt=""></span>
                <ul>
                  <li v-for="bz in fenl.process">
                    <span>{{bz.pcontent}}</span>
                    <img :src="bz.pic" alt="">
                  </li>
                </ul>
              </div> 
        </font></font></div>
        <div class="ui bottom attached tab segment" data-tab="third/b"><font><font>
        <p>可搜索菜的口味：酸，甜，辣，酸辣，香辣等。</p>
              <div class="ui icon input">
                <input id="caiKW" placeholder="请输入期待口味" type="text">
                <button class="ui inverted green button" v-on:click="searchkw">搜索</button>
              </div>
              <div id="results">
              
                <div v-for="todo in kws" style="border:1px solid #ccc;margin:4px;">
               <!--  <p>{{todo}}</p> -->
                  <h2>菜名:{{todo.name}}</h2>
                  <p>准备时间:{{todo.peoplenum}}</p>
                  <p>烹饪时间:{{todo.cookingtime}}</p>
                  <p>介绍:{{todo.content}}</p>
                  <p>标签:{{todo.tag}}</p>
                  <span>图片：<img :src="todo.pic" /></span>
                  <div>材料：
                     <ul>
                       <li v-for="cailiao in todo.material" >{{cailiao.mname}},{{cailiao.amount}}</li>
                     </ul>
                  </div>
                  <div>
                    步骤:
                    <ul>
                      <li v-for="buzou in todo.process" style="border:1px solid #ccc;margin:2px;">
                        <span>{{buzou.pcontent}}</span>
                        <img :src="buzou.pic" alt="">
                      </li>
                    </ul>
                  </div>
                </div>
              </div>
        </font></font></div>
        <div class="ui bottom attached tab segment" data-tab="third/c"><font><font>
        <p>可按菜系查找：东北菜等。可直接搜索地名。</p>
             <div class="ui icon input">
                <input id="caiDF" placeholder="请输入地名" type="text">
                <button class="ui inverted green button" v-on:click="searchdf">搜索</button>
              </div>
              <div id="results">
              
                <div v-for="todo in dfs" style="border:1px solid #ccc;margin:4px;">
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

</div>

</template>




<script>
var homeUrl = "http://api.jisuapi.com/recipe/"
var searchUrl = "search?keyword="
var souUrl = ""
var keyUrl = "&num=10&appkey=468713f9d26b3e56"

 
var id1Url = "byclass?classid="
  var id = ""
  var id2Url = "&start=0&num=10&appkey=468713f9d26b3e56"


export default {
  name: 'three',
  data(){return {
    flid:[],
    kws:[],
    dfs:[]
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
  	searchid(){
        //alert(11)
        var _this = this;
        id = fenleiid.value
        $.ajax({
          url: homeUrl + id1Url + id + id2Url,
          type: 'GET',
          dataType: 'jsonp',
        })
        .done(function(data) {
          data = data.result.list;
          console.log(data)
          _this.flid = data;
        })
       
        
       },
       searchkw(){
        var _this = this;
      //alert(this.json)
      // console.log(this.json)
      // console.log(_this.json[0].name)
      souUrl = caiKW.value
      $.ajax({
        url: homeUrl + searchUrl + souUrl + keyUrl,
        type: 'GET',
        dataType: 'jsonp',
      })
      .done(function(data) {
         data = data.result.list;
        _this.kws = data;
        
      })
      .fail(function() {
        alert("信息未获取到");
      })
      
    
     },
     searchdf(){
        var _this = this;
      //alert(this.json)
      // console.log(this.json)
      // console.log(_this.json[0].name)
      souUrl = caiDF.value
      $.ajax({
        url: homeUrl + searchUrl + souUrl + keyUrl,
        type: 'GET',
        dataType: 'jsonp',
      })
      .done(function(data) {
         data = data.result.list;
        _this.dfs = data;
        
      })
      .fail(function() {
        alert("信息未获取到");
      })
      
    
     }
  }
}

</script>


<style>
	

</style>