
Аннотации
---------

**@Path** - указывает относительный или абсолютный путь к данному ресурсу  
**@GET****, @POST, @PUT, @DELETE** (для методов) - отвечает за тип HTTP запроса релевантный этому методу  
**@Produces** (для методов) - MIME-type отсылаемого запроса, если аннотации нет то метод void. _"application/json"_ - JSON  
**@Consumes** (для методов) - MIME-type принимаемого запроса, если аннотации нет то метод не принимает данные(для POST и PUT). _"application/json"_ - JSON  
**@QueryParam** (для параметров) - Позволяет получить доступ к переданным через URL-параметрам  
**@PathParam** (для параметров)

Рекомендации для написания API
------------------------------

**URL**  
POST /dogs — создать новую собаку  
GET /dogs — получить список собак  
PUT /dogs — редактирование всех собак сразу  
DELETE /dogs — удаление всех собак

POST /dogs/12345 — вернуть ошибку (собака 12345 уже создана)  
GET /dogs/12345 — показать информацию о собаке  
PUT /dogs/12345 — редактировать собаку 12345  
DELETE /dogs/12345 — удалить

**Ошибки**  
Возможно только 3 варианта ответов API  
Запрос прошел успешно  
На вход были переданы неправильные данные — клиентская ошибка  
Произошла ошибка при обработке данных — серверная ошибка

Так что можно взять за основу 3 кода ответов:  
200 OK  
400 Bad Request (некорректный запрос)  
500 Internal server error (внутренняя ошибка сервера)

Если 3-х кодов вам недостаточно — возьмите еще 5:  
201 Created (Запись создана)  
304 Not Modified (Данные не изменились)  
404 Not Found (Данные не найдены)  
401 Unauthorized (Неавторизованный доступ)  
403 Forbidden (Доступ запрещен)

Пример с использование Spring, JSON, Maven, Servlet
---------------------------------------------------

**Зависимости необходимое для работы (pom.xml):**

    <dependencies\>
        <!--servlet-->
        <dependency\>
            <groupId\>javax.servlet</groupId\>
            <artifactId\>servlet-api</artifactId\>
            <version\>2.5</version\>
            <scope\>provided</scope\>
        </dependency\>
 
        <!--Apache CXF-->
        <dependency\>
            <groupId\>org.apache.cxf</groupId\>
            <artifactId\>cxf-rt-frontend-jaxrs</artifactId\>
            <version\>2.7.6</version\>
        </dependency\>
 
        <!--Spring-->
        <dependency\>
            <groupId\>org.springframework</groupId\>
            <artifactId\>spring-web</artifactId\>
            <version\>3.2.4.RELEASE</version\>
        </dependency\>
 
        <!--JSON provider-->
        <dependency\>
            <groupId\>org.codehaus.jackson</groupId\>
            <artifactId\>jackson-jaxrs</artifactId\>
            <version\>1.9.13</version\>
        </dependency\>
    </dependencies\>

  
**Сприноговый контекст (applicationContext.xml):**

    <context:component-scan base-package\="test.cxf"/>
    <bean id\="jsonProvider" class\="org.codehaus.jackson.jaxrs.JacksonJsonProvider"/>
 
    <bean id\="menu" class\="org.apache.cxf.jaxrs.JAXRSServerFactoryBean" init-method\="create"\>
        <property name\="address" value\="/rest/"/>
        <property name\="serviceBeans"\>
            <ref bean\="beanServiceImpl"/>
        </property\>
        <property name\="provider"\>
            <ref bean\="jsonProvider"/>
        </property\>
    </bean\>

  
**Дескриптор развертывания (web.xml):**

    <servlet\>
        <servlet-name\>CXFServlet</servlet-name\>
        <servlet-class\>
            org.apache.cxf.transport.servlet.CXFServlet
        </servlet-class\>
        <load-on-startup\>1</load-on-startup\>
    </servlet\>
 
    <servlet-mapping\>
        <servlet-name\>CXFServlet</servlet-name\>
        <url-pattern\>/cxf/\*</url-pattern\>
    </servlet-mapping\>

**Интерфейс для сервиса (BeanService.java):**

    package test.cxf;
 
    import javax.ws.rs.\*;
 
    public interface BeanService
    {
        @GET
        @Produces ("application/json")
        @Path ("test")
        Object getListTest ();
 
        @GET
        @Produces ("application/json")
        @Path ("test/{name}")
        Object getTest (@PathParam ("name")String name);
 
        @DELETE
        @Produces ("application/json")   //
        @Path ("test/{name}")
        Object deletetest (@PathParam ("name")String name);
 
        @POST
        @Consumes ("application/json")
        @Produces ("application/json")
        @Path ("test")
        Object addTest (BeanRequest beanRequest);
 
        @PUT
        @Produces ("application/json")
        @Consumes ("application/json")
        @Path ("test")
        Object editTest (@FormParam ("name")String name, @FormParam ("test")String test);
    }

**Реализация интерфейса сервиса (BeanServiceImpl.java):**

    package test.cxf;
 
    import org.springframework.stereotype.Service;
 
    import java.util.HashMap;
    import java.util.Map;
 
    @Service
    public class BeanServiceImpl implements BeanService
    {
    @Override
    public Object getListTest()
    {
        Map<String, String > map = new HashMap<>();
        map.put("test", "Hello World");
        return map;
    }
 
    @Override
    public Object getTest(String name)
    {
        String resp = "Your name: " + name;
        return resp ;
    }
    }
