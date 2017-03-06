---
title: "Ancres dans les expressions régulières"
description: "Ancres dans les expressions régulières"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 96dff1be-3005-4ba5-af1b-323182a26085
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 53345ba6ffda09a21cf4c626124797a3818aa504
ms.lasthandoff: 03/02/2017

---

# <a name="anchors-in-regular-expressions"></a>Ancres dans les expressions régulières

Les ancres, ou assertions atomiques de largeur nulle, spécifient une position dans la chaîne où une correspondance doit se produire. Quand vous utilisez une ancre dans votre expression de recherche, le moteur des expressions régulières n'avance pas dans la chaîne ou ne consomme pas de caractères ; il recherche uniquement une correspondance à la position spécifiée. Par exemple, **^** spécifie que la correspondance doit commencer au début d’une ligne ou d’une chaîne. Par conséquent, l'expression régulière `^http:` correspond uniquement à « http: » quand elle se produit au début d'une ligne. Le tableau suivant répertorie les ancres prises en charge par les expressions régulières dans .NET. 

Ancre | Description
------ | ----------- 
**^** | La correspondance doit se produire au début de la chaîne ou de la ligne.
**$** | La correspondance doit se produire à la fin de la chaîne ou de la ligne ou avant \n à la fin de la chaîne ou de la ligne.
**\A** | La correspondance doit se produire au début de la chaîne uniquement (aucun support multiligne).
**\Z** | La correspondance doit se produire à la fin de la chaîne ou avant \n à la fin de la chaîne.
**\z** | La correspondance doit se produire uniquement à la fin de la chaîne. 
**\G** | La correspondance doit démarrer à la position où la correspondance précédente s'est terminée.
**\b** | La correspondance doit se produire à la limite d'un mot.
**\B** | La correspondance ne doit pas se produire à la limite d'un mot.
 
## <a name="start-of-string-or-line-"></a>Début de chaîne ou de ligne : ^

L’ancre **^** spécifie que le modèle suivant doit commencer à la position du premier caractère de la chaîne. Si vous utilisez **^** avec l’option [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) (consultez [Options des expressions régulières](options.md)), la correspondance doit se trouver au début de chaque ligne.

L’exemple suivant utilise l’ancre **^** dans une expression régulière qui extrait des informations à propos des années pendant lesquelles certaines équipes de baseball professionnelles ont existé. L'exemple appelle deux surcharges de la méthode `Regex.Matches` : 

* L’appel à la surcharge [Matches(String, String)](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String)) recherche uniquement la première sous-chaîne dans la chaîne d’entrée qui correspond au modèle d’expression régulière. 

