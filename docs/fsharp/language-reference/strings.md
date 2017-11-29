---
title: "字符串 (F#)"
description: "了解如何 F # 'string' 类型表示不可变的文本为 Unicode 字符序列。"
keywords: "visual f#, f#, 函数编程"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: df7624e5-ca6c-4e77-9e2b-87ca7e5e6f52
ms.openlocfilehash: 96a398ebcd53681481b10d1a2bee5f1e5442a5cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2017
---
# <a name="strings"></a><span data-ttu-id="2ceb0-104">字符串</span><span class="sxs-lookup"><span data-stu-id="2ceb0-104">Strings</span></span>

> [!NOTE]
<span data-ttu-id="2ceb0-105">本文中的 API 参考链接将转至 MSDN。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-105">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="2ceb0-106">Docs.microsoft.com API 参考尚未完成。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="2ceb0-107">`string`类型不可变的文本表示为 Unicode 字符序列。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-107">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="2ceb0-108">`string` 是 .NET Framework 中 `System.String` 的别名。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-108">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ceb0-109">备注</span><span class="sxs-lookup"><span data-stu-id="2ceb0-109">Remarks</span></span>
<span data-ttu-id="2ceb0-110">由引号 （"） 字符分隔字符串。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-110">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="2ceb0-111">反斜杠字符 (\)使用某些特殊字符进行编码。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-111">The backslash character (\) is used to encode certain special characters.</span></span> <span data-ttu-id="2ceb0-112">反斜杠和组合在一起的下一个字符被称为*转义序列*。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-112">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="2ceb0-113">转义序列在 F # 字符串文本显示在下表中受支持。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-113">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="2ceb0-114">字符</span><span class="sxs-lookup"><span data-stu-id="2ceb0-114">Character</span></span>|<span data-ttu-id="2ceb0-115">转义序列</span><span class="sxs-lookup"><span data-stu-id="2ceb0-115">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="2ceb0-116">Backspace</span><span class="sxs-lookup"><span data-stu-id="2ceb0-116">Backspace</span></span>|<span data-ttu-id="2ceb0-117">\b</span><span class="sxs-lookup"><span data-stu-id="2ceb0-117">\b</span></span>|
|<span data-ttu-id="2ceb0-118">换行符</span><span class="sxs-lookup"><span data-stu-id="2ceb0-118">Newline</span></span>|\n|
|<span data-ttu-id="2ceb0-119">回车</span><span class="sxs-lookup"><span data-stu-id="2ceb0-119">Carriage return</span></span>|<span data-ttu-id="2ceb0-120">\r</span><span class="sxs-lookup"><span data-stu-id="2ceb0-120">\r</span></span>|
|<span data-ttu-id="2ceb0-121">Tab</span><span class="sxs-lookup"><span data-stu-id="2ceb0-121">Tab</span></span>|<span data-ttu-id="2ceb0-122">\t</span><span class="sxs-lookup"><span data-stu-id="2ceb0-122">\t</span></span>|
|<span data-ttu-id="2ceb0-123">反斜杠</span><span class="sxs-lookup"><span data-stu-id="2ceb0-123">Backslash</span></span>|\\|
|<span data-ttu-id="2ceb0-124">引号</span><span class="sxs-lookup"><span data-stu-id="2ceb0-124">Quotation mark</span></span>|\"|
|<span data-ttu-id="2ceb0-125">单引号</span><span class="sxs-lookup"><span data-stu-id="2ceb0-125">Apostrophe</span></span>|\'|
|<span data-ttu-id="2ceb0-126">Unicode 字符</span><span class="sxs-lookup"><span data-stu-id="2ceb0-126">Unicode character</span></span>|<span data-ttu-id="2ceb0-127">\u*XXXX*或 \U*XXXXXXXX* (其中*X*指示一个十六进制数字)</span><span class="sxs-lookup"><span data-stu-id="2ceb0-127">\u*XXXX* or \U*XXXXXXXX* (where *X* indicates a hexadecimal digit)</span></span>|

