# Software Maintenance

---

# 1. ความหมายของการบำรุงรักษาซอฟต์แวร์

**Software Maintenance** หมายถึง การปรับเปลี่ยนซอฟต์แวร์หลังการส่งมอบ เพื่อให้ซอฟต์แวร์ยังคงใช้งานได้ตามความต้องการและเหมาะสมกับสภาพแวดล้อมที่เปลี่ยนแปลง รวมถึงการแก้ไขข้อผิดพลาด การเพิ่มหรือปรับปรุงความสามารถ และการป้องกันข้อผิดพลาดที่อาจเกิดขึ้นในอนาคต

ISO/IEC/IEEE 14764:2022 ให้แนวทางเกี่ยวกับกระบวนการ กิจกรรม และงานที่เกี่ยวข้องกับการบำรุงรักษาซอฟต์แวร์ และระบุประเภทของ Maintenance อย่างชัดเจน

> **สรุปง่าย ๆ:** Software Maintenance ไม่ได้หมายถึง “การแก้ Bug อย่างเดียว” แต่ครอบคลุมการแก้ไข ปรับตัว ปรับปรุง และป้องกันปัญหาของซอฟต์แวร์ตลอดช่วงที่ซอฟต์แวร์ถูกใช้งาน

### เหตุผลที่ต้องบำรุงรักษาซอฟต์แวร์

ซอฟต์แวร์ต้องได้รับการบำรุงรักษาเนื่องจาก

1. พบข้อผิดพลาดหลังจากนำระบบไปใช้งานจริง
2. ระบบปฏิบัติการ Hardware Database หรือ API ภายนอกเปลี่ยนแปลง
3. ผู้ใช้หรือองค์กรต้องการความสามารถใหม่
4. ต้องการเพิ่มประสิทธิภาพหรือความสามารถในการบำรุงรักษา
5. ต้องการลดความเสี่ยงจากข้อผิดพลาดที่ยังไม่เกิดขึ้น
6. ข้อกำหนดทางธุรกิจหรือสภาพแวดล้อมของระบบเปลี่ยนไป

การบำรุงรักษาจึงเป็นส่วนสำคัญของวงจรชีวิตซอฟต์แวร์ และควรมีการวางแผนตั้งแต่ช่วงพัฒนาซอฟต์แวร์ ไม่ใช่รอจนระบบมีปัญหาแล้วจึงเริ่มวางแผน

---

# 2. ประเภทของการบำรุงรักษาซอฟต์แวร์

ตามแนวทางของ ISO/IEC/IEEE 14764 มีการจำแนก Software Maintenance ที่สำคัญเป็น **4 ประเภท**

## 2.1 Corrective Maintenance

คือ การแก้ไขซอฟต์แวร์หลังจากพบปัญหาหรือข้อผิดพลาด (Fault/Problem) เพื่อให้ระบบกลับมาทำงานได้ถูกต้อง

### ตัวอย่าง

ระบบคำนวณราคาสินค้าผิดเมื่อมีส่วนลด 20%

```text
ราคาสินค้า = 1,000 บาท
ส่วนลด = 20%

ผลที่ถูกต้อง = 800 บาท
ระบบเดิมคำนวณ = 900 บาท
```

นักพัฒนาจึงแก้ไข Logic การคำนวณ

### ลักษณะสำคัญ

- มักเกิดจากปัญหาที่ตรวจพบหลังส่งมอบ
- มีลักษณะ **Reactive**
- เป้าหมายคือแก้ปัญหาที่เกิดขึ้นแล้ว

---

## 2.2 Adaptive Maintenance

คือ การปรับเปลี่ยนซอฟต์แวร์เพื่อให้สามารถทำงานต่อไปได้เมื่อ **สภาพแวดล้อมของระบบเปลี่ยนแปลง**

สภาพแวดล้อมอาจหมายถึง

- Operating System
- Database
- Hardware
- External API
- Browser
- กฎหมายหรือข้อกำหนดภายนอก
- Platform หรือ Infrastructure

### ตัวอย่าง

ระบบเดิมเชื่อมต่อ Database รุ่นเก่า แต่บริษัทเปลี่ยน Database Server เป็นรุ่นใหม่ที่มีการเปลี่ยน API

