![](img-4.1.png)

# کامنت‌ها ۴
<div dir="rtl">
« کد بد را کامنت نکنید – دوباره بنویسید.»
—Brian W. Kernighan and P. J. Plaugher

هیچ چیز نمی‌تواند به اندازه ی یک کامنت که در جای مناسب قرار گرفته مفید باشد. هیچ چیز نمی‌تواند یک ماژول را به اندازه ی کامنت‌های بیهوده به هم بریزد. هیچ چیز نمیتواند مضر تراز یک کامنت ضعیف قدیمی که اطلاعات غلط میدهد باشد.

کامنت‌ها شبیه شیندلرلیست (نام یک فیلم) نیستند . آنها کاملا خوب نیستند. در حقیقت کامنت‌ها جنایت های لازمی هستند .اگر زبان های برنامه نویسی ما به اندازه ی کافی رسا بودند یا ما تونایی استفاده ی ماهرانه از ان زبان ها برای بیان منظور را داشتیم خیلی به کامنت‌ها نیاز نداشتیم . شاید هم اصلا!

کاربرد مناسب کامنت برای جبران شکست رساندن مفهوم با کد است . توجه داشته باشید از واژه شکست استفاده می‌کنم.منظورم این است که کامنت‌ها همیشه نشانه شکست هستند . ما باید از آنها استفاده کنیم چون همیشه راهی برای توضیح دادن منظورمان بدون آنها پیدا نمی کنیم ولی استفاده از آنها دلیلی برای خوشحالی نیست.

وقتی خودتان را در موقعیتی میبینید که کامنت بگذارید، در موردش فکر کنید و ببینید راهی برای عوض کد و توضیح منظورتان در کد وجود ندارد؟ هر بار که میتوانید منظورتان را درخود کد برسانید باید خودتان را تشویق کنید . هر بار که منظورتان را در کامنت توضیح می‌دهید، باید به خودتان دهن کجی کنید واز توانایی بیانتان احساس شکست کنید .

چرا من انقدر با کامنت مخالفم؟چون آنها دروغ میگویند. نه همیشه ونه عمدا،ولی خیلی زیاد.
هر چه کامنت قدیمی تر باشد و از کدی که توصیف میکند دورتر باشد ، بیشتر احتمال دارد که اشتباه باشد.دلیلش ساده است، برنامه نویس ها نمی‌توانند واقع بینانه از انها استفاده کنند.

کد تغییر میکند و تکامل پیدا میکند. تکه های آن جابه جا میشود.آن تکه ها دوشاخه 1 و باز نویسی میشوند و دوباره گرد هم می آیند تا یک چیز خارق العاده را خلق کنند.

متاسفانه کامنت‌ها همیشه آنها را دنبال نمی‌کنند-در واقع نمی‌توانند دنبال کنند.اغلب اوقات از کدی که توصیف می‌کنند فاصله می‌گیرند وتکه های بریده ای میشوند که باعث کاهش مداوم دقت هستند. به طور مثال ، ببینید چه اتفاقی برای این کامنت و کدی که قصد داشت توضیح بدهد افتاد:
</div>

```java
MockRequest request;
private final String HTTP_DATE_REGEXP =
  "[SMTWF][a-z]{2}\\,\\s[0-9]{2}\\s[JFMASOND][a-z]{2}\\s"+
  "[0-9]{4}\\s[0-9]{2}\\:[0-9]{2}\\:[0-9]{2}\\sGMT";
private Response response;
private FitNesseContext context;
private FileResponder responder;
private Locale saveLocale;
```
<div dir="rtl">
بقیه ی متغیر های نمونه احتمالا بعدا بین ثابت HTTP_DATE_REGEXP وکامنت توضیحی آن اضافه شده اند.

می توان این نکته را بیان کرد که برنامه نویسان باید به اندازه کافی نظم و انضباط داشته باشند که کامنت را به روز،مرتبط و دقیق نگه دارند.

من موافق این کار هستم اما ترجیح می‌دهم آنها این انرژی را صرف واضح کردن کد کنند که در وهله اول نیاز به کامنت نداشته باشد.
کامنت‌های نادرست به مراتب بدتر از نبود هیچ کامنتی هستند. آنها خواننده را گمراه می‌کنند. آنها انتظاراتی به وجود می اورند که هیچ وقت براورده نمی‌کنند و قوانینی را مشخص می‌کنند که لازم نیست یا نباید بعد از این دنبال شوند.

حقیقت را در یک جا میتوان یافت:کد. فقط کد میتواند به درستی به شما بگوید چه کاری انجام میدهد.این تنها منبع درست اطلاعات است.بنابراین، با اینکه کامنت‌ها بعضی اوقات لازم اند ، ما انرژی زیادی صرف می‌کنیم تا آنها را به کمترین حد برسانیم.


## کامنت‌ها برای کد بد نوشته نشده اند
یکی از انگیزه های رایج نوشتن کامنت کد بد است. ما یک ماژول می‌نویسیم و می‌دانیم که گیج‌کننده و بی نظم است. می‌دانیم که کثیف است. ما خودمان می‌دانیم و به خود میگوییم:,
«اوه ،بهتراست کامنتش کنم»، نه! بهتراست تمیزش کنی.
 کامنت‌های زیاد بهتر است. به جای اینکه وقتتان را صرف نوشتن کامنت روی کد کثیف کنید که آن را توضیح دهد، صرف تمیز کردنش کنید

## منظورتان را با کد برسانید
مطمئناً مواردی وجود دارد که کد وسیله ی ضعیفی برای توصیف است. متاسفانه بسیاری از برنامه نویسان این را اینطور برداشت کرده اند که کد بندرت میتواند راه خوبی برای توصیف باشد. این به وضوح اشتباه است. شما ترجیح می‌دهید کدام را ببینید؟ این:
</div>

```java
// Check to see if the employee is eligible for full benefits
if ((employee.flags & HOURLY_FLAG) &&
	(employee.age > 65))
```
<div dir="rtl">
یا این؟
</div>

```java
if (employee.isEligibleForFullBenefits())
```
<div dir="rtl">
فقط چند ثانیه زمان میبرد که بیشتر منظورتان را در کد توضیح دهید . در بیشتر موارد این به سادگی ایجاد یک تابع است که همان چیزی را می گوید که با کامنت می خواهید بگویید.

