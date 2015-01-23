---
layout: post
title: Swift JSON Speed Tests
date: 2015-01-22 23:20:01
categories: [Swift JSON performance]
tags: []
published: true
author: Rick Windham (github.com/rickw)
---

The other day someone sent me this article [Swift Performance: Too Slow for Production](http://blog.sudeium.com/2014/12/10/swift-performance-too-slow-for-production/){:target="_blank"}, and after reading it I decided to do some testing myself. In the comments I found this repo [https://github.com/mnem/swift-json-speedtests](https://github.com/mnem/swift-json-speedtests){:target="_blank"} and forked it [(my fork)](https://github.com/swifttime/swift-json-speedtests){:target="_blank"}. 

I wanted to see how a pure Swift code base would preform, and after much digging&#8212;it seems almost all of the JSON parsing for iOS in Swift uses `NSJSONSerialization`&#8212;I found this library [json-swift](https://github.com/owensd/json-swift){:target="_blank"} and decided to write another test class using all Swift code. The easiest way to do this was simply to put the source code of the new libary in my fork of the speed test repo. 

The results were actually very interesting after changing optimzation levels.

![results](https://raw.githubusercontent.com/swifttime/swift-json-speedtests/master/results.jpg)

After optimzation was set to the "fastest unchcked" level for Swift code generation, the purely Swift code performed faster than the `JSONHelper` version. So it seems that some of the `infex` operator code in Swift is not as optimized as other types of code (at least for now). This was done on an iPod touch 5th generation, which is the slowest deivce that can run iOS 8.

In considering a project to be primarily written in Swift, we should take these results into account. I have not noticed any sluggishness in the UI with Swift yet, but I have not been testing anything very large and complex. I do believe that the benefits found in Swift are worth taking advantage of, and some of these possible pitfalls can be overcome with hypbrid code.

Next I'll have to do some profiling to see where the bottlenecks are.

Be well,<br />
Rick