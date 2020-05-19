# Index
- [Index](#index)
- [About <span>ASP.NET</span> MVC](#about-aspnet-mvc)
  - [ASP(Active Server Pages)](#aspactive-server-pages)
  - [<span>ASP.NET</span>](#aspnet)
  - [ASP.NET MVC](#aspnet-mvc)
    - [Controller](#controller)
    - [View](#view)
    - [Model](#model)
  - [Cookies and Sessions](#cookies-and-sessions)
- [Views](#views)
  - [Razor](#razor)
  - [Razor Syntax](#razor-syntax)
  - [Implicit Razor Expressions](#implicit-razor-expressions)
  - [Explicit Razor Expressions](#explicit-razor-expressions)
  - [Expression Encoding](#expression-encoding)
  - [Razor Code Blocks](#razor-code-blocks)
  - [Implicit Transitions](#implicit-transitions)
  - [Explicit Delimited Transition](#explicit-delimited-transition)
  - [Explicit Line Transition](#explicit-line-transition)
  - [Control Structures](#control-structures)
    - [Conditionals @if, else if, else, and @switch](#conditionals-if-else-if-else-and-switch)
    - [Looping @for, @foreach, @while, and @do while](#looping-for-foreach-while-and-do-while)
      - [`@for`](#for)
      - [`@foreach`](#foreach)
      - [`@while`](#while)
      - [`@do while`](#do-while)
    - [Compound @using](#compound-using)
    - [@try, catch, finally](#try-catch-finally)
    - [Comments](#comments)
  - [Directives](#directives)
    - [@attribute](#attribute)
    - [@code](#code)
    - [@functions](#functions)
  - [Helper Methods](#helper-methods)
    - [ActionLink](#actionlink)
    - [DisplayFor](#displayfor)
    - [DisplayNameFor](#displaynamefor)
    - [LabelFor](#labelfor)
    - [TextBoxFor](#textboxfor)
    - [HiddenFor](#hiddenfor)
    - [PasswordFor](#passwordfor)
    - [RadioButtonFor](#radiobuttonfor)
    - [CheckBoxFor](#checkboxfor)
    - [DropDownListFor](#dropdownlistfor)
    - [BeginForm](#beginform)
    - [model](#model-1)

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


# Views
## Razor
[razor syntax reference for ASP.NET Core | Microsoft Docs](https://docs.microsoft.com/en-us/aspnet/core/mvc/views/razor?view=aspnetcore-3.1)

Razor is a markup syntax for embedding server-based code into webpages. The Razor syntax consists of Razor markup, C#, and HTML. Files containing Razor generally have a .cshtml file extension. Razor is also found in Razor components files (.razor).

## Razor Syntax
[razor syntax reference for ASP.NET Core | Microsoft Docs](https://docs.microsoft.com/en-us/aspnet/core/mvc/views/razor?view=aspnetcore-3.1#razor-syntax)

Razor supports C# and uses the `f`@ symbol to transition from HTML to C#. Razor evaluates C# expressions and renders them in the HTML output.

When an `@` symbol is followed by a Razor reserved keyword, it transitions into Razor-specific markup. Otherwise, it transitions into plain C#.

To escape an `@` symbol in Razor markup, use a second `@` symbol:

```html
<p>@@Username</p>
```

The code is rendered in HTML with a single `@` symbol:

```html
<p>@Username</p>
```

## Implicit Razor Expressions
Implicit Razor expressions start with `@` followed by C# code:

```html
<p>@DateTime.Now</p>
<p>@DateTime.IsLeapYear(2016)</p>
```

With the exception of the C# await keyword, implicit expressions must not contain spaces. If the C# statement has a clear ending, spaces can be intermingled:

```html
<p>@await DoSomething("hello", "world")</p>
```

Implicit expressions cannot contain C# generics, as the characters inside the brackets (`<>`) are interpreted as an HTML tag. The following code is not valid:

```html
<p>@GenericMethod<int>()</p>
```

The preceding code generates a compiler error similar to one of the following:

- The "int" element wasn't closed. All elements must be either self-closing or have a matching end tag.
- Cannot convert method group 'GenericMethod' to non-delegate type 'object'. Did you intend to invoke the method?`

## Explicit Razor Expressions
Explicit Razor expressions consist of an `@` symbol with balanced parenthesis. To render last week's time, the following Razor markup is used:

```html
<p>Last week this time: @(DateTime.Now - TimeSpan.FromDays(7))</p>
```

Explicit expressions can be used to concatenate text with an expression result:

```html
@{
    var joe = new Person("Joe", 33);
}

<p>Age@(joe.Age)</p>
```

Without the explicit expression, `<p>Age@joe.Age</p>` is treated as an email address, and `<p>Age@joe.Age</p>` is rendered. When written as an explicit expression, `<p>Age33</p>` is rendered.

## Expression Encoding
C# expressions that evaluate to a string are HTML encoded. C# expressions that evaluate to IHtmlContent are rendered directly through IHtmlContent.WriteTo. C# expressions that don't evaluate to IHtmlContent are converted to a string by ToString and encoded before they're rendered.

```html
@("<span>Hello World</span>")
```

The code renders the following HTML:

```html
&lt;span&gt;Hello World&lt;/span&gt;
```

The HTML is shown in the browser as:

```html
<span>Hello World</span>
```

## Razor Code Blocks
Razor code blocks start with `@` and are enclosed by `{}`. Unlike expressions, C# code inside code blocks isn't rendered. Code blocks and expressions in a view share the same scope and are defined in order:

```html
@{
    var quote = "The future depends on what you do today. - Mahatma Gandhi";
}

<p>@quote</p>

@{
    quote = "Hate cannot drive out hate, only love can do that. - Martin Luther King, Jr.";
}

<p>@quote</p>
```

The code renders the following HTML:

```html
<p>The future depends on what you do today. - Mahatma Gandhi</p>
<p>Hate cannot drive out hate, only love can do that. - Martin Luther King, Jr.</p>
```

In code blocks, declare local functions with markup to serve as templating methods:

```html
@{
    void RenderName(string name)
    {
        <p>Name: <strong>@name</strong></p>
    }

    RenderName("Mahatma Gandhi");
    RenderName("Martin Luther King, Jr.");
}
```

The code renders the following HTML:

```html
<p>Name: <strong>Mahatma Gandhi</strong></p>
<p>Name: <strong>Martin Luther King, Jr.</strong></p>
```

## Implicit Transitions
The default language in a code block is C#, but the Razor Page can transition back to HTML:

```html
@{
    var inCSharp = true;
    <p>Now in HTML, was in C# @inCSharp</p>
}
```

## Explicit Delimited Transition
To define a subsection of a code block that should render HTML, surround the characters for rendering with the Razor `<text>` tag:

```html
@for (var i = 0; i < people.Length; i++)
{
    var person = people[i];
    <text>Name: @person.Name</text>
}
```

Use this approach to render HTML that isn't surrounded by an HTML tag. Without an HTML or Razor tag, a Razor runtime error occurs.

## Explicit Line Transition
To render the rest of an entire line as HTML inside a code block, use `@:` syntax:

```html
@for (var i = 0; i < people.Length; i++)
{
    var person = people[i];
    @:Name: @person.Name
}
```

Without the `@:` in the code, a Razor runtime error is generated.

Extra `@` characters in a Razor file can cause compiler errors at statements later in the block. These compiler errors can be difficult to understand because the actual error occurs before the reported error. This error is common after combining multiple implicit/explicit expressions into a single code block.

## Control Structures
### Conditionals @if, else if, else, and @switch
`@if` controls when code runs:

```html
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

`else` and `else if` don't require the `@` symbol:

```html
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
else if (value >= 1337)
{
    <p>The value is large.</p>
}
else
{
    <p>The value is odd and small.</p>
}
```

The following markup shows how to use a switch statement:

```html
@switch (value)
{
    case 1:
        <p>The value is 1!</p>
        break;
    case 1337:
        <p>Your number is 1337!</p>
        break;
    default:
        <p>Your number wasn't 1 or 1337.</p>
        break;
}
```

### Looping @for, @foreach, @while, and @do while
Templated HTML can be rendered with looping control statements. To render a list of people:

```html
@{
    var people = new Person[]
    {
          new Person("Weston", 33),
          new Person("Johnathon", 41),
          ...
    };
}
```

The following looping statements are supported:

#### `@for`

```html
@for (var i = 0; i < people.Length; i++)
{
    var person = people[i];
    <p>Name: @person.Name</p>
    <p>Age: @person.Age</p>
}
```

#### `@foreach`

```html
@foreach (var person in people)
{
    <p>Name: @person.Name</p>
    <p>Age: @person.Age</p>
}
```

#### `@while`

```html
@{ var i = 0; }
@while (i < people.Length)
{
    var person = people[i];
    <p>Name: @person.Name</p>
    <p>Age: @person.Age</p>

    i++;
}
```

#### `@do while`

```html
@{ var i = 0; }
@do
{
    var person = people[i];
    <p>Name: @person.Name</p>
    <p>Age: @person.Age</p>

    i++;
} while (i < people.Length);
```

### Compound @using
In C#, a using statement is used to ensure an object is disposed. In Razor, the same mechanism is used to create HTML Helpers that contain additional content. In the following code, HTML Helpers render a <form> tag with the @using statement:

```html
@using (Html.BeginForm())
{
    <div>
        Email: <input type="email" id="Email" value="">
        <button>Register</button>
    </div>
}
```

### @try, catch, finally

```html
@try
{
    throw new InvalidOperationException("You did something invalid.");
}
catch (Exception ex)
{
    <p>The exception message: @ex.Message</p>
}
finally
{
    <p>The finally statement.</p>
}
```

### Comments
Razor supports C# and HTML comments:

```html
@{
    /* C# comment */
    // Another C# comment
}
<!-- HTML comment -->
```

Razor comments are removed by the server before the webpage is rendered. Razor uses @* *@ to delimit comments. The following code is commented out, so the server doesn't render any markup:

```html
@*
    @{
        /* C# comment */
        // Another C# comment
    }
    <!-- HTML comment -->
*@
```

## Directives
Razor directives are represented by implicit expressions with reserved keywords following the @ symbol. A directive typically changes the way a view is parsed or enables different functionality.

### @attribute
The `@attribute` directive adds the given attribute to the class of the generated page or view. The following example adds the `[Authorize]` attribute:

```html
@attribute [Authorize]
```

### @code
_This scenario only applies to Razor components (.razor)._

The `@code` block enables a Razor component to add C# members (fields, properties, and methods) to a component:

```html
@code {
    // C# members (fields, properties, and methods)
}
```

For Razor components, `@code` is an alias of `@functions` and recommended over @functions. More than one `@code` block is permissible.

### @functions
The @functions directive enables adding C# members (fields, properties, and methods) to the generated class:

```html
@functions {
    // C# members (fields, properties, and methods)
}
```

In Razor components, use `@code` over `@functions` to add C# members.

For example:

```html
@functions {
    public string GetHello()
    {
        return "Hello";
    }
}

<div>From method: @GetHello()</div>
```

The code generates the following HTML markup:

```html
<div>From method: Hello</div>
```

`@functions` methods serve as templating methods when they have markup:

```html
@{
    RenderName("Mahatma Gandhi");
    RenderName("Martin Luther King, Jr.");
}

@functions {
    private void RenderName(string name)
    {
        <p>Name: <strong>@name</strong></p>
    }
}
```

## Helper Methods
### ActionLink
```html
@Html.ActionLink("LinkText", "ActionName", ["ControllerName"], ["RootController"])
```

### DisplayFor
Display content of property
```html
@Html.DisplayFor(model => Property)
```

### DisplayNameFor
```html
@Html.DisplayNameFor(model => Property)
```

### LabelFor
```html
@Html.LabelFor(model => Property)
```

### TextBoxFor
```html
@Html.TextBoxFor(model => Property)
```

### HiddenFor
```html
@Html.HiddenFor(model => Property)
```

### PasswordFor
```html
@Html.PasswordFor(model => Property)
```

### RadioButtonFor
```html
@Html.RadioButtonFor(model => Property, Value)
```

### CheckBoxFor
```html
@Html.CheckBoxFor(model => Property)
```

### DropDownListFor
```html
@Html.DropDownListFor(model => Property, SelectList)

@{
    var selectItems = new SelectListItem[] {
        new SelectListItem { Value = "1", Text = "Men" },
        new SelectListItem { Value = "2", Text = "Woen" },
    }
}

@Html.DropDownListFor(model => Property, new SelectList(selectItems, "Value", "Text", Property))
```

### BeginForm
```html
@using(@Html.BeginForm("ActionName", "ControllerName", [Parameter], [FormMethod.Post]) {
    <!-- Content -->
    <!-- Content -->
    <!-- Content -->

    <input type="submit">
}
```

### model
```html
@model ModelClassName
```
