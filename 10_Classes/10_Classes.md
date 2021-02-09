<div align="center">
    <img src="img-10.1.png">
</div>

<div dir="rtl">

# فصل دهم – کلاس ها
تا به اینجای کتاب تمرکز ما روی چگونگی نوشتن خط ها بلوک های کد بوده است. ما یافتیم که چگونه ترکیب صحیحی از فانکشن ها را بنویسیم و آن ها را به هم پیوند دهیم. اما با وجود تمام توجه ها به رسا بودن کد ها و فانکشن هایی که تشکیل میدهند، ما همچنان نمی توانیم کد تمیز داشته باشیم تا زمانی که توجه ما به مرتب سازی کد های رده بالاتر هم باشد. بیاید راجب تمیز کردن کلاس ها صحبت کنیم.

## ساختار کلاس ها
برای تبعیت از قرارداد استاندارد جاوا  ، یک کلاس باید با لیستی از متغیر ها آغاز شود.
اگر ثابت های public static وجود داشته باشد باید اول بیاید . بعد از آن متغیر های  
public می آیند . به ندرت پیش میاید که تعریف کردن یک متغیر private کار درستی باشد.

### کپسوله ساز (Encapsulation)
ما دوست داریم متغیر ها و فانکشن های سودمند مون رو private کنیم ، ولی روی این موضوع تعصبی نداریم. گاهی اوقات ما احتیاج داریم که یک متغیر یا یک فانکشن پر کاربرد را   protected کنیم تا از طریق تست بتوانیم به آن دسترسی یابیم . برای ما تست کردن حرف آخر را میزند . اگر تستی در همان پکیج بخواهد که فانکشنی را صدا بزند یا به متغیر های آن دسترسی یابد ، ما آن را protected یا package scope میکنیم .

## کلاس ها باید کوچک باشند !
اولین قاعده کلاس ها این است که باید کوچک باشند. دومین قاعده کلاس ها این است که باید کوچکتر از آن باشند. خیر ما قرار نیست دقیقا همان متن فصل فانکشن ها را دوباره تکرار کنیم . ولی مانند فانکشن ها کوچکتر بودن قانون اصلی طراحی یک کلاس است . مانند فانکشن ها سوالی که بلافاصله می پرسیم این است "چقدر کوچک ؟" 
برای فانکشن ها ما اندازه ی آن را بر اساس خط های نوشته شده سنجیدیم. برای کلاس ها ما از مقیاس دیگری استفاده میکنیم. مسئولیت ها  را میشماریم.
لیست 10-1 نمای کلی یک کلاس است ، SuperDashboard ، که 70 متد public دارد. بیشتر دولوپر ها موافقند که این کلاس کمی بیش از اندازه بزرگ است (از نظر سایز) . برخی دیگر از SuperDashboard با عنوان " کلاس خدا " یاد میکنند.
<div dir="ltr">

**Listing 10-1**
**Too Many Responsibilities**

