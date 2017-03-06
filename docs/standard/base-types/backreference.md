---
title: "Constructions de références arrière dans les expressions régulières"
description: "Constructions de références arrière dans les expressions régulières"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c453ed78-650f-4c3c-9ab4-9d89d250bf88
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: d6fdf23898cacc7ce569f868b3a31b71eff5c716
ms.lasthandoff: 03/02/2017

---

# <a name="backreference-constructs-in-regular-expressions"></a>Constructions de références arrière dans les expressions régulières

Les références arrière offrent un moyen pratique d’identifier un caractère répété ou une sous-chaîne répétée dans une chaîne. Par exemple, si la chaîne d’entrée contient plusieurs occurrences d’une sous-chaîne arbitraire, vous pouvez faire correspondre la première occurrence à un groupe de capture, puis utiliser une référence arrière pour faire correspondre les occurrences suivantes de la sous-chaîne. 

> [!NOTE]
> Une syntaxe distincte est utilisée pour faire référence à des groupes de capture nommés et numérotés dans les chaînes de remplacement. Pour plus d’informations, consultez [Substitutions dans les expressions régulières](substitutions.md).
 
.NET définit des éléments de langage différents pour faire référence aux groupes de capture nommés et numérotés. Pour plus d’informations sur les groupes de capture, consultez [Constructions de regroupement dans les expressions régulières](grouping.md).

## <a name="numbered-backreferences"></a>Références arrière numérotées

Une référence arrière numérotée utilise la syntaxe suivante :

**\**_numéro_

où *numéro* est la position ordinale du groupe de capture dans l’expression régulière. Par exemple, `\4` correspond au contenu du quatrième groupe de capture. Si *numéro* n’est pas défini dans le modèle d’expression régulière, une erreur d’analyse se produit et le moteur d’expression régulière lève une exception [ArgumentException](xref:System.ArgumentException). Par exemple, l’expression régulière `\b(\w+)\s\1` est valide, car `(\w+)` est le premier et unique groupe de capture dans l’expression. D’un autre côté, `\b(\w+)\s\2` n’est pas valide et lève une exception d’argument, car il n’existe aucun groupe de capture numéroté `\2`.

Remarquez l’ambiguïté entre les codes d’échappement octaux (tels que `\16`) et les références arrière **\**_numéro_ qui utilisent la même notation. Cette ambiguïté est résolue comme suit :

* Les expressions `\1` à `\9` sont toujours interprétées comme références arrière et non comme codes octaux.

* Si le premier chiffre d’une expression à plusieurs chiffres est 8 ou 9 (comme `\80` ou `\91`), l’expression est interprétée comme littéral.

* Les expressions à partir de `\10` et plus sont considérées comme des références arrière s’il existe une référence arrière correspondant à ce numéro ; sinon, elles sont interprétées comme des codes octaux.

* Si une expression régulière contient une référence arrière à un numéro de groupe non défini, une erreur d’analyse se produit et le moteur d’expression régulière lève une exception [ArgumentException](xref:System.ArgumentException).

Si l’ambiguïté est un problème, vous pouvez utiliser la notation **\k<**_nom_**>**, qui est sans équivoque et ne peut pas être confondue avec les codes de caractères octaux. De même, les codes hexadécimaux tels que `\xdd` ne sont pas ambigus et ne peuvent pas être confondus avec les références arrière.

L’exemple suivant recherche des caractères de mot doubles dans une chaîne. Il définit une expression régulière, `(\w)\1,`, qui se compose des éléments suivants.

Élément | Description
------- | -----------
`(\w)` | Mettre en correspondance un caractère de mot et l’affecter au premier groupe de capture.
`\1` | Mettre en correspondance le caractère suivant dont la valeur est identique à celle du premier groupe de capture.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(\w)\1";
      string input = "trellis llama webbing dresser swagger";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found '{0}' at position {1}.", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found 'll' at position 3.
//       Found 'll' at position 8.
//       Found 'bb' at position 16.
//       Found 'ss' at position 25.
//       Found 'gg' at position 33.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(\w)\1"
      Dim input As String = "trellis llama webbing dresser swagger"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found '{0}' at position {1}.", _
                           match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Found 'll' at position 3.
