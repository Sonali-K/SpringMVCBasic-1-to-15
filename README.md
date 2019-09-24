# SpringMVCBasic-1-to-15
********************************************************************************
0.how to import maven project in eclipse
###########################################################
1.copy paste the project in that workspace 
2.in eclipse file-import-general-exiting project into workspace-next-choose path-click add project into working set. -next-finish
3.check project added into workspace or not by path -goto workspace that project rt click then properties copy path and check location
**********************************************************************************************
mysql> CREATE TABLE StudentData( id int NOT NULL AUTO_INCREMENT PRIMARY KEY , name varchar(255) NOT NULL, standard varchar(789),gender varchar(897),city varchar(898),dob date, smssubscribe boolean,sports varchar(898));jdbc:mysql://localhost/db?useUnicode=true&useJDBCCompliantTimezoneShift=true&useLegacyDatetimeCode=false&serverTimezone=UTC

*************************
1..
******************
1.Create Maven Project-file-new-Maven Project-click-create simple project(skip archtype)
give group-id=package name,artifact-id=project name,packaging-war-next-finish
2.Edit Pom -add needed dependencyin pom file.
3.add index.jsp page and WEB-INF folder in =webapp ==run on server check it is working or not.
3.add web.xml and spring-servlet.xml =add both xml files and jsp folder in =WEB-INF 
folder=run on server check it is working or not print some message.

%%%%%%%%%%%%%%%%%%%%%
web.xml
%%%%%%%%%%%%%%%%%%%%%%%%%%%



<?xml version="1.0" encoding="UTF-8"?>

<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns="http://java.sun.com/xml/ns/javaee"
    xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd"
    id="WebApp_ID" version="3.0">
    <display-name>SpringMVC</display-name>
    <servlet>
        <servlet-name>spring</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <load-on-startup>1</load-on-startup>
    </servlet>
    <servlet-mapping>
        <servlet-name>spring</servlet-name>
        <url-pattern>/</url-pattern>
    </servlet-mapping>
</web-app> 


%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
 spring-servlet.xml 
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:context="http://www.springframework.org/schema/context"
    xmlns:mvc="http://www.springframework.org/schema/mvc"
    xsi:schemaLocation="  
            http://www.springframework.org/schema/beans  
            http://www.springframework.org/schema/beans/spring-beans.xsd  
            http://www.springframework.org/schema/context  
            http://www.springframework.org/schema/context/spring-context.xsd  
            http://www.springframework.org/schema/mvc  
            http://www.springframework.org/schema/mvc/spring-mvc.xsd">
    <context:component-scan base-package="com.cdac.student"></context:component-scan>
    <context:annotation-config/>
    <bean
        class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="prefix" value="/WEB-INF/jsp/"></property>
        <property name="suffix" value=".jsp"></property>
    </bean>
    </beans>

*****************************
2..
*******************************
edit pom added needed all dependency

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
pom.xml
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.student</groupId>
  <artifactId>StudentDemo</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  <packaging>war</packaging>
 
  <properties>
        <maven.compiler.target>1.8</maven.compiler.target>
        <maven.compiler.source>1.8</maven.compiler.source>
    </properties>
    <dependencies>
        <!-- https://mvnrepository.com/artifact/org.springframework/spring-webmvc -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>5.1.1.RELEASE</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.apache.tomcat/tomcat-jasper -->
        <dependency>
            <groupId>org.apache.tomcat</groupId>
            <artifactId>tomcat-jasper</artifactId>
            <version>9.0.12</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/javax.servlet/javax.servlet-api -->
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>servlet-api</artifactId>
            <version>3.0-alpha-1</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/javax.servlet/jstl -->
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>jstl</artifactId>
            <version>1.2</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/mysql/mysql-connector-java -->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>8.0.11</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/org.springframework/spring-jdbc -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-jdbc</artifactId>
            <version>5.1.1.RELEASE</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/org.hibernate.validator/hibernate-validator -->
        <dependency>
            <groupId>org.hibernate.validator</groupId>
            <artifactId>hibernate-validator</artifactId>
            <version>6.0.13.Final</version>
        </dependency>
    </dependencies>
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-war-plugin</artifactId>
                <version>2.6</version>
                <configuration>
                    <failOnMissingWebXml>false</failOnMissingWebXml>
                </configuration>
            </plugin>
        </plugins>
    </build>
 