## کامنت‌های خوب
بعضی از کامنت‌ها لازم یا مفید هستند. ما چند مورد را بررسی می‌کنیم که من آنها را لایق بیت هایی که مصرف می‌کنند میدانم. به خاطر داشته باشید، در هر حال، تنها کامنتی که واقعا خوب است کامنتی است که راهی برای ننوشتنش پیدا کنیم.

## کامنت‌های قانونی
گاهی اوقات استاندارد های برنامه نویسی شرکتی ما را مجبور میکند به دلایل قانونی کامنت‌های مشخصی بنویسیم. برای مثال کپی رایت و حق تالیف چیز های منطقی و لازمی هستند برای اینکه اول هر سورس کدی قرار بگیرند.

در اینجا، مثلا، این یک کامنت استاندارد است که درا ول همه سورس ها در FitNesse قرار می‌دهیم. خوشحالم که بگویم IDE ما با از بین بردن این کامنت به طور اتوماتیک، از عمل کردن آن به عنوان یک اخلال گر جلوگیری میکند.
</div>

```java
// Copyright (C) 2003,2004,2005 by Object Mentor, Inc. All rights reserved.
// Released under the terms of the GNU General Public License version 2 or later.
```
<div dir="rtl">
کامنت‌هایی مانند این نباید نوشته شوند. تا جایی که ممکن است، به مجوز های استاندارد یا بقیه ی مدارک خارجی مراجعه شود ، به جای اینکه همه ی آن شرایط و ضوابط را در کامنت قرار دهیم.

## کامنت‌های آموزنده
ارائه ی اطلاعات پایه ای در کامنت مفید است. برای مثال ، به نظر می آید که این کامنت مقدار بازگشتی یک متد abstractرا برمیگرداند .
</div>

```java
// Returns an instance of the Responder being tested.
protected abstract Responder responderInstance();
```
<div dir="rtl">
یک کامنت مثل این گاهی میتواند مفید باشد، اما بهتر است تاجای ممکن برای انتقال اطلاعات از نام تابع استفاده کنیم . مثلا، دراین مورد کامنت می تواند با عوض کردن نام تابع حذف شود. responderBeingTested .
در این مورد کمی بهتر است:
</div>

```java
// format matched kk:mm:ss EEE, MMM dd, yyyy
Pattern timeMatcher = Pattern.compile(
	"\\d*:\\d*:\\d* \\w*, \\w* \\d*, \\d*");
```
<div dir="rtl">
در این مورد کامنت به ما اجازه میدهد بدانیم که این عبارت منظم برای مطابقت زمان و تاریخ در نظر گرفته شده است که با SimpleDateFormat.format  قالب بندی(فرمت) شده است.
تابعی که از فرمت استرینگ معینی استفاده میکند.باز هم میتوانست بهتر باشد ، و واضح تر،اگر این کد به کلاس خاصی که فرمت های تاریخ و زمان را تغییر می دهدمنتقل شده بود ،سپس کامنت احتمالا زیادی میشد.

## شرح نیت

بعضی اوقات یک کامنت فقط از دادن اطلاعات مفید در مورد اجرا فراتر می رود و هدف تصمیم گیری را فراهم می کند. در مورد زیر ، یک تصمیم جالب را می بینیم که توسط یک کامنت مستند شده است. هنگام مقایسه دو شی، ، نویسنده به این نتیجه رسید که می خواهد اشیا کلاس خود را بالاتر از اشیا دیگر مرتب کند.

</div>

```java
public int compareTo(Object o)
{
	if(o instanceof WikiPagePath)
	{
		WikiPagePath p = (WikiPagePath) o;
		String compressedName = StringUtil.join(names, "");
		String compressedArgumentName = StringUtil.join(p.names, "");
		return compressedName.compareTo(compressedArgumentName);
		}
	return 1; // we are greater because we are the right type.
}
```

<div dir="rtl">

در اینجا یک مثال حتی بهتر است. شما ممکن است با راه حل برنامه نویس برای مشکل موافق نباشید ، اما حداقل می دانید که او می خواست چه کاری انجام دهد.

</div>

```java
public void testConcurrentAddWidgets() throws Exception {
	WidgetBuilder widgetBuilder =
	new WidgetBuilder(new Class[]{BoldWidget.class});
	String text = "'''bold text'''";
	ParentWidget parent =
	new BoldWidget(new MockWidgetRoot(), "'''bold text'''");
	AtomicBoolean failFlag = new AtomicBoolean();
	failFlag.set(false);
	//This is our best attempt to get a race condition
	//by creating large number of threads.
	for (int i = 0; i < 25000; i++) {
		WidgetBuilderThread widgetBuilderThread =
		new WidgetBuilderThread(widgetBuilder, text, parent, failFlag);
		Thread thread = new Thread(widgetBuilderThread);
		thread.start();
	}
	assertEquals(false, failFlag.get());
}
```

<div dir="rtl">

## شفاف سازی

گاهی اوقات فقط ترجمه معنای برخی از آرگومان‌های مبهم یا بازگردان مقدار به چیزی که قابل فهمیدن بوده، مفید است. به طور کلی ، بهتر است راهی پیدا کنید که آن آرگومان یا مقدار بازگشتی را به خودی خود روشن کند. اما اگر بخشی از آن در کتابخانه استاندارد باشد یا در کدی باشد که نمی توانید تغییر دهید ، یک توضیح روشن و خوب می تواند مفید باشد.

</div>

```java
public void testCompareTo() throws Exception
{
	WikiPagePath a = PathParser.parse("PageA");
	WikiPagePath ab = PathParser.parse("PageA.PageB");
	WikiPagePath b = PathParser.parse("PageB");
	WikiPagePath aa = PathParser.parse("PageA.PageA");
	WikiPagePath bb = PathParser.parse("PageB.PageB");
	WikiPagePath ba = PathParser.parse("PageB.PageA");
	assertTrue(a.compareTo(a) == 0);       // a == a
	assertTrue(a.compareTo(b) != 0);       // a != b
	assertTrue(ab.compareTo(ab) == 0);     // ab == ab
	assertTrue(a.compareTo(b) == -1);      // a < b
	assertTrue(aa.compareTo(ab) == -1);    // aa < ab
	assertTrue(ba.compareTo(bb) == -1);    // ba < bb
	assertTrue(b.compareTo(a) == 1);       // b > a
	assertTrue(ab.compareTo(aa) == 1);     // ab > aa
	assertTrue(bb.compareTo(ba) == 1);     // bb > ba
}
```

