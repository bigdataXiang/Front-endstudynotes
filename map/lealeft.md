# lealeft


http://leafletjs.com/reference.html

## Rectangle绘制
```
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
rects.push(rect);
```