</project>

1.create one page in jsp folder which redirected by index.jsp page 
2.create form like structure in that page=input,button
3.create package in src/main/java and pojo class==ie.employee.java
4.in pojo class mention pojo class field add getter and setter methode.
5.create cotroller also for that in controller package and annoted with @Controller
6.run on server
************************
3.
***********************
1.create service interface add default methos like save,delete,list,getbyid
2.create service implementation class which implements interface add unimplemented methodes
3. only call dao to perform operations in service part.
4.@autowired the dao interface.
1.Anotation
a.@autowired =controller =Iservice,
              dao=JdbcTemplate
              service=IDao
b.@Controller in controller
c.@service in Service
*********************
4.
*********************
.in dao package create interface and implementation class also,in interface add method
in implementation class add proper queries.
And @autowired @Autowired
    JdbcTemplate template;    
    public void setTemplate(JdbcTemplate template) {    
        this.template = template;    
    }
6.in controller part redirect the page after succussful opertion like index to view page.
7.save and run on the server 
8.for saving add mysql or psql dependency in pom file and add bean properties in dispatcher-servlet.xml file
9.again save ad run on server.

******************************
5.validation

**************************
validation in Employee Project

create EmployeeValidator class which implements validator and Annoted with @component annotation

for annotation add this line in servlet file

 <context:annotation-config/>

import package validator(org.springframework.validation)

add unimplemented method

add message.properties file in src/main/resources

then add following in servlet.xml file

<bean id="messageSource"
       class="org.springframework.context.support.ResourceBundleMessageSource">
       <property name="basename" value="message" />
    </bean>

provide value as file name

add this in jsp page
    <td><form:errors path="email" cssClass="error"/></td>
     in header part add this

<style type="text/css">
.error{
color:red;
}

add this in controller 
@Autowired
private EmployeeValidator employeeValidator;

@InitBinder
protected void initBinder(WebDataBinder binder) {
    binder.addValidators(employeeValidator);
}

then add this also in controller change accordingly in save method of form

@RequestMapping(value="/save",method = RequestMethod.POST)    
    public String save(@ModelAttribute("emp")  @Validated Emp emp,BindingResult result){    

    
        if (result.hasErrors()) {
            return "empform";
        } else {
            dao.save(emp);    
            return "redirect:/viewemp";
        }

 
    } 

****************************************
6.Add Bootstrap
******************************************
search bootstrap CDN getting started

UI BootStrap CDN
after title in head

<!-- Latest compiled and minified CSS -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">

<!-- Optional theme -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap-theme.min.css" integrity="sha384-rHyoN1iRsVXV4nD0JutlnGaslCJuC7uwjduW9SVrLvRYooPp2bWYgmgJQIXwl/Sp" crossorigin="anonymous">

#####################################

before this add
</body>

<!-- Latest compiled and minified JavaScript -->
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>

**************************************************************************************************************
7….Localization..using Cookies
1..add this 3 bean in  follo file

servlet.xml

 <!-- Bean For localization -->
     <bean id="messageSource" class="org.springframework.context.support.ResourceBundleMessageSource">
        <property name="basename" value="message" />
         <property name="defaultEncoding" value="UTF-8" />
    </bean>
    
 
    <bean id="localeResolver"
       class="org.springframework.web.servlet.i18n.CookieLocaleResolver">
       <property name="defaultLocale" value="en" />
       <property name="cookieName" value="kscodesCookie" />
       <property name="cookieMaxAge" value="3600" />
    </bean>
 
    <bean id="localeChangeInterceptor"
       class="org.springframework.web.servlet.i18n.LocaleChangeInterceptor">
       <property name="paramName" value="language" />
    </bean>
 
    <bean
       class="org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerMapping">
       <property name="interceptors">
           <list>
               <ref bean="localeChangeInterceptor" />
           </list>
       </property>
    </bean>

create 2- files in resources folder    
src-main-java-resources

message_en.properties

