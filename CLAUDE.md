# Project Rules — biz-roi-laundromat

ไฟล์ `.xlsx` สร้างจาก `build_roi_template.py` (openpyxl) — **แก้ที่สคริปต์แล้ว
re-generate เสมอ ห้ามแก้ในไฟล์ Excel ตรงๆ** ไม่งั้นครั้งหน้าที่รันสคริปต์จะทับหาย
ราคาแพ็กเกจ PM ในชีต `F_SERVICE` มาจาก repo `biz-pm-pricing-tool` แก้ที่นั่นแล้วต้องตามมาปรับที่นี่

---

## โครงสร้าง repo ของ zitemzon

**กฎ: หนึ่งโปรเจกต์ = หนึ่ง repo เสมอ** ห้ามเอาโปรเจกต์ใหม่ไปฝากเป็น branch ใน repo
ที่ไม่เกี่ยวข้องกัน ตั้งชื่อด้วย prefix ตามหมวด แล้วเสริมด้วย GitHub Topics
(GitHub ไม่มีโฟลเดอร์สำหรับ repo — prefix ทำให้หน้า repo list เรียงเป็นกลุ่มให้เอง)

| prefix | หมวด |
|---|---|
| `tsp-tool-*` | เครื่องมือภายใน / automation |
| `tsp-iot-*` | ฮาร์ดแวร์ / เฟิร์มแวร์ |
| `tsp-web-*` | หน้าเว็บ / แคมเปญ |
| `tsp-ops-*` | SOP / กฎระเบียบพนักงาน / การเงิน |
| `biz-*` | ธุรกิจอื่นนอก Toy Station Plus+ |
| `audio-*` | งานเครื่องเสียง / ลำโพง |

repo ที่มีอยู่ ณ 19 ก.ย. 2026

| repo | หมวด | เนื้อหา |
|---|---|---|
| `tsp-wheel` | เว็บ/แคมเปญ | กิจกรรมหมุนวงล้อหน้าร้าน (ใช้งานจริงอยู่) |
| `tsp-tool-readaloud` | เครื่องมือ | อ่านสรุปประชุมไทย/อังกฤษเป็นเสียงไทย |
| `tsp-iot-revenue-monitor` | ฮาร์ดแวร์ | จอมอนิเตอร์ยอดขาย ESP32-S3 + TFT |
| `tsp-iot-mycw-clock` | ฮาร์ดแวร์ | MyCW Rainbow Clock v2 (ESP8266) |
| `biz-roi-laundromat` | ธุรกิจอื่น | เทมเพลต ROI ร้านสะดวกซัก Samsung Commercial |
| `biz-pm-pricing-tool` | ธุรกิจอื่น | เครื่องมือตั้งราคางาน PM (ป้อนราคาให้ชีต F_SERVICE ของ biz-roi-laundromat) |

### ⛔ ห้ามเปลี่ยนชื่อ repo `tsp-wheel`

URL `https://zitemzon.github.io/tsp-wheel/1.html` ฝังอยู่ใน `og:url` ของทุกหน้า
และอยู่ใน QR code ที่ปริ้นติดหน้าร้านแล้ว GitHub Pages ไม่การันตี redirect
หลังเปลี่ยนชื่อ repo — เปลี่ยนเมื่อไหร่ลูกค้ายิง QR แล้วเจอ 404

### ข้อควรระวังเรื่องสิทธิ์ GitHub

ถ้าเปลี่ยนการตั้งค่า repo access ของ Claude GitHub App **ระหว่างที่ session กำลังทำงานอยู่**
token ของ session นั้นจะค้างค่าเดิม push ไม่ผ่าน (403) จนกว่าจะเปิด session ใหม่
ปัจจุบันตั้งเป็น *All repositories* แล้วจึงไม่ควรเจออีก
