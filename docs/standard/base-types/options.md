---
title: "Options des expressions régulières"
description: "Options des expressions régulières"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 2db2c3e6-953e-4913-8168-d707c437f2df
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: a2a9fe356a0b2e9cf9415714bc01b77ea86229fc

---

# <a name="regular-expression-options"></a>Options des expressions régulières

Par défaut, la comparaison d’une chaîne d’entrée avec des caractères littéraux dans un modèle d’expression régulière respecte la casse, l’espace blanc dans un modèle d’expression régulière est interprété comme un espace blanc littéral et les groupes de capture dans une expression régulière sont nommés de manière implicite aussi bien qu’explicite. Vous pouvez modifier ces aspects, ainsi que d'autres, du comportement par défaut des expressions régulières en spécifiant des options d'expression régulière. Ces options, qui sont répertoriées dans le tableau suivant, peuvent être incluses inline dans le cadre du modèle d’expression régulière ou fournies à un constructeur de classe [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) ou à une méthode de mise en correspondance de modèle statique comme valeur d’énumération [System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions). 

Membre RegexOptions | Caractère inline | Effet
------------------- | ---------------- | ------ 
[Aucun](xref:System.Text.RegularExpressions.RegexOptions.None) | Non disponible | Utilise le comportement par défaut. Pour plus d’informations, consultez [Options par défaut](#default-options).
[IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) | **i** | Utilise la correspondance qui ne respecte pas la casse. Pour plus d’informations, consultez [Correspondance qui ne respecte pas la casse](#case-insensitive-matching).
[Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) | **m** | Utilise le mode multiligne, où **^** et **$** correspondent au début et à la fin de chaque ligne (plutôt qu’au début et à la fin de la chaîne d’entrée). Pour plus d’informations, consultez [Mode multiligne](#multiline-mode).
[Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) | **s** | Utilise le mode à ligne simple, où le point (**.**) correspond à chaque caractère (y compris **\n**). Pour plus d’informations, consultez [Mode à ligne simple](#single-line-mode).
[ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) | **n** | Ne capture aucun groupe sans nom. Les seules captures valides sont les groupes explicitement nommés ou numérotés de la forme **(?<**_nom_**>** _sous-expression_**)**. Pour plus d’informations, consultez [Captures explicites uniquement](#explicit-captures-only).
[Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) | Non disponible | Compile l'expression régulière en un assembly. Pour plus d’informations, consultez [Expressions régulières compilées](#compiled-regular-expressions).
[IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) | **x** | Exclure du modèle l’espace blanc sans séquence d’échappement et autoriser les commentaires après un signe dièse (**#**). Pour plus d’informations, consultez [Ignorer l’espace blanc](#ignore-white-space).
[RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft) | Non disponible | Modifie le sens de la recherche. La recherche s'effectue de droite à gauche au lieu de gauche à droite. Pour plus d’informations, consultez [Mode de recherche de droite à gauche](#right-to-left-mode).
[ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript) | Non disponible | Active le comportement compatible ECMAScript pour l’expression. Pour plus d’informations, consultez [Comportement de correspondance ECMAScript](#ecmascript-matching-behavior).
[CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant) | Non disponible | Ignorer les différences culturelles propres à la langue. Pour plus d’informations, consultez [Comparaison utilisant la culture dite indifférente](#comparison-using-the-invariant-culture).
 
## <a name="specifying-the-options"></a>Spécification des options

Vous pouvez spécifier les options des expressions régulières de trois façons :

* Dans le paramètre *options* d’un constructeur de classe [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) comme [Regex.Regex(String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.%23ctor(System.String,System.Text.RegularExpressions.RegexOptions)) ou d’une méthode de mise en correspondance de modèle statique (Shared en Visual Basic) comme [Regex.Match(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions)). Le paramètre *options* est une combinaison OR au niveau du bit de valeurs énumérées [System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions). 

  Quand des options sont fournies à une instance de [Regex](xref:System.Text.RegularExpressions.Regex) à l’aide du paramètre *options* d’un constructeur de classe, les options sont affectées à la propriété [System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions). Cependant, la propriété [System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) ne reflète pas les options inline dans le modèle d’expression régulière lui-même. 

  L'exemple suivant illustre cette situation. Il utilise le paramètre *options* de la méthode [Regex.Match(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) pour autoriser la correspondance qui ne respecte pas la casse et pour ignorer l’espace blanc du modèle pendant l’identification des mots commençant par la lettre « d ».

  ```csharp
  string pattern = @"d \w+ \s";
  string input = "Dogs are decidedly good pets.";
  RegexOptions options = RegexOptions.IgnoreCase | RegexOptions.IgnorePatternWhitespace;
  
  foreach (Match match in Regex.Matches(input, pattern, options))
     Console.WriteLine("'{0}// found at index {1}.", match.Value, match.Index);
  // The example displays the following output:
  //    'Dogs // found at index 0.
  //    'decidedly // found at index 9.      
  ```

  ```vb
  Dim pattern As String = "d \w+ \s"
  Dim input As String = "Dogs are decidedly good pets."
  Dim options As RegexOptions = RegexOptions.IgnoreCase Or RegexOptions.IgnorePatternWhitespace

  For Each match As Match In Regex.Matches(input, pattern, options)
     Console.WriteLine("'{0}' found at index {1}.", match.Value, match.Index)
  Next
  ' The example displays the following output:
  '    'Dogs ' found at index 0.
  '    'decidedly ' found at index 9.  
  ```

* En appliquant des options inline dans un modèle d’expression régulière avec la syntaxe **(?imnsx-imnsx)**. L’option s’applique au modèle depuis le point où elle est définie jusqu’à la fin du modèle ou jusqu’au point auquel sa définition est annulée par une autre option inline. Notez que la propriété [System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) d’une instance de [Regex](xref:System.Text.RegularExpressions.Regex) ne reflète pas ces options inline. Pour plus d’informations, consultez la rubrique [Constructions diverses dans les expressions régulières](miscellaneous.md).

  L'exemple suivant illustre cette situation. Il utilise des options inline pour autoriser la correspondance qui ne respecte pas la casse et pour ignorer l’espace blanc du modèle pendant l’identification des mots commençant par la lettre « d ».

  ```csharp
  string pattern = @"(?ix) d \w+ \s";
  string input = "Dogs are decidedly good pets.";
  
  foreach (Match match in Regex.Matches(input, pattern))
     Console.WriteLine("'{0}// found at index {1}.", match.Value, match.Index);
  // The example displays the following output:
  //    'Dogs // found at index 0.
  //    'decidedly // found at index 9.      
  ```

  ```vb
  Dim pattern As String = "\b(?ix) d \w+ \s"
  Dim input As String = "Dogs are decidedly good pets."

  For Each match As Match In Regex.Matches(input, pattern)
     Console.WriteLine("'{0}' found at index {1}.", match.Value, match.Index)
  Next
  ' The example displays the following output:
  '    'Dogs ' found at index 0.
  '    'decidedly ' found at index 9.  
  ```

* En appliquant des options inline dans une construction de regroupement particulière au sein d’un modèle d’expression régulière avec la syntaxe **(?imnsx-imnsx:**_sous-expression_**)**. L'absence de signe avant un jeu d'options active ce dernier, tandis qu'un signe moins le désactive. (**?** est une partie fixe de la syntaxe de la construction du langage qui est obligatoire, que les options soient activées ou désactivées.) L'option ne s'applique qu'à ce groupe. Pour plus d’informations, consultez [Constructions de regroupement dans les expressions régulières](grouping.md).

  L'exemple suivant illustre cette situation. Il utilise des options inline dans une construction de regroupement pour autoriser la correspondance qui ne respecte pas la casse et pour ignorer l’espace blanc du modèle pendant l’identification des mots commençant par la lettre « d ».

  ```csharp
  string pattern = @"\b(?ix: d \w+)\s";
  string input = "Dogs are decidedly good pets.";
  
  foreach (Match match in Regex.Matches(input, pattern))
     Console.WriteLine("'{0}// found at index {1}.", match.Value, match.Index);
  // The example displays the following output:
  //    'Dogs // found at index 0.
  //    'decidedly // found at index 9.      
  ```

  ```vb
  Dim pattern As String = "\b(?ix: d \w+)\s"
  Dim input As String = "Dogs are decidedly good pets."

  For Each match As Match In Regex.Matches(input, pattern)
     Console.WriteLine("'{0}' found at index {1}.", match.Value, match.Index)
  Next
  ' The example displays the following output:
  '    'Dogs ' found at index 0.
  '    'decidedly ' found at index 9. 
  ```


Si des options sont spécifiées inline, un signe moins (-) avant une option ou un jeu d’options désactive ces options. Par exemple, la construction inline **(?ix-ms)** active les options [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) et [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) et désactive les options [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) et [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline). Toutes les options d'expression régulière sont désactivées par défaut.

> [!NOTE]
> Si les options d’expression régulière spécifiées dans le paramètre options d’un appel de constructeur ou de méthode entrent en conflit avec les options spécifiées inline dans un modèle d’expression régulière, ces dernières sont utilisées.
 

Les cinq options d’expression régulière suivantes peuvent être définies avec le paramètre *options* et inline :

* [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase)

* [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline)

* [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline)

* [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture)

* [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace)

Les cinq options d’expression régulière suivantes peuvent être définies avec le paramètre *options*, mais ne peuvent pas être définies inline :

* [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None)

* [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled)

* [RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft)

* [RegexOptions.CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant)

* [RegexOptions.ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript)

## <a name="determining-the-options"></a>Détermination des options

Vous pouvez déterminer les options initialement fournies à un objet [Regex](xref:System.Text.RegularExpressions.Regex) au moment de son instanciation en récupérant la valeur de la propriété [Regex.Options](xref:System.Text.RegularExpressions.Regex.Options) en lecture seule.

Pour tester la présence d’une option autre que [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None), effectuez une opération AND avec la valeur de la propriété [Regex.Options](xref:System.Text.RegularExpressions.Regex.Options) et la valeur [RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) qui vous intéresse. Ensuite, déterminez si le résultat est égal à cette valeur [RegexOptions](xref:System.Text.RegularExpressions.RegexOptions). L’exemple suivant détermine si l’option [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) a été définie. 

```csharp
if ((rgx.Options & RegexOptions.IgnoreCase) == RegexOptions.IgnoreCase)
   Console.WriteLine("Case-insensitive pattern comparison.");
else
   Console.WriteLine("Case-sensitive pattern comparison.");
```

```vb
If (rgx.Options And RegexOptions.IgnoreCase) = RegexOptions.IgnoreCase Then
   Console.WriteLine("Case-insensitive pattern comparison.")
Else
   Console.WriteLine("Case-sensitive pattern comparison.")
End If 
```

Pour tester la présence de [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None), déterminez si la valeur de la propriété [RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) est égale à [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None), comme l’illustre l’exemple suivant. 

```csharp
if (rgx.Options == RegexOptions.None)
   Console.WriteLine("No options have been set.");
```

```vb
If rgx.Options = RegexOptions.None Then
   Console.WriteLine("No options have been set.")
End If
```

Les sections suivantes répertorient les options prises en charge par les expressions régulières dans le .NET. 

## <a name="default-options"></a>Options par défaut

L’option [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None) indique qu’aucune option n’a été spécifiée et que le moteur d’expression régulière utilise son comportement par défaut. Ce dernier est détaillé ci-après :

* Le modèle est interprété en tant qu'expression régulière canonique, plutôt qu'en tant qu'expression régulière ECMAScript.

* Le modèle d'expression régulière est appliqué à la chaîne d'entrée de la gauche vers la droite.

* Les comparaisons respectent la casse.

* Les éléments de langage **^** et **$** correspondent au début et à la fin de la chaîne d’entrée.

* L’élément de langage **.** correspond à chaque caractère à l’exception de **\n**.

* Tout espace blanc dans un modèle d’expression régulière est interprété en tant qu’espace littéral.

* Les conventions de la culture actuelle sont utilisées pendant la comparaison du modèle à la chaîne d'entrée. 

* Les groupes de capture dans le modèle d’expression régulière sont implicites aussi bien qu’explicites. 

> [!NOTE]
> L’option [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None) n’a pas d’équivalent inline. Quand les options d'expression régulière sont appliquées inline, le comportement par défaut est restauré option par option, via la désactivation de chaque option concernée. Par exemple, `(?i)` active la comparaison sans respect de la casse, tandis que `(?-i)` restaure la comparaison avec respect de la casse par défaut.
 
Comme l’option [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None) représente le comportement par défaut du moteur d’expression régulière, elle est rarement spécifiée de manière explicite dans un appel de méthode. Un constructeur ou une méthode de mise en correspondance de modèle statique sans paramètre options est appelé à la place.

## <a name="case-insensitive-matching"></a>Correspondance qui ne respecte pas la casse

L’option [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase), ou l’option inline **i**, fournit une correspondance qui ne respecte pas la casse. Par défaut, les conventions de gestion de la casse de la culture actuelle sont utilisées.

L'exemple suivant définit un modèle d'expression régulière, `\bthe\w*\b`, qui met en correspondance tous les mots commençant par « the ». Comme le premier appel de la méthode Match utilise la comparaison avec respect de la casse par défaut, la chaîne « The » n’apparaît pas parmi les résultats de ce premier appel. Par contre, elle est trouvée quand la méthode [Match](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) est appelée avec le paramètre options défini sur [IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase). 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\bthe\w*\b";
      string input = "The man then told them about that event.";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index);

      Console.WriteLine();
      foreach (Match match in Regex.Matches(input, pattern, 
                                            RegexOptions.IgnoreCase))
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found then at index 8.
//       Found them at index 18.
//       
//       Found The at index 0.
//       Found then at index 8.
//       Found them at index 18.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\bthe\w*\b"
      Dim input As String = "The man then told them about that event."
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index)
      Next
      Console.WriteLine()
      For Each match As Match In Regex.Matches(input, pattern, _
                                               RegexOptions.IgnoreCase)
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       Found then at index 8.
'       Found them at index 18.
'       
'       Found The at index 0.
'       Found then at index 8.
'       Found them at index 18.
```

L’exemple suivant modifie le modèle d’expression régulière proposé dans l’exemple précédent de manière à utiliser des options inline au lieu du paramètre *options* pour effectuer une comparaison sans respect de la casse. Le premier modèle définit l’option de non-respect de la casse dans une construction de regroupement qui s’applique uniquement à la lettre « t » de la chaîne « the ». Comme la construction de l’option intervient au début du modèle, le second modèle applique l’option de non-respect de la casse à l’expression régulière entière.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(?i:t)he\w*\b";
      string input = "The man then told them about that event.";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index);

      Console.WriteLine();
      pattern = @"(?i)\bthe\w*\b";
      foreach (Match match in Regex.Matches(input, pattern, 
                                            RegexOptions.IgnoreCase))
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found The at index 0.
//       Found then at index 8.
//       Found them at index 18.
//       
//       Found The at index 0.
//       Found then at index 8.
//       Found them at index 18.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(?i:t)he\w*\b"
      Dim input As String = "The man then told them about that event."
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index)
      Next
      Console.WriteLine()
      pattern = "(?i)\bthe\w*\b"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       Found The at index 0.
'       Found then at index 8.
'       Found them at index 18.
'       
'       Found The at index 0.
'       Found then at index 8.
'       Found them at index 18.
```

## <a name="multiline-mode"></a>Mode multiligne

L’option [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline), ou l’option inline **m**, permet au moteur d’expression régulière de gérer une chaîne d’entrée constituée de plusieurs lignes. Elle modifie l’interprétation des éléments de langage **^** et **$** de manière à ce qu’ils correspondent au début et à la fin d’une ligne, et non au début et à la fin de la chaîne d’entrée. 

Par défaut, **$** correspond uniquement à la fin de la chaîne d’entrée. Si vous spécifiez l’option [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline), elle correspond au caractère de saut de ligne**(\n)** ou à la fin de la chaîne d’entrée. Toutefois, elle ne correspond pas à la combinaison de caractères retour chariot/saut de ligne. Pour les mettre en correspondance, utilisez la sous-expression **\r?$** au lieu de simplement **$**. 

L’exemple suivant extrait les prénoms et scores des lanceurs, puis les ajoute à une collection [SortedList&lt;TKey, TValue&gt;](xref:System.Collections.Generic.SortedList%602) qui les trie dans l’ordre décroissant. La méthode [Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) est appelée deux fois. Dans le premier appel de la méthode, l'expression régulière est `^(\w+)\s(\d+)$` et aucune option n'est définie. Comme le montre la sortie, aucune correspondance n’est trouvée, car le moteur d’expression régulière ne peut pas mettre en correspondance le modèle d’entrée avec le début et la fin de la chaîne d’entrée. Dans le second appel de la méthode, l’expression régulière devient `^(\w+)\s(\d+)\r?$` et les options sont définies sur [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline). Comme le montre la sortie, les noms et scores sont correctement mis en correspondance, et les scores apparaissent dans l'ordre décroissant.

```csharp
using System;
using System.Collections.Generic;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      SortedList<int, string> scores = new SortedList<int, string>(new DescendingComparer<int>());

      string input = "Joe 164\n" + 
                     "Sam 208\n" + 
                     "Allison 211\n" + 
                     "Gwen 171\n"; 
      string pattern = @"^(\w+)\s(\d+)$";
      bool matched = false;

      Console.WriteLine("Without Multiline option:");
      foreach (Match match in Regex.Matches(input, pattern))
      {
         scores.Add(Int32.Parse(match.Groups[2].Value), (string) match.Groups[1].Value);
         matched = true;
      }
      if (! matched)
         Console.WriteLine("   No matches.");
      Console.WriteLine();

      // Redefine pattern to handle multiple lines.
      pattern = @"^(\w+)\s(\d+)\r*$";
      Console.WriteLine("With multiline option:");
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.Multiline))
         scores.Add(Int32.Parse(match.Groups[2].Value), (string) match.Groups[1].Value);

      // List scores in descending order. 
      foreach (KeyValuePair<int, string> score in scores)
         Console.WriteLine("{0}: {1}", score.Value, score.Key);
   }
}

public class DescendingComparer<T> : IComparer<T>
{
   public int Compare(T x, T y)
   {
      return Comparer<T>.Default.Compare(x, y) * -1;       
   }
}
// The example displays the following output:
//   Without Multiline option:
//      No matches.
//   
//   With multiline option:
//   Allison: 211
//   Sam: 208
//   Gwen: 171
//   Joe: 164
```

```vb
Imports System.Collections.Generic
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim scores As New SortedList(Of Integer, String)(New DescendingComparer(Of Integer)())

      Dim input As String = "Joe 164" + vbCrLf + _
                            "Sam 208" + vbCrLf + _
                            "Allison 211" + vbCrLf + _
                            "Gwen 171" + vbCrLf
      Dim pattern As String = "^(\w+)\s(\d+)$"
      Dim matched As Boolean = False

      Console.WriteLine("Without Multiline option:")
      For Each match As Match In Regex.Matches(input, pattern)
         scores.Add(CInt(match.Groups(2).Value), match.Groups(1).Value)
         matched = True
      Next
      If Not matched Then Console.WriteLine("   No matches.")
      Console.WriteLine()

      ' Redefine pattern to handle multiple lines.
      pattern = "^(\w+)\s(\d+)\r*$"
      Console.WriteLine("With multiline option:")
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.Multiline)
         scores.Add(CInt(match.Groups(2).Value), match.Groups(1).Value)
      Next
      ' List scores in descending order. 
      For Each score As KeyValuePair(Of Integer, String) In scores
         Console.WriteLine("{0}: {1}", score.Value, score.Key)
      Next
   End Sub
End Module

Public Class DescendingComparer(Of T) : Implements IComparer(Of T)
   Public Function Compare(x As T, y As T) As Integer _
          Implements IComparer(Of T).Compare
      Return Comparer(Of T).Default.Compare(x, y) * -1       
   End Function
End Class
' The example displays the following output:
'    Without Multiline option:
'       No matches.
'    
'    With multiline option:
'    Allison: 211
'    Sam: 208
'    Gwen: 171
'    Joe: 164
```

Le modèle d'expression régulière `^(\w+)\s(\d+)\r*$` est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`^` | Commencer au début de la ligne.
`(\w+)` | Mettre en correspondance un ou plusieurs caractères alphabétiques. Il s'agit du premier groupe de capture.
`\s` | Mettre en correspondance un espace blanc.
`(\d+)` | Mettre en correspondance un ou plusieurs chiffres décimaux. Il s'agit du deuxième groupe de capture.
`\r?` | Mettre en correspondance zéro ou un caractère de retour chariot.
`$` | Terminer à la fin de la ligne.
 
L’exemple suivant est équivalent à l’exemple précédent, à la différence qu’il utilise l’option inline **(?m)** pour définir l’option multiligne.

```csharp
using System;
using System.Collections.Generic;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      SortedList<int, string> scores = new SortedList<int, string>(new DescendingComparer<int>());

      string input = "Joe 164\n" +  
                     "Sam 208\n" +  
                     "Allison 211\n" +  
                     "Gwen 171\n"; 
      string pattern = @"(?m)^(\w+)\s(\d+)\r*$";

      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.Multiline))
         scores.Add(Convert.ToInt32(match.Groups[2].Value), match.Groups[1].Value);

      // List scores in descending order. 
      foreach (KeyValuePair<int, string> score in scores)
         Console.WriteLine("{0}: {1}", score.Value, score.Key);
   }
}

public class DescendingComparer<T> : IComparer<T>
{
   public int Compare(T x, T y) 
   {
      return Comparer<T>.Default.Compare(x, y) * -1;       
   }
}
// The example displays the following output:
//    Allison: 211
//    Sam: 208
//    Gwen: 171
//    Joe: 164
```

```vb
Imports System.Collections.Generic
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim scores As New SortedList(Of Integer, String)(New DescendingComparer(Of Integer)())

      Dim input As String = "Joe 164" + vbCrLf + _
                            "Sam 208" + vbCrLf + _
                            "Allison 211" + vbCrLf + _
                            "Gwen 171" + vbCrLf
      Dim pattern As String = "(?m)^(\w+)\s(\d+)\r*$"

      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.Multiline)
         scores.Add(CInt(match.Groups(2).Value), match.Groups(1).Value)
      Next
      ' List scores in descending order. 
      For Each score As KeyValuePair(Of Integer, String) In scores
         Console.WriteLine("{0}: {1}", score.Value, score.Key)
      Next
   End Sub
End Module

Public Class DescendingComparer(Of T) : Implements IComparer(Of T)
   Public Function Compare(x As T, y As T) As Integer _
          Implements IComparer(Of T).Compare
      Return Comparer(Of T).Default.Compare(x, y) * -1       
   End Function
End Class
' The example displays the following output:
'    Allison: 211
'    Sam: 208
'    Gwen: 171
'    Joe: 164
```

## <a name="single-line-mode"></a>Mode à ligne simple

L’option [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline), ou l’option inline s, indique au moteur d’expression régulière de traiter la chaîne d’entrée comme si elle était composée d’une seule ligne. Pour ce faire, elle modifie le comportement de l’élément de langage point (**.**) de manière à mettre en correspondance chaque caractère, y compris le caractère de saut de ligne **\n** ou \u000A.

L’exemple suivant montre comment l’utilisation de l’option [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) modifie le comportement de l’élément de langage .. L'expression régulière `^.+` commence au début de la chaîne et correspond à tous les caractères. Par défaut, la correspondance se termine à la fin de la première ligne ; le modèle d’expressions régulières correspond au retour chariot, **\r** ou \u000D, mais il ne correspond pas à **\n**. Étant donné que l’option [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) interprète la chaîne d’entrée entière comme une ligne unique, il correspond à chaque caractère de la chaîne d’entrée, notamment **\n**.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "^.+";
      string input = "This is one line and" + Environment.NewLine + "this is the second.";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(Regex.Escape(match.Value));

      Console.WriteLine();
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.Singleline))
         Console.WriteLine(Regex.Escape(match.Value));
   }
}
// The example displays the following output:
//       This\ is\ one\ line\ and\r
//       
//       This\ is\ one\ line\ and\r\nthis\ is\ the\ second\.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "^.+"
      Dim input As String = "This is one line and" + vbCrLf + "this is the second."
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(Regex.Escape(match.Value))
      Next
      Console.WriteLine()
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.SingleLine)
         Console.WriteLine(Regex.Escape(match.Value))
      Next
   End Sub
End Module
' The example displays the following output:
'       This\ is\ one\ line\ and\r
'       
'       This\ is\ one\ line\ and\r\nthis\ is\ the\ second\.
```

L’exemple suivant est équivalent à l’exemple précédent, à la différence qu’il utilise l’option inline **(?s)** pour activer le mode à ligne simple. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {      
      string pattern = "(?s)^.+";
      string input = "This is one line and" + Environment.NewLine + "this is the second.";

      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(Regex.Escape(match.Value));
   }
}
// The example displays the following output:
//       This\ is\ one\ line\ and\r\nthis\ is\ the\ second\.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(?s)^.+"
      Dim input As String = "This is one line and" + vbCrLf + "this is the second."

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(Regex.Escape(match.Value))
      Next
   End Sub
End Module
' The example displays the following output:
'       This\ is\ one\ line\ and\r\nthis\ is\ the\ second\.
```

## <a name="explicit-captures-only"></a>Captures explicites uniquement

Par défaut, les groupes de capture sont définis à l’aide de parenthèses dans le modèle d’expression régulière. Les groupes nommés se voient affecter un nom ou un nombre par l’option de langage **(?<**_nom_**>** _sous-expression_**)**, tandis que les groupes sans nom sont accessibles en fonction de leur index. Dans l’objet [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection), les groupes sans nom précèdent les groupes nommés. 

Les constructions de regroupement sont souvent utilisées pour simplement appliquer des quantificateurs à plusieurs éléments de langage, et les sous-chaînes capturées ne présentent aucun intérêt. Par exemple, si l'expression régulière suivante :

```
\b\(?((\w+),?\s?)+[\.!?]\)?
```

est uniquement destinée à extraire d’un document les phrases qui se terminent par un point, un point d’exclamation ou un point d’interrogation, seule la phrase résultante (représentée par l’objet [Match](xref:System.Text.RegularExpressions.Match)) présente un intérêt. Les différents mots de la collection n’en présentent pas. 

Les groupes de capture qui ne sont pas utilisés par la suite peuvent affecter les performances, car le moteur d’expression régulière doit remplir les deux objets de collection [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) et [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection). En guise de solution, vous pouvez utiliser l’option [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) ou l’option inline **n** pour indiquer que les seules captures valides sont les groupes explicitement nommés ou numérotés désignés par la construction **(?<**_nom_**>** _sous-expression_**)**. 

L’exemple suivant affiche des informations sur les correspondances retournées par le modèle d’expression régulière `\b\(?((\w+),?\s?)+[\.!?]\)?` quand la méthode [Match](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.Int32)) est appelée avec et sans l’option [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture). Comme le montre la sortie du premier appel de la méthode, le moteur d’expression régulière remplit entièrement les objets de collection [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) et [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) avec des informations relatives aux sous-chaînes capturées. Comme la seconde méthode est appelée avec options défini sur [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture), elle ne capture pas d’information sur les groupes.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"\b\(?((?>\w+),?\s?)+[\.!?]\)?";
      Console.WriteLine("With implicit captures:");
      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine("The match: {0}", match.Value);
         int groupCtr = 0;
         foreach (Group group in match.Groups)
         {
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value);
            groupCtr++;
            int captureCtr = 0;
            foreach (Capture capture in group.Captures)
            {
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value);
               captureCtr++;
            }
         }
      }
      Console.WriteLine();
      Console.WriteLine("With explicit captures only:");
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.ExplicitCapture))
      {
         Console.WriteLine("The match: {0}", match.Value);
         int groupCtr = 0;
         foreach (Group group in match.Groups)
         {
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value);
            groupCtr++;
            int captureCtr = 0;
            foreach (Capture capture in group.Captures)
            {
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value);
               captureCtr++;
            }
         }
      }
   }
}
// The example displays the following output:
//    With implicit captures:
//    The match: This is the first sentence.
//       Group 0: This is the first sentence.
//          Capture 0: This is the first sentence.
//       Group 1: sentence
//          Capture 0: This
//          Capture 1: is
//          Capture 2: the
//          Capture 3: first
//          Capture 4: sentence
//       Group 2: sentence
//          Capture 0: This
//          Capture 1: is
//          Capture 2: the
//          Capture 3: first
//          Capture 4: sentence
//    The match: Is it the beginning of a literary masterpiece?
//       Group 0: Is it the beginning of a literary masterpiece?
//          Capture 0: Is it the beginning of a literary masterpiece?
//       Group 1: masterpiece
//          Capture 0: Is
//          Capture 1: it
//          Capture 2: the
//          Capture 3: beginning
//          Capture 4: of
//          Capture 5: a
//          Capture 6: literary
//          Capture 7: masterpiece
//       Group 2: masterpiece
//          Capture 0: Is
//          Capture 1: it
//          Capture 2: the
//          Capture 3: beginning
//          Capture 4: of
//          Capture 5: a
//          Capture 6: literary
//          Capture 7: masterpiece
//    The match: I think not.
//       Group 0: I think not.
//          Capture 0: I think not.
//       Group 1: not
//          Capture 0: I
//          Capture 1: think
//          Capture 2: not
//       Group 2: not
//          Capture 0: I
//          Capture 1: think
//          Capture 2: not
//    The match: Instead, it is a nonsensical paragraph.
//       Group 0: Instead, it is a nonsensical paragraph.
//          Capture 0: Instead, it is a nonsensical paragraph.
//       Group 1: paragraph
//          Capture 0: Instead,
//          Capture 1: it
//          Capture 2: is
//          Capture 3: a
//          Capture 4: nonsensical
//          Capture 5: paragraph
//       Group 2: paragraph
//          Capture 0: Instead
//          Capture 1: it
//          Capture 2: is
//          Capture 3: a
//          Capture 4: nonsensical
//          Capture 5: paragraph
//    
//    With explicit captures only:
//    The match: This is the first sentence.
//       Group 0: This is the first sentence.
//          Capture 0: This is the first sentence.
//    The match: Is it the beginning of a literary masterpiece?
//       Group 0: Is it the beginning of a literary masterpiece?
//          Capture 0: Is it the beginning of a literary masterpiece?
//    The match: I think not.
//       Group 0: I think not.
//          Capture 0: I think not.
//    The match: Instead, it is a nonsensical paragraph.
//       Group 0: Instead, it is a nonsensical paragraph.
//          Capture 0: Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "\b\(?((?>\w+),?\s?)+[\.!?]\)?"
      Console.WriteLine("With implicit captures:")
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("The match: {0}", match.Value)
         Dim groupCtr As Integer = 0
         For Each group As Group In match.Groups
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value)
            groupCtr += 1
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value)
               captureCtr += 1
            Next
         Next
      Next
      Console.WriteLine()
      Console.WriteLine("With explicit captures only:")
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.ExplicitCapture)
         Console.WriteLine("The match: {0}", match.Value)
         Dim groupCtr As Integer = 0
         For Each group As Group In match.Groups
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value)
            groupCtr += 1
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value)
               captureCtr += 1
            Next
         Next
      Next
   End Sub