นักพัฒนาจึงต้องแก้ไข Software ให้สามารถทำงานกับ Database รุ่นใหม่ได้

### ลักษณะสำคัญ

- ไม่จำเป็นต้องเกิดจาก Bug ของ Software เดิม
- เกิดจาก Environment ที่ Software ต้องทำงานร่วมด้วยเปลี่ยนไป
- เป็นการทำให้ระบบ “ยังใช้งานได้” ในสภาพแวดล้อมใหม่

---

## 2.3 Perfective Maintenance

คือ การปรับปรุงซอฟต์แวร์หลังส่งมอบเพื่อ **เพิ่มความสามารถ ปรับปรุงประสิทธิภาพ ปรับปรุง Maintainability หรือปรับปรุงคุณลักษณะของซอฟต์แวร์**

### ตัวอย่าง

ผู้ใช้ต้องการให้ระบบสั่งอาหารสามารถค้นหาเมนูด้วยชื่ออาหารได้ จากเดิมที่ต้องเลื่อนดูรายการทั้งหมด

นักพัฒนาเพิ่ม Search Function ให้ระบบ

อีกตัวอย่างหนึ่งคือการปรับปรุง Code ให้มีประสิทธิภาพมากขึ้นหรือปรับปรุงเอกสารประกอบระบบ

### ลักษณะสำคัญ

- เน้นการปรับปรุงหรือเพิ่มคุณค่าให้ระบบ
- อาจเกิดจากความต้องการใหม่ของผู้ใช้
- อาจปรับปรุง Performance หรือ Maintainability
- ไม่จำเป็นต้องเกิดจากข้อผิดพลาด

---

## 2.4 Preventive Maintenance

คือ การปรับเปลี่ยนซอฟต์แวร์เพื่อ **ค้นหาและแก้ไขปัญหาที่แฝงอยู่ก่อนที่จะกลายเป็นข้อผิดพลาดที่เกิดขึ้นจริงในการใช้งาน**

เป็น Maintenance แบบ **Proactive**

### ตัวอย่าง

ทีมพัฒนาพบว่า Code มีความซับซ้อนมากและมีโอกาสทำให้เกิดปัญหาในอนาคต จึงทำการ Refactoring ก่อนที่จะเกิด Bug

เช่น

```text
ก่อน Refactoring
Function A มีขนาดใหญ่มาก
และมี Logic ซ้ำกันหลายส่วน

        ↓

ทำ Refactoring

        ↓

แยก Function เป็นส่วนย่อย
ลด Code ซ้ำ
ทำให้ดูแลรักษาง่ายขึ้น
```

### ลักษณะสำคัญ

- มุ่งป้องกันปัญหาในอนาคต
- ทำก่อนที่ Fault จะกลายเป็น Failure ที่เกิดขึ้นจริง
- เกี่ยวข้องกับการปรับปรุงโครงสร้าง Code และ Maintainability ได้ เช่น Refactoring

---

## เปรียบเทียบประเภทของ Software Maintenance

| ประเภท         | จุดประสงค์                                               | ตัวอย่าง                                |
| -------------------- | ------------------------------------------------------------------ | ----------------------------------------------- |
| **Corrective** | แก้ปัญหาที่พบแล้ว                                 | แก้ Bug คำนวณเงินผิด             |
| **Adaptive**   | ปรับให้เข้ากับ Environment ใหม่                  | รองรับ OS/Database/API รุ่นใหม่   |
| **Perfective** | เพิ่มความสามารถหรือปรับปรุงคุณภาพ | เพิ่ม Search และปรับ Performance    |
| **Preventive** | ป้องกันปัญหาที่อาจเกิดขึ้น               | Refactoring Code ที่มีความเสี่ยง |

### Reactive และ Proactive

สามารถมองอีกมุมหนึ่งได้ว่า

```text
Reactive
├── Corrective
└── Adaptive

Proactive
├── Preventive
└── Perfective
```

อย่างไรก็ตาม การจัดกลุ่มในมาตรฐานอาจมีรายละเอียดเฉพาะของแต่ละฉบับ/องค์กร เช่น ISO/IEC/IEEE 14764 จัด Adaptive และ Perfective เป็น **Enhancements** และ Corrective กับ Preventive เป็น **Corrections** ในการจัดประเภทบางระดับ

