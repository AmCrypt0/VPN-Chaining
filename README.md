# VPN Chaining
دسترسی به اینترنت آزاد با استفاده از روش VPN Chaining

سلام

ادامه آموزشی که توی توییتر گذاشته بودم همراه تصویر هر مرحله.

چه چیزایی لازم داریم؟

1.سرور مجازی ایران که در این آموزش بهش میگیم `VPN1`:

برای دور زدن محدودیت های اعمال شده روی اینترنت کاربر عادی به یک سرور مجازی داخل ایران احتیاج داریم.چرا سرور های داخل کشور محدود نمیشن؟چون سرویس دهنده ها و وبسایت ها و اپلیکیشن های داخلی هم روی همین سرور ها ران شدن و اکثرشون برای اینکه بتونن کار کنن وابسته به خیلی از سرویس های خارج از کشور هستن.
در آخر این آموزش ما به سرور `VPN1` متصل میشیم که همون سرور ایرانه. خب حالا بریم و وصلش کنیم به اینترنت بدون فیلترینگ.


2.سرور مجازی خارج از کشور که در این آموزش بهش میگیم `VPN2`:

برای تهیه سرور مجازی خارج از کشور سرویس دهنده های بسیاری هستن که من در این آموزش یکیشون که هم قیمت پایینتری داره و هم برای پرداخت میتونید از بیتکوین و بقیه رمز ارز ها استفاده کنید.

https://www.vps2day.com/

3.چند نرم افزار برای اینکه بتونیم سرورهای مجازی که گرفتیم رو راه اندازی و تنظیم کنیم. کار بسیار آسونیه نیاز به دانش خاصی نداره و حتی اگر باز هم من موفق نشم که همه چیز رو توضیح بدم با یه جستجو کوچیک در اینترنت همه چیز موجوده.

4.کلاینت Wireguard:

این همون نرم افزاری هست که ازش برای اتصال به `VPN1` استفاده میکنیم.چه ویندوز داشته باشید چه iOS و چه Android و لینوکس روی همشون جواب میده و بسیار بسیار راحته.شما بعد از اتمام راه اندازی سرور ایران یاد میگیرید که فایل کانکشن لازم برای استفاده از این نرم افزار رو بسازید و باز هم تکرار میکنم خیلی راحته نگران نباشید.
برای دانلودش از وبسایت رسمی استفاده کنید که لینک دانلود برای هر سیستم عاملی رو قرار داده.

https://www.wireguard.com/install/

خرید و راه اندازی  سرور مجازی خارح از کشور (`VPN2`):
اکانت vps2day رو میتونید خیلی راحت با هر رمز ارزی شارژ کنید. بعد از اینکه اعتبار اضافه کردید میریم برای خرید سرور :

https://my.vps2day.com/server_add.html

