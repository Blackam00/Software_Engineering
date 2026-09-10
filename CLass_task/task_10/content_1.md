# Testing Tactics

Testing Tactics คือกลยุทธ์หรือเทคนิคระดับรายละเอียดที่ใช้เลือกว่าจะสร้าง Test Case อย่างไร เพื่อให้การทดสอบสามารถค้นหาข้อผิดพลาดได้อย่างมีประสิทธิภาพ โดยแนวทางสำคัญคือการทดสอบทั้ง **โครงสร้างภายในของโปรแกรม (White-box)** และ **พฤติกรรมที่ผู้ใช้มองเห็น (Black-box)**

การใช้เพียงแนวทางเดียวไม่เพียงพอ เพราะ White-box และ Black-box มีจุดเน้นต่างกันและสามารถค้นพบข้อผิดพลาดคนละประเภท

---

# 1.1 พื้นฐานการทดสอบซอฟต์แวร์ (Software Testing Fundamentals)

### ความหมาย

Software Testing คือกระบวนการตรวจสอบซอฟต์แวร์ด้วยการกำหนดข้อมูลนำเข้า เงื่อนไข หรือสถานการณ์ต่าง ๆ แล้วสังเกตผลลัพธ์ เพื่อค้นหาข้อผิดพลาดและตรวจสอบว่าซอฟต์แวร์เป็นไปตามข้อกำหนดหรือไม่

เป้าหมายสำคัญของการทดสอบไม่ได้หมายความว่า “พิสูจน์ว่าซอฟต์แวร์ไม่มี Bug” แต่เป็นการเพิ่มโอกาสในการค้นพบข้อผิดพลาดที่มีอยู่

### วัตถุประสงค์ของการทดสอบ

1. ค้นหาข้อผิดพลาดของโปรแกรม
2. ตรวจสอบว่าซอฟต์แวร์ทำงานตามข้อกำหนด
3. ตรวจสอบว่าฟังก์ชันต่าง ๆ ให้ผลลัพธ์ถูกต้อง
4. ตรวจสอบพฤติกรรมของระบบในกรณีปกติและกรณีผิดปกติ
5. ตรวจสอบส่วนติดต่อระหว่างองค์ประกอบของระบบ
6. เพิ่มความมั่นใจในคุณภาพของซอฟต์แวร์

### หลักการสำคัญ

- การทดสอบควรมีเป้าหมายในการค้นหาข้อผิดพลาด
- Test Case ที่ดีควรมีโอกาสสูงในการค้นพบ Error
- ไม่ควรสร้าง Test Case ที่ซ้ำกันโดยไม่จำเป็น
- ควรให้ความสำคัญกับค่าขอบเขต เพราะข้อผิดพลาดมักเกิดบริเวณ Boundary
- ไม่สามารถทดสอบทุก Input ที่เป็นไปได้ในระบบจริง จึงต้องเลือก Test Case อย่างมีหลักการ
- การทดสอบควรเริ่มจากหน่วยเล็กแล้วขยายไปสู่ส่วนที่ใหญ่ขึ้น เช่น Class/Component → Integration → System

### Test Case

Test Case โดยทั่วไปประกอบด้วย

- Input หรือข้อมูลนำเข้า
- เงื่อนไขก่อนการทดสอบ (Precondition)
- ขั้นตอนการทดสอบ
- Expected Result
- Actual Result
- ผลการทดสอบ เช่น Pass/Fail

### Testable Software

ซอฟต์แวร์ที่ทดสอบได้ง่ายควรมีคุณสมบัติ เช่น

- **Operable** – ระบบทำงานได้อย่างเหมาะสม
- **Observable** – สามารถสังเกตผลลัพธ์และความผิดปกติได้
- **Controllable** – สามารถควบคุมสถานะและข้อมูลที่ใช้ทดสอบได้
- **Decomposable** – แบ่งเป็นส่วนย่อยที่สามารถทดสอบแยกกันได้
- **Simple** – มีความซับซ้อนที่ไม่เกินความจำเป็น
- **Stable** – ระบบมีการเปลี่ยนแปลงระหว่างการทดสอบไม่มากจนทำให้ Test Case ใช้ไม่ได้
- **Understandable** – ผู้ทดสอบเข้าใจโครงสร้างและพฤติกรรมของระบบได้

---

# 1.2 การทดสอบกล่องขาว (White-box Testing)

White-box Testing เป็นการออกแบบ Test Case โดยพิจารณา **โครงสร้างภายในของโปรแกรม** เช่น Source Code, Control Flow, Conditions, Loops และ Data Structures

