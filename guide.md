จากการเจาะดูรายละเอียดบนหน้าจอ (UI), โค้ด, และ Text บนสไลด์ในภาพอย่างละเอียด นี่คือรายชื่อ **Tools / Tech Stack** ที่วิทยากรใช้ในแต่ละขั้นตอนครับ:

**1. Input Your Brand Context (สร้าง Visual System เอง)**

* **Claude (Anthropic):** สไลด์ระบุชัดเจนว่าใช้ Claude ในการรับข้อมูลบริบทของแบรนด์ (Moodboard) แล้วประมวลผลออกมาเป็น Brand Guidelines (ภาพที่ 22-25)

**2. Researcher Agent (ระบบนักวิจัยและกรองข่าว)**

* **Perplexity (Deep Research):** ในภาพที่ 26 ตรงกล่องข้อมูลฝั่งซ้ายล่าง มีการระบุ Source อย่างชัดเจนว่ามาจาก *"Perplexity Deep Research"* ซึ่งเป็นเครื่องมือ AI ที่เก่งมากในการค้นหาข้อมูลบนอินเทอร์เน็ตแบบเจาะลึกและมีอ้างอิง

**3. Generate Content Topics and Calendar (ระบบวางแผนคอนเทนต์)**

* **NocoDB:** เป็นระบบ Database แบบ No-Code (คล้าย Airtable/Notion) สไลด์ภาพที่ 27 ระบุชัดเจนว่า *"ทุก Record ถูก Push เข้า NocoDB ผ่าน MCP Integration ทันที"* เพื่อใช้ทำตาราง Content Calendar
* **Claude Code:** ในภาพที่ 27 มีการระบุในตารางการทำงานว่าใช้ Claude Code ในการทำงานเบื้องหลัง
* **MCP (Model Context Protocol):** โปรโตคอลที่เป็นตัวกลางให้ AI (อย่าง Claude) สามารถเชื่อมต่อและสั่งงานยิงข้อมูลเข้า NocoDB ได้

**4. Content Writer / Copywriter Agent**

* *(หัวข้อนี้ไม่มีสไลด์แยก)* แต่จากบริบทการทำงานของ Agent ตัวอื่นๆ คาดว่าใช้โมเดลภาษา (LLM) ตัวหลักของโปรเจกต์คือ **Claude** หรือ **ChatGPT** ในการเขียนเนื้อหา

**5. Content Designer Agent (ระบบนักออกแบบกราฟิก)**

* **GPT Image 2.0:** สไลด์ภาพที่ 16 ระบุชัดเจนว่าใช้เทคโนโลยีนี้ (คาดว่าอ้างอิงถึงระบบการเจนภาพของ DALL-E ผ่านทาง ChatGPT) เพื่อสร้างภาพ Artwork ให้ตรงกับ Brand Guideline

**6. Video Maker Agent (ระบบผลิตวิดีโออัตโนมัติ)**

* **HeyGen:** เป็น AI สำหรับสร้าง Human Avatar (คนจำลอง) พร้อมเสียงพากย์ที่ขยับปากเป๊ะตามสคริปต์
* **Remotion:** เป็น Framework สำหรับสร้างวิดีโอด้วยการเขียนโค้ด (React)
* *(สไลด์ภาพที่ 9 ระบุชัดเจนว่าใช้ Stack: **HeyGen + Remotion** เพื่อทำ Parallel Rendering ทำให้เรนเดอร์วิดีโอเสร็จไวมาก)*
* **Terminal / CLI (Command Line Interface):** สั่งรันคำสั่งผลิตวิดีโอผ่าน Command Line เช่น พิมพ์ `/content-engine ทำ video...` (ภาพที่ 11)

**7. Landing Page Generator (ระบบสร้างหน้าเซลล์เพจ)**

* **Claude Code:** ในภาพที่ 8 หน้าจอ IDE ฝั่งขวาระบุชื่อ **Claude Code** ชัดเจนว่าเป็นตัวรับ Brief แล้วเขียนโค้ดสร้างหน้าเว็บ HTML/CSS ให้
* **Cursor / VS Code:** หน้าจอที่วิทยากรใช้พิมพ์และรัน Agent (ภาพที่ 7, 8, 10) คือหน้าต่าง Code Editor (IDE) ซึ่งหน้าตาเหมือน Cursor (ซึ่งเป็น VS Code fork ที่ฝัง AI ไว้)
* *(มีสไลด์หนึ่งภาพที่ 2 พูดถึง OpenClaw Dashboard คาดว่าเป็นชื่อระบบหลังบ้านที่เขาสร้างขึ้นมาเองเพื่อครอบ Tools เหล่านี้)*

**8. Content Publisher (ระบบเผยแพร่อัตโนมัติ)**

* **Custom CLI Script (คำสั่ง One Command):** จากภาพที่ 5 การสั่งงานจะพิมพ์คำสั่งลงใน Terminal (หน้าจอดำๆ `>_`) เพื่อให้ Script วิ่งไปทำงาน
* **Native Platforms APIs:** ตัว Agent จะยิง API ไปยังระบบหลังบ้านของแพลตฟอร์มต่างๆ เพื่อ Publish โดยอัตโนมัติ (ในภาพที่ 18, 19 มีการโชว์หน้าจอ **Meta Business Suite** และ **YouTube Studio** ที่มี Content ถูกดราฟต์และตั้งเวลาไว้แล้วโดยระบุว่า *Created by AI Academy*)

---

**💡 สรุปภาพรวมของ Tech Stack ชุดนี้:**
โปรเจกต์นี้เป็นการนำโมเดล AI ตัวท็อปอย่าง **Claude** และ **ChatGPT (รวมถึง GPT Image / Perplexity)** มาเป็นมันสมอง แล้วเขียนโค้ด (Script/Agent) เชื่อมต่อ API เพื่อสั่งงานแอปพลิเคชันเฉพาะทางอย่าง **NocoDB** (จัดการข้อมูล) และ **HeyGen+Remotion** (ทำวิดีโอ) โดยรันคำสั่งทั้งหมดผ่านหน้าจอ **Terminal / Code Editor (เช่น Cursor)** แบบ Developer ครับ
