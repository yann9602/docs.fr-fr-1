---
title: "Constructions d’alternative dans les expressions régulières"
description: "Constructions d’alternative dans les expressions régulières"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 59ffac4d-fc6e-461f-8783-d9f8dc88ce2c
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: fa2a880e5bcc36354bd59d3dc032180c89984f1d
ms.lasthandoff: 03/13/2017

---

# <a name="alternation-constructs-in-regular-expressions"></a>Constructions d’alternative dans les expressions régulières

Les constructions d'alternative modifient une expression régulière pour permettre la correspondance de type inclusif/exclusif ou conditionnelle. .NET prend en charge trois constructions d’alternative :

* Critères spéciaux avec **|**

* Correspondance conditionnelle avec **(?(**_expression_**)**_oui_**|**_non_**)**

* Correspondance conditionnelle selon un groupe capturé valide

## <a name="pattern-matching-with-"></a>Critères spéciaux avec |

Vous pouvez utiliser la barre verticale (|) pour mettre en correspondance un modèle d’une série, dans laquelle le caractère | sépare chaque modèle. 

Tout comme la classe de caractères positive, le caractère | peut être utilisé pour mettre en correspondance n’importe quel nombre de caractères uniques. L’exemple suivant utilise une classe de caractères positive et des critères spéciaux de type inclusif/exclusif avec le caractère | pour trouver des occurrences des mots « gray » ou « grey » dans une chaîne. Dans ce cas, le caractère | produit une expression régulière qui est plus détaillée. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      // Regular expression using character class.
      string pattern1 = @"\bgr[ae]y\b";
      // Regular expression using either/or.
      string pattern2 = @"\bgr(a|e)y\b";

      string input = "The gray wolf blended in among the grey rocks.";
      foreach (Match match in Regex.Matches(input, pattern1))
         Console.WriteLine("'{0}' found at position {1}", 
                           match.Value, match.Index);
      Console.WriteLine();
      foreach (Match match in Regex.Matches(input, pattern2))
         Console.WriteLine("'{0}' found at position {1}", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       'gray' found at position 4
//       'grey' found at position 35
//       
//       'gray' found at position 4
//       'grey' found at position 35           
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      ' Regular expression using character class.
      Dim pattern1 As String = "\bgr[ae]y\b"
      ' Regular expression using either/or.
      Dim pattern2 As String = "\bgr(a|e)y\b"

      Dim input As String = "The gray wolf blended in among the grey rocks."
      For Each match As Match In Regex.Matches(input, pattern1)
         Console.WriteLine("'{0}' found at position {1}", _
                           match.Value, match.Index)
      Next      
      Console.WriteLine()
      For Each match As Match In Regex.Matches(input, pattern2)
         Console.WriteLine("'{0}' found at position {1}", _
                           match.Value, match.Index)
      Next      
   End Sub
End Module
' The example displays the following output:
'       'gray' found at position 4
'       'grey' found at position 35
'       
'       'gray' found at position 4
'       'grey' found at position 35 
```

L’expression régulière qui utilise le caractère |, `\bgr(a|e)y\b,`, est interprétée comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`\b` | Commencer à la limite d'un mot.
`gr` | Mettre en correspondance les caractères « gr ».
`(a|e)` | Mettre en correspondance un « a » ou un « e ».
`y\b` |    Mettre en correspondance un « y » à la limite d'un mot.


Le caractère | peut également être utilisé pour effectuer une correspondance de type inclusif/exclusif avec plusieurs caractères ou sous-expressions, qui peuvent inclure toute combinaison de caractère littéraux et éléments de langage d’expressions régulières. (La classe de caractères ne fournit pas cette fonctionnalité.) L’exemple suivant utilise le caractère | pour extraire un numéro de sécurité sociale (SSN) américain, qui est un nombre de 9 chiffres au format *ddd-dd-dddd*, ou un numéro d’identification de l’employeur (EIN) américain, qui est un nombre de 9 chiffres au format *dd-ddddddd*.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b";
      string input = "01-9999999 020-333333 777-88-9999";
      Console.WriteLine("Matches for {0}:", pattern);
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Matches for \b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b:
//          01-9999999 at position 0
//          777-88-9999 at position 22
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b"
      Dim input As String = "01-9999999 020-333333 777-88-9999"
      Console.WriteLine("Matches for {0}:", pattern)
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Matches for \b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b:
'          01-9999999 at position 0
'          777-88-9999 at position 22
```

L'expression régulière `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` est interprétée comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`\b` | Commencer à la limite d'un mot.
`(\d{2}-\d{7}|;\d{3}-\d{2}-\d{4})` | Mettre en correspondance l'un ou l'autre des éléments suivants : deux chiffres décimaux suivis d'un trait d'union suivi de sept chiffres décimaux, ou alors trois chiffres décimaux, un trait d'union, deux chiffres décimaux, un autre trait d'union et quatre chiffres décimaux. 
`\d` | Terminer la correspondance à la limite d'un mot.
                                         
## <a name="conditional-matching-with-an-expression"></a>Correspondance conditionnelle avec une expression

Cet élément de langage tente de mettre en correspondance un modèle parmi deux fournis selon qu'il parvient ou non à mettre en correspondance un modèle initial. Sa syntaxe est la suivante :

**(?(**_expression_**)**_oui_**|**_non_**)**

où *expression* est le modèle initial à faire correspondre, *oui* est le modèle à faire correspondre si l’expression est mise en correspondance, et *no* est le modèle facultatif à faire correspondre si l’*expression* n’est pas mise en correspondance. Le moteur d’expression régulière traite l’*expression* comme une assertion de largeur nulle ; c’est-à-dire que le moteur d’expression régulière n’avance pas dans le flux d’entrée après avoir évalué l’*expression*. Par conséquent, cette construction est équivalente à la suivante :

**(?(?**=_expression_**)**_oui_**|**_non_**)**

où **(?**=_expression_**)** est une construction d’assertion de largeur nulle. (Pour plus d’informations, consultez [Constructions de regroupement dans les expressions régulières](grouping.md).) Étant donné que le moteur d’expression régulière interprète l’*expression* comme une ancre (assertion de largeur nulle), l’*expression* doit être soit une assertion de largeur nulle (pour plus d’informations, consultez [Ancres dans les expressions régulières](anchors.md)), soit une sous-expression qui est également contenue dans *oui*. Sinon, aucune correspondance ne peut être établie avec le modèle *oui*. 

> [!NOTE]
> Si l’*expression* est un groupe de capture nommé ou numéroté, la construction d’alternative est interprétée comme un test de capture. Pour plus d’informations, consultez la section suivante, [Correspondance conditionnelle selon un groupe capturé valide](#conditional-matching-based-on-a-valid-captured-group). En d'autres termes, le moteur des expressions régulières ne tente pas de mettre en correspondance la sous-chaîne capturée, mais à la place teste la présence ou l'absence du groupe.
 

L’exemple suivant est une variante de l’exemple qui s’affiche dans la section précédente. Il utilise la mise en correspondance conditionnelle pour déterminer si les trois premiers caractères après une limite de mot se composent de deux chiffres suivis d'un trait d'union. Si c'est le cas, il tente de mettre en correspondance un numéro d'identification de l'employeur (EIN) américain. Si ce n'est pas le cas, il tente de mettre en correspondance un numéro de sécurité sociale (SSN) américain.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b";
      string input = "01-9999999 020-333333 777-88-9999";
      Console.WriteLine("Matches for {0}:", pattern);
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Matches for \b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b:
//          01-9999999 at position 0
//          777-88-9999 at position 22
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b"
      Dim input As String = "01-9999999 020-333333 777-88-9999"
      Console.WriteLine("Matches for {0}:", pattern)
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Matches for \b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b:
'          01-9999999 at position 0
'          777-88-9999 at position 22
```

Le modèle d'expression régulière `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` est interprété comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`\b` | Commencer à la limite d'un mot.
`(?(\d{2}-)` | Déterminer si les trois caractères suivants se composent de deux chiffres suivis d'un trait d'union.
`\d{2}-\d{7}` | Si le modèle précédent correspond, mettre en correspondance deux chiffres suivis d'un trait d'union suivi de sept chiffres.
`\d{3}-\d{2}-\d{4}` | Si le modèle ne correspond pas, faire correspondre trois chiffres décimaux, un trait d'union, deux chiffres décimaux, un autre trait d'union et quatre chiffres décimaux. 
`\b` | Mettre en correspondance la limite d'un mot.
 
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>Correspondance conditionnelle selon un groupe capturé valide

Cet élément de langage essaie de faire correspondre l'un de deux modèles selon qu'il peut correspondre à un groupe capturé spécifié. Sa syntaxe est la suivante :

**(?(**_nom_**)**_oui_**|**_non_**)**

ou

**(?(**_numéro_**)**_oui_**|**_non_**)**

où *nom* est le nom et *numéro* est le numéro d’un groupe de capture, *oui* est l’expression à faire correspondre si nom ou nombre a une correspondance et *non* est l’expression facultative à faire correspondre dans le cas contraire.

Si *nom* ne correspond pas au nom d’un groupe de capture utilisé dans le modèle d’expression régulière, la construction d’alternative est interprétée comme un test d’expression, comme expliqué dans la section précédente. En général, cela signifie que l’expression prend la valeur `false`. Si `number` ne correspond pas à un groupe de capture numéroté utilisé dans le modèle d’expression régulière, le moteur d’expression régulière lève un [ArgumentException](xref:System.ArgumentException).

L’exemple suivant est une variante de l’exemple qui s’affiche dans la section précédente. Il utilise un groupe de capture nommé `n2` qui se compose de deux chiffres suivis d'un trait d'union. La construction d'alternative tests si ce groupe de capture a été mis en correspondance dans la chaîne d'entrée. Si c'est le cas, la construction alternative essaie de mettre en correspondance les sept derniers chiffres d'un numéro d'identification de l'employeur (EIN) américain. Si ce n'est le cas, il essaie de faire correspondre un numéro de sécurité sociale (SSN) américain.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b";
      string input = "01-9999999 020-333333 777-88-9999";
      Console.WriteLine("Matches for {0}:", pattern);
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Matches for \b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b:
//          01-9999999 at position 0
//          777-88-9999 at position 22
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b"
      Dim input As String = "01-9999999 020-333333 777-88-9999"
      Console.WriteLine("Matches for {0}:", pattern)
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
   End Sub
End Module
```

Le modèle d'expression régulière `\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` est interprété comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`\b` | Commencer à la limite d'un mot.
`(?<n2>\d{2}-)*` | Mettre en correspondance zéro ou une occurrence de deux chiffres suivis d'un trait d'union. Nommer ce groupe de capture `n2`.
`(?(n2)` | Testez si `n2` a été mis en correspondance dans la chaîne d'entrée. 
`)\d{7}` | Si `n2` a été mis en correspondance, faites correspondre sept chiffres décimaux.
`|;\d{3}-\d{2}-\d{4}` | Si `n2` ne correspondait pas, faites correspondre trois chiffres décimaux, un trait d'union, deux chiffres décimaux, un autre trait d'union et quatre chiffres décimaux. 
`\b` | Mettre en correspondance la limite d'un mot.
 
Une variation de cet exemple qui utilise un groupe numéroté au lieu d'un groupe nommé est illustrée dans l'exemple suivant. Son modèle d'expression régulière est `\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b";
      string input = "01-9999999 020-333333 777-88-9999";
      Console.WriteLine("Matches for {0}:", pattern);
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
   }
}
// The example display the following output:
//       Matches for \b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b:
//          01-9999999 at position 0
//          777-88-9999 at position 22
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b"
      Dim input As String = "01-9999999 020-333333 777-88-9999"
      Console.WriteLine("Matches for {0}:", pattern)
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Matches for \b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b:
'          01-9999999 at position 0
'          777-88-9999 at position 22
```

Voir aussi

[Langage des expressions régulières - Aide-mémoire](quick-ref.md)


