# chart.js 使用笔记

+ chartjs官网

http://www.bootcss.com/p/chart.js/docs/

+ 绘制

```
var ctx = document.getElementById("myChart").getContext("2d");
pricedata= JSON.parse(data);
window.myLine = new Chart(ctx, dataStruct(pricedata,pricedata.code));
```

+ 生成表格

```
//表格所需要的数据结构
    function dataStruct(parameter,code){
        var text=""+code;
        var config = {
            type: 'line',
            data: {
                labels: [],
                datasets: [{
                    label: "form one",
                    data: [],
                    fill: false,
                    borderDash: [5, 5],
                }, {
                    hidden: true,
                    label: 'form two',
                    data: [],
                }]
            },
            options:{
                responsive: true,
                title:{
                    display:true,
                    text:"房价曲线图"
                },
                tooltips: {
                    mode: 'label',
                    callbacks: {
                        beforeTitle: function() {
                            return '...beforeTitle';
                        },
                        afterTitle: function() {
                            return '...afterTitle';
                        },
                        beforeBody: function() {
                            return '...beforeBody';
                        },
                        afterBody: function() {
                            return '...afterBody';
                        },
                        beforeFooter: function() {
                            return '...beforeFooter';
                        },
                        footer: function() {
                            return 'Footer';
                        },
                        afterFooter: function() {
                            return '...afterFooter';
                        },
                    }
                },
                hover: {
                    mode: 'dataset'
                },
                scales: {
                    xAxes: [{
                        display: true,
                        scaleLabel: {
                            show: true,
                            labelString: 'Month'
                        }
                    }],
                    yAxes: [{
                        display: true,
                        scaleLabel: {
                            show: true,
                            labelString: 'Value'
                        },
                        ticks: {
                            suggestedMin: 0,
                            suggestedMax: 15,
                        }
                    }]
                }
            }
        };
        for(var i=0;i<parameter.data.length;i++){
            config.data.labels.push(parameter.data[i].date);
        }
        for(var i=0;i<parameter.data.length;i++){
            config.data.datasets[0].data.push(parameter.data[i].average_price);
        }
        for(var i=0;i<parameter.data.length;i++){
            config.data.datasets[1].data.push(parameter.data[i].average_price);
        }
        //说明曲线对应的具体网格值
       config.data.datasets[0].label=""+code;
        //给曲线随机赋颜色值
        for(var i=0;i<config.data.datasets.length;i++){
            config.data.datasets[i].borderColor = randomColor(0.4);
            config.data.datasets[i].backgroundColor = randomColor(0.5);
            config.data.datasets[i].pointBorderColor = randomColor(0.7);
            config.data.datasets[i].pointBackgroundColor = randomColor(0.5);
            config.data.datasets[i].pointBorderWidth = 1;

        }

        return config;
    }
```