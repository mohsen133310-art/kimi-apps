# Kimi Apps

وب‌سایت فارسی و راست‌چین برای معرفی، بررسی و دریافت برنامه‌های ساخته‌شده در Kimi Apps.

## امکانات سایت
- نمایش برنامه‌های منتشرشده از Supabase
- جست‌وجو و فیلتر دسته‌بندی
- صفحه جزئیات هر برنامه و لینک دانلود APK / نسخه وب / GitHub
- ثبت دیدگاه و پاسخ بدون حساب کاربری
- طراحی واکنش‌گرا با تم سفید و بنفش

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
6. در جدول `public.apps`، همین نشانی را در ستون `apk_url` برنامه قرار دهید.

کاربر از داخل Kimi Apps روی «دانلود APK» می‌زند و فایل از GitHub دریافت می‌شود؛ لازم نیست صفحه GitHub را برای پیدا کردن فایل باز کند. خود فایل روی زیرساخت GitHub نگهداری می‌شود.

## مدیریت و انتشار برنامه‌ها و دیدگاه‌ها
اطلاعات فهرست برنامه‌ها و دیدگاه‌ها فعلاً از Supabase خوانده می‌شود. پنل مدیریت عمومی در سایت وجود ندارد.

1. وارد [Supabase Table Editor](https://supabase.com/dashboard/project/rrcalskgqqkclogvjsyv/editor) شوید.
2. جدول `public.apps` را باز کنید و **Insert row** را بزنید.
3. فیلدهای `slug`، `title`، `description`، `category`، `version` و `apk_url` را تکمیل کنید.
4. برای نمایش عمومی، `is_published` را `true` قرار دهید.

### فیلدهای جدول apps
- `slug`: شناسه یکتای انگلیسی، مانند `kimi-notes`
- `title`: نام برنامه
- `description`: توضیحات
- `category`: دسته‌بندی
- `icon_url`: لینک مستقیم تصویر آیکون
- `screenshots`: آرایه لینک تصاویر
- `version`: شماره نسخه
- `apk_url`: لینک مستقیم APK از GitHub Releases
- `web_url`: لینک نسخه وب
- `github_url`: لینک مخزن برنامه
- `is_published`: انتشار عمومی یا پیش‌نویس

## نکته امنیتی
کلید Publishable داخل کد مرورگر قرار دارد و برای دسترسی عمومی طراحی شده است. هرگز کلید `service_role` یا کلیدهای Secret را در این مخزن قرار ندهید. امنیت داده‌ها باید با RLS و policyهای Supabase اعمال شود.