ผู้ทดสอบจึงต้องรู้หรือสามารถตรวจสอบรายละเอียดภายในของโปรแกรมได้

### เป้าหมายหลัก

White-box Testing พยายามทำให้เกิดการครอบคลุมของโครงสร้างโปรแกรม เช่น

1. ให้ Statement ต่าง ๆ ถูก execute อย่างน้อยหนึ่งครั้ง
2. ให้ Logical Decision ถูกทดสอบทั้ง True และ False
3. ให้ Loop ถูกทดสอบบริเวณขอบเขตและจำนวนรอบต่าง ๆ
4. ตรวจสอบการใช้งาน Internal Data Structures

### เทคนิคสำคัญ

- Basis Path Testing
- Condition Testing
- Data Flow Testing
- Loop Testing

### ตัวอย่าง

สมมติว่าโปรแกรมมีเงื่อนไข

```text
if age >= 18
    allow()
else
    reject()
```

White-box Testing จะสนใจว่า Test Case สามารถทำให้ Branch ทั้งสองทำงานหรือไม่ เช่น

- age = 20 → True branch
- age = 15 → False branch

ดังนั้นไม่ได้มองเพียงว่า “ผู้ใช้ได้รับผลลัพธ์ถูกต้องหรือไม่” แต่สนใจว่าภายในโปรแกรมมีการเดินผ่าน Logic ที่ต้องการครบหรือไม่

---

# 1.3 การทดสอบเส้นทางมูลฐาน (Basis Path Testing)

Basis Path Testing เป็นเทคนิค White-box Testing ที่เสนอโดย **Tom McCabe** โดยใช้โครงสร้างการควบคุมของโปรแกรมเพื่อกำหนดชุดเส้นทางการทำงาน (Basis Set of Execution Paths)

แนวคิดสำคัญคือสร้าง **Control Flow Graph / Flow Graph** เพื่อแสดงเส้นทางการทำงานของโปรแกรม แล้วใช้ **Cyclomatic Complexity** เพื่อช่วยคำนวณจำนวน Independent Paths ที่ต้องพิจารณา

### Independent Path

Independent Path คือเส้นทางที่เพิ่ม Statement หรือ Condition/Edge ใหม่จากเส้นทางที่พิจารณาไปแล้ว

หากสามารถสร้าง Test Case ให้ครอบคลุม Basis Set ได้ จะช่วยรับประกันในระดับหนึ่งว่า Statement ของโปรแกรมถูก execute อย่างน้อยหนึ่งครั้ง และสามารถครอบคลุมเงื่อนไขสำคัญได้

### Cyclomatic Complexity

Cyclomatic Complexity ใช้วัดความซับซ้อนเชิงตรรกะของ Control Flow

สูตรที่ใช้ได้ เช่น

```text
V(G) = E - N + 2
```

โดย

- `E` = จำนวน Edges
- `N` = จำนวน Nodes

หรือเมื่อพิจารณา Predicate Nodes:

```text
V(G) = P + 1
```

โดย `P` คือจำนวนจุดตัดสินใจ (Predicate/Decision Nodes)

ค่าที่ได้สามารถใช้เป็นจำนวน Independent Paths ใน Basis Set และเป็นแนวทางในการกำหนดจำนวน Test Cases ที่จำเป็นสำหรับการครอบคลุมเส้นทางพื้นฐาน

### ขั้นตอนของ Basis Path Testing

1. แปลง Control Flow ของโปรแกรมเป็น Flow Graph
2. คำนวณ Cyclomatic Complexity
3. หา Independent Paths ตามจำนวนที่ได้
4. สร้าง Test Case เพื่อบังคับให้โปรแกรมเดินผ่านแต่ละ Path
5. รัน Test Case และตรวจสอบผลลัพธ์

### ข้อดี

- มีหลักการในการเลือกเส้นทางอย่างเป็นระบบ
- ช่วยค้นหา Logic Error
- เหมาะกับ Module ที่มีความสำคัญหรือมี Logic ซับซ้อน

### ข้อจำกัด

- ต้องเข้าใจโครงสร้างโปรแกรม
- เมื่อโปรแกรมมีความซับซ้อนมาก จำนวน Path อาจเพิ่มขึ้นมาก
- การครอบคลุม Path ไม่ได้หมายความว่าซอฟต์แวร์ถูกต้องทุกกรณี

---

