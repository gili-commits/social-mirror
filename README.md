# Social Mirror

PWA לניתוח CBT-עצמי של אינטראקציות חברתיות באמצעות GPT-4o Audio. כל הלוגיקה client-side, ללא שרת, ללא מסד נתונים.

## מבנה

- `index.html` — כל הממשק והלוגיקה
- `manifest.json` — מטא-דאטה של PWA
- `sw.js` — Service Worker (cache-first)
- `icon-192.png`, `icon-512.png` — אייקונים (עדיין לא קיימים)

## הרצה מקומית

```bash
cd ~/Desktop/social-mirror
python3 -m http.server 8000
```

פתיחת `http://localhost:8000` בדפדפן.

> הערה: מיקרופון (`getUserMedia`) דורש HTTPS או `localhost`. `127.0.0.1` עשוי לעבוד גם.

## דפלוי ל-GitHub Pages

```bash
cd ~/Desktop/social-mirror
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/<user>/social-mirror.git
git branch -M main
git push -u origin main
```

ב-GitHub: **Settings → Pages → Source: Deploy from a branch → Branch: main / (root)**.

ה-URL יהיה `https://<user>.github.io/social-mirror/`. HTTPS אוטומטי — חובה ל-`getUserMedia`.

### עדכונים

```bash
git add .
git commit -m "..."
git push
```

## קיצורי מסך בית באנדרואיד

אחרי דפלוי ל-GitHub Pages (HTTPS חובה):

1. על הטלפון — פתח את ה-URL ב-Chrome
2. תפריט ⋮ → **"Install app"** (או "Add to Home screen")
3. האפליקציה תותקן ותופיע במגירת האפליקציות
4. **לחיצה ארוכה** על האייקון → יופיע popup עם 3 קיצורים: זר / מוכר / משפחה
5. לחיצה ארוכה על כל קיצור → **גרור אותו למסך הבית**
6. עכשיו יש לך 3 אייקונים צבעוניים נפרדים על המסך הראשי

לחיצה על אחד מהאייקונים → פתיחה אוטומטית של האפליקציה + התחלת הקלטה מיידית בהקשר המתאים (אחרי אישור הרשאת מיקרופון בפעם הראשונה).

**הערות**:
- בפעם הראשונה יידרש אישור מיקרופון. אחרי זה — מיידי.
- צריך מפתח OpenAI שמור באפליקציה לפני השימוש בקיצורים (⚙ → הגדרות).
- ב-launcher של Samsung (One UI) לפעמים צריך להפעיל ידנית "Add shortcut to home screen" בהגדרות ה-launcher.

## סטטוס בנייה

- [x] שלב 1 — שלד PWA + ניווט בין מסכים
- [x] שלב 2 — שמירת API Key
- [x] שלב 3 — הקלטה (MediaRecorder) + אינדיקציית consent ויזואלית
- [x] שלב 4 — המרת WebM ל-WAV
- [x] שלב 5 — אינטגרציה עם GPT-4o Audio + מסך עיבוד
- [x] שלב 6 — רנדור תוצאות
- [x] שלב 7 — היסטוריה (localStorage)
- [x] שלב 8 — ליטוש עיצובי + הודעות סטטוס
