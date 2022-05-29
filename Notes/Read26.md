
# Intro to MVC

**MVC** is a design pattern or architecture which helps in developing the web application in a most efficient way when compared with the traditional ASP.NET Web Application.

While learning the basics of MVC, let us also understand the differences between both the approaches.

- In traditional ASP.NET web application approach, the user action and view (UI) are combined, i.e., the web page, say, Sample.aspx and code behind Sample.aspx.cs which has the action logic are both tightly coupled, whereas in MVC, the View only deals with UI of the page and the user actions are defined in Controller.

- In any web based application, a user initiates the requests which are nothing but actions. So, for action based requirement, ASP.NET Web Application follows the View based architecture which is not so efficient. MVC is action-based architecture. Based on the action, an appropriate View is displayed. The organization of the code inside MVC is very clean and organized.

- In ASP.NET, View State is used to maintain the state of the web page. Maintaining the state means maintaining the data between post backs for a user. This makes the web page heavy which, in turn, makes the trips to server inefficient. In MVC, we don’t have View State to store the state information.

>Unlike in ASP.NET where entire Page Life cycle is undergone for each request, the response time of the web page is very high which is not user friendly. In MVC, we don’t have the concept of page life cycle. When a request is made, the request hits the Controller which, in turn, hits the appropriate action. Then, the controller collects the required data from model and it is rendered in the appropriate View to user. So the response time is very low.

- Testing is as important as development. A code which is not tested properly may break in few scenarios which degrades the quality of the software. In ASP.NET, testing is tedious task as both View (UI) and Business logic (code behind) are tightly coupled. We cannot test code-behind separately. In MVC, it enhances the test-driven development by making the UI and action logic loosely coupled. As Models, Controllers and Views are all separate layers, they can be tested easily.



Basically, MVC makes the design of the application into three layers namely Model, View, and Controller. Each of these components are built to handle different aspects of the application.

**Model** layer represent the objects in our Application. Model is also a class which has all the objects and its properties and methods defined in it.

**View** Layer has all the html controls which define the UI of the application. Here in MVC, we don’t have drag and drop option for controls as we don’t use server controls. Instead we use Razor Engine available with Visual Studio by default which helps in rendering the View.

**Controller** basically handles the request from user. It is the heart of the MVC application as everyone say. It is responsible to handle the request and return a response to user by loading appropriate View with data from Model.


### Tag Helpers in ASP.NET Core

#### What are Tag Helpers
Tag Helpers enable server-side code to participate in creating and rendering HTML elements in Razor files. For example, the built-in ImageTagHelper can append a version number to the image name. Whenever the image changes, the server generates a new unique version for the image, so clients are guaranteed to get the current image (instead of a stale cached image). There are many built-in Tag Helpers for common tasks - such as creating forms, links, loading assets and more - and even more available in public GitHub repositories and as NuGet packages. Tag Helpers are authored in C#, and they target HTML elements based on element name, attribute name, or parent tag. For example, the built-in LabelTagHelper can target the HTML <label> element when the LabelTagHelper attributes are applied. If you're familiar with HTML Helpers, Tag Helpers reduce the explicit transitions between HTML and C# in Razor views. In many cases, HTML Helpers provide an alternative approach to a specific Tag Helper, but it's important to recognize that Tag Helpers don't replace HTML Helpers and there's not a Tag Helper for each HTML Helper. Tag Helpers compared to HTML Helpers explains the differences in more detail.

#### What Tag Helpers provide
###### An HTML-friendly development experience

For the most part, Razor markup using Tag Helpers looks like standard HTML. Front-end designers conversant with HTML/CSS/JavaScript can edit Razor without learning C# Razor syntax.

###### A rich IntelliSense environment for creating HTML and Razor markup

This is in sharp contrast to HTML Helpers, the previous approach to server-side creation of markup in Razor views. Tag Helpers compared to HTML Helpers explains the differences in more detail. IntelliSense support for Tag Helpers explains the IntelliSense environment. Even developers experienced with Razor C# syntax are more productive using Tag Helpers than writing C# Razor markup.

###### A way to make you more productive and able to produce more robust, reliable, and maintainable code using information only available on the server

### Build fast, responsive sites with Bootstrap