End Module
' The example displays the following output:
'    With implicit captures:
'    The match: This is the first sentence.
'       Group 0: This is the first sentence.
'          Capture 0: This is the first sentence.
'       Group 1: sentence
'          Capture 0: This
'          Capture 1: is
'          Capture 2: the
'          Capture 3: first
'          Capture 4: sentence
'       Group 2: sentence
'          Capture 0: This
'          Capture 1: is
'          Capture 2: the
'          Capture 3: first
'          Capture 4: sentence
'    The match: Is it the beginning of a literary masterpiece?
'       Group 0: Is it the beginning of a literary masterpiece?
'          Capture 0: Is it the beginning of a literary masterpiece?
'       Group 1: masterpiece
'          Capture 0: Is
'          Capture 1: it
'          Capture 2: the
'          Capture 3: beginning
'          Capture 4: of
'          Capture 5: a
'          Capture 6: literary
'          Capture 7: masterpiece
'       Group 2: masterpiece
'          Capture 0: Is
'          Capture 1: it
'          Capture 2: the
'          Capture 3: beginning
'          Capture 4: of
'          Capture 5: a
'          Capture 6: literary
'          Capture 7: masterpiece
'    The match: I think not.
'       Group 0: I think not.
'          Capture 0: I think not.
'       Group 1: not
'          Capture 0: I
'          Capture 1: think
'          Capture 2: not
'       Group 2: not
'          Capture 0: I
'          Capture 1: think
'          Capture 2: not
'    The match: Instead, it is a nonsensical paragraph.
'       Group 0: Instead, it is a nonsensical paragraph.
'          Capture 0: Instead, it is a nonsensical paragraph.
'       Group 1: paragraph
'          Capture 0: Instead,
'          Capture 1: it
'          Capture 2: is
'          Capture 3: a
'          Capture 4: nonsensical
'          Capture 5: paragraph
'       Group 2: paragraph
'          Capture 0: Instead
'          Capture 1: it
'          Capture 2: is
'          Capture 3: a
'          Capture 4: nonsensical
'          Capture 5: paragraph
'    
'    With explicit captures only:
'    The match: This is the first sentence.
'       Group 0: This is the first sentence.
'          Capture 0: This is the first sentence.
'    The match: Is it the beginning of a literary masterpiece?
'       Group 0: Is it the beginning of a literary masterpiece?
'          Capture 0: Is it the beginning of a literary masterpiece?
'    The match: I think not.
'       Group 0: I think not.
'          Capture 0: I think not.
'    The match: Instead, it is a nonsensical paragraph.
'       Group 0: Instead, it is a nonsensical paragraph.
'          Capture 0: Instead, it is a nonsensical paragraph.
```

Le modèle d'expression régulière `\b\(?((?>\w+),?\s?)+[\.!?]\)?` est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`\b` | Commencer à la limite d'un mot.
`\(?` | Mettre en correspondance zéro occurrence, ou plus, de la parenthèse ouvrante (« ( »).
`(?>\w+),?` | Mettre en correspondance un ou plusieurs caractères alphabétiques, suivis de zéro virgule, ou plus. Ne pas effectuer de recherches rétroactives quand des caractères alphabétiques sont mis en correspondance.
`\s?` | Mettre en correspondance zéro ou des espaces blancs.
`((\w+),?\s?)+` | Mettre en correspondance la combinaison d'un ou plusieurs caractères alphabétiques, suivis de zéro ou d'une virgule, suivies de zéro ou d'un espace blanc, une ou plusieurs fois.
`[\.!?]\)?` | Mettre en correspondance n'importe lequel des trois symboles de ponctuation, suivi de zéro ou d'une parenthèse fermante (« ) »).
 
Vous pouvez également utiliser l’élément inline **(?n)** pour supprimer les captures automatiques. L’exemple suivant modifie le modèle d’expression régulière précédent pour utiliser l’élément inline **(?n)** au lieu de l’option [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture).

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"(?n)\b\(?((?>\w+),?\s?)+[\.!?]\)?";

      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine("The match: {0}", match.Value);
         int groupCtr = 0;
         foreach (Group group in match.Groups)
         {
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value);
            groupCtr++;
            int captureCtr = 0;
            foreach (Capture capture in group.Captures)
            {
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value);
               captureCtr++;
            }
         }
      }
   }
}
// The example displays the following output:
//       The match: This is the first sentence.
//          Group 0: This is the first sentence.
//             Capture 0: This is the first sentence.
//       The match: Is it the beginning of a literary masterpiece?
//          Group 0: Is it the beginning of a literary masterpiece?
//             Capture 0: Is it the beginning of a literary masterpiece?
//       The match: I think not.
//          Group 0: I think not.
//             Capture 0: I think not.
//       The match: Instead, it is a nonsensical paragraph.
//          Group 0: Instead, it is a nonsensical paragraph.
//             Capture 0: Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "(?n)\b\(?((?>\w+),?\s?)+[\.!?]\)?"

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("The match: {0}", match.Value)
         Dim groupCtr As Integer = 0
         For Each group As Group In match.Groups
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value)
            groupCtr += 1
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value)
               captureCtr += 1
            Next
         Next
      Next
   End Sub
End Module
' The example displays the following output:
'       The match: This is the first sentence.
'          Group 0: This is the first sentence.
'             Capture 0: This is the first sentence.
'       The match: Is it the beginning of a literary masterpiece?
'          Group 0: Is it the beginning of a literary masterpiece?
'             Capture 0: Is it the beginning of a literary masterpiece?
'       The match: I think not.
'          Group 0: I think not.
'             Capture 0: I think not.
'       The match: Instead, it is a nonsensical paragraph.
'          Group 0: Instead, it is a nonsensical paragraph.
'             Capture 0: Instead, it is a nonsensical paragraph.
```

