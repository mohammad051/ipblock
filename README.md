# ip-blocker

این اسکریپ شمارو از شر ابیوز ها هتزنر رها خواهد کرد!

## ویژگی‌ها
- دریافت لیست IP ها از گیت‌هاب
- مسدود کردن IP های دریافت شده با استفاده از `iptables`
- باز کردن پورت‌های مشخص شده برای ارتباطات مجاز
- تنظیم کرون جاب برای به‌روزرسانی خودکار هر 3 روز

## پیش‌نیازها
- سیستم عامل لینوکس (Ubuntu توصیه می‌شود)
- دسترسی root یا sudo برای اجرای دستورات `iptables` و `ufw`
- نصب `curl` و `ufw` بر روی سیستم

## نصب

1. **کلون کردن مخزن گیت‌هاب**
   ابتدا این اسکریپت را از گیت‌هاب دانلود کنید:
   ```bash
   git clone https://raw.githubusercontent.com/mohammad051/ipblock/refs/heads/main/block_ips.sh
   cd ip-blocker
   ```

2. **مجوزهای لازم**
   اسکریپت باید با مجوزهای root اجرا شود تا بتواند تغییرات لازم را در `iptables` و `ufw` اعمال کند. بنابراین، قبل از اجرا، اطمینان حاصل کنید که مجوزهای لازم را دارید.

3. **نصب وابستگی‌ها**
   برای نصب `curl` و `ufw` در صورتی که قبلاً نصب نشده‌اند:
   ```bash
   sudo apt-get update
   sudo apt-get install curl ufw
   ```

4. **اجرای اسکریپت**
   اسکریپت را با استفاده از دستور زیر اجرا کنید:
   ```bash
   sudo bash script.sh
   ```

5. **تنظیم کرون جاب**
   کرون جاب به طور خودکار تنظیم می‌شود که اسکریپت هر 3 روز یک بار اجرا شود. این کار برای به‌روزرسانی لیست IP ها و اعمال قوانین جدید است.

## نحوه استفاده

- اسکریپت به طور خودکار لیست IP های مسدود شده را از گیت‌هاب دریافت کرده و آن‌ها را با استفاده از `iptables` مسدود می‌کند.
- پس از اجرای اسکریپت، پورت‌های ضروری (22, 2053, 443, 8443, 54879, 80) باز خواهند شد.
- کرون جاب برای به‌روزرسانی خودکار تنظیم خواهد شد تا هر 3 روز یک بار اسکریپت اجرا شود.

## حذف اسکریپت

اگر خواسته باشید اسکریپت را حذف کنید و تنظیمات را برگردانید، می‌توانید با استفاده از دستورات زیر قوانین `iptables` و `ufw` را حذف کنید:
```bash
sudo iptables -F
sudo ufw disable
```

## توجه

- اطمینان حاصل کنید که این اسکریپت را تنها بر روی سیستم‌هایی که به امنیت آن‌ها اعتماد دارید، اجرا کنید.
- برای دریافت لیست جدید IP ها از گیت‌هاب، اسکریپت به اینترنت نیاز دارد.
