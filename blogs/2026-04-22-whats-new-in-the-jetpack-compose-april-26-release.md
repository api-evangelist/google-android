---
title: "What's new in the Jetpack Compose April '26 release"
url: "https://android-developers.googleblog.com/2026/04/jetpack-compose-april-2026-updates.html"
date: "2026-04-22T16:00:00.000-07:00"
author: "Android Developers (noreply@blogger.com)"
feed_url: "https://android-developers.googleblog.com/feeds/posts/default"
---
<img src="https://blogger.googleusercontent.com/img/a/AVvXsEhgVW3uXlpqZ7PcHixqBlJ2AG19VCQosSAZfuCaqN5WnsvBCiGJdFo4WersXe30hoBz9w6iNYN6QfyY7ae3pNYaa6BQpveTPDKFXXEhJkMXFfxoJIUOXzoaslEJ6NkAA85VvXU4Kv5oZnfG1BDe5dlxsEVxkeyZ1OECfXLSmbcP46IPw5JBj2eBWascC6A" style="display: none;" /><div><i>Posted by Meghan Mehta,&nbsp;Android Developer Relations Engineer</i></div><div class="separator" style="clear: both; text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhZHE0FDmx0vqGgZ6V5OvwB9prJFgTdYZbOOkQ1h8bS_5BuTn3TyomD5gYJdqvcJP2rE5Ju4147sThpKYIiCKXQ3DTw2gQtVjWRM23gzPdpDo5jyblVPbjNRqiVVC9bWW92xNYtARsoCDWuyxAiYRyxtgeAQRqI_t6bTR2PFrdQZCHMgXgU82TBolFXXkw/s8583/0420%20Compose%201.11%20_%20Blog%20(1).png" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhZHE0FDmx0vqGgZ6V5OvwB9prJFgTdYZbOOkQ1h8bS_5BuTn3TyomD5gYJdqvcJP2rE5Ju4147sThpKYIiCKXQ3DTw2gQtVjWRM23gzPdpDo5jyblVPbjNRqiVVC9bWW92xNYtARsoCDWuyxAiYRyxtgeAQRqI_t6bTR2PFrdQZCHMgXgU82TBolFXXkw/s16000/0420%20Compose%201.11%20_%20Blog%20(1).png" /></a></div><br /><p><br /></p><p>Today, the Jetpack Compose April ‘26 release is stable. This release contains version 1.11 of core Compose modules (see the <a href="https://developer.android.com/jetpack/androidx/releases/compose-bom#bom-mapping">full BOM mapping</a>), shared element debug tools, trackpad events, and more. We also have a few experimental APIs that we’d love you to try out and give us feedback on.
</p>

  To use today’s release, upgrade your <a href="https://developer.android.com/develop/ui/compose/bom">Compose BOM</a> version to:

<pre><code>implementation(platform("androidx.compose:compose-bom:2026.04.01"))</code></pre>
<h3>Changes in Compose 1.11.0</h3>
<h2>Coroutine execution in tests</h2>
<p>
  We’re introducing a major update to how Compose handles test timing. Following the opt-in period announced in Compose 1.10, the v2 testing APIs are now the default, and the v1 APIs have been deprecated. The key change is a shift in the default test dispatcher. While the v1 APIs relied on <code><a href="https://developer.android.com/kotlin/coroutines/test#unconfinedtestdispatcher">UnconfinedTestDispatcher</a></code>, which executed coroutines immediately, the v2 APIs use the <code><a href="https://developer.android.com/kotlin/coroutines/test#standardtestdispatcher">StandardTestDispatcher</a></code>. This means that when a coroutine is launched in your tests, it is now queued and does not execute until the virtual clock is advanced.
</p>

<p>
  This better mimics production conditions, effectively flushing out race conditions and making your test suite significantly more robust and less flaky.
</p>

<p>
  To ensure your tests align with standard coroutine behavior and to avoid future compatibility issues, we strongly recommend migrating your test suite. Check out our comprehensive&nbsp;&nbsp;<a href="https://developer.android.com/develop/ui/compose/testing/migrate-v2">migration guide</a> for API mappings and common fixes.