<div dir="rtl">

البته یک خطر اساسی وجود دارد که یک کامنت روشن نادرست باشد. مثال قبلی را مرور کنید و ببینید تایید صحت آنها چقدر دشوار است. هم شفاف‌سازی لازم است و هم اینکه چرا خطرناک است. بنابراین قبل از نوشتن کامنت‌هایی از این دست ، مراقب باشید که راهی بهتر وجود نداشته باشد و حتی بیشتر دقت کنید که درست باشند.

</div>

![](img-4.2.png)

<div dir="rtl">

## هشدار پیامدها

گاهی اوقات مفید است که به سایر برنامه نویسان در مورد عواقب خاص هشدار دهید. به عنوان مثال ، در اینجا یک کامنت وجود دارد که توضیح می دهد چرا یک مورد آزمایشی خاص خاموش است:

</div>

```java
// Don't run unless you
// have some time to kill.
public void _testWithReallyBigFile()
{
	writeLinesToFile(10000000);
	response.setBody(testFile);
	response.readyToSend(this);
	String responseString = output.toString();
	assertSubString("Content-Length: 1000000000", responseString);
	assertTrue(bytesSent > 1000000000);
}
```
<div dir="rtl">

البته امروزه ، ما می توانیم با استفاده از ویژگی @Ignore با یک رشته توضیحی مناسب ، مورد آزمایشی را خاموش کنیم. @Ignore ("برای اجرای خیلی طولانی می شود"). اما در روزهای قبل از JUnit4 ، قرار دادن underscore در مقابل نام متد یک امر عادی بود. این کامنت هر چند گنگ است ، اما نکته را به خوبی بیان می کند.در اینجا مثال مهیج تر دیگری وجود دارد:

</div>

```java
public static SimpleDateFormat makeStandardHttpDateFormat()
{
	//SimpleDateFormat is not thread safe,
	//so we need to create each instance independently.
	SimpleDateFormat df = new SimpleDateFormat("EEE, dd MMM yyyy HH:mm:ss z");
	df.setTimeZone(TimeZone.getTimeZone("GMT"));
	return df;
}
```

<div dir="rtl">

ممکن است شکایت کنید که روش های بهتری برای حل این مشکل وجود دارد. ممکن است با شما موافق باشم اما کامنت ، همانطور که در اینجا ارائه شد ، کاملاً منطقی است. این باعث می شود که برخی از برنامه نویسان بیش از حد مشتاق از یک مقداردهنده اولیه ثابت برای کارایی استفاده نکنند.

## TODO کامنت‌های

گاهی اوقات منطقی است که یادداشت های "TODO" را در قالب کامنت‌های TODO // انجام دهید. در مورد زیر ، کامنت‌های TODO توضیح می دهد که چرا این تابع یک اجرای منحط دارد و آینده آن تابع چگونه است.

</div>

```java
//TODO-MdM these are not needed
// We expect this to go away when we do the checkout model
protected VersionInfo makeVersion() throws Exception
{
	return null;
}
```

<div dir="rtl">

TODO کارهایی است که به نظر برنامه نویس باید انجام شود ، اما به دلایلی فعلاً نمی تواند انجام دهد. این ممکن است یک یادآوری برای حذف یک ویژگی منسوخ شده یا یک درخواست برای شخص دیگری برای بررسی یک مشکل باشد. این ممکن است درخواستی باشد که شخص دیگری به نام بهتر فکر کند یا یادآوری باشد برای ایجاد تغییری وابسته به یک برنامه ریزی. TODO هرچه باشد ، بهانه ای برای گذاشتن کد بد در سیستم نیست.

امروزه ، اکثر IDE های خوب ویژگی های خاصی را برای یافتن همه کامنت‌های TODO ارائه می دهند ، بنابراین احتمالاً گم نمی شوند. اگر هم نمی خواهید کد شما با TODO پر شود، مرتباً از طریق آنها اسکن کرده و مواردی را که می توانید حذف کنید.

## تقویت

ممکن است کامنت برای تقویت اهمیت چیزی استفاده شود که در غیر این صورت بی اهمیت به نظر می رسد.

</div>

```java
String listItemContent = match.group(3).trim();
// the trim is real important. It removes the starting
// spaces that could cause the item to be recognized
// as another list.
new ListItemWidget(this, listItemContent, this.level + 1);
return buildList(text.substring(match.end()));
```

<div dir="rtl">

## اسناد java در API های عمومی

هیچ چیز به اندازه یک API عمومی خوش‌توضیح، مفید و رضایت بخش وجود ندارد. javadocs برای کتابخانه استاندارد جاوا نمونه ای از این موارد است. در بهترین حالت نوشتن برنامه های جاوا بدون آنها دشوار خواهد بود.

اگر در حال نوشتن یک API عمومی هستید ، مطمئناً باید javadocs خوبی برای آن بنویسید. اما بقیه توصیه های این فصل را به خاطر بسپارید. Javadocs می تواند مانند هر نوع نظر دیگر گمراه کننده ، غیرمحلی و غیر صادق باشد.

# کامنت‌های بد

بیشتر کامنت‌ها در این گروه قرار می گیرند. معمولاً آنها بهانه‌ای برای کد ضعیف یا توجیهی برای تصمیمات ناکافی هستند، کمی بیشتر از صحبت های برنامه نویس با خودش.

## غرزدن

یهویی کامنتی نوشتن فقط به این دلیل که احساس می کنید باید این کار را انجام دهید یا این که روند کار به آن نیاز دارد، جالب نیست. اگر تصمیم دارید یک کامنت بنویسید ، وقت لازم را صرف کنید تا مطمئن شوید بهترین کامنتی است که می توانید بنویسید.

به عنوان مثال ، این مورد موردی است که من در FitNesse پیدا کردم ، جایی که یک کامنت واقعاً مفید بوده است. اما نویسنده عجله داشت یا فقط توجه زیادی نمی‌کرد. غر زدن او یک معما را پشت سر گذاشت:

</div>

