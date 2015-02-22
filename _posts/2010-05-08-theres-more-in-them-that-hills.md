--- 
title: "There's more in them thar hills..." 
layout: "post" 
permalink: "/2010/05/theres-more-in-them-that-hills.html" 
uuid: "8431719887998070747" 
guid: "tag:blogger.com,1999:blog-6728560442491983758.post-8431719887998070747" 
date: "2010-05-08 19:12:00"
updated: "2010-05-08 20:42:26" 
description: 
blogger: 
siteid: "6728560442491983758" 
postid: "8431719887998070747" 
comments: "0" 
categories: 
author: 
name: "Paul D'Ambra" 
url: "https://plus.google.com/114260096260757534167?rel=author" 
image: "//lh5.googleusercontent.com/-nN3yNuaSWDs/AAAAAAAAAAI/AAAAAAAABQU/ESeyTW5Duf0/s512-c/photo.jpg"
---

...than just the <a href="http://en.wikipedia.org/wiki/Factory_method_pattern">Factory pattern</a>.

So anyway I learn about design patterns and begin to use the factory pattern. And much like many other people I settle into a world where there are no other patterns. All is comfortable and fluffy and instantiated simply from calling code much as it was in days gone by.

<!--more-->

Then comes the day I need to handle the responses to a monthly mailing to over 70,000 email addresses and so I write this bitchin' code. Well maybe not bitchin'... what would be the right word - oh yeah "messy".
    <br />
    <br />It all started out really nice and clean but then I realised I needed to handle a couple of more cases than I'd intended when I began... and lots and lots of mail servers have been configured to return non-standard responses to failed mailings which
    is great for a human but not so great for a piece of software trying to classify that response.
    <br />
    <br />So time passes and I'm correctly responding to over 90% of the returns we get (all of which stops evil companies like Yahoo for blacklisting us because we're mailing to non-existent addresses) but my code has got really, really messy.
    <br />
    <br />Really messy.
    <br />
    <br />Oh God it's awful.
    <br />
    <br />I decide to refactor but no matter what I think of I can't get a Factory to solve my problem. Yeah, yeah I know but if you're gonna have a hammer it might as well be <a href="http://en.wikipedia.org/wiki/Golden_hammer">shiny</a>. Now, I could go ahead
    and invent my own solution but as far as I'm concerned writing software is about having to do less and that sounds like too much work.
    <br />
    <br />A little thought later and I decide it's time to add the command pattern to my arsenal. After all, I'm categorising mail, potentially selecting from a database, potentially updating a database, potentially replying to or forwarding an email and then
    deleting the mail I just dealt with. Wrap that up and then bash out the various alternatives I need. <a href="http://www.urbandictionary.com/define.php?term=bazinga">Bazinga</a>!
    <br />
    <br />I also like to be sure about what I'm doing before I start. Well, sometimes... So I dig out <a href="http://www.amazon.com/Patterns-Catalog-Reusable-Design-Illustrated/dp/0471258393">Patterns in Java Volume 1</a> and do a little reading and what I saw
    was such a great idea I realised I had to do everything I could not to forget... it is important to note that I am an idiot savant and it is possible that this is covered in most people's coding 101 and is adding nothing to the grand total of the
    internet. If that is the case then this blog is (as intended) the same as almost every other single one :-) read only by its writer.
    <br />
    {% highlight java %}
    public abstract class AbstractCommand {
    	public final static CommandManager manager = new CommandManager();
    	public abstract thePointOfThisClass();
    }
    {% endhighlight %}
    <br />
    <br />Now this made me double take... You might simply be saying "So What?" but I said "What the what?".
    <br />
    <br />See I write lots of code like this
    <br />
    {% highlight java %}
    public class MyClass { 
    	ThingManager thisThingManager = new ThingManager();
    	Thing thisThing = new Thing();
    	thisThingManager.doThisThingToThatOtherThing(thisThing);
    }
    {% endhighlight %}
    <br />
    <br />I dig <a href="http://en.wikipedia.org/wiki/Single_responsibility_principle">separation of responsibility</a> so I like to separate out a "manager" or "controller" class from the other classes who don't need the logic that it encapsulates.
    <br />
    <br />But of course that pretty tightly couples everything together. If I manage to strip a lot of code out of something (as I did when I bought the excellent <a href="http://www.dimastr.com/redemption/">Outlook redemption library</a> recently) then there's
    more to change.
    <br />
    <br />Here all of the logic for the command is bound up within it even though CommandManager class is still separate. I like that and I hadn't realised you could do this kind of thing by declaring something as static... I like to find a nice little elegant
    bit of sugar like that.
    <br />
 {% highlight java %}
 public class MyClass{
  Thing thisThing = new Thing();
  thisThing.DoThatThingToThisThing();
 }
 {% endhighlight %}
    <br />
    <br />or even better with a little factory magic in the background
    <br />
{%highlight java%}
public class MyClass{
	Thing.DoSomethingToThisThing(FactoryChoiceEnum.Choice);
}
{% endhighlight %}
    <br />
    <br />So we've got one line of code and with reasonable variable names it doesn't even need comments. For Example...
    <br />
{% highlight c# %}
public class MyClass {
	currentMailItem.DealWithThisMailItem(MailResponseEnum.Unsubscribe);
}
{% endhighlight %}
    <br />I hope that you've stumbled on this post and it solves your problem.
}
</div>