* L’appel à la surcharge [Matches(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) avec le paramètre options défini sur [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) recherche les cinq sous-chaînes.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      int startPos = 0, endPos = 70;
      string input = "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957\n" +
                     "Chicago Cubs, National League, 1903-present\n" + 
                     "Detroit Tigers, American League, 1901-present\n" + 
                     "New York Giants, National League, 1885-1957\n" +  
                     "Washington Senators, American League, 1901-1960\n";   
      string pattern = @"^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+";
      Match match;

      if (input.Substring(startPos, endPos).Contains(",")) {
         match = Regex.Match(input, pattern);
         while (match.Success) {
            Console.Write("The {0} played in the {1} in", 
                              match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);

            Console.WriteLine(".");
            startPos = match.Index + match.Length;
            endPos = startPos + 70 <= input.Length ? 70 : input.Length - startPos;
            if (! input.Substring(startPos, endPos).Contains(",")) break;
            match = match.NextMatch();
         }
         Console.WriteLine();
      }

      if (input.Substring(startPos, endPos).Contains(",")) {
         match = Regex.Match(input, pattern, RegexOptions.Multiline);
         while (match.Success) {
            Console.Write("The {0} played in the {1} in", 
                              match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);

            Console.WriteLine(".");
            startPos = match.Index + match.Length;
            endPos = startPos + 70 <= input.Length ? 70 : input.Length - startPos;
            if (! input.Substring(startPos, endPos).Contains(",")) break;
            match = match.NextMatch();
         }
         Console.WriteLine();
      }
   }
}
// The example displays the following output:
//    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
//    
//    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
//    The Chicago Cubs played in the National League in 1903-present.
//    The Detroit Tigers played in the American League in 1901-present.
//    The New York Giants played in the National League in 1885-1957.
//    The Washington Senators played in the American League in 1901-1960.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim startPos As Integer = 0
      Dim endPos As Integer = 70
      Dim input As String = "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957" + vbCrLf + _
                            "Chicago Cubs, National League, 1903-present" + vbCrLf + _
                            "Detroit Tigers, American League, 1901-present" + vbCrLf + _
                            "New York Giants, National League, 1885-1957" + vbCrLf + _
                            "Washington Senators, American League, 1901-1960" + vbCrLf  

      Dim pattern As String = "^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+"
      Dim match As Match

      ' Provide minimal validation in the event the input is invalid.
      If input.Substring(startPos, endPos).Contains(",") Then
         match = Regex.Match(input, pattern)
         Do While match.Success
            Console.Write("The {0} played in the {1} in", _
                              match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
            startPos = match.Index + match.Length 
            endPos = CInt(IIf(startPos + 70 <= input.Length, 70, input.Length - startPos))
            If Not input.Substring(startPos, endPos).Contains(",") Then Exit Do
            match = match.NextMatch()            
         Loop
         Console.WriteLine()                               
      End If      

      startPos = 0
      endPos = 70
      If input.Substring(startPos, endPos).Contains(",") Then
         match = Regex.Match(input, pattern, RegexOptions.Multiline)
         Do While match.Success
            Console.Write("The {0} played in the {1} in", _
                              match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
            startPos = match.Index + match.Length 
            endPos = CInt(IIf(startPos + 70 <= input.Length, 70, input.Length - startPos))
            If Not input.Substring(startPos, endPos).Contains(",") Then Exit Do
            match = match.NextMatch()            
         Loop
         Console.WriteLine()                               
      End If      


'       For Each match As Match in Regex.Matches(input, pattern, RegexOptions.Multiline)
'          Console.Write("The {0} played in the {1} in", _
'                            match.Groups(1).Value, match.Groups(4).Value)
'          For Each capture As Capture In match.Groups(5).Captures
'             Console.Write(capture.Value)
'          Next
'          Console.WriteLine(".")
'       Next
   End Sub
End Module
' The example displays the following output:
'    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
'    
'    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
'    The Chicago Cubs played in the National League in 1903-present.
'    The Detroit Tigers played in the American League in 1901-present.
'    The New York Giants played in the National League in 1885-1957.
'    The Washington Senators played in the American League in 1901-1960.
```

Le modèle d'expression régulière `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`^` | Commencer la correspondance au début de la chaîne d'entrée (ou au début de la ligne si la méthode est appelée avec l'option `RegexOptions.Multiline`).
`((\w+(\s?)){2,}` | Mettre en correspondance un ou plusieurs caractères de mot suivis de zéro ou d'un espace précisément deux fois. Il s'agit du premier groupe de capture. Cette expression définit également un deuxième et un troisième groupe de capture : le deuxième se compose du mot capturé, et le troisième se compose des espaces capturés. 
`,\s` | Mettre en correspondance une virgule suivie d'un caractère d'espace blanc.
`(\w+\s\w+)` | Mettre en correspondance un ou plusieurs caractères de mot suivis d'un espace, suivi d'un ou plusieurs caractères de mot. Il s'agit du quatrième groupe de capture.
`,` | Mettre en correspondance une virgule.
`\s\d{4}` | Mettre en correspondance un espace suivi de quatre chiffres décimaux.
`(-(\d{4}`&#124;`present))?` |    Mettre en correspondance zéro ou une occurrence d'un trait d'union suivie de quatre chiffres décimaux ou de la chaîne « present ». Il s'agit du sixième groupe de capture. Il inclut également un septième groupe de capture. 
`,?` | Mettre en correspondance zéro ou une occurrence d'une virgule.
`(\s\d{4}(-(\d{4}`&#124;`present))?,?)+` | Mettre en correspondance une ou plusieurs occurrences des éléments suivants : un espace, quatre chiffres décimaux, zéro ou une occurrence d'un trait d'union suivie de quatre chiffres décimaux ou de la chaîne « present » et zéro ou une virgule. Il s'agit du cinquième groupe de capture.
 
## <a name="end-of-string-or-line-"></a>Fin de chaîne ou de ligne : $

L’ancre **$** spécifie que le modèle précédent doit se produire à la fin de la chaîne d’entrée ou avant \n en fin de chaîne d’entrée. 

Si vous utilisez **$** avec l’option [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline), la correspondance peut également se trouver à la fin d’une ligne. Notez que **$** correspond à **\n**, mais ne correspond pas à **\r\n** (combinaison de caractères de retour chariot et de saut de ligne ou CR/LF). Pour établir une correspondance avec la combinaison de caractères CR/LF, incluez **\r?$** dans le modèle d’expression régulière.

L’exemple suivant ajoute l’ancre **$** au modèle d’expression régulière utilisé dans l’exemple dans la section « Début de chaîne ou de ligne » précédente. En cas d’utilisation avec la chaîne d’entrée d’origine, qui inclut cinq lignes de texte, la méthode [Regex.Matches(String, String)](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String)) ne peut pas trouver de correspondance, parce que la fin de la première ligne ne correspond pas au modèle **$**. Quand la chaîne d'entrée d'origine est fractionnée dans un tableau de chaînes, la méthode `Regex.Matches(String, String)` réussit à faire correspondre chacune des cinq lignes. Quand la méthode [Regex.Matches(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) est appelée avec le paramètre *options* ayant la valeur `RegexOptions.Multiline`, aucune correspondance n’est trouvée parce que le modèle d’expression régulière ne représente pas l’élément de retour chariot (\u+000D). Toutefois, quand le modèle d’expression régulière est modifié par le remplacement de **$** par **\r?$**, l’appel de la méthode `Regex.Matches(String, String, RegexOptions)` avec le paramètre *options* ayant la valeur `RegexOptions.Multiline` trouve encore cinq correspondances.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      int startPos = 0, endPos = 70;
      string cr = Environment.NewLine;
      string input = "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957" + cr +
                     "Chicago Cubs, National League, 1903-present" + cr + 
                     "Detroit Tigers, American League, 1901-present" + cr + 
                     "New York Giants, National League, 1885-1957" + cr +  
                     "Washington Senators, American League, 1901-1960" + cr;   
      Match match;

      string basePattern = @"^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+";
      string pattern = basePattern + "$";
      Console.WriteLine("Attempting to match the entire input string:");
      if (input.Substring(startPos, endPos).Contains(",")) {
         match = Regex.Match(input, pattern);
         while (match.Success) {
            Console.Write("The {0} played in the {1} in", 
                              match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);

            Console.WriteLine(".");
            startPos = match.Index + match.Length;
            endPos = startPos + 70 <= input.Length ? 70 : input.Length - startPos;
            if (! input.Substring(startPos, endPos).Contains(",")) break;
            match = match.NextMatch();
         }
         Console.WriteLine();
      }

      string[] teams = input.Split(new String[] { cr }, StringSplitOptions.RemoveEmptyEntries);
      Console.WriteLine("Attempting to match each element in a string array:");
      foreach (string team in teams)
      {
         if (team.Length > 70) continue;

         match = Regex.Match(team, pattern);
         if (match.Success)
         {
            Console.Write("The {0} played in the {1} in", 
                          match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);
            Console.WriteLine(".");
         }
      }
      Console.WriteLine();

      startPos = 0;
      endPos = 70;
      Console.WriteLine("Attempting to match each line of an input string with '$':");
      if (input.Substring(startPos, endPos).Contains(",")) {
         match = Regex.Match(input, pattern, RegexOptions.Multiline);
         while (match.Success) {
            Console.Write("The {0} played in the {1} in", 
                              match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);

            Console.WriteLine(".");
            startPos = match.Index + match.Length;
            endPos = startPos + 70 <= input.Length ? 70 : input.Length - startPos;
            if (! input.Substring(startPos, endPos).Contains(",")) break;
            match = match.NextMatch();
         }
         Console.WriteLine();
      }

      startPos = 0;
      endPos = 70;
      pattern = basePattern + "\r?$"; 
      Console.WriteLine(@"Attempting to match each line of an input string with '\r?$':");
      if (input.Substring(startPos, endPos).Contains(",")) {
         match = Regex.Match(input, pattern, RegexOptions.Multiline);
         while (match.Success) {
            Console.Write("The {0} played in the {1} in", 
                              match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);

            Console.WriteLine(".");
            startPos = match.Index + match.Length;
            endPos = startPos + 70 <= input.Length ? 70 : input.Length - startPos;
            if (! input.Substring(startPos, endPos).Contains(",")) break;
            match = match.NextMatch();
         }
         Console.WriteLine();
      }
   }
}
// The example displays the following output:
//    Attempting to match the entire input string:
//    
//    Attempting to match each element in a string array:
//    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
//    The Chicago Cubs played in the National League in 1903-present.
//    The Detroit Tigers played in the American League in 1901-present.
//    The New York Giants played in the National League in 1885-1957.
//    The Washington Senators played in the American League in 1901-1960.
//    
//    Attempting to match each line of an input string with '$':
//    
//    Attempting to match each line of an input string with '\r+$':
//    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
//    The Chicago Cubs played in the National League in 1903-present.
//    The Detroit Tigers played in the American League in 1901-present.
//    The New York Giants played in the National League in 1885-1957.
//    The Washington Senators played in the American League in 1901-1960.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim startPos As Integer = 0
      Dim endPos As Integer = 70
      Dim input As String = "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957" + vbCrLf + _
                            "Chicago Cubs, National League, 1903-present" + vbCrLf + _
                            "Detroit Tigers, American League, 1901-present" + vbCrLf + _
                            "New York Giants, National League, 1885-1957" + vbCrLf + _
                            "Washington Senators, American League, 1901-1960" + vbCrLf  

      Dim basePattern As String = "^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+"
      Dim match As Match

      Dim pattern As String = basePattern + "$"
      Console.WriteLine("Attempting to match the entire input string:")
      ' Provide minimal validation in the event the input is invalid.
      If input.Substring(startPos, endPos).Contains(",") Then
         match = Regex.Match(input, pattern)
         Do While match.Success
            Console.Write("The {0} played in the {1} in", _
                              match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
            startPos = match.Index + match.Length 
            endPos = CInt(IIf(startPos + 70 <= input.Length, 70, input.Length - startPos))
            If Not input.Substring(startPos, endPos).Contains(",") Then Exit Do
            match = match.NextMatch()            
         Loop
         Console.WriteLine()                               
      End If      

      Dim teams() As String = input.Split(New String() { vbCrLf }, StringSplitOptions.RemoveEmptyEntries)
      Console.WriteLine("Attempting to match each element in a string array:")
      For Each team As String In teams
         If team.Length > 70 Then Continue For
         match = Regex.Match(team, pattern)
         If match.Success Then
            Console.Write("The {0} played in the {1} in", _
                           match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
         End If
      Next
      Console.WriteLine()

      startPos = 0
      endPos = 70
      Console.WriteLine("Attempting to match each line of an input string with '$':")
      ' Provide minimal validation in the event the input is invalid.
      If input.Substring(startPos, endPos).Contains(",") Then
         match = Regex.Match(input, pattern, RegexOptions.Multiline)
         Do While match.Success
            Console.Write("The {0} played in the {1} in", _
                              match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
            startPos = match.Index + match.Length 
            endPos = CInt(IIf(startPos + 70 <= input.Length, 70, input.Length - startPos))
            If Not input.Substring(startPos, endPos).Contains(",") Then Exit Do
            match = match.NextMatch()            
         Loop
         Console.WriteLine()                               
      End If      


      startPos = 0
      endPos = 70
      pattern = basePattern + "\r?$" 
      Console.WriteLine("Attempting to match each line of an input string with '\r?$':")
      ' Provide minimal validation in the event the input is invalid.
      If input.Substring(startPos, endPos).Contains(",") Then
         match = Regex.Match(input, pattern, RegexOptions.Multiline)
         Do While match.Success
            Console.Write("The {0} played in the {1} in", _
                              match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
            startPos = match.Index + match.Length 
            endPos = CInt(IIf(startPos + 70 <= input.Length, 70, input.Length - startPos))
            If Not input.Substring(startPos, endPos).Contains(",") Then Exit Do
            match = match.NextMatch()            
         Loop
         Console.WriteLine()                               
      End If      
   End Sub
End Module
' The example displays the following output:
'    Attempting to match the entire input string:
'    
'    Attempting to match each element in a string array:
'    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
'    The Chicago Cubs played in the National League in 1903-present.
'    The Detroit Tigers played in the American League in 1901-present.
'    The New York Giants played in the National League in 1885-1957.
'    The Washington Senators played in the American League in 1901-1960.
'    
'    Attempting to match each line of an input string with '$':
'    
'    Attempting to match each line of an input string with '\r+$':
'    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
'    The Chicago Cubs played in the National League in 1903-present.
'    The Detroit Tigers played in the American League in 1901-present.
'    The New York Giants played in the National League in 1885-1957.
'    The Washington Senators played in the American League in 1901-1960.
```

## <a name="start-of-string-only-a"></a>Début de chaîne uniquement : \A

L’ancre **\A** spécifie qu’une correspondance doit se produire au début de la chaîne d’entrée. Elle est identique à l’ancre **^**, si ce n’est que **\A** ignore l’option [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline). Par conséquent, elle peut correspondre uniquement au début de la première ligne dans une chaîne d'entrée multiligne.

L’exemple suivant est semblable aux exemples des ancres **^** et **$**. Il utilise l’ancre **\A** dans une expression régulière qui extrait des informations sur les années où jouaient certaines équipes de baseball professionnelles. La chaîne d'entrée inclut cinq lignes. L’appel à la méthode [Regex.Matches(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) recherche uniquement la première sous-chaîne dans la chaîne d’entrée qui correspond au modèle d’expression régulière. Comme le montre l'exemple, l'option `Multiline` n'a aucun effet.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      int startPos = 0, endPos = 70;
      string input = "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957\n" +
                     "Chicago Cubs, National League, 1903-present\n" + 
                     "Detroit Tigers, American League, 1901-present\n" + 
                     "New York Giants, National League, 1885-1957\n" +  
                     "Washington Senators, American League, 1901-1960\n";   

      string pattern = @"\A((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+";
      Match match;

      if (input.Substring(startPos, endPos).Contains(",")) {
         match = Regex.Match(input, pattern, RegexOptions.Multiline);
         while (match.Success) {
            Console.Write("The {0} played in the {1} in", 
                              match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);

            Console.WriteLine(".");
            startPos = match.Index + match.Length;
            endPos = startPos + 70 <= input.Length ? 70 : input.Length - startPos;
            if (! input.Substring(startPos, endPos).Contains(",")) break;
            match = match.NextMatch();
         }
         Console.WriteLine();
      }
   }
}
// The example displays the following output:
//    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim startPos As Integer = 0
      Dim endPos As Integer = 70
      Dim input As String = "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957" + vbCrLf + _
                            "Chicago Cubs, National League, 1903-present" + vbCrLf + _
                            "Detroit Tigers, American League, 1901-present" + vbCrLf + _
                            "New York Giants, National League, 1885-1957" + vbCrLf + _
                            "Washington Senators, American League, 1901-1960" + vbCrLf  

      Dim pattern As String = "\A((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+"
      Dim match As Match

      ' Provide minimal validation in the event the input is invalid.
      If input.Substring(startPos, endPos).Contains(",") Then
         match = Regex.Match(input, pattern, RegexOptions.Multiline)
         Do While match.Success
            Console.Write("The {0} played in the {1} in", _
                              match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
            startPos = match.Index + match.Length 
            endPos = CInt(IIf(startPos + 70 <= input.Length, 70, input.Length - startPos))
            If Not input.Substring(startPos, endPos).Contains(",") Then Exit Do
            match = match.NextMatch()            
         Loop
         Console.WriteLine()                               
      End If      
   End Sub   
End Module
' The example displays the following output:
'    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
```

## <a name="end-of-string-or-before-ending-newline-z"></a>Fin de chaîne ou avant un saut de ligne final : \Z

L’ancre **\Z** spécifie qu’une correspondance doit se produire à la fin de la chaîne d’entrée ou avant **\n** en fin de chaîne d’entrée. Elle est identique à l’ancre **$**, si ce n’est que **\Z** ignore l’option [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline). Par conséquent, dans une chaîne multiligne, elle peut correspondre uniquement à la fin de la dernière ligne ou à la dernière ligne avant **\n**.

Notez que **\Z** correspond à **\n**, mais ne correspond pas à **\r\n** (combinaison de caractères CR/LF). Pour établir une correspondance avec les caractères CR/LF, incluez **\r?\Z** dans le modèle d’expression régulière.

L’exemple suivant utilise l’ancre **\Z** dans une expression régulière qui est semblable à l’exemple dans la section « Début de chaîne ou de ligne » précédente, qui extrait des informations à propos des années pendant lesquelles certaines équipes de baseball professionnelles ont existé. La sous-expression `\r?\Z` dans l’expression régulière `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` correspond à la fin d’une chaîne et correspond également à une chaîne qui se termine par **\n** ou **\r\n**. Par conséquent, chaque élément du tableau correspond au modèle d’expression régulière.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957",  
                          "Chicago Cubs, National League, 1903-present" + Environment.NewLine, 
                          "Detroit Tigers, American League, 1901-present" + Regex.Unescape(@"\n"), 
                          "New York Giants, National League, 1885-1957", 
                          "Washington Senators, American League, 1901-1960" + Environment.NewLine}; 
      string pattern = @"^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z";

      foreach (string input in inputs)
      {
         if (input.Length > 70 || ! input.Contains(",")) continue;

         Console.WriteLine(Regex.Escape(input));
         Match match = Regex.Match(input, pattern);
         if (match.Success)
            Console.WriteLine("   Match succeeded.");
         else
            Console.WriteLine("   Match failed.");
      }   
   }
}
// The example displays the following output:
//    Brooklyn\ Dodgers,\ National\ League,\ 1911,\ 1912,\ 1932-1957
//       Match succeeded.
//    Chicago\ Cubs,\ National\ League,\ 1903-present\r\n
//       Match succeeded.
//    Detroit\ Tigers,\ American\ League,\ 1901-present\n
//       Match succeeded.
//    New\ York\ Giants,\ National\ League,\ 1885-1957
//       Match succeeded.
//    Washington\ Senators,\ American\ League,\ 1901-1960\r\n
//       Match succeeded.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957",  _
                            "Chicago Cubs, National League, 1903-present" + vbCrLf, _
                            "Detroit Tigers, American League, 1901-present" + vbLf, _
                            "New York Giants, National League, 1885-1957", _
                            "Washington Senators, American League, 1901-1960" + vbCrLf }  
      Dim pattern As String = "^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z"

      For Each input As String In inputs
         If input.Length > 70 Or Not input.Contains(",") Then Continue For

         Console.WriteLine(Regex.Escape(input))
         Dim match As Match = Regex.Match(input, pattern)
         If match.Success Then
            Console.WriteLine("   Match succeeded.")
         Else
            Console.WriteLine("   Match failed.")
         End If
      Next   
   End Sub
