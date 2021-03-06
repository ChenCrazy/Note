## Javabean 
Javabean是一种符合了某种特定的规范的类，使得其代码区分明确提高了可维护性

### 三个常用标签
<jsp:useBeans> <jsp:getProperty> <jsp:setProperty>

### 四个作用域范围

* 说明：使用<jsp:userBean>的scope属性可以用来指定javabean的作用范围
  * page: 仅在当前页面有效
  * request：可以通过HttpRequest.getAttribute()方法取得JavaBean对象
  * session: 可以通过HttpSession.getAttribute()方法取得JavaBean对象
  * application：可以通过application.getAttribute()方法取得JavaBean对象

## JSP的动作元素(action elements)
动作元素请求处理阶段提供信息。动作元素遵循XML元素的语法，有一个包含元素名的开始标签，可以有属性、可选的内容、与开始标签匹配的结束标签

* 第一类： 与存取JavaBean有关的
	* `<jsp:useBean>` `<jsp:setProperty>` `<jsp:getProperty>`
* 第二类： 在JSP1.2开始有的基本元素，包括6个动作元素
	* `<jsp:include>` `<jsp:forward>` `<jsp:param>` `<jsp:plugin>` `<jsp:params>`  `<jsp:fallback>`
* 第三类： JSP2.0新增的动作元素，主要与JSP Document 有关，包括六个元素
	* `<jsp:root>` `<jsp:declaration>` `<jsp:scriptlet>` `<jsp:expression>` `<jsp:text>` `<jsp:output>`
* 第四类： JSP新增的动作元素，主要用来动态生成XML元素标签的值，包括三个动作
	* `<jsp:attribute>` `<jsp:body>` `<jsp:element>` 
* 第五类： JSP2.0新增的动作元素，主要用在Tag File中，有两个元素
	* `<jsp:invoke>` `<jsp:dobody>` 



## Javabean的设计原则  
必须是一个公有类  必须包含一个无参的公有的构造方法 在其中的所有属性都是私有，并且使用getter和setter方法防问器对这些私有属性进行封装

## 在JSP页面中使用Javabeans
1. 像使用普通java类一样，使用new 这个类的构造方法来创建javabean的实例
2. 在Jsp页面中通常使用Jsp的动作标签来使用javabean
* `<jsp:userBean>`
	* 作用：在jsp页面中实例化或者在指定范围内使用javabean
* `<jsp:userBean id="标识符" class="javabean使用的java类全名" scope="作用范围"/>`

* `<jsp:setProperty>`
	* 作用:给已经实例化的Javabean对象的属性赋值，一共四种形式
	* `<jsp:setProperty name="JavaBean实例名" property="*" />`
		* (跟表单关联，根据表单提交过来的参数名字和JavaBean中的属性名字一一匹配，若匹配上则自动赋值，*表示匹配所有属性)
	* `<jsp:setProperty name="JavaBean实例名" property="JavaBean属性名" />`
		* (跟表单关联，对部分指定的属性进行匹配)
	* `<jsp:setProperty name="JavaBean实例名" property="JavaBean属性名" valu="BeanValue" />`
		* (手工设置，使用value值进行匹配)
	* `<jsp:setProperty name="JavaBean实例名" property="propertyName" param="request对象中的参数名" />`
		* (跟request参数关联，通过URL地址传参的方式来传递,匹配传进的值将是表单提交的action的值)

* `<jsp:getProperty>`
	* 作用:获取指定Javabean对象的属性值
	* `<jsp:getProperty name="JavaBean实例名" property="属性名" />`

### Model1简介  
Model1出现前，整个Web应用的情况几乎全部由JSP页面组成，JSP页面接收处理客户端请求，对请求处理后直接做出响应  
在界面层会充斥着大量的业务逻辑的代码和数据访问层的代码，Web程序的可扩展性和可维护性极差。  
JavaBean的出现可以使JSP页面中使用JavaBean封装的数据或者调用JavaBean的业务逻辑代码，提升了程序的可维护性  
即将业务逻辑代码放到另一个类中封装起来，让他与数据库交互，叫它JavaBean，然后在jsp页面中调用JavaBean的代码，这样产生分离的错觉  
    