![image](https://user-images.githubusercontent.com/105618808/168515438-8baa623b-94c7-467c-9cc5-c7e20da3fdd1.png)

سیستم عامل `ubuntu server 20.04` انتخاب کنید.
![image](https://user-images.githubusercontent.com/105618808/168515709-29420de5-3c95-4a03-b27a-92f6c1779d86.png)


کشور های زیادی موجود هستن برای موقعیت مکانی سرور که من در این آموزش سوئد رو انتخاب کردم.

برای کاربری مورد نظر ما  در این آموزش همون اولین پلن 5 یورویی کافیه و لازم نیست بیشتر هزینه کنید و مدت تمدید سرویس رو هم بسته به نیاز خودتون انتخاب کنید.
بقیه موارد هم دست نزنید و در آخر `Order Server` رو بزنید تا سفارش تکمیل بشه.

![image](https://user-images.githubusercontent.com/105618808/168516587-c9a9cd2e-696c-4c7d-aae9-ba6ea19c70c9.png)


بعد از چند دقیقه سرور آماده میشه و به شما تحویل داده میشه. برمیگردیم به پنل کاربری my.vps2day.com

![image](https://user-images.githubusercontent.com/105618808/168516827-44a06e19-2962-4aab-b1f2-37c3fb427200.png)

قسمت `ip address` همون آدرسی هست که ما برای وصل شدن به سرور استفاده میکنیم پس یادداشتش کنید.

با کلیک روی سرور جزئیات رو باز میکنیم و در پایین جدول نام کاربری و کلمه عبور رو یادداشت میکنیم.

![image](https://user-images.githubusercontent.com/105618808/168517145-0c3a5dd1-ca38-4fa9-aac8-5f3a7b4d6833.png)

برای اتصال به سرور از طریق ssh به یک نرم افزار لازم به نام putty که از لینک سایت خودش میتونید دانلودش کنید.نرم افزار winscp رو هم دانلود کنید در ادامه لازمش داریم.

https://www.putty.org/

https://winscp.net/eng/download.php

بعد از نصب putty اجراش کنید یه صفحه مثل صفحه زیر باز میشه که در قسمت `Hostname` همون آدرس آی پی سرور که قبلا یادداشت کرده بودیم رو وارد میکنیم و open رو میزنیم. 


![image](https://user-images.githubusercontent.com/105618808/168518043-ab3066e1-acaa-4e90-ab19-03fe33d28f29.png)


 در قسمت login as نام کاربری رو وارد میکنیم و دکمه ENTER رو میزنیم.

 ![image](https://user-images.githubusercontent.com/105618808/168518294-5130cc40-905a-43b4-878b-23c18606ef95.png)


بعد رمز عبور رو وارد میکنیم و مجدد Enter میزنیم و به سرور متصل میشیم.

حالا سرور رو با استفاده از دستورات زیر آپدیت میکنیم.توجه کنید که اگر در حین آپدیت پیغامی داد فقط Enter بزنید مهم نیست.

```bash
sudo apt update
sudo apt upgrade
```
اگر ارور داد بدون `sudo` بزنید.

```bash
apt update
apt upgrade
```

حالا که سرور آماده شد میریم برای نصب Opnvpn روی سرور که بعدش بتونیم با سرور ایران بهش وصل بشیم.
از دستور زیر استفاده کنید و مراحل رو گام به گام با من انجام بدید:

```bash
wget https://git.io/vpn -O openvpn-install.sh && bash openvpn-install.sh
```

![image](https://user-images.githubusercontent.com/105618808/168518912-fdb67d69-4514-4b01-9da4-b32f07186ef6.png)

در قسمت پروتوکول 2 رو بزنید و Enter کنید.


![image](https://user-images.githubusercontent.com/105618808/168519064-8f91423f-3fc7-4828-89f1-a09b8963e254.png)

در قسمت port عدد 443 رو بزنید و Enter کنید.

![image](https://user-images.githubusercontent.com/105618808/168519149-b6955a4d-2744-412b-98f1-05b3f4baf2c2.png)

در قسمت `DNS Server` عدد 3 رو بزنید و `Enter` کنید.

و در نهایت در قسمت `name` بزنید `vpstovpn` و `Enter` کنید.

چند ثانیه یا حداکثر چند دقیقه طول میکشه و نصب به اتمام میرسه و یه پیغام شبیه زیر بهتون نمایش میده.

![image](https://user-images.githubusercontent.com/105618808/168519395-2b99f8f3-4b33-43b8-88fe-fb1e7a3e02ea.png)

میتونید صفحه رو ببندید کار ما اینجا تمومه و حالا میریم سراغ `winscp`.

برنامه `winscp` رو باز کنید و مجدد اطلاعات ورود به سرور رو که بالا یادداشت کردید وارد کنید و در نهایت Login رو بزنید.

![image](https://user-images.githubusercontent.com/105618808/168519757-032d553c-85af-4586-8e57-4caa905756ba.png)

بعد از وارد شدن حالا شما به فیا های روی سرور دسترسی دارید و فایل کانفیگی در بالا تولید کردیم رو دانلود میکنیم روی سیستم خودمون.خیلی راحت بکشیدش مثلا روی دسکتاپ تا بعدا انتقالش بدیم به سرور ایران.


![image](https://user-images.githubusercontent.com/105618808/168536198-cdd23f03-c8a7-46a3-bc7a-f37b3b9b1f20.png)

دیگه کاری به این سرور نداریم و میریم برای ادامه کارها.

تهیه و راه اندازی سرور مجازی ایران (`VPN2`):

روش خریدش رو دیپه لازم نیست توضیح بدم صدها شرکت ایرانی هستن از بینشون یکیو انتخاب کنید.
برای مشخصات سرور کمترینش رو انتخاب کنید تا هزینه کمتری بدید، این کار نیاز به منابع خاصی نداره و یه سرور ساده با 500 مگابایت رم برای متصل شدن تمام دوستان و آشناهاتون کافیه.
فقط دقت کنید که سیستم عاملش رو `Ubuntu Server 20.04` انتخاب کنید.
بعد از خرید سرور مشخصاتش رو دریافت کنید دقیقا مثل سرور قبلی که راه اندازی کردم یاد داشت کنید که در ادامه مراحل لازم میشه.
برنامه winscp رو باز کنید و به سرور ایران متصل بشید با آی پی آدرس و نام کاربری و کلمه عبوری که دریافت کردید.
بعد از ورود فایلی رو که قبلتر از روی سرور خارج دانلود کردیم رو انتقال بدید به همون فولدر اصلی (root).اسم فایل رو هم که یادتونه `vpstovpn.ovpn`
بعد از اینکه فایل کپی شد برنامه putty رو باز کنید و به سرور ایران متصل بشید.
دستورات زیر رو برای آپدیت سرور وارد کنید و Enter بزنید:

```bash
sudo apt update
sudo apt upgrade 
```

در حین آپدیت هر پیغامی دیدید Enter بزنید مهم نیست.
بعد از اینکه مرحله آپدیت تموم شد دستور زیر رو وارد کنید و مراحل بعدی رو دنبال کنید:

```bash
wget https://git.io/wireguard -O wireguard-install.sh && bash wireguard-install.sh
```

برای port number عدد `50820` رو وارد کنید

![image](https://user-images.githubusercontent.com/105618808/168539758-5b4b641a-3297-4f57-81a0-e4ceb6c5e26c.png)

در قسمت `client` هر اسمی بخواید میتونید وارد کنید. من برای این آموزش از اسم `client1` استفاده میکنم تا روش ساخت کلاینت های بیشتر رو هم راحت تر توضیح بدم.

![image](https://user-images.githubusercontent.com/105618808/168540156-86b292fb-e7ee-4680-8ef9-4de1cfdd96ac.png)

در قسمت DNS حتما عدد 1 رو وارد کنید و Enter بزنید و بعد مجددا Enter بزنید.

![image](https://user-images.githubusercontent.com/105618808/168540269-b5ddebd0-c198-40d3-8889-a125494b028d.png)

ممکنه روند نصب چند دقیقه طول بکشه و بعدش با این پیغام مواجه میشید.

![image](https://user-images.githubusercontent.com/105618808/168540590-e64d845c-00e2-4d03-8810-35fd57235686.png)

تبریک میگم تا اینجا هر دو سرور رو راه اندازی کردید حالا میمونه متصل کردن این دو بهم.
حالا `openvpn` رو روی سرور ایران نصب میکنیم که برای اتصال دو سرور بهش نیاز داریم.
```bash
apt install openvpn 
```

دستور زیر رو وارد کنید تا یه پنجره دیگه باز کنیم.
```bash
screen -S vpn
```

حالا دستور زیر رو وارد کنید تا سرور ایران رو به سرور مجازی خارج از کشور متصل کنید.

```bash
openvpn --config vpstovpn.ovpn --route-nopull
```

اگر همه چیز درست انجام شده باشه موفق شدید دو سرور رو بهم وصل کنید. حالا باید این پنجره رو ترک کنیم بدون اینکه اتصال قطع بشه و به پنجره قبلی برگردیم.
دکمه ctrl + a + d رو باهم بزنید.
حالا دستورات زیر رو وارد کنید تا سرور ترافیک رو از داخل تونل openvpn به سرور خارج از کشور منتقل کنه.

```bash
iptables -t nat -D POSTROUTING -s 10.7.0.0/24 ! -d 10.7.0.0/24 -j SNAT --to-source YOUR_IRAN_SERVER_IP

iptables -A FORWARD -i tun0 -o wg0 -j ACCEPT

iptables -A FORWARD -i wg0 -o tun0 -j ACCEPT 

iptables -A FORWARD -d 10.7.0.0/24 -m state --state ESTABLISHED,RELATED -j ACCEPT

iptables -t nat -A POSTROUTING -s 10.7.0.0/24 -j SNAT --to-source 10.8.0.2

ip route add default via 10.8.0.2 table 120 

ip rule add from 10.7.0.0/24 table 120 
```

و تمام حالا آماده اید که به سرور ایران وصل بشید و از اینترنت بدون فیلتر استفاده کنید.برای ساخت فایل کانفیگ بیشتر میتونید مجدد دستور زیر رو اجرا کنید و یوزر های بیشتری بسازید.

```bash
wget https://git.io/wireguard -O wireguard-install.sh && bash wireguard-install.sh
```

![image](https://user-images.githubusercontent.com/105618808/168543062-77f6f538-fd67-4fa4-b20c-79c29b6de1c6.png)

فایل های ساخته شده با فرمت `.conf` هستن و برای تمام کلاینت ها یکسانن چه برای آندروید و iOS و چه ویندوز. فقط کافیه با winscp کانفیگ های ساخته شده رو دانلود کنید و انتقال بدید به کامپیوتر و موبایل و از طریق نرم افزار رسمی وایرگارد که نصب کردید به سرور خودتون متصل بشید.
