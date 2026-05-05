---
title: "The Fourth Beta of Android 17"
url: "https://android-developers.googleblog.com/2026/04/the-fourth-beta-of-android-17.html"
date: "2026-04-16T13:00:00.000-07:00"
author: "Android Developers (noreply@blogger.com)"
feed_url: "https://android-developers.googleblog.com/feeds/posts/default"
---
<img alt="Featured Metadata Image" src="https://blogger.googleusercontent.com/img/a/AVvXsEjRi_pfW7jI2yTebiDh4niQsTN1UL9MmUbO1DUy_ensXVVhStxJt5PUfBSQVOkpOC4ReJ1G2OMtpOZj0fq_3XiUY3fVq91hldHzZU-FPcHkLnG33NAEAV9Wxl4PVZWJHUwbbi1mZxUzQA5YIOGMhDC6mL00CYZei7fNAGDpMhK1JqtlwIOtoIVmIZn2XTE" />
<div><i>Posted by Dan Galpin, Developer Relations Engineer</i></div><div><div class="separator" style="clear: both; text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgEq1ZzmrzFT6TQrAQEnFFtGjEewn6KV8agh0vWMj1DDmokXVbYQns14dj-zgya-ALvJoS-CQd118t-RgMncsR6zfOPqNvvYOm_ETomGHIExmUwC2sJ3QqLJvS5wjRNhn2qESbefeVRJzcL_rQ5-LCgwgkFMMbdFikuEJUUgVdgKTFztSwaATcS9GYfHiw/s6314/Android%2017%20Beta-3%20Banner%20(1).png" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgEq1ZzmrzFT6TQrAQEnFFtGjEewn6KV8agh0vWMj1DDmokXVbYQns14dj-zgya-ALvJoS-CQd118t-RgMncsR6zfOPqNvvYOm_ETomGHIExmUwC2sJ3QqLJvS5wjRNhn2qESbefeVRJzcL_rQ5-LCgwgkFMMbdFikuEJUUgVdgKTFztSwaATcS9GYfHiw/s16000/Android%2017%20Beta-3%20Banner%20(1).png" /></a></div><br /><i><br /></i><p>Android 17 has reached beta 4, the last scheduled beta of this release cycle, a critical milestone for app compatibility and platform stability. Whether you're fine-tuning your app's user experience, ensuring smooth edge-to-edge rendering, or leveraging the newest APIs, Beta 4 provides the near-final environment you need to be testing with.</p>

<h3>Get your apps, libraries, tools, and game engines ready!</h3>
<p>If you develop an Android SDK, library, tool, or game engine, it's critical to prepare any necessary updates now to prevent your downstream app and game developers from being blocked by compatibility issues and allow them to target the latest SDK features. Please let your downstream developers know if updates are needed to fully support Android 17.</p><div class="separator" style="clear: both; text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj_sAqwsBgETGFvPCfaavnq5fNx4S-ey-UzxhfTp6A1Sji7v1ZrbVRF9gAkq_5VMcmV_R4PdWIE5HphsWTqujq6Q9FlRiUoBak1Gjt5VOl9f-__nzxX4JRm4rnVIyhRYiFqriSoliTmSGqRRN6iq8uDsWS1rI8ivYEAOBDdk8ARCUmR9_McCvuuU4ahGQ8/s3840/Android%2017%20Timeline%2001%20V02%20(2)%20(1).png" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj_sAqwsBgETGFvPCfaavnq5fNx4S-ey-UzxhfTp6A1Sji7v1ZrbVRF9gAkq_5VMcmV_R4PdWIE5HphsWTqujq6Q9FlRiUoBak1Gjt5VOl9f-__nzxX4JRm4rnVIyhRYiFqriSoliTmSGqRRN6iq8uDsWS1rI8ivYEAOBDdk8ARCUmR9_McCvuuU4ahGQ8/s16000/Android%2017%20Timeline%2001%20V02%20(2)%20(1).png" /></a></div><br /><p style="text-align: center;"><br /></p>

<p>Testing involves installing your production app or a test app making use of your library or engine using Google Play or other means onto a device or emulator running Android 17 Beta 4. Work through all your app's flows and look for functional or UI issues. Each release of Android contains platform changes that improve privacy, security, and overall user experience; review the app impacting behavior changes for apps <a href="https://developer.android.com/about/versions/17/behavior-changes-all">running on</a> and <a href="https://developer.android.com/about/versions/17/behavior-changes-17">targeting</a> Android 17 to focus your testing, including the following:</p>

