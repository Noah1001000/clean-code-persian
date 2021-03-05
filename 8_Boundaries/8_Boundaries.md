![](img-8.1.png) 

ما به ندرت تمام نرم افزارهای موجود در سیستم های خود را کنترل می کنیم. بعضی اوقات ما بسته های نرم افزاری را می خریم یا از کد های اپن سورس استفاده می کنیم. در مواقع دیگر بسته به تیم هایی که در شرکت داریم از آنها میخواهیم تا کامپوننت یا زیر سیستم را برایمان تولید کنند . به نوعی ما باید این کد خارجی را با کد اختصاصی خود ادغام کنیم. در این فصل ما به تمرین ها و تکنیک های برای تمیز نگه داشتن محدوده نرم افزار خود نگاه می اندازیم .

# استفاده از کد های دیگران
همیشه یک تنش طبیعی بین ارائه دهنده رابط ( interface ) واستفاده کننده ی آن وجود دارد. ارائه دهندگان بسته ها و فریمورک ها سعی دارند کاربردپذیری را افزیش دهند تا کد های آنها در محیط های مختلفی استفاده شده و مخاطبان بیشتری را جذب کنند. از طرف دیگر ، استفاده کنندگان می خواهند رابطی مختص نیازهای خاص خود داشته باشند. این تنش می تواند در محدوده سیستم های ما مشکل ایجاد کند. به عنوان مثال به java.util.Map نگاه کنید . همانطور که با بررسی شکل 8-1 مشاهده می کنید ، Maps دارای یک رابط بسیار گسترده با قابلیت های فراوان است . مطمئناً این قدرت و انعطاف پذیری مفید است ، اما یک دقدقه ایجاد میکند . به عنوان مثال ،ممکن است ما در برنامه یک Map ایجاد کنیم و آن را به مکان های مختلف ارجاع دهیم . هدف ما ممکن است این باشد که هیچ یک از ارجاع دهندگان Map ما چیزی را در آن حذف نکنند. اما دقیقاً در بالای لیست ، متد ()clear وجود دارد. هر کاربری که از Map استفاده میکند قدرت پاک کردن آن را دارد. یا شاید طراحی ما این است که فقط انواع خاصی از اشیا را می توان در نقشه ذخیره کرد ، اما Maps برای نوع خاصی قابل اطمینانی محدود نشده است. همه می تواند هر نوعی را به هر Map ی اضافه کند.


• clear() void – Map
• containsKey(Object key) boolean – Map
• containsValue(Object value) boolean – Map
• entrySet() Set – Map
• equals(Object o) boolean – Map
• get(Object key) Object – Map
• getClass() Class<? extends Object> – Object
• hashCode() int – Map
• isEmpty() boolean – Map
• keySet() Set – Map
• notify() void – Object
• notifyAll() void – Object
• put(Object key, Object value) Object – Map
• putAll(Map t) void – Map
• remove(Object key) Object – Map
• size() int – Map
• toString() String – Object
• values() Collection – Map
• wait() void – Object
• wait(long timeout) void – Object
• wait(long timeout, int nanos) void – Object

اگر برنامه ما به سنسور از نوع Map احتیاج داشته باشد اینطوری ساخته می شود :


```java
Map sensors = new HashMap();
```

سپس ، هنگامی که قسمت دیگری از کد نیاز به دسترسی به سنسور دارد ، این کد را مشاهده می کنید: 

```java
Sensor s = (Sensor)sensors.get(sensorId );
```

نه فقط یک بار ، که بارها آ را در سراسر کد مشاهده می کنیم. سرویس گیرنده این کد مسئولیت دریافت Object از Map و تبدیل آن به نوع صحیح برعهده دارد. این کد کار می کند ، اما کد تمیز نیست. همچنین ، این کد داستان خود را به بهترین شکل ممکن بیان نمی کند. همانطور که در زیر نشان داده شده است ، خوانایی این کد با استفاده از تعریف نوع جنریک بسیار قابل بهبود است:

```java
Map<Sensor> sensors = new HashMap<Sensor>();
...
Sensor s = sensors.get(sensorId );
```

