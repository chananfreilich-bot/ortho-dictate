# Ortho Dictate: setup

## 1. Microphone (Boya mini 2)
1. Plug in the Boya receiver.
2. Windows: Settings → System → Sound → Input → choose the Boya. On a Mac: System Settings → Sound → Input.
3. In Chrome, go to `chrome://settings/content/microphone` and pick the Boya at the top.
4. Turn the Boya's noise cancellation on and clip it about a hand's width below your chin.

## 2a. Option A: Inside Smilecloud (inserts the note directly)
1. In Chrome, install **Tampermonkey** from the Chrome Web Store.
2. Go to `chrome://extensions`. Turn on **Developer mode** (top right). Open Tampermonkey → **Details** and turn on **Allow User Scripts**.
3. Drag `ortho-dictate-smilecloud.user.js` into a Chrome window, then click **Install**.
4. Open Smilecloud and refresh the page. The 🦷 Ortho Dictate panel appears in the bottom right. You can drag it by the header and hide it with Alt+O.
   *If it doesn't appear:* your Smilecloud address may not contain "smilecloud". Open Tampermonkey → Dashboard → Ortho Dictate → Edit. Add this line under the other `@include` lines, put your address in it, then save:
   `// @match https://YOUR-SMILECLOUD-ADDRESS/*`
5. To use it, open the patient's note and **click inside the note box**. Pick the appointment type, click 🎙 (or press Alt+D) and dictate. Then click **Insert into Smilecloud** (or say "insert note"). The note is also copied to the clipboard each time, so if a box won't accept the insert, press Ctrl+V.

## 2b. Option B: Separate window (copy and paste)
Open `OrthoDictate.html` in Chrome or Edge. Dictate, then click **Copy note** and paste it into Smilecloud. Or click **Save .txt** to save the note as a file.

## How to dictate
- **Just talk through the note in order. You don't need to pause:** "Chief complaint crowding, last dental visit six months ago, dentist Dr. Cohen, TMJ no clicking or popping…" Each field name moves the text to that field. You can say fields in **any order**. The note is always printed in the template's order. A field name used as part of a sentence stays put ("correct the posterior crossbite", "big overjet").
- **Missing and impacted teeth:** "no missing teeth, no impacted teeth" → Missing Teeth: None, Impacted Teeth: None. "Missing upper right two" → Missing Teeth: UR2. The same works for "no crossbite", "no broken brackets" and "no elastics".
- **Findings go to their field automatically, even without the field name:** "permanent dentition" → Dentition, "narrow maxilla" → Transverse, "normal divergent" → Normodivergent, "Class I, Class I" or "Class I angle and canine" → Angle and Canine, "OH good" → OH, "both midlines are on" → both midlines, "mild maxillary spacing" → Maxillary, "I did not take a ceph" → Skeletal Class: No ceph. On the treatment line, the treatment type stays in Tx, the rest goes to TxP, and "about 36 months" goes to Time.
- **If text lands in the wrong field,** say "scratch that" or click the field and fix it.
- **Commands:** "next", "previous", "scratch that", "clear field", "new line", "period", "comma", "copy note", "insert note", "stop listening".
- **Teeth:** "upper right two" → UR2. "lower left primary second molar" → LLE. "upper six to six" → U6-6. "upper and lower seven to seven" → U and L 7-7.
- **Wires:** "sixteen by twenty-two NiTi" → .016x.022 NiTi. "oh one four nitinol" → .014 NiTi. "heat activated NiTi eighteen" → .018 HA NiTi.
- **Elastics:** "class two, quarter inch, three and a half ounce" → Class II, 1/4", 3.5 oz.
- **Units:** "3 millimeters" → 3mm. "40 percent" → 40%. "6 weeks" → 6 wks. "half cusp" → 1/2 cusp. "phase one" → Ph I.
- You can type in any field to fix something before inserting.

## Have it on every computer automatically
1. Sign in to Chrome with your Google account and turn on sync.
2. In Tampermonkey: open the **Dashboard**, go to **Settings**, and set **Config mode** to *Advanced*. Under **Script Sync**, choose **Browser Sync** (or Google Drive), tick **Enable Script Sync**, then click **Save**.
3. On another computer: sign in to Chrome with the same account. Tampermonkey installs itself, and Ortho Dictate follows within a few minutes. Turn on **Allow User Scripts** once on that computer (step 3 above).
Your ⚙ settings and custom words stay on the computer where you set them. Send any words you add to Claude so they can be built into the script.

## Headings
- Notes use full-word headings (Chief Complaint, Overbite, Upper Midline, Oral Hygiene, Treatment Plan, Next Visit…). To switch back to the short ones (CC, OB, U Midline, OH, TxP, NV, E, U, L), use ⚙.
- You can say either form: "overbite" or "OB", "overjet" or "OJ", "crossbite" or "CXB/XB", "upper midline" or "U ML", "lower midline" or "L ML", "curve of spee" or "COS", "oral hygiene" or "OH", "chief complaint" or "CC", "last dental visit" or "LDV", "treatment plan" or "TxP", "next visit" or "NV".

## AI tidy-up (free)
- **✨ Tidy up (on this computer):** only shows on computers that can run Chrome's built-in AI. The note never leaves the computer. The first use downloads Chrome's AI model once. It's a small AI, so always read the result.
- **🤖 Copy for AI → 📥 Paste AI result:** click Copy for AI and paste into Claude.ai (or another AI chat). Copy its answer, then click Paste AI result → Apply to note. Keep patient names out of it.
- **↶ Undo** brings back the note from before the tidy-up.

## Settings (⚙)
- **Custom words:** if a word keeps coming out wrong, add a line like `nighty => NiTi`. You can also add your own shorthand, like `power chain => PC`.
- **On-device recognition:** keeps the audio on your computer. It needs a recent Chrome and works best with English (US). Chrome downloads the speech model once.
- **Recognize field names without pausing:** on by default. Turn it off if you'd rather pause before each field name.
- **Templates (advanced):** change field labels or spoken names, or add new appointment types.

## Privacy
Unless on-device recognition is on, Chrome sends the audio to Google's speech service to transcribe it. Edge sends it to Microsoft's. Avoid saying patient names or ID numbers out loud; the note goes into the patient's own chart anyway. Draft notes are never saved. Only your settings are stored, in this browser.
