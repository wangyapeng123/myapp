<template>
  <div class="hello">
    <div id="context1">
      <div class="ui secondary menu">
        <a class="item" data-tab="first"><font><font>菜谱直搜</font></font></a>
        <a class="item" data-tab="second" ><font><font>菜谱分类</font></font></a>
        <a class="item" data-tab="third"><font><font>分类搜索</font></font></a>
      </div>
      <div class="ui tab segment" data-tab="first">
       <one></one>
        
      </div>
      <div class="ui tab segment active" data-tab="second">
      <two></two>
        
      </div>
      <div class="ui tab segment" data-tab="third">
      <three></three>
        
      </div>
    </div>
     

    
  </div>
</template>

<script>
import Vue from 'vue'
import jQuery from "../assets/Semantic/jquery.min"
import semantic from "../assets/Semantic/semantic.min"

import one from "./one"
import two from "./two"
import three from "./three"

//import iview_js from "//unpkg.com/iview/dist/iview.min.js"

  // var homeUrl = "http://api.jisuapi.com/recipe/"
  // var searchUrl = "search?keyword="
  // var souUrl = ""
  // var fenleiUrl = "class?appkey=468713f9d26b3e56"
  // var keyUrl = "&num=10&appkey=468713f9d26b3e56"
  
  // var id1Url = "byclass?classid="
  // var id = ""
  // var id2Url = "&start=0&num=10&appkey=468713f9d26b3e56"
export default {

  name: 'hello',
  components:{
    one,
    two,
    three,
  },
  data(){return {
    json:[],
    classs:[],
    flid:[],
    }
  },
  created(){
      
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
    
      // var _this = this;
      //   console.log(111)
      //   $.ajax({
      //     url: homeUrl + fenleiUrl ,
      //     type: 'GET',
      //     dataType: 'jsonp',
      //   })
      //   .done(function(data) {
      //     data = data.result;
      //    // console.log(data);
      //     _this.classs = data;
      //   })
    
    

  },
  methods:{
       // fen(){
        
        
        
       // },
       // searchid(){
       //  //alert(11)
       //  var _this = this;
       //  id = fenleiid.value
       //  $.ajax({
       //    url: homeUrl + id1Url + id + id2Url,
       //    type: 'GET',
       //    dataType: 'jsonp',
       //  })
       //  .done(function(data) {
       //    data = data.result.list;
       //    console.log(data)
       //    _this.flid = data;
       //  })
       
        
       // },
     //  search(){
     //    var _this = this;
     //  //alert(this.json)
     //  // console.log(this.json)
     //  // console.log(_this.json[0].name)
     //  souUrl = caiName.value
     //  $.ajax({
     //    url: homeUrl + searchUrl + souUrl + keyUrl,
     //    type: 'GET',
     //    dataType: 'jsonp',
     //  })
     //  .done(function(data) {
     //     data = data.result.list;
     //    _this.json = data;
        
     //  })
     //  .fail(function() {
     //    alert("信息未获取到");
     //  })
      
    
     // }
    
  },
  
}


  
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
#results{
  border:0px;padding:3px; PADDING:0px; width:100%; height:100%; LINE-HEIGHT: 20px; OVERFLOW: auto;
}
@import "../assets/Semantic/semantic.min.css"


</style>
