<p align="center"><img src="assets/nudge-girl-mascot.svg" width="220" alt="Nudge Girl mascot"></p>

# Nudge Girl

An edge-AI bin monitor that catches food waste and recyclables at the moment they are dropped into a general-waste bin, and rings a bell.

Submission for the **ASUS UGen AI League 2026** hackathon — Battlefield Lightning (ASUS UGen300 / Hailo-10H), Workplace AI theme, Global Online Track.

**Team Judge Boys:** Ting-Jun, Lin & Chia-Ti, Ling

## How it works

1. **See** — a camera looks only at the bin opening (cropped ROI, no faces, nothing recorded).
2. **Recognize** — YOLOv8 (COCO-pretrained, Hailo Model Zoo) detects the item on the UGen300.
3. **Decide** — COCO classes are mapped to waste categories; the same object won't be classified twice.
4. **Nudge** — bell chime and Nudge Girl's stern face on a small screen.

| Category   | COCO classes | Action |
|------------|--------------|--------|
| Food waste | banana, apple, orange, sandwich, pizza, donut, cake, hot dog, broccoli, carrot | Bell |
| Recyclable | bottle, cup, paper lunch box | Bell |
| Other      | anything else | Silent |

## Architecture

- **Hardware:** USB camera → host (Mini PC on Ubuntu) + ASUS UGen300 → Chime, LEDs, small screen
- **Software:** Python · HailoRT (YOLOv8n for inference) · event logic 

## Status

Stage I: proposal and concept renders. Stage II (if selected): port to the UGen300 and run a two-week pilot in our department lounge.

## References

- Lin et al., "Microsoft COCO: Common Objects in Context," ECCV 2014
- Ultralytics YOLOv8 documentation, docs.ultralytics.com
- Hailo Model Zoo, github.com/hailo-ai/hailo_model_zoo (for HAILO10H)
- Taiwan Ministry of Environment, 應回收項目 (Recyclable Items), recycle.moenv.gov.tw/Understanding/RecyclableItems
- Asus UGen300 USB AI Accelerator asus.com/tw/motherboards-components/ai-accelerator/ugen/ugen300-usb-8g

