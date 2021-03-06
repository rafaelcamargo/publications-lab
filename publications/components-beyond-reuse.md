# Components beyond reuse

We are living times where the Model/View/Controller concept is getting more and more obsolete making Component-Based approach the new standard to develop web applications now. 

However, as well as Component-based has become a so popular concept, I still see a lot of developers understanding components in a surprisingly weird way.

Which kind of weirdness? (you might be thinking)

a) In the first case, I see developers considering a View as a component. So, the "component" is, in fact, a huge piece of code extremely coupled with its context offering zero flexibility and reuse.
 
b) In the second one, I see developers not considering components with no behavior as components. They think markup encapsulation is not worth it. The result is a markup code replication and, consequently, pain at the moment you need to make changes in something that should be in one place only.

First of all, I would like to share the concept of what I believe to be a component. These are some wise words written by [Derick Bailey](https://twitter.com/derickbailey) in one of his [blog posts](https://derickbailey.com/2015/08/26/building-a-component-based-web-ui-with-modern-javascript-frameworks/):

> [...] a component in a web application’s UI could be the display panel used to show an employee’s information, such as their name, email address, employee id and more. This component may include buttons to edit the employee or other controls to perform other functions as well.
>
>What makes that example a component, in the end, is not just the code that controls it and the UI that represents it on the screen. Rather, it is the encapsulation of this behavior, UI and associated code and configuration, into something that is easily orchestrated into a larger system.

That said, I'll show you two other benefits beyond reuse which most of the people might not get at first glance:

## Small Responsibilities

When you encapsulate a small part of a View in an independent component, you are removing responsibilities from a huge piece of code that would be controlling the whole View. Imagine a website showing some Weather Card on its homepage. On the same homepage you can see a bar showing some current stock prices, a logo, a carousel containing some breaking news, and a card with real-time currency rates.

![small-responsibilities](https://user-images.githubusercontent.com/4738687/35834748-39799be0-0abe-11e8-89c3-48fb225acc4a.png)

Why should be the entire homepage controlled by one piece of code only? That doesn't make sense. The more you concentrate responsibility, less you enjoy the power of flexibility.

## Flexibility

Now, suppose the product team has decided to move the Weather Card to another View. You have in your hands the job of moving it from one View to another. So easy, right?

![flexibility](https://user-images.githubusercontent.com/4738687/35684732-f11f2b3e-074e-11e8-8224-5e1661c928d9.png)

Maybe. It depends on how you have organized the code distributed along the homepage. If the homepage is controlled by one piece of code only, you will probably need to make a delicate surgery on this. You have to remove the portion of code related to the Weather Card from those huge homepage files. Then, you will need to accommodate this exact same portion of code into the other View's files.

That's done, ok? Not yet.

The homepage tests will not pass anymore. You have just changed it. The same can happen to the other View tests, once you have also changed that. In a Component-Based approach, Weather Card is a component. It encapsulates all its markup, style, behavior and tests. So, all you have to do is moving a simple HTML tag from one View to the other one.

![delicate-surgery](https://user-images.githubusercontent.com/4738687/35834754-3f24ecca-0abe-11e8-9afa-9ea3700eac1b.png)

As you can see, reuse is actually a consequence of the above two benefits. When you break any View in several small pieces of code (small responsibilities), you make it so easy to move them from a context to another (flexibility) or, consequently, reuse them in any other View.
