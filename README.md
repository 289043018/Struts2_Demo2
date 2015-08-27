# Struts2_Demo2
这是一个完整的struts2示例

代码包含了web.xml配置文件，pom依赖文件以及struts的配置文件。
web.xml:

<display-name>Archetype Created Web Application</display-name>
  
	  <filter>
	  	<filter-name>Struts2Filter</filter-name>
	  	<filter-class>org.apache.struts2.dispatcher.ng.filter.StrutsPrepareAndExecuteFilter</filter-class>
	  </filter>
	  <filter-mapping>
	  	<filter-name>Struts2Filter</filter-name>
	  	<url-pattern>/*</url-pattern>
	  </filter-mapping>
	  
pom听说只要依赖core就可以自动下载struts的所有依赖，但是没测试过。

index.jsp的：
<%@ page language="java" import="java.util.*" pageEncoding="utf-8"%>
<%
String path = request.getContextPath();
String basePath = request.getScheme()+"://"+request.getServerName()+":"+request.getServerPort()+path+"/";
%>
是文件编码格式和文件路径的获取。
struts.xml文件放置在SRC/MAIN/RESOURCE中，配置如下：
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE struts PUBLIC
	"-//Apache Software Foundation//DTD Struts Configuration 2.3//EN"
	"http://struts.apache.org/dtds/struts-2.3.dtd">
<!-- 配置根元素 -->
<struts>
	<!-- bean标签用于一个JavaBean实例 -->

   <!--  constant标签用于Struts2默认行为标签 -->
<!--    配置web默认编码集，相当于HttpServletRequest.setChartacterIncoding用法 -->
  <constant name="struts.i18n.encoding" value="UTF-8"></constant>
<!--   默认的Struts2的请求后缀是.action，也就是说我们不配置该元素，也就是说我们这里设置了action/do都会被拦截 -->
  <constant name="struts.action.extension" value="action,do"></constant>
  	<!-- 设置浏览器是否缓存静态内容，默认值为true。在我们开发阶段，建议修改为false，放置修改后测试不到 -->
  	<constant name="struts.serve.static.browserCache" value="false"></constant>
  	<!-- 当struts配置文件修改之后，系统是否自动重新加载该文件，默认为false，部署到服务器之后就可以改为false -->
  	<constant name="struts.configuration.xml.reload" value="true"></constant>
  	<!-- 开发模式下使用，这样可以打印出更加详细的错误信息，便于调试 -->
  	<constant name="struts.devMode" value="true"></constant>
  	<!-- 默认视图主题 -->
  	<constant name="struts.ui.theme" value="simple"></constant>
	<!--   package标签包标签，用于区分不同的请求文件的标签，比方说
  	网站前台请求和网站后台请求 -->
  	<!-- name属性：包名，用于被别的包调用或者继承 -->
  	<package name="test" namespace="/new" extends="struts-default">
  	<!-- action相当于以前的servlet的概念，对应一个请求name为请求的url地址 
  		localhost：8080/项目名/new/login.do
  	-->
  		<action name="login" class="com.hand.action.LoginAction">
  			<result name="success">/success.jsp</result>
  			<result name="fail">/fail.jsp</result>
  		</action>
  	</package>
  		
	<!--   	include标签用于引入其他的xml配置文件 -->

</struts>

public class LoginAction {
	private String username;
	private String password;
	
	public String execute(){
		if(username.equals("admin")){
			return "success";
		}else{
			return "fail";
		}
	}
	这里使用右键加载getting和setting方法
}