</p>

<h2>Shared element improvements and animation tooling</h2>
<div class="separator" style="clear: both; text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi4CPWGQS1YJIuKDoVHrHVoXkXd1CeRWXew-VTXok2Mvh_Dh1k37F8j9GzSw204ICu2xwVs9CtlYlJyAD-iifjyYL07U0vax-5Y1TUw1oX2_BmEmh0prbjuBzznkJE8hcnkqbpjaBk7_jeolgsMyXNF2gKtzLRJBrxQ-B8yiUXCG3Ekmon0CBAERiVqSjE/s836/sharedElement.gif" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="400" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi4CPWGQS1YJIuKDoVHrHVoXkXd1CeRWXew-VTXok2Mvh_Dh1k37F8j9GzSw204ICu2xwVs9CtlYlJyAD-iifjyYL07U0vax-5Y1TUw1oX2_BmEmh0prbjuBzznkJE8hcnkqbpjaBk7_jeolgsMyXNF2gKtzLRJBrxQ-B8yiUXCG3Ekmon0CBAERiVqSjE/w180-h400/sharedElement.gif" width="180" /></a></div><div class="separator" style="clear: both; text-align: center;"><br /></div>
<p>
  We’ve also added some handy visual debugging tools for shared elements and <code>Modifier.animatedBounds</code>. You can now see exactly what’s happening under the hood—like target bounds, animation trajectories, and how many matches are found—making it much easier to spot why a transition might not be behaving as expected. To use the new tooling, simply surround your <code>SharedTransitionLayout</code> with the <code><a href="https://developer.android.com/reference/kotlin/androidx/compose/animation/package-summary#LookaheadAnimationVisualDebugging(kotlin.Boolean,androidx.compose.ui.graphics.Color,androidx.compose.ui.graphics.Color,androidx.compose.ui.graphics.Color,kotlin.Boolean,kotlin.Function0)">LookaheadAnimationVisualDebugging</a></code> composable. 
</p>

<pre><code>LookaheadAnimationVisualDebugging(
    overlayColor = Color(0x4AE91E63),
    isEnabled = true,
    multipleMatchesColor = Color.Green,
    isShowKeylabelEnabled = false,
    unmatchedElementColor = Color.Red,
) {
    SharedTransitionLayout {
        CompositionLocalProvider(
            LocalSharedTransitionScope provides this,
        ) {
            // your content
        }
    }
}<br /></code></pre><h2>Trackpad events</h2>
<p>
  We’ve revamped Compose support for trackpads, like built-in laptop trackpads, attachable trackpads for tablets, or external/virtual trackpads. Basic trackpad events will now generally be considered <code>PointerType.Mouse</code> events, aligning mouse and trackpad behavior to better match user expectations. Previously, these trackpad events were interpreted as fake touchscreen fingers of <code>PointerType.Touch</code>, which led to confusing user experiences. For example, clicking and dragging with a trackpad would scroll instead of selecting. By changing the pointer type these events have in the latest release of Compose, clicking and dragging with a trackpad will no longer scroll.
</p>

<p>
  We also added support for more complicated trackpad gestures as recognized by the platform since API 34, including <a href="https://developer.android.com/reference/android/view/MotionEvent#CLASSIFICATION_TWO_FINGER_SWIPE">two finger swipes</a> and <a href="https://developer.android.com/reference/android/view/MotionEvent#CLASSIFICATION_PINCH">pinches</a>. These gestures are automatically recognized by components like <code>Modifier.scrollable</code> and <code>Modifier.transformable</code> to have better behavior with trackpads.
</p>

<p>
  These changes improve behavior for trackpads across built-in components, with redundant touch slop removed, a more intuitive drag-and-drop starting gesture, double-click and triple-click selection in text fields, and desktop-styled context menus in text fields.
</p>

