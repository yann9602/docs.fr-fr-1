---
title: "Chaînes interpolées (C#)"
ms.date: 10/18/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b8a1fe0be82a0e09d61c66ed463199ff626c9faa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="interpolated-strings-c-reference"></a>Chaînes interpolées (référence C#)

Permettent de construire des chaînes.  Une chaîne interpolée ressemble à une chaîne de modèle contenant des *expressions interpolées*.  Une chaîne interpolée retourne une chaîne qui remplace les expressions interpolées qu’elle contient par leur représentation sous forme de chaîne. Cette fonctionnalité est disponible dans c# 6 et versions ultérieures.

Les arguments d’une chaîne interpolée sont plus faciles à comprendre qu’une [chaîne de format composite](../../../standard/base-types/composite-formatting.md#composite-format-string).  Par exemple, la chaîne interpolée  
  
```csharp  
Console.WriteLine($"Name = {name}, hours = {hours:hh}");
```  
contient deux expressions interpolées, '{name}' et '{heures : hh}'. La chaîne de format composite équivalente est la suivante :

```csharp
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

La structure d’une chaîne interpolée est :  
  
```  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

où : 

- *field-width* est un entier signé qui indique le nombre de caractères du champ. S’il est positif, le champ est aligné à droite ; s’il est négatif, il est aligné à gauche. 

- *format-string* est une chaîne de format qui convient au type d’objet mis en forme. Par exemple, pour une valeur <xref:System.DateTime>, cela peut signifier une chaîne de format de date et heure standard, comme "D" ou "d".

> [!IMPORTANT]
> Vous ne pouvez avoir n’importe quel espace blanc entre le `$` et `"` qui commence la chaîne. Cela provoque une erreur de compilation.

 Vous pouvez utiliser une chaîne interpolée partout où vous pouvez utiliser un littéral de chaîne.  La chaîne interpolée est évaluée à chaque exécution du code contenant la chaîne interpolée. Cela vous permet de séparer la définition et l’évaluation d’une chaîne interpolée.  
  
 Pour ajouter une accolade ("{" ou "}") dans une chaîne interpolée, utilisez deux accolades "{{" ou "}}".  Pour plus d’informations, consultez la section « Conversions implicites ».  

Si la chaîne interpolée contient d’autres caractères ayant une signification particulière dans une chaîne interpolée, comme le guillemet ("), les deux-points (:) ou la virgule (,), ils doivent être échappés s’ils se trouvent dans du texte littéral, ou être inclus dans une expression délimitée par des parenthèses s’ils s’agit d’éléments de langage inclus dans une expression interpolée. L’exemple suivant échappe des guillemets pour les inclure dans la chaîne de résultat, et utilise des parenthèses pour délimiter l’expression `(age == 1 ? "" : "s")` pour que le signe deux-points ne soit pas interprété comme commençant une chaîne de format.

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]  

Textuellement interpolées utilisation des chaînes du `$` suivi par le `@` caractère. Pour plus d’informations sur les chaînes textuelles, consultez le [chaîne](string.md) rubrique. Le code suivant est une version modifiée de l’extrait de code précédent à l’aide d’une chaîne interpolée textuelle :

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings5.cs#1)]  

Les modifications de mise en forme sont nécessaires, car les chaînes textuelles n’obéissent pas à `\` séquences d’échappement.

> [!IMPORTANT]
> Le `$` jeton doit apparaître avant le `@` jeton dans une chaîne interpolée textuelle.


## <a name="implicit-conversions"></a>Conversions implicites  

Trois conversions de type implicite sont possibles à partir d’une chaîne interpolée :  

1. La conversion d’une chaîne interpolée en un <xref:System.String>. L’exemple suivant retourne une chaîne dont les expressions de chaîne interpolée ont été remplacées par leur représentation sous forme de chaîne. Exemple :

   [!code-csharp[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]  

   Il s’agit du résultat final d’une interprétation de chaîne. Toutes les occurrences d’accolades doubles (« {{ » et « }} ») sont converties en une seule accolade. 

2. La conversion d’une chaîne interpolée en variable <xref:System.IFormattable> qui permet de créer plusieurs chaînes de résultats avec un contenu spécifique de la culture, à partir d’une seule instance <xref:System.IFormattable>. Ce type de conversion est utile pour inclure des éléments, tels que les formats numériques et les formats de date adaptés à une culture.  Toutes les occurrences d’accolades doubles (« {{ » et « }} ») sont conservées tant que vous ne mettez pas en forme la chaîne en appelant explicitement ou implicitement la méthode <xref:System.Object.ToString>.  Toutes les expressions d’interpolation contenues sont converties en {0}, {1}, etc.  

   L’exemple suivant utilise la réflexion pour afficher les membres ainsi que les valeurs de champ et de propriété d’une variable <xref:System.IFormattable> créée à partir d’une chaîne interpolée. Il passe également le <xref:System.IFormattable> variable à la <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> (méthode).

   [!code-csharp[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]  

   Notez que la chaîne interpolée ne peut être inspectée qu’à l’aide de la réflexion. Si elle est passée à une chaîne de mise en forme de méthode, telles que <xref:System.Console.WriteLine(System.String)>, ses éléments de format sont résolues et la chaîne de résultat est retourné. 

3. La conversion d’une chaîne interpolée en variable <xref:System.FormattableString> qui représente une chaîne de format composite. L’inspection de la chaîne de format composite et de son rendu sous forme de chaîne de résultat, peut, par exemple, vous aider à réduire les risques d’attaque par injection pendant la création d’une requête. <xref:System.FormattableString> inclut également les surcharges <xref:System.FormattableString.ToString> qui vous permettent de générer des chaînes de résultat pour <xref:System.Globalization.CultureInfo.InvariantCulture> et <xref:System.Globalization.CultureInfo.CurrentCulture>.  Toutes les occurrences d’accolades doubles (« {{ » et « }} ») sont conservées, sauf si vous appliquez une mise en forme.  Toutes les expressions d’interpolation contenues sont converties en {0}, {1}, etc.  

   [!code-csharp[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]  

## <a name="language-specification"></a>Spécification du langage  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)