# 1.4 การทดสอบโครงสร้างควบคุม (Control Structure Testing)

Control Structure Testing เป็นกลุ่มเทคนิค White-box Testing ที่เน้นโครงสร้างควบคุมของโปรแกรม โดย Pressman แบ่งแนวทางสำคัญเป็น

1. Condition Testing
2. Data Flow Testing
3. Loop Testing

## 1.4.1 Condition Testing

เน้นตรวจสอบเงื่อนไขในคำสั่ง เช่น

```text
if (A && B)
```

ควรออกแบบ Test Case เพื่อให้สามารถตรวจสอบผลลัพธ์ของเงื่อนไขต่าง ๆ เช่น A เป็น True/False และ B เป็น True/False ตามความเหมาะสม

จุดประสงค์คือค้นหา Error ใน Logical Expression และ Operator เช่น `AND`, `OR`, `NOT`, `>`, `<`, `==`

## 1.4.2 Data Flow Testing

Data Flow Testing ติดตามการใช้งานตัวแปรตั้งแต่การกำหนดค่า (Definition) ไปจนถึงการนำค่าไปใช้งาน (Use)

ตัวอย่างปัญหาที่ต้องการค้นหา:

- ตัวแปรถูกใช้ก่อนกำหนดค่า
- กำหนดค่าให้ตัวแปรแต่ไม่เคยนำไปใช้
- ตัวแปรถูกกำหนดค่าซ้ำโดยไม่ใช้ค่าก่อนหน้า
- เส้นทางการทำงานทำให้ค่าตัวแปรผิด

## 1.4.3 Loop Testing

Loop เป็นแหล่งที่เกิด Error ได้บ่อย จึงควรทดสอบจำนวนรอบหลายกรณี เช่น

- 0 รอบ
- 1 รอบ
- 2 รอบ
- จำนวนรอบปกติ
- จำนวนรอบสูงสุด
- เกินขอบเขตที่กำหนด

ตัวอย่างเช่น Loop ที่อนุญาตให้ทำงาน 1–10 รอบ ควรสนใจค่า 0, 1, 2, 9, 10 และ 11 เพื่อค้นหาข้อผิดพลาดบริเวณ Boundary

---

# 1.5 การทดสอบกล่องดำ (Black-box Testing)

Black-box Testing เป็นการออกแบบ Test Case โดย **ไม่พิจารณาโครงสร้างภายในของโปรแกรม** แต่พิจารณาจาก Functional Requirements, Specification, Input และ Expected Output

จึงเรียกอีกอย่างว่า **Specification-based Testing**

### สิ่งที่ Black-box Testing มุ่งตรวจสอบ

- ฟังก์ชันที่ขาดหายหรือทำงานผิด
- Interface Error
- ปัญหาการเข้าถึงฐานข้อมูลหรือโครงสร้างข้อมูลภายนอก
- Behavior และ Performance
- Initialization และ Termination

### เทคนิคสำคัญ

#### 1. Equivalence Partitioning

แบ่ง Input Domain ออกเป็นกลุ่มที่คาดว่าจะมีพฤติกรรมเหมือนกัน แล้วเลือกตัวแทนจากแต่ละกลุ่ม

ตัวอย่าง:

ระบบรับอายุ 18–60 ปี

แบ่งได้เป็น

- ต่ำกว่า 18 → Invalid
- 18–60 → Valid
- มากกว่า 60 → Invalid

ไม่จำเป็นต้องทดสอบทุกค่าตั้งแต่ 0–100 แต่เลือกตัวแทนจากแต่ละกลุ่ม

#### 2. Boundary Value Analysis

เน้นทดสอบบริเวณขอบเขต เพราะ Error มักเกิดที่ Boundary

จากตัวอย่าง 18–60 อาจเลือก

- 17
- 18
- 19
- 59
- 60
- 61

#### 3. Graph-based Testing

สร้าง Graph ที่แสดง Object หรือความสัมพันธ์/การเปลี่ยนแปลง แล้วออกแบบ Test Case เพื่อให้ครอบคลุม Nodes และ Links ที่สำคัญ

#### 4. Model-based Testing

สร้างแบบจำลองพฤติกรรมของระบบ เช่น State หรือ Transition แล้วสร้าง Test Case จากแบบจำลองนั้น

### เปรียบเทียบ White-box กับ Black-box