<p>
  To test trackpad behavior, there are new testing APIs with <code><a href="https://developer.android.com/reference/kotlin/androidx/compose/ui/test/SemanticsNodeInteraction?hl=en#(androidx.compose.ui.test.SemanticsNodeInteraction).performTrackpadInput(kotlin.Function1)">performTrackpadInput</a></code>, which allow validating the behavior of your apps when being used with a trackpad. If you have custom gesture detectors, validate behavior across input types, including touchscreens, mice, trackpads, and styluses, and ensure support for mouse scroll wheels and trackpad gestures.
</p>

<table style="border-collapse: collapse; width: 100%;">
 </table><table style="border-collapse: collapse; width: 100%;">
  <thead>
    <tr>
      <th style="text-align: center;">Before</th>
      <th style="text-align: center;">After</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align: center; width: 50%;">
        <div class="separator" style="clear: both;">
          <a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhPrtrimI6TGSfomNIoLe6bnkyrwEBYtIc1mehBgJZxnxGl3kxvlPpOZFMyyfbSThY7ECio5BNtswy2gsmXmi1EMdsqbGK9zDnUyK49PUv_Z1LKHyD6vWLIHxQSo75zEQ8m4tsPTyToitGSN3Ciuj2lTYfggHO9Z3CQhTk3ZjkrGLd9gn8JXkMzzwOeKIs/s1600/before%202.gif" style="display: block; padding: 1em 0px; text-align: center;">
            <img alt="Before" border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhPrtrimI6TGSfomNIoLe6bnkyrwEBYtIc1mehBgJZxnxGl3kxvlPpOZFMyyfbSThY7ECio5BNtswy2gsmXmi1EMdsqbGK9zDnUyK49PUv_Z1LKHyD6vWLIHxQSo75zEQ8m4tsPTyToitGSN3Ciuj2lTYfggHO9Z3CQhTk3ZjkrGLd9gn8JXkMzzwOeKIs/s16000/before%202.gif" style="height: auto; width: 100%;" />
          </a>
        </div>
      </td>
      <td style="text-align: center; width: 50%;">
        <div class="separator" style="clear: both;">
          <a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi24EUtKJ-bdapy5LjBehqxDwV1LS9giT6u4K279a5UVO-XkKAuEAbNpCQqbHHaIqn7JOC0fJZ3xNgAds2c0dBTqhbVKcafFhXh4QuMZNMpfqvDsH8s4IJJ4iNzXRGhnGwctzGczKCgf39X308h5WcP3g3dLrQUHlLrIsRgB_9RgAzUwXk8ZvXzUh46qto/s1600/after%203.gif" style="display: block; padding: 1em 0px; text-align: center;">
            <img alt="After" border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi24EUtKJ-bdapy5LjBehqxDwV1LS9giT6u4K279a5UVO-XkKAuEAbNpCQqbHHaIqn7JOC0fJZ3xNgAds2c0dBTqhbVKcafFhXh4QuMZNMpfqvDsH8s4IJJ4iNzXRGhnGwctzGczKCgf39X308h5WcP3g3dLrQUHlLrIsRgB_9RgAzUwXk8ZvXzUh46qto/s16000/after%203.gif" style="height: auto; width: 100%;" />
          </a>
        </div>
      </td>
    </tr>
  </tbody>
</table>

<h2>Composition host defaults (Compose runtime)</h2>
<p>
  We introduced <code><a href="https://developer.android.com/reference/kotlin/androidx/compose/runtime/HostDefaultProvider">HostDefaultProvider</a></code>, <code>LocalHostDefaultProvider</code>, <code>HostDefaultKey</code>, and <code>ViewTreeHostDefaultKey</code> to supply host-level services directly through compose-runtime. This removes the need for libraries to depend on compose-ui for lookups, better supporting Kotlin Multiplatform. To link these values to the composition tree, library authors can use <code>compositionLocalWithHostDefaultOf</code> to create a <code>CompositionLocal</code> that resolves defaults from the host.
</p>

<h2>Preview wrappers</h2>
<p>
  Android Studio custom previews is a new feature that allows you to define exactly how the contents of a Compose preview are displayed.
</p>