Enfin, vous pouvez utiliser l’élément de groupe inline **(?n:)** pour supprimer les captures automatiques groupe par groupe. L'exemple suivant modifie le modèle précédent pour supprimer les captures sans nom du groupe externe, `((?>\w+),?\s?)`. Notez que cette opération supprime également les captures sans nom du groupe interne.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"\b\(?(?n:(?>\w+),?\s?)+[\.!?]\)?";

      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine("The match: {0}", match.Value);
         int groupCtr = 0;
         foreach (Group group in match.Groups)
         {
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value);
            groupCtr++;
            int captureCtr = 0;
            foreach (Capture capture in group.Captures)
            {
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value);
               captureCtr++;
            }
         }
      }
   }
}
// The example displays the following output:
//       The match: This is the first sentence.
//          Group 0: This is the first sentence.
//             Capture 0: This is the first sentence.
//       The match: Is it the beginning of a literary masterpiece?
//          Group 0: Is it the beginning of a literary masterpiece?
//             Capture 0: Is it the beginning of a literary masterpiece?
//       The match: I think not.
//          Group 0: I think not.
//             Capture 0: I think not.
//       The match: Instead, it is a nonsensical paragraph.
//          Group 0: Instead, it is a nonsensical paragraph.
//             Capture 0: Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "\b\(?(?n:(?>\w+),?\s?)+[\.!?]\)?"

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("The match: {0}", match.Value)
         Dim groupCtr As Integer = 0
         For Each group As Group In match.Groups
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value)
            groupCtr += 1
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value)
               captureCtr += 1
            Next
         Next
      Next
   End Sub
