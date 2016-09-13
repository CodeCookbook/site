+++
date = "2016-09-12T23:41:28-04:00"
draft = true
title = "How React Native Dies"
+++

## by Chef Matt @ [Code Cookbook](http://codecookbook.co)

>Recruiter: "Why don't you want to work at a company that uses Cordova?"

>Me: "Look at the top 100 apps in the app store. None of those apps use Cordova. I want to build the best possible apps I can, so I don't use Cordova, nor am I interested in learning how to build Cordova applications."

As the above (actual) conversation suggests, I've typically been skeptical of any kind of mobile development that doesn't use the Android and iOS SDKs. I was skeptical of React Native too until I tried it. Now, I honestly believe that React Native *can* be a viable contender to standard mobile application development. This is exciting. Writing nearly identical code for both platforms is a huge waste of time, so the "learn once. write everywhere" value proposition is pretty compelling.

I really want react native to succeed, but there's a lot of hype around react native right now, and this hype can blind us to potentially deadly problems that react native faces as a technology. [Pre-mortems](https://hbr.org/2007/09/performing-a-project-premortem) are thought experiments designed to help us look past a project's hype and think carefully about what needs to change about a product so that it can be successful in the long run. This article is a pre-mortem on React Native. It's an invitation to imagine how react native dies so that we can make sure that it lives in the long run. I don't think anyone wants to to writing nearly identical code on both platforms, so we all have some work to do to make sure that React Native makes it.

### React Native, the Adoption Lifecycle, and "the Chasm"

![Adoption lifecycle](/img/adoption-lifecycle.png)

"[The adoption lifecycle](https://en.wikipedia.org/wiki/Technology_adoption_life_cycle)," as the name implies, divides a product's adopters into different categories based on when they'll adopt a product. Right now, I'd say that react native is being adopted by some "early adopters" like [Palantir](https://medium.com/@clayallsopp/react-native-in-production-2b3c6e6078ad#.bh69dkdlp), [Sound Cloud](https://developers.soundcloud.com/blog/react-native-at-soundcloud), [Artsy](http://artsy.github.io/blog/2016/08/15/React-Native-at-Artsy), and [Chalk and Chisel](https://chalkchisel.com/blog/ios-developer-react-native).

[Geoffrey Moore famously suggested](https://en.wikipedia.org/wiki/Crossing_the_Chasm) that its *more difficult* for a product to capture the *early majority* than it is to capture *early adopters*. Moreover, he claims that the many products and companies dies as a result of failing to "cross the chasm" between early adopters and the early majority.

Interestingly, he claims via a "High-Tech Parable" that a product is often at the edge of the chasm just when hype about a new product is at its greatest.

>...the company wins over several more visionary early adopters, including a handful of truly major deals...everyone is convinced it is time to ramp up...[one year later]...third quarter revenue results are in - and they're absolutely dismal...What the company staff interpreted as a ramp in sales leading smoothly "up the [adoption lifecycle] curve" was in fact an initial blip...and not the first indications of an emerging mainstream market.

> Crossing the Chasm, 23-24


I think that react native is actually close to the edge of the chasm, so the path forward for React Native, if we want to take Geoffrey Moore's model seriously, is to find a way to win over the early majority.

### Helping React Native Cross the Chasm

Who exactly is the early majority? Well, they are companies whose developers are more skeptical versions of me. These companies are full of native mobile developers who have invested a ton of time and energy learning the iOS and Android SDKs. These developers have seen Cordova come and go and they're skeptical that anything other than the iOS and Android SDKs can deliver a truly native *look and feel.*

**If this is true, then we can identify one thing that could kill react native: a user experience that doesn't *look and feel* like ordinary Android and iOS apps.**

This may seem obvious. After all, the whole point of react native is to let us build apps that feel like native apps without duplicating code across platforms. But hear me out. I think that many *react native developers are failing at this*.

Although react native is capable of delivering a native look and feel, I think many react native developers fail to take *full* advantage of this. Many react native applications that I look at still look like web applications. These applications don't exhibit any real concern for following the *UI design guidelines for the various platforms.*

I think that if react native dies, it'll be because it doesn't figure out how to make it easy for its community to build apps that fall in line with the Android and iOS UI and UX design specs. Maybe the folks at Facebook don't even necessarily need to change anything about react native for this to happen. Maybe we, as developers, just need to decide to do better with this.

As more native developers come on board, the job of convincing the others will be easier. This isn't just because people like to hop on band wagons. As [Eloy from Artsy](http://artsy.github.io/blog/2016/08/15/React-Native-at-Artsy/) and [James from Exponent](https://www.youtube.com/watch?v=2Zthnq-hIXA) have pointed out, native developers have insight on how to build better react native applications and when the skeptical native developers start seeing more quality react native apps, they'll eventually be won over.

### Conclusion

If you agree, then the next time you start a react native app, checkout the [Android](https://material.google.com/) and [iOS](https://developer.apple.com/ios/human-interface-guidelines/) design guidelines and tell you friends to do the same. If you think I'm wrong, then I'd love to hear what you think is the most threatening problem that react native faces on its way to mainstream adoption.

Either way, let's do what we can to make sure that we don't have to go back to writing the same code on two different platforms.