```java
public class SuperDashboard extends JFrame implements MetaDataUser
    public String getCustomizerLanguagePath()
    public void setSystemConfigPath(String systemConfigPath)
    public String getSystemConfigDocument()
    public void setSystemConfigDocument(String systemConfigDocument)
    public boolean getGuruState()
    public boolean getNoviceState()
    public boolean getOpenSourceState()
    public void showObject(MetaObject object)
    public void showProgress(String s)
    public boolean isMetadataDirty()
    public void setIsMetadataDirty(boolean isMetadataDirty)
    public Component getLastFocusedComponent()
    public void setLastFocused(Component lastFocused)
    public void setMouseSelectState(boolean isMouseSelected)
    public boolean isMouseSelected()
    public LanguageManager getLanguageManager()
    public Project getProject()
    public Project getFirstProject()
    public Project getLastProject()
    public String getNewProjectName()
    public void setComponentSizes(Dimension dim)
    public String getCurrentDir()
    public void setCurrentDir(String newDir)
    public void updateStatus(int dotPos, int markPos)
    public Class[] getDataBaseClasses()
    public MetadataFeeder getMetadataFeeder()
    public void addProject(Project project)
    public boolean setCurrentProject(Project project)
    public boolean removeProject(Project project)
    public MetaProjectHeader getProgramMetadata()
    public void resetDashboard()
    public Project loadProject(String fileName, String projectName)
    public void setCanSaveMetadata(boolean canSave)
    public MetaObject getSelectedObject()
    public void deselectObjects()
    public void setProject(Project project)
    public void editorAction(String actionName, ActionEvent event)
    public void setMode(int mode)
    public FileManager getFileManager()
    public void setFileManager(FileManager fileManager)
    public ConfigManager getConfigManager()
    public void setConfigManager(ConfigManager configManager)
    public ClassLoader getClassLoader()
    public void setClassLoader(ClassLoader classLoader)
    public Properties getProps()
    public String getUserHome()
    public String getBaseDir()
    public int getMajorVersionNumber()
    public int getMinorVersionNumber()
    public int getBuildNumber()
    public MetaObject pasting(MetaObject target, MetaObject pasted, MetaProject project)
    public void processMenuItems(MetaObject metaObject)
    public void processMenuSeparators(MetaObject metaObject)
    public void processTabPages(MetaObject metaObject)
    public void processPlacement(MetaObject object)
    public void processCreateLayout(MetaObject object)
    public void updateDisplayLayer(MetaObject object, int layerIndex)
    public void propertyEditedRepaint(MetaObject object)
    public void processDeleteObject(MetaObject object)
    public boolean getAttachedToDesigner()
    public void processProjectChangedState(boolean hasProjectChanged)
    public void processObjectNameChanged(MetaObject object)
    public void runProject()
    public void setAçowDragging(boolean allowDragging)
    public boolean allowDragging()
    public boolean isCustomizing()
    public void setTitle(String title)
    public IdeMenuBar getIdeMenuBar()
    public void showHelper(MetaObject metaObject, String propertyName)
    // ... many non-public methods follow ...
}
```
</div>

اما چه اتفاقی می افتاد اگر SuperDashboard فقط متد های لیست 10-2 را دارا بود ؟
<div dir="ltr">

**Listing 10-2**
**Small Enough?**

```java
public class SuperDashboard extends JFrame implements MetaDataUser
    public Component getLastFocusedComponent()
    public void setLastFocused(Component lastFocused)
    public int getMajorVersionNumber()
    public int getMinorVersionNumber()
    public int getBuildNumber()
}
```
</div>

پنج متد زیاد نیست مگه نه ؟ در این حالت زیاد هم هست چون علا رغم متد های کم آن ، SuperDashboard مسئولیت های زیادی بر عهده دارد.
نام کلاس باید توضیح دهد که کلاس چه مسئولیت هایی بر عهده دارد. در واقع نامگذاری اولین راهی است که میتوان با آن اندازه کلاس را تخمین زد. اگر ما نتوانیم اسمی مختصر برای یک کلاس در نظر بگیریم ، پس احتمالا خیلی بزرگ است. هرچه نام کلاس مبهم تر باشد احتمالا مسئولیت های بیشتری بر عهده دارد. برای مثال ، نام کلاس هایی دارای معانی گنگ مانند Processor یا Manager یا Super هستند معمولا نشان از توده ای از مسئولیت ها دارند.
همچنین ما باید بتوانیم توضیح مختصری از کلاس در 25 کلمه بدهیم ، البته بدون استفاده از کلمات " اگر "، " و "، " یا " ، "اما" .  چگونه SuperDashboard  را توضیح دهیم ؟
 >" کلاس SuperDashboard امکان دسترسی به کامپوننت هایی که در گذشته روی آن تمرکز کردیم را میدهد و همچنین به ما اجازه میدهد تا ورژن و شماره ساخت برنامه ها را پیگیری کنیم."  .

