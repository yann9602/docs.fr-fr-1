---
title: "Cha&#238;nes interpol&#233;es (R&#233;f&#233;rence C# et Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Cha&#238;nes interpol&#233;es (R&#233;f&#233;rence C# et Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Permettent de construire des chaînes.  Une expression de chaîne interpolée s’apparente à une chaîne de modèle contenant des expressions.  Elle crée une chaîne en remplaçant les expressions contenues par les représentations ToString des résultats des expressions.  Les arguments d’une chaîne interpolée sont plus compréhensibles que dans une [Mise en forme composite](../Topic/Composite%20Formatting.md).  Voici un exemple de chaîne interpolée :  
  
```c#  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")  
```  
  
 Une chaîne interpolée se présente comme suit :  
  
```  
$ " <text> { <interpolation-expression> <optional-comma-field-width> <optional-colon-format> } <text> ... } "  
```  
  
 Vous pouvez utiliser une chaîne interpolée partout où vous pouvez utiliser un littéral de chaîne.  Au moment de l’exécution, votre programme exécute le code avec le littéral de chaîne interpolée, et le code calcule un nouveau littéral de chaîne en évaluant les expressions d’interpolation.  Ce calcul se produit à chaque exécution du code contenant la chaîne interpolée.  
  
 Pour ajouter une accolade \(« { » ou « } »\) dans une chaîne interpolée, utilisez deux accolades \(« {{ » ou « }} »\).  Pour plus d’informations, consultez la section « Conversions implicites ».  
  
## Conversions implicites  
 Des conversions de type implicite sont effectuées à partir d’une chaîne interpolée :  
  
```c#  
var s = $"hello, {name}" System.IFormattable s = $"Hello, {name}" System.FormattableString s = $"Hello, {name}"  
  
```  
  
 Le premier exemple génère une valeur `string` où toutes les valeurs d’interpolation de chaîne ont été calculées.  Il s’agit du résultat final, de type string.  Toutes les occurrences d’accolades doubles \(« {{ » et « }} »\) sont converties en une seule accolade.  
  
 Le deuxième exemple génère une variable <xref:System.IFormattable> qui vous permet de convertir la chaîne avec un contexte Invariant.  Cela permet d’obtenir des formats de données et de nombres corrects dans différentes langues.  Toutes les occurrences d’accolades doubles \(« {{ » et « }} »\) sont conservées, sauf si vous appliquez la mise en forme ToString à la chaîne.  Toutes les expressions d’interpolation contenues sont converties en {0}, {1}, etc.  
  
```c#  
s.ToString(null, System.Globalization.CultureInfo.InvariantCulture);  
```  
  
 Le troisième exemple génère une valeur <xref:System.FormattableString>, qui vous permet d’inspecter les objets résultant des calculs d’interpolation.  L’inspection d’objets et de leur rendu sous forme de chaînes vous permet, par exemple, de réduire les risques d’attaque par injection pendant la création d’une requête.<xref:System.FormattableString> constitue un moyen pratique d’obtenir les résultats de chaîne InvariantCulture et CurrentCulture.  Toutes les occurrences d’accolades doubles \(« {{ » et « }} »\) sont conservées, sauf si vous appliquez une mise en forme.  Toutes les expressions d’interpolation contenues sont converties en {0}, {1}, etc.  
  
## Exemples  
  
```c#  
$"Name = {name}, hours = {hours:hh}" var s = $"hello, {name}" System.IFormattable s = $"Hello, {name}" System.FormattableString s = $"Hello, {name}" $"{person.Name, 20} is {person.Age:D3} year {(p.Age == 1 ? "" : "s")} old."  
  
```  
  
 Les guillemets utilisés dans les expressions d’interpolation contenues n’ont pas besoin d’être placés entre d’autres guillemets. En effet, les expressions de chaîne interpolée commencent par $ et le compilateur les analyse comme étant équilibrées jusqu’à ce qu’il rencontre une virgule, un deux\-points ou une accolade fermante.  Pour les mêmes raisons, le dernier exemple utilise des parenthèses pour inclure l’expression conditionnelle \(`p.Age == 1 ? "" : "s"`\) dans l’expression d’interpolation sans le signe deux\-points marquant le début d’une spécification de format.  En dehors de l’expression d’interpolation contenue \(mais toujours à l’intérieur de l’expression de chaîne interpolée\), vous devez utiliser des caractères d’échappement comme vous le faites habituellement.  
  
## Syntaxe  
  
```  
expression: interpolated-string-expression interpolated-string-expression: interpolated-string-start interpolations interpolated-string-end interpolations: single-interpolation single-interpolation interpolated-string-mid interpolations single-interpolation: interpolation-start interpolation-start : regular-string-literal interpolation-start: expression expression , expression  
  
```  
  
## Spécifications du langage  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
 Pour plus d’informations, consultez [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md).  
  
## Voir aussi  
 <xref:System.IFormattable?displayProperty=fullName>   
 <xref:System.FormattableString?displayProperty=fullName>   
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)   
 [Visual Basic Programming Guide](../../../visual-basic/programming-guide/index.md)