objectToQuery
=============

将JS对象 转化为查询字符串，方便构造Url 以免自己手动拼接出错

    function objectToQuery(/*Object*/ obj){
    		// summary:
            //		
            //	将Javascript对象转为查询字符串
            var enc = encodeURIComponent, resultArray = [];
            for(var name in obj){
                  var value = obj[name];           
                    var assign = enc(name) + "=";
                    if(Object.prototype.toString.call(value).slice(8,-1)==="Array"){
                        for(var i = 0, l = value.length; i < l; ++i){
                            resultArray.push(assign + enc(value[i]));
                        }
                    }else{
                        resultArray.push(assign + enc(value));
                    }
                
            }
            return resultArray.join("&"); // String
        }
        
Test

    var obj={
        name:"kunkun",
        chinese:"坤坤",
        book:["math","Physics"]
    }
    console.log(objectToQuery(obj))

输出结果：

name=kunkun&chinese=%E5%9D%A4%E5%9D%A4&book=math&book=Physics 


