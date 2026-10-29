# Geek-vip

مستودع العمل الأساسي لمشاريع **Geek-vip** — ألعاب ومنصات ويب، تُبنى وتُنشر آليًا.

## القاعدة الأمنية الأولى

> **التوكن لا يُقرأ ولا يُطبع.** أسرار Cloudflare موجودة في GitHub Secrets فقط،
> وتُحقَن داخل بيئة تشغيل GitHub Actions لحظة النشر، ثم تختفي.
> لا يمرّ أي سر عبر أي محادثة أو ملف أو سجل.

التفاصيل الكاملة في **[docs/PM-PLAYBOOK.md](docs/PM-PLAYBOOK.md)**.

## النشر

```
.github/workflows/deploy-cloudflare.yml   ← يدوي (workflow_dispatch)
```

من واجهة GitHub: **Actions → Deploy → Cloudflare → Run workflow**
ثم اختَر: `target` (pages/worker)، `project`، و`dry_run` أول مرة.

أو من الطرفية:

```bash
gh workflow run deploy-cloudflare.yml \
  -f target=pages -f project=my-project -f dry_run=true
```

`dry_run=true` يبني فقط ولا ينشر — استخدمه دائمًا في أول تشغيل.

## الأسرار المطلوبة

| الاسم | الغرض |
|---|---|
| `CLOUDFLARE_API_TOKEN` | مصادقة النشر |
| `CLOUDFLARE_ACCOUNT_ID` | رقم الحساب |

## البنية

```
docs/                       قرارات ومعايير العمل
.github/workflows/          خطوط النشر الآلي
```

_جارٍ التجهيز للمشروع الأول._