End Module
' The example displays the following output:
'       The match: This is the first sentence.
'          Group 0: This is the first sentence.
'             Capture 0: This is the first sentence.
'       The match: Is it the beginning of a literary masterpiece?
'          Group 0: Is it the beginning of a literary masterpiece?
'             Capture 0: Is it the beginning of a literary masterpiece?
'       The match: I think not.
'          Group 0: I think not.
'             Capture 0: I think not.
'       The match: Instead, it is a nonsensical paragraph.
'          Group 0: Instead, it is a nonsensical paragraph.
'             Capture 0: Instead, it is a nonsensical paragraph.
```

## <a name="compiled-regular-expressions"></a>Expressions régulières compilées

Par défaut, les expressions régulières dans .NET sont interprétées. Quand un objet [Regex](xref:System.Text.RegularExpressions.Regex) est instancié ou qu’une méthode [Regex](xref:System.Text.RegularExpressions.Regex) statique est appelée, le modèle d’expression régulière est analysé de manière à générer un ensemble d’opcodes personnalisés, puis un interpréteur utilise ces opcodes pour exécuter l’expression régulière. Cela implique un compromis : le coût d'initialisation du moteur d'expression régulière est réduit au prix d'une baisse des performances au moment de l'exécution.

Vous pouvez utiliser des expressions régulières compilées à la place d’expressions régulières interprétées en utilisant l’option [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled). Dans ce cas, quand un modèle est transmis au moteur d’expression régulière, il est analysé de manière à générer un ensemble d’opcodes convertis ensuite en un code MSIL (Microsoft Intermediate Language), qui peut être directement communiqué au Common Language Runtime. Les expressions régulières compilées optimisent les performances d'exécution au détriment du temps d'initialisation.

> [!NOTE]
> Pour compiler une expression régulière, vous devez fournir la valeur [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) au paramètre options d’un constructeur de classe [Regex](xref:System.Text.RegularExpressions.Regex) ou d’une méthode de mise en correspondance de modèle statique. La compilation ne peut pas être effectuée via une option inline. 
 

Vous pouvez utiliser des expressions régulières compilées dans les appels d'expressions régulières statiques et d'instance. Dans les expressions régulières statiques, l’option [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) est transmise au paramètre options de la méthode de mise en correspondance de modèle d’expression régulière. Dans les expressions régulières d’instance, elle est transmise au paramètre options du constructeur de classe [Regex](xref:System.Text.RegularExpressions.Regex). Dans les deux cas, les performances s'en trouvent améliorées. 

Toutefois, cette amélioration ne se produit que dans les conditions suivantes :

* Un objet [Regex](xref:System.Text.RegularExpressions.Regex) qui représente une expression régulière particulière est utilisé dans plusieurs appels de méthodes de mise en correspondance de modèle d’expression régulière.

* La portée de l’objet [Regex](xref:System.Text.RegularExpressions.Regex) est strictement délimitée, ce qui permet sa réutilisation.

* Une expression régulière statique est utilisée dans plusieurs appels de méthodes de mise en correspondance de modèle d’expression régulière. (L'amélioration des performances est possible, car les expressions régulières utilisées dans les appels de méthode statique sont mises en cache par le moteur d'expression régulière.) 

## <a name="ignore-white-space"></a>Ignorer l’espace blanc

Par défaut, l’espace blanc dans un modèle d’expression régulière est significatif ; il oblige le moteur d’expression régulière à mettre en correspondance un espace blanc dans la chaîne d’entrée. Ainsi, les expressions régulières `"\b\w+\s"` et `"\b\w+ "` sont pratiquement équivalentes. En outre, quand le signe dièse (**#**) est rencontré dans un modèle d’expression régulière, il est interprété comme un caractère littéral à mettre en correspondance.

L’option [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace), ou l’option inline **x**, modifie ce comportement par défaut comme suit :

* L’espace blanc sans séquence d’échappement dans le modèle d’expression régulière est ignoré. Pour faire partie d’un modèle d’expression régulière, les espaces blancs doivent être inclus dans une séquence d’échappement (par exemple, « **\s** » ou « **\**  »).

* Le signe dièse (**#**) est interprété comme le début d’un commentaire, plutôt que comme un caractère littéral. Tout le texte d’un modèle d’expression régulière depuis le caractère **#** jusqu’à la fin de la chaîne est interprété comme un commentaire.

Toutefois, dans les cas suivants, les espaces blancs d’une expression régulière ne sont pas ignorés, même si vous utilisez l’option [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) : 

* L'espace blanc dans une classe de caractères est toujours interprété de façon littérale. Par exemple, le modèle d'expression régulière `[ .,;:]` met en correspondance n'importe quel espace blanc, point, virgule, point-virgule ou symbole deux-points unique. 

* L’espace blanc n’est pas autorisé dans un quantificateur entre accolades, comme **{**_n_**}**, **{**_n_**,}** et **{**_n_**,**_m_**}**. Par exemple, le modèle d’expression régulière **\d{1. 3}** ne peut pas mettre en correspondance les séquences d’un à trois chiffres, car il contient un espace blanc. 

* L'espace blanc n'est pas autorisé dans une séquence de caractères qui introduit un élément de langage. Exemple : 

    * L’élément de langage **(?:**_sous-expression_**)** représente un groupe sans capture, et la partie **(?:** de l’élément ne peut pas comporter d’espaces. Le modèle **(? :**_sous-expression_**)** lève une [ArgumentException](xref:System.ArgumentException) au moment de l’exécution, car le moteur d’expression régulière ne peut pas l’analyser, et le modèle **(? :**_sous-expression_**)** ne parvient pas à mettre en correspondance *sous-expression*.

    * L’élément de langage **\p{**_nom_**}**, qui représente une catégorie Unicode ou un bloc nommé, ne peut pas comporter d’espaces dans sa partie **\p{**. Si vous incluez un espace blanc, l’élément lève une [ArgumentException](xref:System.ArgumentException) au moment de l’exécution. 

L'activation de cette option permet de simplifier les expressions régulières qui sont souvent difficiles à analyser et à comprendre. Elle améliore la lisibilité et rend possible la documentation d'une expression régulière. 

L’exemple ci-après définit le modèle d’expression régulière suivant :

`\b \(? ( (?>\w+) ,?\s? )+ [\.!?] \)? # Matches an entire sentence`.