End Module
' The example displays the following output:
'    Brooklyn\ Dodgers,\ National\ League,\ 1911,\ 1912,\ 1932-1957
'       Match succeeded.
'    Chicago\ Cubs,\ National\ League,\ 1903-present\r\n
'       Match succeeded.
'    Detroit\ Tigers,\ American\ League,\ 1901-present\n
'       Match succeeded.
'    New\ York\ Giants,\ National\ League,\ 1885-1957
'       Match succeeded.
'    Washington\ Senators,\ American\ League,\ 1901-1960\r\n
'       Match succeeded.
```

## <a name="end-of-string-only-z"></a>Fin de chaîne uniquement : \z

L’ancre **\z** spécifie qu’une correspondance doit se produire à la fin de la chaîne d’entrée. Comme l’élément de langage **$**, **\z** ignore l’option [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline). Contrairement à l’élément de langage **\Z**, **\z** ne correspond pas à un caractère **\n** à la fin d’une chaîne. Par conséquent, elle peut correspondre uniquement à la dernière ligne de la chaîne d'entrée.

L’exemple suivant utilise l’ancre **\z** dans une expression régulière qui est sinon identique à l’exemple dans la section précédente, qui extrait des informations à propos des années pendant lesquelles certaines équipes de baseball professionnelles ont existé. L'exemple essaie de faire correspondre chacun des cinq éléments dans un tableau de chaînes avec le modèle d'expression régulière `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z`. Deux des chaînes se terminent par un retour chariot et des caractères de saut de ligne, l'une se termine par un caractère de saut de ligne, et deux ne se terminent ni par un retour chariot ni par un caractère de saut de ligne. Comme le montre la sortie, seules les chaînes sans retour chariot ou caractère de saut de ligne correspondent au modèle. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957", 
                          "Chicago Cubs, National League, 1903-present" + Environment.NewLine,
                          "Detroit Tigers, American League, 1901-present\\r",
                          "New York Giants, National League, 1885-1957",
                          "Washington Senators, American League, 1901-1960" + Environment.NewLine };  
      string pattern = @"^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z";

      foreach (string input in inputs)
      {
         if (input.Length > 70 || ! input.Contains(",")) continue;

         Console.WriteLine(Regex.Escape(input));
         Match match = Regex.Match(input, pattern);
         if (match.Success)
            Console.WriteLine("   Match succeeded.");
         else
            Console.WriteLine("   Match failed.");
      }   
   }
}
// The example displays the following output:
//    Brooklyn\ Dodgers,\ National\ League,\ 1911,\ 1912,\ 1932-1957
//       Match succeeded.
//    Chicago\ Cubs,\ National\ League,\ 1903-present\r\n
//       Match failed.
//    Detroit\ Tigers,\ American\ League,\ 1901-present\n
//       Match failed.
//    New\ York\ Giants,\ National\ League,\ 1885-1957
//       Match succeeded.
//    Washington\ Senators,\ American\ League,\ 1901-1960\r\n
//       Match failed.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957",  _
                            "Chicago Cubs, National League, 1903-present" + vbCrLf, _
                            "Detroit Tigers, American League, 1901-present" + vbLf, _
                            "New York Giants, National League, 1885-1957", _
                            "Washington Senators, American League, 1901-1960" + vbCrLf }  
      Dim pattern As String = "^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z"

      For Each input As String In inputs
         If input.Length > 70 Or Not input.Contains(",") Then Continue For

         Console.WriteLine(Regex.Escape(input))
         Dim match As Match = Regex.Match(input, pattern)
         If match.Success Then
            Console.WriteLine("   Match succeeded.")
         Else
            Console.WriteLine("   Match failed.")
         End If
      Next   
   End Sub
End Module
' The example displays the following output:
'    Brooklyn\ Dodgers,\ National\ League,\ 1911,\ 1912,\ 1932-1957
'       Match succeeded.
'    Chicago\ Cubs,\ National\ League,\ 1903-present\r\n
'       Match failed.
'    Detroit\ Tigers,\ American\ League,\ 1901-present\n
'       Match failed.
'    New\ York\ Giants,\ National\ League,\ 1885-1957
'       Match succeeded.
'    Washington\ Senators,\ American\ League,\ 1901-1960\r\n
'       Match failed.
```

