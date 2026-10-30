# Cadence — Privacy Policy

_Last updated: 30 October 2026_

Cadence is a Chrome extension that queues prompts into Google Flow, saves each result with an
ordered file name, and turns your voice over and those images into a video in its Studio. You sign in with Google to use it; the one record that keeps is described below.

This policy describes everything the extension stores and everything it causes to leave your
computer. It is written against what the code actually does.

## What stays on your device

- **Your settings** — generation, pacing, saving, language and theme choices. Stored with
  Chrome's local extension storage. Not synced.
- **Your prompts and Audio to video plan** — the text you paste into the Queue (prompts, your
  production script and the plan), so it is still there next time you open the panel.
- **Your voice over recording** — the audio file you add in Audio to video, kept in the
  extension's own browser database (IndexedDB) so it can be transcribed and loaded into the
  Studio, until you replace it.
- **Your character images** — the character images or character sheets you add on the
  Character tab and their tags. The images are kept in the extension's browser database; the
  tags in local storage.
- **A record of the last run** — which prompts were sent, which images are ready, failed or
  saved, and an activity log, so the panel can show progress after it is reopened.
- **Which character images were already uploaded to each Flow project**, keyed by the
  project's id, so the same image isn't uploaded twice.
- **Which prompt made each saved file** — the file's path in your Downloads folder and a short
  fingerprint (hash) of its prompt, so a file already saved from the same prompt isn't made
  again.
- **Studio preferences and edits** — the look, voice over volume, subtitle style, export
  quality, and per-image changes you make (motion, transition, start time), keyed by the
  project title.
- **Your videos in progress** — each Flow project's plan, transcript and settings, listed in the
  video picker so you can switch between them.
- **A subtitle font**, if you upload one in the Studio, kept in the extension's browser
  database so it is there next time.
- **Folders you let the Studio use** — when you choose a folder to export into, or the folder
  your runs are saved in, Chrome gives the Studio access to that folder, and Cadence keeps that
  permission in its browser database so you don't have to choose it every time. Chrome may ask
  you to confirm it again after a restart.

**Voice over transcription** happens on your computer too. The recording you add in Audio to
video is decoded and transcribed inside the extension by a speech model (Whisper) running on your
own graphics card or processor; the audio is never uploaded. The first time you transcribe,
Cadence downloads the model's weight files (about 200 MB) from Hugging Face (huggingface.co) and
your browser keeps them for next time. That download is an ordinary file request: it tells
Hugging Face your IP address and that the model was fetched, and sends nothing of yours. The
transcript is saved in local extension storage with your plan, and beside your images as
transcript.srt when a run saves them.

## Writing the plan with Gemini (optional)

Audio to video can have Google's Gemini write the production script and image plan for you, on
your own Gemini API key from Google AI Studio. This is off until you add a key, and the
copy-and-paste prompt keeps working without one.

- **Your key** is kept in Chrome's local extension storage on this computer. It is sent only to
  Google, with each Gemini request, and never to us. Remove it from the Gemini key section at
  any time.
- **When you press "Write the plan with Gemini"**, Cadence sends the plan prompt straight from
  your browser to Google's Gemini API (generativelanguage.googleapis.com). The prompt holds
  your voice over's transcript, your production script if you gave one, and your plan settings
  (art style, timing, title). The reply is shown in the plan box and saved locally like a
  pasted plan. Nothing passes through any server of ours.
- Google handles these requests under its own Gemini API terms and privacy policy. On Gemini's
  free tier, Google may use what is sent to improve its products; on a paid key it does not.
  If you'd rather not send the transcript to Google, copy the prompt into an AI chat of your
  choice instead.
- Chrome asks your permission for Cadence to reach generativelanguage.googleapis.com the first
  time you save a key, and the permission is given back when you remove it.

Files you open in the Studio (images, audio, plan, transcript), and the files in a run folder
you let it open, are read inside that browser tab only. They are never uploaded anywhere, and
the videos and subtitle files the Studio exports are rendered on your computer by Chrome's own
encoder and saved to Downloads or the folder you chose.

None of this is readable by us. All of it is removed when you uninstall the extension.

## Google sign-in

When you **Sign in with Google**, Google confirms who you are to Cadence's account service,
which is hosted on Supabase. Cadence then keeps one record about you in that database:

- your Google account's email address, name and profile picture link
- your approximate country (a two-letter code such as NG or US), worked out on your computer from
  its time-zone setting each time Cadence opens; no IP address is collected or stored