Ce modèle est similaire au modèle défini dans la section [Captures explicites uniquement](#explicit-captures-only), à la différence qu’il utilise l’option [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) pour ignorer l’espace blanc du modèle.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"\b\(?((?>\w+),?\s?)+[\.!?]\)?";

      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnorePatternWhitespace))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       This is the first sentence.
//       Is it the beginning of a literary masterpiece?
//       I think not.
//       Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence."

      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnorePatternWhitespace)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       This is the first sentence.
'       Is it the beginning of a literary masterpiece?
'       I think not.
'       Instead, it is a nonsensical paragraph.
```

L’exemple suivant utilise l’option inline **(?x)** pour ignorer l’espace blanc du modèle.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"(?x)\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.";

      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       This is the first sentence.
//       Is it the beginning of a literary masterpiece?
//       I think not.
//       Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "(?x)\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence."

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       This is the first sentence.
'       Is it the beginning of a literary masterpiece?
'       I think not.
'       Instead, it is a nonsensical paragraph.
```

## <a name="right-to-left-mode"></a>Mode de recherche de droite à gauche

Par défaut, le moteur d'expression régulière recherche de gauche à droite. Vous pouvez inverser le sens de la recherche à l’aide de l’option [RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft). La recherche commence automatiquement à la position du dernier caractère de la chaîne. Pour les méthodes de mise en correspondance de modèle qui comprennent un paramètre de position de début, comme [Regex.Match(String, Int32)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.Int32)), la position de début est l’index de la position du caractère le plus à droite à laquelle la recherche doit commencer. 