welcome.emp = Employee
#\u0915\u0930\u094D\u092E\u091A\u093E\u0930\u0940
emp.name.empty = Please Enter a Name.
emp.dob.empty=Please Enter a Date of Birth.
emp.gender.empty=Select gender.
emp.city.empty=Select at least one city.
emp.food.empty=Select at least one food.
emp.phno.empty=Please Enter a Mobile Number.
emp.phno.invalid=Please Enter valid Mobile Number.
emp.email.empty=Please Enter a Email.
emp.email.invalid=Please Enter valid Email
emp.acno.empty=Please Enter a Account No.
emp.ifsc.empty=Please Enter a IFSC Code.

message_hi.properties

welcome.emp = \u0915\u0930\u094D\u092E\u091A\u093E\u0930\u0940
emp.ifsc.empty=\u0939\u093F\u0902\u0926\u0940
emp.name.empty =\u0915\u0943\u092A\u092F\u093E \u090F\u0915 \u0928\u093E\u092E \u0926\u0930\u094D\u091C \u0915\u0930\u0947\u0902\u0964
emp.dob.empty=\u0915\u0943\u092A\u092F\u093E \u091C\u0928\u094D\u092E \u0924\u093F\u0925\u093F \u0926\u0930\u094D\u091C \u0915\u0930\u0947\u0902\u0964
 emp.gender.empty= \u0932\u093F\u0902\u0917 \u091A\u0941\u0928\u0947\u0902\u0964
 emp.city.empty=\u0915\u092E \u0938\u0947 \u0915\u092E \u090F\u0915 \u0936\u0939\u0930 \u091A\u0941\u0928\u0947\u0902\u0964
 emp.food.empty=\u0915\u092E \u0938\u0947 \u0915\u092E \u090F\u0915 \u092D\u094B\u091C\u0928 \u091A\u0941\u0928\u0947\u0902\u0964
 emp.phno.empty=\u0915\u0943\u092A\u092F\u093E \u090F\u0915 \u092E\u094B\u092C\u093E\u0907\u0932 \u0928\u0902\u092C\u0930 \u0926\u0930\u094D\u091C \u0915\u0930\u0947\u0902\u0964
 emp.phno.invalid=\u0915\u0943\u092A\u092F\u093E \u092E\u093E\u0928\u094D\u092F \u092E\u094B\u092C\u093E\u0907\u0932 \u0928\u0902\u092C\u0930 \u0926\u0930\u094D\u091C \u0915\u0930\u0947\u0902\u0964
 emp.email.empty=\u0915\u0943\u092A\u092F\u093E \u090F\u0915 \u0908\u092E\u0947\u0932 \u0926\u0930\u094D\u091C \u0915\u0930\u0947\u0902\u0964
emp.email.invalid=\u0915\u0943\u092A\u092F\u093E \u0935\u0948\u0927 \u0908\u092E\u0947\u0932 \u0926\u0930\u094D\u091C\u093C \u0915\u0930\u0947\u0902
emp.acno.empty=\u0915\u0943\u092A\u092F\u093E \u090F\u0915 \u0916\u093E\u0924\u093E \u0938\u0902\u0916\u094D\u092F\u093E \u0926\u0930\u094D\u091C \u0915\u0930\u0947\u0902
emp.ifsc.empty=\u0915\u0943\u092A\u092F\u093E \u090F\u0915 IFSC \u0915\u094B\u0921 \u0926\u0930\u094D\u091C \u0915\u0930\u0947\u0902\u0964

in jsp page add this

    <%@ taglib uri="http://www.springframework.org/tags/form" prefix="form"%>    
     <%@ taglib uri="http://www.springframework.org/tags" prefix="spring"%>    
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>    

header part
 Language : <a href="?language=en">English</a>|<a href="?language=hi">HINDI</a>
    
    
     Current Locale : ${pageContext.response.locale}
     
footer part

welcome.springmvc : <spring:message code="welcome.emp" text="default text" />

3……...to add localization in filed add the error message in form field like comment actual text part
<td><!--  Name :--><spring:message code="lbl.name"/></td>
                
               <td><form:input path="name" /></td>
                    <td><form:errors path="name" cssClass="error"/></td>
                
           </tr>
add error messages in properties file from label field

4.to add location in comment part then only change in both messages.properties file 
message_en.properties

