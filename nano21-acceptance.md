# An image API acceptance test should check pixels, not only task success

Disclosure: I maintain FreyaVideo. This note was prepared with AI assistance and reviewed against our integration records. It is an acceptance-test worksheet, not an independent model review or a quality ranking.

A provider can return success while the file still needs inspection. We recently integrated Nano Banana 2.1 and separated three checks: request acceptance, decoded output properties, and whether the image is useful for the intended layout.

## What our three acceptance calls established

| Requested | Decoded output | What it establishes |
| --- | --- | --- |
| 2K, two JPEG outputs, 16:9 | Two 2752 × 1536 JPEG images | Count and format were accepted; ratio was approximately 1.79:1 |
| 4K, one WebP, 1:4 | 2048 × 8256 WebP | Tall format accepted; inspect dimensions before placing it |
| 1K, one PNG, 8:1, fourteen distinct references | 2928 × 352 PNG | Request accepted; actual ratio was approximately 8.32:1 |

Three calls do not establish typical latency, reference fidelity, comparative quality, or every parameter combination. The third request accepting fourteen references does not prove that every reference influenced the result.

## Decode downloaded files before reviewing the layout

```js
import sharp from "sharp";
import { readFile } from "node:fs/promises";

const image = await readFile("output.png");
const { width, height, format } = await sharp(image).metadata();
if (!width || !height) throw new Error("Missing dimensions");
const requestedRatio = 8;
const actualRatio = width / height;
console.log({ width, height, format, actualRatio,
  ratioDeviationPercent: 100 * Math.abs(actualRatio / requestedRatio - 1) });
```

Record a request ID before polling. Avoid blindly retrying an uncertain generation POST: success may have happened even when the response was lost. Count decoded files separately from tasks. If a design needs an exact ratio, explicitly review and crop the output; do not silently remove important content.

## Keep three prices separate

Record the credits shown to the user, the credits actually reserved/refunded, and the provider invoice as separate fields. Our generation key could not read Fal's usage endpoint (403), so these tests do not claim verified supplier charges or profit. An advertised API price is not an invoice.

A reusable worksheet row is:

```text
request_id, model, resolution, requested_count, actual_count,
requested_ratio, width, height, format,
shown_credits, charged_credits, refunded_credits,
provider_invoice_cost, reviewed_layout, notes
```

Leave invoice and quality fields unknown until verified. A technical success is not the same as a usable image.

For the model-selection context, we keep a [Nano Banana 2.1 versus Pro guide](https://freyavideo.com/blog/nano-banana-2-1-vs-pro?utm_source=github&utm_medium=referral&utm_campaign=nano21_acceptance_20261009). The [Nano Banana 2.1 generator](https://freyavideo.com/image-models/nano-banana-2-1?utm_source=github&utm_medium=referral&utm_campaign=nano21_acceptance_20261009) exposes the corresponding controls; its quoted credits should be checked before submission. These are our own product links.
