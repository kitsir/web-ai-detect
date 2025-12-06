https://web-aidetect.web.app/
ลิงค์เว็บไซต์ รอ 1 นาทีเมื่อไม่ได้เรียกใช้นาน


I Image Detector Web Application
โปรเจกต์นี้เป็นเว็บแอปพลิเคชันสำหรับตรวจสอบและจำแนกรูปภาพว่าเป็นภาพถ่ายจริง (Real) หรือภาพที่สร้างขึ้นโดยปัญญาประดิษฐ์ (AI Generated) โดยทำงานผ่านโมเดล Deep Learning ที่เชื่อมต่อระหว่างส่วนประมวลผล (Backend) และส่วนแสดงผล (Frontend)

สิ่งที่ต้องติดตั้งล่วงหน้า (Prerequisites)
ก่อนเริ่มต้นใช้งาน กรุณาตรวจสอบว่าเครื่องคอมพิวเตอร์ของคุณได้ติดตั้งโปรแกรมพื้นฐานดังต่อไปนี้แล้ว:

Python (เวอร์ชัน 3.9 หรือใหม่กว่า)

Node.js (เวอร์ชัน 16 หรือใหม่กว่า)

ขั้นตอนการติดตั้งและรันโปรแกรม
ระบบแบ่งออกเป็น 2 ส่วน คือ Backend และ Frontend ซึ่งต้องรันควบคู่กัน กรุณาทำตามขั้นตอนทีละส่วนดังนี้

ส่วนที่ 1: การรัน Backend (Server)
เปิด Terminal หรือ Command Prompt

พิมพ์คำสั่งเพื่อเข้าไปยังโฟลเดอร์ backend cd backend

(แนะนำ) สร้าง Virtual Environment เพื่อแยกไลบรารีของโปรเจกต์ python -m venv venv

เรียกใช้งาน Virtual Environment

สำหรับ Windows: venv\Scripts\activate

สำหรับ macOS หรือ Linux: source venv/bin/activate

ติดตั้งไลบรารีที่จำเป็นทั้งหมดจากไฟล์ requirements.txt pip install -r requirements.txt

หมายเหตุ: หากยังไม่มีไฟล์ requirements.txt สามารถติดตั้งด้วยคำสั่งตรงๆ ดังนี้: pip install fastapi uvicorn python-multipart tensorflow numpy pillow

ตรวจสอบว่าไฟล์โมเดลชื่อ fine_tuned_ai_model.h5 อยู่ในโฟลเดอร์ backend เรียบร้อยแล้ว

เริ่มต้นการทำงานของ Server uvicorn main:app --reload --host 0.0.0.0 --port 8000

เมื่อรันสำเร็จ จะปรากฏข้อความระบุว่า Application startup complete

ส่วนที่ 2: การรัน Frontend (User Interface)
เปิด Terminal หน้าต่างใหม่ (ห้ามปิดหน้าต่าง Backend ที่กำลังรันอยู่)

พิมพ์คำสั่งเพื่อเข้าไปยังโฟลเดอร์ frontend cd frontend

ติดตั้ง Dependencies ที่จำเป็นสำหรับ React npm install

เริ่มต้นการทำงานของหน้าเว็บ npm run dev

ระบบจะแสดง URL สำหรับเข้าใช้งาน (ปกติจะเป็น http://localhost:5173) ให้เปิด URL ดังกล่าวในเว็บเบราว์เซอร์

คู่มือการใช้งานเว็บไซต์
เมื่อเข้าสู่หน้าเว็บไซต์แล้ว สามารถใช้งานได้ตามขั้นตอนดังนี้:

เลือกรูปภาพ คลิกที่ปุ่ม Choose File หรือบริเวณกรอบตรงกลางเพื่อเลือกไฟล์รูปภาพที่ต้องการตรวจสอบ (รองรับไฟล์นามสกุล .jpg, .png, .webp)

เริ่มการตรวจสอบ เมื่อรูปภาพตัวอย่างปรากฏขึ้น ให้คลิกที่ปุ่ม Analyze Image ระบบจะทำการส่งรูปภาพไปประมวลผลที่ Backend

อ่านผลลัพธ์ ผลการวิเคราะห์จะแสดงที่กล่องด้านขวา ประกอบด้วย:

Label: ระบุว่าเป็น Real (ภาพจริง) หรือ Fake (ภาพจาก AI)

Confidence: แถบแสดงค่าความมั่นใจเป็นเปอร์เซ็นต์

ล้างค่า หากต้องการตรวจสอบรูปภาพใหม่ ให้คลิกปุ่ม Reset เพื่อเคลียร์ข้อมูลเดิม

การแก้ไขปัญหาเบื้องต้น
กรณีสั่ง npm install แล้ว Error: ให้ลองลบโฟลเดอร์ node_modules และไฟล์ package-lock.json ในโฟลเดอร์ frontend ทิ้ง แล้วรันคำสั่ง npm install ใหม่อีกครั้ง

กรณีหน้าเว็บขึ้น Error ว่า Failed to fetch: ตรวจสอบว่า Backend Server ใน Terminal หน้าต่างแรกกำลังทำงานอยู่หรือไม่ และทำงานอยู่ที่ Port 8000 หรือไม่

กรณีหาไฟล์โมเดลไม่เจอ: ตรวจสอบให้แน่ใจว่าไฟล์ fine_tuned_ai_model.h5 วางอยู่ในระดับเดียวกับไฟล์ main.py ในโฟลเดอร์ backend