"و" ی اول نشان از آن دارد که SuperDashboard مسئولیت های زیادی دارد.

### اصل تک مسئولیتی
اصل تک مسئولیتی (SRP)  بدین معناست که هر کلاس یک دلیل و فقط یک دلیل برای تغییر دادن داشته باشد. این اصل به ما هم معنی مسئولیت را می گوید و هم راهنمایی هایی برای اندازه کلاس ها به ما میکند. کلاس ها باید یک مسئولیت و یک دلیل برای تغییر داده شدن داشته باشند.
کلاس به ظاهر کوچک SuperDashboard در لیست 10-2 دو دلیل برای تغییر دارد. اولین دلیل اینکه ، هر دفعه که اطلاعات به برنامه فرستاده میشود باید اطلاعات مربوط به ورژن (نسخه) بروز شود.. دومین دلیل اینکه ، این کلاس کامپوننت های Java Swing را مدیریت میکند (مشتقی از JFrame است ، Swing نمایانگر پنجره های گرافیکی سطح بالا است). شکی نیست که وقتی ما هر کدام از کد های  Swing را عوض میکنیم میخواهیم که شماره نسخه برنامه نیز عوض شود ، ولی خلاف آن الزاما درست نیست: شاید ما بخواهیم اطلاعات ورژن را بر اساس تغییرات در دیگر کد های سیستم تغییر دهیم.
تلاش برای شناختن مسئولیت ها(دلایلی برای تغییر) اکثر اوقات به ما کمک میکند که مفهوم کد را بهتر بشناسیم و آن را بیان کنیم. ما به سادگی می توانیم هر سه متد SuperDashboard که با اطلاعات مربوط به ورژن سروکار دارند را به یک کلاس جدا به نام Version تبدیل کنیم. (لیست 10-3 را نگاه کنید !) کلاس ورژن Version توانایی آن را دارد که در برنامه های دیگر نیز استفاده شود!
<div dir="ltr">

**Listing 10-3**
**A single-responsibility class**

```java
public class Version {
    public int getMajorVersionNumber()
    public int getMinorVersionNumber()
    public int getBuildNumber()
}
```
</div>

SRP is one of the more important concept in OO design. It’s also one of the simpler
concepts to understand and adhere to. Yet oddly, SRP is often the most abused class design
principle. We regularly encounter classes that do far too many things. Why?
Getting software to work and making software clean are two very different activities.
Most of us have limited room in our heads, so we focus on getting our code to work more
than organization and cleanliness. This is wholly appropriate. Maintaining a separation of
concerns is just as important in our programming activities as it is in our programs.
The problem is that too many of us think that we are done once the program works.
We fail to switch to the other concern of organization and cleanliness. We move on to the
next problem rather than going back and breaking the overstuffed classes into decoupled
units with single responsibilities.
At the same time, many developers fear that a large number of small, single-purpose
classes makes it more difficult to understand the bigger picture. They are concerned that
they must navigate from class to class in order to figure out how a larger piece of work gets
accomplished.
However, a system with many small classes has no more moving parts than a system
with a few large classes. There is just as much to learn in the system with a few large
classes. So the question is: Do you want your tools organized into toolboxes with many
small drawers each containing well-defined and well-labeled components? Or do you want
a few drawers that you just toss everything into?
Every sizable system will contain a large amount of logic and complexity. The primary goal in managing such complexity is to organize it so that a developer knows where
to look to find things and need only understand the directly affected complexity at any
given time. In contrast, a system with larger, multipurpose classes always hampers us by
insisting we wade through lots of things we don’t need to know right now.
To restate the former points for emphasis: We want our systems to be composed of
many small classes, not a few large ones. Each small class encapsulates a single responsibility, has a single reason to change, and collaborates with a few others to achieve the
desired system behaviors.

