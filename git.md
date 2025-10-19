حتماً! 😊 بیایم یه **خلاصه کامل و مرحله‌به‌مرحله** از اون چیزی که تا الان انجام دادی، با توضیح هر دستور، داشته باشیم:

---

## ۱️⃣ مقداردهی اولیه ریپازیتوری

تو پوشه پروژه‌ت (`project1`) این دستور رو زدی:

```bash
git init
```

* Git یه مخزن جدید داخل پوشه ایجاد کرد (`.git`)
* از این به بعد می‌تونی تغییرات فایل‌ها رو پیگیری کنی.

---

## ۲️⃣ ساخت فایل جدید

ایجاد یه فایل به اسم `readme.txt` با محتوا:

```bash
echo Hello Git! > readme.txt
```

* توی این فایل نوشتیم `"Hello Git!"`
* فایل آماده شد ولی هنوز Git نمی‌دونه باید پیگیریش کنه.

---

## ۳️⃣ اضافه کردن فایل به staging area

```bash
git add readme.txt
```

* فایل رو به **staging area** اضافه کردی
* یعنی آماده شد برای commit بعدی.
* بررسی وضعیت با:

```bash
git status
```

خروجی می‌گه فایل آماده commit هست.

---

## ۴️⃣ تنظیم نام و ایمیل کاربر

قبل از اولین commit، Git باید بدونه کی تغییرات رو ثبت می‌کنه:

```bash
git config user.name "mahdyram"
git config user.email "mahdyramshini@gmail.com"
```

* این فقط برای همین پروژه بود (اگه `--global` می‌ذاشتی، برای همه پروژه‌ها اعمال می‌شد).

---

## ۵️⃣ ساخت اولین commit

```bash
git commit -m "readme file created"
```

* commit واقعی ساخته شد و فایل `readme.txt` ذخیره شد.
* پیام commit هم `"readme file created"` بود.

---

## ✅ بررسی وضعیت بعد از commit

```bash
git status
```

* خروجی:

```
On branch master
nothing to commit, working tree clean
```

* یعنی همه چیز ذخیره شده و هیچ تغییر جدیدی برای commit وجود نداره.

---

💡 نکته:

* `.git` → مخفی، همه تاریخچه و تنظیمات پروژه توش ذخیره میشه.
* `staging area` → جایی که فایل‌ها قبل از commit آماده می‌شن.
* commit → یه snapshot از پروژه با پیام توضیحی.

<!-- -------------------------------------------- -->
<hr style="height:5px; background-color:red" />
<!-- -------------------------------------------- -->

عالی 👏 تغییر فایل توسط ادیتور انجام شده و Git این تغییر رو شناسایی کرده ✅

بیای توضیح بدیم خروجی `git status` که دیدی یعنی چی:

---

### 🔍 تحلیل خروجی

```
Changes not staged for commit:
	modified:   readme.txt
```

* یعنی فایل `readme.txt` تغییر کرده ولی هنوز **به staging area اضافه نشده**.
* Git هنوز نمی‌دونه می‌خوای این تغییرات رو در commit بعدی ذخیره کنی یا نه.

```
no changes added to commit (use "git add" and/or "git commit -a")
```

* یعنی فعلاً هیچ چیزی آماده commit نیست.

---

### 🔧 راه‌های بعدی

#### ۱️⃣ اضافه کردن تغییرات به staging (معمول‌ترین روش)

```bash
git add readme.txt
```

* بعدش commit می‌کنی:

```bash
git commit -m "Update readme file"
```

#### ۲️⃣ یا مستقیم commit کردن همه تغییرات بدون `git add`

```bash
git commit -am "Update readme file"
```

* حرف `-a` یعنی همه فایل‌های **tracked** که تغییر کردن رو مستقیماً commit کن
* حرف `-m` هم پیام commit رو مشخص می‌کنه.

<!-- -------------------------------------------- -->
<hr style="height:5px; background-color:red" />
<!-- -------------------------------------------- -->

عالی 👏 الان تاریخچه commit‌هات رو دیدی و همه چیز درست ثبت شده ✅

