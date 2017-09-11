---
title: "Chaînes interpolées (C#)"
ms.date: 2017-02-03
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: 9
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
ms.sourcegitcommit: 03d1e3f0897713e25be7d7f893861a3eb4dac211
ms.openlocfilehash: ee35da0a008a19ad643fffff64d74485237d716f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/11/2017

---
# <a name="interpolated-strings-c-reference"></a><span data-ttu-id="f79a0-102">Chaînes interpolées (informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="f79a0-102">Interpolated Strings (C# Reference)</span></span>

<span data-ttu-id="f79a0-103">Permettent de construire des chaînes.</span><span class="sxs-lookup"><span data-stu-id="f79a0-103">Used to construct strings.</span></span>  <span data-ttu-id="f79a0-104">Une chaîne interpolée ressemble à une chaîne de modèle contenant des *expressions interpolées*.</span><span class="sxs-lookup"><span data-stu-id="f79a0-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="f79a0-105">Une chaîne interpolée retourne une chaîne qui remplace les expressions interpolées qu’elle contient par leur représentation sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="f79a0-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span>  

<span data-ttu-id="f79a0-106">Les arguments d’une chaîne interpolée sont plus faciles à comprendre qu’une [chaîne de format composite](../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="f79a0-106">The arguments of an interpolated string are easier to understand than a [composite format string](../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="f79a0-107">Par exemple, la chaîne interpolée</span><span class="sxs-lookup"><span data-stu-id="f79a0-107">For example, the interpolated string</span></span>  
  
```csharp  
Console.WriteLine($"Name = {name}, hours = {hours:hh}"); 
```  
<span data-ttu-id="f79a0-108">contient deux expressions interpolées, ’{name}’ et ’{hours:hh}’.</span><span class="sxs-lookup"><span data-stu-id="f79a0-108">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="f79a0-109">La chaîne de format composite équivalente est la suivante :</span><span class="sxs-lookup"><span data-stu-id="f79a0-109">The equivalent composite format string is:</span></span>

```csharp
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours);  
```  

<span data-ttu-id="f79a0-110">La structure d’une chaîne interpolée est :</span><span class="sxs-lookup"><span data-stu-id="f79a0-110">The structure of an interpolated string is:</span></span>  
  
```  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

<span data-ttu-id="f79a0-111">où :</span><span class="sxs-lookup"><span data-stu-id="f79a0-111">where:</span></span> 

- <span data-ttu-id="f79a0-112">*field-width* est un entier signé qui indique le nombre de caractères du champ.</span><span class="sxs-lookup"><span data-stu-id="f79a0-112">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="f79a0-113">S’il est positif, le champ est aligné à droite ; s’il est négatif, il est aligné à gauche.</span><span class="sxs-lookup"><span data-stu-id="f79a0-113">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span> 

- <span data-ttu-id="f79a0-114">*format-string* est une chaîne de format qui convient au type d’objet mis en forme.</span><span class="sxs-lookup"><span data-stu-id="f79a0-114">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="f79a0-115">Par exemple, pour une valeur @System.DateTime, cela peut signifier une chaîne de format de date et heure standard, comme "D" ou "d".</span><span class="sxs-lookup"><span data-stu-id="f79a0-115">For example, for a @System.DateTime value, it could be a standard date and time format string such as "D" or "d".</span></span>

 <span data-ttu-id="f79a0-116">Vous pouvez utiliser une chaîne interpolée partout où vous pouvez utiliser un littéral de chaîne.</span><span class="sxs-lookup"><span data-stu-id="f79a0-116">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="f79a0-117">La chaîne interpolée est évaluée à chaque exécution du code contenant la chaîne interpolée.</span><span class="sxs-lookup"><span data-stu-id="f79a0-117">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="f79a0-118">Cela vous permet de séparer la définition et l’évaluation d’une chaîne interpolée.</span><span class="sxs-lookup"><span data-stu-id="f79a0-118">This allows you to separate the definition and evaluation of an interpolated string.</span></span>  
  
 <span data-ttu-id="f79a0-119">Pour ajouter une accolade ("{" ou "}") dans une chaîne interpolée, utilisez deux accolades "{{" ou "}}".</span><span class="sxs-lookup"><span data-stu-id="f79a0-119">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="f79a0-120">Pour plus d’informations, consultez la section « Conversions implicites ».</span><span class="sxs-lookup"><span data-stu-id="f79a0-120">See the Implicit Conversions section for more details.</span></span>  

<span data-ttu-id="f79a0-121">Si la chaîne interpolée contient d’autres caractères ayant une signification particulière dans une chaîne interpolée, comme le guillemet ("), les deux-points (:) ou la virgule (,), ils doivent être échappés s’ils se trouvent dans du texte littéral, ou être inclus dans une expression délimitée par des parenthèses s’ils s’agit d’éléments de langage inclus dans une expression interpolée.</span><span class="sxs-lookup"><span data-stu-id="f79a0-121">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="f79a0-122">L’exemple suivant échappe des guillemets pour les inclure dans la chaîne de résultat, et utilise des parenthèses pour délimiter l’expression `(age == 1 ? "" : "s")` pour que le signe deux-points ne soit pas interprété comme commençant une chaîne de format.</span><span class="sxs-lookup"><span data-stu-id="f79a0-122">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

<span data-ttu-id="f79a0-123">[!code-cs[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="f79a0-123">[!code-cs[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]</span></span>  

## <a name="implicit-conversions"></a><span data-ttu-id="f79a0-124">Conversions implicites</span><span class="sxs-lookup"><span data-stu-id="f79a0-124">Implicit Conversions</span></span>  

<span data-ttu-id="f79a0-125">Trois conversions de type implicite sont possibles à partir d’une chaîne interpolée :</span><span class="sxs-lookup"><span data-stu-id="f79a0-125">There are three implicit type conversions from an interpolated string:</span></span>  

1. <span data-ttu-id="f79a0-126">La conversion d’une chaîne interpolée en un @System.String.</span><span class="sxs-lookup"><span data-stu-id="f79a0-126">Conversion of an interpolated string to a @System.String.</span></span> <span data-ttu-id="f79a0-127">L’exemple suivant retourne une chaîne dont les expressions de chaîne interpolée ont été remplacées par leur représentation sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="f79a0-127">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="f79a0-128">Exemple :</span><span class="sxs-lookup"><span data-stu-id="f79a0-128">For example:</span></span>

   <span data-ttu-id="f79a0-129">[!code-cs[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="f79a0-129">[!code-cs[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]</span></span>  

   <span data-ttu-id="f79a0-130">Il s’agit du résultat final d’une interprétation de chaîne.</span><span class="sxs-lookup"><span data-stu-id="f79a0-130">This is the final result of a string interpretation.</span></span> <span data-ttu-id="f79a0-131">Toutes les occurrences d’accolades doubles (« {{ » et « }} ») sont converties en une seule accolade.</span><span class="sxs-lookup"><span data-stu-id="f79a0-131">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span> 

2. <span data-ttu-id="f79a0-132">La conversion d’une chaîne interpolée en variable <xref:System.IFormattable> qui permet de créer plusieurs chaînes de résultats avec un contenu spécifique de la culture, à partir d’une seule instance <xref:System.IFormattable>.</span><span class="sxs-lookup"><span data-stu-id="f79a0-132">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="f79a0-133">Ce type de conversion est utile pour inclure des éléments, tels que les formats numériques et les formats de date adaptés à une culture.</span><span class="sxs-lookup"><span data-stu-id="f79a0-133">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="f79a0-134">Toutes les occurrences d’accolades doubles (« {{ » et « }} ») sont conservées tant que vous ne mettez pas en forme la chaîne en appelant explicitement ou implicitement la méthode @System.Object.ToString.</span><span class="sxs-lookup"><span data-stu-id="f79a0-134">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the @System.Object.ToString method.</span></span>  <span data-ttu-id="f79a0-135">Toutes les expressions d’interpolation contenues sont converties en {0}, {1}, etc.</span><span class="sxs-lookup"><span data-stu-id="f79a0-135">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="f79a0-136">L’exemple suivant utilise la réflexion pour afficher les membres ainsi que les valeurs de champ et de propriété d’une variable <xref:System.IFormattable> créée à partir d’une chaîne interpolée.</span><span class="sxs-lookup"><span data-stu-id="f79a0-136">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="f79a0-137">Il passe également la variable <xref:System.IFormattable> à la méthode @System.Console(System.String).</span><span class="sxs-lookup"><span data-stu-id="f79a0-137">It also passes the <xref:System.IFormattable> variable to the @System.Console(System.String) method.</span></span>

   <span data-ttu-id="f79a0-138">[!code-cs[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="f79a0-138">[!code-cs[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]</span></span>  

   <span data-ttu-id="f79a0-139">Notez que la chaîne interpolée ne peut être inspectée qu’à l’aide de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="f79a0-139">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="f79a0-140">Si elle est passée à une méthode de mise en forme de chaîne, telle que @System.Console.WriteLine(System.String), ses éléments de mise en forme sont résolus et la chaîne de résultat est retournée.</span><span class="sxs-lookup"><span data-stu-id="f79a0-140">If it is passed to a string formatting method, such as @System.Console.WriteLine(System.String), its format items are resolved and the result string returned.</span></span> 

3. <span data-ttu-id="f79a0-141">La conversion d’une chaîne interpolée en variable <xref:System.FormattableString> qui représente une chaîne de format composite.</span><span class="sxs-lookup"><span data-stu-id="f79a0-141">Conversion of an interpolated string to an <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="f79a0-142">L’inspection de la chaîne de format composite et de son rendu sous forme de chaîne de résultat, peut, par exemple, vous aider à réduire les risques d’attaque par injection pendant la création d’une requête.</span><span class="sxs-lookup"><span data-stu-id="f79a0-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span>  <span data-ttu-id="f79a0-143"><xref:System.FormattableString> inclut également les surcharges <xref:System.FormattableString.ToString> qui vous permettent de générer des chaînes de résultat pour @System.Globalization.InvariantCulture et @System.Globalization.CurrentCulture.</span><span class="sxs-lookup"><span data-stu-id="f79a0-143"><xref:System.FormattableString> also includes <xref:System.FormattableString.ToString> overloads that let you produce result strings for the @System.Globalization.InvariantCulture and @System.Globalization.CurrentCulture.</span></span>  <span data-ttu-id="f79a0-144">Toutes les occurrences d’accolades doubles (« {{ » et « }} ») sont conservées, sauf si vous appliquez une mise en forme.</span><span class="sxs-lookup"><span data-stu-id="f79a0-144">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces, until you format.</span></span>  <span data-ttu-id="f79a0-145">Toutes les expressions d’interpolation contenues sont converties en {0}, {1}, etc.</span><span class="sxs-lookup"><span data-stu-id="f79a0-145">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="f79a0-146">[!code-cs[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="f79a0-146">[!code-cs[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]</span></span>  

## <a name="language-specification"></a><span data-ttu-id="f79a0-147">Spécification du langage</span><span class="sxs-lookup"><span data-stu-id="f79a0-147">Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f79a0-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f79a0-148">See Also</span></span>  
 <span data-ttu-id="f79a0-149"><xref:System.IFormattable?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="f79a0-149"><xref:System.IFormattable?displayProperty=fullName></span></span>   
 <span data-ttu-id="f79a0-150"><xref:System.FormattableString?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="f79a0-150"><xref:System.FormattableString?displayProperty=fullName></span></span>   
 <span data-ttu-id="f79a0-151">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f79a0-151">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 [<span data-ttu-id="f79a0-152">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f79a0-152">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)