### پیوستگی
Classes should have a small number of instance variables. Each of the methods of a class
should manipulate one or more of those variables. In general the more variables a method
manipulates the more cohesive that method is to its class. A class in which each variable is
used by each method is maximally cohesive.
In general it is neither advisable nor possible to create such maximally cohesive
classes; on the other hand, we would like cohesion to be high. When cohesion is high, it
means that the methods and variables of the class are co-dependent and hang together as a
logical whole.
Consider the implementation of a Stack in Listing 10-4. This is a very cohesive class.
Of the three methods only size() fails to use both the variables. 

<div dir="ltr">

**Listing 10-4**
**Stack.java A cohesive class.**

</div>

```java
public class Stack {
    private int topOfStack = 0;
    List<Integer> elements = new LinkedList<Integer>();
    public int size() {
        return topOfStack;
    }
    public void push(int element) {
        topOfStack++;
        elements.add(element);
    }
    public int pop() throws PoppedWhenEmpty {
        if (topOfStack == 0)
            throw new PoppedWhenEmpty();
        int element = elements.get(--topOfStack);
        elements.remove(topOfStack);
        return element;
    }
}
```
The strategy of keeping functions small and keeping parameter lists short can sometimes lead to a proliferation of instance variables that are used by a subset of methods.
When this happens, it almost always means that there is at least one other class trying to get out of the larger class. You should try to separate the variables and methods into two or
more classes such that the new classes are more cohesive.

### حفظ انسجام نتایج در چند کلاس کوچک

Just the act of breaking large functions into smaller functions causes a proliferation of
classes. Consider a large function with many variables declared within it. Let’s say you
want to extract one small part of that function into a separate function. However, the code
you want to extract uses four of the variables declared in the function. Must you pass all
four of those variables into the new function as arguments?
Not at all! If we promoted those four variables to instance variables of the class, then
we could extract the code without passing any variables at all. It would be easy to break
the function up into small pieces.
Unfortunately, this also means that our classes lose cohesion because they accumulate
more and more instance variables that exist solely to allow a few functions to share them.
But wait! If there are a few functions that want to share certain variables, doesn’t that
make them a class in their own right? Of course it does. When classes lose cohesion, split
them!
So breaking a large function into many smaller functions often gives us the opportunity to split several smaller classes out as well. This gives our program a much better organization and a more transparent structure.
As a demonstration of what I mean, let’s use a time-honored example taken from
Knuth’s wonderful book Literate Programming.3 Listing 10-5 shows a translation into Java
of Knuth’s PrintPrimes program. To be fair to Knuth, this is not the program as he wrote it
but rather as it was output by his WEB tool. I’m using it because it makes a great starting
place for breaking up a big function into many smaller functions and classes.

<div dir="ltr">

**Listing 10-5**
**PrintPrimes.java**

```java
package literatePrimes;
public class PrintPrimes {
    public static void main(String[] args) {
        final int M = 1000;
        final int RR = 50;
        final int CC = 4;
        final int WW = 10;
        final int ORDMAX = 30;
        int P[] = new int[M + 1];
        int PAGENUMBER;
        int PAGEOFFSET;
        int ROWOFFSET;
        int C;
        int J;
        int K;
        boolean JPRIME;
        int ORD;
        int SQUARE;
        int N;
        int MULT[] = new int[ORDMAX + 1];
        J = 1;
        K = 1;
        P[1] = 2;
        ORD = 2;
        SQUARE = 9;
        while (K < M) {
            do {
                J = J + 2;
                if (J == SQUARE) {
                    ORD = ORD + 1;
                    SQUARE = P[ORD] * P[ORD];
                    MULT[ORD - 1] = J;
                }
                N = 2;
                JPRIME = true;
                while (N < ORD && JPRIME) {
                    while (MULT[N] < J){
                        MULT[N] = MULT[N] + P[N] + P[N];
                    }
                    if (MULT[N] == J)
                        JPRIME = false;
                    N = N + 1;
                }
            } while (!JPRIME);
            K = K + 1;
            P[K] = J;
        }
        {
            PAGENUMBER = 1;
            PAGEOFFSET = 1;
            while (PAGEOFFSET <= M) {
                System.out.println("The First " + M + " Prime Numbers ---Page " + PAGENUMBER);
                System.out.println("");
                for (ROWOFFSET = PAGEOFFSET; ROWOFFSET < PAGEOFFSET + RR; ROWOFFSET++){
                    for (C = 0; C < CC;C++)
                        if (ROWOFFSET + C * RR <= M)
                            System.out.format("%10d", P[ROWOFFSET + C * RR]);
                    System.out.println("");
                }
                System.out.println("\f");
                PAGENUMBER = PAGENUMBER + 1;
                PAGEOFFSET = PAGEOFFSET + RR * CC;
            }
        }
    }
}
```
</div>


