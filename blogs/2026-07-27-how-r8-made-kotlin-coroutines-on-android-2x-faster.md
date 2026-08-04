---
title: "How R8 made Kotlin Coroutines on Android 2x faster"
url: "https://android-developers.googleblog.com/2026/07/how-r8-made-kotlin-coroutines-2x-faster.html"
date: "2026-07-27"
author: "Android Developers"
feed_url: "https://android-developers.googleblog.com/feeds/posts/default"
---
Posted by Andrei Shikov, Senior Software Engineer, Android Toolkit and Jonathan Starup, Software Engineer, R8 Team Starting from AGP 9.2.0, R8 optimizes most Atomic*FieldUpdater calls into Unsafe variants that perform 2x to 4x better on common operations . This has a particularly large impact on the kotlinx.atomicfu library that implements atomics for kotlinx.coroutines , making launching and cancelling coroutines up to 2x faster. In order to get the benefits, update your AGP to 9.2.0 or above.
