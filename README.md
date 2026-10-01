# Mahmmoud33

ملفات الموقع موجودة في فولدر `public/`. أي push على فرع `main` بيرفعها تلقائياً على سيرفر الـ FTP باستخدام GitHub Actions (`.github/workflows/deploy.yml`). وممكن كمان تشغّل الرفع بإيدك من تبويب **Actions**، بعد ما تختار **Deploy via FTP** وتدوس **Run workflow**.

## الإعداد (مرة واحدة)

ادخل على الريبو في GitHub وروح لـ **Settings → Secrets and variables → Actions → New repository secret**، وضيف السيكرتس دي:

| الاسم | القيمة |
|---|---|
| `FTP_SERVER` | عنوان سيرفر الـ FTP |
| `FTP_USERNAME` | اسم المستخدم |
| `FTP_PASSWORD` | الباسورد |
| `FTP_PORT` | اختياري، الافتراضي `21` |
| `FTP_SERVER_DIR` | اختياري، الفولدر اللي هيترفع فيه على السيرفر (مثلاً `public_html/`). لازم ينتهي بـ `/` |

> ⚠️ متكتبش الباسورد في أي ملف جوه الريبو ولا تبعته في شات. مكانه الوحيد هو GitHub Secrets.

## ملاحظة أمان

الـ workflow بيستخدم `ftp` العادي، وده بيبعت الباسورد من غير تشفير. لو الاستضافة بتدعم FTPS، غيّر `protocol: ftp` لـ `protocol: ftps` في ملف الـ workflow.
