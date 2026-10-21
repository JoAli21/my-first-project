<!-- ملاحظة: الأسطر اللي تبدي بـ <!-- وتنتهي بـ --> هي تعليقات مخفية. تشوفها بـ VS Code بس، وما تطلع على GitHub -->

# My First Project

<!-- هذا وصف المشروع: مشروع بايثون صغير سويته حتى أتعلم Git و GitHub خطوة بخطوة، مثل فريق شغل حقيقي -->

A small Python project I built to learn **Git** and **GitHub** step by step — from setting up Git to working with branches, Pull Requests, and Issues like a real development team.

**Author:** Ali Adel ([@JoAli21](https://github.com/JoAli21))

---

## 📁 Project Files

<!-- ملفات المشروع: main.py يطبع ترحيب وبيه دالة الجمع، و calculator.py بيه دوال الضرب والطرح والقسمة -->

| File | Description |
|---|---|
| `main.py` | Prints a greeting and uses an `add` function |
| `calculator.py` | Calculator functions: `multiply`, `subtract`, `divide` (handles division by zero) |

## ▶️ How to Run

<!-- طريقة تشغيل الملفات من الترمنل -->

```bash
python main.py
python calculator.py
```

---

## 🧭 What I Learned — Step by Step

### 1. Setting up Git (one time only)

<!-- الإعداد: مرة وحدة بس على الجهاز. نعرّف Git منو انت، حتى كل حفظ ينكتب باسمك -->
<!-- git --version = أتأكد إن Git منصّب -->
<!-- user.name = اسمي ، user.email = ايميل حساب GitHub -->

```bash
git --version
git config --global user.name "Ali Adel"
git config --global user.email "my-email@example.com"
```

Tells Git who I am, so every commit is saved under my name.

### 2. Creating the repository

<!-- سويت repo على GitHub باسم my-first-project، وسويت مجلد بنفس الاسم وفتحته بـ VS Code، وكتبت main.py وشغلته -->

- Created a new repository on GitHub: `my-first-project`
- Created the project folder and opened it in **VS Code**
- Wrote `main.py` and ran it from the VS Code terminal

### 3. First commit and first push

<!-- أول حفظ وأول رفع. هاي الأوامر تنكتب مرة وحدة لكل مشروع جديد -->
<!-- git init = خلّي Git يبدي يراقب المجلد -->
<!-- git status = شنو تغيّر؟ (للمشاهدة بس، ما يغيّر شي) -->
<!-- git add . = أجهّز كل الملفات (أحطها بالكارتونة) -->
<!-- git commit -m = أحفظ نسخة على جهازي (أسد الكارتونة وأكتب عليها) -->
<!-- git branch -M main = أسمّي الفرع main بدل master -->
<!-- git remote add origin = أربط مشروعي برابط الـ repo على GitHub (عنوان البريد) -->
<!-- git remote -v = أتأكد إن الربط صار -->
<!-- git push -u origin main = أرفع للـ GitHub أول مرة (أدز الكارتونة للمخزن) -->

```bash
git init                     # start tracking the folder
git status                   # see what changed
git add .                    # stage all changed files
git commit -m "First commit" # save a snapshot locally
git branch -M main           # rename branch to main
git remote add origin https://github.com/JoAli21/my-first-project.git
git remote -v                # confirm the connection
git push -u origin main      # upload to GitHub
```

### 4. The daily cycle (edit → save → upload)

<!-- الدورة اليومية: كل ما أعدّل الكود أعيد هاي الأربع أوامر -->
<!-- بعد أول push -u ، أكتب git push بس بدون origin main -->

```bash
git status
git add .
git commit -m "Describe what I changed"
git push
```

After the first `push -u`, only `git push` is needed.

### 5. Working with branches and Pull Requests

<!-- الفروع: أشتغل على ميزة جديدة بفرع منفصل حتى ما أخرّب الكود الأصلي بـ main -->
<!-- git checkout -b = أسوي فرع جديد وأدخل بيه -->
<!-- git push -u origin اسم_الفرع = أرفع الفرع أول مرة -->

```bash
git checkout -b feature-calculator     # create a new branch and switch to it
# write calculator.py
git add .
git commit -m "Add calculator functions"
git push -u origin feature-calculator
```

<!-- Pull Request = طلب دمج. أكول بيه: هاي تعديلاتي بالفرع، راجعوها وادمجوها بـ main -->
<!-- Files changed: الأخضر + يعني أسطر انضافت، والأحمر - يعني أسطر انمسحت -->

Then on GitHub:
- Opened a **Pull Request** (`base: main ← compare: feature-calculator`)
- Reviewed **Files changed** (green `+` = added lines, red `-` = removed lines)
- **Merged** the Pull Request and deleted the branch

<!-- بعد الدمج على GitHub، أرجع لجهازي وأجيب التحديث -->
<!-- git checkout main = أرجع لفرع main -->
<!-- git pull = أنزّل التحديثات من GitHub لجهازي (أجيب البضاعة من المخزن للدكان) -->
<!-- git branch -d = أحذف الفرع لأن شغله خلص وصار جزء من main -->
<!-- git branch = يراويني كل الفروع، واللي جنبه * هو اللي آني بيه -->

Back in VS Code:

```bash
git checkout main
git pull                              # download the merge to my computer
git branch -d feature-calculator      # delete the finished branch
git branch                            # list branches (* = current branch)
```

### 6. Team workflow simulation: Manager 👔 and Employee 👷

<!-- لعبة المدير والموظف: نفس طريقة الشغل بالشركات -->
<!-- المدير يكتب Issue (تاسك) ← الموظف يسوي فرع ويشتغل ويرفع ← الموظف يسوي PR ← المدير يراجع ويدمج -->
<!-- كلمة Closes #2 بوصف الـ PR تخلي GitHub يسكّر التاسك #2 تلقائياً بعد الدمج -->

| Role | Step |
|---|---|
| 👔 Manager | Created **Issue #2**: "Add divide function to calculator" |
| 👷 Employee | `git checkout main` → `git pull` → `git checkout -b issue-2-divide` |
| 👷 Employee | Wrote the `divide` function → tested it → `git add calculator.py` → `git commit` → `git push -u origin issue-2-divide` |
| 👷 Employee | Opened **Pull Request #3** with `Closes #2` in the description |
| 👔 Manager | Reviewed **Files changed**, left a comment on a line, submitted the review, then **merged** |
| 🪄 GitHub | Closed **Issue #2** automatically because of `Closes #2` |
| 👷 Employee | `git checkout main` → `git pull` → `git branch -d issue-2-divide` |

<!-- تسمية الفرع: issue - رقم التاسك - وصف قصير. مثال: تاسك رقم 3 لصفحة الدخول = issue-3-login -->
<!-- لا تحط مسافات بالاسم، استخدم - بدالها -->

**Branch naming convention:** `issue-<number>-<short-description>`, e.g. `issue-3-login`. No spaces, use `-`.

<!-- أرفع ملف واحد بس: git add اسم_الملف بدل git add . حتى كل حفظ يكون تاسك واحد -->

**Commit only specific files:** `git add calculator.py` instead of `git add .` — so each commit contains one task only.

---

## 🛠️ Problems I Faced and How I Fixed Them

<!-- الأخطاء اللي صارت وياي وحلولها: -->
<!-- 1. كتبت git add. بدون مسافة ← لازم مسافة: git add . -->
<!-- 2. خطأ 403: الجهاز كان محفوظ بيه حساب GitHub ثاني ← مسحته بأمر cmdkey وسجلت بحسابي -->
<!-- 3. غلطت بحرف باسم الفرع (calculater بدل calculator) ← أتأكد من الاسم بـ git branch -->
<!-- 4. كتبت -U كابيتل ← الصح -u سمول، لأن Git يفرّق بين الكبير والصغير -->
<!-- 5. حاولت أحذف الفرع وآني بيه ← لازم أطلع منه أول بـ git checkout main -->
<!-- 6. الملف اختفى لما رجعت لـ main ← لأن main على جهازي قديم، والحل git pull -->

| Error | Cause | Fix |
|---|---|---|
| `git: 'add.' is not a git command` | Missing space | `git add .` |
| `Permission ... denied to <another account>` (403) | Windows had another GitHub account saved | `cmdkey /delete:git:https://github.com` then push again and sign in with the right account |
| `src refspec ... does not match any` | Typo in branch name | Check names with `git branch` |
| `unknown switch 'U'` | Git is case-sensitive | Use `-u` (lowercase) |
| `cannot delete branch ... used by worktree` | Tried to delete the branch I was on | `git checkout main` first, then delete |
| File disappeared after switching to `main` | Local `main` was behind GitHub | `git pull` |

---

## 🧠 Golden Rules

<!-- القواعد الذهبية: -->
<!-- 1. قبل أي شغل جديد: git checkout main وبعدها git pull -->
<!-- 2. تاسك واحد = فرع واحد = PR واحد -->
<!-- 3. دائماً أشوف اسم الفرع تحت يسار VS Code قبل أي أمر -->
<!-- 4. رسالة الـ commit بالإنكليزي وتوصف شنو سويت -->
<!-- 5. أجرّب الكود قبل ما أحفظه -->

1. Before starting any new work: `git checkout main` then `git pull`
2. One task = one branch = one Pull Request
3. Always check the current branch name (bottom-left in VS Code)
4. Write clear commit messages in English that describe *what* changed
5. Test the code before committing
