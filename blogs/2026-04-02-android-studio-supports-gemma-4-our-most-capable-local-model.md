---
title: "Android Studio supports Gemma 4: our most capable local model for agentic coding"
url: "https://android-developers.googleblog.com/2026/04/android-studio-supports-gemma-4-local.html"
date: "2026-04-02T07:00:00.003-07:00"
author: "Android Developers (noreply@blogger.com)"
feed_url: "https://android-developers.googleblog.com/feeds/posts/default"
---
<img src="https://blogger.googleusercontent.com/img/a/AVvXsEgXYlRjbxC3pzK0IAAN_lsTJmGKOPQFRkB3VSQ_VASBbDptbLR-ZouiXNcNQ1ZLpyqcYhkFK4G8H7lf6IulQYuvjBEVPyzXRCDwDbf7HmNV16MyqsE53T6icyLQuXOmASIBNV05FzacpAf6Zcox4qIdg1jBK-rOK4KmTAYjFSlfSQ0lmrK8GhyltG-85k0" style="display: none;" />
<div><i>Posted by Matthew Warner, Google Product Manager</i></div><div><div class="separator" style="clear: both; text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjL2TZw-GrI4OzbxMKTVdt4f7mZwFKPSGFYnmekpRjBZmd_daEMz0fuBJ41EklTr72GScWmr6HF0gqTGypgUVjRAKvd5zTJKF58xwfwJqvzaeECy420fXJXmm67YxSg3b1qATc3tB5mccZHys2WmIvvtyAKQzkwjbnykEpdmxPo5kPbPuIYG2jKQ7L24IM/s8459/Gemma%204%20Android%20Studio-%20Blog.png" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjL2TZw-GrI4OzbxMKTVdt4f7mZwFKPSGFYnmekpRjBZmd_daEMz0fuBJ41EklTr72GScWmr6HF0gqTGypgUVjRAKvd5zTJKF58xwfwJqvzaeECy420fXJXmm67YxSg3b1qATc3tB5mccZHys2WmIvvtyAKQzkwjbnykEpdmxPo5kPbPuIYG2jKQ7L24IM/s16000/Gemma%204%20Android%20Studio-%20Blog.png" /></a></div><br /><i><br /></i><p>Every developer's AI workflow and needs are unique, and it's important to be able to choose how AI helps your development. In January, we introduced <a href="https://android-developers.googleblog.com/2026/01/llm-flexibility-agent-mode-improvements.html" target="_blank">the ability to choose any local or remote AI model to power AI functionality in Android Studio,</a> and today, we're announcing the availability of <a href="https://blog.google/innovation-and-ai/technology/developers-tools/gemma-4/" target="_blank">Gemma 4</a> for AI coding assistance in Android Studio. This new local model trained on Android development provides the best of both worlds: the privacy and cost-efficiency of on-device processing alongside state-of-the-art reasoning and tool-calling capabilities.</p>

<h3>AI assistance, locally delivered</h3>

<p>By running locally on your machine, Gemma 4 gives you AI code assistance that doesn't require an internet connection or an API key for its core operations. Key benefits include:</p>

<ul>
    <li><strong>Privacy and security:</strong> Your code stays on your machine. Gemma 4 processes all Agent Mode requests locally, making it an ideal choice for developers working with data privacy requirements or in secure corporate environments.</li>
    <li><strong>Cost efficiency:</strong> Run complex agentic workflows without worrying about hitting quotas. Gemma 4 is optimized to run efficiently on modern development hardware, utilizing local GPU and RAM to provide snappy, responsive assistance.</li>
    <li><strong>Offline availability:</strong> Use the agent to write code even when you don’t have an internet connection.</li>
    <li><strong>State-of-the-art reasoning:</strong> Gemma 4 delivers best-in-class reasoning, capable of complex multi-step coding tasks in Agent Mode.</li>
</ul>

<h3>Powerful agentic coding</h3>

<p>Gemma 4 was trained for Android development with agentic tool calling capabilities. When you select Gemma 4 as your local model, you can leverage Agent Mode for a variety of development use cases, such as:</p>

<ul>
    <li><strong>Designing new features:</strong> Developers can ask the agent to build a new feature or an entire app with commands like “build a calculator app” and the agent will not only generate the UI code but will use Android best practices like writing in Kotlin and using Jetpack Compose.</li>
    <li><strong>Refactoring:</strong> You can give high-level commands such as "Extract all hardcoded strings and migrate them to strings.xml." The agent will scan your codebase, identify instances requiring changes, and apply the edits across multiple files simultaneously.</li>
    <li><strong>Bug fixing and build resolution:</strong> If a project fails to build or has persistent lint errors, you can prompt the agent to "Build my project and fix any errors." The agent will navigate to the offending code and iteratively apply fixes until the build is successful.</li>
  </ul>
<br />
  <div class="separator" style="clear: both; text-align: center;">
    
    </div>
<h3>Recommended hardware requirements</h3>

<p>The 26B MoE is recommended for Android app developers using a machine with the minimum hardware requirements. Total RAM needed includes both Android Studio and Gemma.</p>

