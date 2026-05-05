---
title: "Experimental hybrid inference and new Gemini models for Android"
url: "https://android-developers.googleblog.com/2026/04/Hybrid-inference-and-new-AI-models-are-coming-to-Android.html"
date: "2026-04-17T13:00:00.000-07:00"
author: "Android Developers (noreply@blogger.com)"
feed_url: "https://android-developers.googleblog.com/feeds/posts/default"
---
<div style="display: none;">
  <img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgoPylOD-Ekyhe8AVg3iMvz6S1rsvUT_2Eb4m-77FRH4eebi5psKE8VJwu6xVxCzKXyTXpoxb3-k04e21C6-8KX0BQw0qiCBGToSHJzVYQRckBYqby9csdOCHWp_23DTfPOpWqfjFTL-vJh86Q-DhGLZnbs1L62q4iUsaHHWlpQ2oyLXo3OO0rGsH9ngxw/s1600/Hybrid%20inference%20solution%20for%20Android%20%20-%20Meta.png" />
</div><i>Posted by Thomas Ezan, Senior Developer Relations Engineer</i><div><i><br /></i></div><div><div class="separator" style="clear: both; text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg4_6pZO5RgA6G3e721iCaVVSfrwZStUKlddvxF2XgQc7M0VGtG8_KPiv7ZEkx4_a7xo2HiltuDyw55rGH7KoVn58oSU7xJ4LOWkaBfNn6TfdBxN9aCBsW-KMW9cN0wF-4NIFTXAOu4pBs0xP-43SDm3mpQ5yODRQ-NAdwP4SH6virP8z0CTDlC9fvOE9Y/s8419/Hybrid%20inference%20solution%20for%20Android%20-%20Blog%20%20(1).png" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg4_6pZO5RgA6G3e721iCaVVSfrwZStUKlddvxF2XgQc7M0VGtG8_KPiv7ZEkx4_a7xo2HiltuDyw55rGH7KoVn58oSU7xJ4LOWkaBfNn6TfdBxN9aCBsW-KMW9cN0wF-4NIFTXAOu4pBs0xP-43SDm3mpQ5yODRQ-NAdwP4SH6virP8z0CTDlC9fvOE9Y/s16000/Hybrid%20inference%20solution%20for%20Android%20-%20Blog%20%20(1).png" /></a></div><br /><i><br /></i><p>If you are an Android developer looking to implement innovative AI features into your app, we recently launched powerful new updates: Hybrid inference, a new API for Firebase AI Logic to leverage both on-device and Cloud inference, and support for new Gemini models including the latest Nano Banana models for image generation.</p>

<p>Let’s jump in!</p>

<h2>Experiment with hybrid inference</h2>

<p>With the new <a href="https://firebase.google.com/docs/ai-logic/hybrid/android/get-started?api=dev">Firebase API for hybrid inference</a>, we implemented a simple rule-based routing approach as an initial solution to let you use both on-device and cloud inference via a unified API. We are planning on providing more sophisticated routing capabilities in the future.</p>

<p>It allows your app to dynamically switch between Gemini Nano running locally on the device and cloud-hosted Gemini models. The on-device execution uses ML Kit's Prompt API. The cloud inference supports all the Gemini models from Firebase AI Logic in both Vertex AI and the Developer API.</p>

<p>To use it, add the <code>firebase-ai-ondevice</code> dependencies to your app along with Firebase AI Logic:</p>

<pre><code>dependencies {
 [...] 
 implementation("com.google.firebase:firebase-ai:17.11.0")
 implementation("com.google.firebase:firebase-ai-ondevice:16.0.0-beta01")
}</code></pre>

<p>During initialization, you create a <code>GenerativeModel</code> instance and configure it with specific inference modes, such as <code>PREFER_ON_DEVICE</code> (falls back to cloud if&nbsp;Gemini Nano is not available on the device) or <code>PREFER_IN_CLOUD</code> (falls back to on-device inference if offline):</p>

<pre><code>val model = Firebase.ai(backend = GenerativeBackend.googleAI())
    .generativeModel(
        modelName = "gemini-3.1-flash-lite",
        onDeviceConfig = OnDeviceConfig(
           mode = InferenceMode.PREFER_ON_DEVICE
        )
    )

val response = model.generateContent(prompt)</code></pre>

<p>The Firebase API for hybrid inference for Android is still experimental, and we encourage you to try it in your app, especially if you are already using Firebase AI Logic. Currently, on-device models are specialized for single-turn text generation based on text or single Bitmap image inputs. Review the <a href="https://firebase.google.com/docs/ai-logic/hybrid/android/get-started?api=dev#features-not-yet-available">limitations</a> for more details.</p>