## <a name="contiguous-matches-g"></a>Correspondances contiguës : \G

L’ancre **\G** spécifie qu’une correspondance doit se produire au point où la correspondance précédente s’est terminée. Quand vous utilisez cette ancre avec la méthode [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) ou [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch), elle garantit que toutes les correspondances sont contiguës. 

L'exemple suivant utilise une expression régulière pour extraire les noms d'espèces de rongeurs d'une chaîne délimitée par des virgules. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "capybara,squirrel,chipmunk,porcupine,gopher," + 
                     "beaver,groundhog,hamster,guinea pig,gerbil," + 
                     "chinchilla,prairie dog,mouse,rat";
      string pattern = @"\G(\w+\s?\w*),?";
      Match match = Regex.Match(input, pattern);
      while (match.Success) 
      {
         Console.WriteLine(match.Groups[1].Value);
         match = match.NextMatch();
      } 
   }
}
// The example displays the following output:
//       capybara
//       squirrel
//       chipmunk
//       porcupine
//       gopher
//       beaver
//       groundhog
//       hamster
//       guinea pig
//       gerbil
//       chinchilla
//       prairie dog
//       mouse
//       rat
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "capybara,squirrel,chipmunk,porcupine,gopher," + _
                            "beaver,groundhog,hamster,guinea pig,gerbil," + _
                            "chinchilla,prairie dog,mouse,rat"
      Dim pattern As String = "\G(\w+\s?\w*),?"
      Dim match As Match = Regex.Match(input, pattern)
      Do While match.Success
         Console.WriteLine(match.Groups(1).Value)
         match = match.NextMatch()
      Loop 
   End Sub