بیای توضیح بدیم که چی دیدی:

---

### 🔍 تحلیل خروجی `git log`

```
commit a04f3a98bf7d91b7f023770851ac147b3a334265 (HEAD -> master)
Author: mahdyram <mahdyramshini@gmail.com>
Date:   Mon Oct 13 02:24:23 2025 +0330

    added my name to the readme file
```

* `a04f3a9...` → شناسه (hash) commit، هر commit یه کد یکتا داره
* `HEAD -> master` → یعنی این commit آخرین commit روی شاخه master هست
* `Author` → کی این commit رو زده
* `Date` → زمان commit
* پیام commit → `"added my name to the readme file"`

---

```
commit ac92aacb76a2738e391b37214bdfcfcdc62b28e5
Author: mahdyram <mahdyramshini@gmail.com>
Date:   Mon Oct 13 02:13:27 2025 +0330

    readme file created
```

* این هم **اولین commit پروژه** هست
* پیامش `"readme file created"` بود

---

💡 نکته‌ها:

* هر commit یک snapshot از پروژه‌ت هست
* HEAD همیشه روی **آخرین commit** قرار داره
* می‌تونی با `git log --oneline` یک نمای خلاصه و کوتاه از commit‌ها ببینی

<!-- -------------------------------------------- -->
<hr style="height:5px; background-color:red" />
<!-- -------------------------------------------- -->

خیلی سؤال خوبیه! 👍 تفاوت این دو دستور ظریف ولی مهمه:

---

### ۱️⃣ `git add .`

* همه‌ی **فایل‌های جدید و تغییر یافته در پوشه‌ی فعلی و زیرپوشه‌ها** رو اضافه می‌کنه.
* **اما فایل‌های حذف شده** رو **اضافه نمی‌کنه**.
* مثال:

  * `readme.txt` تغییر کرده → اضافه میشه ✅
  * `page1.html` جدید → اضافه میشه ✅
  * `oldfile.txt` حذف شده → اضافه نمیشه ❌

---

### ۲️⃣ `git add -A` یا `git add --all`

* همه چیز رو اضافه می‌کنه:

  1. فایل‌های **جدید**
  2. فایل‌های **تغییر یافته**
  3. فایل‌های **حذف شده**
* یعنی staging area دقیقاً همون چیزی میشه که توی دایرکتوری پروژه داری.

---

### 🔹 جمع‌بندی سریع

| دستور        | شامل چه چیزهایی می‌شود؟                    |
| ------------ | ------------------------------------------ |
| `git add .`  | تغییرات + فایل‌های جدید                    |
| `git add -A` | تغییرات + فایل‌های جدید + فایل‌های حذف شده |

---

💡 نکته:
اگر خواستی commit بعدی دقیقاً همه چیز رو با همان وضعیت پوشه ثبت کنی، بهتره از `git add -A` استفاده کنی.

<!-- -------------------------------------------- -->
<hr style="height:5px; background-color:red" />
<!-- -------------------------------------------- -->

عالی 👏 داری کاملاً با مفاهیم **staging**, **reset**, و **checkout** آشنا می‌شی!
بیای یک مرور سریع و مرحله‌به‌مرحله از کاری که انجام دادی داشته باشیم:

---

### 🔹 ۱️⃣ مشاهده تفاوت‌ها

```bash
git diff HEAD
```

* نمایش تغییرات **در فایل‌های unstaged** نسبت به آخرین commit
* چون قبل از `git add -A` بود، هنوز چیزی در staging نبود و تغییرات رو می‌دیدی.

---

### 🔹 ۲️⃣ اضافه کردن همه تغییرات به staging

```bash
git add -A
```

* همه فایل‌های تغییر یافته و حذف شده رو آماده commit کردی.

---

### 🔹 ۳️⃣ مشاهده وضعیت staging

```bash
git status
```

* `page1.html` و `page3.html` آماده commit شدن

---

### 🔹 ۴️⃣ مشاهده تفاوت staged files

```bash
git diff --staged
```

* تغییراتی که آماده commit شدن رو نشون می‌ده

---

