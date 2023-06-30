# StyleGuide

# C#命名约定

常见的命名规则：

**Pascal** 规则： 每个单词开头的字母大写(如 TestCounter PhysicalAddress DataService)。

**Camel** 规则： 除了第一个单词外的其他单词的开头字母大写. 如. testCounter physicalAddress dataService。

**Upper** 规则： 仅用于一两个字符长的常量的缩写命名,超过三个字符长度应该应用Pascal规则。

例如：
```c#
public class Math
{
    private string testCounter; //Camel
    public double PI {get;set;} //Upper
    public double FeigenBaumNumber {get;set;}   //Pascal 
}
```

基本命名规范：

一定要为各种类型，函数，变量，特性和数据结构选取有意义的命名。其命名应该能直接反映其作用。所谓自注释的代码就是好代码。

名称应该说明“什么”而不是“如何”。通过避免使用公开基础实现（它们会发生改变）的名称，可以保留简化复杂性的抽象层。例如，可以使用 GetNextStudent()，而不是 GetNextArrayElement()。

不应该在标识符名中使用不常见的或有歧义的缩短或缩略形式的词。比如，使用 “GetTemperature” 而不是 “GetTemp”，Temp到底是Temperature的缩写还是Temporary的缩写呢。对于公共类型或大家都知道的缩写，则可以使用缩略词，如：线程过程，窗口过程，和对话框过程函数，为“ThreadProc”, “DialogProc”, “WndProc” 等使用公共后缀。

一定不要使用下划线，连字号，或其他任何非字母数字的字符。

不要使用计算机领域中未被普遍接受的缩写。

在适当的时候，使用众所周知的缩写替换冗长的词组名称。例如，用 UI 作为 User Interface 缩 写，用 OLAP 作为 On-line Analytical Processing 的缩写。

在使用缩写时，对于超过两个字符长度的缩写请使用 Pascal 命名法或驼峰命名法。例如使用 HtmlButton 或 HTMLButton；但是，应当大写仅有两个字符的缩写，如：System.IO，而不是 System.Io。

不要在标识符或参数名称中使用缩写。如果必须使用缩写，对于由多于两个字符所组成的缩写请使用驼峰命名法。

选择正确名称时的困难可能表明需要进一步分析或定义项的目的。

使名称足够长以便有一定的意义，并且足够短以避免冗长。


## 1. 类命名规则

- 类名应该为名词及名词短语，尽可能使用完整的词。
- 使用Pascal规则。
- 不要使用类前缀 - 不要使用下划线字符 (_)。
- 有时候需要提供以字母 I 开始的类名称，虽然该类不是接口。只要 I 是作为类名称组成部分的整个单词的第一个字母，这便是适当的。例如，类名称 IdentityStore 就是适当的。
- 在适当的地方，使用复合单词命名派生的类。派生类名称的第二个部分应当是基类的名称。例如，ApplicationException 对于从名为 Exception 的类派生的类是适当的名称，原因是 ApplicationException 是一种 Exception。请在应用该规则时进行合理的判断。例如，Button 对于从 Control 派生的类是适当的名称。尽管按钮是一种控件，但是将 Control 作为类名称的一部分将使名称不必要地加长。

## 2. 接口命名规则

- 接口名称应该为名词及名词短语或者描述其行为的形容词，尽可能使用完整的词。(Example IComponent or IEnumberable)
- 使用Pascal规则。
- 使用字符I为前缀，并紧跟一个大写字母（即接口名的第一个字母大写）。

例如:
```c#
interface ICompare
{
    int Compare();
}
```

## 3. 枚举命名规则

- 对于 Enum 类型和值名称使用 Pascal 大小写。
- 少用缩写。
- 尽量避免在 Enum 类型名称上使用 Enum 后缀。
- 对大多数 Enum 类型使用单数名称，但是对作为位域的 Enum 类型使用复数名称。
- 总是将 FlagsAttribute 添加到位域 Enum 类型。

## 4. 变量命名

- 仅在简单的循环语句中计数器变量使用 i, j, k, l, m, n。
- 使用 Camel 命名规则。
- 不需要给成员变量加任何前缀（如、m、s_、t_等等）。如果想要区分局部变量和成员变量，可以使用this关键字。
- 在变量名中使用互补对，如 min/max、begin/end 和 open/close。
- 命名 private 或 internal 字段时，可以以 _ 作为前缀。（因为在支持语句完成的IDE中编辑 C# 代码时，键入 _ 将显示所有对象范围的成员。）但也可以不使用 _ 作为前缀，因为在某些IDE中本就可以快速筛选所有字段、属性、方法。

