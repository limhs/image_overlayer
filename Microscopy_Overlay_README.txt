MICROSCOPY STUDIO — CHANNEL OVERLAY, VERSION 3

Open Microscopy_Overlay.html in Chrome or Safari. No installation, server, or internet connection is needed. All image processing stays in the browser.

QUICK START
1. Add BF and at least one color channel: Blue, Green, or Red.
2. Select background, then drag a rectangle over an empty BF region without cells or bright spots. The same coordinates are measured independently in every supplied color channel.
3. Generate preview.
4. Choose All channels, BF + one color, BF only, or an individual color only. Individual views use exactly the same corrected channel values as the overlays.
5. Save PNG or TIFF to download the selected view at original resolution. Save settings records the region, thresholds, display ranges, hidden channels, gains, filenames, and selected view. The selection outline is never included in downloads.

INPUTS
Single-image, unsigned 8-bit TIFF; PNG; JPG. Grayscale inputs are recommended. Color inputs are converted to Rec.709 luminance. All channels must have identical dimensions and represent the same field of view. No spatial registration is performed. Limits: 100 MB and 16 megapixels per image. 16-bit TIFF and multi-page TIFF/Z-stack inputs must first be exported as individual 8-bit channel images using the desired display range.

BACKGROUND-REFERENCED COLOR PROCESSING
For each color separately:
- Measure the median, maximum, and robust noise estimate (1.4826 × median absolute deviation) within your selected background rectangle.
- Subtract the larger of the region maximum and median + 6 × estimated noise. Clip negatives to zero. This makes every pixel in the selected background region black in the isolated color view.
- Find 8-connected regions above max(minimum contrast, 3 × estimated noise). Default minimum contrast: 12/255.
- A qualifying spot must have at least 16 connected pixels and a peak at least 64/255 above the background cutoff by default.
- Auto-scale only channels with qualifying spots. Use max(64, 99.5th percentile of qualifying spot peaks) as the upper display limit. This prevents scaling arbitrarily tiny residuals to full brightness.
- With Hide channels below spot criteria enabled (default), a channel without qualifying spots is displayed as black. Otherwise residuals remain at the native 0–255 display scale and are not automatically boosted.
- Blue, Green and Red brightness gains can each be adjusted. Fine-tune settings contains the shared spot criteria. Changes to criteria require Generate preview again.
- BF brightness is unchanged. Colored signals use screen blending over BF. Isolated colors have black backgrounds.

INTERPRETATION
These are conservative display rules, not a test of biological fluorescence presence or absence. Genuine weak signals may fall below the defaults; adjust the criteria if appropriate and record settings. A contaminated background selection can remove true signal; choose an empty representative region. Uneven background elsewhere in the image can remain after a constant background cutoff. Auto-scaled display intensities cannot be compared directly between images. Use matched acquisition and analysis settings for quantitative comparisons.

The synthetic demo includes signal in Blue and Green and no qualifying Red signal, to illustrate suppression of a noise-only channel. It is not experimental data.

LICENSES
MIT is the name of an open-source software license, not a statement of the user's university affiliation.
- UTIF.js 3.1.0: MIT.
- pako 1.0.11: MIT AND zlib (including its zlib port).
Third-party licenses permit use and modification, including commercial use, subject to their notice and attribution conditions. Preserve the bundled notices when redistributing the app; do not misrepresent authorship, and mark modifications to the zlib sources if you modify those sources. The licenses include warranty disclaimers.
The full notices are embedded in the HTML under About third-party licenses and included as THIRD_PARTY_NOTICES.txt. They apply to those libraries, not your input images or exported figures. No separate open-source license has been selected for the app-specific code.

VALIDATION
Processing checks cover zeroing the selected background, rejection of noise-only and isolated hot-pixel channels, retention of qualifying spots, isolated RGB views, combinations, unchanged BF, and exact TIFF output roundtrip.
Using an example background region (x=10, y=10, width=80, height=50), the two original only samples' Green channels are suppressed by the default criteria, while their Blue channels are retained. Results depend on the actual selected region.
Browser layout and native file-chooser interactions could not be tested in this environment due browser URL restrictions. A simulated DOM test checks application controls and processing flows; this does not replace visual browser testing.

This is a standalone local web app. Hosted publication is not available in the current workspace.