> [!NOTE]
> Pour utiliser le mode de recherche de droite à gauche, vous devez fournir la valeur [RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft) au paramètre options d’un constructeur de classe [Regex](xref:System.Text.RegularExpressions.Regex) ou d’une méthode de mise en correspondance de modèle statique. La compilation ne peut pas être effectuée via une option inline. 
 

L’option [RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft) modifie uniquement le sens de la recherche ; elle n’interprète pas le modèle d’expression régulière de droite à gauche. Par exemple, l'expression régulière `\bb\w+\s` met en correspondance les mots qui commencent par la lettre « b » et qui sont suivis d'un espace blanc. Dans l'exemple suivant, la chaîne d'entrée se compose de trois mots qui comprennent un ou plusieurs caractères « b ». Le premier mot commence par « b », le deuxième se termine par « b », tandis que le troisième comprend deux caractères « b » en son milieu. Comme le montre la sortie de l’exemple, seul le premier mot correspond au modèle d’expression régulière. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\bb\w+\s";
      string input = "builder rob rabble";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.RightToLeft))
         Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);     
   }
}
// The example displays the following output:
//       'builder ' found at position 0.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\bb\w+\s"
      Dim input As String = "builder rob rabble"
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.RightToLeft)
         Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)     
      Next
   End Sub
End Module
' The example displays the following output:
'       'builder ' found at position 0.
```

Notez également que l’assertion de préanalyse (l’élément de langage **(?**=_sous-expression_**)** et l’assertion de postanalyse (l’élément de langage **(?<**=_sous-expression_**)** ne changent pas le sens. Les assertions de préanalyse recherchent vers la droite, tandis que les assertions de postanalyse recherchent vers la gauche. Par exemple, l'expression régulière `(?<=\d{1,2}\s)\w+,?\s\d{4}` utilise l'assertion de postanalyse pour déterminer si une date précède le nom d'un mois. Ensuite, l'expression régulière met en correspondance le mois et l'année. Pour plus d’informations sur les assertions de préanalyse et de postanalyse, consultez [Constructions de regroupement dans les expressions régulières](grouping.md).

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "1 May 1917", "June 16, 2003" };
      string pattern = @"(?<=\d{1,2}\s)\w+,?\s\d{4}";

      foreach (string input in inputs)
      {
         Match match = Regex.Match(input, pattern, RegexOptions.RightToLeft);
         if (match.Success)
            Console.WriteLine("The date occurs in {0}.", match.Value);
         else
            Console.WriteLine("{0} does not match.", input);
      }
   }
}
// The example displays the following output:
//       The date occurs in May 1917.
//       June 16, 2003 does not match.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "1 May 1917", "June 16, 2003" }
      Dim pattern As String = "(?<=\d{1,2}\s)\w+,?\s\d{4}"

      For Each input As String In inputs
         Dim match As Match = Regex.Match(input, pattern, RegexOptions.RightToLeft)
         If match.Success Then
            Console.WriteLine("The date occurs in {0}.", match.Value)
         Else
            Console.WriteLine("{0} does not match.", input)
         End If
      Next
   End Sub
End Module
' The example displays the following output:
'       The date occurs in May 1917.
'       June 16, 2003 does not match.
```

Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`(?<=\d{1,2}\s)` | Le début de la correspondance doit être précédé d'un ou deux chiffres décimaux suivis d'un espace.
`\w+` | Mettre en correspondance un ou plusieurs caractères alphabétiques.
`,?` | Mettre en correspondance zéro ou une virgule.
`\s` | Mettre en correspondance un espace blanc.
`\d{4}` | Mettre en correspondance quatre chiffres décimaux.
 
