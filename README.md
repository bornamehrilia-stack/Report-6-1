# Report-6-1



---

# گزارش پروژه: ساخت پیانو ساده با آردوینو (Simple Piano with Arduino)

## ۱. مقدمه  
در این پروژه، چهار دکمه به آردوینو متصل شده‌اند و با فشار دادن هر دکمه، یک نت موسیقی خاص پخش می‌شود..



## ۳. قطعات مورد استفاده  
- برد آردوینو Uno  
- چهار دکمه (Push Button)  
- یک buzzer (سیم‌پیچ صوتی)  
- چهار مقاومت pull-up (مثلاً ۱۰k اهم)  
- برد برد (Breadboard)  
- سیم‌های جامپر (jumper wires)
.

## ۴. نحوه‌ی ساخت مدار  
- **دکمه‌ها**:  
  - هر دکمه → به یکی از پین‌های دیجیتال ۷ تا ۱۰ آردوینو متصل شده است.  
  - هر دکمه با یک مقاومت pull-up (۱۰k اهم) به 5V متصل شده است.  
  - زمین (GND) دکمه به GND آردوینو متصل شده است.  
- **buzzer**:  
  - یک سر → **پین دیجیتال ۱۱** آردوینو  
  - سر دیگر → **GND**



## ۵. کد برنامه (اسکچ):

```cpp
#define T_A 262
#define T_B 294
#define T_C 330
#define T_D 349
#define T_E 392
#define T_F 440
#define T_G 493

const int A = 10;   // تعریف پین دکمه A
const int B = 9;    // تعریف پین دکمه B
const int C = 8;    // تعریف پین دکمه C
const int D = 7;    // تعریف پین دکمه D

const int Buzz = 11; // تعریف پین buzzer

void setup() {
  pinMode(A, INPUT);   // تنظیم پین A به عنوان ورودی
  digitalWrite(A, HIGH); // فعال کردن مقاومت pull-up

  pinMode(B, INPUT);   // تنظیم پین B به عنوان ورودی
  digitalWrite(B, HIGH); // فعال کردن مقاومت pull-up

  pinMode(C, INPUT);   // تنظیم پین C به عنوان ورودی
  digitalWrite(C, HIGH); // فعال کردن مقاومت pull-up

  pinMode(D, INPUT);   // تنظیم پین D به عنوان ورودی
  digitalWrite(D, HIGH); // فعال کردن مقاومت pull-up
}

void loop() {
  // اگر دکمه A فشرده شود → نت A پخش شود
  while (digitalRead(A) == LOW) {
    tone(Buzz, T_A);
  }

  // اگر دکمه B فشرده شود → نت B پخش شود
  while (digitalRead(B) == LOW) {
    tone(Buzz, T_B);
  }

  // اگر دکمه C فشرده شود → نت C پخش شود
  while (digitalRead(C) == LOW) {
    tone(Buzz, T_C);
  }

  // اگر دکمه D فشرده شود → نت D پخش شود
  while (digitalRead(D) == LOW) {
    tone(Buzz, T_D);
  }

  // اگر هیچ دکمه‌ای فشرده نشود → buzzer خاموش شود
  noTone(Buzz);
}
```

### توضیح کد:  

- `const int A = 10;` — تعریف پین دکمه A.  
- `pinMode(A, INPUT);` — تنظیم پین A به عنوان ورودی.  
- `digitalWrite(A, HIGH);` — فعال کردن مقاومت pull-up.  
- `while (digitalRead(A) == LOW)` — اگر دکمه A فشرده شود، نت A پخش شود.  
- `tone(Buzz, T_A);` — پخش نت A با فرکانس مشخص.  
- `noTone(Buzz);` — خاموش کردن buzzer وقتی هیچ دکمه‌ای فشرده نشود.

## ۶. نحوه‌ی کارکرد  
- پس از آپلود کد، با فشار دادن هر دکمه، نت مربوطه پخش می‌شود.  
- اگر دکمه‌ای فشرده شود، buzzer نت مربوطه را پخش می‌کند.  
- اگر دکمه را رها کنید، buzzer خاموش می‌شود.

## ۷. نتایج  
buzzer به درستی نت‌های موسیقی را با فشار دادن دکمه‌ها پخش می‌کند.