### 🔹 ۵️⃣ unstaging یک فایل

```bash
git reset page3.html
```

* فقط `page3.html` از staging خارج شد و به حالت **unstaged** برگشت

---

### 🔹 ۶️⃣ لغو تغییرات در working directory

```bash
git checkout -- page3.html
```

* تغییرات `page3.html` کاملاً لغو شد و به حالت آخرین commit برگشت
* اینجوری دیگه روی این فایل تغییری نداشتی

---

### 🔹 ۷️⃣ commit فایل staged

```bash
git commit -m "changing page number page1 from digits to characters"
```

* فقط `page1.html` commit شد
* بعدش `git status` نشون داد همه چیز **clean** هست

---

✅ نتیجه نهایی:

* `page1.html` تغییر داده و commit شد
* `page3.html` بدون تغییر باقی موند
* staging area خالیه و working tree تمیزه

<!-- -------------------------------------------- -->
<hr style="height:5px; background-color:red" />
<!-- -------------------------------------------- -->

حتماً! 😄 بیایم مفصل درباره `git diff` صحبت کنیم، چون خیلی مهمه و بهت کمک می‌کنه تغییرات رو دقیق ببینی.

---

## 🔹 ۱️⃣ مفهوم کلی

`git diff` تغییراتی که بین فایل‌های **working directory**، **staging area** و **commitها** هست رو نمایش می‌ده.

* یعنی قبل از commit یا بعدش، می‌تونی ببینی چه چیزی اضافه، حذف یا تغییر کرده.

---

## 🔹 انواع استفاده

### ۱️⃣ `git diff`

```bash
git diff
```

* تغییراتی که **هنوز به staging اضافه نشده** رو نشون می‌ده
* یعنی فایل‌هایی که تغییر دادن اما با `git add` آماده commit نشدن.

مثال خروجی:

```
diff --git a/readme.txt b/readme.txt
index 8c3f2d1..a7b8c9e 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1 +1 @@
-Hello Git!
+Hello Git! Edited
```

* خط با `-` → حذف شده
* خط با `+` → اضافه شده

---

### ۲️⃣ `git diff --staged` یا `git diff --cached`

```bash
git diff --staged
```

* تغییراتی که **در staging area آماده commit هستن** رو نشون می‌ده
* یعنی تغییراتی که با `git add` اضافه کردی

---

### ۳️⃣ `git diff <commit>` یا `git diff master`

```bash
git diff HEAD
```

* تغییرات **working directory نسبت به آخرین commit** رو نشون می‌ده

```bash
git diff master
```

* تغییرات نسبت به شاخه master (یا هر commit مشخص)

---

### ۴️⃣ تفاوت بین diff و log

* `git log` → تاریخچه commit‌ها
* `git diff` → تغییرات **قبل از commit** یا بین commit‌ها

---

### 🔹 نکته‌ها

* با diff می‌تونی قبل از commit مطمئن بشی که چه چیزی قراره ذخیره بشه.
* خطوط اضافه شده و حذف شده با `+` و `-` مشخص می‌شن.
* برای فایل‌های بزرگ، می‌تونی از `git diff --color-words` استفاده کنی تا تغییرات دقیق‌تر به رنگ نمایش داده بشن.

<!-- -------------------------------------------- -->
<hr style="height:5px; background-color:red" />
<!-- -------------------------------------------- -->

حتماً! 😄 بیاییم یه **چک‌لیست کامل و مرحله‌به‌مرحله از تمام دستورات Git که تا الان استفاده کردی** داشته باشیم، همراه با توضیح کاربرد هر کدوم. اینطوری یه مرجع عالی برای مرور داری:

---

## ۱️⃣ مقداردهی اولیه ریپازیتوری

```bash
git init
```

* ایجاد یک مخزن Git جدید در پوشه پروژه (`.git`)
* شروع پیگیری تغییرات فایل‌ها

---

## ۲️⃣ بررسی وضعیت پروژه

```bash
git status
```

* نشون میده چه فایل‌هایی **تغییر کردن، آماده commit هستن یا هنوز tracked نیستن**

---

## ۳️⃣ ساخت فایل و مشاهده محتوا

