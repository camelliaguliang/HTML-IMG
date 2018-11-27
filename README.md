# HTML-IMG
+ 将html转换为img并保存到本地
+ 方案一：将DOM改写为canvas，然后利用canvas的toDataURL方法实现将DOM输出为包含图片展示
+ 方案二：第三方插件 dom-to-image
     + dom-to-image支持将HTML（包括table或者svg）转换为svg、png、jpeg、Blob、pixelData
     ----
          var node = document.getElementById('table');
          domtoimage.toPng(node).then(function (dataUrl) {
             //var img = new Image();
             //img.src = dataUrl;
             //document.body.appendChild(img);---向页面添加img

             var $image=$("<img style='margin:30px'>"); //可以给当前img添加id和样式
             $('#area').prepend($image); //向div的前面添加img
             $image.attr('id','XXX');
             $image.attr('src',dataUrl);
         });
     ----
 + 方案三：html2canvas    将HTML-canvas-url
    ----
         var node = document.getElementById('#print');
         html2canvas(node,{scale:1,logging:false,useCORS:true}).then(function(canvas){
           //document.body.appendChild(canvas);--将canvas添加到页面
           var dataURL = canvas.toDataURL();
           $('#down_button').attr( 'href' ,dataURL) ;  
           $('#down_button').attr( 'download' , "image/png" ) ;  
         })
    ----
  
  + ps：svg转换为canvas，可用第三方js--canvg
