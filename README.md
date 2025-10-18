FROM: you@example.com
TO: friend@example.org
SUBJECT: Hello!
BODY: How are you?
```

#### Transport Layer:
**المهمة**: إنشاء اتصال end-to-end موثوق
- **Protocol**: **TCP** (Transmission Control Protocol)
- **الوظيفة**: 
  - تقسيم الرسالة لـ segments
  - ضمان وصول كل segment
  - إعادة الإرسال لو في فقدان
  - ترتيب الـ segments

**تشبيه**: TCP زي شركة الشحن اللي بتضمن وصول الطرد كامل وسليم.

#### Network Layer:
**المهمة**: إضافة عنوان الوجهة النهائية
- **Protocol**: **IP** (Internet Protocol)
- **الوظيفة**: 
  - إضافة IP address للمصدر والوجهة
  - Routing (اختيار الطريق)

**مثال**:
```
Source IP: 41.65.x.x (مصر)
Destination IP: 172.217.x.x (سيرفر Gmail في أمريكا)
```

#### Data Link & Physical Layers:
**المهمة**: إضافة physical address والوصول للوسط
- **Protocols**: 
  - **MAC** (Media Access Control) addressing
  - Ethernet, WiFi
- **الوظيفة**:
  - **Encryption** (التشفير): حماية البيانات
  - إضافة **physical address** (MAC address) للـ next hop
  - **Accessing medium**: الوصول للكابل أو الـ wireless channel

**MAC Address مثال**: `00:1A:2B:3C:4D:5E`

#### Physical Layer:
**المهمة النهائية**: إرسال الإشارات الفعلية
- **إشارة أو مجموعة إشارات** بتتبعت من الكمبيوتر المصدر للكمبيوتر الوجهة
- **الوسط**: كهرباء في أسلاك، ضوء في fiber optic، موجات راديو في wireless

### الترتيب:
كل software package بيستخدم خدمات الـ package اللي تحته:
```
Application (SMTP)
    ↓ uses
Transport (TCP)
    ↓ uses
Network (IP)
    ↓ uses
Data Link (Ethernet/WiFi)
    ↓ uses
Physical (Signals)
```

**الملخص**: المهمة المعقدة (إرسال إيميل عبر العالم) اتقسمت لمهام بسيطة، كل واحدة متخصصة في حاجة معينة.

---

## الصفحة 11 (الصورة): Layered Tasks

**الصورة بتوضح**:

مثال على الـ layered approach:
- **Sender** (المرسل) على الشمال
- **Receiver** (المستقبل) على اليمين
- كل طبقة في المرسل بتتكلم (logically) مع نفس الطبقة في المستقبل

**النقطة المهمة**: 
- الطبقات بتتكلم مع بعض **منطقياً** (logically)
- لكن **فيزيائياً** (physically)، البيانات بتنزل لـ Physical Layer وتعدي في الوسط

**Encapsulation** (التغليف):
كل طبقة بتضيف **header** (رأسية) للبيانات:
```
Application: Data
Transport: [TCP Header][Data]
Network: [IP Header][TCP Header][Data]
Data Link: [Ethernet Header][IP Header][TCP Header][Data][Trailer]
Physical: Bits (01010101...)