```bash
echo "Hello Git!" > readme.txt
cat readme.txt
```

* ساخت فایل متنی و اضافه کردن محتوا
* نمایش محتوا با `cat`

---

## ۴️⃣ اضافه کردن فایل به staging area

```bash
git add readme.txt
git add page1.html page2.html page3.html
git add .
git add -A
```

* `git add <file>` → اضافه کردن یک فایل به staging
* `git add .` → اضافه کردن همه فایل‌های جدید و تغییر یافته در پوشه جاری و زیرپوشه‌ها
* `git add -A` → اضافه کردن **تمام فایل‌های جدید، تغییر یافته و حتی حذف شده**

---

## ۵️⃣ تنظیم نام و ایمیل کاربر

```bash
git config user.name "mahdyram"
git config user.email "mahdyramshini@gmail.com"
```

* Git نیاز داره بدونه کی تغییرات رو ثبت کرده
* `--global` → برای همه پروژه‌ها
* بدون `--global` → فقط برای همین پروژه

---

## ۶️⃣ commit کردن تغییرات

```bash
git commit -m "readme file created"
git commit -m "added my name to the readme file"
git commit -m "changing page number page1 from digits to characters"
git commit -am "Update readme file"
```

* `-m` → پیام commit
* `-a` → همه فایل‌های **tracked** که تغییر کردن رو مستقیم commit می‌کنه

---

## ۷️⃣ مشاهده تاریخچه commit

```bash
git log
git log --oneline
git diff HEAD
git diff --staged
git diff master
```

* `git log` → نمایش کامل تاریخچه commit‌ها
* `git log --oneline` → نمایش خلاصه commit‌ها
* `git diff` → تغییرات **unstaged** نسبت به آخرین commit
* `git diff --staged` → تغییرات **staged** که آماده commit هستن
* `git diff <branch>` → تغییرات نسبت به شاخه یا commit مشخص

---

## ۸️⃣ لغو تغییرات یا unstaging

```bash
git reset page3.html
git checkout -- page3.html
git restore <file>
git restore --staged <file>
```

* `git reset <file>` → فایل از staging خارج می‌شود ولی تغییرات باقی می‌مونه
* `git checkout -- <file>` → تغییرات در working directory به آخرین commit برمی‌گرده
* `git restore` → جایگزین جدید برای checkout برای بازگردانی تغییرات
* `git restore --staged` → unstaging کردن فایل

---

## ۹️⃣ مشاهده فایل‌ها و وضعیت پوشه

```bash
ls
ls -a
cat <file>
```

* `ls` → لیست فایل‌ها
* `ls -a` → نمایش فایل‌های مخفی (مثل `.git`)
* `cat <file>` → نمایش محتوای فایل

---

## 🔹 نکات مهم و مفاهیم کلیدی

* **working directory** → جایی که فایل‌ها رو ویرایش می‌کنیم
* **staging area** → جایی که تغییرات آماده commit ذخیره میشن
* **commit** → snapshot یا تاریخچه ذخیره شده
* `.git` → مخزن مخفی که همه تاریخچه و تنظیمات Git توش ذخیره میشه
* `HEAD` → اشاره به آخرین commit در شاخه فعلی

<!-- -------------------------------------------- -->
<hr style="height:5px; background-color:red" />
<!-- -------------------------------------------- -->

عالی 👏
تو الان عملاً یکی از **اصلی‌ترین چرخه‌های کاری گیت (Git workflow)** رو کامل انجام دادی — از ساخت branch تا merge.
بیایم مثل همیشه، یه **چک‌لیست خلاصه و دقیق از تمام دستوراتی که در این مرحله زدی** بنویسم تا هم برای مرور و هم برای مرجع آینده‌ات کامل داشته باشی 👇

---

## 🧭 چک‌لیست Git تا اینجا

### ✅ مرحله ۱: ساخت و آماده‌سازی مخزن

```bash
git init
```

📘 ایجاد ریپازیتوری محلی (پوشه `.git`)

---

### ✅ مرحله ۲: اضافه کردن و commit اولیه