'       Found 'll' at position 8.
'       Found 'bb' at position 16.
'       Found 'ss' at position 25.
'       Found 'gg' at position 33.
```

## <a name="named-backreferences"></a>Références arrière nommées

Une référence arrière nommée est définie avec la syntaxe suivante :

**\k<**_nom_**>**

ou :

**\k'**_nom_**'**

où *nom* est le nom d’un groupe de capture défini dans le modèle d’expression régulière. Si *nom* n’est pas défini dans le modèle d’expression régulière, une erreur d’analyse se produit et le moteur d’expression régulière lève une exception [ArgumentException](xref:System.ArgumentException).

L’exemple suivant recherche des caractères de mot doubles dans une chaîne. Il définit une expression régulière, `(?<char>\w)\k<char>`, qui se compose des éléments suivants.

Élément | Description
------- | -----------
`(?<char>\w)` | Mettre en correspondance un caractère de mot et l’affecter à un groupe de capture nommé char.
`\k<char>` | Mettre en correspondance le caractère suivant dont la valeur est identique à celle du groupe de capture char.
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(?<char>\w)\k<char>";
      string input = "trellis llama webbing dresser swagger";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found '{0}' at position {1}.", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found 'll' at position 3.
//       Found 'll' at position 8.
//       Found 'bb' at position 16.
//       Found 'ss' at position 25.
//       Found 'gg' at position 33.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(?<char>\w)\k<char>"
      Dim input As String = "trellis llama webbing dresser swagger"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found '{0}' at position {1}.", _
                           match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Found 'll' at position 3.
'       Found 'll' at position 8.
'       Found 'bb' at position 16.
'       Found 'ss' at position 25.
'       Found 'gg' at position 33.
```

Remarquez que *nom* peut également être la représentation sous forme de chaîne d’un numéro. Par exemple, l’exemple suivant utilise l’expression régulière `(?<2>\w)\k<2>` pour rechercher des caractères de mot doubles dans une chaîne.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(?<2>\w)\k<2>";
      string input = "trellis llama webbing dresser swagger";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found '{0}' at position {1}.", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found 'll' at position 3.
//       Found 'll' at position 8.
//       Found 'bb' at position 16.
//       Found 'ss' at position 25.
//       Found 'gg' at position 33.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(?<2>\w)\k<2>"
      Dim input As String = "trellis llama webbing dresser swagger"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found '{0}' at position {1}.", _
                           match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Found 'll' at position 3.
'       Found 'll' at position 8.
'       Found 'bb' at position 16.
'       Found 'ss' at position 25.
'       Found 'gg' at position 33.
```

## <a name="what-backreferences-match"></a>Correspondance des références arrière

Une référence arrière référence la définition la plus récente d’un groupe (la définition la plus immédiatement à gauche, dans le cadre d’une mise en correspondance de gauche à droite). Quand un groupe effectue plusieurs captures, une référence arrière référence la capture la plus récente. 

L’exemple suivant inclut un modèle d’expression régulière, `(?<1>a)(?<1>\1b)*`, qui redéfinit le groupe nommé \1. Le tableau suivant décrit chaque modèle dans l’expression régulière. 

Modèle | Description
------- | -----------
`(?<1>a)` | Mettre en correspondance le caractère « a » et affecter le résultat au groupe de capture nommé 1.
`(?<1>\1b)*` |Mettre en correspondance 0 ou 1 occurrence du groupe nommé 1 avec un « b » et affecter le résultat au groupe de capture nommé 1. 
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(?<1>a)(?<1>\1b)*";
      string input = "aababb";
      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine("Match: " + match.Value);
         foreach (Group group in match.Groups)
            Console.WriteLine("   Group: " + group.Value);
      }
   }
}
// The example displays the following output:
//          Group: aababb
//          Group: abb
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(?<1>a)(?<1>\1b)*"
      Dim input As String = "aababb"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Match: " + match.Value)
         For Each group As Group In match.Groups
            Console.WriteLIne("   Group: " + group.Value)
         Next
      Next
   End Sub
End Module
' The example display the following output:
'          Group: aababb
'          Group: abb
```

En comparant l’expression régulière à la chaîne d’entrée (« aababb »), le moteur d’expression régulière effectue les opérations suivantes :

