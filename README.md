## 学校查询
```
<body>
    <div class="container">
        <form id="form">
            <h1>请输入学校名字</h1>
            <input style="width:300px;" class="form-control" type="text" name="name">
        </form>
        <a href="javascript:void(0)" class="btn btn-success" id="btn">查询</a>
        <p style="margin-top:20px;">状态:<span id="msg"></span></p>
        <p>学校名字:<span id="name"></span></p>
        <p style="width:100px;max-height:100px;overflow:hidden;border:solid 1px #ccc;"><img id="pic" style="width:100%" src="" alt="暂无"></p>
        <p>地址:<span id="address"></span></p>
        <p>信息:<span id="info"></span></p>
        <p>城市:<span id="city"></span></p>
        <p>类型:<span id="type"></span></p>
        <p>邮箱:<span id="email"></span></p>
        <p>网址:<span id="website"></span></p>
        <p>电话:<span id="phone"></span></p>
    </div>
    <script src="js/jquery-1.11.3.min.js"></script>
    <script src="lib/bootstrap/js/bootstrap.min.js"></script>
    <script>
        $("#btn").click(function(){
            $.ajax({
                url:'http://apis.baidu.com/jidichong/school_search/school_search',
                headers:{
                    apikey:"59de88dbdeaa8a97f149dfcbd475a591"
                },
                type:'get',
                // async:true,//异步
                data:$('#form').serialize(),
                dataType:'json',
                success:function(res){
                    console.log(res)
                    $("#msg").text(res.msg)
                    var all = res.result.data[0]
                    for(var key in all){
                        $('#'+key).text(all[key]);
                    }
                    $("#pic").attr('src',all.img)
                },
                error:function(err){
                    console.log(err);
                }
            })
        })
    </script>
</body>
