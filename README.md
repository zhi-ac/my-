
##添加预览图片功能
~~~
//获取数据
                getList:function (state) {
                    if(state){
                        page = 1;
                        isShowPage = false;
                    }
                    var parm = {
                        page: page,
                        number: size,
                    };
                    DYB_POST_JSON("/xnAdmin/xnFeedback/showList", "post", parm,function(res){
                        var records = res.data.records;
                        vueApp.object = records;
                        //分页
                        showPage(res.data.current, res.data.total)
                        setTimeout(function(){
                            layer.photos({
                                photos: '#layer-photos-demo'
                                ,anim: 5 //0-6的选择，指定弹出图片动画类型，默认随机（请注意，3.0之前的版本用shift参数）
                            });
                        },1000);

                    });
                },
~~~
并在最外层标签上加id = layer-photos-demo
~~~
<tbody id="layer-photos-demo">
~~~
