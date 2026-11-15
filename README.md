# Kimi Apps

وب‌سایت فارسی و راست‌چین برای معرفی، بررسی و دریافت برنامه‌های ساخته‌شده در Kimi Apps.

## امکانات سایت
- نمایش برنامه‌های فهرست‌شده در فایل `apps.json` مخزن GitHub
- جست‌وجو و فیلتر دسته‌بندی
- صفحه جزئیات هر برنامه و لینک دانلود APK / نسخه وب / GitHub
- طراحی واکنش‌گرا با تم سفید و بنفش
- بدون نیاز به پایگاه داده یا سرویس بک‌اند

## میزبانی سایت
سایت به‌صورت استاتیک با **GitHub Pages** منتشر می‌شود. فایل اصلی سایت `index.html` است و workflow موجود در `.github/workflows/deploy-pages.yml` با هر تغییر در آن، سایت را منتشر می‌کند.

نشانی سایت:
https://mohsen133310-art.github.io/kimi-apps/

اگر Pages هنوز فعال نشده است، یک‌بار وارد **Settings → Pages** مخزن شوید و در بخش **Build and deployment → Source** گزینه **GitHub Actions** را انتخاب کنید. سپس از تب **Actions** اجرای workflow با نام **Deploy Kimi Apps to GitHub Pages** را بررسی کنید.

## نگهداری و دانلود فایل‌های APK
فایل‌های نصب را داخل سورس سایت قرار نمی‌دهیم. برای هر برنامه یک **GitHub Release** بسازید و APK را به‌عنوان فایل پیوست همان Release بارگذاری کنید.

مراحل:
1. در مخزن به بخش [Releases](https://github.com/mohsen133310-art/kimi-apps/releases) بروید.
2. گزینه **Draft a new release** را بزنید.
3. یک برچسب نسخه مانند `v1.0.0` بسازید.
4. فایل APK را در بخش پیوست فایل‌ها (Attach binaries) اضافه و Release را منتشر کنید.
5. نشانی مستقیم فایل را کپی کنید. قالب نشانی معمولاً چنین است:
   `https://github.com/mohsen133310-art/kimi-apps/releases/download/v1.0.0/APP-NAME.apk`
6. نشانی را در فیلد `apk_url` همان برنامه در فایل `apps.json` قرار دهید.

کاربر از داخل Kimi Apps روی «دانلود APK» می‌زند و فایل از GitHub دریافت می‌شود؛ لازم نیست صفحه GitHub را برای پیدا کردن فایل باز کند. خود فایل روی زیرساخت GitHub نگهداری می‌شود.

## مدیریت و انتشار برنامه‌ها

فهرست برنامه‌ها از فایل `apps.json` در همین مخزن GitHub خوانده می‌شود. برای افزودن یا ویرایش برنامه:

1. فایل `apps.json` را در مخزن باز کنید.
2. برای هر برنامه یک شیء با فیلدهای `id`، `title`، `description`، `category`، `icon_url`، `version`، `apk_url`، `web_url` و `github_url` اضافه کنید.
3. فایل را Commit کنید؛ سایت پس از انتشار خودکار، فهرست جدید را نمایش می‌دهد.

نمونه ساختار:
```json
[
  {
    "id": "kimi-demo",
    "title": "نام برنامه",
    "description": "توضیح برنامه",
    "category": "ابزار",
    "icon_url": "",
    "version": "1.0.0",
    "apk_url": "https://github.com/.../releases/download/v1.0.0/app.apk",
    "web_url": "",
    "github_url": ""
  }
]
```