## <a name="ecmascript-matching-behavior"></a>Comportement de correspondance ECMAScript

Par défaut, le moteur d’expression régulière utilise un comportement canonique pour appliquer un modèle d’expression régulière à un texte d’entrée. Toutefois, vous pouvez indiquer au moteur d’expression régulière d’utiliser un comportement de correspondance ECMAScript en spécifiant l’option [RegexOptions.ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript). 

> [!NOTE]
> À cette fin, vous devez fournir la valeur [RegexOptions.ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript) au paramètre options d’un constructeur de classe [Regex](xref:System.Text.RegularExpressions.Regex) ou d’une méthode de mise en correspondance de modèle statique. La compilation ne peut pas être effectuée via une option inline. 
 
L’option [RegexOptions.ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript) ne peut être combinée qu’aux options [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) et [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline). L’utilisation d’une autre option dans une expression régulière aboutit à une [ArgumentOutOfRangeException](xref:System.ArgumentOutOfRangeException).

Le comportement des expressions régulières ECMAScript et canoniques diffère dans trois domaines : la syntaxe de la classe de caractères, les groupes de capture avec référence circulaire et l’interprétation des séquences d’échappement octales ou des références arrière. 

* Syntaxe de la classe de caractères. Comme les expressions régulières canoniques prennent en charge Unicode, contrairement à ECMAScript, les classes de caractères dans ECMAScript possèdent une syntaxe plus limitée, et certains éléments de langage des classes de caractères ont une signification différente. Par exemple, ECMAScript ne prend pas en charge les éléments de langage tels que la catégorie Unicode ou les éléments de bloc *\p* et **\P**. De même, l’élément **\w**, qui correspond à un caractère alphabétique, est équivalent à la classe de caractères **[a-zA-Z_0-9]**, dans le cas de l’utilisation d’ECMAScript, et à **[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]**, dans le cas de l’utilisation du comportement canonique. Pour plus d’informations, consultez [Classes de caractères dans les expressions régulières](classes.md).

  L’exemple suivant illustre la différence entre les mises en correspondance de modèle canonique et ECMAScript. Il définit une expression régulière, `\b(\w+\s*)+`, qui met en correspondance les mots suivis d'espaces blancs. L'entrée se compose de deux chaînes ; l'une d'elles utilise le jeu de caractères latin, l'autre le jeu de caractères cyrillique. Comme le montre la sortie, l’appel de méthode [Regex.IsMatch(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) qui utilise la correspondance ECMAScript ne parvient pas à mettre en correspondance les mots cyrilliques, contrairement à l’appel de méthode qui utilise la correspondance canonique. 

  ```csharp
  using System;
  using System.Text.RegularExpressions;
  
  public class Example
  {
     public static void Main()
     {
        string[] values = { "целый мир", "the whole world" };
        string pattern = @"\b(\w+\s*)+";
        foreach (var value in values)
        {
           Console.Write("Canonical matching: ");
           if (Regex.IsMatch(value, pattern))
              Console.WriteLine("'{0}' matches the pattern.", value);
           else
              Console.WriteLine("{0} does not match the pattern.", value);
  
           Console.Write("ECMAScript matching: ");
           if (Regex.IsMatch(value, pattern, RegexOptions.ECMAScript))
              Console.WriteLine("'{0}' matches the pattern.", value);
           else
              Console.WriteLine("{0} does not match the pattern.", value);
           Console.WriteLine();
        }
     }
  }
  // The example displays the following output:
  //       Canonical matching: 'целый мир' matches the pattern.
  //       ECMAScript matching: целый мир does not match the pattern.
  //       
  //       Canonical matching: 'the whole world' matches the pattern.
  //       ECMAScript matching: 'the whole world' matches the pattern.
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim values() As String = { "целый мир", "the whole world" }
        Dim pattern As String = "\b(\w+\s*)+"
        For Each value In values
           Console.Write("Canonical matching: ")
           If Regex.IsMatch(value, pattern)
              Console.WriteLine("'{0}' matches the pattern.", value)
           Else
              Console.WriteLine("{0} does not match the pattern.", value)
           End If

           Console.Write("ECMAScript matching: ")
           If Regex.IsMatch(value, pattern, RegexOptions.ECMAScript)
              Console.WriteLine("'{0}' matches the pattern.", value)
           Else
              Console.WriteLine("{0} does not match the pattern.", value)
           End If
           Console.WriteLine()
        Next
     End Sub
  End Module
  ' The example displays the following output:
  '       Canonical matching: 'целый мир' matches the pattern.
  '       ECMAScript matching: целый мир does not match the pattern.
  '       
  '       Canonical matching: 'the whole world' matches the pattern.
  '       ECMAScript matching: 'the whole world' matches the pattern.
  ```

* Groupes de capture avec référence circulaire. Une classe de capture d'expression régulière avec une référence arrière à elle-même doit être mise à jour à chaque itération de capture. Comme le montre l'exemple suivant, cette fonctionnalité permet à l'expression régulière `((a+)(\1) ?)+` de mettre en correspondance la chaîne d'entrée «  aa aaaa aaaaaa  » dans le cas de l'utilisation de la correspondance ECMAScript, mais pas dans le cas de l'utilisation de la correspondance canonique. 

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     static string pattern;
  
     public static void Main()
     {
        string input = "aa aaaa aaaaaa "; 
        pattern = @"((a+)(\1) ?)+";
  
        // Match input using canonical matching.
        AnalyzeMatch(Regex.Match(input, pattern));

        // Match input using ECMAScript.
        AnalyzeMatch(Regex.Match(input, pattern, RegexOptions.ECMAScript));
     }   

     private static void AnalyzeMatch(Match m)
     {
        if (m.Success)
        {
           Console.WriteLine("'{0}' matches {1} at position {2}.",  
                             pattern, m.Value, m.Index);
           int grpCtr = 0;
           foreach (Group grp in m.Groups)
           {
              Console.WriteLine("   {0}: '{1}'", grpCtr, grp.Value);
              grpCtr++;
              int capCtr = 0;
              foreach (Capture cap in grp.Captures)
              {
                 Console.WriteLine("      {0}: '{1}'", capCtr, cap.Value);
                 capCtr++;
              }
           }
        }
        else
        {
           Console.WriteLine("No match found.");
        }   
        Console.WriteLine();
     }
  }
  // The example displays the following output:
  //    No match found.
  //    
  //    '((a+)(\1) ?)+' matches aa aaaa aaaaaa  at position 0.
  //       0: 'aa aaaa aaaaaa '
  //          0: 'aa aaaa aaaaaa '
  //       1: 'aaaaaa '
  //          0: 'aa '
  //          1: 'aaaa '
  //          2: 'aaaaaa '
  //       2: 'aa'
  //          0: 'aa'
  //          1: 'aa'
  //          2: 'aa'
  //       3: 'aaaa '
  //          0: ''
  //          1: 'aa '
  //          2: 'aaaa '
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Dim pattern As String

     Public Sub Main()
        Dim input As String = "aa aaaa aaaaaa " 
        pattern = "((a+)(\1) ?)+"
  
        ' Match input using canonical matching.
        AnalyzeMatch(Regex.Match(input, pattern))

        ' Match input using ECMAScript.
        AnalyzeMatch(Regex.Match(input, pattern, RegexOptions.ECMAScript))
     End Sub   

     Private Sub AnalyzeMatch(m As Match)
        If m.Success
           Console.WriteLine("'{0}' matches {1} at position {2}.", _ 
                             pattern, m.Value, m.Index)
           Dim grpCtr As Integer = 0
           For Each grp As Group In m.Groups
              Console.WriteLine("   {0}: '{1}'", grpCtr, grp.Value)
              grpCtr += 1
              Dim capCtr As Integer = 0
              For Each cap As Capture In grp.Captures
                 Console.WriteLine("      {0}: '{1}'", capCtr, cap.Value)
                 capCtr += 1
              Next
           Next
        Else
           Console.WriteLine("No match found.")
        End If   
        Console.WriteLine()
     End Sub
  End Module
  ' The example displays the following output:
  '    No match found.
  '    
  '    '((a+)(\1) ?)+' matches aa aaaa aaaaaa  at position 0.
  '       0: 'aa aaaa aaaaaa '
  '          0: 'aa aaaa aaaaaa '
  '       1: 'aaaaaa '
  '          0: 'aa '
  '          1: 'aaaa '  
  '          2: 'aaaaaa '
  '       2: 'aa'
  '          0: 'aa'
  '          1: 'aa'
  '          2: 'aa'
  '       3: 'aaaa '
  '          0: ''
  '          1: 'aa '
  '          2: 'aaaa '
  ``

  The regular expression is defined as shown in the following table.