## 5. 方法命名

- 使用Pascal规则。
- 对方法名采用一致的动词/宾语或宾语/动词顺序。例如，将动词置于前面时，所使用的名称诸如 InsertWidget 和 InsertSprocket；将宾语置于前面时，所使用的名称诸如 WidgetInsert 和 SprocketInsert。
- 推荐名称应该为动词或动词短语.例如Save，SaveCustomer，而不要使用CustomerSave。
- 不要在方法中重复类的名称。例如，如果某个类已命名为 Book，则不要将某个方法称为 Book.CloseBook，而可以将方法命名为 Book.Close。

## 6. 属性命名

- 名称应该为名词及名词短语。
- 使用Pascal规则。
- 对于bool型属性或者变量使用Is（is）作为前缀，不要使用Flag后缀，例如应该使用IsDeleted,而不要使用DeleteFlag。若单词的意义本身已经包含是非的情况，可省略Is，如Exist。
- 在类属性的名称中包含类名是多余的，如 User.UserName。而是应该使用 User.Name。
- 一些常用属性命名规约：
    1. 获取单个对象的方法用 Get 做前缀。
    2. 获取多个对象的方法用List做后缀，如：GetOrdersList。
    3. 获取统计值的方法用 Count 做后缀。
    4. 添加或更新的方法用 Save或Add。
    5. 删除的方法用 Remove/Delete。
    6. 修改的方法用 Update。

## 7. 集合命名
- 名称应该为名词及名词短语。
- 使用Pascal规则。
- 名称后面追加“Collection”。

## 8. 事件命名
- event handlers命名使用 EventHandler 后缀.。
- 两个参数分别使用 sender 及 e。
- 使用Pascal规则。
- 事件参数使用EventArgs 后缀。
- 事件命名使用语法时态反映其激发的状态，例如 Changed，Changing。
- 考虑使用动词命名。

## 9. 自定义的属性和异常以Attribute和Exception结尾

例如:
```c#
public class AuthorAttribute : Attribute
{
}

public class AppException : Exception
{
}
```

## 10. 避免使用公共字段

- 不要在类中使用公共字段，使用自动属性代替公共字段。
- 因为属性可以快速查找使用方，所以某些情况下，也可以使用私有属性替代字段。

# 布局约定

- 在类的顶部声明所有的成员变量，静态变量声明在最前面
- 每行只写一条语句、声明。
- 在方法定义与属性定义之间添加至少一个空白行。
- 类、字段、属性、方法等需要添加private protect public internal修饰符。
- 将 using 指令放在命名空间声明之外。

例如:
```c#
using Azure;

namespace Test
{
    public class Account
    {
        private string name;
        public static string BankName;
        public static decimal Reserves;
    
        public string Number {get; set;}
        public DateTime DateOpened {get; set;}
        public DateTime DateClosed {get; set;}
        public decimal Balance {get; set;}
    
        // Constructor
        public Account()
        {
            // ...
        }
    }
}
```

# 语言准则

## 1. 字符串数据类型、

- 使用字符串内插来连接短字符串，如下面的代码所示。

```c#
string displayName = $"{nameList[n].LastName}, {nameList[n].FirstName}";
```
- 若要在循环中追加字符串，尤其是在使用大量文本时，请使用 StringBuilder 对象。
```c#
var phrase = "lalalalalalalalalalalalalalalalalalalalalalalalalalalalalala";
var manyPhrases = new StringBuilder();
for (var i = 0; i < 10000; i++)
{
    manyPhrases.Append(phrase);
}
//Console.WriteLine("tra" + manyPhrases);
```

## 2. 隐式类型本地变量

- 当变量类型明显来自赋值的右侧时，或者当精度类型不重要时，请对本地变量进行隐式类型化。
```c#
var var1 = "This is clearly a string.";
var var2 = 27;
```

- 当类型并非明显来自赋值的右侧时，请勿使用 var。 请勿假设类型明显来自方法名称。 如果变量类型为 new 运算符或显式强制转换，则将其视为明显来自方法名称。
```c#
int var3 = Convert.ToInt32(Console.ReadLine());
int var4 = ExampleClass.ResultSoFar();
```

