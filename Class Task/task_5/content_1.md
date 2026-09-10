# 1. สถาปัตยกรรมซอฟต์แวร์

## 1.1 ความหมายของสถาปัตยกรรมซอฟต์แวร์

สถาปัตยกรรมซอฟต์แวร์ (Software Architecture) คือโครงสร้างระดับสูงของระบบซอฟต์แวร์ ซึ่งกำหนดองค์ประกอบหลัก (Components) ความสัมพันธ์ การสื่อสาร และหลักการออกแบบ เพื่อให้ระบบตอบสนองทั้งด้านหน้าที่การทำงานและคุณภาพ เช่น ประสิทธิภาพ ความปลอดภัย การบำรุงรักษา และการขยายระบบ

## 1.2 ความหมายของการออกแบบสถาปัตยกรรมซอฟต์แวร์

เป็นกระบวนการกำหนดโครงสร้างหลักของระบบ เลือกองค์ประกอบและรูปแบบสถาปัตยกรรมที่เหมาะสม เพื่อให้ตรงกับความต้องการของผู้ใช้และข้อกำหนดด้านคุณภาพ ก่อนเข้าสู่การออกแบบรายละเอียดและการพัฒนา

## 1.3 สไตล์และแบบรูปสถาปัตยกรรม

### 1.3.1 Architectural Styles

Architectural Style คือ แนวทางหรือรูปแบบระดับสูงในการจัดโครงสร้างของระบบ โดยกำหนดว่าระบบควรแบ่งส่วนและสื่อสารกันอย่างไร เช่น

#### 1. Layered Architecture

แบ่งระบบออกเป็นหลายชั้น เช่น Presentation, Business Logic, Data Access และ Database แต่ละชั้นติดต่อเฉพาะชั้นที่อยู่ติดกัน

