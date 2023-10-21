---
description: How do you use this library?
---

# 🖥 How to use

## How do you write Figlet text?

Figletize is easy to use. Just call the `Console.WriteLine()` function with `FigletTools.RenderFiglet()`, passing the text and the figlet font name (lowercase):

```csharp
string figletText = FigletTools.RenderFiglet("Hello!", "banner");
Console.WriteLine(figletText);
```

Additionally, you can get the Figlet font instance using one of the following `FigletizeFonts` functions, passing the font name (lowercase) to the first argument:

* `GetByName()`
* `TryGetByName()`

After you get the instance, you can call the `Render()` function on it, passing the text as the first argument.

```csharp
var fontInstance = FigletizeFonts.TryGetByName(fontName);
if (fontInstance is null)
{
    Console.Error.WriteLine($"Font {fontName} not found. Exiting...");
    return;
}
string rendered = fontInstance.Render(message);
Console.WriteLine(rendered);
```

### Other ways

Additionally, you can use the `FigletTools` class to get a list of supported Figlet fonts and their instances using the `GetFigletFonts()` function.

`GetFigletFont()` also does the same as `GetByName()`, except that it uses the fallback font, `small`, when the font is not found.

You can also use the source generator on your partial class, like the following:

```csharp
namespace Test.Namespace
{
    [GenerateFigletizeText("Member", "stacey", "Figletize")]
    internal partial class DemoUsage
    {
    }
}
```

Once your code is compiled, you can use the property that you've named in the first argument to get the resulting Figlet text.