```bash
git add <file>
git commit -m "readme file created"
```

📘 اضافه کردن فایل‌ها و ساخت اولین snapshot (commit)

---

### ✅ مرحله ۳: ساخت شاخه (branch) جدید

```bash
git branch fixpages
git checkout fixpages
```

📘 ایجاد شاخه جدید به اسم `fixpages` و سوئیچ به اون
(یا معادل کوتاه‌تر: `git checkout -b fixpages`)

---

### ✅ مرحله ۴: اعمال تغییرات در فایل‌ها و مرحله‌بندی (staging)

```bash
git add -A
git reset footer.html
```

📘 همه تغییرات به staging رفتن (`-A` یعنی همه فایل‌های جدید/تغییر یافته/حذف‌شده)
📘 فایل `footer.html` از staging خارج شد (اما هنوز در working directory هست)

---

### ✅ مرحله ۵: commit کردن تغییرات آماده

```bash
git commit -m "adding html and body to pages"
```

📘 تغییرات صفحات (page1 تا page3) commit شدن

---

### ✅ مرحله ۶: اضافه کردن فایل جدید و commit جداگانه

```bash
git add -A
git commit -m "footer added"
```

📘 فایل `footer.html` به staging اضافه و commit شد

---

### ✅ مرحله ۷: مشاهده وضعیت و تاریخچه

```bash
git status
git --no-pager log
git --no-pager branch
```

📘 `git status` → بررسی وضعیت staging و commit
📘 `git log` → مشاهده commitها (بدون pager با `--no-pager`)
📘 `git branch` → بررسی شاخه‌های موجود و شاخه فعلی (`* fixpages`)

---

### ✅ مرحله ۸: سوئیچ بین شاخه‌ها

```bash
git checkout master
git checkout fixpages
```

📘 جابه‌جایی بین شاخه اصلی (`master`) و شاخه‌ی جدید (`fixpages`)

---

### ✅ مرحله ۹: ادغام شاخه‌ها (merge)

```bash
git checkout master
git merge fixpages
```

📘 ادغام تغییرات شاخه `fixpages` در شاخه‌ی اصلی (`master`)
📘 چون هیچ تغییری متضاد نبود، **Fast-forward merge** انجام شد
📘 فایل‌های جدید و تغییرات در `master` ادغام شدن

---

### ✅ مرحله ۱۰: بررسی نهایی

```bash
git status
git --no-pager branch
```

📘 تأیید اینکه:

* شاخه فعلی `master` است
* همه‌چیز commit شده
* شاخه `fixpages` ادغام شده و کار تمیزه

---

## 🧩 خلاصه جریان کاری (Workflow)

```
master  ←  fixpages
  ↑          ↑
  │          ├── تغییر فایل‌ها، commit
  │          ├── افزودن فایل جدید (footer.html)
  │          └── git merge → بازگشت به master
```

---

می‌خوای مرحله‌ی بعدی رو با هم بریم؟ مثلاً یاد بگیری:

* چطور **branch حذف یا نگهداری** بشه بعد از merge
* یا اینکه چطور **conflictها** (تضادها) رو موقع merge حل کنیم؟

<!-- -------------------------------------------- -->
<hr style="height:5px; background-color:red" />
<!-- -------------------------------------------- -->

عالی مهدي 👏
تو عملاً **یه چرخه‌ی کاملِ حرفه‌ای از مدیریت شاخه‌ها (branch workflow)** رو انجام دادی — دقیق و تمیز، بدون هیچ خطایی ✅

بذار خلاصه‌ش رو برات به‌صورت یک **چک‌لیست گام‌به‌گام نهایی** بنویسم تا مثل یه راهنمای کامل Git در عمل داشته باشی 👇

---

## 🧭 چک‌لیست کامل Git تا الان

### 🔹 مرحله ۱: ساخت مخزن

```bash
git init
```

ایجاد ریپازیتوری جدید محلی و ساخت پوشه `.git`

---

### 🔹 مرحله ۲: اضافه‌کردن فایل و اولین commit

```bash
echo "Hello Git!" > readme.txt
git add readme.txt
git commit -m "readme file created"
```