---

# 3. กระบวนการบำรุงรักษาซอฟต์แวร์

Software Maintenance ควรดำเนินการอย่างเป็นกระบวนการ ไม่ควรแก้ไข Source Code โดยตรงโดยไม่มีการวิเคราะห์และควบคุมการเปลี่ยนแปลง

กระบวนการโดยสรุปสามารถแสดงได้ดังนี้

```text
Problem / Change Request
          ↓
Identification & Classification
          ↓
Impact Analysis
          ↓
Planning & Prioritization
          ↓
Design / Modification
          ↓
Implementation
          ↓
Testing & Regression Testing
          ↓
Review / Approval
          ↓
Release / Deployment
          ↓
Evaluation & Closure
```

## 3.1 Problem / Modification Request

เริ่มจากการได้รับคำขอแก้ไขหรือปรับปรุง เช่น

- ผู้ใช้แจ้ง Bug
- ผู้ใช้ขอ Feature ใหม่
- Environment เปลี่ยน
- ทีมพัฒนาพบความเสี่ยงใน Code

คำขอควรถูกบันทึกเป็น **Modification Request (MR)** หรือ Problem Report ตามกระบวนการขององค์กร

---

## 3.2 Identification and Classification

ระบุรายละเอียดของคำขอและจัดประเภทว่าเป็น

- Corrective
- Adaptive
- Perfective
- Preventive

พร้อมกำหนดความสำคัญและความเร่งด่วน

ตัวอย่าง

```text
MR-001
ปัญหา: ระบบคำนวณภาษีผิด
ประเภท: Corrective
Priority: High
```

มาตรฐาน IEEE 1219 เดิมอธิบายกิจกรรม เช่น การกำหนดหมายเลข การจัดประเภท การวิเคราะห์เพื่อยอมรับ/ปฏิเสธ การประมาณขนาด และการจัดลำดับความสำคัญของ Modification Request

---

## 3.3 Impact Analysis

วิเคราะห์ว่าการเปลี่ยนแปลงจะส่งผลกระทบต่อส่วนใดของระบบบ้าง

ต้องพิจารณา เช่น

- Source Code
- Database
- API
- Module อื่น
- User Interface
- Test Case
- Documentation
- Performance
- Security

### ตัวอย่าง

หากเปลี่ยนโครงสร้าง `Customer` อาจส่งผลต่อ

```text
Customer
   ↓
Order
   ↓
Payment
   ↓
Report
```

ดังนั้นไม่ควรแก้เฉพาะ `Customer` โดยไม่ตรวจสอบ Class/Module ที่เกี่ยวข้อง

---

## 3.4 Planning and Prioritization

กำหนด

- ใครเป็นผู้รับผิดชอบ
- ต้องแก้ไขอะไร
- ต้องใช้เวลาเท่าใด
- มีความเสี่ยงอะไร
- ต้องทดสอบส่วนใด
- จะ Release เมื่อใด
- ควรทำก่อนหรือหลัง Maintenance Request อื่น

การจัดลำดับความสำคัญช่วยให้ทีมจัดการปัญหาที่สำคัญก่อน

---

## 3.5 Design and Implementation

เมื่ออนุมัติการเปลี่ยนแปลงแล้ว จึงออกแบบและแก้ไขระบบ

ตัวอย่าง

```text
Requirement
     ↓
Design
     ↓
Code Modification
```

ควรควบคุม Version ของ Source Code และบันทึก Change ที่เกิดขึ้น เพื่อให้สามารถติดตามย้อนกลับได้

---

## 3.6 Testing

หลังจากแก้ไขต้องทดสอบเพื่อยืนยันว่า

1. ปัญหาเดิมได้รับการแก้ไข
2. Function ใหม่ทำงานถูกต้อง
3. การเปลี่ยนแปลงไม่ได้ทำให้ Function เดิมเสีย

### Regression Testing

เป็นส่วนสำคัญของ Software Maintenance เพราะการแก้ไขหนึ่งส่วนอาจส่งผลกระทบต่อส่วนอื่นที่เคยทำงานได้