![Coupling and Cohesion: The Two Principles for Effective Architecture](https://images.openai.com/static-rsc-4/rXoj-0aKXroYV2apRly21Yw_ZWOtriC76Z62Rq2EUpUFDxrOVXlM7OD2Pri0xAqsOytcpwYjZKEXn47vtYNUHYNR14EPhJBI674zngKnn422d77ZYJ1LtPaTLLSx8ySn9RKtTVr9X2G-2QfZEngmIexKVhzpDQbs9Rtf5-JSHuoUuMB-W9UE0HciJ4kizFQZ?purpose=fullsize)

[https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/n-tier?utm_source=chatgpt.com](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/n-tier?utm_source=chatgpt.com)

**การทำงาน**

- ผู้ใช้ส่งคำขอผ่าน Presentation Layer
- Business Logic ประมวลผล
- Data Access ติดต่อฐานข้อมูล
- ส่งผลลัพธ์กลับไปยังผู้ใช้

#### 2. Client-Server

แบ่งเป็น Client และ Server

![Dhanian 🗯️ (@e_opore) on X](https://images.openai.com/static-rsc-4/OrnmXjPsZ9kSADv5NhT3DP4CjQLWbRAUqo44emzvNUQON2AyPoYCb2FFuow4sPIc7C4d8KYnUcu6VP_LVkGK2qcNLVRKYrIfVFqZR5c1ednlnC6OmlH-VR2CT4XW0y3hbXpIvGPNsD4OgHYhcZaY2qIC84YcqOVIC2y_537b_cR5U_NVufo4UDRrF2TXFhzN?purpose=fullsize)

[https://www.geeksforgeeks.org/system-design/client-server-model/](https://www.geeksforgeeks.org/system-design/client-server-model/)

**การทำงาน**

1. Client ส่ง Request
2. Server ประมวลผล
3. Server ส่ง Response กลับ

ตัวอย่าง: เว็บไซต์ แอปพลิเคชันมือถือ ระบบธนาคารออนไลน์

#### 3. Microservices

แบ่งระบบเป็นบริการย่อยหลาย Service ที่ทำงานและ Deploy แยกกันได้

![What Is a Distributed System? - SolarWinds Blog](https://images.openai.com/static-rsc-4/xMJkbH79I-OO73YUO35Kbg8jL2cgnP5mUo8PHecVbBDJMkDbsElxYirxkt1UzWF9zk0wcC13J-LqBJP7bvNxasaKHEcwQhGacfb7hkJWmz1Tuf49k4ZfTlQ0cTQ7V-QAPDoZQ5ybc8ysjqwKYN7CwQOn-WrfhuglP6wg0hd7o9Knz-enbAAQ3EDt4DVNfKAJ?purpose=fullsize)

[https://learn.microsoft.com/en-us/dotnet/architecture/microservices/?utm_source=chatgpt.com](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/?utm_source=chatgpt.com)

**การทำงาน**

- Order Service รับคำสั่งซื้อ
- Product Service ตรวจสอบสินค้า
- Payment Service ชำระเงิน
- Shipping Service จัดส่งสินค้า

Service ต่าง ๆ สื่อสารกันผ่าน API

### 1.3.2 Architectural Patterns

Architectural Pattern คือ แนวทางแก้ปัญหาที่สามารถนำกลับมาใช้ซ้ำได้ โดยระบุโครงสร้างและบทบาทขององค์ประกอบในระบบ

#### 1. MVC (Model-View-Controller)

![iphone - Understanding MVC pattern used in iOS apps - Stack Overflow](https://images.openai.com/static-rsc-4/2GNn1_ZVZcbBoNazsxpf4r8kO-FPcDHBM6fE_m1acbsyMxdRHhzs0Gz9GKmf5_kNCPtCWc29T_fCSoIWsF1kvv8bQ2mb7k_REtppVX_Xg6fVLFLfOCZDAvy_6zgTYqZ8vJWORDEhNIhQ8HamUo7KntJ0jeuZqwhTFaos0WgSFdnfGOl10gA8fQyYqD2fd-sF?purpose=fullsize)

[https://learn.microsoft.com/en-us/aspnet/mvc/overview/?utm_source=chatgpt.com](https://learn.microsoft.com/en-us/aspnet/mvc/overview/?utm_source=chatgpt.com)

**การทำงาน**

1. Controller รับคำสั่งจากผู้ใช้
2. Model ประมวลผลข้อมูล
3. View แสดงผลลัพธ์

ตัวอย่าง: Laravel, ASP.NET MVC, Spring MVC

#### 2. MVVM (Model-View-ViewModel)

![Software Architectural Patterns: MVVM | by Andrew Lundy | Medium](https://images.openai.com/static-rsc-4/_L6_ue4sS4ZNdUlpcYcXzMwtyVH_mNL3o2OzmwBb6EVCzklxwQ6y8_ngGxUTX1ye6cE0aq5KF_mwL1YhZr5f_vUVqF0f9RGE_RbYmUKjTGVX5mCRUqfswKQFsiVUNWIaHuV_MjI_ytCYcDsUTKKIdC-Tbn1ditHap317YvmJmPbZeJ3dnpgWzxBHhazRaWQa?purpose=fullsize)

[https://learn.microsoft.com/en-us/aspnet/mvc/overview/?utm_source=chatgpt.com](https://learn.microsoft.com/en-us/aspnet/mvc/overview/?utm_source=chatgpt.com)

**การทำงาน**
ViewModel เป็นตัวกลางระหว่าง View และ Model และใช้ Data Binding เพื่ออัปเดตหน้าจออัตโนมัติ

ตัวอย่าง: WPF, Xamarin, .NET MAUI

#### 3. SOA (Service-Oriented Architecture)

![Software Architecture: 11. Component-Based Architecture | by Gabriel Bravo | Mar, 2026 | Medium](https://images.openai.com/static-rsc-4/-XpJyPsKP77_LE9gHh-bX-4w7Vbv2PbiJju6tlGA_2pvFe6ZtjqXOb-t6_GSmNtSi0cpZN-Er3N0qmxTpT9-enxg8oujPcZBsCcPk5vGdec_WZMUnkTd-9VZFjTblBkWuDuzF65olwUSA3TQmmiMgFBaL_dEdyKaSkcGNdRovtkyKKzlnKEzROc-G-40IBbw?purpose=fullsize)

[https://www.ibm.com/think/topics/soa?utm_source=chatgpt.com](https://www.ibm.com/think/topics/soa?utm_source=chatgpt.com)

**การทำงาน**
หลายระบบสามารถเรียกใช้ Service เดียวกันผ่าน Web Service หรือ API ทำให้ลดความซ้ำซ้อนและนำบริการกลับมาใช้ซ้ำได้

ตัวอย่าง: ระบบธนาคารและระบบองค์กรขนาดใหญ่

## 1.4 กระบวนการออกแบบเชิงสถาปัตยกรรม

1. วิเคราะห์ความต้องการ
2. ระบุคุณลักษณะด้านคุณภาพ (Quality Attributes)
3. เลือก Architectural Style/Pattern
4. กำหนดองค์ประกอบและการเชื่อมต่อ
5. ประเมินและปรับปรุงสถาปัตยกรรม
6. จัดทำเอกสารสถาปัตยกรรม

## สรุป

สถาปัตยกรรมซอฟต์แวร์เป็นการออกแบบโครงสร้างระดับสูงของระบบ เพื่อให้ซอฟต์แวร์มีคุณภาพ ขยายระบบได้ง่าย และบำรุงรักษาได้ดี การออกแบบที่ดีต้องเลือกสไตล์และแบบรูปที่เหมาะสม พร้อมประเมินคุณภาพก่อนพัฒนา