welcome.emp = Employee
emp.name.empty = Please Enter a Name.
emp.dob.empty=Please Enter a Date of Birth.
emp.gender.empty=Select gender.

message_hi.properties

welcome.emp = \u0915\u0930\u094D\u092E\u091A\u093E\u0930\u0940
emp.name.empty =\u0915\u0943\u092A\u092F\u093E \u090F\u0915 \u0928\u093E\u092E \u0926\u0930\u094D\u091C \u0915\u0930\u0947\u0902\u0964
emp.dob.empty=\u0915\u0943\u092A\u092F\u093E \u091C\u0928\u094D\u092E \u0924\u093F\u0925\u093F \u0926\u0930\u094D\u091C \u0915\u0930\u0947\u0902\u0964
 emp.gender.empty= \u0932\u093F\u0902\u0917 \u091A\u0941\u0928\u0947\u0902\u0964

********************************************
8.Localization Using Session
implement session in localization

annd bean in servlet.xml file which is given below

<bean id="localeResolver"
  class="org.springframework.web.servlet.i18n.SessionLocaleResolver">
    <property name="defaultLocale" value="en" />
</bean>

we can do same operation using cookies also

need to add follo bean in servlet file
  <bean id="localeResolver" class="org.springframework.web.servlet.i18n.CookieLocaleResolver">
       <property name="defaultLocale" value="en" />
       <property name="cookieName" value="kscodesCookie" />
       <property name="cookieMaxAge" value="3600" />
    </bean>
 
#############################################################################################
9.Installation steps of postgres on ubanatu
#############################################################################################
 
photoes in cellphone
 
 
 
 
 
 
***********************************************************************************************************************************
9. 1 Postgres  connection with springMVC project Employee
***********************************************************************************************************************************
1.Add this in servlet.xml file and comment mysql bean

<!-- Bean for Postgres database -->
<bean id="multipartResolver"
        class="org.springframework.web.multipart.commons.CommonsMultipartResolver">
        <property name="maxUploadSize" value="8000000" />
    </bean>
    <bean id="ds"
        class="org.springframework.jdbc.datasource.DriverManagerDataSource">
        <property name="driverClassName"
            value="org.postgresql.Driver" />
        <property name="url"
            value="jdbc:postgresql://localhost:5432/Employee" />
        <property name="username" value="postgres" />
        <property name="password" value="root" />
        <property name="connectionProperties">
            <props>
                <prop key="socketTimeout">10</prop>
            </props>
        </property>
    </bean>

add this in pom file
<!-- https://mvnrepository.com/artifact/postgresql/postgresql -->
        <dependency>
            <groupId>postgresql</groupId>
            <artifactId>postgresql</artifactId>
            <version>9.1-901-1.jdbc4</version>
        </dependency>

create database and table in PG Admin
 
this step done in Employee project after file upload and display 
 
************************************************************************************************************************************
9.2study and implement how to save data in hindi in database
study and implement how to save data in hindi in database
add in web.xml file in exiting project SpringMVCCRUDSimple

