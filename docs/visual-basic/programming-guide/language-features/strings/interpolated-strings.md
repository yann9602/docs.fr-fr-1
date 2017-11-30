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
# <a name="interpolated-strings-visual-basic-reference"></a>Chaînes interpolées (référence Visual Basic)

Permettent de construire des chaînes.  Une chaîne interpolée ressemble à une chaîne de modèle contenant des *expressions interpolées*.  Une chaîne interpolée retourne une chaîne qui remplace les expressions interpolées qu’elle contient par leur représentation sous forme de chaîne. Cette fonctionnalité est disponible dans Visual Basic 14 et versions ultérieures.

Les arguments d’une chaîne interpolée sont plus faciles à comprendre qu’une [chaîne de format composite](../../../../standard/base-types/composite-formatting.md#composite-format-string).  Par exemple, la chaîne interpolée  
  
```vb  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```  
contient deux expressions interpolées, ’{name}’ et ’{hours:hh}’. La chaîne de format composite équivalente est la suivante :

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

La structure d’une chaîne interpolée est :  
  
```vb  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

où : 

- *field-width* est un entier signé qui indique le nombre de caractères du champ. S’il est positif, le champ est aligné à droite ; s’il est négatif, il est aligné à gauche. 

- *format-string* est une chaîne de format qui convient au type d’objet mis en forme. Par exemple, pour un <xref:System.DateTime> valeur, il peut être un [chaîne de format de date et heure standard](~/docs/standard/base-types/standard-date-and-time-format-strings.md) tels que « D » ou « d ».

> [!IMPORTANT]
> Vous ne pouvez avoir n’importe quel espace blanc entre le `$` et `"` qui commence la chaîne. Cela provoque une erreur du compilateur.

 Vous pouvez utiliser une chaîne interpolée partout où vous pouvez utiliser un littéral de chaîne.  La chaîne interpolée est évaluée à chaque exécution du code contenant la chaîne interpolée. Cela vous permet de séparer la définition et l’évaluation d’une chaîne interpolée.  
  
 Pour ajouter une accolade ("{" ou "}") dans une chaîne interpolée, utilisez deux accolades "{{" ou "}}".  Pour plus d’informations, consultez la section « Conversions implicites ».  

Si la chaîne interpolée contient d’autres caractères ayant une signification particulière dans une chaîne interpolée, comme le guillemet ("), les deux-points (:) ou la virgule (,), ils doivent être échappés s’ils se trouvent dans du texte littéral, ou être inclus dans une expression délimitée par des parenthèses s’ils s’agit d’éléments de langage inclus dans une expression interpolée. L’exemple suivant échappe des guillemets pour les inclure dans la chaîne de résultat, et utilise des parenthèses pour délimiter l’expression `(age == 1 ? "" : "s")` pour que le signe deux-points ne soit pas interprété comme commençant une chaîne de format.

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]  

## <a name="implicit-conversions"></a>Conversions implicites  

Trois conversions de type implicite sont possibles à partir d’une chaîne interpolée :  

1. La conversion d’une chaîne interpolée en un <xref:System.String>. L’exemple suivant retourne une chaîne dont les expressions de chaîne interpolée ont été remplacées par leur représentation sous forme de chaîne. Exemple :

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]  

   Il s’agit du résultat final d’une interprétation de chaîne. Toutes les occurrences d’accolades doubles (« {{ » et « }} ») sont converties en une seule accolade. 

2. La conversion d’une chaîne interpolée en variable <xref:System.IFormattable> qui permet de créer plusieurs chaînes de résultats avec un contenu spécifique de la culture, à partir d’une seule instance <xref:System.IFormattable>. Ce type de conversion est utile pour inclure des éléments, tels que les formats numériques et les formats de date adaptés à une culture.  Toutes les occurrences d’accolades doubles (« {{ » et « }} ») sont conservées tant que vous ne mettez pas en forme la chaîne en appelant explicitement ou implicitement la méthode <xref:System.Object.ToString>.  Toutes les expressions d’interpolation contenues sont converties en {0}, {1}, etc.  

   L’exemple suivant utilise la réflexion pour afficher les membres ainsi que les valeurs de champ et de propriété d’une variable <xref:System.IFormattable> créée à partir d’une chaîne interpolée. Il passe également le <xref:System.IFormattable> variable à la <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> (méthode).

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]  

   Notez que la chaîne interpolée ne peut être inspectée qu’à l’aide de la réflexion. Si elle est passée à une chaîne de mise en forme de méthode, telles que <xref:System.Console.WriteLine(System.String)>, ses éléments de format sont résolues et la chaîne de résultat est retourné. 

3. Conversion d’une chaîne interpolée un <xref:System.FormattableString> variable qui représente une chaîne de format composite. L’inspection de la chaîne de format composite et de son rendu sous forme de chaîne de résultat, peut, par exemple, vous aider à réduire les risques d’attaque par injection pendant la création d’une requête. A <xref:System.FormattableString> comprend également :

      - A <xref:System.FormattableString.ToString> surcharge qui produit une chaîne de résultat pour le <xref:System.Globalization.CultureInfo.CurrentCulture>.
      
      - A <xref:System.FormattableString.Invariant%2A> méthode qui produit une chaîne pour le <xref:System.Globalization.CultureInfo.InvariantCulture>.
      
      - A <xref:System.FormattableString.ToString(System.IFormatProvider)> méthode qui produit une chaîne de résultat d’une culture spécifiée. 
  
    Toutes les occurrences d’accolades (« {{ » et «}} ») sont conservées en deux accolades jusqu'à ce que vous mettez en forme.  Toutes les expressions d’interpolation contenues sont converties en {0}, {1}, etc.  

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]  

## <a name="see-also"></a>Voir aussi  
f<xref:System.IFormattable?displayProperty=nameWithType>   
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [Informations de référence sur le langage Visual Basic](index.md)  
 