<ul>
  <li><strong>Resizability on large screens:</strong> Once you target Android 17, you can no longer opt out of maintaining orientation, resizability and aspect ratio constraints <a href="https://developer.android.com/about/versions/17/changes/ff-restrictions-ignored">on large screens</a>.</li>
  <li><strong>Dynamic code loading:</strong> If your app targets Android 17 or higher, the Safer Dynamic Code Loading (DCL) protection <a href="https://developer.android.com/about/versions/14/behavior-changes-14#safer-dynamic-code-loading">introduced in Android 14</a> for DEX and JAR files now extends to native libraries. All native files loaded using System.load() must be marked as read-only. Otherwise, the system throws UnsatisfiedLinkError.</li>
  <li><strong>Enable CT by default:</strong> <a href="https://developer.android.com/privacy-and-security/security-config#CertificateTransparencySummary">Certificate transparency (CT)</a> is enabled by default. (On Android 16, CT is available but apps had to <a href="https://developer.android.com/privacy-and-security/security-config#certificateTransparency">opt in</a>.)</li>
  <li><strong>Local network protections:</strong> Apps targeting Android 17 or higher have <a href="https://developer.android.com/privacy-and-security/local-network-permission#android-17-enforcement">local network access blocked by default</a>. Switch to using privacy preserving pickers if possible, and use the new <a href="https://developer.android.com/reference/kotlin/android/Manifest.permission#access_local_network">ACCESS_LOCAL_NETWORK</a> permission for broad, persistent access.</li>
  <li><strong>Background audio hardening:</strong> Starting in Android 17, the audio framework enforces <a href="https://developer.android.com/about/versions/17/changes/bg-audio">restrictions on background audio interactions</a> including audio playback, <a href="https://developer.android.com/media/optimize/audio-focus">audio focus</a> requests, and <a href="https://developer.android.com/reference/android/media/AudioManager#adjustStreamVolume(int,%20int,%20int)">volume change</a> APIs. Based on your feedback, we’ve made some changes since beta 2, including targetSDK gating while-in-use FGS enforcement and exempting alarm audio. Full details available in <a href="https://developer.android.com/about/versions/17/changes/bg-audio">updated guidance</a>.</li>
</ul>

<h3>App memory limits</h3>
<p>Android is introducing app memory limits based on the device's total RAM to create a more stable and deterministic environment for your applications and Android users. In Android 17, limits are set conservatively to establish system baselines, targeting extreme memory leaks and other outliers before they trigger system-wide instability resulting in UI stuttering, higher battery drain, and apps being killed. While we anticipate minimal impact on the vast majority of app sessions, we recommend the <a href="https://developer.android.com/topic/performance/memory">following memory best practices</a>, including establishing a baseline for memory.</p>

<p>In the current implementation, <a href="https://developer.android.com/reference/android/app/ApplicationExitInfo#getDescription()">getDescription</a> in <a href="https://developer.android.com/reference/kotlin/android/app/ApplicationExitInfo">ApplicationExitInfo</a>&nbsp;will contain the string "MemoryLimiter" if your app was impacted. You can also use <a href="https://developer.android.com/topic/performance/tracing/profiling-manager/trigger-based-capture">trigger-based profiling</a> with <a href="https://developer.android.com/reference/android/os/ProfilingTrigger#TRIGGER_TYPE_ANOMALY">TRIGGER_TYPE_ANOMALY</a> to get heap dumps that are collected when the memory limit is hit.</p><p style="text-align: center;"><span id="docs-internal-guid-d4861f27-7fff-b96d-4122-2c1bbd6bff29"><span face="&quot;Google Sans&quot;, sans-serif" style="font-size: 11pt; vertical-align: baseline;"><span style="border: none; display: inline-block; height: 295px; overflow: hidden; width: 624px;"><img height="295" src="https://blogger.googleusercontent.com/img/a/AVvXsEg-8qL-AbPrbUrvk9Othuvb2JjbGvZwc--3CFZ3UrBMMEo4PMkcLGkEXioFkeNmGZX3TBmIYZ0iCeZ5hVKxnW2IvE4Q3SFsSNUXrx2bRRsbOdnvkjbtpr_SsNXMQvNIQGFaWI-yHM5wZlp8zby27MQW-JRL4YkKwEfUupEuOtt72ePjRSac518BqsHuTgg" style="margin-left: 0px; margin-top: 0px;" width="624" /></span></span></span></p>

<i><div style="text-align: center;"><i>The LeakCanary task in the Android Studio Profiler</i></div></i><p>To help you find memory leaks, Android Studio Panda adds LeakCanary integration directly in the Android Studio Profiler as a dedicated task, contextualized within the IDE and fully integrated with your source code.</p>

<p>A lighter memory footprint translates directly to smoother performance, longer battery life, and a premium experience across all form factors. Let’s build a faster, more reliable future for the Android ecosystem together!</p>

<h3>Profiling triggers for app anomalies</h3>
<p>Android introduces an on-device anomaly detection service that monitors for resource-intensive behaviors and potential compatibility regressions. Integrated with <a href="https://developer.android.com/topic/performance/tracing/profiling-manager/overview">ProfilingManager</a>, this service allows your app to receive profiling artifacts triggered by specific system-detected events.</p>

