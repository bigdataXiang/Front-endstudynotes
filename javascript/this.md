# this

>在 JavaScript 中,上下文对象就是 this 指针,即被调用函数所处的环境。上下文对象 的作用是在一个函数内部引用调用它的对象本身。
在 JavaScript 中,本质上,函数类型的变量是指向这个函数实体的一个引用,在引用之 间赋值不会对对象产生复制行为。我们可以通过函数的任何一个引用调用这个函数,不同之 处仅仅在于上下文。

``` javascript
rect= L.rectangle(bounds, {color:mycolor(200),opacity:0.9,fillColor:gridvalue.color,weight:1,fillOpacity:0.6,className:code});
rect.index=gridcode;
rect.data=price.data[rect.index];
rect.on('click', function(code){
    //console.log(rect.code);
    var json={
        "collname":"resold_code_3000",
        "type":"woaiwojia",
        "code":this.data.code
    };
    $.post("/price", JSON.stringify(json),
            function(data,status){
                var ctx = document.getElementById("myChart").getContext("2d");
                pricedata= JSON.parse(data);
                window.myLine = new Chart(ctx, dataStruct(pricedata,pricedata.code));
                $('#charttitle').text('code:'+pricedata.code);
                $('#myModal').modal();
            }
    )
});
rect.addTo(map);
```