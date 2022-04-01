```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        function processData(data){
            let arr = [];
            for(let k in data){
                let str = k + "=" + data[k];
                arr.push(str);
            }
            return arr.join("&");
            
        }

        function transmit(options){
            let xhr = new XMLHttpRequest();

            let qs = processData(options.data);

            if(options.method.toUpperCase() === "GET"){
                xhr.open(options.method,options.url+"?"+qs);
                xhr.send();

            }else if(options.method.toUpperCase() === "Post"){
                xhr.open(options.method,options.url+"?"+qs);
                xhr.setRequestHeader('Content-Type','application/x-www-form-urlencoded');
                xhr.send(qs);

            }


            xhr.onreadystatechange = function(){
                if(xhr.readyState ===4 && xhr.status ===200){
                    
                    let result = JSON.parse(xhr.responseText);
                    options.success(result);
                }
            }

        }

        let test = {
            method:"GET",
            url:"http://www.liulongbin.top:3006/api/getbooks",
            data:{
                id:1
            },
            success:function(res){
                console.log(res);
            }

        }

        transmit(test);
    </script>
</body>
</html>
```