1. Il commence au début de la chaîne et réussit à mettre en correspondance « a » avec l’expression `(?<1>a)`. La valeur du groupe 1 est maintenant « a ».

2. Il passe au deuxième caractère et réussit à mettre en correspondance la chaîne « ab » avec l’expression `\1b`, ou « ab ». Il affecte ensuite le résultat, « ab », à `\1`.

3. Il passe au quatrième caractère. L’expression `(?<1>\1b)` doit être mise en correspondance zéro fois ou plus, donc il réussit à mettre en correspondance la chaîne « abb » avec l’expression `\1b`. Il réaffecte le résultat, « abb », à `\1`.

Dans cet exemple, \* est un quantificateur en boucle : il est évalué à plusieurs reprises jusqu’à ce que le moteur d’expression régulière ne puisse pas mettre en correspondance le modèle qu’il définit. Les quantificateurs en boucle ne suppriment pas les définitions de groupe.

Si un groupe n’a capturé aucune sous-chaîne, aucune référence arrière à ce groupe n’est définie et aucune correspondance n’est trouvée. Ce point est illustré par le modèle d’expression régulière `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b,` qui est défini comme suit :

Modèle | Description
------- | -----------
`\b` | Commencer la correspondance à la limite d'un mot.
`(\p{Lu}{2})` | Mettre en correspondance deux lettres majuscules. Il s'agit du premier groupe de capture.
`(\d{2})?` | Mettre en correspondance zéro ou une occurrence de deux chiffres décimaux. Il s'agit du deuxième groupe de capture.
`(\p{Lu}{2})` | Mettre en correspondance deux lettres majuscules. Il s'agit du troisième groupe de capture.
`\b` | Terminer la correspondance à la limite d'un mot.

Une chaîne d’entrée peut mettre en correspondre cette expression régulière même si les deux chiffres décimaux définis par le deuxième groupe de capture ne sont pas présents. L’exemple suivant montre que, même si la mise en correspondance réussit, un groupe de capture vide est trouvé entre deux groupes de capture trouvés.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b";
      string[] inputs = { "AA22ZZ", "AABB" };
      foreach (string input in inputs)
      {
         Match match = Regex.Match(input, pattern);
         if (match.Success)
         {
            Console.WriteLine("Match in {0}: {1}", input, match.Value);
            if (match.Groups.Count > 1)
            {
               for (int ctr = 1; ctr <= match.Groups.Count - 1; ctr++)
               {
                  if (match.Groups[ctr].Success)
                     Console.WriteLine("Group {0}: {1}", 
                                       ctr, match.Groups[ctr].Value);
                  else
                     Console.WriteLine("Group {0}: <no match>", ctr);
               }
            }
         }
         Console.WriteLine();
      }      
   }
}
// The example displays the following output:
//       Match in AA22ZZ: AA22ZZ
//       Group 1: AA
//       Group 2: 22
//       Group 3: ZZ
//       
//       Match in AABB: AABB
//       Group 1: AA
//       Group 2: <no match>
//       Group 3: BB
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b"
      Dim inputs() As String = { "AA22ZZ", "AABB" }
      For Each input As String In inputs
         Dim match As Match = Regex.Match(input, pattern)
         If match.Success Then
            Console.WriteLine("Match in {0}: {1}", input, match.Value)
            If match.Groups.Count > 1 Then
               For ctr As Integer = 1 To match.Groups.Count - 1
                  If match.Groups(ctr).Success Then
                     Console.WriteLine("Group {0}: {1}", _
                                       ctr, match.Groups(ctr).Value)
                  Else
                     Console.WriteLine("Group {0}: <no match>", ctr)
                  End If      
               Next
            End If
         End If
         Console.WriteLine()
      Next      
   End Sub
End Module
' The example displays the following output:
'       Match in AA22ZZ: AA22ZZ
'       Group 1: AA
'       Group 2: 22
'       Group 3: ZZ
'       
'       Match in AABB: AABB
'       Group 1: AA
'       Group 2: <no match>
'       Group 3: BB
```

## <a name="see-also"></a>Voir aussi

[Langage des expressions régulières - Aide-mémoire](quick-ref.md)


