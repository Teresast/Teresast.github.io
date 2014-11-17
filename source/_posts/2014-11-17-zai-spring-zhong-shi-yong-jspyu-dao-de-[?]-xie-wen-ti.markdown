---
layout: post
title: ""在spring 中使用jsp遇到的一些问题""
date: 2014-11-17 16:30:42 +0800
comments: true
categories: issues
---
###<span style="color:orange;">当你的jsp中有如下标签引用时报错</span>

	<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
	<c:set var="pageTitle" scope="request" value="myTestPage”/> 
	
可能是因为需要加jar包，jstl.jar，standard.jar

standard.jar是JSP 标准标签库，在1.0、1.1的版本中，和jstl.jar 一起使用，但在jstl-1.2.jar 就不再需要了


###<span style="color:orange;">jsp 页面的 EL 表达式不被解析时在 <%@ page %>头上加上 isELIgnored=“false" ，否则EL会不被执行。</span>
#####方法：1.JSP页面中<%@ page isELIgnored="false" %>，
每个页面都如此，就会很麻烦。 

#####2.将web.xml中的声明改为2.4版本，如下：

<web-app xmlns="http://java.sun.com/xml/ns/javaee" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" version="2.4" xsi:schemaLocation="http://java.sun.com/xml/ns/javaee   http://java.sun.com/xml/ns/javaee/web-app_2_4.xsd”>  

————————————————————————————————————————————————————————————————————————————————————————————————
org.apache.el.parser.SKIP_IDENTIFIER_CHECK  =  true   //run-> runner : Tomcat 运行参数

===============================================================================================================