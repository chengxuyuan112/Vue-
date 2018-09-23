#### Vue操作元素属性:

####          v-bind :绑定属性

####    Vue的stache与v-once使用

​     v-once :只绑定数据一次，再次更新数据，dom不会更新

```html
 <h2 v-once>{{hd1}}</h2>
```

​     v-model:数据绑定

#### v-text v-html使用

​     v-text:显示原始的数据，HTML元素也不会解析

```html
<h1 v-text="hd"></h1>
```

   v-html:显示数据，会将HTML元素解析成正确的元素

```html
   <h1 v-html="hd"></h1>
```

#### vascriptpt表达式的方法

```html
<div id="app5">
    <h1 v-once=""></h1>
    <h1 v-bind:class="'hd'+n">{{n}}，后盾网，</h1>
    <input type="text" v-model="n">
    <input type="radio" value="1" v-model="n">红色
    <input type="radio" value="2" v-model="n">绿色
</div>
 var app5=new Vue({
          el:'#app5',
          data:{
              n:1
          }
      })
```

####  Vuecomputed实例（购物车总价动态计算值）

```html
  var app6=new Vue({
          el:'#app6',
          data:{
              n1:0,
              n2:0,
          },
          computed:{
               sum:function () {
                  return this.n1*1+this.n2*1;
              }
          }
      })
      <div id="app6">
    <input type="text" v-model="n1">+
    <input type="text" v-model="n2">=
    <input type="text" v-model="sum">
</div>
```

#### vue 实现类似百度搜索功能（watch对变量的监听）

```html
  var app7=new Vue({
          el:'#app7',
          watch:{
              words: function (a,b) {
                  console.log(a+"====>"+b);
                  axios.get('9.php?word='+a).then(function (response) {
                       console.log(response);
                      console.log(this);
                      app7.result=response.data;
                  })
              }
          },
          data:{
              result:'',
              words:''
          }
      })
      <div id="app7">
    <input type="text" v-model="words">
    <h1>搜索的结果是:{{result}}</h1>
</div>
```

####    使用lodash实现过滤请求（类似Android中的rxjava过滤）

​      