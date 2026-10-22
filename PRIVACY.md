# Cadence — Privacy Policy

_Last updated: 22 October 2026_

Cadence is a Chrome extension that queues prompts into Google Flow, saves each result with an
ordered file name, and assembles timestamped images and a voice over into a video in its
Studio. You sign in with Google to use it; the one record that keeps is described below.

This policy describes everything the extension stores and everything it causes to leave your
computer. It is written against what the code actually does.

## What stays on your device

- **Your settings** — generation, pacing, saving, language and theme choices. Stored with
  Chrome's local extension storage. Not synced.
- **Your prompts and story plan** — the text you paste into the Queue, so it is still there
  next time you open the panel.
- **Your cast images** — the character images you add on the Cast tab and their tags. The
  images are kept in the extension's own browser database (IndexedDB); the tags in local
  storage.
- **A record of the last run** — which prompts were sent, which images are ready, failed or
  saved, and an activity log, so the panel can show progress after it is reopened.
- **Which cast images were already uploaded to each Flow project**, keyed by the project's id,
  so the same image isn't uploaded twice.
- **Studio preferences and edits** — the look settings, export quality, and per-image changes
  you make (motion, transition, start time), keyed by the project title.

**Voice over transcription** happens on your computer too. The recording you add in the story
plan is decoded and transcribed inside the extension by a speech model (Whisper) running on your
own graphics card or processor; the audio is never uploaded. The first time you transcribe,
Cadence downloads the model's weight files (about 200 MB) from Hugging Face (huggingface.co) and
your browser keeps them for next time. That download is an ordinary file request: it tells
Hugging Face your IP address and that the model was fetched, and sends nothing of yours. The
transcript is saved in local extension storage with your story plan, and beside your images as
transcript.srt when a run saves them.

Files you open in the Studio (images, audio, plan, transcript) are read inside that browser tab
only. They are never uploaded anywhere, and the videos the Studio exports are rendered on your
computer by Chrome's own encoder.

None of this is readable by us. All of it is removed when you uninstall the extension.

## Google sign-in

When you **Sign in with Google**, Google confirms who you are to Cadence's account service,
which is hosted on Supabase. Cadence then keeps one record about you in that database:

- your Google account's email address, name and profile picture link
- your plan (free or pro) and, for a paid plan, when it ends
- if you subscribe to Cadence Pro, the subscription's status (on trial, active, cancelled…) and
  the customer and subscription ids Lemon Squeezy gives it
- when you first signed in and when you last opened Cadence while signed in

Your sign-in session (access and refresh tokens issued by that service) is kept in Chrome's
local extension storage so you stay signed in. Cadence never sees your Google password.

Nothing else goes to the account service: your prompts, cast images, story plans, Studio files,
exported videos and run history stay on your device as described above. Sign out from the
account menu in the panel at any time.

## Cadence Pro payments

Cadence Pro (the Story plan and the Studio) is a paid subscription sold through Lemon Squeezy
(lemonsqueezy.com), which acts as the merchant of record: it takes the payment, handles sales
tax, and runs the free trial. When you press the upgrade button, Cadence opens Lemon Squeezy's
checkout page with your Cadence account id and your email address filled in, so the
subscription can be matched to your account.

You enter your card or PayPal details on Lemon Squeezy's page, not in Cadence; Cadence never
sees them. Lemon Squeezy handles them under its own privacy policy
(lemonsqueezy.com/privacy). Whenever your subscription changes (trial started, renewed,
cancelled, expired), Lemon Squeezy tells Cadence's account service, which updates the plan
fields listed above. You can manage or cancel the subscription from the account menu, which
opens Lemon Squeezy's customer portal.

## What happens in Google Flow

Cadence works inside the Google Flow tab you have open (flow.google.com or labs.google), in
your own Google account, the same way you would by hand:

- It **types your prompts** into Flow's prompt box and presses Generate.
- It **changes Flow's generation settings** (image or video, model, aspect ratio, duration,
  number of results) when you ask it to.
- It **uploads your cast images** into your Flow project as references, and attaches them to
  the prompts that mention them, only when you use the Cast feature.
- It **reads the Flow page** to see which results have finished or failed, and their
  download links.

What you send to Flow this way is handled by Google under Google's own terms and privacy
policy, exactly as if you had typed or uploaded it yourself. Cadence sends it nowhere else.

To press Flow's Generate button, which does not respond to simulated clicks, Cadence uses
Chrome's debugger interface to send one real mouse click to that button. It attaches to the
Flow tab only for that click and detaches immediately; Chrome shows a "Cadence started
debugging this browser" notice while it does. It is not used to read pages, network traffic
or any other tab.

## Downloads

Finished images and videos are saved to your Downloads folder through Chrome's downloader,
from Google's servers, with your existing Google session — the same request Flow makes when you
press its own download button. When Cadence asks Flow for an upscaled version, Flow starts the
download and Cadence gives the file its ordered name. Cadence only renames downloads that come
from Flow while it is waiting for one; your other downloads are left untouched.

During a run Cadence may also zoom the Flow tab out (so Flow keeps every result loaded), keep
your computer from sleeping, and stop Chrome from unloading the tab. All three are undone when
the run ends.

## What is never collected

Apart from the account record above, nothing is sent to us. There
are no analytics, no usage statistics, no crash reporting, no advertising, and no third-party
libraries that phone home. No passwords, and no card or payment details. No location. No browsing history. The extension
does not read any website other than Google Flow, and it contains no remotely loaded code.

Nothing is sold or rented. The only data shared with anyone is your account id and email,
passed to Lemon Squeezy when you choose to upgrade, as described above. Nothing is used for any
purpose other than running your Flow batches, building your videos, and your Pro subscription.

## Retention

Everything Cadence keeps locally stays on your device until you clear it (the Queue, Cast and Activity
tabs each have a clear or remove control) or uninstall the extension. Files it downloads are
yours and stay in your Downloads folder. The sign-in record is kept while you use Cadence with
an account; email nwodochristian@gmail.com to have it deleted. Lemon Squeezy keeps its own
records of any purchase for as long as the law requires it to.

## Changes

If the extension's data handling changes, this policy changes with it before the new version
ships.

## Contact

Questions about this policy: nwodochristian@gmail.com
