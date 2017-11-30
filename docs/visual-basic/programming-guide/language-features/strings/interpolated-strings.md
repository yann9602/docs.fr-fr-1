---
title: "Chaînes interpolées (Visual Basic)"
ms.date: 10/31/2017
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f865d5a7167847bf869d70a39570413dac271a2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="interpolated-strings-visual-basic-reference"></a><span data-ttu-id="34e1b-102">Chaînes interpolées (référence Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34e1b-102">Interpolated Strings (Visual Basic Reference)</span></span>

<span data-ttu-id="34e1b-103">Permettent de construire des chaînes.</span><span class="sxs-lookup"><span data-stu-id="34e1b-103">Used to construct strings.</span></span>  <span data-ttu-id="34e1b-104">Une chaîne interpolée ressemble à une chaîne de modèle contenant des *expressions interpolées*.</span><span class="sxs-lookup"><span data-stu-id="34e1b-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="34e1b-105">Une chaîne interpolée retourne une chaîne qui remplace les expressions interpolées qu’elle contient par leur représentation sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="34e1b-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="34e1b-106">Cette fonctionnalité est disponible dans Visual Basic 14 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="34e1b-106">This feature is available in Visual Basic 14 and later versions.</span></span>

<span data-ttu-id="34e1b-107">Les arguments d’une chaîne interpolée sont plus faciles à comprendre qu’une [chaîne de format composite](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="34e1b-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="34e1b-108">Par exemple, la chaîne interpolée</span><span class="sxs-lookup"><span data-stu-id="34e1b-108">For example, the interpolated string</span></span>  
  
```vb  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```  
<span data-ttu-id="34e1b-109">contient deux expressions interpolées, ’{name}’ et ’{hours:hh}’.</span><span class="sxs-lookup"><span data-stu-id="34e1b-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="34e1b-110">La chaîne de format composite équivalente est la suivante :</span><span class="sxs-lookup"><span data-stu-id="34e1b-110">The equivalent composite format string is:</span></span>

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

<span data-ttu-id="34e1b-111">La structure d’une chaîne interpolée est :</span><span class="sxs-lookup"><span data-stu-id="34e1b-111">The structure of an interpolated string is:</span></span>  
  
```vb  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

<span data-ttu-id="34e1b-112">où :</span><span class="sxs-lookup"><span data-stu-id="34e1b-112">where:</span></span> 

- <span data-ttu-id="34e1b-113">*field-width* est un entier signé qui indique le nombre de caractères du champ.</span><span class="sxs-lookup"><span data-stu-id="34e1b-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="34e1b-114">S’il est positif, le champ est aligné à droite ; s’il est négatif, il est aligné à gauche.</span><span class="sxs-lookup"><span data-stu-id="34e1b-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span> 

- <span data-ttu-id="34e1b-115">*format-string* est une chaîne de format qui convient au type d’objet mis en forme.</span><span class="sxs-lookup"><span data-stu-id="34e1b-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="34e1b-116">Par exemple, pour un <xref:System.DateTime> valeur, il peut être un [chaîne de format de date et heure standard](~/docs/standard/base-types/standard-date-and-time-format-strings.md) tels que « D » ou « d ».</span><span class="sxs-lookup"><span data-stu-id="34e1b-116">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](~/docs/standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34e1b-117">Vous ne pouvez avoir n’importe quel espace blanc entre le `$` et `"` qui commence la chaîne.</span><span class="sxs-lookup"><span data-stu-id="34e1b-117">You cannot have any whitespace between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="34e1b-118">Cela provoque une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="34e1b-118">Doing so causes a compiler error.</span></span>

 <span data-ttu-id="34e1b-119">Vous pouvez utiliser une chaîne interpolée partout où vous pouvez utiliser un littéral de chaîne.</span><span class="sxs-lookup"><span data-stu-id="34e1b-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="34e1b-120">La chaîne interpolée est évaluée à chaque exécution du code contenant la chaîne interpolée.</span><span class="sxs-lookup"><span data-stu-id="34e1b-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="34e1b-121">Cela vous permet de séparer la définition et l’évaluation d’une chaîne interpolée.</span><span class="sxs-lookup"><span data-stu-id="34e1b-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>  
  
 <span data-ttu-id="34e1b-122">Pour ajouter une accolade ("{" ou "}") dans une chaîne interpolée, utilisez deux accolades "{{" ou "}}".</span><span class="sxs-lookup"><span data-stu-id="34e1b-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="34e1b-123">Pour plus d’informations, consultez la section « Conversions implicites ».</span><span class="sxs-lookup"><span data-stu-id="34e1b-123">See the Implicit Conversions section for more details.</span></span>  

<span data-ttu-id="34e1b-124">Si la chaîne interpolée contient d’autres caractères ayant une signification particulière dans une chaîne interpolée, comme le guillemet ("), les deux-points (:) ou la virgule (,), ils doivent être échappés s’ils se trouvent dans du texte littéral, ou être inclus dans une expression délimitée par des parenthèses s’ils s’agit d’éléments de langage inclus dans une expression interpolée.</span><span class="sxs-lookup"><span data-stu-id="34e1b-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="34e1b-125">L’exemple suivant échappe des guillemets pour les inclure dans la chaîne de résultat, et utilise des parenthèses pour délimiter l’expression `(age == 1 ? "" : "s")` pour que le signe deux-points ne soit pas interprété comme commençant une chaîne de format.</span><span class="sxs-lookup"><span data-stu-id="34e1b-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]  

## <a name="implicit-conversions"></a><span data-ttu-id="34e1b-126">Conversions implicites</span><span class="sxs-lookup"><span data-stu-id="34e1b-126">Implicit Conversions</span></span>  

<span data-ttu-id="34e1b-127">Trois conversions de type implicite sont possibles à partir d’une chaîne interpolée :</span><span class="sxs-lookup"><span data-stu-id="34e1b-127">There are three implicit type conversions from an interpolated string:</span></span>  

1. <span data-ttu-id="34e1b-128">La conversion d’une chaîne interpolée en un <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="34e1b-128">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="34e1b-129">L’exemple suivant retourne une chaîne dont les expressions de chaîne interpolée ont été remplacées par leur représentation sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="34e1b-129">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="34e1b-130">Exemple :</span><span class="sxs-lookup"><span data-stu-id="34e1b-130">For example:</span></span>

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]  

   <span data-ttu-id="34e1b-131">Il s’agit du résultat final d’une interprétation de chaîne.</span><span class="sxs-lookup"><span data-stu-id="34e1b-131">This is the final result of a string interpretation.</span></span> <span data-ttu-id="34e1b-132">Toutes les occurrences d’accolades doubles (« {{ » et « }} ») sont converties en une seule accolade.</span><span class="sxs-lookup"><span data-stu-id="34e1b-132">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span> 

2. <span data-ttu-id="34e1b-133">La conversion d’une chaîne interpolée en variable <xref:System.IFormattable> qui permet de créer plusieurs chaînes de résultats avec un contenu spécifique de la culture, à partir d’une seule instance <xref:System.IFormattable>.</span><span class="sxs-lookup"><span data-stu-id="34e1b-133">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="34e1b-134">Ce type de conversion est utile pour inclure des éléments, tels que les formats numériques et les formats de date adaptés à une culture.</span><span class="sxs-lookup"><span data-stu-id="34e1b-134">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="34e1b-135">Toutes les occurrences d’accolades doubles (« {{ » et « }} ») sont conservées tant que vous ne mettez pas en forme la chaîne en appelant explicitement ou implicitement la méthode <xref:System.Object.ToString>.</span><span class="sxs-lookup"><span data-stu-id="34e1b-135">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="34e1b-136">Toutes les expressions d’interpolation contenues sont converties en {0}, {1}, etc.</span><span class="sxs-lookup"><span data-stu-id="34e1b-136">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="34e1b-137">L’exemple suivant utilise la réflexion pour afficher les membres ainsi que les valeurs de champ et de propriété d’une variable <xref:System.IFormattable> créée à partir d’une chaîne interpolée.</span><span class="sxs-lookup"><span data-stu-id="34e1b-137">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="34e1b-138">Il passe également le <xref:System.IFormattable> variable à la <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="34e1b-138">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]  

   <span data-ttu-id="34e1b-139">Notez que la chaîne interpolée ne peut être inspectée qu’à l’aide de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="34e1b-139">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="34e1b-140">Si elle est passée à une chaîne de mise en forme de méthode, telles que <xref:System.Console.WriteLine(System.String)>, ses éléments de format sont résolues et la chaîne de résultat est retourné.</span><span class="sxs-lookup"><span data-stu-id="34e1b-140">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span> 

3. <span data-ttu-id="34e1b-141">Conversion d’une chaîne interpolée un <xref:System.FormattableString> variable qui représente une chaîne de format composite.</span><span class="sxs-lookup"><span data-stu-id="34e1b-141">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="34e1b-142">L’inspection de la chaîne de format composite et de son rendu sous forme de chaîne de résultat, peut, par exemple, vous aider à réduire les risques d’attaque par injection pendant la création d’une requête.</span><span class="sxs-lookup"><span data-stu-id="34e1b-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="34e1b-143">A <xref:System.FormattableString> comprend également :</span><span class="sxs-lookup"><span data-stu-id="34e1b-143">A <xref:System.FormattableString> also includes:</span></span>

      - <span data-ttu-id="34e1b-144">A <xref:System.FormattableString.ToString> surcharge qui produit une chaîne de résultat pour le <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="34e1b-144">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      
      - <span data-ttu-id="34e1b-145">A <xref:System.FormattableString.Invariant%2A> méthode qui produit une chaîne pour le <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="34e1b-145">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      
      - <span data-ttu-id="34e1b-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> méthode qui produit une chaîne de résultat d’une culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="34e1b-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span> 
  
    <span data-ttu-id="34e1b-147">Toutes les occurrences d’accolades (« {{ » et «}} ») sont conservées en deux accolades jusqu'à ce que vous mettez en forme.</span><span class="sxs-lookup"><span data-stu-id="34e1b-147">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span></span>  <span data-ttu-id="34e1b-148">Toutes les expressions d’interpolation contenues sont converties en {0}, {1}, etc.</span><span class="sxs-lookup"><span data-stu-id="34e1b-148">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]  

## <a name="see-also"></a><span data-ttu-id="34e1b-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34e1b-149">See Also</span></span>  
<span data-ttu-id="34e1b-150">f<xref:System.IFormattable?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="34e1b-150">f <xref:System.IFormattable?displayProperty=nameWithType></span></span>   
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [<span data-ttu-id="34e1b-151">Informations de référence sur le langage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="34e1b-151">Visual Basic Language Reference</span></span>](index.md)  
 