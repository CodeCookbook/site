+++
date = "2016-10-01T11:28:44-04:00"
draft = false
title = "Why I'm a React Native Developer: a Response to Ariel Elkin"
description = "Ariel Elkin recently wrote an excellent article in which he explains why he thinks using react native is a bad idea. While several good points were made, I think that ultimately the argument he puts forth is lacking. In this article, I try to say where I think Ariel goes wrong in his arguments against react native."
subscribecopy = "React Native recipes delivered to your inbox"
+++

Most of my experience is in native Android and iOS mobile development. Although I've typically been skeptical of cross-platform development tools for mobile, I think that react native is really neat. In fact, I'm willing to bet that its the future of mobile development.

I disagree with Ariel Elkin, who recently wrote [an excellent article](https://arielelkin.github.io/articles/why-im-not-a-react-native-developer.html) in which he explains why he thinks using react native is a bad idea. While several good points were made, I think that ultimately the argument he puts forth is lacking. In this article, I try to say where I think Ariel goes wrong in his arguments against react native.

# React Native's licensing isn't Scary

In the section (cleverly) titled "Patently Daunting," Ariel argues that by using React Native,

>...I’m jeopardising...both the platform my app depends on as well as my intellectual property.

He then says that:

>iOS apps enter the App Store entirely at Apple’s discretion. I don’t want to multiply that uneasy feeling by two.

There's [a comment on HN](https://news.ycombinator.com/item?id=12597488) that pretty well addresses this concern:

>...if you're not using React you're probably already using open source software. And in the JS ecosystem that probably means you're using software under MIT, BSD and ISC licenses [licensed used by projects like jQuery, Angular, and Ember], which have no patent provisions whatsoever.

>In other words: unless you have an explicit patent grant, you're at risk of being sued by the owners of whatever patents you happen to be infringing upon. The only difference is that you're entirely reliant upon the goodwill of the patent owners while React explicitly shields you unless you sue Facebook over patents.

Organizations that use any of these open source packages do so because they believe that the advantages of using these packages outweigh the risk of getting sued for patent infringement. This seems like a reasonable assessment in general and, as we'll see in the next sections, I think its a reasonable assessment for react native in particular.

# Its not Javascript, its just good business

After pointing out some of the legal concerns with using React Native, Ariel launches into a long list of Javascript's flaws. The list is meant to convey that "switching to React Native from Swift is the technical regress: you have to adopt and use JavaScript, a language that’s technically defective, unsafe, and slowly evolving." Ariel then suggests that Flow isn't a solution to Javascript's problems because Flow doesn't ultimately address JavaScript's "insecure foundations." I think neither of these arguments are particularly compelling. Here's why.

## The Business benefits of RN probably outweigh Javascript's defects

I don't like javascript. I think that many of the criticisms Ariel lodges against javascript are spot on. For better or worse, however, we have to think about javascript from the perspective of the people who are paying our salaries. If we think about javascript from their perspective, I think we'll see that the benefits of RN outweigh javascript's flaws.

Mobile developers have been a special snowflake in many companies hiring and development processes. We have our own skills with our own tools and our own languages. This costs businesses a lot of money. The ability for businesses to say, "Our web developers can now develop mobile applications" is a huge win.<sup>1</sup>

Mobile developers have been writing almost exactly the same code for two different platforms for almost 8 years now. Businesses simply do not want to keep paying us to write the same code twice, especially now that the mobile app market is becoming saturated.<sup>2</sup>

This is what our employers are thinking:

"You mean I can share up to 85% percent of my code across both platforms<sup>3</sup> and I can have my web developers contribute to mobile apps and all I have to do is use an inferior programming language? Sign me up!"

The relevant question here isn't "Is javascript inferior to Swift?" Rather, the question is: "Is Swift so much better than javascript that it will save me the money I could save from sharing 85% percent of my code across platforms and sharing my web team with my mobile team?" The answer to this later, more relevant question is almost certainly "no."

## Flow isn't like Flossing

Later on in the Javascript section, Ariel argues that Flow, Facebook's static type-checker, doesn't solve javascript's problems. Again, some of the points here are good, but ultimately, they are inadequate as an argument against React Native.

The first argument against flow has something to do with it being built on "weak foundations:"

>Impressive as an engineering effort Flow may be, it remains a superset of JavaScript and thus forces you to build on inherently weak foundations...The fact that things can be built on unsafe foundations does not make the foundations any safer, nor does it make the process any more efficient.

Everything Ariel says is correct in this passage. Javascript is a weak foundation, flow is built on a weak foundation, and flow doesn't make the "the foundations any safer".

Here's the thing: all programming languages are built on an unsafe, unproductive foundation: binary. This fact doesn't bother us because the abstractions and tools we've built on top of binary and assembly are good enough to allow us to be very productive.

We can say the same thing about javascript. If we build abstractions and tools that allow us to be productive, then the foundation doesn't matter. Regarding Ariel's claim that the tools built on top of javascript haven't actually made developers more effective, Facebook, Google, Microsoft, and many other companies using flow and typescript seem to disagree.

There's a second argument that Ariel offers against the usefulness of flow that's pretty interesting:

>There is another fundamental problem with these palliative measures [like flow and linters]. Safeguards, like laws, are worth very little if they’re not actually enforced by the authorities and respected by the community. Flow doesn’t stop you from building and running React Native apps with code bound to generate runtime crashes. And that is a basic safety requirement for a programming language: if it’s a preventable error, the language should actively prevent it, it should stop me from writing and running unsafe code by default, not as an afterthought.

A part of this seems right to me. All other things being equal, a language is better if by default it catches errors earlier on in the development cycle.

I do, however, think that its wrong to suggest that the tools and languages that are built on top of js are worth little unless the entire community uses those tools. A single team can get a lot from enforcing the usage of these tools, and it doesn't take much work to fail your builds if your javascript is missing type annotations.

Over time, I think more and more teams will see the value in these tools and we'll get the benefit of having our dependencies leveraging these javascript-enhancing tools.

# For better or worse, React Native is a good bet

None of this, by the way, is meant to suggest that building on top of javascript is *ideal*. If I had my way, I'd prefer Ariel's solution: replace javascript. However, if we're trying to make good decisions about which tech to invest in as developers, we have to think about this issue from the perspective of the people who are paying our salaries and these people have *a lot* invested in javascript.

I believe in react native so much, in fact, that I'm betting my business on it. Code Cookbook is a company that helps teams start using react native for their business. Sign up for our email list below for updates and online tutorials on react native or email me at **chefmatt[that symbol that comes between a handle and a domain]codecookbook.co** so we can chat about how I can help.

p.s. As you can tell from the obnoxious way I just published my email, I hate spam, so I won't be spamming your inbox either.

## Notes:

1. I'm not saying here that native mobile development expertise isn't (at this point) necessary for being an effective react native mobile developer.

1. For evidence of the saturation of the app market, take a look at slides 11 and 12 of [this past year's internet trends report](http://www.kpcb.com/internet-trends).

1. [Facebook was able to achieve 85% code reused for their conference app.](http://makeitopen.com/tutorials/building-the-f8-app/planning/)

