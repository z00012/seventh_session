### ساختار مدار پخش صدا با آردوینو
## هدف
هدف این آزمایش، طراحی مداری است که با استفاده از آردوینو و دکمهها بتواند صداهای مختلفی را در فرکانسهای متفاوت
پخش کند . هر دکمه نشاندهندهی یک نت موسیقی است که با فشار دادن آن صدا از پین خروجی آردوینو پخش میشود .
## مواد و ابزار لازم
برد آردوینو
بلندگو یا بازر (Buzzer) ۴ عدد دکمه فشاری
سیمهای اتصال
مقاومتهای مناسب
## نحوه بستن آزمایش
در این آزمایش، چهار دکمه فشاری به پینهای دیجیتال آردوینو متصل شدهاند تا نتهای مختلف موسیقی را ایجاد کنند . مراحل اتصال به شرح زیر است : 1. اتصال دکمهها به آردوینو : - پینهای A ، B ، C ، و D به ترتیب به پینهای دیجیتال 5 ، 6 ، 7 ، و 8 آردوینو متصل میشوند . - هر دکمه به صورت pull-up داخلی تنظیم شده، به این معنی که در حالت عادی پین ورودی HIGH است و زمانی که دکمه فشرده شود، به LOW تغییر میکند . 2. اتصال بازر (Buzzer): - پایه مثبت بازر به پین دیجیتال 11 آردوینو (Burr) متصل میشود و پایه منفی به زمین (GND). با این اتصالات، با فشردن هر دکمه، فرکانس مشخصی به بازر اعمال میشود که صدای مربوط به هر نت را ایجاد میکند .
## کد
```
#define T_C 262
#define T_D 294
#define T_E 330
#define T_F 349
#define T_G 392
#define T_A 440
#define T_B 493
const int A = 5;
const int B = 6;
const int C = 7;
const int D= 8;
const int Burr = 11;


void setup() {
 
    pinMode(A, INPUT);
    digitalWrite(A, HIGH);
    pinMode(B, INPUT);
    digitalWrite(B, HIGH);
    pinMode(C, INPUT);
    digitalWrite(C, HIGH);
    pinMode(D, INPUT);
    digitalWrite(D, HIGH);
  }


void loop() {

  while (digitalRead(A) == LOW) {
    tone(Burr,T_C);
  }
  while (digitalRead(B) == LOW) {
    tone(Burr,T_D);
  }
  while (digitalRead(C) == LOW) {
    tone(Burr,T_E);
  }
  while (digitalRead(D) == LOW) {
    tone(Burr,T_F);
  }
  noTone(Burr);
}



```
## توضیحات کد
1. تعریف فرکانس نتها : در کد، نتهای موسیقی به صورت ثابتهای #define تعریف شدهاند که فرکانس مربوط به هر نت
را مشخص میکند .
```
#define T_C 262
#define T_D 294
#define T_E 330
#define T_F 349
#define T_G 392
#define T_A 440
#define T_B 493
 ```
3. تنظیم پینها در :setup پینهای A ، B ، C و D به عنوان ورودی تعریف شدهاند و به حالت pull-up داخلی تنظیم شدهاند .
```
 void setup() {
pinMode(A, INPUT);
digitalWrite(A, HIGH);
pinMode(B, INPUT);
digitalWrite(B, HIGH);
pinMode(C, INPUT);
digitalWrite(C, HIGH);
pinMode(D, INPUT);
digitalWrite(D, HIGH); }
```
5. پخش صدا در تابع loop: این تابع، وضعیت دکمهها را بررسی میکند و در صورت فشرده شدن هر دکمه، با استفاده از
تابع tone صدای مربوط به فرکانس آن نت را از طریق بازر پخش میکند .
```
void loop() {
 while (digitalRead(A) == LOW) {
 tone(Burr, T_C); }
 while (digitalRead(B) == LOW) {
tone(Burr, T_D); }
while (digitalRead(C) == LOW) {
 tone(Burr, T_E); }
while (digitalRead(D) == LOW) {
 tone(Burr, T_F); } noTone(Burr); }
 ```
## نتیجه
با استفاده از این کد و مدار، هر دکمه که فشرده میشود، نت مربوط به آن فرکانس در بازر پخش میشود . این پروژه نشان
دهندهی نحوه ایجاد صداهای مختلف با آردوینو است .