<p>Use the <a href="https://developer.android.com/reference/kotlin/android/os/ProfilingTrigger#trigger_type_anomaly">TRIGGER_TYPE_ANOMALY</a> trigger to detect system performance issues such as excessive binder calls and excessive memory usage. When an app breaches OS-defined memory limits, the anomaly trigger allows developers to receive app-specific heap dumps to help identify and fix memory issues. Additionally, for excessive binder spam, the anomaly trigger provides a stack sampling profile on binder transactions.</p>

<p>This API callback occurs prior to any system imposed enforcements. For example, it can help developers collect debug data before the app is terminated by the system due exceeding memory limits. To understand how to use the trigger check out our documentation on <a href="https://developer.android.com/topic/performance/tracing/profiling-manager/trigger-based-capture">trigger based profiling</a>.</p>

<pre class="prettyprint">val profilingManager = applicationContext.getSystemService(ProfilingManager::class.java)
val triggers = ArrayList&lt;ProfilingTrigger&gt;()  
triggers.add(ProfilingTrigger.Builder(
             ProfilingTrigger.TRIGGER_TYPE_ANOMALY))
val mainExecutor: Executor = Executors.newSingleThreadExecutor()
val resultCallback = Consumer&lt;ProfilingResult&gt; { profilingResult -&gt;
    if (profilingResult.errorCode != ProfilingResult.ERROR_NONE) {
        // upload profile result to server for further analysis          
        setupProfileUploadWorker(profilingResult.resultFilePath)
    } 
}
profilingManager.registerForAllProfilingResults(mainExecutor, resultCallback)
profilingManager.addProfilingTriggers(triggers)
</pre>

<h3>Post-Quantum Cryptography (PQC) in Android Keystore</h3>
<p>Android Keystore <a href="https://security.googleblog.com/2026/03/post-quantum-cryptography-in-android.html">added support</a> for the <a href="https://csrc.nist.gov/pubs/fips/204/final">NIST-standardized</a> ML-DSA (Module-Lattice-Based Digital Signature Algorithm). On supported devices, you can generate ML-DSA keys and use them to produce quantum-safe signatures, entirely in the device’s secure hardware. Android Keystore exposes the ML-DSA-65 and ML-DSA-87 algorithm variants through the standard Java Cryptographic Architecture APIs: <a href="https://developer.android.com/reference/java/security/KeyPairGenerator">KeyPairGenerator,</a> <a href="https://developer.android.com/reference/java/security/KeyFactory">KeyFactory</a>, and <a href="https://developer.android.com/reference/java/security/Signature">Signature</a>. For further details, see our <a href="https://developer.android.com/reference/android/security/keystore/KeyGenParameterSpec#example:-ml-dsa-key-pair-for-signing">developer documentation.</a></p>

<pre class="prettyprint">KeyPairGenerator generator = KeyPairGenerator.getInstance(
        “ML-DSA-65”, "AndroidKeyStore");
generator.initialize(
        new KeyGenParameterSpec.Builder(
                “my-key-alias”,
                KeyProperties.PURPOSE_SIGN | KeyProperties.PURPOSE_VERIFY)
        .build());
KeyPair keyPair = generator.generateKeyPair();
</pre>

<h3>Get started with Android 17</h3>
<p>You can <a href="https://www.google.com/android/beta">enroll any supported Pixel device</a> to get this and future Android Beta updates over-the-air. If you don’t have a Pixel device, you can <a href="https://developer.android.com/about/versions/17/get#on_emulator">use the 64-bit system images with the Android Emulator</a> in Android Studio.</p>

<p>If you are currently in the Android Beta program, you will be offered an over-the-air update to Beta 4. Continue to <a href="https://developer.android.com/about/versions/17/feedback">report issues and submit feature requests</a> on the <a href="https://developer.android.com/about/versions/16/feedback">feedback page</a>. The earlier we get your feedback, the more we can include in our work on the final release.</p>

<p>For the best development experience with Android 17, we recommend that you use the latest preview of <a href="https://developer.android.com/studio/preview">Android Studio (Panda)</a>. Once you’re set up, here are some of the things you should do:</p>

<ul>
  <li>Compile against the new SDK, test in CI environments, and report any issues in our tracker on the <a href="https://developer.android.com/about/versions/17/feedback">feedback page</a>.</li>
  <li>Test your current app for compatibility, learn whether your app is affected by changes in Android 17, and install your app onto a device or emulator running Android 17 and extensively test it.</li>
</ul>

<p>We’ll update the <a href="https://developer.android.com/about/versions/17/download">preview/beta system images</a> and SDK regularly throughout the Android 17 release cycle. Once you’ve installed a beta build, you’ll automatically get future updates over-the-air for all later previews and Betas. For complete information, visit the <a href="https://developer.android.com/about/versions/17">Android 17 developer site</a>.</p>

<h3>Join the conversation</h3>
<p>Your feedback remains our most valuable asset. Whether you’re an <a href="https://www.reddit.com/r/android_canary/">early adopter on the Canary channel</a> or an <a href="https://www.reddit.com/r/android_beta/">app developer testing on Beta 4</a>, consider joining our communities and filing feedback. We’re listening.</p></div>