ตัวอย่าง

```text
แก้ Payment
   ↓
Test Payment
   ↓
Regression Test
   ↓
ตรวจสอบ Order
ตรวจสอบ Wallet
ตรวจสอบ Receipt
```

---

## 3.7 Review, Release และ Deployment

เมื่อผ่านการทดสอบแล้ว จะมีการ Review/Approval ก่อนนำ Version ใหม่ไปใช้งาน

ขั้นตอนอาจประกอบด้วย

```text
Code Review
    ↓
Test Approval
    ↓
Build
    ↓
Release
    ↓
Deployment
```

ควรมีการเก็บ Version และ Release Information เพื่อให้สามารถตรวจสอบย้อนหลังหรือ Rollback ได้หากเกิดปัญหา

---

## 3.8 Evaluation and Closure

หลังจาก Release ควรประเมินผลว่า Maintenance ที่ดำเนินการสามารถแก้ปัญหาหรือบรรลุวัตถุประสงค์หรือไม่

จากนั้นปิด Maintenance Request และบันทึกข้อมูลที่จำเป็น เช่น

- สิ่งที่แก้ไข
- สาเหตุของปัญหา
- เวลาในการแก้ไข
- ผลการทดสอบ
- Version ที่แก้ไข
- ปัญหาที่อาจต้องติดตามต่อ

---

# 4. เทคนิคในการบำรุงรักษาซอฟต์แวร์

เทคนิคที่ใช้ในการบำรุงรักษาขึ้นอยู่กับชนิดของปัญหาและโครงสร้างของระบบ แต่เทคนิคสำคัญมีดังนี้

## 4.1 Refactoring

**Refactoring** คือการปรับโครงสร้างภายในของ Source Code โดยพยายามไม่เปลี่ยนพฤติกรรมที่ผู้ใช้มองเห็น

ตัวอย่าง

```text
ก่อน Refactoring
Function ใหญ่
   ├── ตรวจสอบข้อมูล
   ├── คำนวณ
   ├── บันทึกข้อมูล
   └── ส่ง Email

หลัง Refactoring
validateData()
calculate()
saveData()
sendEmail()
```

ประโยชน์:

- ลด Code Complexity
- ลด Code Duplication
- เพิ่ม Maintainability
- ทำให้แก้ไขในอนาคตง่ายขึ้น

---

## 4.2 Regression Testing

ใช้ทดสอบว่า Modification ใหม่ไม่ได้ทำให้ Function เดิมเสีย

ควรมี Automated Test Suite เพื่อให้สามารถรัน Regression Test ได้อย่างรวดเร็ว โดยเฉพาะระบบที่มีการเปลี่ยนแปลงบ่อย

---

## 4.3 Impact Analysis

วิเคราะห์ผลกระทบก่อนแก้ไขระบบ

คำถามสำคัญคือ

```text
ถ้าแก้ Module นี้
        ↓
Module ไหนจะได้รับผลกระทบ?
        ↓
Test Case ไหนต้องรันใหม่?
        ↓
Database/API/UI ส่วนไหนต้องเปลี่ยน?
```

เทคนิคนี้ช่วยลดความเสี่ยงจากการแก้ไขระบบโดยไม่ทราบผลกระทบ

---

## 4.4 Reverse Engineering

Reverse Engineering คือการวิเคราะห์ Software ที่มีอยู่เพื่อทำความเข้าใจโครงสร้าง การทำงาน หรือการออกแบบของระบบ

มีประโยชน์อย่างมากเมื่อ

- ระบบเก่าไม่มีเอกสาร
- Developer เดิมไม่ได้ทำงานกับระบบแล้ว
- Source Code ซับซ้อน
- ต้องการทำความเข้าใจระบบก่อนแก้ไข

ตัวอย่าง

```text
Existing System
      ↓
Analyze Source Code
      ↓
Understand Architecture
      ↓
Create Documentation / Model
      ↓
Maintenance
```

---

## 4.5 Program Comprehension

คือการทำความเข้าใจโปรแกรมก่อนทำการแก้ไข

อาจใช้

- Source Code Reading
- Code Search
- Dependency Analysis
- Call Graph
- UML Diagram
- Documentation
- Debugging Tools
- Static Analysis