```java
public void loadProperties()
{
	try
	{
		String propertiesPath = propertiesLocation + "/" + PROPERTIES_FILE;
		FileInputStream propertiesStream = new FileInputStream(propertiesPath);
		loadedProperties.load(propertiesStream);
	}
	catch(IOException e)
	{
		// No properties files means all defaults are loaded
	}
}
```

<div dir="rtl">

این کامنت در بلوک catch به چه معناست؟ واضح است که این برای نویسنده معنی داشته است ، اما معنی آن واضح نیست. ظاهراً ، اگر IOException دریافت کنیم ، به این معنی است که هیچ فایلی وجود نداشته است. و در این حالت تمام پیش فرض ها بارگیری می شوند. اما چه کسی تمام پیش فرض ها را بارگیری می کند؟ آیا آنها قبل از صدازدن loadProperties.load بارگیری شده اند؟ یا آیا loadProperties.load استثنا را گرفت ، پیش فرض ها را بارگذاری کرد و سپس استثنا را به ما منتقل کرد تا نادیده بگیریم؟ یا آیا loadProperties.load قبل از بارگیری فایل ، همه پیش فرض ها را بارگیری کرده است؟ آیا نویسنده سعی در دلجویی از این واقعیت داشت که بلوک catch را خالی می گذارد؟ یا - و این احتمال ترسناک است - آیا نویسنده سعی داشته به خودش بگوید بعداً به اینجا برگردد و کدی را بنویسد که پیش فرض ها را بارگیری کند؟

تنها راه حل ما این است که کد را در قسمت های دیگر سیستم بررسی کنیم تا بفهمیم چه خبر است. هر کامنتی که شما را مجبور کند به دنبال معنای آن کامنت در یک ماژول دیگر بگردید ، در برقراری ارتباط با شما ناموفق بوده و ارزش بیت های مصرفی آن را ندارد.

## کامنت‌های اضافی

لیست 4-1 تابع ساده ای را با یک عنوان هدر کاملاً زائد نشان می دهد.
خواندن این کامنت احتمالاً طولانی تر از خود کد است.

</div>

Listing 4-1

waitForClose
```java
// Utility method that returns when this.closed is true. Throws an exception
// if the timeout is reached.
public synchronized void waitForClose(final long timeoutMillis)
throws Exception
{
	if(!closed)
	{
		wait(timeoutMillis);
		if(!closed)
		throw new Exception("MockResponseSender could not be closed");
	}
}
```
<div dir="rtl">

این کامنت چه هدفی را دنبال می کند؟ مطمئناً از کد بیشتر آموزنده نیست. این کد را توجیه نمی کند ، یا قصد یا منطقی را ارائه نمی دهد. خواندن آن از کد آسان نیست. در حقیقت ، دقت آن کمتر از کد است و خواننده را فریب می دهد که به جای درک درست ، عدم دقت را بپذیرد. این کار دقیقاً مانند این است که یک فروشنده ماشین دست دوم خوشحال به شما اطمینان دهد که نیازی به دیدن زیر کاپوت نیست.

اکنون javadocs بی فایده و زائد را در لیست 4-2 برگرفته از تامکت در نظر بگیرید. این کامنت‌ها فقط برای بهم ریختن و پنهان کردن کد کار می کنند. اصلاً هدف مستندی ندارند. برای بدتر کردن ، من فقط چند مورد اول را به شما نشان دادم. تعداد بیشتری در این ماژول وجود دارد.

</div>

Listing 4-2

ContainerBase.java (Tomcat)
```java
public abstract class ContainerBase
	implements Container, Lifecycle, Pipeline,
	MBeanRegistration, Serializable {
	/**
	* The processor delay for this component.
	*/
	protected int backgroundProcessorDelay = -1;
	/**
	* The lifecycle event support for this component.
	*/
	protected LifecycleSupport lifecycle =
	new LifecycleSupport(this);
	/**
	* The container event listeners for this Container.
	*/
	protected ArrayList listeners = new ArrayList();
	/**
	* The Loader implementation with which this Container is
	* associated.
	*/
	protected Loader loader = null;
	/**
	* The Logger implementation with which this Container is
	* associated.
	*/
	protected Log logger = null;
	/**
	* Associated logger name.
	*/
	protected String logName = null;
	/**
	* The Manager implementation with which this Container is
	* associated.
	*/
	protected Manager manager = null;
	/**
	* The cluster with which this Container is associated.
	*/
	protected Cluster cluster = null;
	/**
	* The human-readable name of this Container.
	*/
	protected String name = null;
	/**
	* The parent Container to which this Container is a child.
	*/
	protected Container parent = null;
	/**
	* The parent class loader to be configured when we install a
	* Loader.
	*/
	protected ClassLoader parentClassLoader = null;
	/**
	* The Pipeline object with which this Container is
	* associated.
	*/
	protected Pipeline pipeline = new StandardPipeline(this);
	/**
	* The Realm with which this Container is associated.
	*/
	protected Realm realm = null;
	/**
	* The resources DirContext object with which this Container
	* is associated.
	*/
	protected DirContext resources = null;
}
```

<div dir="rtl">

## کامنت‌های گمراه کننده

گاهی اوقات ، با بهترین آرزوها ، یک برنامه نویس بیانیه ای را در کامنت‌های خود ارائه می دهد که دقیق نیست. لیست ۴-۲ را درنظر بگیرید.

آیا کشف کردید که چگونه این کامنت گمراه کننده است؟ وقتی this.closed درست است، این متد چیزی برنمی گرداند. اگر this.closed درست باشد ، بر می گردد. در غیر این صورت ، منتظر تایم اوت است و اگر this.closed همچنان درست نباشد، exception پرتاب می‌شود.

این اطلاعات نادرست ، که در کامنتی ارائه می شود که خواندن آن دشوارتر از متن کد است ، می تواند باعث شود تا برنامه نویس دیگری با خیال راحت این تابع را  صدا زند. آن برنامه نویس ضعیف سپس خود را درحال رفع اشکال پیدا می کند و می خواهد بفهمد چرا کد او به این کندی اجرا شده است.

## کامنت‌های مجاز

این یک قانون احمقانه‌ای است که هر تابع باید یک javadoc، یا هر متغیر باید یک کامنت داشته باشد. کامنت‌هایی از این دست فقط کد را بهم می ریزند ، دروغ ها را تبلیغ می کنند ، و باعث سردرگمی و بی نظمی می شوند.

