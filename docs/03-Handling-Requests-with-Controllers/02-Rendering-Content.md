# Rendering Content

###### Showing content to the user.

A big part of a controller's task is to respond to the user. In Wheels you can 
respond to the user in three different ways:

- Displaying content
- Redirecting to another URL
- Sending a file

You can only respond once per request. If you do not explicitly call any of the 
response functions ( [renderPage()][1], [sendFile()][2] etc) then Wheels will 
assume that you want to show the view for the current controller and action and 
do it for you.

This chapter covers the first method listed above—displaying content. The 
chapters about [Redirecting Users][3] and [Sending Files][4] cover the other two
response methods.

## Rendering a Page
This is the most common way of responding to the user. It's done with the 
[[renderPage()][1]][1] function, but most often you probably won't call it 
yourself and instead let Wheels do it for you.

Sometimes you will want to call it though and specify to show a view page for a 
controller/action other than the current one. One common technique for handling 
a form submission, for example, is to show the view page for the 
controller/action that contains the form (as opposed to the one that just 
handles the form submission and redirects the user afterwards). When doing this,
it's very important to keep in mind that [renderPage()][1] will 
**not run the code** for the controller's action—all it does is process the view
page for it.

You can also call [renderPage()][1] explicitly if you wish to cache the response
or use a different layout than the default one.

If the `controller` and `action` arguments do not give you enough flexibility, 
you can use the `template` argument that is available for [renderPage()][1].

Refer to the [Pages][5] chapter for more details about rendering content. More 
specifically, that chapter describes where to place those files and what goes in
them.

## Rendering a Partial
This is done with the [renderPartial()][7] function. It's most often used with 
AJAX requests that are meant to update only parts of a page.

## Rendering Nothing at All
Sometimes you don't need to return anything at all to the browser. Perhaps 
you've made an AJAX request that does not require a response or executed a 
scheduled task that no end user sees the results of. In these cases you can use 
the [renderNothing()][8] function to tell Wheels to just render an empty page to
the browser.

## Rendering Text
This is done with the [renderText()][9] function. It just returns the text you 
specify. In reality it is rarely used but could be useful as a response to AJAX 
requests sometimes.

## Rendering to a Variable
Normally when you call any of the rendering functions, the result is stored 
inside an internal Wheels variable. This value is then outputted to the browser 
at the end of the request.

Sometimes you may want to do some additional processing on the rendering result 
before outputting it though. This is where the `returnAs` argument comes in 
handy. It's available on both [renderPage()][1] and [renderPartial()][7]. 
Setting `returnAs` to `string` will return the result to you instead of placing 
it in the internal Wheels variable.

## Caching the Response
Two of the functions listed above are capable of caching the content for you; 
[renderPage()][1] and [renderPartial()][7]. Just pass in `cache=true` (to use 
the default cache time set in `config/settings.cfm`) or `cache=x` where `x` is 
the number of minutes you want to cache the content for. Keep in mind that this 
caching respects the global setting set for it in your configuration files so 
normally no pages will be cached when in Design or Development mode.

We cover caching in greater detail in the [Caching][9] chapter.

## Using a Layout
The [renderPage()][1] function accepts an argument named `layout`. Using this 
you can wrap your content with common header/footer style code. This is such an 
important concept though so we'll cover all the details of it in the chapter 
called [Using Layouts][10].

[1]: TBD
[2]: TBD
[3]: 03-Redirecting-Users.md
[4]: 04-Sending-Files.md
[5]: ../05-Displaying-Views-to-Users/01-Pages.md
[6]: TBD
[7]: TBD
[8]: TBD
[9]: 14-Caching.md
[10]: ../05-Displaying-Views-to-Users/04-Layouts.md