| ประเด็น | White-box | Black-box |
|---|---|---|
| สิ่งที่สนใจ | โครงสร้างภายใน | พฤติกรรม/ข้อกำหนด |
| ต้องเห็น Source Code หรือไม่ | โดยทั่วไปต้องรู้โครงสร้างภายใน | ไม่จำเป็น |
| ตัวอย่างเทคนิค | Basis Path, Condition, Data Flow, Loop | Equivalence Partitioning, Boundary Value |
| จุดเด่น | ตรวจสอบ Logic และ Control Flow | ตรวจสอบ Function ที่ผู้ใช้มองเห็น |
| เหมาะกับ | Unit/Component และ Logic สำคัญ | Functional/System/Acceptance ตามบริบท |
| ควรใช้ร่วมกันหรือไม่ | ใช่ | ใช่ |

---

# 1.6 วิธีทดสอบเชิงวัตถุ (Object-Oriented Testing Methods)

Object-Oriented Testing (OOT) ต้องคำนึงถึงคุณสมบัติของ Object-Oriented Programming เช่น

- Class
- Object
- Encapsulation
- Inheritance
- Polymorphism
- Message Passing
- Collaboration ระหว่าง Object

ในระบบเชิงวัตถุ หน่วยที่เหมาะสมสำหรับ Unit Testing คือ **Class/Object ที่ห่อหุ้ม State และ Operations ไว้ด้วยกัน** ไม่ใช่เพียงการทดสอบ Method แยกจากบริบทของ Class เสมอไป

### ประเด็นที่ทำให้ OO Testing แตกต่าง

#### 1. Encapsulation

ข้อมูลภายใน Object อาจไม่สามารถเข้าถึงโดยตรงจากภายนอก จึงต้องทดสอบผ่าน Public Operations และ Interface ของ Class

#### 2. Inheritance

ต้องตรวจสอบว่าพฤติกรรมของ Subclass ยังคงถูกต้องเมื่อรับคุณสมบัติหรือ Method จาก Superclass

#### 3. Polymorphism

Method เดียวกันอาจทำงานแตกต่างกันตามชนิดของ Object จึงต้องทดสอบหลายชนิดของ Object ที่สามารถถูกส่งเข้ามาได้

#### 4. State

Object อาจให้ผลลัพธ์แตกต่างกันตาม State ปัจจุบัน ดังนั้น Test Case ต้องพิจารณาลำดับของ Operation

### วิธีการสำคัญในการทดสอบ OO

- Fault-based Testing
- Scenario-based Test Design
- Class Hierarchy Testing
- Surface Structure Testing
- Deep Structure Testing

**Surface Structure Testing** เน้นสิ่งที่มองเห็นจากภายนอกและมีลักษณะคล้าย Black-box Testing

**Deep Structure Testing** เน้น Dependency, Behavior และ Communication ภายในโครงสร้าง OO และมีลักษณะใกล้เคียง White-box Testing

---

# 1.7 การประยุกต์วิธีการทดสอบ ณ ระดับคลาส (Testing Methods Applicable at the Class Level)

การทดสอบระดับ Class มุ่งทดสอบ Class หนึ่ง ๆ พร้อม Methods และ State ที่อยู่ภายใน Class

Pressman กล่าวถึงวิธีสำคัญ 2 แนวทาง คือ

1. Random Testing for OO Classes
2. Partition Testing at the Class Level

## 1.7.1 Random Testing for OO Classes

สร้างลำดับการเรียก Operation ของ Object แบบสุ่ม แต่ต้องไม่ละเมิดข้อจำกัดของ State

ตัวอย่าง Class `Account`

```text
open()
setup()
deposit()
withdraw()
balance()
summarize()
creditLimit()
close()
```

ไม่สามารถเรียก `withdraw()` ก่อน `open()` ได้อย่างถูกต้องในทุกระบบ ดังนั้น Random Testing ต้องสร้าง Sequence ที่สอดคล้องกับข้อจำกัดของ Class

ตัวอย่าง Test Sequence:

```text
open → setup → deposit → balance → withdraw → close
```

หรือ

```text
open → setup → deposit → deposit → summarize → withdraw → close
```

ข้อดีคือช่วยค้นหาพฤติกรรมที่เกิดจากลำดับการเรียก Method ที่แตกต่างกัน

ข้อจำกัดคือจำนวน Permutations อาจเพิ่มขึ้นอย่างรวดเร็ว จึงควรใช้วิธีลดจำนวน Combination เมื่อระบบมีความซับซ้อนมาก

## 1.7.2 Partition Testing at the Class Level

