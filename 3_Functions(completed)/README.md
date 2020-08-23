# 3\_Functions

<div dir='rtl'>

* [توابع](3_Functions(completed)/3_Functions.md#%D8%AA%D9%88%D8%A7%D8%A8%D8%B9)

  * [کوچک بودن!](3_Functions(completed)/3_Functions.md#%DA%A9%D9%88%DA%86%DA%A9-%D8%A8%D9%88%D8%AF%D9%86)
    * [بلوک ها و تو رفتگی ها](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D8%A8%D9%84%D9%88%DA%A9-%D9%87%D8%A7-%D9%88-%D8%AA%D9%88-%D8%B1%D9%81%D8%AA%DA%AF%DB%8C-%D9%87%D8%A7)
  * [انجام دادن یک کار دیگر](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D8%A7%D9%86%D8%AC%D8%A7%D9%85-%D8%AF%D8%A7%D8%AF%D9%86-%DB%8C%DA%A9-%DA%A9%D8%A7%D8%B1-%D8%AF%DB%8C%DA%AF%D8%B1)
    * [بخش‌های داخت توابع](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D8%A8%D8%AE%D8%B4%D9%87%D8%A7%DB%8C-%D8%AF%D8%A7%D8%AE%D8%AA-%D8%AA%D9%88%D8%A7%D8%A8%D8%B9)
  * [یک سطح انتزاع به ازای هر تابع](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%DB%8C%DA%A9-%D8%B3%D8%B7%D8%AD-%D8%A7%D9%86%D8%AA%D8%B2%D8%A7%D8%B9-%D8%A8%D9%87-%D8%A7%D8%B2%D8%A7%DB%8C-%D9%87%D8%B1-%D8%AA%D8%A7%D8%A8%D8%B9)
    * [خواندن کد از بالا به پایین: قاعده گام به گام](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D8%AE%D9%88%D8%A7%D9%86%D8%AF%D9%86-%DA%A9%D8%AF-%D8%A7%D8%B2-%D8%A8%D8%A7%D9%84%D8%A7-%D8%A8%D9%87-%D9%BE%D8%A7%DB%8C%DB%8C%D9%86-%D9%82%D8%A7%D8%B9%D8%AF%D9%87-%DA%AF%D8%A7%D9%85-%D8%A8%D9%87-%DA%AF%D8%A7%D9%85)
  * [Switch Statements](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#switch-statements)
  * [استفاده از نام های توصیفی](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D8%A7%D8%B3%D8%AA%D9%81%D8%A7%D8%AF%D9%87-%D8%A7%D8%B2-%D9%86%D8%A7%D9%85-%D9%87%D8%A7%DB%8C-%D8%AA%D9%88%D8%B5%DB%8C%D9%81%DB%8C)
  * [آرگومان های تابع](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D8%A2%D8%B1%DA%AF%D9%88%D9%85%D8%A7%D9%86-%D9%87%D8%A7%DB%8C-%D8%AA%D8%A7%D8%A8%D8%B9)
    * [فرم رایج Monadic](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D9%81%D8%B1%D9%85-%D8%B1%D8%A7%DB%8C%D8%AC-monadic)
    * [آرگومان های پرچم](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D8%A2%D8%B1%DA%AF%D9%88%D9%85%D8%A7%D9%86-%D9%87%D8%A7%DB%8C-%D9%BE%D8%B1%DA%86%D9%85)
    * [توابع Dyadic](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D8%AA%D9%88%D8%A7%D8%A8%D8%B9-dyadic)
    * [سه آرگومانی](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D8%B3%D9%87-%D8%A2%D8%B1%DA%AF%D9%88%D9%85%D8%A7%D9%86%DB%8C)
    * [آبجکت های آرگومان](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D8%A2%D8%A8%D8%AC%DA%A9%D8%AA-%D9%87%D8%A7%DB%8C-%D8%A2%D8%B1%DA%AF%D9%88%D9%85%D8%A7%D9%86)
    * [لیست های آرگومان](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D9%84%DB%8C%D8%B3%D8%AA-%D9%87%D8%A7%DB%8C-%D8%A2%D8%B1%DA%AF%D9%88%D9%85%D8%A7%D9%86)
    * [افعال و کیوردها](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D8%A7%D9%81%D8%B9%D8%A7%D9%84-%D9%88-%DA%A9%DB%8C%D9%88%D8%B1%D8%AF%D9%87%D8%A7)
  * [نداشتن هیچ عوارض جانبی](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D9%86%D8%AF%D8%A7%D8%B4%D8%AA%D9%86-%D9%87%DB%8C%DA%86-%D8%B9%D9%88%D8%A7%D8%B1%D8%B6-%D8%AC%D8%A7%D9%86%D8%A8%DB%8C)
    * [آرگومان های خروجی](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D8%A2%D8%B1%DA%AF%D9%88%D9%85%D8%A7%D9%86-%D9%87%D8%A7%DB%8C-%D8%AE%D8%B1%D9%88%D8%AC%DB%8C)
  * [جداسازی رایج Query](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D8%AC%D8%AF%D8%A7%D8%B3%D8%A7%D8%B2%DB%8C-%D8%B1%D8%A7%DB%8C%D8%AC-query)
  * [ترجیح Exception ها نسبت به برگرداندن کد خطا](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D8%AA%D8%B1%D8%AC%DB%8C%D8%AD-exception-%D9%87%D8%A7-%D9%86%D8%B3%D8%A8%D8%AA-%D8%A8%D9%87-%D8%A8%D8%B1%DA%AF%D8%B1%D8%AF%D8%A7%D9%86%D8%AF%D9%86-%DA%A9%D8%AF-%D8%AE%D8%B7%D8%A7)
    * [استخراج بلوک های Try/Catch](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D8%A7%D8%B3%D8%AA%D8%AE%D8%B1%D8%A7%D8%AC-%D8%A8%D9%84%D9%88%DA%A9-%D9%87%D8%A7%DB%8C-trycatch)
    * [مدیریت خطا یک چیز است](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D9%85%D8%AF%DB%8C%D8%B1%DB%8C%D8%AA-%D8%AE%D8%B7%D8%A7-%DB%8C%DA%A9-%DA%86%DB%8C%D8%B2-%D8%A7%D8%B3%D8%AA)
    * [آهنربای وابستگی Error.java](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D8%A2%D9%87%D9%86%D8%B1%D8%A8%D8%A7%DB%8C-%D9%88%D8%A7%D8%A8%D8%B3%D8%AA%DA%AF%DB%8C-errorjava)
  * [خود را تکرار نکنید](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D8%AE%D9%88%D8%AF-%D8%B1%D8%A7-%D8%AA%DA%A9%D8%B1%D8%A7%D8%B1-%D9%86%DA%A9%D9%86%DB%8C%D8%AF)
  * [برنامه نویسی ساخت یافته](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D8%A8%D8%B1%D9%86%D8%A7%D9%85%D9%87-%D9%86%D9%88%DB%8C%D8%B3%DB%8C-%D8%B3%D8%A7%D8%AE%D8%AA-%DB%8C%D8%A7%D9%81%D8%AA%D9%87)
  * [چگونه می توانید توابعی مانند این را بنویسید؟](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%DA%86%DA%AF%D9%88%D9%86%D9%87-%D9%85%DB%8C-%D8%AA%D9%88%D8%A7%D9%86%DB%8C%D8%AF-%D8%AA%D9%88%D8%A7%D8%A8%D8%B9%DB%8C-%D9%85%D8%A7%D9%86%D9%86%D8%AF-%D8%A7%DB%8C%D9%86-%D8%B1%D8%A7-%D8%A8%D9%86%D9%88%DB%8C%D8%B3%DB%8C%D8%AF)
  * [نتیجه گیری](https://github.com/Kaaveh/clean-code-persian/blob/master/3_Functions(completed)/3_Functions.md#%D9%86%D8%AA%DB%8C%D8%AC%D9%87-%DA%AF%DB%8C%D8%B1%DB%8C)
  
</div>