<filter>
       <filter-name>encodingFilter</filter-name>
       <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
       <init-param>
           <param-name>encoding</param-name>
           <param-value>UTF-8</param-value>
       </init-param>
       <init-param>
           <param-name>forceEncoding</param-name>
           <param-value>true</param-value>
       </init-param>
    </filter>

    <filter-mapping>
       <filter-name>encodingFilter</filter-name>
       <url-pattern>/*</url-pattern>
    </filter-mapping>
 

servlet.xml

add this in database url
 ?charSet=UTF-8

eg…

<property name="url"
       
    value="jdbc:postgresql://localhost:5432/Employee?charSet=UTF-8" />
this actually working but in mysql there is issue regarding ?charSet=UTF-8

need to check for mysql

postgres is working fine
#########################################################################
10.Implementation of DataTable
read and implement datatable




1.Add datatable link in index file like

<li><a href="viewempDataTable">View Employee DataTable</a></li>
add this link in all bootstrap pages
Servlet.xml

<mvc:resources mapping="/resources/**"
       location="/resources/" cache-period="31556926" />
    <mvc:annotation-driven />



pom.xml add dependency

<dependency>
           <groupId>org.codehaus.jackson</groupId>
           <artifactId>jackson-mapper-asl</artifactId>
           <version>1.9.13</version>
       </dependency>

update Maven Project

controller

@RequestMapping("/viewstuddatatable")
//    @ResponseBody
    public String viewStudentDataTable(Model model, Locale locale) throws JsonGenerationException, JsonMappingException, IOException{
       List<Student> list=studentService.getStudents();
//       LoadDataService dataService = new LoadDataService();
       ObjectMapper mapper = new ObjectMapper();
       model.addAttribute("studentList", mapper.writeValueAsString(studentService.getStudents()));
       return "viewDataTable";    
    }

****
*************************************************************
No need to add This
************************************************************

datatable.js-webapp-resources-js-datatable.js

$(document).ready(function(){
var data =eval('${studentList}');
var table = $('#StudentTable').DataTable( {
"aaData": data,
"aoColumns": [
    { "mData": "id"},
    { "mData": "standard" },
    { "mData": "gender" },
    { "mData": "city" },
    { "mData": "dob" },
    { "mData": "smssubscription" }
    ]
});
});

*********************************************************************************

create jsp page viewDataTable.jsp  in jsp page first add basic bootstrap tag in head and then navbar in body
then add actual datatable bootstrap tags then add remainning part below nav bar end update maven project and run on server

<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<%@taglib prefix="spring" uri="http://www.springframework.org/tags"%>
<%@ page session="false" %>
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml"
    xmlns:th="http://www.thymeleaf.org">
<head>
<meta charset="utf-8" />
<title>Spring Boot + JPA + Datatables</title>
<link rel="stylesheet"
    href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
<script
    src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
<script
    src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
<link rel="stylesheet"
    href="https://cdn.datatables.net/1.10.12/css/jquery.dataTables.min.css">
<script
    src="https://cdn.datatables.net/1.10.12/js/jquery.dataTables.min.js"></script>
<%-- <script type="text/javascript"
    src="${pageContext.request.contextPath}/resources/js/datatable.js"></script> --%>
</head>

<body>
    <h1>Student Table</h1>
    <table id="StudentTable" class="display">

       <!-- Header Table -->
       <thead>
           <tr>
               <th>Id</th>
               <th>Name</th>
               <th>Standard</th>
               <th>Gender</th>
               <th>City</th>
               <th>Date of Birth</th>
               <th>SMS Service</th>
           </tr>
       </thead>
       <!-- BODY -->
        
        
       <!-- Footer Table -->
       <tfoot>
           <tr>
               <th>Id</th>
               <th>Name</th>
               <th>Standard</th>
               <th>Gender</th>
               <th>City</th>
               <th>Date of Birth</th>
               <th>SMS Service</th>
           </tr>
       </tfoot>
    </table>

</body>
</html>
<script type="text/javascript">
$(document).ready(function(){
    var data =eval('${studentList}');
    var table = $('#StudentTable').DataTable( {
         "aaData": data,
         "aoColumns": [
           { "mData": "id"},
           { "mData": "name"},
           { "mData": "standard"},
           { "mData": "gender"},
           { "mData": "city"},
           { "mData": "dob"},
           { "mData": "smssubscribe"}
         ],
         "paging":false
       });
});
</script>

###################################################################################11.Upload File(jpeg,odt,pdf) on default path /images  (in hidden file)

create link in index.jsp page also add in all pages bootstrap link like below
<li><a href="upload">Upload File</a></li>
add in pom.xml file

<!-- Dependacy for file upload -->
        <dependency>
            <groupId>commons-fileupload</groupId>
            <artifactId>commons-fileupload</artifactId>
            <version>1.2.1</version> <!-- makesure you put a correct version here -->
        </dependency>
        <!-- for upload -->
        <dependency>
<groupId>commons-io</groupId>
<artifactId>commons-io</artifactId>
<version>2.4</version>
</dependency>

add this bean in servlet.xml    
<bean id="multipartResolver" class="org.springframework.web.multipart.commons.CommonsMultipartResolver"/>

 add this in controller
private static final String UPLOAD_DIRECTORY ="/images";
    private static final int THRESHOLD_SIZE = 1024 * 1024 * 3; // 3MB
    
    @RequestMapping("upload")
    public ModelAndView uploadForm(){
        return new ModelAndView("upload");    
    }
    
    @RequestMapping(value="savefile",method=RequestMethod.POST)
    public ModelAndView saveimage( @RequestParam CommonsMultipartFile file,HttpSession session) throws Exception
    {
        
    DiskFileItemFactory factory = new DiskFileItemFactory();
    factory.setSizeThreshold(THRESHOLD_SIZE);
    factory.setRepository(new File(System.getProperty("java.io.tmpdir")));
    
    ServletFileUpload upload = new ServletFileUpload(factory);
    ServletContext context = session.getServletContext();

    String uploadPath = context.getRealPath(UPLOAD_DIRECTORY);
    System.out.println(uploadPath);    

    byte[] bytes = file.getBytes();
    BufferedOutputStream stream =new BufferedOutputStream(new FileOutputStream(new File(uploadPath + File.separator + file.getOriginalFilename())));
    stream.write(bytes);
    stream.flush();
    stream.close();
    
    return new ModelAndView("upload","filesuccess","File successfully saved!");
    }

create folder images in webapp

create jsp page follow the same same steps above for bootstrap and links upload .jsp

in jsp page it is necessary to add this 3 tag lines to support file upload

<%@ taglib uri="http://www.springframework.org/tags/form" prefix="form"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>
<%@ taglib uri="http://www.springframework.org/tags" prefix="spring"%>

<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
    <%@ taglib uri="http://www.springframework.org/tags/form" prefix="form"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>
<%@ taglib uri="http://www.springframework.org/tags" prefix="spring"%>
    
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>File Upload</title>
<!-- Latest compiled and minified CSS -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">

<!-- Optional theme -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap-theme.min.css" integrity="sha384-rHyoN1iRsVXV4nD0JutlnGaslCJuC7uwjduW9SVrLvRYooPp2bWYgmgJQIXwl/Sp" crossorigin="anonymous">

</head>
<body>
<!-- Nav bar  Start -->
<nav class="navbar navbar-default">
  <div class="container-fluid">
    <!-- Brand and toggle get grouped for better mobile display -->
    <div class="navbar-header">
      <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1" aria-expanded="false">
        <span class="sr-only">Toggle navigation</span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
      </button>
      <a class="navbar-brand" href="#">Brand</a>
    </div>

    <!-- Collect the nav links, forms, and other content for toggling -->
    <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
      <ul class="nav navbar-nav">
        <li class="active"><a href="employeeForm">Employee Info Form <span class="sr-only">(current)</span></a></li>
        <li><a href="viewemp">View Employee Data</a></li>
          <li><a href="viewempDataTable">View Employee DataTable</a></li>
          <li><a href="upload">Upload File</a></li>
          
        </li>
      </ul>
       </form>
       </div><!-- /.navbar-collapse -->
  </div><!-- /.container-fluid -->
</nav>
<!-- Nav Bar End -->

<h1>File Upload Example - JavaTpoint</h1>

<h3 style="color:red">${filesuccess}</h3>
<form:form method="post" action="savefile1" enctype="multipart/form-data">
<p><label for="image">Choose Image</label></p>
<p><input name="file" id="fileToUpload" type="file" /></p>
<p><input type="submit" value="Upload"></p>
</form:form>

<!-- Latest compiled and minified JavaScript -->
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>

</body>
</html>



update Maven Project and run on server


###################################################################################12….upload file in given path like in project inside web-app images folder like imgaes
/home/sonali/eclipse-workspace/Employee/src/main/webapp/images/


first change the path in given line in upload file code

    private static final String UPLOAD_DIRECTORY ="/home/sonali/eclipse-workspace/Employee/src/main/webapp/images/";


then comment some part 

//ServletContext context = session.getServletContext();

3.remove same in the line like
String uploadPath = context.getRealPath(UPLOAD_DIRECTORY);

String uploadPath = UPLOAD_DIRECTORY;

in following code of file upload

private static final String UPLOAD_DIRECTORY ="/home/sonali/eclipse-workspace/Employee/src/main/webapp/images/";
    private static final int THRESHOLD_SIZE = 1024 * 1024 * 3; // 3MB
    
    @RequestMapping("upload")
    public ModelAndView uploadForm(){
        return new ModelAndView("upload");    
    }
    
    @RequestMapping(value="savefile1",method=RequestMethod.POST)
    public ModelAndView saveimage( @RequestParam CommonsMultipartFile file,HttpSession session) throws Exception
    {
        
    DiskFileItemFactory factory = new DiskFileItemFactory();
    factory.setSizeThreshold(THRESHOLD_SIZE);
    factory.setRepository(new File(System.getProperty("java.io.tmpdir")));
    
    ServletFileUpload upload = new ServletFileUpload(factory);
    //ServletContext context = session.getServletContext();

    String uploadPath = UPLOAD_DIRECTORY;
    System.out.println(uploadPath);    

    byte[] bytes = file.getBytes();
    BufferedOutputStream stream =new BufferedOutputStream(new FileOutputStream(new File(uploadPath + File.separator + file.getOriginalFilename())));
    stream.write(bytes);
    stream.flush();
    stream.close();
    
    return new ModelAndView("upload","filesuccess","File successfully saved!");
    }




update and run on server.

###############################################################################
13….Display the uploaded file
upload and display image in exiting project Employee

1......give link in index file like in other pages also in bootstrap
 <li><a href="displayFile">Display File</a></li>

2....in servlet.xml file

add this

<mvc:resources
        location="file:///home/cdac-kharghar2/eclipse-workspace1/SpringMVCCRUDSimple/src/main/webapp/images/"
        mapping="/upload_images/**" />
        <mvc:annotation-driven />

same path given for image upload...

for this path goto home that eclipse workspace click on same project then src-main-webapp-images-RT copy path and paste

3......in controller
@RequestMapping(value = "/displayFile")
    public String displayFile(Model model, HttpServletRequest request) {
        File uploadLocationDir = new File(UPLOAD_DIRECTORY);
        String[] files = uploadLocationDir.list();
        System.out.println("files " + Arrays.toString(files));
        model.addAttribute("fileList", files);
        //model.addAttribute("filePath", downloadDirectory);
        return "displayFile";
    }




in follo line
File uploadLocationDir = new File(UPLOAD_DIRECTORY);
UPLOAD_DIRECTORY === is the variable name of upload file path given below

    private static final String UPLOAD_DIRECTORY ="/home/cdac-kharghar2/eclipse-workspace1/SpringMVCCRUDSimple/src/main/webapp/images";

we must add  4 tag in display page 
    
<%@ taglib uri="http://www.springframework.org/tags/form" prefix="form"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>
<%@taglib prefix="spring" uri="http://www.springframework.org/tags"%>
<%@ page session="false"%>

4......create displayFile.jsp page

<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
    <%@ taglib uri="http://www.springframework.org/tags/form" prefix="form"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>
<%@taglib prefix="spring" uri="http://www.springframework.org/tags"%>
<%@ page session="false"%>
    
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
<!-- Latest compiled and minified CSS -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">

<!-- Optional theme -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap-theme.min.css" integrity="sha384-rHyoN1iRsVXV4nD0JutlnGaslCJuC7uwjduW9SVrLvRYooPp2bWYgmgJQIXwl/Sp" crossorigin="anonymous">

</head>
<body>

<h1>Display File</h1>
 <!-- Nav bar  Start -->
<nav class="navbar navbar-default">
  <div class="container-fluid">
    <!-- Brand and toggle get grouped for better mobile display -->
    <div class="navbar-header">
      <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1" aria-expanded="false">
        <span class="sr-only">Toggle navigation</span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
      </button>
      <a class="navbar-brand" href="#">Brand</a>
    </div>

    <!-- Collect the nav links, forms, and other content for toggling -->
    <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
      <ul class="nav navbar-nav">
        <li class="active"><a href="employeeForm">Employee Info Form <span class="sr-only">(current)</span></a></li>
        <li><a href="viewemp">View Employee Data</a></li>
          <li><a href="viewempDataTable">View Employee DataTable</a></li>
          <li><a href="displayFile">Display File</a></li>
          
        </li>
      </ul>
       </form>
       </div><!-- /.navbar-collapse -->
  </div><!-- /.container-fluid -->
</nav>
<!-- Nav Bar End -->
<table>
        <tr>
            <th>File Name</th>
            <th>File Preview</th>
            <th>Download</th>
        </tr>
        <c:forEach var="fileName" items="${fileList}">
            <tr>
                <td>${fileName}</td>
                <td><img  src="<spring:url value='/upload_images/${fileName}'/>" height="100" width="100"></td>
                <td><a href='downloadFile/${fileName}'>Click Here</a></td>
        </tr>
        </c:forEach>
    </table>

<!-- Latest compiled and minified JavaScript -->
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>

</body>
</html>

5...update Maven project and run on server
 
14...download the uploaded and displayed file by link

add this in display.jsp page
<td><a href='downloadFile/${fileName}' download>Click Here</a></td>

table>
        <tr>
            <th>File Name</th>
            <th>File Preview</th>
            <th>Download</th>
        </tr>
        <c:forEach var="fileName" items="${fileList}">
            <tr>
                <td>${fileName}</td>
                <td><img  src="<spring:url value='/upload_images/${fileName}'/>" height="100" width="100"></td>
                <td><a href='downloadFile/${fileName}' download>Click Here</a></td>

        </tr>
        </c:forEach>
    </table>

add this part in controller part

    @ResponseBody
    @RequestMapping(value = "/downloadFile/{fileName}", produces = MediaType.IMAGE_JPEG_VALUE)
    public byte[] downloadFile(@PathVariable("fileName") String fileName) throws IOException {
        InputStream in = new FileInputStream(filePath+fileName+".jpeg");
        return IOUtils.toByteArray(in);
    }

here filePath is path given to store uploadedfile we need to give this path 

for example:
    private static final String UPLOAD_DIRECTORY ="/home/cdac-kharghar2/eclipse-workspace1/SpringMVCCRUDSimple/src/main/webapp/images/";

 filePath == UPLOAD_DIRECTORY

update maven project and run on server.

#########################################################################15..save the image in database
#########################################################################

1.create database images in pg admin
id serial
img_data bytea
img_title character varing

2.add this in dao/service part

if there is only dao part then add 2 and 3 steps code
  /*******Insert Image Into Database********/