- 请勿依靠变量名称来指定变量的类型。 它可能不正确。 在以下示例中，变量名称 inputInt 会产生误导性。 它是字符串。
```c#
var inputInt = Console.ReadLine();
Console.WriteLine(inputInt);
```

- 避免使用 var 来代替 dynamic。 如果想要进行运行时类型推理，请使用 dynamic。

- 使用隐式类型化来确定 for 循环中循环变量的类型。下面的示例在 for 语句中使用隐式类型化。
```c#
var phrase = "lalalalalalalalalalalalalalalalalalalalalalalalalalalalalala";
var manyPhrases = new StringBuilder();
for (var i = 0; i < 10000; i++)
{
    manyPhrases.Append(phrase);
}
//Console.WriteLine("tra" + manyPhrases);
```

- 不要使用隐式类型化来确定 foreach 循环中循环变量的类型。 在大多数情况下，集合中的元素类型并不明显。 不应仅依靠集合的名称来推断其元素的类型。
下面的示例在 foreach 语句中使用显式类型化。
```c#
foreach (char ch in laugh)
{
    if (ch == 'h')
        Console.Write("H");
    else
        Console.Write(ch);
}
Console.WriteLine();
```

## 3. 事件处理

如果你正在定义一个稍后不需要删除的事件处理程序，请使用 lambda 表达式。

```c#
public Form2()
{
    this.Click += (s, e) =>
        {
            MessageBox.Show(
                ((MouseEventArgs)e).Location.ToString());
        };
}
```

Lambda 表达式缩短了以下传统定义。

```c#
public Form1()
{
    this.Click += new EventHandler(Form1_Click);
}

void Form1_Click(object? sender, EventArgs e)
{
    MessageBox.Show(((MouseEventArgs)e).Location.ToString());
}
```

## 4. && 和 || 运算符

若要通过跳过不必要的比较来避免异常并提高性能，请在执行比较时使用 &&（而不是 &）和 ||（而不是 |），如下面的示例所示。

```c#
Console.Write("Enter a dividend: ");
int dividend = Convert.ToInt32(Console.ReadLine());

Console.Write("Enter a divisor: ");
int divisor = Convert.ToInt32(Console.ReadLine());

if ((divisor != 0) && (dividend / divisor > 0))
{
    Console.WriteLine("Quotient: {0}", dividend / divisor);
}
else
{
    Console.WriteLine("Attempted division by 0 ends up here.");
}
```
如果除数为 0，则 if 语句中的第二个子句将导致运行时错误。 但是，当第一个表达式为 false 时，&& 运算符将发生短路。 也就是说，它并不评估第二个表达式。 如果 divisor 为 0，则 & 运算符将同时计算这两个表达式，这会导致运行时错误。

## 5. 委托

使用 Func<> 和 Action<>，而不是定义委托类型。 在类中，定义委托方法。

```c#
public static Action<string> ActionExample1 = x => Console.WriteLine($"x is: {x}");

public static Action<string, string> ActionExample2 = (x, y) =>
    Console.WriteLine($"x is: {x}, y is {y}");

public static Func<string, int> FuncExample1 = x => Convert.ToInt32(x);

public static Func<int, int, int> FuncExample2 = (x, y) => x + y;
```

## 5. try-catch 和 using 语句

- 对大多数异常处理使用 try-catch 语句。
```c#
static string GetValueFromArray(string[] array, int index)
{
    try
    {
        return array[index];
    }
    catch (System.IndexOutOfRangeException ex)
    {
        Console.WriteLine("Index is out of range: {0}", index);
        throw;
    }
}
```

- 通过使用 C# using 语句简化你的代码。 如果具有 try-finally 语句（该语句中 finally 块的唯一代码是对 Dispose 方法的调用），请使用 using 语句代替。在以下示例中，try-finally 语句仅在 finally 块中调用 Dispose。
```c#
Font font1 = new Font("Arial", 10.0f);
try
{
    byte charset = font1.GdiCharSet;
}
finally
{
    if (font1 != null)
    {
        ((IDisposable)font1).Dispose();
    }
}
```
可以使用 using 语句执行相同的操作。
```c#
using (Font font2 = new Font("Arial", 10.0f))
{
    byte charset2 = font2.GdiCharSet;
}
```
使用不需要大括号的新 using 语法：
```c#
using Font font3 = new Font("Arial", 10.0f);
byte charset3 = font3.GdiCharSet;
```
