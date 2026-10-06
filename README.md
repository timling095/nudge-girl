<p align="center"><img src="assets/nudge-girl-mascot.svg" width="220" alt="Nudge Girl mascot"></p>

# Nudge Girl

An edge-AI bin monitor that catches food waste and recyclables at the moment they are dropped into a general-waste bin, and rings a bell.

Submission for the **ASUS UGen AI League 2026** hackathon — Battlefield Lightning (ASUS UGen300 / Hailo-10H), Workplace AI theme, Global Online Track.

**Team Selfie Freak:** 林廷峻、凌嘉悌

## How it works

1. **See** — a camera looks only at the bin opening (cropped ROI, no faces, nothing recorded).
2. **Recognise** — YOLOv8 (COCO-pretrained, Hailo Model Zoo) detects the item on the UGen300.
3. **Decide** — COCO classes are mapped to waste categories; a detection must persist for N frames, then a cooldown.
4. **Nudge** — bell chime, an LED pointing to the correct bin, and Nudge Girl's stern face on a small screen.

| Category   | COCO classes | Action |
|------------|--------------|--------|
| Food waste | banana, apple, orange, sandwich, pizza, donut, cake, hot dog, broccoli, carrot | Bell |
| Recyclable | bottle, cup | Bell |
| Other      | anything else | Silent |

## Architecture

- **Hardware:** USB camera → host (Raspberry Pi 5 or mini PC) + ASUS UGen300 → speaker, LEDs, small screen
- **Software:** Python · OpenCV (capture, ROI, motion gate) · HailoRT (inference) · event logic · SQLite (anonymous counts)

## Status

Stage I: proposal and concept renders. Stage II (if selected): port to the UGen300 and run a two-week pilot in our department lounge.

## References

- Lin et al., "Microsoft COCO: Common Objects in Context," ECCV 2014
- Proença and Simões, "TACO: Trash Annotations in Context," arXiv:2003.06975, 2020
- Ultralytics YOLOv8 — https://docs.ultralytics.com
- Hailo Model Zoo — https://github.com/hailo-ai/hailo_model_zoo
- Taiwan Ministry of Environment, 應回收項目 — https://recycle.moenv.gov.tw/Understanding/RecyclableItems
