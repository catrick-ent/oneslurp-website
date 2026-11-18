# Android testing onboarding and website hosting

Verified November 18, 2026. This is an operator guide; it does not authorize invitations, messages, enrollment, releases, store changes, DNS changes, or production deployment.

## Website ownership and publishing

| Site | Source | Publishing |
| --- | --- | --- |
| one-slurp.com | catrick-ent/oneslurp-website | GitHub Pages, main branch, repository root |
| one-shake.com | catrick-ent/oneshake | GitHub Pages, main branch, repository root |
| OneStay marketing page | one-stay.html in oneslurp-website | https://one-slurp.com/one-stay.html, same main-branch Pages deployment |

The accessible catrick-ent repository inventory contained no separate OneStay website repository. one-stay.app failed DNS resolution in this environment; no registrar/DNS configuration was inspected or changed. Do not replace native referral domains with a static marketing URL without verifying the invite/review routes and association files.

Apple-link corrections are isolated in website draft PR #1: https://github.com/catrick-ent/oneslurp-website/pull/1 . It fixes exactly two OneSlurp hrefs and one OneStay href. Anchor counts, document structure/text, other attributes, Android links and unrelated content remain unchanged. Both Apple destinations resolve to the expected Greg Hutchins listings. No CI workflow exists in this static repository. Main-branch merge would publish; the draft is not a live-site fix.

## Verified Android status

The Catrick Enterprises Play Console dashboard showed all three apps in closed testing, inactive production, and disabled Apply for production buttons. A published closed-test release was marked complete. Last verified opted-in counts:

| App | Package | Opted in | Additional people needed to reach 12 |
| --- | --- | ---: | ---: |
| OneSlurp | com.oneslurp.app | 3 | 9 |
| OneShake | com.oneshake.app | 2 | 10 |
| OneStay | com.onestay.app | 0 | 12 |

Each app must have at least 12 testers opted in continuously for the preceding 14 days before applying for production access. Counts and elapsed eligibility must be rechecked at application time. Do not infer that the existing testers already satisfy the duration or that approval is automatic. The account separately requests a trader-status declaration by February 1, 2027; this is distinct from the displayed testing gate. OneSpoon appears as Draft; no readiness claim follows.

Public US package URLs for OneShake/OneSlurp returned 404. The homepage internal-test links and the download page's generic testing links do not establish which current closed track grants access. A later read-only console attempt authenticated successfully but rendered blank app pages, so the intended track opt-in URLs were not copied or changed. Do not synthesize a public release URL or promise unrestricted downloads.

## Operator onboarding steps

1. In the correct app, open **Test and release → Testing → Closed testing** and select the intended active track. Verify its release/build and supported countries/device requirements.
2. Read the **Testers** configuration. Record whether access uses an email list or Google Group. Copy that track's actual opt-in link and verify it with an already authorized tester. Do not substitute an internal-test link. This console inspection is the remaining prerequisite to verifying the acquisition destinations.
3. Obtain explicit permission before inviting anyone, editing a tester list/group, sending onboarding messages, or enrolling an account. Confirm the tester's Google account used in the Play Store; it need not be a Gmail address. Do not publish their address or list membership.
4. Once access is authorized and granted, the tester opens the verified opt-in URL with that same account, opts in themselves, then installs from the provided Play Store destination. The request form merely prepares an email draft; the tester must send it. Sending the request does not grant access or opt the tester in.
5. Have approved testers stay opted in throughout the required period and use the app meaningfully. Capture feedback through an approved channel. No invitation or feedback message is sent by this guide.
6. Recheck the per-app count/duration. Once eligible, the operator can prepare production-access answers about the app, testing and readiness. Submission, release rollout and listing edits require their own authorization. No public launch date is promised.

Source: Google's production testing requirements, https://support.google.com/googleplay/android-developer/answer/14151465?hl=en ; track/tester setup, https://support.google.com/googleplay/android-developer/answer/9845334?hl=en .

## Device and dev-notification prerequisites

Android Studio, a Pixel_9 AVD and API 36 ARM64 Google Play image are installed; the last ADB inventory showed no connected device/emulator. Xcode beta and iOS runtimes are installed, with no booted simulator in the last inventory. A dev notification test needs an attached supported test device/emulator, a matching native development build, and approved test-only accounts. Expo push support must be verified for the chosen runtime; an emulator alone does not establish delivery.

The native apps select the shared backend using `__DEV__`. An EAS `APP_ENV=preview` label is not proof of a development backend. Verify the runtime project URL/ref explicitly before any test-account write or notification test, and do not assume an installed closed-test store build uses dev.

OneSource code fixes are in draft PR #14, https://github.com/catrick-ent/one-source/pull/14 ; all eight checks passed on c56a1be. Dev read-only preflight is reproducible with `scripts/check-dev-notification-preflight.py` in that branch. Dev has zero push-token rows; the user/app uniqueness migration is pending, the old functions remain deployed, WEBHOOK_SECRET is absent, and notifications webhook/pg_cron setup is absent. Explicit setup approval, a securely provisioned dev secret, reviewed gateway authentication, migration/deployment validation and a dedicated test device are still needed before delivery. No secret was created, no schema changed, and no notification sent in this investigation.
