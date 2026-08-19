# พักใจ (PAKJAI)

MVP เว็บอ่านคอนเทนต์แนว Solarpunk / Nature / Calm สร้างด้วย React + Vite และ Express + Supabase PostgreSQL/Auth
## ติดตั้งและรัน
```powershell
cd frontend
npm install
Copy-Item .env.example .env
npm run dev
```

เปิดอีก terminal:

```powershell
cd backend
npm install
Copy-Item .env.example .env
npm run dev
```

## Environment Variables
Frontend: `VITE_SUPABASE_URL`, `VITE_SUPABASE_ANON_KEY`, `VITE_API_URL` (ห้ามใส่ service role key)
Backend: `PORT`, `SUPABASE_URL`, `SUPABASE_SERVICE_ROLE_KEY` (เก็บเฉพาะฝั่ง server)

## ตั้งค่า Supabase
1. สร้าง Project ที่ Supabase และนำ URL/keys ไปใส่ใน `.env` ของแต่ละฝั่ง
2. เปิด Authentication > Providers > Google แล้วตั้งค่า Client ID/Secret และ callback URL ตาม Supabase dashboard
3. เปิด SQL Editor แล้วรัน `supabase/schema.sql` เพื่อสร้างตาราง, foreign keys, unique constraint, trigger และ RLS
4. เพิ่มบทความผ่าน Table Editor ใน `articles` (หรือสร้าง admin API ต่อในภายหลัง)

## ฟีเจอร์ MVP
หน้า Home, Feed, Explore, Article detail, Saved, Login UI และหน้า **บันทึกเรื่องราว** ที่ผู้ใช้สามารถเขียนโพสต์, เลือกสาธารณะ/ส่วนตัว, กด รัก/ขอบคุณ/กอด, แก้ไข และลบโพสต์ของตัวเองได้ พร้อม REST API และ RLS สำหรับ `stories`. UI ใช้ฟอนต์ Kanit น้ำหนักเบาและการ์ดมุมโค้งเพื่อให้สัมผัสนุ่ม สบายตา
API สำหรับเรื่องราว: `GET /api/stories`, `POST /api/stories`, `PUT /api/stories/:id`, `DELETE /api/stories/:id`, `POST /api/stories/:id/reactions`
เมนูจัดการโพสต์อยู่ที่ปุ่มสามจุดมุมขวาบนของโพสต์ โดยจะแสดงตัวเลือกแก้ไขและลบเมื่อกดเปิดเมนูเท่านั้น ผู้ใช้เลือก reaction ได้เพียง 1 แบบต่อโพสต์ เมื่อกดจะแสดงตัวเลขความรู้สึกเพิ่มขึ้น 1 ครั้ง และสามารถเปลี่ยนไปเลือกความรู้สึกแบบอื่นได้โดยระบบย้ายจำนวนให้อัตโนมัติ หลังโพสต์สำเร็จะแสดงแอนิเมชันใบไม้ปลิว พร้อมปุ่ม `บันทึกโพสต์` และหน้ารวม `/stories/saved` รวมถึงหมวดหมู่ของโพสต์ที่บันทึกไว้ โดยฐานข้อมูลรองรับผ่าน `saved_stories` และ RLS
API บันทึกโพสต์: `GET /api/saved-stories`, `POST /api/saved-stories`, `DELETE /api/saved-stories/:storyId`

หน้าเว็บมี demo content เพื่อให้รันและดู UI ได้แม้ยังไม่ใส่ Supabase credentials; การใช้งานโพสต์จริงต้อง Login และตั้งค่า Supabase ให้เรียบร้อย
## Deploy
Deploy `frontend` เป็น Vercel project โดยใช้ Vite และตั้ง `VITE_*` variables. Deploy `backend` เป็น Vercel Node project หรือ service ที่รองรับ Node โดยตั้ง backend variables และกำหนด `VITE_API_URL` ให้ชี้ API URL. ห้าม commit `.env` หรือ service role key.
