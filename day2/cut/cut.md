# 📘 `cut` — מדריך מלא (Markdown)

````markdown
# 🟦 מה זה cut?

`cut` הוא כלי בלינוקס המיועד **לשלוף חלקים מסוימים מתוך שורות טקסט**.  
הוא יודע "לחתוך" טקסט לפי:
- מפריד (delimiter) — כמו פסיק `,` או נקודתיים `:`
- מספרי עמודות (fields)
- טווח תווים (character positions)

הפקודה מאוד שימושית בעבודה עם:
- קבצי CSV
- קבצי Log
- קבצי מערכת כמו `/etc/passwd`
- Pipelines בשילוב עם grep, sort, awk ועוד

---

# 🟩 דוגמאות בסיסיות

## 🔹 חיתוך עמודה ראשונה מתוך CSV
```bash
cut -d ',' -f1 users.csv
````

**הסבר:**

* `-d ','` קובע שהמפריד בין עמודות הוא פסיק
* `-f1` מחלץ את השדה הראשון
  → מחזיר את עמודת ה־ID

---

## 🔹 חיתוך עמודות 1–3 מתוך `/etc/passwd`

```bash
cut -d ':' -f1,2,3 /etc/passwd
```

**הסבר:**

* מפריד העמודות הוא `:`
* `-f1,2,3` מחלץ 3 שדות:

  1. שם משתמש
  2. ערך סיסמה (x)
  3. UID

---

## 🔹 חיתוך טווח תווים מתוך קובץ טקסט

```bash
cut -c1-10 report.txt
```

**הסבר:**

* `-c1-10` מחלץ תווים מהעמדה הראשונה עד העשירית
  → שימושי להוצאת תאריך/קידומת

---

# 🟦 דוגמאות קבצים לתרגול

## 📄 users.csv

```csv
id,name,email
1,Daniel,daniel@example.com
2,Alice,alice@example.com
3,Bob,bob@example.com
4,Eden,eden@example.com
```

## 📄 /etc/passwd (גרסת דוגמה)

```text
root:x:0:0:root:/root:/bin/bash
student:x:1000:1000:Student:/home/student:/bin/bash
service:x:1001:1001:Service Account:/srv/service:/usr/sbin/nologin
guest:x:2000:2000:Guest:/home/guest:/bin/bash
```

## 📄 report.txt

```text
2024-11-01 System check OK
2024-11-02 Warning: High CPU
2024-11-03 Error: Disk full
2024-11-04 Maintenance completed
```

---

# 🟦 מתי משתמשים ב-cut?

| שימוש         | תיאור                                  |
| ------------- | -------------------------------------- |
| חילוץ נתונים  | פילטור עמודות מתוך CSV או logs         |
| עיבוד קבצים   | חיתוך שדות מקובצי מערכת                |
| Shell Scripts | אוטומציה של ניתוח טקסט                 |
| Pipelines     | שילוב עם grep, sort, uniq לניתוח מתקדם |

---

# 🟦 יתרונות מרכזיים

* מהיר מאוד (עובד ברמת system calls)
* פשוט לשימוש
* קיים בכל מערכת לינוקס
* אידיאלי לעיבוד טקסטים גדולים

---

# 🟩 סיכום

`cut` הוא כלי בסיסי וחיוני למי שעובד עם לינוקס.
הוא מאפשר בצורה קלה ומדויקת לחלץ נתונים מקבצים — במיוחד CSV ו־Log Files — ומהווה חלק מרכזי מכל pipeline מקצועי.

```
