# insertBefore--insertAfter
自己封装insertBefore相反的功能   (insertBefore:在已有的子节点之前插入一个新的子节点)




1): insertBefore() 方法在已有的子节点之前插入一个新的子节点。

      语法：
      elementNode.insertBefore(new_node,existing_node)
      
      参数	描述
      new_node	必需。要插入的节点(新创建的元素节点)。
      existing_node	必需。已有节点。在此节点之前插入新节点。

      注意： insertBefore 是把新插入的节点放到被插入节点的前面
      
            <div>
		 <span></span>
		 <p></p>
		 <a></a>
		 <h1></h1>
             </div>
        
        var div=document.getElementsByTagName("div")[0];
        var span=document.getElementsByTagName("span")[0];
        var creates=document.createElement("i");

        div.insertBefore(creates,span)   // 这样就把 i元素节点插入到span元素节点的前面
     
     
  * 这样我觉得 既然可以插入到前面 就可以插入到后面？ 遗憾的是js内置方法没有实现这个功能，那咋们就自己实现它
 

	     Element.prototype.insertAfter=function(targetNode,afterNode){ 
	      //解释：那下面span来说，span的下一个兄弟节点是p,
		var beforeNode=afterNode.nextElementSibling;
		  if(beforeNode==null){
			this.appendChild(targetNode);
		  }else{
		    //就在p前面插入新节点，(这样以来不是在span后面插入新节点吗？,因为p前面节点就是span)
			this.insertBefore(targetNode,beforeNode);
		  }
	     }

	     var div=document.getElementsByTagName("div")[0];
	     var span=document.getElementsByTagName("span")[0];
	     var creates=document.createElement("i");

	    div.insertAfter(creates,span)   // 把新创建的i元素，插入到span元素后面

     
     
     
     
     
     
     
     
     
     