📘 ساخت commit اولیه

---

### 🔹 مرحله ۳: تغییر فایل‌ها و commit‌های بعدی

```bash
git add -A
git commit -m "added my name to the readme file"
```

📘 انجام تغییرات و ذخیره آنها در commitهای جدید

---

### 🔹 مرحله ۴: افزودن چند فایل

```bash
touch page1.html page2.html page3.html
git add -A
git commit -m "add 3 page files"
```

📘 اضافه کردن فایل‌های جدید و commit کردن آنها

---

### 🔹 مرحله ۵: ایجاد شاخه جدید برای اصلاحات

```bash
git branch fixpages
git checkout fixpages
```

📘 ساخت و سوئیچ به branch جدید برای کار جدا از master

---

### 🔹 مرحله ۶: انجام تغییرات و commit در شاخه جدید

```bash
git add -A
git reset footer.html
git commit -m "adding html and body to pages"
git add -A
git commit -m "footer added"
```

📘 چند commit در شاخه `fixpages`

---

### 🔹 مرحله ۷: ادغام شاخه fixpages در master

```bash
git checkout master
git merge fixpages
```

📘 Fast-forward merge
📘 تغییرات بدون conflict ادغام شدن

---

### 🔹 مرحله ۸: ساخت شاخه جدید برای لینک‌سازی

```bash
git branch linkingpages
git checkout linkingpages
```

📘 شاخه جدید برای کارهای بعدی

---

### 🔹 مرحله ۹: حذف و افزودن فایل‌ها در شاخه linkingpages

```bash
git rm footer.html
git commit -m "removed footer"

touch index.html
git add -A
git commit -m "index page with page links created"
```

📘 حذف footer و ساخت فایل index با لینک‌ها

---

### 🔹 مرحله ۱۰: ادغام شاخه linkingpages در master

```bash
git checkout master
git merge linkingpages
```

📘 ادغام تغییرات (`footer.html` حذف و `index.html` اضافه شد)

---

### 🔹 مرحله ۱۱: حذف شاخه‌های ادغام‌شده

```bash
git branch -d fixpages
git branch -d linkingpages
```

📘 حذف شاخه‌های merge شده برای تمیز نگه داشتن پروژه

---

### 🔹 مرحله ۱۲: بررسی وضعیت و تاریخچه

```bash
git status
git --no-pager branch
git --no-pager log --oneline
```

📘 تأیید تمیزی شاخه‌ها
📘 نمایش خلاصه commitها (اکنون فقط master باقی مانده)

---

## 🧩 وضعیت نهایی (خلاصه گرافی)

```
(master)
   │
   ├── ac92aac  readme file created
   ├── a04f3a9  added my name to readme
   ├── 3303065  add 3 page files
   ├── 8ace4cc  added my last name
   ├── 70d8207  changing page number
   ├── 1159f9e  adding html and body
   ├── 06e0e9c  footer added
   ├── c660454  removed footer
   └── 758313d  index page with page links created
```

---

## ✅ مهارت‌هایی که تا الان یاد گرفتی

| مبحث                                         | تسلط       |
| -------------------------------------------- | ---------- |
| `git init`, `add`, `commit`, `status`, `log` | 🔹🔹🔹🔹🔹 |
| `branch` و `checkout`                        | 🔹🔹🔹🔹🔹 |
| `merge` (Fast-forward)                       | 🔹🔹🔹🔹   |
| `reset`, `restore`, `rm`                     | 🔹🔹🔹🔹   |
| حذف شاخه‌ها و تمیزکاری پروژه                 | 🔹🔹🔹🔹   |
| استفاده از `--no-pager`, `--oneline`, `diff` | 🔹🔹🔹🔹   |

---

می‌خوای گام بعدی رو با هم بریم؟
می‌تونیم بریم سراغ **تضادهای merge (merge conflicts)** یا یاد بگیری چطور پروژه‌ت رو به **GitHub** push کنی و کار با remoteها (`origin`, `push`, `pull`) رو تمرین کنیم.
کدومو انتخاب می‌کنی؟