به عنوان مثال ، javadocs مورد نیاز برای هر تابع منجر به مکروهاتی مانند لیست 4-3 می شود. این بی نظمی چیزی اضافه نمی کند و فقط باعث کدرشدن کد و ایجاد پتانسیل دروغ وسوتفاهم می‌شود.

</div>

Listing 4-3
```java
/**
*
* @param title The title of the CD
* @param author The author of the CD
* @param tracks The number of tracks on the CD
* @param durationInMinutes The duration of the CD in minutes
*/
public void addCD(String title, String author,
		int tracks, int durationInMinutes) {
	CD cd = new CD();
	cd.title = title;
	cd.author = author;
	cd.tracks = tracks;
	cd.duration = duration;
	cdList.add(cd);
}
```

<div dir="rtl">

## کامنت‌های گزارشی

گاهی اوقات افراد هر بار که ویرایش می کنند یک کامنت به شروع ماژول اضافه می کنند. این کامنت‌ها به عنوان نوعی ژورنال ، یا گزارش ، از هر تغییری که ایجاد شده است جمع می شود. من چند ماژول با ده ها صفحه از این ورودی های ژورنال دیده ام.

</div>

```
Changes (from 11-Oct-2001)
--------------------------
* 11-Oct-2001 : Re-organised the class and moved it to new package
* com.jrefinery.date (DG);
* 05-Nov-2001 : Added a getDescription() method, and eliminated NotableDate
* class (DG);
* 12-Nov-2001 : IBD requires setDescription() method, now that NotableDate
* class is gone (DG); Changed getPreviousDayOfWeek(),
* getFollowingDayOfWeek() and getNearestDayOfWeek() to correct
* bugs (DG);
* 05-Dec-2001 : Fixed bug in SpreadsheetDate class (DG);
* 29-May-2002 : Moved the month constants into a separate interface
* (MonthConstants) (DG);
* 27-Aug-2002 : Fixed bug in addMonths() method, thanks to N???levka Petr (DG);
* 03-Oct-2002 : Fixed errors reported by Checkstyle (DG);
* 13-Mar-2003 : Implemented Serializable (DG);
* 29-May-2003 : Fixed bug in addMonths method (DG);
* 04-Sep-2003 : Implemented Comparable. Updated the isInRange javadocs (DG);
* 05-Jan-2005 : Fixed bug in addYears() method (1096282) (DG);
```

<div dir="rtl">

مدت ها پیش دلیل خوبی برای ایجاد و نگهداری این ورودی های log در ابتدای هر ماژول وجود داشت. ما سیستم های کنترل کد منبع نداشتیم که این کار را برای ما انجام دهند. امروزه ، این ژورنال‌های طولانی فقط به ماژول آشفتگی اضافه می‌کنند. باید کاملاً برداشته شوند.

## کامنت‌های شلوغ

بعضی اوقات کامنت‌هایی را می بینید که چیزی جز سر و صدا نیست. موارد واضحی را بیان می کنند و هیچ اطلاعات جدیدی ارائه نمی دهند.

</div>

```java
	/**
	* Default constructor.
	*/
	protected AnnualDateRule() {
	}
```

<div dir="rtl">

نه، واقعا؟ یا چگونه در مورد این:

</div>

```java
	/** The day of the month. */
	private int dayOfMonth;
```

<div dir="rtl">

و سپس این مثال اضافی وجود دارد:

</div>

```java
	/**
	* Returns the day of the month.
	*
	* @return the day of the month.
	*/
	public int getDayOfMonth() {
		return dayOfMonth;
	}
```

<div dir="rtl">

این کامنت‌ها آنقدر پر سر و صدا هستند که یاد می گیریم آنها را نادیده بگیریم. وقتی کد را می خوانیم ، چشمانمان به راحتی از روی آنها عبور می کنند. سرانجام با تغییر کد پیرامون ، کامنت‌ها شروع به دروغ گفتن می کنند.

اولین کامنت در لیست 4-4 مناسب به نظر می رسد. دلیل نادیده گرفته شدن بلوک catch را توضیح می دهد. اما کامنت دوم کاملا سر و صدا است. ظاهراً برنامه نویس از نوشتن بلوک های try / catch در این تابع آنقدر ناامید شده بود که نیاز به تخلیه داشت.

</div>

Listing 4-4

startSending

```java
private void startSending()
{
	try
	{
		doSending();
	}
	catch(SocketException e)
	{
		// normal. someone stopped the request.
	}
	catch(Exception e)
	{
		try
		{
			response.add(ErrorResponder.makeExceptionString(e));
			response.closeAll();
		}
		catch(Exception e1)
		{
			//Give me a break!
		}
	}
}
```

<div dir="rtl">

به جای تخلیه کامنت‌های بی ارزش و پر سر و صدا ، برنامه نویس باید تشخیص می داد که با بهبود ساختار کد خود می تواند ناامیدی او را برطرف کند. باید انرژی خود را به استخراج آخرین بلوک try / catch به یک تابع جداگانه هدایت کند ، همانطور که در لیست 4-5 نشان داده شده است.

</div>

Listing 4-5
```java
startSending (refactored)
private void startSending()
{
	try
	{
		doSending();
	}
	catch(SocketException e)
	{
		// normal. someone stopped the request.
	}
	catch(Exception e)
	{
		addExceptionAndCloseResponse(e);
	}
}
private void addExceptionAndCloseResponse(Exception e)
{
	try
	{
		response.add(ErrorResponder.makeExceptionString(e));
		response.closeAll();
	}
	catch(Exception e1)
	{
	}
}
```

<div dir="rtl">

وسوسه ایجاد نویز را با تصمیم برای پاک کردن کد خود جایگزین کنید. خواهید فهمید که این باعث می شود شما یک برنامه نویس بهتر و شاد باشید.

## شلوغی هولناک

Javadocs همچنین می تواند پر سر و صدا باشد. Javadocs زیر (از یک کتابخانه منبع باز مشهور) چه هدفی را دنبال می کند؟ جواب: هیچی. فقط کامنت‌های پر سر و صداي زائدي هستند كه به دليل تمايل بي جا به ارائه مستندات نوشته شده اند.