<table style="border-collapse: collapse; margin: 20px 0px; width: 100%;">
    <thead>
        <tr style="border-bottom: 1px solid rgb(204, 204, 204); text-align: left;">
            <th style="padding: 10px;">Model</th>
            <th style="padding: 10px;">Total RAM needed</th>
            <th style="padding: 10px;">Storage needed</th>
        </tr>
    </thead>
    <tbody>
        <tr style="border-bottom: 1px solid rgb(238, 238, 238);">
            <td style="padding: 10px;">Gemma E2B</td>
            <td style="padding: 10px;">8GB</td>
            <td style="padding: 10px;">2 GB</td>
        </tr>
        <tr style="border-bottom: 1px solid rgb(238, 238, 238);">
            <td style="padding: 10px;">Gemma E4B</td>
            <td style="padding: 10px;">12 GB</td>
            <td style="padding: 10px;">4 GB</td>
        </tr>
        <tr style="border-bottom: 1px solid rgb(238, 238, 238);">
            <td style="padding: 10px;">Gemma 26B MoE</td>
            <td style="padding: 10px;">24 GB</td>
            <td style="padding: 10px;">17 GB</td>
        </tr>
    </tbody>
</table>

<h3>Get started</h3>
<div style="text-align: left;">To get started, ensure you have the latest version of <strong>Android Studio</strong> installed.</div>
<ol>
    <li>Install an LLM provider, such as <a href="https://lmstudio.ai/" target="_blank">LM Studio</a> or <a href="https://ollama.com/" target="_blank">Ollama</a>, on your local computer.</li>
    <li>In <strong>Settings &gt; Tools &gt; AI &gt; Model Providers</strong> add your LM Studio or Ollama instance.&nbsp;<div class="separator" style="clear: both; text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjOCk_88MuU-aNx5gt9NI6iaMid6Y8nXz8R9BVzcE_nk0bMBO_7me6cxhkzZZjQIP3cEdJIHWZUEcSN1P1jq0tdu28i8Z2Xt2yqv4yWi6KaQTvZwXE5azXdfA8YmVRtMBx0RFIp8I3lCVwPh6GSXABRhJr0B6VQs24d2kTPtPW3Mc_B-G4tmR7WV9HhWhQ/s1948/Screenshot%202026-04-05%20at%209.14.11%E2%80%AFAM.png" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjOCk_88MuU-aNx5gt9NI6iaMid6Y8nXz8R9BVzcE_nk0bMBO_7me6cxhkzZZjQIP3cEdJIHWZUEcSN1P1jq0tdu28i8Z2Xt2yqv4yWi6KaQTvZwXE5azXdfA8YmVRtMBx0RFIp8I3lCVwPh6GSXABRhJr0B6VQs24d2kTPtPW3Mc_B-G4tmR7WV9HhWhQ/s16000/Screenshot%202026-04-05%20at%209.14.11%E2%80%AFAM.png" /></a></div><br /></li><li>Download the Gemma 4 model from <a href="https://ollama.com/library?sort=newest&amp;q=gemma" target="_blank">Ollama</a> or <a href="https://lmstudio.ai/models" target="_blank">LM Studio</a>. Refer to hardware requirements for model size selection.</li><li>In Agent Mode, select <b>Gemma 4</b> as your active model.</li>
</ol>

<div class="separator" style="clear: both; text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi8zC0sNBHZvfECFROpAR6fBWlhzLUWVHTp6ryJVP9RWKSjOurYNLzzsl6u7oxYnLiM-LkbRWHOxjbmvw4ACGu9Xio4hvPl83QooOdkuC7d8Kvmnv4Zp7R5LPh6NKM8T7m9YXcwxK8i_ke-NC50qIxvcVyfNp9MvLbLiCY7F7_51N0QTqwZ2ov6IOh8GTM/s1128/Screenshot%202026-04-05%20at%209.14.33%E2%80%AFAM.png" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="400" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi8zC0sNBHZvfECFROpAR6fBWlhzLUWVHTp6ryJVP9RWKSjOurYNLzzsl6u7oxYnLiM-LkbRWHOxjbmvw4ACGu9Xio4hvPl83QooOdkuC7d8Kvmnv4Zp7R5LPh6NKM8T7m9YXcwxK8i_ke-NC50qIxvcVyfNp9MvLbLiCY7F7_51N0QTqwZ2ov6IOh8GTM/w319-h400/Screenshot%202026-04-05%20at%209.14.33%E2%80%AFAM.png" width="319" /></a></div>
<p>For a detailed walkthrough on configuration, check out the official documentation on <a href="https://developer.android.com/studio/gemini/use-a-local-model" target="_blank">how to use a local model</a>.</p>

<p>We are excited to see how Gemma 4 enables more private, secure, and powerful development workflows. As always, your feedback is essential as we continue to refine the AI experience in Android Studio. If you find a bug or issue, please <a href="https://developer.android.com/studio/report-bugs" target="_blank">file an issue</a>. Also you can be part of our vibrant Android developer community on <a href="https://www.linkedin.com/showcase/androiddev/posts/?feedView=all" target="_blank">LinkedIn</a>, <a href="https://www.youtube.com/c/AndroidDevelopers/videos" target="_blank">YouTube</a>, or <a href="https://x.com/androidstudio" target="_blank">X</a>. Happy coding!</p></div>