เป็นการแบ่ง Test Case ออกเป็นกลุ่มตามลักษณะของ Operation, Attribute หรือ State เพื่อให้ลดจำนวน Test Case แต่ยังคงครอบคลุมพฤติกรรมที่สำคัญ

สามารถพิจารณา Partition เช่น

- **State-based partition** – แบ่งตาม State ของ Object
- **Attribute-based partition** – แบ่งตามค่าหรือช่วงของ Attribute
- **Category-based partition** – แบ่งตามประเภทของข้อมูลหรือพฤติกรรม

ตัวอย่าง Object `Account`

อาจแบ่ง State เป็น

```text
New → Open → Active → Closed
```

แล้วออกแบบ Test Case ให้ครอบคลุม Operation ที่อนุญาตและไม่อนุญาตในแต่ละ State

---

# 1.8 การออกแบบกรณีการทดสอบระหว่างคลาส (Inter Class Test Case Design)

Interclass Test Case Design คือการออกแบบ Test Case เพื่อทดสอบ **การทำงานร่วมกันและการสื่อสารระหว่างหลาย Class**

ปัญหาที่ต้องตรวจสอบจึงไม่ใช่เพียงว่าแต่ละ Class ทำงานถูกต้องหรือไม่ แต่ต้องตรวจสอบว่าเมื่อ Class ส่ง Message หรือเรียก Operation ของ Class อื่นแล้ว ระบบยังทำงานถูกต้องหรือไม่

ตัวอย่าง

```text
Customer → Order → Payment → Wallet
```

แต่ละ Class อาจผ่าน Unit Test ของตัวเองทั้งหมด แต่เมื่อทำงานร่วมกันอาจเกิดปัญหา เช่น

- ส่ง Parameter ผิดชนิด
- เรียก Method ผิดลำดับ
- State ของ Object ไม่ตรงกัน
- Class หนึ่งคาดหวังข้อมูลที่อีก Class ไม่ได้ส่ง
- Message/Interface ระหว่าง Class ทำงานผิด

## 1.8.1 Multiple Class Testing

เป็นการสร้าง Test Case ที่เกี่ยวข้องกับหลาย Class โดยพิจารณา Operations ของ Client Class ที่ส่ง Message ไปยัง Server Class

แนวทางทั่วไป:

1. ระบุ Client Class
2. ระบุ Server Class ที่ Client ส่ง Message ไปหา
3. ระบุ Operations ที่ถูกเรียก
4. สร้าง Sequence ของ Operation
5. สร้าง Test Case เพื่อทดสอบ Sequence และผลลัพธ์
6. ตรวจสอบ State และผลกระทบที่เกิดกับแต่ละ Object

ตัวอย่าง:

```text
Customer.login()
    ↓
Order.create()
    ↓
Payment.pay()
    ↓
Wallet.deduct()
```

Test Case ควรตรวจสอบทั้งผลลัพธ์ของแต่ละขั้นและผลลัพธ์รวมของ Collaboration

## 1.8.2 Tests Derived from Behavior Models

อีกแนวทางหนึ่งคือสร้าง Test Case จาก Behavioral Model เช่น

- State Diagram
- State Transition
- Sequence Diagram
- Collaboration/Interaction Diagram

ตัวอย่าง Order:

```text
Created → Paid → Preparing → Completed
```

ควรทดสอบทั้ง Transition ที่ถูกต้อง เช่น

```text
Created → Paid
Paid → Preparing
Preparing → Completed
```

และ Transition ที่ไม่ควรเกิด เช่น

```text
Created → Completed
```

หากระบบกำหนดว่าต้องผ่าน Paid และ Preparing ก่อน

### จุดสำคัญของ Interclass Testing

ต้องตรวจสอบว่า Test Case ครอบคลุม

- Collaboration ระหว่าง Class
- Message ที่ส่งระหว่าง Object
- ลำดับการเรียก Method
- State Transition
- Parameter และ Return Value
- ผลกระทบต่อ State ของ Object ที่เกี่ยวข้อง

---

# แหล่งอ้างอิง
- Pressman, *Software Engineering: A Practitioner's Approach*: https://whyphi.staff.telkomuniversity.ac.id/files/2016/01/ebook-pressman-sw-engineering.pdf
- Old Dominion University — White-Box Testing: https://www.cs.odu.edu/~zeil/cs333/website-s12/Lectures/wbtesting/page/wbtesting.html
- Wiley — Black-Box Testing: https://onlinelibrary.wiley.com/doi/full/10.1002/0471028959.sof022