This program, written as a single function, is a mess. It has a deeply indented structure, a plethora of odd variables, and a tightly coupled structure. At the very least, the one
big function should be split up into a few smaller functions.
Listing 10-6 through Listing 10-8 show the result of splitting the code in Listing 10-5
into smaller classes and functions, and choosing meaningful names for those classes, functions, and variables. 

<div dir="ltr">

**Listing 10-6**
**PrimePrinter.java (refactored)**

```java
package literatePrimes;

public class PrimePrinter {
    public static void main(String[] args) {
        final int NUMBER_OF_PRIMES = 1000;
        int[] primes = PrimeGenerator.generate(NUMBER_OF_PRIMES);
        final int ROWS_PER_PAGE = 50;
        final int COLUMNS_PER_PAGE = 4;
        RowColumnPagePrinter tablePrinter =
        new RowColumnPagePrinter(ROWS_PER_PAGE,COLUMNS_PER_PAGE, "The First" + NUMBER_OF_PRIMES + " Prime Numbers");
        tablePrinter.print(primes);
    }
}
```
</div>

<div dir="ltr">

**Listing 10-7**
**RowColumnPagePrinter.java**

```java
package literatePrimes;
import java.io.PrintStream;
public class RowColumnPagePrinter {
    private int rowsPerPage;
    private int columnsPerPage;
    private int numbersPerPage;
    private String pageHeader;
    private PrintStream printStream;
    public RowColumnPagePrinter(int rowsPerPage,
    int columnsPerPage,
    String pageHeader) {
        this.rowsPerPage = rowsPerPage;
        this.columnsPerPage = columnsPerPage;
        this.pageHeader = pageHeader;
        numbersPerPage = rowsPerPage * columnsPerPage;
        printStream = System.out;
    }
    public void print(int data[]) {
        int pageNumber = 1;
        for (int firstIndexOnPage = 0;
            firstIndexOnPage < data.length;
            firstIndexOnPage += numbersPerPage) {
                int lastIndexOnPage =
                Math.min(firstIndexOnPage + numbersPerPage - 1,
                data.length - 1);
            printPageHeader(pageHeader, pageNumber);
            printPage(firstIndexOnPage, lastIndexOnPage, data);
            printStream.println("\f");
            pageNumber++;
        }
    }
    private void printPage(int firstIndexOnPage,
        int lastIndexOnPage,
        int[] data) {
        int firstIndexOfLastRowOnPage =
        firstIndexOnPage + rowsPerPage - 1;
        for (int firstIndexInRow = firstIndexOnPage;
            firstIndexInRow <= firstIndexOfLastRowOnPage;
            firstIndexInRow++) {
            printRow(firstIndexInRow, lastIndexOnPage, data);
            printStream.println("");
        }
    }
    private void printRow(int firstIndexInRow,
        int lastIndexOnPage,
        int[] data) {
        for (int column = 0; column < columnsPerPage; column++) {
            int index = firstIndexInRow + column * rowsPerPage;
            if (index <= lastIndexOnPage){
                printStream.format("%10d", data[index]);
            }
        }
    }
    private void printPageHeader(String pageHeader, int pageNumber) {
        printStream.println(pageHeader + " --- Page " + pageNumber);
        printStream.println("");
    }
    public void setOutput(PrintStream printStream) {
        this.printStream = printStream;
    }
}
```
</div>