เป้าหมายคือทำให้ Maintainer เข้าใจว่า Code ส่วนที่ต้องแก้ทำงานอย่างไรและเชื่อมโยงกับส่วนอื่นอย่างไร

---

## 4.6 Code Analysis / Static Analysis

ใช้เครื่องมือวิเคราะห์ Source Code โดยไม่จำเป็นต้องรันโปรแกรม เช่น ตรวจสอบ

- Code Smell
- Unused Variable
- Duplicate Code
- Complexity
- Potential Bug
- Security Issue

ช่วยค้นหาปัญหาใน Code ได้ตั้งแต่ก่อนนำระบบไปใช้งานจริง

---

## 4.7 Configuration Management และ Version Control

ใช้ควบคุม Version ของ Source Code และ Artifact ที่เกี่ยวข้อง

ตัวอย่างเครื่องมือ เช่น

```text
Git
GitHub
GitLab
Bitbucket
```

ช่วยให้ทีมสามารถ

- ติดตามว่าใครแก้ไขอะไร
- เปรียบเทียบ Version
- ย้อนกลับไป Version ก่อนหน้า
- ทำ Branch
- Merge การเปลี่ยนแปลง
- ตรวจสอบประวัติการแก้ไข

---

## 4.8 Automated Testing และ Continuous Integration

การมี Automated Test ช่วยให้สามารถตรวจสอบระบบหลังจากมีการแก้ไขได้รวดเร็ว

ตัวอย่างกระบวนการ

```text
Developer Commit
       ↓
Build
       ↓
Automated Test
       ↓
Regression Test
       ↓
Pass → Release
Fail → Fix
```

เหมาะอย่างยิ่งกับระบบที่มีการ Maintenance และ Release บ่อย

---

## 4.9 Documentation

เอกสารที่ดีช่วยลดเวลาในการทำความเข้าใจระบบ โดยเฉพาะระบบที่มีอายุการใช้งานยาวนาน

ควรดูแล เช่น

- System Architecture
- Database Schema
- API Documentation
- Installation Guide
- Configuration
- User Manual
- Change Log
- Maintenance Record

เมื่อมีการเปลี่ยนแปลง Software ควรปรับปรุงเอกสารที่เกี่ยวข้องด้วย

---

## สรุปสั้นสำหรับการจำ

**Software Maintenance = การดูแลและปรับเปลี่ยน Software หลังส่งมอบ เพื่อให้ระบบยังคงถูกต้อง ใช้งานได้ และตอบสนองต่อความต้องการที่เปลี่ยนแปลง**

จำประเภทด้วยคำว่า **C-A-P-P**

- **C — Corrective:** แก้ Bug
- **A — Adaptive:** ปรับตาม Environment
- **P — Perfective:** ปรับปรุง/เพิ่มความสามารถ
- **P — Preventive:** ป้องกันปัญหา

จำกระบวนการแบบย่อ:

**Request → Classify → Analyze → Plan → Modify → Test → Release → Evaluate**

---

# แหล่งอ้างอิง

1. ISO/IEC/IEEE 14764:2022, *Software engineering — Software life cycle processes — Maintenance*. International Organization for Standardization (ISO).https://www.iso.org/standard/80710.html
2. IEEE Computer Society, *SWEBOK Guide — Software Maintenance*. เนื้อหาเกี่ยวกับประเภทและแนวคิดของ Software Maintenance.https://www.swebok.org/
3. Thomas M. Pigoski, *Software Maintenance*, Software Engineering Body of Knowledge (SWEBOK). อธิบาย Corrective, Adaptive, Perfective และ Preventive Maintenance รวมถึง Maintenance Process.https://sceweb.uhcl.edu/helm/SWEBOK_IEEE/data/swebok_chapter_06.pdf
4. IEEE Technology Navigator, *Software Maintenance*. สรุปความหมาย ประเภท และแนวทางการจัดการ Software Maintenance.https://technav.ieee.org/topic/software-maintenance/
5. IEEE Std 1219-1998, *IEEE Standard for Software Maintenance*. ใช้เป็นข้อมูลประกอบด้านกระบวนการ Maintenance เช่น การระบุ Classification, Prioritization และ Modification Request
