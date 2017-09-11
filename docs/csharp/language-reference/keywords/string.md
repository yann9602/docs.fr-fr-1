---
title: "string (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- string
- string_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 56847aad4cb8b0427594a299df2306d21675506b
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="string-c-reference"></a><span data-ttu-id="5e1ac-102">string (référence C#)</span><span class="sxs-lookup"><span data-stu-id="5e1ac-102">string (C# Reference)</span></span>
<span data-ttu-id="5e1ac-103">Le type `string` représente une séquence de zéro, un ou plusieurs caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-103">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="5e1ac-104">`string` est un alias pour <xref:System.String> dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-104">`string` is an alias for <xref:System.String> in the .NET Framework.</span></span>  
  
 <span data-ttu-id="5e1ac-105">Bien que `string` soit un type référence, les opérateurs d’égalité (`==` et `!=`) sont définis pour comparer les valeurs d’objets `string`, pas les références.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-105">Although `string` is a reference type, the equality operators (`==` and `!=`) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="5e1ac-106">Cela permet de tester l’égalité de chaînes de façon plus intuitive.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-106">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="5e1ac-107">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5e1ac-107">For example:</span></span>  
  
```csharp  
string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 <span data-ttu-id="5e1ac-108">Cette opération affiche « True », puis « False », car le contenu des chaînes est équivalent, mais `a` et `b` ne font pas référence à la même instance de chaîne.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-108">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>  
  
 <span data-ttu-id="5e1ac-109">L’opérateur + concatène les chaînes :</span><span class="sxs-lookup"><span data-stu-id="5e1ac-109">The + operator concatenates strings:</span></span>  
  
```csharp  
string a = "good " + "morning";  
```  
  
 <span data-ttu-id="5e1ac-110">Cela crée un objet String qui contient « good morning ».</span><span class="sxs-lookup"><span data-stu-id="5e1ac-110">This creates a string object that contains "good morning".</span></span>  
  
 <span data-ttu-id="5e1ac-111">Les chaînes sont *immuables* : il est impossible de changer le contenu d’un objet String après avoir créé l’objet, bien que la syntaxe semble indiquer le contraire.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-111">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="5e1ac-112">Par exemple, lorsque vous écrivez ce code, le compilateur crée en fait un nouvel objet String pour stocker la nouvelle séquence de caractères, et ce nouvel objet est assigné à b.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-112">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to b.</span></span> <span data-ttu-id="5e1ac-113">La chaîne « h » est alors disponible pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-113">The string "h" is then eligible for garbage collection.</span></span>  
  
```csharp
string b = "h";  
b += "ello";  
```  
  
 <span data-ttu-id="5e1ac-114">L’opérateur [] peut être utilisé pour un accès en lecture seule aux différents caractères d’un objet `string` :</span><span class="sxs-lookup"><span data-stu-id="5e1ac-114">The [] operator can be used for readonly access to individual characters of a `string`:</span></span>  
  
```csharp  
string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 <span data-ttu-id="5e1ac-115">Les littéraux de chaîne sont de type `string` et peuvent être écrits sous deux formes, entre guillemets et @-quoted.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-115">String literals are of type `string` and can be written in two forms, quoted and @-quoted.</span></span> <span data-ttu-id="5e1ac-116">Les littéraux de chaîne entre guillemets sont placés entre guillemets doubles (") :</span><span class="sxs-lookup"><span data-stu-id="5e1ac-116">Quoted string literals are enclosed in double quotation marks ("):</span></span>  
  
```csharp  
"good morning"  // a string literal  
```  
  
 <span data-ttu-id="5e1ac-117">Les littéraux de chaîne peuvent contenir tout littéral de caractère.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-117">String literals can contain any character literal.</span></span> <span data-ttu-id="5e1ac-118">Les séquences d’échappement sont incluses.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-118">Escape sequences are included.</span></span> <span data-ttu-id="5e1ac-119">L’exemple suivant utilise la séquence d’échappement `\\` pour la barre oblique inverse, `\u0066` pour la lettre f et `\n` pour un saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-119">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>  
  
```  
string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  <span data-ttu-id="5e1ac-120">Le code d’échappement `\udddd` (où `dddd` est un nombre à quatre chiffres) représente le caractère Unicode U+`dddd`.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-120">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="5e1ac-121">Les codes d’échappement Unicode à huit chiffres sont également reconnus : `\Udddddddd`.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-121">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>  
  
 <span data-ttu-id="5e1ac-122">Les littéraux de chaîne textuelle commencent par @ et sont placés entre guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-122">Verbatim string literals start with @ and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="5e1ac-123">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5e1ac-123">For example:</span></span>  
  
```csharp  
@"good morning"  // a string literal  
```  
  
 <span data-ttu-id="5e1ac-124">L’avantage des chaînes textuelles est que les séquences d’échappement *ne sont pas* traitées, ce qui facilite l’écriture, par exemple, d’un nom de fichier complet :</span><span class="sxs-lookup"><span data-stu-id="5e1ac-124">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified file name:</span></span>  
  
```csharp  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 <span data-ttu-id="5e1ac-125">Pour inclure un guillemet double dans une chaîne @-quoted, doublez-le :</span><span class="sxs-lookup"><span data-stu-id="5e1ac-125">To include a double quotation mark in an @-quoted string, double it:</span></span>  
  
```csharp  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 <span data-ttu-id="5e1ac-126">Une autre manière d’utiliser le symbole @ consiste à utiliser des identificateurs ([/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)) référencés qui sont des mots clés C#.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-126">Another use of the @ symbol is to use referenced ([/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)) identifiers that are C# keywords.</span></span>  
  
 <span data-ttu-id="5e1ac-127">Pour plus d’informations sur les chaînes en C#, consultez la rubrique [Chaînes](../../../csharp/programming-guide/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="5e1ac-127">For more information about strings in C#, see [Strings](../../../csharp/programming-guide/strings/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e1ac-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="5e1ac-128">Example</span></span>  
 <span data-ttu-id="5e1ac-129">[!code-cs[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="5e1ac-129">[!code-cs[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="5e1ac-130">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="5e1ac-130">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5e1ac-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e1ac-131">See Also</span></span>  
 <span data-ttu-id="5e1ac-132">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="5e1ac-132">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="5e1ac-133">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5e1ac-133">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="5e1ac-134">[Bonnes pratiques pour l’utilisation de chaînes](../../../standard/base-types/best-practices-strings.md) </span><span class="sxs-lookup"><span data-stu-id="5e1ac-134">[Best Practices for Using Strings](../../../standard/base-types/best-practices-strings.md) </span></span>  
 <span data-ttu-id="5e1ac-135">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="5e1ac-135">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="5e1ac-136">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5e1ac-136">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="5e1ac-137">[Types référence](../../../csharp/language-reference/keywords/reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="5e1ac-137">[Reference Types](../../../csharp/language-reference/keywords/reference-types.md) </span></span>  
 <span data-ttu-id="5e1ac-138">[Types valeur](../../../csharp/language-reference/keywords/value-types.md) </span><span class="sxs-lookup"><span data-stu-id="5e1ac-138">[Value Types](../../../csharp/language-reference/keywords/value-types.md) </span></span>  
 <span data-ttu-id="5e1ac-139">[Opérations de chaînes de base](../../../standard/base-types/basic-string-operations.md) </span><span class="sxs-lookup"><span data-stu-id="5e1ac-139">[Basic String Operations](../../../standard/base-types/basic-string-operations.md) </span></span>  
 <span data-ttu-id="5e1ac-140">[Création de chaînes](../../../standard/base-types/creating-new.md) </span><span class="sxs-lookup"><span data-stu-id="5e1ac-140">[Creating New Strings](../../../standard/base-types/creating-new.md) </span></span>  
 [<span data-ttu-id="5e1ac-141">Tableau des formats des résultats numériques</span><span class="sxs-lookup"><span data-stu-id="5e1ac-141">Formatting Numeric Results Table</span></span>](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)

