# Image-to-video creative workflow resources

Practical checklists for preparing AI images, testing edits, and comparing video generations. Maintained by the FreyaVideo team; the linked guides and tools are our own resources. This is a documentation repository, not a model implementation or an independent benchmark.

## 1. Prepare and edit the source image

Write down the subject, framing, lighting and elements that must remain unchanged before editing. Change one property at a time and compare each output against the last acceptable version.

- [GPT Image 2.5 generation and editing workspace](https://freyavideo.com/image-models/gpt-image-2-5) — start from a prompt or a reference image and inspect the available generation settings.
- [GPT Image 2.5: noise and editing guide](https://freyavideo.com/blog/gpt-image-2-5-noise-editing) — use a repeatable edit protocol and inspect unwanted changes before moving to animation.

### Source-image acceptance checklist

- Is the subject still recognizable after the edit?
- Are edges, textures and small lettering acceptable at the intended display size?
- Did the requested change affect unrelated objects or composition?
- Is the framing suitable for the intended video aspect ratio?
- Save the original, prompt and last acceptable output before trying another edit.

## 2. Plan the video generation

Describe one main action, camera movement and intended duration. Start with a short test, inspect the result, then refine the prompt. These resources cover different parts of that workflow:

- [H3 Max tutorial](https://freyavideo.com/blog/h3-max-tutorial) — a practical starting point for planning prompts and generating a clip.
- [H3 Max video generation workspace](https://freyavideo.com/video-models/minimax-h3-max) — the model page for putting the workflow into practice.

## 3. Compare outputs fairly

A useful comparison records the same input, prompt, aspect ratio, duration and quality settings. Record queue time separately from processing time when available. A single fast generation does not establish a universal speed ranking.

- [H3 Max versus Kling](https://freyavideo.com/blog/h3-max-vs-kling) — comparison context for choosing which workflow to evaluate.
- [AI video generation speed guide](https://freyavideo.com/blog/fastest-ai-video-generator) — considerations when evaluating turnaround time alongside output quality.

Use [comparison-template.csv](comparison-template.csv) to record your own observations. The template contains no measured results and makes no claims about a winning model.

## 中文资源

同一套流程也提供中文页面：先检查图片与编辑结果，再测试视频生成，最后在一致条件下记录速度和画面质量。

| 环节 | 资料 |
| --- | --- |
| 图片生成与编辑 | [GPT Image 2.5 工具页](https://freyavideo.com/zh/image-models/gpt-image-2-5) |
| 图片质量检查 | [GPT Image 2.5 噪点与编辑指南](https://freyavideo.com/zh/blog/gpt-image-2-5-noise-editing) |
| 视频操作教程 | [H3 Max 使用教程](https://freyavideo.com/zh/blog/h3-max-tutorial) |
| 视频生成 | [H3 Max 模型页](https://freyavideo.com/zh/video-models/minimax-h3-max) |
| 模型比较 | [H3 Max 与 Kling 对比](https://freyavideo.com/zh/blog/h3-max-vs-kling) |
| 速度评估 | [AI 视频生成速度指南](https://freyavideo.com/zh/blog/fastest-ai-video-generator) |

## Notes

Model availability, prices and settings can change; check the linked workspace before generating. Use images you have permission to upload. No sample outputs or performance figures are claimed in this repository.
