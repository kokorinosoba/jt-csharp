# About <span>ASP.NET</span> MVC
## ASP(Active Server Pages)
[Active Server Pages - Wikipedia](https://en.wikipedia.org/wiki/Active_Server_Pages)

Active Server Pages (ASP) is Microsoft's first server-side script engine for dynamically generated web pages.  
Extension of IIS(Internet Information Services) which is the server software made by Microsoft.
ASP uses server-side scripting to generate content that is sent to the client's web browser. The ASP interpreter reads and executes all script code between <% and %> tags, the result of which is content generation. These scripts were written using VBScript, JScript, or PerlScript. The @Language directive, the `<script language="manu" runat="server" />` syntax or server configuration can be used to select the language.

## <span>ASP.NET</span>
[ASP.NET - Wikipedia](https://en.wikipedia.org/wiki/ASP.NET)

<span>ASP.NET</span> is an open-source server-side web-application framework designed for web development to produce dynamic web pages developed by Microsoft to allow programmers to build dynamic web sites, applications and services.

## ASP.NET MVC
[ASP.NET MVC - Wikipedia](https://en.wikipedia.org/wiki/ASP.NET_MVC)

The <span>ASP.NET</span> MVC is a discontinued web application framework developed by Microsoft, which implements the model–view–controller (MVC) pattern. It is open-source software, apart from the ASP.NET Web Forms component which is proprietary.

vs <span>ASP.NET</span>
- Easy of unit testing
  - Server environment is required to generate pages classes
  - It is hard to automate user operations
- Enlargement of controllers
- Originality
  - Hard to develop for those who has never developed a web form before
  - Supported only windows server 

Features
- MVC
- Front controllers
- Divide by server control(web form)
- Multiplatform

### Controller
A component to create the processing for a request
- Processing for request
- Response data creation
- Session management

### View
A component to create a response
- Response creation
- Client side processing 

### Model
A component to create a business logic
- Connection to data model
- Validation

## Cookies and Sessions
[How Do Web Sessions Work? | Hazelcast](https://hazelcast.com/glossary/web-session/)

A cookie is a small piece of data from a web site that is stored on a visitor’s browser to help the website track the visitor’s activity on the web site. Sessions and cookies are sometimes conflated, creating confusion. More specifically, session IDs and cookie IDs are confused. While they are closely related, they are not the same thing. A cookie identifies, often anonymously, a specific visitor or a specific computer. Cookies can be used for authentication, storing site preferences, saving shopping carts, and server session identification

By knowing who is visiting a site and what they’ve done before, web developers can customize pages to create a personalized web experience. For example, a cookie may store information such as your name and preferences that it gathered when you filled out a form, then use that information to populate pages you visit throughout one or multiple web sessions.

Server logs typically contain both the session ID and cookie ID of a visitor. A web session ID is unique to a specific visit, while a cookie is unique to a specific visitor and thus (developers hope) remains the same through multiple web sessions. By mapping a single cookie ID to multiple session IDs, developers and analysts can get a clearer picture of how visitors interact with their web applications.