<span data-ttu-id="2ceb0-128">如果以 @ 符号，则该文本是原义字符串。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-128">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="2ceb0-129">这意味着，任何转义序列将被忽略，只不过两个引号字符解释为一个引号字符。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-129">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="2ceb0-130">此外，可能由三个引号括字符串。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-130">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="2ceb0-131">在这种情况下，将忽略所有转义序列，包括双引号字符。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-131">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="2ceb0-132">若要指定包含嵌入的带引号的字符串的字符串，你可以使用原义字符串或三引号的字符串。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-132">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="2ceb0-133">如果你使用原义字符串，则必须指定两个引号字符来表示单引号字符。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-133">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="2ceb0-134">如果使用三引号字符串，你可以使用单引号字符，如果没有它们解析为字符串的末尾。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-134">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="2ceb0-135">当您使用 XML 或包含嵌入的引号其他结构时，此技术很有用。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-135">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="2ceb0-136">在代码中，接受字符串的分行符和换行符处换行是按原义解释为换行符，除非反斜杠字符是换行之前的最后一个字符。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-136">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="2ceb0-137">使用反斜杠字符时，将忽略在下一行的前导空格。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-137">Leading whitespace on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="2ceb0-138">下面的代码产生的字符串`str1`值`"abc\n     def"`和字符串`str2`值`"abcdef"`。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-138">The following code produces a string `str1` that has value `"abc\n     def"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="2ceb0-139">你可以通过类似数组的语法，如下所示访问字符串中的单个字符。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-139">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="2ceb0-140">输出为 `b`。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-140">The output is `b`.</span></span>

<span data-ttu-id="2ceb0-141">或者，可以使用数组的切片语法，通过提取子字符串，如下面的代码中所示。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-141">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="2ceb0-142">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-142">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="2ceb0-143">您可以通过无符号字节，类型的数组表示 ASCII 字符串`byte[]`。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-143">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="2ceb0-144">添加后缀`B`到字符串文本以指示它是 ASCII 字符串。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-144">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="2ceb0-145">使用的字节数组的 ASCII 字符串文字支持为 Unicode 字符串，除 Unicode 转义序列相同的转义序列。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-145">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]
    
## <a name="string-operators"></a><span data-ttu-id="2ceb0-146">字符串运算符</span><span class="sxs-lookup"><span data-stu-id="2ceb0-146">String Operators</span></span>
<span data-ttu-id="2ceb0-147">有两种方法将字符串串联： 通过使用`+`运算符或通过使用`^`运算符。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-147">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="2ceb0-148">`+`运算符维护与.NET Framework 字符串处理功能的兼容性。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-148">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="2ceb0-149">下面的示例阐释了字符串串联。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-149">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]
    
## <a name="string-class"></a><span data-ttu-id="2ceb0-150">字符串类</span><span class="sxs-lookup"><span data-stu-id="2ceb0-150">String Class</span></span>
<span data-ttu-id="2ceb0-151">因为在 F # 中的字符串类型是一个.NET 框架，实际`System.String`键入所有`System.String`成员均可。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-151">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="2ceb0-152">这包括`+`运算符，用于将字符串串联`Length`属性，与`Chars`属性，作为 Unicode 字符数组中返回的字符串。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-152">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="2ceb0-153">有关字符串的详细信息，请参阅`System.String`。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-153">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="2ceb0-154">通过使用`Chars`属性`System.String`，你可以通过指定索引，如下面的代码中所示访问字符串中的每个字符。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-154">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]
    
## <a name="string-module"></a><span data-ttu-id="2ceb0-155">字符串模块</span><span class="sxs-lookup"><span data-stu-id="2ceb0-155">String Module</span></span>
<span data-ttu-id="2ceb0-156">用于字符串处理的其他功能包含在`String`中的模块`FSharp.Core`命名空间。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-156">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="2ceb0-157">有关详细信息，请参阅[Core.String 模块](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="2ceb0-157">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="2ceb0-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ceb0-158">See Also</span></span>
[<span data-ttu-id="2ceb0-159">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="2ceb0-159">F# Language Reference</span></span>](index.md)