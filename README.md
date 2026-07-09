# Science Assistant KUSRC 🎓🤖

ระบบผู้ช่วยอัจฉริยะสำหรับนิสิตคณะวิทยาศาสตร์ พัฒนาขึ้นเพื่อช่วยตอบคำถามเกี่ยวกับข้อมูลคณะ หลักสูตร และเอกสารต่างๆ โดยเน้นความแม่นยำด้วยการใช้ **RAG (Retrieval-Augmented Generation)** ผ่าน Google Gemini API

## 🚀 Key Features

* **Intelligent AI Chatbot**: ใช้โมเดล `gemini-flash-latest` ในการประมวลผล พร้อมระบบสลับ API Key อัตโนมัติ (Failover) เพื่อความเสถียรของระบบ
* **Knowledge Retrieval System**: 
    * ระบบดึงข้อมูลจากเว็บไซต์คณะโดยอัตโนมัติ (Auto-Scraper) และจัดเก็บในฐานข้อมูล
    * รองรับการอ่านเนื้อหาจากไฟล์ PDF เพื่อใช้เป็นฐานความรู้ (Knowledge Base) สำหรับตอบคำถาม
* **Automated Pipeline**: มีการตั้งเวลา (Scheduler) ทำงานทุกเที่ยงคืน เพื่ออัปเดตข้อมูลให้เป็นปัจจุบันเสมอ
* **Authentication**: รองรับการยืนยันตัวตนด้วย **LINE Login**
* **Management & Analytics**: 
    * ระบบหลังบ้านสำหรับ Admin เพื่อดูสถิติการใช้งาน และหัวข้อคำถามยอดนิยม (Top Questions)
    * ระบบบันทึก Feedback (Like/Dislike) เพื่อนำไปพัฒนาประสิทธิภาพ AI ต่อไป

## 🛠️ Technical Stack

* **Language**: Python
* **Framework**: Flask
* **Database**: SQLAlchemy (สนับสนุน SQLite พร้อมการจัดการระดับ Production ด้วย WAL mode)
* **AI Engine**: Google Gemini API
* **Deployment**: รองรับการตั้งค่าผ่าน Environment Variables

## 📂 Project Structure 

ไฟล์ `app.py` เป็นหัวใจหลักของระบบ โดยทำหน้าที่จัดการ:
* การเชื่อมต่อฐานข้อมูลและการทำ Migration
* การควบคุม Logic ของ Scraper และ Scheduler
* การประมวลผลข้อความจากผู้ใช้และสร้างบริบท (Context) ส่งให้ AI
* การจัดการเส้นทาง (Routes) ทั้งฝั่งผู้ใช้งานทั่วไปและ Admin Panel