<div dir="ltr">

**Listing 10-8**
**PrimeGenerator.java**

```java
package literatePrimes;
import java.util.ArrayList;
public class PrimeGenerator {
    private static int[] primes;
    private static ArrayList<Integer> multiplesOfPrimeFactors;
    protected static int[] generate(int n) {
        primes = new int[n];
        multiplesOfPrimeFactors = new ArrayList<Integer>();
        set2AsFirstPrime();
        checkOddNumbersForSubsequentPrimes();
        return primes;
    }
    private static void set2AsFirstPrime() {
        primes[0] = 2;
        multiplesOfPrimeFactors.add(2);
    }
    private static void checkOddNumbersForSubsequentPrimes() {
        int primeIndex = 1;
        for (int candidate = 3; primeIndex < primes.length; candidate += 2) {
            if (isPrime(candidate)){
                primes[primeIndex++] = candidate;
            }
        }
    }
    private static boolean isPrime(int candidate) {
        if (isLeastRelevantMultipleOfNextLargerPrimeFactor(candidate)) {
            multiplesOfPrimeFactors.add(candidate);
            return false;
        }
        return isNotMultipleOfAnyPreviousPrimeFactor(candidate);
    }
    private static boolean isLeastRelevantMultipleOfNextLargerPrimeFactor(int candidate) {
        int nextLargerPrimeFactor = primes[multiplesOfPrimeFactors.size()];
        int leastRelevantMultiple = nextLargerPrimeFactor * nextLargerPrimeFactor;
        return candidate == leastRelevantMultiple;
    }
    private static boolean isNotMultipleOfAnyPreviousPrimeFactor(int candidate) {
        for (int n = 1; n < multiplesOfPrimeFactors.size(); n++) {
            if (isMultipleOfNthPrimeFactor(candidate, n))
                return false;
        }
        return true;
    }
    private static boolean isMultipleOfNthPrimeFactor(int candidate, int n) {
        return candidate == smallestOddNthMultipleNotLessThanCandidate(candidate, n);
    }
    private static int smallestOddNthMultipleNotLessThanCandidate(int candidate, int n) {
        int multiple = multiplesOfPrimeFactors.get(n);
        while (multiple < candidate)
            multiple += 2 * primes[n];
        multiplesOfPrimeFactors.set(n, multiple);
        return multiple;
    }
}
```
</div>

The first thing you might notice is that the program got a lot longer. It went from a
little over one page to nearly three pages in length. There are several reasons for this
growth. First, the refactored program uses longer, more descriptive variable names.
Second, the refactored program uses function and class declarations as a way to add
commentary to the code. Third, we used whitespace and formatting techniques to keep
the program readable.
Notice how the program has been split into three main responsibilities. The main
program is contained in the PrimePrinter class all by itself. Its responsibility is to handle
the execution environment. It will change if the method of invocation changes. For
example, if this program were converted to a SOAP service, this is the class that would
be affected.
The RowColumnPagePrinter knows all about how to format a list of numbers into
pages with a certain number of rows and columns. If the formatting of the output needed
changing, then this is the class that would be affected.
The PrimeGenerator class knows how to generate a list prime numbers. Notice that it
is not meant to be instantiated as an object. The class is just a useful scope in which
its variables can be declared and kept hidden. This class will change if the algorithm for
computing prime numbers changes.
This was not a rewrite! We did not start over from scratch and write the program over
again. Indeed, if you look closely at the two different programs, you’ll see that they use the
same algorithm and mechanics to get their work done.
The change was made by writing a test suite that verified the precise behavior of the
first program. Then a myriad of tiny little changes were made, one at a time. After each
change the program was executed to ensure that the behavior had not changed. One tiny
step after another, the first program was cleaned up and transformed into the second.