End Module
' The example displays the following output:
'       capybara
'       squirrel
'       chipmunk
'       porcupine
'       gopher
'       beaver
'       groundhog
'       hamster
'       guinea pig
'       gerbil
'       chinchilla
'       prairie dog
'       mouse
'       rat
```

L'expression régulière `\G(\w+\s?\w*),?` est interprétée comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`\G` | Commencer là où la dernière correspondance s'est terminée.
`\w+` | Mettre en correspondance un ou plusieurs caractères alphabétiques.
`\s?` | Mettre en correspondance zéro ou un espace.
`\w*` | Mettre en correspondance zéro, un ou plusieurs caractères alphabétiques.
`(\w+\s?\w*)` | Mettre en correspondance un ou plusieurs caractères de mot suivis de zéro ou d'un espace, suivi de zéro ou davantage de caractères de mot. Il s'agit du premier groupe de capture.
`,?` | Mettre en correspondance zéro ou une occurrence d'une virgule littérale.
 
## <a name="word-boundary-b"></a>Limite de mot : \b

L’ancre **\b** spécifie que la correspondance doit se produire à la limite entre un caractère de mot (élément de langage **\w**) et un caractère n’appartenant pas à un mot (élément de langage **\W**). Les caractères de mot se composent de caractères alphanumériques et de traits de soulignement ; un caractère n'appartenant pas à un mot est un caractère qui n'est pas alphanumérique ou qui n'est pas un trait de soulignement. (Pour plus d’informations, consultez [Classes de caractères dans les expressions régulières](classes.md).) La correspondance peut également se produire à la limite d'un mot au début ou à la fin de la chaîne.

L’ancre **\b** est fréquemment utilisée pour faire en sorte qu’une sous-expression corresponde à un mot entier plutôt qu’au début ou à la fin d’un mot uniquement. L'expression régulière `\bare\w*\b` dans l'exemple suivant illustre cette utilisation. Elle correspond à tout mot qui commence par la sous-chaîne « are ». La sortie de l’exemple illustre également que **\b** correspond à la fois au début et la fin de la chaîne d’entrée. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "area bare arena mare";
      string pattern = @"\bare\w*\b";
      Console.WriteLine("Words that begin with 'are':");
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("'{0}' found at position {1}",
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       Words that begin with 'are':
//       'area' found at position 0
//       'arena' found at position 10
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "area bare arena mare"
      Dim pattern As String = "\bare\w*\b"
      Console.WriteLine("Words that begin with 'are':")
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("'{0}' found at position {1}", _
                           match.Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       Words that begin with 'are':
'       'area' found at position 0
'       'arena' found at position 10
```