</div>

```java
/** The name. */
private String name;
/** The version. */
private String version;
/** The licenceName. */
private String licenceName;
/** The version. */

private String info;
```

<div dir="rtl">

این کامنت‌ها را با دقت بیشتری دوباره بخوانید. خطای cut-paste را مشاهده می کنید؟ اگر نویسندگان هنگام نوشتن کامنت‌ها (یا چسباندن) توجه نمی کنند ، چرا از خوانندگان انتظار می رود که از آنها سود ببرند؟

## زمانی که میتوانید از یک تابع یا متغییر استفاده کنید از کامنت‌ها استفاده نکنید

بخش زیر کد را در نظر بگیرید:

</div>

```java
// does the module from the global list <mod> depend on the
// subsystem we are part of?
if (smodule.getDependSubsystems().contains(subSysMod.getSubSystem()))
```

<div dir="rtl">

بدون تفسیر می توان این را دوباره بیان کرد

</div>

```java
ArrayList moduleDependees = smodule.getDependSubsystems();
String ourSubSystem = subSysMod.getSubSystem();
if (moduleDependees.contains(ourSubSystem))
```

<div dir="rtl">

نویسنده کد اصلی ممکن است ابتدا کامنت را نوشته باشد (بعید است) و سپس کد را برای تحقق کامنت نوشته باشد. با این حال ، نویسنده باید همانند من کدها را مجدداً ویرایش می‌کرد تا بتواند کامنت را حذف کند.

## نشانگرهای موقعیت

گاهی اوقات برنامه نویسان دوست دارند موقعیت خاصی را در یک فایل منبع علامت گذاری کنند. به عنوان مثال ، من اخیراً این را در برنامه ای یافتم که در جستجوی آن بودم:

</div>

```java
// Actions //////////////////////////////////
```

<div dir="rtl">

موارد نادری وجود دارد که جمع آوری برخی کارها در زیر یک بنر مانند این منطقی باشد. اما به طور کلی، بی نظمی هستند که باید از بین بروند - به ویژه قطار پر سر و صدا اسلش در انتها.

اینجوری فکر کن اگر شما اغلب بنرها را مشاهده نکنید ، یک بنر حیرت انگیز و واضح است. بنابراین خیلی کم و فقط در صورت سودمند بودن از آنها استفاده کنید. اگر بیش از اندازه از بنرها استفاده نکنید ، در سر و صدای پس زمینه قرار می گیرند و نادیده گرفته می شوند.

## کامنت‌های بستن آکولاد

بعضی اوقات ، برنامه نویسان نظیر لیست 4-6 ، کامنت‌های ویژه ای در مورد آکولاد‌های بسته می‌نهند. اگرچه این ممکن است برای توابع طولانی با ساختارهای کاملاً تو در تو منطقی باشد ، اما در انواع توابع کوچک و محصور شده فقط منجر به  بهم ریختن می‌شود. بنابراین اگر متوجه شدید که می خواهید آکولادهای بسته خود را مشخص کنید ، سعی کنید در عوض توابع خود را کوتاه کنید.

</div>

Listing 4-6

wc.java

```java
public class wc {
	public static void main(String[] args) {
		BufferedReader in = new BufferedReader(new InputStreamReader(System.in));
		String line;
		int lineCount = 0;
		int charCount = 0;
		int wordCount = 0;
		try {
			while ((line = in.readLine()) != null) {
				lineCount++;
				charCount += line.length();
				String words[] = line.split("\\W");
				wordCount += words.length;
			} //while
			System.out.println("wordCount = " + wordCount);
			System.out.println("lineCount = " + lineCount);
			System.out.println("charCount = " + charCount);
		} // try
		catch (IOException e) {
			System.err.println("Error:" + e.getMessage());
		} //catch
	} //main
}
```

<div dir="rtl">

## خصیصه‌ها و خطوط معرف نویسنده کد

</div>


```java
/* Added by Rick */
```

<div dir="rtl">

سیستم های کنترل کد منبع در به خاطر سپردن اینکه چه کسی چه چیزی را اضافه کرده است ، بسیار خوب است. نیازی به آلوده سازی کد با کمترین bylines نیست. ممکن است فکر کنید چنین کامنت‌هایی برای کمک به دیگران در دانستن اینکه با چه کسی در مورد کد صحبت می کنند مفید باشد. اما واقعیت این است که سالها و سالها در اطراف بمانند ، هرچه دقیق تر و کم اهمیت تر می شوند.

باز هم ، سیستم کنترل کد منبع مکان بهتری برای این نوع اطلاعات است.

## کامنت کردن کد

تعداد کمی از اعمال به اندازه کد توضیح دادن کراهت دارند. این کار را نکنید!

</div>

```java
// InputStreamResponse response = new InputStreamResponse();
// response.setBody(formatter.getResultStream(), formatter.getByteCount());
// InputStream resultsStream = formatter.getResultStream();
// StreamReader reader = new StreamReader(resultsStream);
// response.setContent(reader.read(formatter.getByteCount()));
```

<div dir="rtl">

دیگران که این کد کامنت شده را می بینند ، جرات حذف آن را ندارند. آنها فکر می کنند آنجا به دلایلی وجود دارد و حذف آنها بسیار خطرناک است. بنابراین کد کامنت شده مانند خاکه ته یک بطری بد شراب جمع می شود.

این را از apache commons در نظر بگیرید:

</div>

```java
this.bytePos = writeBytes(pngIdBytes, 0);
//hdrPos = bytePos;
writeHeader();
writeResolution();
//dataPos = bytePos;
if (writeImageData()) {
	writeEnd();
	this.pngBytes = resizeByteArray(this.pngBytes, this.maxPos);
}
else {
	this.pngBytes = null;
}
return this.pngBytes;
```

<div dir="rtl">

چرا آن دو خط کد کامنت داده شده است؟ آیا آنها مهم هستند؟ آیا آنها به عنوان یادآوری برای برخی تغییرات قریب الوقوع باقی مانده بودند؟ یا اینها فقط ظلم هایی هستند که کسی سالها پیش در مورد آنها کامنت داده و زحمت تمیز کردنش را نکشیده است.