<p>
  By implementing the <code>PreviewWrapperProvider</code> interface and applying the new <code>@PreviewWrapper</code> annotation, you can easily inject custom logic, such as applying a specific Theme. The annotation can be applied to a function annotated with <code>@Composable</code> and <code>@Preview</code> or <code>@MultiPreview</code>, offering a generic, easy-to-use solution that works across preview features and significantly reduces repetitive code.
</p>

<pre><span id="docs-internal-guid-abe8e28a-7fff-d18a-2ace-96633e0a3887"><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>class ThemeWrapper: </span><span>PreviewWrapper</span><span> {</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;@Composable</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;override fun Wrap(content: </span><span>@Composable</span><span> (() -&gt; Unit)) {</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;JetsnackTheme {</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;content()</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;}</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>}</span></p><br /><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>@PreviewWrapperProvider</span><span>(ThemeWrapper::class)</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>@Preview</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>@Composable</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>private fun ButtonPreview() {</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;// JetsnackTheme in effect</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;Button(onClick = {}) {</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Text(text = "Demo")</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;}</span></p><p dir="ltr" style="line-height: 1.8; margin-bottom: 0pt; margin-top: 0pt;"><span>}</span></p></span></pre>

<h3>Deprecations and removals</h3>
<p></p><ul style="text-align: left;"><li>As announced in the <a href="https://android-developers.googleblog.com/2025/12/whats-new-in-jetpack-compose-december.html">Compose 1.10 blog post</a>, we’re deprecating <code>Modifier.onFirstVisible()</code>. Its name often led to misconceptions, particularly within lazy layouts, where it would trigger multiple times during scrolling. We recommend migrating to <code><a href="https://developer.android.com/reference/kotlin/androidx/compose/ui/layout/package-summary#(androidx.compose.ui.Modifier).onVisibilityChanged(kotlin.Long,kotlin.Float,androidx.compose.ui.layout.LayoutBoundsHolder,kotlin.Function1)">Modifier.onVisibilityChanged()</a></code>, which allows for more precise manual tracking of visibility states tailored to your specific use case requirements.
</li><li>The <code>ComposeFoundationFlags.isTextFieldDpadNavigationEnabled</code> flag was removed because D-pad navigation for <code>TextFields</code> is now always enabled by default. The new behavior ensures that the D-pad events from a gamepad or a TV remote first move the cursor in the given direction. The focus can move to another element only when the cursor reaches the end of the text.
</li></ul>
  <p></p>


<h3>Upcoming APIs</h3>
<p>
  In the upcoming Compose 1.12.0 release, the <code>compileSdk</code> will be upgraded to <code>compileSdk 37</code>, with AGP 9 and all apps and libraries that depend on Compose inheriting this requirement. We recommend keeping up to date with the latest released versions, as Compose aims to promptly adopt new <code>compileSdks</code> to provide access to the latest Android features. Be sure to check out the&nbsp;<a href="https://developer.android.com/build/releases/gradle-plugin#api-level-support">documentation here</a> for more information on which version of AGP is supported for different API levels. 
</p>

<p>
  In Compose 1.11.0, the following APIs are introduced as <code>@Experimental</code>, and we look forward to hearing your feedback as you explore them in your apps. Note that <code>@Experimental</code> APIs are provided for early evaluation and feedback and may undergo significant changes or removal in future releases.
</p>

<h2>Styles (Experimental)</h2>
<p>
  We are introducing a new experimental foundation API for <a href="https://developer.android.com/develop/ui/compose/styles">styling</a>. The Style API is a new paradigm for customizing visual elements of components, which has traditionally been performed with modifiers. It is designed to unlock deeper, easier customization by exposing a standard set of styleable properties with simple state-based styling and animated transitions.&nbsp;With this new API, we’re already seeing promising <a href="https://developer.android.com/develop/ui/compose/styles/performance">performance benefits</a>. We plan to adopt Styles in Material components once the Style API stabilizes.</p>

<p>
  A basic example of overriding a pressed state style background:
</p>

<pre><code>@Composable
fun LoginButton(modifier: Modifier = Modifier) {
    Button(
        onClick = {
            // Login logic
        },
        modifier = modifier,
        style = {
            background(
                Brush.linearGradient(
                    listOf(lightPurple, lightBlue)
                )
            )
            width(75.dp)
            height(50.dp)
            textAlign(TextAlign.Center)
            externalPadding(16.dp)

            pressed {
                background(
                    Brush.linearGradient(
                        listOf(Color.Magenta, Color.Red)
                    )
                )
            }
        }
    ){
        Text(
            text = "Login",
        )
    }
}</code></pre><br /><div><br /><div class="separator" style="clear: both; text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhzKgxY8FG0-Yf5HGCa-4OJeBgqmau8GIIODou5Wc4RFgIbI1nPHnO_wOp24UMUdyLoENyIe6iAby97tQLDRQhKVk5RYUVwBt-d5cuC1dcKYjJUVpYqBCKFugjCT4R-d2Hp_oohdUn1YLtJra-VXwQoU4UNgb5YenVsJ2O8H67NtLeZfMMpLLdp1VPJUhE/s900/styles.gif" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="278" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhzKgxY8FG0-Yf5HGCa-4OJeBgqmau8GIIODou5Wc4RFgIbI1nPHnO_wOp24UMUdyLoENyIe6iAby97tQLDRQhKVk5RYUVwBt-d5cuC1dcKYjJUVpYqBCKFugjCT4R-d2Hp_oohdUn1YLtJra-VXwQoU4UNgb5YenVsJ2O8H67NtLeZfMMpLLdp1VPJUhE/w400-h278/styles.gif" width="400" /></a></div><div class="separator" style="clear: both; text-align: center;"><br /></div><div class="separator" style="clear: both; text-align: left;">Check out the <a href="https://developer.android.com/develop/ui/compose/styles" target="_blank">documentation</a> and file any bugs <a href="https://www.google.com/url?q=https://issuetracker.google.com/issues/new?component%3D612128&amp;sa=D&amp;source=docs&amp;ust=1776894674938834&amp;usg=AOvVaw1Kl3kZ7NxHRGsmZUWh6iT7" target="_blank">here</a>.</div>

<h2>MediaQuery (Experimental)</h2>
<p>
  The new <code><a href="https://developer.android.com/develop/ui/compose/layouts/adaptive/mediaquery">mediaQuery</a></code> API provides a declarative and performant way to adapt your UI to its environment. It abstracts complex information retrieval into simple conditions within a <code><a href="https://developer.android.com/reference/kotlin/androidx/compose/ui/UiMediaScope">UiMediaScope</a></code>, ensuring recomposition only happens when needed.
</p>

<p>
  With support for a wide range of environmental signals—from device capabilities like keyboard types and pointer precision, to contextual states like window size and posture—you can build deeply responsive experiences. Performance is baked in with <code><a href="https://developer.android.com/reference/kotlin/androidx/compose/ui/package-summary#derivedMediaQuery(kotlin.Function1)">derivedMediaQuery</a></code> to handle high-frequency updates, while the ability to override scopes makes testing and previews seamless across hardware configurations.
</p>

<p>
  Previously, to get access to certain device properties — like if a device was in <a href="https://developer.android.com/develop/ui/compose/layouts/adaptive/foldables/make-your-app-fold-aware#features_of_foldable_displays">tabletop mode</a> — you’d need to write a lot of boilerplate to do so: 
</p>

<pre><code>@Composable
fun isTabletopPosture(
    context: Context = LocalContext.current
): Boolean {
    val windowLayoutInfo by
        WindowInfoTracker
            .getOrCreate(context)
            .windowLayoutInfo(context)
            .collectAsStateWithLifecycle(null)

    return windowLayoutInfo.displayFeatures.any { displayFeature -&gt;
        displayFeature is FoldingFeature &amp;&amp;
            displayFeature.state == FoldingFeature.State.HALF_OPENED &amp;&amp;
            displayFeature.orientation == FoldingFeature.Orientation.HORIZONTAL
    }
}

@Composable
fun VideoPlayer() {
    if(isTabletopPosture()) {
        TabletopLayout()
    } else {
        FlatLayout()
    }
}</code></pre>

<p>
  Now, with <code>UIMediaQuery</code>, you can add the <code>mediaQuery</code> syntax to query device properties, such as if a device is in tabletop mode:
</p>

<pre><code>@OptIn(ExperimentalMediaQueryApi::class)
@Composable
fun VideoPlayer() {
    if (mediaQuery { windowPosture == UiMediaScope.Posture.Tabletop }) {
        TabletopLayout()
    } else {
        FlatLayout()
    }
}</code></pre>

<p>
  Check out the <a href="https://developer.android.com/develop/ui/compose/layouts/adaptive/mediaquery">documentation</a> and file any bugs <a href="https://issuetracker.google.com/issues?q=componentid:1876021">here</a>.
</p>

<h2>Grid (Experimental)</h2>
<p>
  <code><a href="https://developer.android.com/develop/ui/compose/layouts/adaptive/grid">Grid</a></code> is a powerful new API for building complex, two-dimensional layouts in Jetpack Compose. While <code>Row</code> and <code>Column</code> are great for linear designs, <code>Grid</code> gives you the structural control needed for screen-level architecture and intricate components without the overhead of a scrollable list.
</p>

<p>
  <code>Grid</code> allows you to define your layout using tracks, gaps, and cells, offering familiar sizing options like <code>Dp</code>, percentages, intrinsic content sizes, and flexible "Fr" units. 
</p>

<pre><span id="docs-internal-guid-f771cc35-7fff-11ce-f06a-37fd1c308045"><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>@OptIn</span><span>(ExperimentalGridApi::</span><span>class</span><span>)</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>@Composable</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>fun </span><span>GridExample() {</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;Grid(</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;config = {</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;repeat(</span><span>4</span><span>) { column(</span><span>0</span><span>.</span><span>25f</span><span>) }</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;repeat(</span><span>2</span><span>) { row(</span><span>0</span><span>.</span><span>5f</span><span>) }</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;gap(</span><span>16</span><span>.dp)</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;) {</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Card1(modifier = Modifier.gridItem(rowSpan = </span><span>2</span><span>)</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Card2(modifier = Modifier.gridItem(colmnSpan = </span><span>3</span><span>)</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Card3(modifier = Modifier.gridItem(columnSpan = </span><span>2</span><span>)</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Card4()</span></p><p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span>&nbsp;&nbsp;&nbsp;&nbsp;}</span></p><p dir="ltr" style="line-height: 1.8; margin-bottom: 0pt; margin-top: 0pt;"><span>}</span></p><div><span><br /></span></div></span></pre>

<p>
  You can place items automatically or explicitly span them across multiple rows and columns for precision. Best of all, it’s highly adaptive—you can dynamically reconfigure your grid tracks and spans to respond to device states like tabletop mode or orientation changes, ensuring your UI looks great across form factors.
</p><div class="separator" style="clear: both; text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgTDUrQltkehSG0RuoiwDzVefCFsJBOn4I4zVYiee1NMYS5UeNdK9j4rP28myI7IwH8Me12xUDF_O5_MOH2dMWnysVD5dc6yx2Ag454bG1ShjuC_0UlX-bv15SJbW0bjSvrMHGbrit9qaNMa8PsDasFzKaoV1gdep3d7tgdaixqd7zvL-CrGbJ_lRIx7KI/s554/Grid.gif" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="398" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgTDUrQltkehSG0RuoiwDzVefCFsJBOn4I4zVYiee1NMYS5UeNdK9j4rP28myI7IwH8Me12xUDF_O5_MOH2dMWnysVD5dc6yx2Ag454bG1ShjuC_0UlX-bv15SJbW0bjSvrMHGbrit9qaNMa8PsDasFzKaoV1gdep3d7tgdaixqd7zvL-CrGbJ_lRIx7KI/w400-h398/Grid.gif" width="400" /></a></div><p><br /></p>

<p>
  Check out the <a href="https://developer.android.com/develop/ui/compose/layouts/adaptive/grid" target="_blank">documentation</a> and&nbsp;file any bugs <a href="https://issuetracker.google.com/issues/new?component=1876021&amp;template=1424126" target="_blank">here</a>.</p>

<h2>FlexBox (Experimental)</h2>
<p><a href="https://developer.android.com/reference/kotlin/androidx/compose/foundation/layout/package-summary#FlexBox(androidx.compose.ui.Modifier,androidx.compose.foundation.layout.FlexBoxConfig,kotlin.Function1)">FlexBox</a> is a layout container designed for high performance, adaptive UIs. It manages item sizing and space distribution based on available container dimensions. It handles complex tasks like wrapping (<code>wrap</code>) and multi-axis alignment of items (<code>justifyContent</code>, <code>alignItems</code>, <code>alignContent</code>). It allows items to grow (<code>grow</code>) or shrink (<code>shrink</code>) to fill the container.</p>

<pre><code>@OptIn(ExperimentalFlexBoxApi::class)
fun FlexBoxWrapping(){
    FlexBox(
        config = {
            wrap(FlexWrap.Wrap)
            gap(8.dp)
        }
    ) {
        RedRoundedBox()
        BlueRoundedBox()
        GreenRoundedBox(modifier = Modifier.width(350.dp).flex { grow(1.0f) })
        OrangeRoundedBox(modifier = Modifier.width(200.dp).flex { grow(0.7f) })
        PinkRoundedBox(modifier = Modifier.width(200.dp).flex { grow(0.3f) })
    }
}</code></pre>

<div class="separator" style="clear: both; text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgmcEvU3D7gpqW-gwblZmbXvzJo-cxVbSJJN0Q5UA4JACUThZ3x1xMUKKRqezPh4LSIWFcj1agYgdmYRwCovI9lCJ48sHZXNyY5bVi8Ow_WNc7718kc5njqAnSjLCDflE1gWcUiZ-lShOlRHDE3jXQygdCVKQqN2yaGIchpbVZaycj2Os-fVgsOzrrU230/s3092/AnimationGif.gif" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgmcEvU3D7gpqW-gwblZmbXvzJo-cxVbSJJN0Q5UA4JACUThZ3x1xMUKKRqezPh4LSIWFcj1agYgdmYRwCovI9lCJ48sHZXNyY5bVi8Ow_WNc7718kc5njqAnSjLCDflE1gWcUiZ-lShOlRHDE3jXQygdCVKQqN2yaGIchpbVZaycj2Os-fVgsOzrrU230/s16000/AnimationGif.gif" /></a></div><br /><h3><br /></h3><div><br /></div><h2><br /></h2><h2><br /></h2>Check out the&nbsp;<a href="https://developer.android.com/develop/ui/compose/layouts/adaptive/flexbox">documentation</a>&nbsp;and file any bugs&nbsp;<a href="https://b.corp.google.com/issues/new?component=1876021&amp;title=%5BFlexBox%5D&amp;pli=1&amp;template=0">here</a>.<h2>New SlotTable implementation (Experimental)</h2>
<p>
  We’ve introduced a new implementation of the <code>SlotTable</code>, which is disabled by default in this release. <code>SlotTable</code> is the internal data structure that the Compose runtime uses to track the state of your composition hierarchy, track invalidations/recompositions, store remembered values, and track all metadata of the composition at runtime. This new implementation is designed to improve performance, primarily around random edits.
</p>

<p>
  To try the new <code>SlotTable</code>, enable <code><a href="https://developer.android.com/reference/kotlin/androidx/compose/runtime/ComposeRuntimeFlags?hl=en#isLinkBufferComposerEnabled()">ComposeRuntimeFlags.isLinkBufferComposerEnabled</a></code>. 
</p>

<h3>Start coding today!</h3>
<p>
  With so many exciting new APIs in Jetpack Compose, and many more coming up, it's never been a better time to <a href="https://developer.android.com/develop/ui/compose/migrate/migrate-xml-views-to-jetpack-compose">migrate to Jetpack Compose</a>. As always, we value your feedback and feature requests (especially on <code>@Experimental</code> features that are still baking) — please file them <a href="https://issuetracker.google.com/issues/new?component=612128">here</a>. Happy composing!
</p></div>