Le modèle d’expression régulière est interprété comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`\b` | Commencer la correspondance à la limite d'un mot.
`are` | Mettre en correspondance la sous-chaîne « are ».
`\w*` | Mettre en correspondance zéro, un ou plusieurs caractères alphabétiques.
`\b` | Terminer la correspondance à la limite d'un mot.
 
## <a name="non-word-boundary-b"></a>Limite n'appartenant pas à un mot : \B

L’ancre **\B** spécifie que la correspondance ne doit pas se produire à la limite d’un mot. Elle est le contraire de l’ancre **\b**.

L’exemple suivant utilise l’ancre **\B** pour trouver des occurrences de la sous-chaîne « qu » dans un mot. Le modèle d'expression régulière `\Bqu\w+` met en correspondance une sous-chaîne qui commence par un « qu » qui n'est pas en début de mot et continue jusqu'à la fin du mot.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "equity queen equip acquaint quiet";
      string pattern = @"\Bqu\w+";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("'{0}' found at position {1}", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       'quity' found at position 1
//       'quip' found at position 14
//       'quaint' found at position 21
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "equity queen equip acquaint quiet"
      Dim pattern As String = "\Bqu\w+"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("'{0}' found at position {1}", _
                           match.Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       'quity' found at position 1
'       'quip' found at position 14
'       'quaint' found at position 21
```

Le modèle d'expression régulière est interprété comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`\B` | Ne pas commencer la correspondance à la limite d'un mot.
`qu` | Mettre en correspondance la sous-chaîne « qu ».
`\w+` | Mettre en correspondance un ou plusieurs caractères alphabétiques.
 
## <a name="see-also"></a>Voir aussi

[Langage des expressions régulières - Aide-mémoire](quick-ref.md)

[Options des expressions régulières](options.md)
 