- your plan (free or pro) and, for a paid plan, when it ends
- if you subscribe to Cadence Pro, the subscription's status (on trial, active, cancelled…) and
  the customer and subscription ids Lemon Squeezy gives it
- when you first signed in and when you last opened Cadence while signed in

Your sign-in session (access and refresh tokens issued by that service) is kept in Chrome's
local extension storage so you stay signed in. Cadence never sees your Google password.

Nothing else goes to the account service (your Gemini key and plan requests go only to Google,
as described above): your prompts, character images, voice over, plans,
Studio files, exported videos and run history stay on your device as described above. Sign out from the
account menu in the panel at any time.

## Cadence Pro payments

Cadence Pro (Audio to video and the Studio) is a paid subscription sold through Lemon Squeezy
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
- It **uploads your character images** into your Flow project as references, and attaches
  them to the prompts that mention them, only when you use character references.
- It **reads the Flow page** to see which results have finished or failed, and their
  download links.
- When your Audio to video plan has **video clips**, it switches Flow to Video → Frames once the
  images are saved, puts each clip beat's own image in Flow's Start frame, and sends that beat's
  motion prompt. Before that it **reads your Flow credit balance** from Flow's account panel and
  the cost Flow shows for a clip, so it makes only the clips your credits cover. The balance is
  only shown in the panel's activity log; it is not stored or sent anywhere.
- When you ask the Studio to **generate missing images**, it sends those images' prompts to
  your Flow tab the same way, and if no Flow project is open it opens Flow and starts a new
  project in your account for them.

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

To avoid making or saving the same file twice, Cadence looks up its own files in Chrome's list
of downloads: the files in the run's folder, by name, and whether each finished download is
still on disk. It doesn't read the contents of those files or look at any other download. When
you press **Show in folder** after a Studio export, Chrome opens that file's folder.

During a run Cadence keeps your computer from sleeping and stops Chrome from unloading the Flow
tab. If you turn on "Zoom Flow out during runs" (off by default), or the Flow window is too
narrow for Flow's full layout, it also zooms that one tab out so Flow keeps every result loaded.
All of these are undone when the run ends.

## Reports that help keep Cadence working

**When Google Flow changes.** Cadence relies on parts of Flow's page (the prompt box, the
Generate button, the settings button, the add-image button, and Flow's menus). If it can't find
one of them, or a run keeps failing at the same step, the panel shows a warning and, while you
are signed in, sends Cadence's account service a short report: which part was missing, a
one-line description of the failure, and the Cadence version. At most one report per problem a
day. It holds no account id, no prompts, images, file names or Flow project addresses.

**Usage counts, only if you say yes.** After you sign in, Cadence asks once whether you'd like to
share anonymous counts of the steps you reach: installed, signed in, first run, images saved,
Studio opened, video or Shorts exported, checkout opened, Gemini key added, clip saved. Each step
is noted on your computer and, only if you choose "Share counts" (or switch it on in Output),
sent once, as just the step's name, the Cadence version and your approximate country (from the
time-zone setting, as above). No account id, install id, prompts,
media or anything else. Switch it off at any time in Output; nothing further is sent.

## What is never collected

Apart from the account record and the reports above, nothing is sent to us. There
are no analytics, no usage statistics, no crash reporting, no advertising, and no third-party
libraries that phone home. No passwords, and no card or payment details. No location beyond the country above (no IP address, GPS or city). No browsing history. The extension
does not read any website other than Google Flow, and it contains no remotely loaded code.
Gemini's reply is text that Cadence reads as a plan; it is never run as code.

Nothing is sold or rented. The only data shared with anyone is your account id and email,
passed to Lemon Squeezy when you choose to upgrade, and, if you use Gemini, the plan prompt
sent to Google on your own key, as described above. Nothing is used for any
purpose other than running your Flow batches, building your videos, and your Pro subscription.

## Retention

Everything Cadence keeps locally stays on your device until you clear it (the Queue, Character and Activity
tabs each have a clear or remove control) or uninstall the extension. Files it downloads are
yours and stay in your Downloads folder. The sign-in record is kept while you use Cadence with
an account; email nwodochristian@gmail.com to have it deleted. Lemon Squeezy keeps its own
records of any purchase for as long as the law requires it to.

## Changes

If the extension's data handling changes, this policy changes with it before the new version
ships.

## Contact

Questions about this policy: nwodochristian@gmail.com
