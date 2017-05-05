<template>
<div class="two">
	<div class="ui top attached tabular menu">
          <a class="item" data-tab="second/a" ><font><font><!-- 2a -->{{classs[0].name}}</font></font></a>
          <a class="item" data-tab="second/b"><font><font><!-- 2b -->{{classs[4].name}}</font></font></a>
          <a class="item" data-tab="second/c"><font><font><!-- 2c -->{{classs[5].name}}</font></font></a>
          <a class="item" data-tab="second/d"><font><font><!-- 2d -->{{classs[7].name}}</font></font></a>
        </div>
        <div class="ui bottom attached tab segment" data-tab="second/a">
          <!-- 2A -->
          <div>
          <p style="font-size:3vw;color:green;">记下菜品ID，可到分类搜索查找具体菜谱</p>
            <ul>
              <li v-for="clas in classs[0].list"><b style="font-size:3vw;">菜品编号:{{clas.classid}};功效：{{clas.name}}</b></li>
            </ul>
          </div>
       </div>
        <div class="ui bottom attached tab segment" data-tab="second/b"><font><font>
        <!-- 2B -->
         <div>
         <p style="font-size:3vw;color:green;">记下菜系ID，可到分类搜索查找具体菜谱</p>
            <ul>
              <li v-for="clas in classs[4].list"><b style="font-size:3vw;">菜品编号:{{clas.classid}};菜系：{{clas.name}}</b></li>
            </ul>
          </div>
        </font></font></div>
        <div class="ui bottom attached tab segment" data-tab="second/c"><font><font>
        <!-- 2C -->
         <div>
         <p style="font-size:3vw;color:green;">记下地方ID，可到分类搜索查找具体菜谱</p>
            <ul>
              <li v-for="clas in classs[5].list"><b style="font-size:3vw;">菜品编号:{{clas.classid}};地方：{{clas.name}}</b></li>
            </ul>
          </div>
        </font></font></div>
        <div class="ui bottom attached tab segment" data-tab="second/d"><font><font>
        <!-- 2d -->
         <div>
         <p style="font-size:3vw;color:green;">记下口味ID，可到分类搜索查找具体菜谱</p>
            <ul>
              <li v-for="clas in classs[7].list"><b style="font-size:3vw;">菜品编号:{{clas.classid}};口味：{{clas.name}}</b></li>
            </ul>
          </div>
        </font></font></div>



</div>


</template>

<script>
var homeUrl = "http://api.jisuapi.com/recipe/"
var fenleiUrl = "class?appkey=468713f9d26b3e56"



export default {
name: 'two',
data(){return {
    classs:[{"name":""},{"name":""},{"name":""},{"name":""},{"name":""},{"name":""},{"name":""},{"name":""}],
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
created(){
   var _this = this;
   //      console.log(111)
        $.ajax({
          url: homeUrl + fenleiUrl ,
          type: 'GET',
          dataType: 'jsonp',
        })
        .done(function(data) {
        	console.log(data)
          data = data.result;
         // console.log(data);
          _this.classs = data;
        })
},
}


</script>

<style>
	

</style>