However, this doesn’t solve the problem that Map<Sensor> provides more capability than we
need or want.
Passing an instance of Map<Sensor> liberally around the system means that there will
be a lot of places to fix if the interface to Map ever changes. You might think such a change
to be unlikely, but remember that it changed when generics support was added in Java 5.
Indeed, we’ve seen systems that are inhibited from using generics because of the sheer
magnitude of changes needed to make up for the liberal use of Maps.
A cleaner way to use Map might look like the following. No user of Sensors would care
one bit if generics were used or not. That choice has become (and always should be) an
implementation detail.

```java
public class Sensors {
    private Map sensors = new HashMap();
    public Sensor getById(String id) {
        return (Sensor) sensors.get(id);
    }
    //snip
}
```

The interface at the boundary ( Map) is hidden. It is able to evolve with very little impact on
the rest of the application. The use of generics is no longer a big issue because the casting
and type management is handled inside the Sensors class.
This interface is also tailored and constrained to meet the needs of the application. It
results in code that is easier to understand and harder to misuse. The Sensors class can
enforce design and business rules.
We are not suggesting that every use of Map be encapsulated in this form. Rather, we
are advising you not to pass Map s (or any other interface at a boundary) around your
system. If you use a boundary interface like Map, keep it inside the class, or close family
of classes, where it is used. Avoid returning it from, or accepting it as an argument to,
public APIs.

# Exploring and Learning Boundaries
Third-party code helps us get more functionality delivered in less time. Where do we start
when we want to utilize some third-party package? It’s not our job to test the third-party
code, but it may be in our best interest to write tests for the third-party code we use.
Suppose it is not clear how to use our third-party library. We might spend a day or two
(or more) reading the documentation and deciding how we are going to use it. Then we
might write our code to use the third-party code and see whether it does what we think. We
would not be surprised to find ourselves bogged down in long debugging sessions trying to
figure out whether the bugs we are experiencing are in our code or theirs.
Learning the third-party code is hard. Integrating the third-party code is hard too.
Doing both at the same time is doubly hard. What if we took a different approach? Instead
of experimenting and trying out the new stuff in our production code, we could write some
tests to explore our understanding of the third-party code. Jim Newkirk calls such tests
learning tests.1
In learning tests we call the third-party API, as we expect to use it in our application.
We’re essentially doing controlled experiments that check our understanding of that API.
The tests focus on what we want out of the API.

# Learning log4j
Let’s say we want to use the apache log4j package rather than our own custom-built log-
ger. We download it and open the introductory documentation page. Without too much
reading we write our first test case, expecting it to write “hello” to the console.


```java
@Test
public void testLogCreate() {
    Logger logger = Logger.getLogger("MyLogger");
    logger.info("hello");
}
```

When we run it, the logger produces an error that tells us we need something called an
Appender. After a little more reading we find that there is a ConsoleAppender. So we create a
ConsoleAppender and see whether we have unlocked the secrets of logging to the console.

```java
@Test
public void testLogAddAppender() {
    Logger logger = Logger.getLogger("MyLogger");
    ConsoleAppender appender = new ConsoleAppender();
    logger.addAppender(appender);
    logger.info("hello");
}
```

This time we find that the Appender has no output stream. Odd—it seems logical that it’d
have one. After a little help from Google, we try the following:

```java
@Test
public void testLogAddAppender() {
    Logger logger = Logger.getLogger("MyLogger");
    logger.removeAllAppenders();
    logger.addAppender(new ConsoleAppender(
    new PatternLayout("%p %t %m%n"),
    ConsoleAppender.SYSTEM_OUT));
    logger.info("hello");
}
```

That worked; a log message that includes “hello” came out on the console! It seems odd
that we have to tell the ConsoleAppender that it writes to the console.
Interestingly enough, when we remove the ConsoleAppender.SystemOut argument, we
see that “hello” is still printed. But when we take out the PatternLayout, it once again com-
plains about the lack of an output stream. This is very strange behavior.
Looking a little more carefully at the documentation, we see that the default
ConsoleAppender constructor is “unconfigured,” which does not seem too obvious or useful.
This feels like a bug, or at least an inconsistency, in log4j.
A bit more googling, reading, and testing, and we eventually wind up with Listing 8-1.
We’ve discovered a great deal about the way that log4j works, and we’ve encoded that
knowledge into a set of simple unit tests.


Listing 8-1
LogTest.java

