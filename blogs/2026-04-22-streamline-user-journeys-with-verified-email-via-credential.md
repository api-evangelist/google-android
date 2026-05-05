---
title: "Streamline User Journeys with Verified Email via Credential Manager"
url: "https://android-developers.googleblog.com/2026/04/streamline-auth-credential-manager-verified-email.html"
date: "2026-04-22T13:00:00.000-07:00"
author: "Android Developers (noreply@blogger.com)"
feed_url: "https://android-developers.googleblog.com/feeds/posts/default"
---
<img src="https://blogger.googleusercontent.com/img/a/AVvXsEgseJ0HOa6wGI4egBEWBTC4Pawhiiv3BQIDm5R3XjY2D0uBRcZJaNTWcsHkMXY8VnbtA98-sojfdwKttHh6x82yQSg1sCsAWSKb8QXgVo5bQk4wtoi2LoM5u-TXYeIDD-fbqkA3SJssiUWgFTWsf44BAjzk06Iov-uDeIXJm6elMrcsNQoEU2KbVYN6SQo" style="display: none;" /><div class="entry-content"><i>Posted by Niharika Arora, Senior Developer Relations Engineer and Jean-Pierre Pralle, Product Manager, Credential Manager</i></div><div class="entry-content"><p></p><div class="separator" style="clear: both; text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgrkwBoNh5swqed4VY1XpXFkClSeuytxVntwZHc1t33e6_N49ra3ja_C4d9m_kE9GUuA2AvXz7696z08MAop8fcK1Ac69MB9QnQcBc4Qy-VYPwjjksvUEVzvSwvFRPocxWEVUv71EodUFWOMgBDiTI7TDTys7kqKMVHCpi4R-yDpzGkJVJpPx5Im1r2Yqk/s8419/Streamline-user-animation-V02%20Blog.png" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em; text-align: left;"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgrkwBoNh5swqed4VY1XpXFkClSeuytxVntwZHc1t33e6_N49ra3ja_C4d9m_kE9GUuA2AvXz7696z08MAop8fcK1Ac69MB9QnQcBc4Qy-VYPwjjksvUEVzvSwvFRPocxWEVUv71EodUFWOMgBDiTI7TDTys7kqKMVHCpi4R-yDpzGkJVJpPx5Im1r2Yqk/s16000/Streamline-user-animation-V02%20Blog.png" /></a></div><br /><span style="text-align: center;"><br /></span><p></p><p>In the modern digital landscape, the first encounter a user has with an app is often the most critical. Yet, for decades, this initial interaction has been hindered by the friction of traditional verification methods. Today, we're excited to announce a <a href="https://developer.android.com/identity/digital-credentials/email-verification">new verified email credential issued by Google</a>, which developers can now retrieve directly from Android’s Credential Manager Digital Credential API.</p>

  <h2>The Problem: Authentication Friction in the Modern Era</h2>
  <p>The "current era" of authentication is defined by a trade-off between security and convenience. To ensure that a user owns the email address they provide, you typically rely on One-Time Passwords (OTPs) or "magic links" sent by email or SMS.</p>
  
  <p>While effective, these traditional steps introduce significant hurdles:</p>
  <ul>
    <li><strong>Context switching:</strong> Users must leave the app, open their inbox or messaging app, find the code, and return, a process where many potential users simply drop off.</li>
    <li><strong>Delivery issues:</strong> While Emails are free, they can be delayed or diverted to spam folders.</li>
    <li><strong>Onboarding friction:</strong> Every extra second spent in the "verification loop" is a second where a user might lose interest, directly impacting conversion rates.</li>
  </ul>

  <h2>The Solution: Seamless, Verified Email</h2>
  <p>Google now issues a cryptographically verified email credential directly to Android devices. This verified email credential is delivered through the <a href="https://developer.android.com/identity/credential-manager">Credential Manager API</a>, which is Android's implementation of the<a href="https://www.w3.org/TR/digital-credentials/"> W3C's Digital Credential API</a> standard.</p>
  
  <p>For users, this completely removes the need to manually verify their email through external channels. For developers, the API securely delivers these verified user claims for any scenario whether you are building an account creation flow, a recovery process, or a high-risk step-up authentication.</p>
  
  <p>While this specific verified email address is sourced securely from the user's Google Account on their device, the underlying Digital Credentials API is issuer-agnostic. This fosters an open ecosystem, allowing any holder of a digital credential with an email claim to offer that verification to your app.</p>

  <h2>User Experience</h2>
  <p>The beauty of this API lies in its simplicity for the end user. Instead of hunting for OTP codes, the experience is integrated directly into the Android OS:</p>
  <ul>
    <li><strong>Initiation:</strong> The process begins when a user focuses on an email input field or taps a "Sign up" or "Recover account" button. You can also initiate the process on page load.</li>
    <li><strong>Transparency:</strong> A native Android bottom sheet appears, clearly detailing exactly what data is being requested (for example, user’s verified email address).</li>
    <li><strong>One-tap consent:</strong> The user simply taps "Agree and continue" to share the data.</li>
    <li><strong>Immediate progress:</strong> Once consent is given, the app receives the data instantly. For sign-up or account recovery flows, you can then seamlessly transition the user into passkey creation, ensuring:
      <ul>
        <li>Users do not have to enter any user information manually, as compared to the traditional username/password registration.</li>
        <li>Their next login is even faster and more secure.</li>
      </ul>
    </li>
  </ul>

  <h2>Use case 1. Sign up</h2>
  <p>Accelerate onboarding by fetching a verified email the moment the user taps "Sign up". We strongly recommend you pair the verified email retrieval with passkey creation, also part of the Credential Manager API:</p><div class="separator" style="clear: both; text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhB0XD7gJHIVNibV1Ha-Nc9gt6ZtetHbj3Q-kEdl4T2LdraGEjhjuw2_vIu4oJypeeFIVt17ilknHKW6YtLtqVgGG3bu1STEB57NVaquTUzMitGQ6_Kx0rQFTqVCm9Xh16dpx9dnohMoEay851uoBmmyzbE-8FI6BRpKbr7eLz1f4I-vmV_fjXYIp3FDtc/s11200/%E2%80%A2%20(7).png" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhB0XD7gJHIVNibV1Ha-Nc9gt6ZtetHbj3Q-kEdl4T2LdraGEjhjuw2_vIu4oJypeeFIVt17ilknHKW6YtLtqVgGG3bu1STEB57NVaquTUzMitGQ6_Kx0rQFTqVCm9Xh16dpx9dnohMoEay851uoBmmyzbE-8FI6BRpKbr7eLz1f4I-vmV_fjXYIp3FDtc/s16000/%E2%80%A2%20(7).png" /></a></div><br /><p><br /></p>
  <p><em>Note: You can also fetch other unverified fields such as a user’s given name, family name, name, profile picture and the hosted domain connected with the verified email.</em></p>

  <h2>Use case 2. Account recovery</h2>
  <p>Eliminate the frustration of users hunting for recovery codes in their spam folders by allowing them to recover their account using the verified email securely stored on their device.</p><div class="separator" style="clear: both; text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhxvTQN0G2H_TJQ8T4lIMNEdmTbeLZ3NocqBv8ilMHZhPz-2W4lyjSYnByGJgf2H6gVBfUqhz7A8BELqWS1eo6xUnp44lzeHD1nG3n0iqrrnpfV7iyUyIIZv7Arfk8MGYr5frMdsA1cyDsR0Bx7zVpcXQD2-g3pTf1HuPj-GimaUXlb47gKT_995Hv5yEw/s11200/%E2%80%A2%20(8).png" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhxvTQN0G2H_TJQ8T4lIMNEdmTbeLZ3NocqBv8ilMHZhPz-2W4lyjSYnByGJgf2H6gVBfUqhz7A8BELqWS1eo6xUnp44lzeHD1nG3n0iqrrnpfV7iyUyIIZv7Arfk8MGYr5frMdsA1cyDsR0Bx7zVpcXQD2-g3pTf1HuPj-GimaUXlb47gKT_995Hv5yEw/s16000/%E2%80%A2%20(8).png" /></a></div><br /><p><br /></p>

  <h2>Use case 3. Re-authentication for sensitive actions</h2>
  <p>Protect sensitive user actions, such as changing settings or updating profile details, by requiring a quick re-authentication step. Instead of an OTP, you can provide a low-friction verification using the device's verified email.</p><div class="separator" style="clear: both; text-align: center;"><a href="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhdxwdKc_D_ZADn0IGuUsPHJNmyXxQPgevHU9JgbjVJDF7B6smZCiCUcEJlUfKxejRvCs0gTDLv3XkxLZ7Zu_gPcQ4oY5oxmTCNvLTB9ECY7SPFQ0W5PwREzvEvZUfiq7uFcrR3Ts8bEmn2xa97yzRPam1Ei1J0CyWDZ43e8pWT8nr6FArwu5jlN8jxdVM/s8408/%E2%80%A2%20(9).png" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;"><img border="0" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhdxwdKc_D_ZADn0IGuUsPHJNmyXxQPgevHU9JgbjVJDF7B6smZCiCUcEJlUfKxejRvCs0gTDLv3XkxLZ7Zu_gPcQ4oY5oxmTCNvLTB9ECY7SPFQ0W5PwREzvEvZUfiq7uFcrR3Ts8bEmn2xa97yzRPam1Ei1J0CyWDZ43e8pWT8nr6FArwu5jlN8jxdVM/s16000/%E2%80%A2%20(9).png" /></a></div><br /><p><br /></p>

  <h2>Important Considerations</h2>
  <p>As you design your authentication architecture around the Digital Credentials API, keep the following details in mind:</p>
  <ul>
    <li><strong>Account support:</strong> For the specific email credential issued by Google, only regular consumer Google Accounts are supported (Workspace and supervised accounts are currently not supported). Keep in mind that the Credential Manager API itself is issuer-agnostic, meaning other identity providers can issue credentials with their own account support policies.</li>
    <li><strong>Other user data:</strong> Beyond email, you can request the user's given name, family name, full name, and profile picture. However, note that only the email is verified by Google.</li>
    <li><strong>Auto verify your @gmail accounts:</strong> The API provides verified emails for all consumer Google Accounts. We recommend auto-verifying @gmail.com users and routing custom domains to your existing verification flow - for example, an OTP flow. This ensures you maintain long-term access for external domains not directly managed by Google.</li>
    <li><strong>Complementary to Sign in with Google:</strong> While both the new verified email credential &amp; Sign in with Google API provides a verified email, the choice depends on the intended user experience:
      <ul>
        <li>Use Sign in with Google when your users want to create a federated login session.</li>
        <li>Use Verified Email when your users want to sign in traditionally with a username/password or passkey but want to auto-verify the email address without the manual chore of an OTP.</li>
      </ul>
    </li>
  </ul>

  <h2>Conclusion and Next steps</h2>
  <p>By integrating <a href="https://developer.android.com/identity/digital-credentials/email-verification">the new verified email via Credential Manager API</a>, you can drastically reduce onboarding friction and provide users with a more streamlined, secure authentication journey. This represents a shift toward a future where "verification" is no longer a manual chore for the user, but a seamless, integrated part of the native mobile experience.</p>
  
  <p>Ready to see how this fits into your own app? To get started, update your project to the latest Credential Manager API and explore our <a href="https://developer.android.com/identity/digital-credentials/email-verification">Integration Guide</a>. We encourage you to explore how this streamlined verification can simplify your critical user journeys from optimizing account creation, to enhancing re-authentication flows.</p>
</div>