## اماده سازی برای تغییر
For most systems, change is continual. Every change subjects us to the risk that the
remainder of the system no longer works as intended. In a clean system we organize our
classes so as to reduce the risk of change.
The Sql class in Listing 10-9 is used to generate properly formed SQL strings given
appropriate metadata. It’s a work in progress and, as such, doesn’t yet support SQL functionality like update statements. When the time comes for the Sql class to support an
update statement, we’ll have to “open up” this class to make modifications. The problem
with opening a class is that it introduces risk. Any modifications to the class have the
potential of breaking other code in the class. It must be fully retested.

<div dir="ltr">

**Listing 10-9**
**A class that must be opened for change**

```java
public class Sql {
    public Sql(String table, Column[] columns)
    public String create()
    public String insert(Object[] fields)
    public String selectAll()
    public String findByKey(String keyColumn, String keyValue)
    public String select(Column column, String pattern)
    public String select(Criteria criteria)
    public String preparedInsert()
    private String columnList(Column[] columns)
    private String valuesList(Object[] fields, final Column[] columns)
    private String selectWithCriteria(String criteria)
    private String placeholderList(Column[] columns)
}
```
</div>

The Sql class must change when we add a new type of statement. It also must change
when we alter the details of a single statement type—for example, if we need to modify
the select functionality to support subselects. These two reasons to change mean that the
Sql class violates the SRP.
We can spot this SRP violation from a simple organizational standpoint. The method
outline of Sql shows that there are private methods, such as selectWithCriteria, that
appear to relate only to select statements.
Private method behavior that applies only to a small subset of a class can be a useful
heuristic for spotting potential areas for improvement. However, the primary spur for taking action should be system change itself. If the Sql class is deemed logically complete,
then we need not worry about separating the responsibilities. If we won’t need update
functionality for the foreseeable future, then we should leave Sql alone. But as soon as we
find ourselves opening up a class, we should consider fixing our design.
What if we considered a solution like that in Listing 10-10? Each public interface
method defined in the previous Sql from Listing 10-9 is refactored out to its own derivative
of the Sql class. Note that the private methods, such as valuesList, move directly where they are needed. The common private behavior is isolated to a pair of utility classes, Where
and ColumnList.

<div dir="ltr">

**Listing 10-10**
**A set of closed classes**

```java
abstract public class Sql {
    public Sql(String table, Column[] columns)
    abstract public String generate();
}
public class CreateSql extends Sql {
    public CreateSql(String table, Column[] columns)
    @Override public String generate()
}
public class SelectSql extends Sql {
    public SelectSql(String table, Column[] columns)
    @Override public String generate()
}
public class InsertSql extends Sql {
    public InsertSql(String table, Column[] columns, Object[] fields)
    @Override public String generate()
    private String valuesList(Object[] fields, final Column[] columns)
}
public class SelectWithCriteriaSql extends Sql {
    public SelectWithCriteriaSql(String table, Column[] columns, Criteria criteria)
    @Override public String generate()
}
public class SelectWithMatchSql extends Sql {
    public SelectWithMatchSql(String table, Column[] columns, Column column, String pattern)
    @Override public String generate()
}
public class FindByKeySql extends Sql
    public FindByKeySql(String table, Column[] columns, String keyColumn, String keyValue)
    @Override public String generate()
}
public class PreparedInsertSql extends Sql {
    public PreparedInsertSql(String table, Column[] columns)
    @Override public String generate() {
    private String placeholderList(Column[] columns)
}
public class Where {
    public Where(String criteria)
    public String generate()
}
public class ColumnList {
    public ColumnList(Column[] columns)
    public String generate()
}
```
</div>