زمانی در دهه شصت بود که ممکن است کد کامنت شده مفید باشد. اما مدت زمان زیادی است که سیستم های کنترل کد منبع خوبی داریم. آن سیستم ها کد را برای ما به خاطر می آورند. دیگر لازم نیست درباره آن توضیح دهیم. فقط کد را حذف کنید. ما آن را از دست نخواهیم داد. قول می‌دهم.

## HTML کامنت‌های

همانطور که می توانید با خواندن کد زیر متوجه شوید HTML در کامنت‌های کد منبع مکروه است. خواندن کامنت‌ها در مکانی که خواندن آنها آسان است - ادیتور / IDE - را دشوار می کند. اگر قرار است کامنت‌ها توسط برخی از ابزارها (مانند Javadoc) برای نمایش در یک صفحه وب استخراج شود ، تزیین کامنت‌ها با HTML مناسب باید به عهده آن ابزار باشد و نه برنامه نویس.

</div>

```java
/**
* Task to run fit tests.
* This task runs fitnesse tests and publishes the results.
* <p/>
* <pre>
* Usage:
* &lt;taskdef name=&quot;execute-fitnesse-tests&quot;
*
classname=&quot;fitnesse.ant.ExecuteFitnesseTestsTask&quot;
*
classpathref=&quot;classpath&quot; /&gt;
* OR
* &lt;taskdef classpathref=&quot;classpath&quot;
*
resource=&quot;tasks.properties&quot; /&gt;
* <p/>
* &lt;execute-fitnesse-tests
*
suitepage=&quot;FitNesse.SuiteAcceptanceTests&quot;
*
fitnesseport=&quot;8082&quot;
*
resultsdir=&quot;${results.dir}&quot;
*
resultshtmlpage=&quot;fit-results.html&quot;
*
classpathref=&quot;classpath&quot; /&gt;
* </pre>
*/
```

<div dir="rtl">

## اطلاعات غیرمحلی

اگر لازم است یک کامنت بنویسید، پس مطمئن شوید که کامنت شما کد اطراف خودش را توضیح میدهد. در یک کامنت محلی نیازی نیست اطلاعات بین المللی به خواننده بدهید، همانقدر که آن قسمت از کد را توضیح دهید کفایت میکند. فرضا این کامنت در مثال جاوایی زیر را درنظر بگیرید. با اینکه به طور ترسناکی زائد به نظر میرسد، اما اطلاعات خوبی درباره پورت پیشفرض برنامه به استفاده کننده میدهد. تابع مطلقا کنترلی روی اینکه پیشفرضش چه باشد ندارد. این کامنت ، تابع را توضیح نمیدهد و در حقیقت چیزی که این کامنت توضیح میدهد در نقطه ای دورتر از این قسمت قرار دارد. مطمئنا هیچ تضمینی نیست که اگر پورت پیشفرض برنامه عوض شد، این کامنت هم تغییر کند.

</div>

```java
/**
* Port on which fitnesse would run. Defaults to <b>8082</b>.
*
* @param fitnessePort
*/
public void setFitnessePort(int fitnessePort)
{
	this.fitnessePort = fitnessePort;
}
```

<div dir="rtl">

## اطلاعات بیش از اندازه

بحث های جذاب تاریخی و توصیف های بی ربطتان را در جایی غیر از کامنت‌هایتان قرار دهید. کامنت زیر را در یک ماژول پیدا کردیم که طراحی شده بود برای تست یک تابع که کارش انکد و دیکد کردن base64 است. به جز کد RFC، بقیه نوشته ها اضافی هستند و کسی که این کد را میخواند نیازی به داشتن این اطلاعات مسخره ندارد.

</div>

```java
/*
	RFC 2045 - Multipurpose Internet Mail Extensions (MIME)
	Part One: Format of Internet Message Bodies
	section 6.8. Base64 Content-Transfer-Encoding
	The encoding process represents 24-bit groups of input bits as output
	strings of 4 encoded characters. Proceeding from left to right, a
	24-bit input group is formed by concatenating 3 8-bit input groups.
	These 24 bits are then treated as 4 concatenated 6-bit groups, each
	of which is translated into a single digit in the base64 alphabet.
	When encoding a bit stream via the base64 encoding, the bit stream
	must be presumed to be ordered with the most-significant-bit first.
	That is, the first bit in the stream will be the high-order bit in
	the first 8-bit byte, and the eighth bit will be the low-order bit in
	the first 8-bit byte, and so on.
*/
```

<div dir="rtl">

## ارتباط نامشخص

ارتباط بین کامنت و کدی که در حال توضیح آن است باید واضح باشد. اگر قصد کامنت نوشتن دارید به این نکته توجه کنید که خواننده کد باید بتواند با نگاه کردن به کد بفهمد که شما دقیقا دارید درباره کدام قسمت توضیح می‌دهید.
مثلا این کامنت از apache commons بیرون کشیده شده:

</div>

```java
/*
* start with an array that is big enough to hold all the pixels
* (plus filter bytes), and an extra 200 bytes for header info
*/
this.pngBytes = new byte[((this.width + 1) * this.height * 3) + 200];
```

<div dir="rtl">

اینجا filter byte چیست؟ آیا مربوط میشود به +1 یا به *3؟ یا اصلا به هر دو؟ آیا هر پیکسل یک بایت است؟ چرا 200؟ کامنت برای کدی استفاده میشود که خودش، خودش را توضیح نمیدهد، اینجا باید کامنت دیگری بنویسیم که این کامنت را توضیح دهد!

## عناوین تابع

توابع کوچک نیاز به توضیحات زیادی ندارند. یک اسم که خوب اتخاب شود برای یک تابع کوچک بسیار مفید تر از یک کامنت طولانی است.

## اسناد java در کد غیرعمومی

همانقدر که jovadoc ها برای api های عمومی مناسب هستند، برای کد هایی که عمومی نیستند غیر مفیدند. تولید کردن javadoc برای کلاس ها و تابع ها در یک سیستم آنقدر ها هم مفید نیست، و زیاد بودن javadoc ها هم چیزی جز حواس پرتی به ارمغان نمیاورد.

## مثال