Pattern | Description
------- | ----------- 
`(a+)` | Match the letter "a" one or more times. This is the second capturing group.
`(\1)` | Match the substring captured by the first capturing group. This is the third capturing group.
`?` | Match zero or one space characters.
`((a+)(\1) ?)+` | Match the pattern of one or more "a" characters followed by a string that matches the first capturing group followed by zero or one space characters one or more times. This is the first capturing group.
  
* Resolution of ambiguities between octal escapes and backreferences. The following table summarizes the differences in octal versus backreference interpretation by canonical and ECMAScript regular expressions.

Regular expression | Canonical behavior | ECMAScript behavior
------------------ | ------------------ | ------------------- 
`\0` followed by 0 to 2 octal digits | Interpret as an octal. For example, `\044` is always interpreted as an octal value and means "**$**". | Same behavior.
**\** followed by a digit from 1 to 9, followed by no additional decimal digits | Interpret as a backreference. For example, \9 always means backreference 9, even if a ninth capturing group does not exist. If the capturing group does not exist, the regular expression parser throws an [ArgumentException](xref:System.ArgumentException). | If a single decimal digit capturing group exists, backreference to that digit. Otherwise, interpret the value as a literal.
**\** followed by a digit from 1 to 9, followed by additional decimal digits | Interpret the digits as a decimal value. If that capturing group exists, interpret the expression as a backreference. Otherwise, interpret the leading octal digits up to octal 377; that is, consider only the low 8 bits of the value. Interpret the remaining digits as literals. For example, in the expression `\3000`, if capturing group 300 exists, interpret as backreference 300; if capturing group 300 does not exist, interpret as octal 300 followed by 0. | Interpret as a backreference by converting as many digits as possible to a decimal value that can refer to a capture. If no digits can be converted, interpret as an octal by using the leading octal digits up to octal 377; interpret the remaining digits as literals.
 
## Comparison using the invariant culture

By default, when the regular expression engine performs case-insensitive comparisons, it uses the casing conventions of the current culture to determine equivalent uppercase and lowercase characters. 

However, this behavior is undesirable for some types of comparisons, particularly when comparing user input to the names of system resources, such as passwords, files, or URLs. The following example illustrates such as scenario. The code is intended to block access to any resource whose URL is prefaced with **FILE://**. The regular expression attempts a case-insensitive match with the string by using the regular expression `$FILE://`. However, when the current system culture is tr-TR (Turkish-Turkey), "I" is not the uppercase equivalent of "i". As a result, the call to the [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) method returns `false`, and access to the file is allowed. 

```csharp
CultureInfo defaultCulture = Thread.CurrentThread.CurrentCulture;
Thread.CurrentThread.CurrentCulture = new CultureInfo("tr-TR");

string input = "file://c:/Documents.MyReport.doc";
string pattern = "FILE://";

Console.WriteLine("Culture-sensitive matching ({0} culture)...", 
                  Thread.CurrentThread.CurrentCulture.Name);
if (Regex.IsMatch(input, pattern, RegexOptions.IgnoreCase))
   Console.WriteLine("URLs that access files are not allowed.");      
else
   Console.WriteLine("Access to {0} is allowed.", input);

Thread.CurrentThread.CurrentCulture = defaultCulture;
// The example displays the following output:
//       Culture-sensitive matching (tr-TR culture)...
//       Access to file://c:/Documents.MyReport.doc is allowed.
```

```vb
Dim defaultCulture As CultureInfo = Thread.CurrentThread.CurrentCulture
Thread.CurrentThread.CurrentCulture = New CultureInfo("tr-TR")

Dim input As String = "file://c:/Documents.MyReport.doc"
Dim pattern As String = "$FILE://"

Console.WriteLine("Culture-sensitive matching ({0} culture)...", _
                  Thread.CurrentThread.CurrentCulture.Name)
If Regex.IsMatch(input, pattern, RegexOptions.IgnoreCase) Then
   Console.WriteLine("URLs that access files are not allowed.")      
Else
   Console.WriteLine("Access to {0} is allowed.", input)
End If

Thread.CurrentThread.CurrentCulture = defaultCulture
' The example displays the following output:
'       Culture-sensitive matching (tr-TR culture)...
'       Access to file://c:/Documents.MyReport.doc is allowed.
```

> [!NOTE]
>   Pour plus d’informations sur les comparaisons de chaînes respectant la casse et utilisant la culture dite indifférente, consultez [Bonnes pratiques pour l’utilisation de chaînes](best-practices.md).
 
Au lieu d’utiliser les comparaisons sans respect de la casse de la culture actuelle, vous pouvez spécifier l’option [RegexOptions.CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant) pour ignorer les différences culturelles propres à la langue et pour utiliser les conventions de la culture dite indifférente.

> [!NOTE]
> Pour effectuer une comparaison en utilisant la culture dite indifférente, vous devez fournir la valeur [RegexOptions.CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant) au paramètre options d’un constructeur de classe [Regex](xref:System.Text.RegularExpressions.Regex) ou d’une méthode de mise en correspondance de modèle statique. La compilation ne peut pas être effectuée via une option inline. 
 
L’exemple suivant est identique à l’exemple précédent, à la différence que la méthode [Regex.IsMatch(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) statique est appelée avec des options qui incluent [RegexOptions.CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant). Même si la culture actuelle est définie sur Turc (Turquie), le moteur d'expression régulière parvient à mettre en correspondance « FILE » et « file » et à bloquer l'accès à la ressource de fichier. 

```csharp
CultureInfo defaultCulture = Thread.CurrentThread.CurrentCulture;
Thread.CurrentThread.CurrentCulture = new CultureInfo("tr-TR");

string input = "file://c:/Documents.MyReport.doc";
string pattern = "FILE://";

Console.WriteLine("Culture-insensitive matching...");
if (Regex.IsMatch(input, pattern, 
                  RegexOptions.IgnoreCase | RegexOptions.CultureInvariant)) 
   Console.WriteLine("URLs that access files are not allowed.");
else
   Console.WriteLine("Access to {0} is allowed.", input);

Thread.CurrentThread.CurrentCulture = defaultCulture;
// The example displays the following output:
//       Culture-insensitive matching...
//       URLs that access files are not allowed.
```

```vb
Dim defaultCulture As CultureInfo = Thread.CurrentThread.CurrentCulture
Thread.CurrentThread.CurrentCulture = New CultureInfo("tr-TR")

Dim input As String = "file://c:/Documents.MyReport.doc"
Dim pattern As String = "$FILE://"

Console.WriteLine("Culture-insensitive matching...")
If Regex.IsMatch(input, pattern, _
               RegexOptions.IgnoreCase Or RegexOptions.CultureInvariant) Then
   Console.WriteLine("URLs that access files are not allowed.")      
Else
   Console.WriteLine("Access to {0} is allowed.", input)
End If
Thread.CurrentThread.CurrentCulture = defaultCulture
' The example displays the following output:
'        Culture-insensitive matching...
'        URLs that access files are not allowed.
```

## <a name="see-also"></a>Voir aussi

[Langage des expressions régulières - Aide-mémoire](quick-ref.md)




<!--HONumber=Nov16_HO3-->