The code in each class becomes excruciatingly simple. Our required comprehension
time to understand any class decreases to almost nothing. The risk that one function could
break another becomes vanishingly small. From a test standpoint, it becomes an easier
task to prove all bits of logic in this solution, as the classes are all isolated from one
another.
Equally important, when it’s time to add the update statements, none of the existing
classes need change! We code the logic to build update statements in a new subclass of Sql
named UpdateSql. No other code in the system will break because of this change.
Our restructured Sql logic represents the best of all worlds. It supports the SRP. It also
supports another key OO class design principle known as the Open-Closed Principle, or
OCP:4 Classes should be open for extension but closed for modification. Our restructured
Sql class is open to allow new functionality via subclassing, but we can make this change
while keeping every other class closed. We simply drop our UpdateSql class in place.
We want to structure our systems so that we muck with as little as possible when we
update them with new or changed features. In an ideal system, we incorporate new features by extending the system, not by making modifications to existing code. 

### جلوگیری از تغییر
Needs will change, therefore code will change. We learned in OO 101 that there are concrete classes, which contain implementation details (code), and abstract classes, which
represent concepts only. A client class depending upon concrete details is at risk when
those details change. We can introduce interfaces and abstract classes to help isolate the
impact of those details.
Dependencies upon concrete details create challenges for testing our system. If we’re
building a Portfolio class and it depends upon an external TokyoStockExchange API to
derive the portfolio’s value, our test cases are impacted by the volatility of such a lookup.
It’s hard to write a test when we get a different answer every five minutes!
Instead of designing Portfolio so that it directly depends upon TokyoStockExchange,
we create an interface, StockExchange, that declares a single method:
<div dir="ltr">

```java
public interface StockExchange {
    Money currentPrice(String symbol);
}
```
</div>
We design TokyoStockExchange to implement this interface. We also make sure that the
constructor of Portfolio takes a StockExchange reference as an argument:
<div dir="ltr">

```java
public Portfolio {
    private StockExchange exchange;
    public Portfolio(StockExchange exchange) {
        this.exchange = exchange;
    }
 // ...
}
```
</div>

Now our test can create a testable implementation of the StockExchange interface that
emulates the TokyoStockExchange. This test implementation will fix the current value for
any symbol we use in testing. If our test demonstrates purchasing five shares of Microsoft
for our portfolio, we code the test implementation to always return $100 per share of
Microsoft. Our test implementation of the StockExchange interface reduces to a simple
table lookup. We can then write a test that expects $500 for our overall portfolio value.

<div dir="ltr">

```java
public class PortfolioTest {
    private FixedStockExchangeStub exchange;
    private Portfolio portfolio;
    @Before
    protected void setUp() throws Exception {
        exchange = new FixedStockExchangeStub();
        exchange.fix("MSFT", 100);
        portfolio = new Portfolio(exchange);
    }
    @Test
    public void GivenFiveMSFTTotalShouldBe500() throws Exception {
        portfolio.add(5, "MSFT");
        Assert.assertEquals(500, portfolio.value());
    }
}
```
</div>

If a system is decoupled enough to be tested in this way, it will also be more flexible
and promote more reuse. The lack of coupling means that the elements of our system are
better isolated from each other and from change. This isolation makes it easier to understand each element of the system.
By minimizing coupling in this way, our classes adhere to another class design principle known as the Dependency Inversion Principle (DIP).5
 In essence, the DIP says that our
classes should depend upon abstractions, not on concrete details.
Instead of being dependent upon the implementation details of the TokyoStockExchange class, our Portfolio class is now dependent upon the StockExchange interface.
The StockExchange interface represents the abstract concept of asking for the current price
of a symbol. This abstraction isolates all of the specific details of obtaining such a price,
including from where that price is obtained.


</div>

* [فصل قبل](../9_Unit_Tests/9_Unit_Tests.md)
