## 学校查询
```
<html>
    <head>
        <title>ajax</title>
        <meta charset="utf-8">
    </head>
    <body>
        <form id="form">
        请输入要查询的手机号码
        <input type="text" name="phone">
        </form>
        <a href="javascript:void(0)" id="btn">查询</a>
        <p>手机号码:<span id="phone"></span></p>
        <p>信号类型:<span id="supplier"></span></p>
        <p>归属地:<span id="province"></span></p>
        <p>城市:<span id="city"></span></p>
        <p>卡类型:<span id="suit"></span></p>
        <script src="jquery.min.js"></script>
        <script>
            $("#btn").click(function(){
                $.ajax({
                    url:'http://apis.baidu.com/apistore/mobilenumber/mobilenumber',
                    headers:{
                        apikey:"59de88dbdeaa8a97f149dfcbd475a591"
                    },
                    type:'get',
                    // async:true,//异步
                    data:$('#form').serialize(),
                    dataType:'json',
                    success:function(res){
                        console.log(res);
                        for(var key in res.retData){
                            $('#'+key).text(res.retData[key]);
                        }
                    },
                    error:function(err){
                        console.log(err);
                    }
                })
            })
        </script>
    </body>
</html>