public int insertRecords(String title, MultipartFile photo) throws IOException
{
        byte[] photoBytes = photo.getBytes();
        String sql = "INSERT INTO images(img_title,img_data) VALUES (?,?)";
        return template.update(sql, new Object[] { title, photoBytes });
}



3. add these 2 in controller savefile part

    String filename = file.getOriginalFilename();

               dao.insertRecords(filename,file);


@RequestMapping(value="savefile1",method=RequestMethod.POST)
    public ModelAndView saveimage( @RequestParam CommonsMultipartFile file,HttpSession session) throws Exception
    {
        
    DiskFileItemFactory factory = new DiskFileItemFactory();
    factory.setSizeThreshold(THRESHOLD_SIZE);
    factory.setRepository(new File(System.getProperty("java.io.tmpdir")));
    
    ServletFileUpload upload = new ServletFileUpload(factory);
    //ServletContext context = session.getServletContext();

    String uploadPath = UPLOAD_DIRECTORY;
    String filename = file.getOriginalFilename();
    System.out.println(uploadPath);    

    byte[] bytes = file.getBytes();
    BufferedOutputStream stream =new BufferedOutputStream(new FileOutputStream(new File(uploadPath + File.separator + file.getOriginalFilename())));
    stream.write(bytes);
    employeeService.insertRecords(filename,file);

    stream.flush();
    stream.close();
    
    return new ModelAndView("upload","filesuccess","File successfully saved!");
    }

2.1  if there is service part then first add interface in dao and service 

    public int insertRecords(String title, MultipartFile photo) throws IOException ;    

2.2 in implementation of service and dao add this unimplemented methods  
   
service
             @Override
    public int insertRecords(String title, MultipartFile photo) throws IOException {
        // TODO Auto-generated method stub
        return employeeDao.insertRecords(title,photo);
    }
dao
      /*******Insert Image Into Database********/
    public int insertRecords(String title, MultipartFile photo) throws IOException
    {
            byte[] photoBytes = photo.getBytes();
            String sql = "INSERT INTO images(img_title,img_data) VALUES (?,?)";
            return template.update(sql, new Object[] { title, photoBytes });
    }
   

then check into database file save or not