<p>We just published a <a href="https://github.com/android/ai-samples/tree/main/samples/gemini-hybrid">new sample in the AI Sample Catalog leveraging the Firebase API for hybrid</a>; it demonstrates how the Firebase API for hybrid inference can be used to generate a review based on a few selected topics and then translating it into various languages. Check out the code to see it in action!</p><div><br /></div><div class="separator" style="clear: both; text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh6VaPz5_ZUBQI0yLu4Pkr0FVCWhKv-6TfUr3wmN3SMoVGZJLolOEP8vS966Y42P0bvC-EdQQocotdvE232ho72Ld772uWp8PNi-OdFq_IMNgQVjPNSJGoo38cDZZNYKgDH1lVi9nimXoTaaVqFm4eJNsBulaGIHmQnEM-7L2H5GgkVSou6tDfxIhXGftE/s1440/Hybrid_Inference-Inline-imagery%20(1).gif" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="640" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh6VaPz5_ZUBQI0yLu4Pkr0FVCWhKv-6TfUr3wmN3SMoVGZJLolOEP8vS966Y42P0bvC-EdQQocotdvE232ho72Ld772uWp8PNi-OdFq_IMNgQVjPNSJGoo38cDZZNYKgDH1lVi9nimXoTaaVqFm4eJNsBulaGIHmQnEM-7L2H5GgkVSou6tDfxIhXGftE/w640-h640/Hybrid_Inference-Inline-imagery%20(1).gif" width="640" /></a></div><div><br /></div>

<div style="text-align: center;"><i style="font-weight: normal;">The new hybrid inference sample in action</i></div>

<h2>Try our new models</h2>

<p>As part of the new Gemini models, we've released two models particularly helpful to Android developers and easy to integrate in your application via the Firebase AI Logic SDK.</p>

<h3>Nano Banana</h3>
<p>Last year we released Nano Banana, a state-of-the-art image generation model. And a few weeks ago, we released a couple of new Nano Banana models.</p>

<a href="https://deepmind.google/models/gemini-image/pro/">Nano Banana Pro (Gemini 3 Pro Image)</a> is designed for professional asset production and can render high-fidelity text, even in a specific font or simulating different types of handwriting.</div><div><br /><a href="https://deepmind.google/models/gemini-image/flash/">Nano Banana 2 (Gemini 3.1 Flash Image)</a> is the high-efficiency counterpart to Nano Banana Pro. It's optimized for speed and high-volume use cases. It can be used for a broad range of use cases (infographics, virtual stickers, contextual illustrations, etc.).<br /><ul>
</ul>

<p>The new Nano Banana models leverage real-world knowledge and deep reasoning capabilities to generate precise and detailed images.</p>

<p>We updated our Magic Selfie sample (use image generation to change the background of your selfie!) to use Nano Banana 2. The background segmentation is now handled directly with the image generation model which makes the implementation easier and lets Nano Banana 2 improved image generation capabilities shine. See it in action <a href="https://github.com/android/ai-samples/tree/main/samples/magic-selfie">here</a>.</p>

<div style="text-align: center;"><img height="640" src="https://blogger.googleusercontent.com/img/a/AVvXsEgtCKSZ8de610IYRl704wX8u30O56GNCKj10heNFZohoC92VVRGOJcZtYRY36DvVnHxy46KVeuunNTd8FNWmlFavvfDXn7EwwDNnUXEBXnTzBYHxL2Td1jvL30QuL-FozQ5IiDVAFaj8fyBkjmz5VTOAsASSjlY_AYZnHy_kAAuNit_C51uJgL7EeXHz7Q=w304-h640" width="304" /></div><i><div style="text-align: center;"><i>The updated Magic Selfie sample uses Nano Banana 2 to update a selfie background</i></div></i><p>You can use it via Firebase AI Logic SDK. Read more about it in the <a href="https://developer.android.com/ai/gemini/developer-api#generate-images">Android documentation</a>.</p>

<h3>Gemini 3.1 Flash-Lite</h3>
<p>We also released <a href="https://deepmind.google/models/model-cards/gemini-3-1-flash-lite/">Gemini 3.1 Flash-Lite</a>, a new version of the Gemini Flash-Lite family. The Gemini Flash-Lite models have been particularly favored by Android developers for its good quality/latency ratio and low inference cost. It’s been used by Android developers for various use-cases such as in-app messaging translation or generating a recipe from a picture of a dish.</p>

<p>Gemini 3.1 Flash-Lite, currently in preview, will enable more advanced use cases with latency comparable to Gemini 2.5 Flash-Lite. To learn more about this model, review the <a href="https://firebase.google.com/docs/ai-logic/models">Firebase documentation</a>.</p>

<h2>Conclusion</h2>

<p>It’s a great time to explore the new Hybrid sample in our catalog to see these capabilities in action and understand the benefits of routing between on-device and cloud inference. We also encourage you to check out our documentation to test the new Gemini models.</p></div>