من ماژولی که در Listing 4-7 هست را نوشته ام برای اولین تجربه شما. قصد این ماژول، بودن مثالی برای کدنویسی بد و سبک کامنت نویسی است. سپس Kent Beck این کد را جلوی چندین دانشجوی مشتاق به شکل بسیار پسندیده تری ریفکتور کرده. بعدتر من از این مثال برای کتاب خودم یعنی Agile Software Development, Principles, Patterns, and Practices استفاده کردم.
چیزی که درمورد این کد جالب است این است که ما در ابتدا آن را کاملا مستند فرض میکردیم، در حالی که الان آن را یک آشفتگی کوچک می‌دانیم. ببینید چند مشکل مختلف در کامنت گذاری این کد میتوانید پیدا کنید.

</div>

Listing 4-7

GeneratePrimes.java
```java
/**
* This class Generates prime numbers up to a user specified
* maximum. The algorithm used is the Sieve of Eratosthenes.
* <p>
* Eratosthenes of Cyrene, b. c. 276 BC, Cyrene, Libya --
* d. c. 194, Alexandria. The first man to calculate the
* circumference of the Earth. Also known for working on
* calendars with leap years and ran the library at Alexandria.
* <p>
* The algorithm is quite simple. Given an array of integers
* starting at 2. Cross out all multiples of 2. Find the next
* uncrossed integer, and cross out all of its multiples.
* Repeat untilyou have passed the square root of the maximum
* value.
*
* @author Alphonse
* @version 13 Feb 2002 atp
*/
import java.util.*;
public class GeneratePrimes
{
	/**
	* @param maxValue is the generation limit.
	*/
	public static int[] generatePrimes(int maxValue)
	{
		if (maxValue >= 2) // the only valid case
		{
			// declarations
			int s = maxValue + 1; // size of array
			boolean[] f = new boolean[s];
			int i;
			// initialize array to true.
			for (i = 0; i < s; i++)
			f[i] = true;
			// get rid of known non-primes
			f[0] = f[1] = false;
			// sieve
			int j;
			for (i = 2; i < Math.sqrt(s) + 1; i++)
			{
				if (f[i]) // if i is uncrossed, cross its multiples.
				{
					for (j = 2 * i; j < s; j += i)
					f[j] = false; // multiple is not prime
				}
			}
			// how many primes are there?
			int count = 0;
			for (i = 0; i < s; i++)
			{
				if (f[i])
				count++; // bump count.
			}
			int[] primes = new int[count];
			// move the primes into the result
			for (i = 0, j = 0; i < s; i++)
			{
				if (f[i])
				// if prime
				primes[j++] = i;
			}
			return primes; // return the primes
		}
		else // maxValue < 2
		return new int[0]; // return null array if bad input.
	}
}
```

<div dir="rtl">

در Listing 4-8 میتوانید یک نسخه بازنویسی شده از همان ماژول قبلی را ببینید. دقت کنید که استفاده از کامنت به طور قابل توجهی مهار شده و فقط دو کامنت در این کد دیده میشود. هر دو کامنت ماهیت توضیح دادن دارند.

</div>

Listing 4-8

PrimeGenerator.java (refactored)
```java
/**
* This class Generates prime numbers up to a user specified
* maximum. The algorithm used is the Sieve of Eratosthenes.
* Given an array of integers starting at 2:
* Find the first uncrossed integer, and cross out all its
* multiples. Repeat until there are no more multiples
* in the array.
*/
public class PrimeGenerator
{
	private static boolean[] crossedOut;
	private static int[] result;
	public static int[] generatePrimes(int maxValue)
	{
		if (maxValue < 2)
		return new int[0];
		else
		{
			uncrossIntegersUpTo(maxValue);
			crossOutMultiples();
			putUncrossedIntegersIntoResult();
			return result;
		}
	}
	private static void uncrossIntegersUpTo(int maxValue)
	{
		crossedOut = new boolean[maxValue + 1];
		for (int i = 2; i < crossedOut.length; i++)
		crossedOut[i] = false;
	}
	private static void crossOutMultiples()
	{
		int limit = determineIterationLimit();
		for (int i = 2; i <= limit; i++)
		if (notCrossed(i))
		crossOutMultiplesOf(i);
	}
	private static int determineIterationLimit()
	{
		// Every multiple in the array has a prime factor that
		// is less than or equal to the root of the array size,
		// so we don't have to cross out multiples of numbers
		// larger than that root.
		double iterationLimit = Math.sqrt(crossedOut.length);
		return (int) iterationLimit;
	}
	private static void crossOutMultiplesOf(int i)
	{
		for (int multiple = 2*i;
		multiple < crossedOut.length;
		multiple += i)
		crossedOut[multiple] = true;
	}
	private static boolean notCrossed(int i)
	{
		return crossedOut[i] == false;
	}
	private static void putUncrossedIntegersIntoResult()
	{
		result = new int[numberOfUncrossedIntegers()];
		for (int j = 0, i = 2; i < crossedOut.length; i++)
		if (notCrossed(i))
		result[j++] = i;
	}
	private static int numberOfUncrossedIntegers()
	{
		int count = 0;
		for (int i = 2; i < crossedOut.length; i++)
		if (notCrossed(i))
		count++;
		return count;
	}
}
```

<div dir="rtl">

فهمیدنش راحت است که کامنت اول بیخودی انجا نوشته شده، چرا که خود اسم generatePrimes را توضیح داده. این اسم به اندازه کافی کاربرد تابع را بیان میکند. من فکر می‌کنم کامنت‌ها برای راحت تر کردن کار خواننده نوشته میشوند، پس ترجیح می‌دهم این کامنت اضافی را آنجا قرار ندهم.
بحث دوم قطعا ضروری است. این منطق پشت استفاده از ریشه دوم به عنوان حد حلقه را توضیح میدهد.البته استفاده از ریشه دوم عدد ممکن است فقط از نظر تئوری جالب به نظر برسد، آیا واقعا با محاسبه ریشه دوم و محدود کردن حلقه به آن، زمان بیشتری ذخیره می‌کنیم؟
ارزش فکر کردن را دارد. استفاده از ریشه دوم برای محدود کردن تکرار حلقه، هکر قدیمی c و اسمبلی نویس درونم را راضی میکند، ولی فکر نمی‌کنم ارزش وقت و تلاشی که بقیه برای فهمیدن آن صرف می‌کنند را داشته باشد.

</div>

* [فصل بعد](../5_Formatting(completed)/5_Formatting.md)

* [فصل قبل](../3_Functions(completed)/3_Functions.md)
