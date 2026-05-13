# Ancient Scripts Converter
[![PyPI Downloads](https://static.pepy.tech/personalized-badge/ancientlinesoftheworld?period=total&units=INTERNATIONAL_SYSTEM&left_color=BLACK&right_color=GREEN&left_text=downloads)](https://pepy.tech/projects/ancientlinesoftheworld)

📜 A Python package for converting text to ancient writing systems

## How It Works / نحوه کارکرد

The converter works **character by character** using **mapping dictionaries**.  
مبدل به صورت **حرف به حرف** و با استفاده از **دایره‌المعارف‌های نگارشی** کار می‌کند.
# Text Conversion Flow

```
Input Text
│
▼
[Iterate Character by Character]
│
▼
[Check Character Type]
├─ Persian Letter → Persian Mapping Dictionary
├─ English Letter → English Mapping Dictionary
├─ Number → Number Mapping Dictionary
└─ Symbol → Symbol Mapping Dictionary
│
▼
[Convert or Keep Original]
│
▼
Output Text in Ancient Script
```


### Explanation / توضیح مرحله به مرحله:

1. **Character Mapping / نگاشت حروف**  
   - Each ancient script has its own dictionary mapping **Persian, English, numbers, and symbols**.  
     هر خط باستانی دارای دیکشنری مخصوص خود است که **حروف فارسی، انگلیسی، اعداد و علائم** را به نمادهای مربوطه تبدیل می‌کند.

2. **Conversion / تبدیل**  
   - Iterate through each character of the input text.  
   - Replace it with the mapped symbol from the dictionary.  
   - If a character is not found, keep it unchanged.  
   - هر حرف متن ورودی بررسی می‌شود، جایگزین نماد متناظر می‌شود، و اگر در دیکشنری نبود، بدون تغییر باقی می‌ماند.

3. **Supported Types / انواع پشتیبانی شده**  
   - Persian letters / حروف فارسی  
   - English letters / حروف انگلیسی  
   - Numbers / اعداد  
   - Some punctuation and symbols / برخی علائم نگارشی و سمبل‌ها

4. **Optimized Scripts / خطوط بهینه شده**  
   - Some scripts like **Linear B** or **Oracle Bone** use optimized mappings for **faster and more accurate conversion**.  
     برخی خطوط مانند **خط ب یا اوراکل بون** دارای **دایره‌المعارف بهینه** برای تبدیل سریع‌تر و دقیق‌تر هستند.

## Installation
```bash
pip install --upgrade  ancientlinesoftheworld
```

## Usage
```python

from   ancient import AncientScripts

converter = AncientScripts()

#  تبدیل  متن به خط باستانی میخی
cuneiform_text = converter.cuneiform("سلام")

print(cuneiform_text)

# تبدیل متن به خط باستانی مصری 
hieroglyph_text = converter.hieroglyph("خدا")

print(hieroglyph_text)

# تبدیل متن  تاریخی اوستایی

avesta = converter.avestan("hiسلام")
print(avesta)

print(converter.get_supported_scripts())

brahmi = converter.brahmi ("HI سلام")

print(brahmi)
kharosthi = converter.kharosthi("hiسلام")

print(kharosthi)

runic = converter.runic("hello سلام")
print(runic)
```

## Project :
```python

from ancient import AncientScripts, AncientTimeline

# ایجاد نمونه از کلاس اصلی
c = AncientScripts()

# ایجاد تایم‌لاین با خط پهلوی
t = AncientTimeline(script='pahlavi')

print("🕊️ Welcome to AncientLinesOfTheWorld 🏛️")
print("=" * 60)
print("🔹 Supported Ancient Scripts:")
for name, desc in c.get_supported_scripts().items():
    print(f"  - {name:<12} → {desc}")
print("=" * 60)


text = "hi"
print(f"\nOriginal text: {text}\n")

print("🪶 Converted Texts:")
print(f"  🔸 Pahlavi:       {c.pahlavi(text)}")
print(f"  🔸 Akkadian:      {c.akkadian(text)}")
print(f"  🔸 Avestan:       {c.avestan(text)}")
print(f"  🔸 Manichaean:    {c.manichaean(text)}")
print(f"  🔸 Linear B:      {c.linear_b(text)}")
print(f"  🔸 Hebrew:        {c.hebrew(text)}")
print(f"  🔸 Hieroglyph:    {c.hieroglyph(text)}")
print(f"  🔸 Sanskrit:      {c.sanskrit(text)}")
print(f"  🔸 Oracle Bone:   {c.oracle_bone(text)}")
print(f"  🔸 : cuneiform :  {c.cuneiform(text)}")
print(f"  🔸 brahmi :  {c.brahmi (text)}")
print(f"   runic:{c.runic(text)}")
print(f"   kharosthi:{c.kharosthi(text)} ")

print("\n" + "=" * 60)

# 🕰️ نمایش زمان زنده با خط پهلوی
print("📜 Real-time Ancient Timeline (Pahlavi Script):")
t.show()

print("=" * 60)
print("💫 Powered by AncientLinesOfTheWorld | Created by AmirHosseinPython")
```

## generate image
تولید تصاویر با خطوط باستانی | Generate Images with Ancient Scripts
این کلاس متن شما را به خط باستانی مورد نظر تبدیل کرده و روی یک تصویر پس‌زمینه قرار می‌دهد. خروجی نهایی یک تصویر زیبا با متن باستانی است که در پوشه پروژه شما ذخیره می‌شود
English:
This class converts your text into the desired ancient script and places it on a background image. The final output is a beautiful image with ancient text, saved in your project directory.
⚙️ پارامترهای constructor | Constructor Parameters

پارامتر	نوع	پیش‌فرض	توضیح
script	str	"cuneiform"	خط باستانی مورد نظر (cuneiform)
log_level	int	logging.INFO	سطح لاگ‌گیری برای دیباگ
پارامتر های ورودی این کلاس:
text =اجباری
متنی که می‌خواهید به خط باستانی تبدیل شود
output_filename=اختیاری
نام دلخواه برای فایل خروجی. اگر خالی بماند، خودکار ساخته می‌شود
rtl=اختیاری
اگر True باشد، متن راست‌به‌چپ نوشته می‌شود 
enhance_contrast=اختیاری
اگر True باشد، رنگ متن با توجه به پس‌زمینه تنظیم می‌شود
text_color=اختیاری
رنگ دلخواه به صورت RGB. مثال: (255,0,0) برای قرمز

## ساده‌ترین حالت
```python
from ancient import AncientImageGenerator

# ساخت شیء از کلاس و تعیین نوع خط
generator = AncientImageGenerator(script="cuneiform")

# متنی که می‌خوای تبدیل بشه
text = "تمدن از اینجا آغاز شد"

# تولید تصویر با متن باستانی
output_image = generator.generate_image(text)

print(f"📜 تصویر آماده شد و در این مسیر ذخیره شد:\n{output_image}")

```
## با نام دلوخواه
```python
gen.generate_image(
    "متن باستانی", 
    output_filename="my_ancient_text.png"
)



```
با رنگ طلایی و کنتراست خودکار
```python
gen.generate_image(
    "شاهکار تاریخ",
    text_color=(255, 215, 0),  # طلایی
    enhance_contrast=True
)
```

پاک کردن کش های که استفاده شده:
```python
gen.clear_font_cache()
```
رنگ‌های پرکاربرد | Common Colors:
text_color=(255, 0, 0)    # 🔴 قرمز | Red
text_color=(0, 255, 0)    # 🟢 سبز | Green
text_color=(0, 0, 255)    # 🔵 آبی | Blue
text_color=(255, 255, 0)  # 🟡 زرد | Yellow
text_color=(255, 0, 255)  # 🟣 بنفش | Magenta
text_color=(0, 255, 255)  # 🔷 فیروزه‌ای | Cyan
text_color=(0, 0, 0)      # ⚫ مشکی | Black
text_color=(255, 255, 255) # ⚪ سفید | White
text_color=(255, 215, 0)   # 🏆 طلایی | Gold
text_color=(192, 192, 192) # ⚪ نقره‌ای | Silver
text_color=(128, 0, 128)   # 🟣 ارغوانی | Purple
text_color=(255, 165, 0)   # 🟠 نارنجی | Orange
#  AncientTimeline

کلاس `AncientTimeline` برای **نمایش زمان فعلی به خطوط باستانی** (میخی، پهلوی، منیایی، هیروگلیف، اکدی، اوراکل بون، اوستایی) طراحی شده است.

### ⚙️ پارامترها

| پارامتر | نوع | توضیح |
|---------|-----|-------|
| `script` | `str` | خط باستانی برای نمایش (`'cuneiform'`, `'pahlavi'`, `'manichaean'`, `'hieroglyph'`, `'akkadian'`, `'oracle_bone'`, `'avestan'`) |
| `ancient_format` | `bool` | اگر `True` باشد، تاریخ به سبک باستانی نمایش داده می‌شود |

### 🖥️ نمونه استفاده

# 🏺 AncientTimeline

کلاس `AncientTimeline` برای **نمایش زمان فعلی به خطوط باستانی** (میخی، پهلوی، منیایی، هیروگلیف، اکدی، اوراکل بون، اوستایی) طراحی شده است.

### ⚙️ پارامترها

| پارامتر | نوع | توضیح |
|---------|-----|-------|
| `script` | `str` | خط باستانی برای نمایش (`'cuneiform'`, `'pahlavi'`, `'manichaean'`, `'hieroglyph'`, `'akkadian'`, `'oracle_bone'`, `'avestan'`) |
| `ancient_format` | `bool` | اگر `True` باشد، تاریخ به سبک باستانی نمایش داده می‌شود |

### 🖥️ نمونه استفاده

```python
from ancient import AncientTimeline

timeline = AncientTimeline(script='pahlavi', ancient_format=True)

print(timeline.as_text())  # دریافت زمان فعلی به صورت متن
timeline.show()            # نمایش زمان روی کنسول


```
## 🔑 پیش‌نیاز

برای استفاده از این کلاس شما نیاز دارید:

1. ثبت‌نام در لیارا و دریافت **API Key**:
   [https://console.liara.ir/ai](https://console.liara.ir/ai)

   

## AncientScriptAI :
| پارامتر               | نوع    | توضیح                                                               |
| --------------------- | ------ | ------------------------------------------------------------------- |
| `user_input`          | `str`  | متن ورودی کاربر که می‌خواید به زبان باستانی پاسخ داده شود           |
| `script`              | `str`  | زبان باستانی هدف (یکی از `SUPPORTED_SCRIPTS`)                       |
| `include_translation` | `bool` | اگر `True` باشد، خروجی شامل **ترجمه فارسی و انگلیسی** نیز خواهد بود |


```python
from ancient import  AncientScriptAI

# وارد کردن توکن API خود
api_key = ""
ai_bot =  AncientScriptAI(api_key=api_key,ase_url= "")

# متن ورودی کاربر
text = "سلام باستانی"
script = "cuneiform"


# گرفتن پاسخ AI
response = ai_bot.get_ancient_response(text, script)
print(response)



```


## AncientAnimator



AncientAnimator converts input text into ancient scripts and displays the result as an
animated, character-by-character output.

It simulates real-time writing by rendering each character with a configurable delay.
The animation can be shown directly in the terminal or streamed through a callback function,
making it suitable for CLI tools, GUI applications, and web-based environments.

---



AncientAnimator متن ورودی را به خط‌های باستانی تبدیل کرده و خروجی را به‌صورت انیمیشنی،
کاراکتر به کاراکتر نمایش می‌دهد.

این کلاس فرآیند «نوشتن تدریجی» را شبیه‌سازی می‌کند و می‌تواند خروجی را مستقیماً در ترمینال
نمایش دهد یا از طریق یک تابع callback در GUI یا وب استفاده شود.

---

## Parameters | پارامترها

- **text**  
  - English: Input text to be converted  
  - فارسی: متن ورودی برای تبدیل

- **script**  
  - English: Target ancient script  
  - فارسی: خط باستانی مقصد

- **delay**  
  - English: Delay between each character (in seconds)  
  - فارسی: تأخیر بین هر کاراکتر (بر حسب ثانیه)

- **output_func**  
  - English: Optional callback function for receiving animated output step-by-step  
  - فارسی: تابع callback اختیاری برای دریافت خروجی انیمیشنی به‌صورت مرحله‌ای

---

## Example – Terminal | مثال – ترمینال

```python
from ancient  import AncientAnimator

animator = AncientAnimator(delay=0.1)

animator.run(
    text="Hello World",
    script="pahlavi"
)

```
## Example – Callback | مثال – با Callback

```python
from ancient import AncientAnimator

def output_callback(chunk: str):
    print(chunk)

animator = AncientAnimator(delay=0.05)

animator.run(
    text="HI",
    script="cuneiform",
    output_func=output_callback
)


```

## مثال ها
```python
from ancient import AncientAnimator

anim = AncientAnimator(delay=0.1)
anim.run("hello amirhossin", "cuneiform")

```
## مثال تحت وب
```python

from flask import Flask,jsonify,request,Response
from ancient import AncientAnimator
import time
app = Flask(__name__)

anim = AncientAnimator(delay=0.1)


def generate():
    converted = anim.convert("سلام به وب", "cuneiform")
    full = ""
    for ch in converted:
        full += ch
        yield f"data: {full}\n\n"
        time.sleep(0.1)
    
    


@app.route('/stream')
def stream():
    return Response(generate(), mimetype='text/event-stream')

app.run()



```
```python
import tkinter as tk
from ancient import AncientAnimator

def update_label(text):
    label.config(text=text)
    root.update()

root = tk.Tk()
root.title("انیمیشن")
root.geometry("500x300")

label = tk.Label(root, text="", font=("Courier", 20), wraplength=450)
label.pack(pady=50)

def start():
    anim = AncientAnimator(delay=0.1)
    anim.run("hello amirhossin", "cuneiform", output_func=update_label)

btn = tk.Button(root, text="شروع", command=start, font=("Arial", 14))
btn.pack()

root.mainloop()
```




# 🌐 بخش WebApp — کلاس `AncientWeb`

کلاس **`AncientWeb`** یکی از قابلیت‌های منحصربه‌فرد کتابخانه `ancientlinesoftheworld` است.  
این کلاس یک **وب‌اپلیکیشن لوکال** فراهم می‌کند که به شما اجازه می‌دهد متن‌ها را به **خطوط باستانی** تبدیل کنید، بدون نیاز به هاست یا سرور خارجی.

---


## 🎯 وظیفه کلاس

- اجرای خودکار یک **وب‌اپ Flask** روی سیستم شما  
- نمایش رابط کاربری ساده و کاربرپسند  
- پشتیبانی از **تمام خطوط باستانی موجود در کتابخانه**  
- امکان استفاده آفلاین و لوکال  
- مناسب برای تست، دمو یا استفاده شخصی و آموزشی  

---

## 🚀 نمونه استفاده

```python
from ancient  import AncientWeb

# ایجاد نمونه کلاس
app = AncientWeb(version="2.5.0")

# اجرای وب‌اپ لوکال
app.run_app()

```

## 📚 لیست کلاس‌های کتابخانه و قابلیت‌های آن‌ها:

| ردیف | کلاس | قابلیت |
| :--- | :--- | :--- |
| 1 | **AncientScripts** | تبدیل متن فارسی و انگلیسی به ۱۵+ خط باستانی (میخی، هیروگلیف، پهلوی، اوستایی، رونی، ایلامی، فنیقی و...) |
| 2 | **AncientTimeline** | نمایش زمان فعلی به خطوط باستانی (میخی، پهلوی، اوستایی و...) |
| 3 | **AncientImageGenerator** | تولید تصاویر با کیفیت بالا از خطوط باستانی (قابل تنظیم رنگ، سایه و کنتراست) |
| 4 | **AncientAnimator** | انیمیشن نوشته شدن خطوط باستانی حرف به حرف با قابلیت تنظیم سرعت |
| 5 | **AncientWeb** | وب اپ محلی آفلاین برای تبدیل متن به خطوط باستانی (بدون نیاز به سرور) |
| 6 | **AncientAIWeb** | وب اپ هوشمند ترکیبی (ساخت تصویر + تحلیل عکس با هوش مصنوعی) |
| 7 | **AncientScriptAI** | چت هوشمند با هوش مصنوعی به خطوط باستانی |
| 8 | **AncientReverseAI** | ترجمه مفهومی خطوط باستانی به فارسی و انگلیسی با هوش مصنوعی |
| 9 | **AnalyzePhoto** | تشخیص و ترجمه خطوط باستانی از روی عکس با هوش مصنوعی |
| 10 | **Plugin / Plagine** | ساخت خطوط باستانی جدید بدون تغییر در کد اصلی (سیستم پلاگین) |
| 11 | **SpeechToAncient** | تبدیل گفتار (ضبط صدا یا فایل صوتی) به خطوط باستانی |
| 12 | **AncientDocs** | سایت داکیومنت کتابخانه برای مستندات |
| 13 | **AncientBot** | ربات پیام رسان برای تبدیل متن به خطوط باستانی|
## 🔁 AncientReverseAI  
### AI-Powered Ancient Script → Persian & English Translator  
### مبدل هوشمند خطوط باستانی به فارسی و انگلیسی

`AncientReverseAI` is an advanced and **unique AI-based module** designed to translate  
**ancient scripts into meaningful Persian and English text**.

`AncientReverseAI` یک ماژول پیشرفته و منحصربه‌فرد است که با استفاده از **هوش مصنوعی معنایی**،  
متون باستانی را به **فارسی و انگلیسی قابل فهم** تبدیل می‌کند.

## ✨ Key Features | ویژگی‌ها

- 🧠 AI-based semantic translation  
  ترجمه هوشمند و مفهومی با هوش مصنوعی

- 📜 Supports multiple ancient writing systems  
  پشتیبانی از خطوط باستانی متنوع

- 🌍 Dual output: Persian & English  
  خروجی همزمان فارسی و انگلیسی

- 🧩 Context-aware translation (not literal)  
  درک جمله و معنا، نه ترجمه سطحی

- 🔌 Requires Internet & API Key  
  نیازمند اینترنت و کلید API

## ⚠️ Important Notes | نکات مهم
This is conceptual & historical translation, not glyph decoding
این ترجمه مفهومی است، نه صرفاً بازگردانی کاراکتر

Multiple interpretations may exist for ancient texts
ممکن است یک متن باستانی چند تفسیر معتبر داشته باشد

Best results with complete sentences
بهترین نتیجه با متون کامل و پیوسته حاصل می‌شود
## 🗂️ Supported Scripts | خطوط پشتیبانی‌شده

| # | Script | خط | Civilization |
|:--|:-------|:---|:-------------|
| 1 | Cuneiform | میخی | Achaemenid, Mesopotamia |
| 2 | Pahlavi | پهلوی | Sassanian Iran |
| 3 | Manichaean | منیایی | Mani Faith |
| 4 | Hieroglyph | هیروگلیف | Ancient Egypt |
| 5 | Akkadian | اکدی | Mesopotamia |
| 6 | Oracle Bone | استخوان پیشگویی | Ancient China |
| 7 | Avestan | اوستایی | Zoroastrian |
| 8 | Linear B | خط B | Ancient Greece |
| 9 | Kharosthi | خروشتی | North India |
| 10 | Runic | رونی | Vikings |
| 11 | Brahmi | براهمی | Ancient India |
| 12 | Hebrew | عبری | Ancient Hebrew |
| 13 | Sanskrit | سانسکریت | Ancient India |
| 14 | Elamite 🆕 | عیلامی | Elamite Civilization (Iran) |
| 15 | Phoenician 🆕 | فنیقی | Mother of Alphabets |


## 🚀 Usage Example | نمونه استفاده
```python
from ancient import AncientReverseAI

ai = AncientReverseAI(api_key="YOUR_API_KEY",base_url= "")

ancient_text = "𒀀𒁀𒂊"

result = ai.translate(
    text=ancient_text,
    script="cuneiform"
)

print(result)

```
# AnalyzePhoto - تحلیل‌گر خطوط باستانی


## این کلاس چه کاری انجام می‌دهد؟ 
توجه:
خروجی توسط هوش مصنوعی تولید می‌شود و احتمال خطا وجود دارد.
این نسخه اولیه کلاس و صرفاً در حد تست است.




یک تصویر از خط باستانی دریافت می‌کند و برمی‌گرداند:

- نوع خط (مثلاً میخی، هیروگلیف، پهلوی)
- تحلیل ظاهری حروف و نمادها
- یک تفسیر روان و کامل از متن (حتی اگر ناقص باشد)
- ترجمه فارسی و انگلیسی
## نحوه استفاده

```python
from ancient import AnalyzePhoto

img = AnalyzePhoto(
    base_url='',
    api_key='',
    
)



print(img.analyze_image('test.png'))

```
## کلاس AncientAIWeb
وب اپ هوشمند ترکیب کلاس های :
AncientImageGenerator
AnalyzePhoto
برای ساخت تصویر وتحلیل عکس باهوش مصنوعی 
ودانلود تصویر

```python
from ancient import AncientAIWeb

api = ""

url = "https://api.gapgpt.app/v1"
web = AncientAIWeb(
    api_key=api,
    base_url=url
)

## ورودی های تنظیمات برای شخصی سازی ظاهر عکس

web.set_config(
    enhance_contrast=True,
    text_color=(255, 215, 2),
    rtl=True,
    
    
    
    
)

web.run_app(port=8000)


```

## کلاس :Plugin 
## 🎯 سیستم پلاگین (Plugin System)
بدون تغییر در کد اصلی، خطوط باستانی خودت را بساز باکمک کلاس
Plugin
## راهنمای کامل کلاس‌ :Plugin
کلاس اصلی برای ساخت پلاگین‌های جدید.
سازنده (Constructor)
```python
Plugin:(
    mapping: Dict[str, str],     # اجباری - دیکشنری نگاشت حروف
    script_name: str,            # اجباری - نام خط (با همین نام صدا زده می‌شود)
    description: str = "",       # اختیاری - توضیحات خط
    author: str = ""             # اختیاری - نام سازنده
)

```
متدها

```
created_script()ساخت و ثبت نهایی پلاگین
p.created_script()
```
## کلاس AncientScripts
متدها
```
get_supported_scripts()لیست همه خطوط (اصلی + پلاگین)
converter.get_supported_scripts()
```
## مثال های کامل از ثبت خط جدید
```python
from ancient import Plugin,AncientScripts

mapping = {
    'ا': '𒀀',
    'ب': '𒁀',
    'س': '𒊓',
}


plugin = Plugin(
    mapping=mapping,
    description="script",
    author="اسم سازنده خط",
    script_name="my_script"
)
# برای ایجاد
plugin.created_script()

c = AncientScripts()

print(c.my_script())

```

## قابلیت تبدیل صوت به متن وتبدیل متن به خطوط باستانی
## کلاس :SpeechToAncient
کلاس SpeechToAncient
این کلاس، صدای کاربر را از طریق میکروفون ضبط می‌کند، سپس با استفاده از هوش مصنوعی، صدای ضبط‌شده را به متن تبدیل می‌نماید. در مرحله بعد، متن حاصل از گفتار شما را تحلیل کرده و در نهایت به خطوط باستانی تبدیل می‌کند.
ودرنوع دیگه اش ورودی فایل صوت شمارو میگیره وتحلیل میکنه

```python
from ancient import SpeechToAncient,AncientScripts


stt = SpeechToAncient(
    api_key="",
    script="pahlavi",
    base_url=""
    
    
)

result = stt.to_ancient(duration=5)
print(f"🏛️ خط میخی: {result}")

result2 = stt.from_file("my_voice.mp3")

print(result2)
```
## کلاس سایت داکیومنت :AncientDocs
برای دیدن سایت به صورت لوکال که هرزمان نسخه جدید منتشربشه این سایت هم بروزمیشه


```python
from ancient import AncientDocs




doc = AncientDocs()




doc.run()
```
## کلاس:AncientBot

ربات هوشمند تبدیل متن به خطوط باستانی برای پیام‌رسان‌های تلگرام و روبیکا

کاس AncientBot یک رابط کاربری ساده و قدرتمند برای استفاده از کتابخانه AncientLinesOfTheWorld در پیام‌رسان‌های تلگرام و روبیکا است.
## نحوه کار
کاربر در ربات دستور باستانی متن خود را ارسال می‌کند

ربات متن را به خط باستانی تبدیل می‌کند

ربات از خط باستانی یک تصویر طلایی با کیفیت بالا می‌سازد

ربات متن و تصویر را برای کاربر ارسال می‌کند

## آماده‌سازی توکن

برای تلگرام روبیکا :
به این ایدی پیام رسان برید:@BotFather
## روش استفاده

```python
from ancient import AncientBot

# ساخت ربات با خط میخی
bot = AncientBot(script="cuneiform")

# اجرا با توکن تلگرام
bot.run_telegram("")
#_______________________________
#اجرا برای ربات روبیکا
bot.run_rubika("")
```

## یاداشت علمی درباره این پروژه:





**1. سایت علمی civilica**
   [https://civilica.com/note/17282/](https://civilica.com/note/17282/)
   




```bash
pip install --upgrade  ancientlinesoftheworld
```


```bash
pip install -i https://mirror-pypi.runflare.com/simple --upgrade  ancientlinesoftheworld
```
