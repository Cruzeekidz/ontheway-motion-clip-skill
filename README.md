# OntheWay Motion Clip Skill

แพ็ก skill สำหรับทีมงาน ดาวน์โหลดได้โดยไม่ต้องมีบัญชี GitHub

## ดาวน์โหลด OntheWay Motion Clip

แพ็กวันที่ **3 ตุลาคม 2026** จาก skill ที่ติดตั้งในเครื่องต้นทาง รวม templates, SFX, scripts, references และ Gemini TTS ที่ bundle มา

[เปิดไฟล์ ZIP เพื่อดาวน์โหลด](./ontheway-claude-motion-clip-team-2026-10-03.zip)

1. เปิดไฟล์ ZIP ตามลิงก์ด้านบน แล้วกด **Download raw file** (ไอคอนดาวน์โหลด)
2. แตก ZIP จะได้ `INSTALL-TH.txt` และโฟลเดอร์ `ontheway-claude-motion-clip`

## ติดตั้งครั้งแรก

คัดลอกโฟลเดอร์ `ontheway-claude-motion-clip` ทั้งโฟลเดอร์ไปที่:

| แอป | ตำแหน่ง |
| --- | --- |
| Codex (ตามเอกสารปัจจุบัน) | `~/.agents/skills/ontheway-claude-motion-clip/` |
| Claude Code | `~/.claude/skills/ontheway-claude-motion-clip/` |

`~` หมายถึงโฟลเดอร์ผู้ใช้ บน Windows เช่น `C:\Users\ชื่อผู้ใช้` ตรวจให้ `SKILL.md` อยู่ในโฟลเดอร์ skill โดยตรง ไม่ซ้อนโฟลเดอร์อีกชั้น แล้วเปิดแอปใหม่หรือเริ่มแชตใหม่

[เอกสาร OpenAI เรื่องตำแหน่ง skills](https://learn.chatgpt.com/docs/customization/overview#skills)

เครื่องปลายทางต้องมี **Node.js >=22, FFmpeg/ffprobe, Python 3 และ Pillow** บน Windows ใช้ Bash ผ่าน WSL หรือ Git Bash สำหรับ `setup.sh`

ตั้ง **Gemini API key ของตัวเอง** ตาม `references/onboarding.md` ใน skill และเก็บที่ `~/.claude/secrets/gemini.env` ห้ามใส่ key ลง repository นี้

เวอร์ชันนี้ไม่บังคับ API key ให้ขึ้นต้นด้วย `AIza` หรือ prefix ใด ๆ ตรวจด้วยการเรียก TTS จริง

จากโฟลเดอร์ skill รัน:

```bash
bash scripts/setup.sh
```

หรือบอก AI ว่า:

```text
ใช้ ontheway-claude-motion-clip ช่วยตรวจ setup เครื่องนี้และแนะนำการติดตั้ง dependency ที่ขาดก่อนเริ่มทำวิดีโอ
```

ขั้นตอน setup เรียก HyperFrames ผ่าน npx และทดสอบ Gemini TTS ผ่านเครือข่าย อาจใช้โควตา API ของเจ้าของ key

## เรียกใช้ทุกครั้งที่ทำคลิป

ใน Codex พิมพ์ชื่อ skill พร้อม `$` หรือระบุชื่อในคำสั่ง เช่น:

```text
$ontheway-claude-motion-clip
สร้างวิดีโอโฆษณา Cruzee แนวตั้ง 1080×1920 ความยาวประมาณ 30 วินาที
สินค้า: จักรยานขาไถ Cruzee
กลุ่มเป้าหมาย: ผู้ปกครองเด็กเล็ก
โทน: สนุก อบอุ่น
เสียงพากย์: ผู้หญิง
ใช้รูปสินค้าจากโฟลเดอร์ source_material ของโปรเจกต์นี้
ก่อนเริ่ม ขอให้ถามข้อมูลที่ขาดและเสนอคอนเซปต์ให้เลือก
```

ทีมงานควรระบุแบรนด์ สินค้าและจุดเด่น กลุ่มเป้าหมาย โทนการสื่อสาร และเพศเสียงพากย์ พร้อมให้ไฟล์รูป/วิดีโอที่ต้องใช้

skill จะตรวจ setup → เก็บข้อมูล → เสนอคอนเซปต์ → ให้อนุมัติ storyboard → สร้างและตรวจวิดีโอ → ให้เลือกเสียง/BGM/SFX → ผสมเสียงและส่งงาน

สำหรับ Cruzee ให้ใช้ข้อมูลสินค้าและภาพจริงที่ผ่านการอนุมัติ หากต้องการกฎแบรนด์อัตโนมัติ ต้องติดตั้ง skill แบรนด์แยกต่างหาก เพราะไม่ได้รวมในแพ็กนี้

## ขอบเขตและการอัปเดต

- แพ็กนี้เป็นสำเนา ณ วันที่ระบุ ไม่อัปเดตตามเครื่องต้นทางอัตโนมัติ
- ไม่มี API key หรือ secrets ของเครื่องต้นทาง
- ไม่รวมโปรแกรมระบบหรือ skill อื่นทั้งหมดที่เอกสารอ้างถึง ดู `references/dependencies.md` สำหรับ HyperFrames family และ helper สำหรับ copywriting
- ตรวจ ZIP แล้วว่าแตกไฟล์ได้ แต่ยังไม่ได้ทดสอบครบทุกขั้นบนเครื่องทีมงาน
- เมื่อมีเวอร์ชันใหม่ ให้ดาวน์โหลดแพ็กใหม่ สำรอง skill เก่า แล้วแทนที่โฟลเดอร์ skill; key ที่เก็บนอกโฟลเดอร์ skill ใช้ต่อได้