```java
public class LogTest {
    private Logger logger;
    @Before
    public void initialize() {
        logger = Logger.getLogger("logger");
        logger.removeAllAppenders();
        Logger.getRootLogger().removeAllAppenders();
    }
    @Test
    public void basicLogger() {
        BasicConfigurator.configure();
        logger.info("basicLogger");
    }
    @Test
    public void addAppenderWithStream() {
        logger.addAppender(new ConsoleAppender(
        new PatternLayout("%p %t %m%n"),
        ConsoleAppender.SYSTEM_OUT));
        logger.info("addAppenderWithStream");
    }
    @Test
    public void addAppenderWithoutStream() {
        logger.addAppender(new ConsoleAppender(
        new PatternLayout("%p %t %m%n")));
        logger.info("addAppenderWithoutStream");
    }
}
```

Now we know how to get a simple console logger initialized, and we can encapsulate
that knowledge into our own logger class so that the rest of our application is isolated from
the log4j boundary interface.

# Learning Tests Are Better Than Free
The learning tests end up costing nothing. We had to learn the API anyway, and writing
those tests was an easy and isolated way to get that knowledge. The learning tests were
precise experiments that helped increase our understanding.
Not only are learning tests free, they have a positive return on investment. When there
are new releases of the third-party package, we run the learning tests to see whether there
are behavioral differences.
Learning tests verify that the third-party packages we are using work the way we
expect them to. Once integrated, there are no guarantees that the third-party code will stay
compatible with our needs. The original authors will have pressures to change their code to
meet new needs of their own. They will fix bugs and add new capabilities. With each
release comes new risk. If the third-party package changes in some way incompatible with
our tests, we will find out right away.
Whether you need the learning provided by the learning tests or not, a clean boundary
should be supported by a set of outbound tests that exercise the interface the same way the
production code does. Without these boundary tests to ease the migration, we might be
tempted to stay with the old version longer than we should.

# Using Code That Does Not Yet Exist
There is another kind of boundary, one that separates the known from the unknown. There
are often places in the code where our knowledge seems to drop off the edge. Sometimes
what is on the other side of the boundary is unknowable (at least right now). Sometimes
we choose to look no farther than the boundary.
A number of years back I was part of a team developing software for a radio com-
munications system. There was a subsystem, the “Transmitter,” that we knew little
about, and the people responsible for the subsystem had not gotten to the point of defining
their interface. We did not want to be blocked, so we started our work far away from the
unknown part of the code.
We had a pretty good idea of where our world ended and the new world began. As we
worked, we sometimes bumped up against this boundary. Though mists and clouds of
ignorance obscured our view beyond the boundary, our work made us aware of what we
wanted the boundary interface to be. We wanted to tell the transmitter something like this:
Key the transmitter on the provided frequency and emit an analog representation of the
data coming from this stream.
We had no idea how that would be done because the API had not been designed yet.
So we decided to work out the details later.
To keep from being blocked, we defined our own interface. We called it something
catchy, like Transmitter. We gave it a method called transmit that took a frequency and a
data stream. This was the interface we wished we had.
One good thing about writing the interface we wish we had is that it’s under our
control. This helps keep client code more readable and focused on what it is trying to
accomplish.
In Figure 8-2, you can see that we insulated the CommunicationsController classes
from the transmitter API (which was out of our control and undefined). By using our own
application specific interface, we kept our CommunicationsController code clean and
expressive. Once the transmitter API was defined, we wrote the TransmitterAdapter to
bridge the gap. The ADAPTER2 encapsulated the interaction with the API and provides a
single place to change when the API evolves.

![](img-8.2.png) 

This design also gives us a very convenient seam3 in the code for testing. Using a
suitable FakeTransmitter, we can test the CommunicationsController classes. We can also
create boundary tests once we have the TransmitterAPI that make sure we are using the
API correctly.
Clean Boundaries
Interesting things happen at boundaries. Change is one of those things. Good software
designs accommodate change without huge investments and rework. When we use code
that is out of our control, special care must be taken to protect our investment and make
sure future change is not too costly.
Code at the boundaries needs clear separation and tests that define expectations. We
should avoid letting too much of our code know about the third-party particulars. It’s better
to depend on something you control than on something you don’t control, lest it end up
controlling you.
We manage third-party boundaries by having very few places in the code that refer to
them. We may wrap them as we did with Map, or we may use an ADAPTER to convert from
our perfect interface to the provided interface. Either way our code speaks to us better,
promotes internally consistent usage across the boundary, and has fewer maintenance
points when the third-party code changes.











 
 
