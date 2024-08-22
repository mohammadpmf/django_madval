# django_madval
A django package to use either persian numbers or comma separated persian numbers on djanog. Also can translate weekdays to persian.


# How to use? (چگونه استفاده کنیم؟)

##### To use this package, do the following
##### جهت استفاده از این پکیج، مراحل زیر را انجام دهید.

```bash
pip install django_madval
```

##### In the next step, install the app in your settings.py
##### در مرحله بعد، در فایل settings.py، اپ را اضافه کنید.

```bash
INSTALLED_APPS = [
    # ...
    'django_madval',
    # ...
]
```

##### Load madval_persian_translation file in your templates to use translation filters.
##### برای استفاده از تمپلیت فیلترهای مربوط به تبدیل اعداد به فارسی، فایل madval_persian_translation را لود کنید.

sample in a template file named order_detail.html:
```bash
...
{% load madval_persian_translation %}
...
```

##### Defined filters so far are "pn" "pnf" "cspn" "p_weekday"
**pn** stands for **p**ersian_**n**umbers

**pnf** stands for **p**ersian_**n**umbers_**f**loat

**cspn** stands for **c**omma_**s**eparated_**p**ersian_**n**umbers

**p_weekday** stands for **p**ersian_**weekday**

##### فیلترهای تعریف شده فعلی، "pn" "pnf" "cspn" "p_weekday" ها هستند.

sample usage in order_detail.html:
```bash
{{ order.phone_number|pn }}
{{ order.items.count|pn }}
```
 جهت نمایش ارقام به فارسی و به صورت جدا نشده
<hr>

```bash
{{ order.get_total_price|cspn }}
```
جهت نمایش ارقام به فارسی و ۳ رقم ۳ رقم جدا شده
<hr>

در صورت نیاز می توانید به فیلتر "cspn" ورودی بدهید تا اعداد را به مقدار دلخواه شما جدا کند. مثلا کد زیر اعداد را ۵ رقم ۵ رقم جدا میکند.
```bash
{{ order.get_total_price|cspn:5 }}
```
<hr>

در صورتی که روز هفته را به صورت میلادی (مثلا Tuesday یا Tue) دارید، می توانید با فیلتر p_weekday آن را به سه‌شنبه تبدیل کنید. در مثال زیر از پکیج  [جلالی] نیز استفاده شده است که برای نصب آن باید به مستندات مربوطه مراجعه کنید.
```bash
{{ order.datetime_created|to_jalali:'%A'|p_weekday }}
```
پس از فیلتر "to_jalali:'%A'" که اسم روز هفته را گرفتیم، با استفاده از فیلتر "p_weekday" آن را به روز معادل فارسی تبدیل کردیم.


[جلالی]: https://github.com/a-roomana/django-jalali-date/tree/master
