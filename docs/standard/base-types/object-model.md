---
title: "Modèle objet d’expression régulière"
description: "Modèle objet d’expression régulière"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a1e611ec-c6a2-48c6-9c52-0ed845787621
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: becfe2624ad1ee1d03707ef48c780f518eb8eb28

---

# <a name="the-regular-expression-object-model"></a>Modèle objet d’expression régulière

Cette rubrique décrit le modèle objet utilisé avec les expressions régulières .NET. Elle contient les sections suivantes :

* [Moteur d’expression régulière](#the-regular-expression-engine)

* [Objets MatchCollection et Match](#the-matchcollection-and-match-objects)

* [Collection de groupes](#the-group-collection)

* [Groupe capturé](#the-captured-group)

* [Collection de captures](#the-capture-collection)

* [Capture individuelle](#the-individual-capture)

## <a name="the-regular-expression-engine"></a>Moteur d’expression régulière

Le moteur d’expression régulière dans .NET est représenté par la classe [Regex](xref:System.Text.RegularExpressions.Regex). Le moteur d’expression régulière prend en charge l’analyse et la compilation d’une expression régulière, ainsi que les opérations qui mettent en correspondance le modèle d’expression régulière avec une chaîne d’entrée. Le moteur est le composant central du modèle objet des expressions régulières .NET.

Vous pouvez utiliser le moteur d'expression régulière de deux façons :

* En appelant les méthodes statiques de la classe [Regex](xref:System.Text.RegularExpressions.Regex). Les paramètres des méthodes comprennent la chaîne d’entrée et le modèle d’expression régulière. Le moteur d'expression régulière met en cache les expressions régulières utilisées dans les appels de méthode statique ; les appels répétés de méthodes d'expression régulière statiques qui utilisent la même expression régulière offrent donc des performances relativement bonnes.

* En instanciant un objet [Regex](xref:System.Text.RegularExpressions.Regex), via la transmission d’une expression régulière au constructeur de classe. Dans ce cas, l’objet [Regex](xref:System.Text.RegularExpressions.Regex) est immuable (lecture seule) et représente un moteur d’expression régulière étroitement lié à une expression régulière unique. Comme les expressions régulières utilisées par les instances de Regex ne sont pas mises en cache, vous ne devez pas instancier un objet [Regex](xref:System.Text.RegularExpressions.Regex) plusieurs fois avec la même expression régulière.

Vous pouvez appeler les méthodes de la classe [Regex](xref:System.Text.RegularExpressions.Regex) pour effectuer les opérations suivantes : 

* Déterminer si une chaîne correspond à un modèle d’expression régulière.

* Extraire une correspondance unique ou la première correspondance.

* Extraire toutes les correspondances.

* Remplacer une sous-chaîne mise en correspondance.

* Fractionner une chaîne spécifique en un tableau de chaînes.

Ces opérations sont décrites en détail dans les sections suivantes.

### <a name="matching-a-regular-expression-pattern"></a>Mise en correspondance d’un modèle d’expression régulière

La méthode [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) retourne `true` si la chaîne correspond au modèle, `false` sinon. La méthode [IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) est souvent utilisée pour valider une entrée de chaîne. Par exemple, le code suivant s'assure qu'une chaîne correspond à un numéro de sécurité sociale valide au États-Unis.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] values = { "111-22-3333", "111-2-3333"};
      string pattern = @"^\d{3}-\d{2}-\d{4}$";
      foreach (string value in values) {
         if (Regex.IsMatch(value, pattern))
            Console.WriteLine("{0} is a valid SSN.", value);
         else   
            Console.WriteLine("{0}: Invalid", value);
      }
   }
}
// The example displays the following output:
//       111-22-3333 is a valid SSN.
//       111-2-3333: Invalid
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim values() As String = { "111-22-3333", "111-2-3333"}
      Dim pattern As String = "^\d{3}-\d{2}-\d{4}$"
      For Each value As String In values
         If Regex.IsMatch(value, pattern) Then
            Console.WriteLine("{0} is a valid SSN.", value)
         Else   
            Console.WriteLine("{0}: Invalid", value)
         End If   
      Next
   End Sub
End Module
' The example displays the following output:
'       111-22-3333 is a valid SSN.
'       111-2-3333: Invalid
```

Le modèle d'expression régulière `^\d{3}-\d{2}-\d{4}$` est interprété comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`^` | Mettre en correspondance le début de la chaîne d'entrée.
`\d{3}` | Mettre en correspondance trois chiffres décimaux.
`-` | Mettre en correspondance un trait d'union.
`\d{2}` | Mettre en correspondance deux chiffres décimaux.
`-` | Mettre en correspondance un trait d'union.
`\d{4}` | Mettre en correspondance quatre chiffres décimaux.
`$` | Mettre en correspondance la fin de la chaîne d'entrée.
 
### <a name="extracting-a-single-match-or-the-first-match"></a>Extraction d’une correspondance unique ou de la première correspondance

La méthode [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) retourne un objet [Match](xref:System.Text.RegularExpressions.Match) qui contient des informations sur la première sous-chaîne qui correspond à un modèle d’expression régulière. Si la propriété `Match.Success` retourne `true`, indiquant alors qu’une correspondance a été trouvée, vous pouvez récupérer les informations sur les correspondances suivantes en appelant la méthode [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch). Ces appels de méthode peuvent se poursuivre jusqu'à ce que la propriété `Match.Success` retourne `false`. Par exemple, le code suivant utilise la méthode [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String)) pour rechercher la première occurrence d’un mot en double dans une chaîne. Il appelle ensuite la méthode [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) pour rechercher les occurrences supplémentaires éventuelles. L’exemple examine la propriété `Match.Success` après chaque appel de méthode pour déterminer si la mise en correspondance actuelle a réussi et si elle doit être suivie d’un appel de la méthode [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch).

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is a a farm that that raises dairy cattle."; 
      string pattern = @"\b(\w+)\W+(\1)\b";
      Match match = Regex.Match(input, pattern);
      while (match.Success)
      {
         Console.WriteLine("Duplicate '{0}' found at position {1}.",  
                           match.Groups[1].Value, match.Groups[2].Index);
         match = match.NextMatch();
      }                       
   }
}
// The example displays the following output:
//       Duplicate 'a' found at position 10.
//       Duplicate 'that' found at position 22.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is a a farm that that raises dairy cattle." 
      Dim pattern As String = "\b(\w+)\W+(\1)\b"
      Dim match As Match = Regex.Match(input, pattern)
      Do While match.Success
         Console.WriteLine("Duplicate '{0}' found at position {1}.", _ 
                           match.Groups(1).Value, match.Groups(2).Index)
         match = match.NextMatch()
      Loop                       
   End Sub
End Module
' The example displays the following output:
'       Duplicate 'a' found at position 10.
'       Duplicate 'that' found at position 22.
```

Le modèle d'expression régulière `\b(\w+)\W+(\1)\b` est interprété comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`\b` | Commencer la correspondance à la limite d'un mot.
`(\w+)` | Mettre en correspondance un ou plusieurs caractères alphabétiques. Il s'agit du premier groupe de capture.
`\W+` | Mettre en correspondance un ou plusieurs caractères non alphabétiques.
`(\1)` | Mettre en correspondance la première chaîne capturée. Il s'agit du deuxième groupe de capture. 
`\b` | Terminer la correspondance à la limite d'un mot.
 
### <a name="extracting-all-matches"></a>Extraction de toutes les correspondances

La méthode [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) retourne un objet [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) qui contient des informations sur toutes les correspondances trouvées par le moteur d’expression régulière dans la chaîne d’entrée. Ainsi, l’exemple précédent peut être réécrit pour appeler la méthode [Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) au lieu des méthodes [Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) et [NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch).

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is a a farm that that raises dairy cattle."; 
      string pattern = @"\b(\w+)\W+(\1)\b";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Duplicate '{0}' found at position {1}.",  
                           match.Groups[1].Value, match.Groups[2].Index);
   }
}
// The example displays the following output:
//       Duplicate 'a' found at position 10.
//       Duplicate 'that' found at position 22.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is a a farm that that raises dairy cattle." 
      Dim pattern As String = "\b(\w+)\W+(\1)\b"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Duplicate '{0}' found at position {1}.", _ 
                           match.Groups(1).Value, match.Groups(2).Index)
      Next                       
   End Sub
End Module
' The example displays the following output:
'       Duplicate 'a' found at position 10.
'       Duplicate 'that' found at position 22.
```

### <a name="replacing-a-matched-substring"></a>Remplacement d’une sous-chaîne mise en correspondance

La méthode [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) remplace chaque sous-chaîne mise en correspondance par le modèle d’expression régulière par une chaîne ou un modèle d’expression régulière spécifique, puis retourne la chaîne d’entrée entière avec les remplacements. Par exemple, le code suivant ajoute le symbole de devise des États-Unis avant un nombre décimal dans une chaîne.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b\d+\.\d{2}\b";
      string replacement = "$$$&"; 
      string input = "Total Cost: 103.64";
      Console.WriteLine(Regex.Replace(input, pattern, replacement));     
   }
}
// The example displays the following output:
//       Total Cost: $103.64
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b\d+\.\d{2}\b"
      Dim replacement As String = "$$$&" 
      Dim input As String = "Total Cost: 103.64"
      Console.WriteLine(Regex.Replace(input, pattern, replacement))     
   End Sub
End Module
' The example displays the following output:
'       Total Cost: $103.64
```

Le modèle d'expression régulière `\b\d+\.\d{2}\b` est interprété comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`\b` | Commencer la correspondance à la limite d'un mot.
`\d+` | Mettre en correspondance un ou plusieurs chiffres décimaux.
`\.` | Mettre en correspondance un point.
`\d{2}` | Mettre en correspondance deux chiffres décimaux.
`\b` | Terminer la correspondance à la limite d'un mot.
 
Le modèle de remplacement `$$$&` est interprété comme indiqué dans le tableau suivant.

Modèle | Chaîne de remplacement
------- | ------------------ 
`$$` | Caractère du signe dollar (**$**).
`$&` | Sous-chaîne entière mise en correspondance.
 
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>Fractionnement d’une chaîne spécifique en un tableau de chaînes

La méthode [Regex.Split](xref:System.Text.RegularExpressions.Regex.Split(System.String)) fractionne la chaîne d’entrée aux positions définies par une correspondance d’expression régulière. Par exemple, le code suivant place les éléments d'une liste numérotée dans un tableau de chaînes.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "1. Eggs 2. Bread 3. Milk 4. Coffee 5. Tea";
      string pattern = @"\b\d{1,2}\.\s";
      foreach (string item in Regex.Split(input, pattern))
      {
         if (! String.IsNullOrEmpty(item))
            Console.WriteLine(item);
      }      
   }
}
// The example displays the following output:
//       Eggs
//       Bread
//       Milk
//       Coffee
//       Tea
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "1. Eggs 2. Bread 3. Milk 4. Coffee 5. Tea"
      Dim pattern As String = "\b\d{1,2}\.\s"
      For Each item As String In Regex.Split(input, pattern)
         If Not String.IsNullOrEmpty(item) Then
            Console.WriteLine(item)
         End If
      Next      
   End Sub
End Module
' The example displays the following output:
'       Eggs
'       Bread
'       Milk
'       Coffee
'       Tea
```

Le modèle d'expression régulière `\b\d{1,2}\.\s` est interprété comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`\b` | Commencer la correspondance à la limite d'un mot.
`\d{1,2}` | Mettre en correspondance un ou deux chiffres décimaux.
`\.` | Mettre en correspondance un point.
`\s` | Mettre en correspondance un espace blanc.
 
## <a name="the-matchcollection-and-match-objects"></a>Objets MatchCollection et Match

Les méthodes [Regex](xref:System.Text.RegularExpressions.Regex) retournent deux objets qui font partie du modèle objet d’expression régulière : l’objet [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) et l’objet [Match](xref:System.Text.RegularExpressions.Match). 

### <a name="the-match-collection"></a>Collection de correspondances

La méthode [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) retourne un objet [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) qui contient des objets [Match](xref:System.Text.RegularExpressions.Match) représentant toutes les correspondances trouvées par le moteur d’expression régulière, dans l’ordre dans lequel elles se produisent dans la chaîne d’entrée. S’il n’existe aucune correspondance, la méthode retourne un objet [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) contenant un objet [Match](xref:System.Text.RegularExpressions.Match) sans membres. La propriété [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) `Item` vous permet d’accéder à des membres spécifiques de la collection en fonction de leur index, qui est compris entre zéro et la valeur de la propriété [MatchCollection.Count](xref:System.Text.RegularExpressions.MatchCollection.Count) moins une unité. « Item » est l’indexeur de la collection (en C#) et la propriété par défaut (en Visual Basic).

Par défaut, l’appel de la méthode [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) utilise une évaluation paresseuse pour remplir l’objet [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection). L’accès aux propriétés qui nécessitent une collection entièrement remplie, telles que les propriétés [MatchCollection.Count](xref:System.Text.RegularExpressions.MatchCollection.Count) et `Item`, peut affecter les performances. Nous vous recommandons donc d’accéder à la collection en utilisant l’objet [IEnumerator](xref:System.Collections.IEnumerator) retourné par la méthode [MatchCollection.GetEnumerator](xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator). Des constructions propres au langage, comme `foreach` en C# et « For Each » en Visual Basic, incluent l’interface IEnumerator](xref:System.Collections.IEnumerator) de la collection dans un wrapper.

L’exemple suivant utilise la méthode [Regex.Matches(String)](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) pour remplir un objet [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) avec toutes les correspondances trouvées dans une chaîne d’entrée. L’exemple énumère la collection, copie les correspondances dans un tableau de chaînes et enregistre les positions de caractère dans un tableau d’entiers.

```csharp
using System;
using System.Collections.Generic;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
       MatchCollection matches;
       List<string> results = new List<string>();
       List<int> matchposition = new List<int>();

       // Create a new Regex object and define the regular expression.
       Regex r = new Regex("abc");
       // Use the Matches method to find all matches in the input string.
       matches = r.Matches("123abc4abcd");
       // Enumerate the collection to retrieve all matches and positions.
       foreach (Match match in matches)
       {
          // Add the match string to the string array.
           results.Add(match.Value);
           // Record the character position where the match was found.
           matchposition.Add(match.Index);
       }
       // List the results.
       for (int ctr = 0; ctr < results.Count; ctr++)
         Console.WriteLine("'{0}' found at position {1}.", 
                           results[ctr], matchposition[ctr]);  
   }
}
// The example displays the following output:
//       'abc' found at position 3.
//       'abc' found at position 7.
```

```vb
Imports System.Collections.Generic
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
       Dim matches As MatchCollection
       Dim results As New List(Of String)
       Dim matchposition As New List(Of Integer)

       ' Create a new Regex object and define the regular expression.
       Dim r As New Regex("abc")
       ' Use the Matches method to find all matches in the input string.
       matches = r.Matches("123abc4abcd")
       ' Enumerate the collection to retrieve all matches and positions.
       For Each match As Match In matches
          ' Add the match string to the string array.
           results.Add(match.Value)
           ' Record the character position where the match was found.
           matchposition.Add(match.Index)
       Next
       ' List the results.
       For ctr As Integer = 0 To results.Count - 1
         Console.WriteLine("'{0}' found at position {1}.", _
                           results(ctr), matchposition(ctr))  
       Next
   End Sub
End Module
' The example displays the following output:
'       'abc' found at position 3.
'       'abc' found at position 7.
```

### <a name="the-match"></a>Classe Match

La classe [Match](xref:System.Text.RegularExpressions.Match) représente le résultat d’une correspondance d’expression régulière unique. Vous pouvez accéder aux objets [Match](xref:System.Text.RegularExpressions.Match) de deux façons :

* En les récupérant de l’objet [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) retourné par la méthode Regex.Matches. Pour récupérer des objets [Match](xref:System.Text.RegularExpressions.Match) spécifiques, itérez la collection en utilisant une construction `foreach` (en C#) ou `For Each...Next` (en Visual Basic), ou utilisez la propriété [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) `Item` pour récupérer un objet [Match](xref:System.Text.RegularExpressions.Match) spécifique en fonction de son index ou de son nom. Vous pouvez également récupérer des objets [Match](xref:System.Text.RegularExpressions.Match) spécifiques de la collection en itérant la collection à partir des valeurs d’index, qui peuvent aller de zéro au nombre d’objets dans la collection moins une unité. Toutefois, cette méthode ne tire pas parti de l’évaluation paresseuse, car elle accède à la propriété [MatchCollection.Count](xref:System.Text.RegularExpressions.MatchCollection.Count). 

  L’exemple suivant récupère des objets [Match](xref:System.Text.RegularExpressions.Match) spécifiques d’un objet [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) en itérant la collection à l’aide de la construction `foreach`. L'expression régulière met simplement en correspondance la chaîne « abc » dans la chaîne d'entrée.

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     public static void Main()
     {
        string pattern = "abc";
        string input = "abc123abc456abc789";
        foreach (Match match in Regex.Matches(input, pattern))
           Console.WriteLine("{0} found at position {1}.", 
                             match.Value, match.Index);
     }
  }
  // The example displays the following output:
  //       abc found at position 0.
  //       abc found at position 6.
  //       abc found at position 12.
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim pattern As String = "abc"
        Dim input As String = "abc123abc456abc789"
        For Each match As Match In Regex.Matches(input, pattern)
           Console.WriteLine("{0} found at position {1}.", _
                             match.Value, match.Index)
        Next                     
     End Sub
  End Module
  ' The example displays the following output:
  '       abc found at position 0.
  '       abc found at position 6.
  '       abc found at position 12.
  ```

* En appelant la méthode [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)), qui retourne un objet [Match](xref:System.Text.RegularExpressions.Match) représentant la première correspondance dans une chaîne ou dans une partie d’une chaîne. Vous pouvez déterminer si la correspondance a été trouvée en récupérant la valeur de la propriété `Match.Success`. Pour récupérer les objets [Match](xref:System.Text.RegularExpressions.Match) qui représentent les correspondances suivantes, appelez la méthode [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) de manière répétée, jusqu’à ce que la propriété `Success` de l’objet [Match](xref:System.Text.RegularExpressions.Match) retourné ait pour valeur `false`. 

  L’exemple suivant utilise les méthodes [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String)) et [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) pour mettre en correspondance la chaîne « abc » dans la chaîne d’entrée.

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     public static void Main()
     {
        string pattern = "abc";
        string input = "abc123abc456abc789";
        Match match = Regex.Match(input, pattern);
        while (match.Success)
        {
           Console.WriteLine("{0} found at position {1}.", 
                             match.Value, match.Index);
           match = match.NextMatch();                  
        }                     
     }
  }
  // The example displays the following output:
  //       abc found at position 0.
  //       abc found at position 6.
  //       abc found at position 12.
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim pattern As String = "abc"
        Dim input As String = "abc123abc456abc789"
        Dim match As Match = Regex.Match(input, pattern)
        Do While match.Success
           Console.WriteLine("{0} found at position {1}.", _
                             match.Value, match.Index)
           match = match.NextMatch()                  
        Loop                     
     End Sub
  End Module
  ' The example displays the following output:
  '       abc found at position 0.
  '       abc found at position 6.
  '       abc found at position 12.
  ```

Deux propriétés de la classe [Match](xref:System.Text.RegularExpressions.Match) retournent des objets de collection :

* La propriété [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) retourne un objet [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) qui contient des informations sur les sous-chaînes correspondant aux groupes de capture dans le modèle d’expression régulière. 

* La propriété `Match.Captures` retourne un objet [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) dont l’utilisation est limitée. La collection n’est pas remplie dans le cas d’un objet [Match](xref:System.Text.RegularExpressions.Match) dont la propriété `Success` a pour valeur `false`. Sinon, elle contient un objet [Capture](xref:System.Text.RegularExpressions.Capture) unique qui possède les mêmes informations que l’objet [Match](xref:System.Text.RegularExpressions.Match). 

Pour plus d’informations sur ces objets, consultez les sections [Collection de groupes](#the-group-collection) et [Collection de captures](#the-capture-collection) plus loin dans cette rubrique.

Deux propriétés supplémentaires de la classe [Match](xref:System.Text.RegularExpressions.Match) fournissent des informations sur la correspondance. La propriété `Match.Value` retourne la sous-chaîne de la chaîne d'entrée qui correspond au modèle d'expression régulière. La propriété `Match.Index` retourne la position de début en base zéro de la chaîne mise en correspondance dans la chaîne d'entrée.

En outre, la classe [Match](xref:System.Text.RegularExpressions.Match) possède deux méthodes de mise en correspondance de modèle :

* La méthode [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) trouve la correspondance après la correspondance représentée par l’objet [Match](xref:System.Text.RegularExpressions.Match) actuel, puis retourne un objet [Match](xref:System.Text.RegularExpressions.Match) représentant cette correspondance.

* La méthode [Match.Result](xref:System.Text.RegularExpressions.Match.NextMatch) effectue une opération de remplacement spécifique sur la chaîne mise en correspondance et retourne le résultat. 


L’exemple suivant utilise la méthode [Match.Result](xref:System.Text.RegularExpressions.Match.NextMatch) pour ajouter un symbole **$** et un espace avant chaque nombre comprenant deux chiffres fractionnaires. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b\d+(,\d{3})*\.\d{2}\b";
      string input = "16.32\n194.03\n1,903,672.08"; 

      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Result("$$ $&"));
   }
}
// The example displays the following output:
//       $ 16.32
//       $ 194.03
//       $ 1,903,672.08
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b\d+(,\d{3})*\.\d{2}\b"
      Dim input As String = "16.32" + vbCrLf + "194.03" + vbCrLf + "1,903,672.08" 

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Result("$$ $&"))
      Next
   End Sub
End Module
' The example displays the following output:
'       $ 16.32
'       $ 194.03
'       $ 1,903,672.08
```

Le modèle d'expression régulière `\b\d+(,\d{3})*\.\d{2}\b` est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`\b` | Commencer la correspondance à la limite d'un mot.
`\d+` | Mettre en correspondance un ou plusieurs chiffres décimaux.
`(,\d{3})*` | Mettre en correspondance zéro occurrence, ou plus, d'une virgule suivie de trois chiffres décimaux.
`\.` | Mettre en correspondance le séparateur décimal.
\d{2} | Mettre en correspondance deux chiffres décimaux.
`\b` | Terminer la correspondance à la limite d'un mot.
 
Le modèle de remplacement **$$ $&** indique que la sous-chaîne mise en correspondance doit être remplacée par un symbole dollar (**$**) (modèle `$$`), suivi d’un espace et de la valeur de la correspondance (modèle `$&`).

## <a name="the-group-collection"></a>Collection de groupes

La propriété [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) retourne un objet [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) qui contient des objets [Group](xref:System.Text.RegularExpressions.Group) représentant des groupes capturés dans une même correspondance. Le premier objet [Group](xref:System.Text.RegularExpressions.Group) de la collection (index 0) représente la correspondance entière. Chaque objet qui suit représente le résultat d'un groupe de capture spécifique. 

Vous pouvez récupérer des objets [Group](xref:System.Text.RegularExpressions.Group) spécifiques dans la collection en utilisant la propriété [GroupCollection.Item](xref:System.Text.RegularExpressions.GroupCollection.Item(System.Int32)). Vous pouvez récupérer les groupes sans nom en fonction de leur position ordinale dans la collection, et les groupes nommés en fonction de leur nom ou de leur position ordinale. Les captures sans nom apparaissent en premier dans la collection et sont indexées de la gauche vers la droite dans l'ordre dans lequel elles figurent dans le modèle d'expression régulière. Les captures nommées sont indexées après les captures sans nom, de la gauche vers la droite dans l’ordre dans lequel elles apparaissent dans le modèle d’expression régulière. Pour déterminer les groupes numérotés disponibles dans la collection retournée pour une méthode de mise en correspondance d’expression régulière particulière, vous pouvez appeler la méthode d’instance [Regex.GetGroupNumbers](xref:System.Text.RegularExpressions.Regex.GetGroupNumbers). Pour déterminer les groupes nommés disponibles dans la collection, vous pouvez appeler la méthode d’instance [Regex.GetGroupNames](xref:System.Text.RegularExpressions.Regex.GetGroupNames). Les deux méthodes sont particulièrement utiles dans les opérations générales qui analysent les correspondances trouvées par une expression régulière. 

La propriété [GroupCollection.Item](xref:System.Text.RegularExpressions.GroupCollection.Item(System.Int32)) représente l’indexeur de la collection en C# et la propriété par défaut de l’objet de collection en Visual Basic. Cela signifie que les différents objets [Group](xref:System.Text.RegularExpressions.Group) sont accessibles en fonction de leur index (ou nom, dans le cas des groupes nommés) comme suit : 

```csharp
Group group = match.Groups[ctr];
```

```vb
Dim group As Group = match.Groups(ctr)
```

L'exemple suivant définit une expression régulière qui utilise des constructions de regroupement pour capturer les mois, jour et année d'une date. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\w+)\s(\d{1,2}),\s(\d{4})\b";
      string input = "Born: July 28, 1989";
      Match match = Regex.Match(input, pattern);
      if (match.Success)
         for (int ctr = 0; ctr <  match.Groups.Count; ctr++)
            Console.WriteLine("Group {0}: {1}", ctr, match.Groups[ctr].Value);
    }
}
// The example displays the following output:
//       Group 0: July 28, 1989
//       Group 1: July
//       Group 2: 28
//       Group 3: 1989
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\w+)\s(\d{1,2}),\s(\d{4})\b"
      Dim input As String = "Born: July 28, 1989"
      Dim match As Match = Regex.Match(input, pattern)
      If match.Success Then
         For ctr As Integer = 0 To match.Groups.Count - 1
            Console.WriteLine("Group {0}: {1}", ctr, match.Groups(ctr).Value)
         Next      
      End If   
   End Sub
End Module
' The example displays the following output:
'       Group 0: July 28, 1989
'       Group 1: July
'       Group 2: 28
'       Group 3: 1989
```

Le modèle d'expression régulière `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`\b` | Commencer la correspondance à la limite d'un mot.
`(\w+)` | Mettre en correspondance un ou plusieurs caractères alphabétiques. Il s'agit du premier groupe de capture.
`\s` | Mettre en correspondance un espace blanc.
`(\d{1,2})` | Mettre en correspondance un ou deux chiffres décimaux. Il s'agit du deuxième groupe de capture.
`,` | Mettre en correspondance une virgule.
`\s` | Mettre en correspondance un espace blanc.
`(\d{4})` | Mettre en correspondance quatre chiffres décimaux. Il s'agit du troisième groupe de capture.
`\b` | Terminer la correspondance à la limite d'un mot.
 
## <a name="the-captured-group"></a>Groupe capturé

La classe [Group](xref:System.Text.RegularExpressions.Group) représente le résultat d’un groupe de capture spécifique. Les objets [Group](xref:System.Text.RegularExpressions.Group) qui représentent les groupes de capture définis dans une expression régulière sont retournés par la propriété [Item](xref:System.Text.RegularExpressions.GroupCollection.Item(System.Int32)) de l’objet [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) retourné par la propriété [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups). La propriété [Item](xref:System.Text.RegularExpressions.GroupCollection.Item(System.Int32)) représente l’indexeur (en C#) et la propriété par défaut (en Visual Basic) de la classe [Group](xref:System.Text.RegularExpressions.Group). Vous pouvez également récupérer des membres spécifiques en itérant la collection à l’aide de la construction `foreach`. La section précédente propose un exemple.

L'exemple suivant utilise des constructions de regroupement imbriquées pour capturer des sous-chaînes en groupes. Le modèle d'expression régulière `(a(b))c` met en correspondance la chaîne « abc ». Il affecte la sous-chaîne « ab » au premier groupe de capture, et la sous-chaîne « b » au second groupe de capture.

```csharp
List<int> matchposition = new List<int>();
List<string> results = new List<string>();
// Define substrings abc, ab, b.
Regex r = new Regex("(a(b))c"); 
Match m = r.Match("abdabc");
for (int i = 0; m.Groups[i].Value != ""; i++) 
{
   // Add groups to string array.
   results.Add(m.Groups[i].Value); 
   // Record character position.
   matchposition.Add(m.Groups[i].Index); 
}

// Display the capture groups.
for (int ctr = 0; ctr < results.Count; ctr++)
   Console.WriteLine("{0} at position {1}", 
                     results[ctr], matchposition[ctr]);
// The example displays the following output:
//       abc at position 3
//       ab at position 3
//       b at position 4
```

```vb
Dim matchposition As New List(Of Integer)
 Dim results As New List(Of String)
 ' Define substrings abc, ab, b.
 Dim r As New Regex("(a(b))c") 
 Dim m As Match = r.Match("abdabc")
 Dim i As Integer = 0
 While Not (m.Groups(i).Value = "")    
    ' Add groups to string array.
    results.Add(m.Groups(i).Value)     
    ' Record character position. 
    matchposition.Add(m.Groups(i).Index) 
     i += 1
 End While

 ' Display the capture groups.
 For ctr As Integer = 0 to results.Count - 1
    Console.WriteLine("{0} at position {1}", _ 
                      results(ctr), matchposition(ctr))
 Next                     
' The example displays the following output:
'       abc at position 3
'       ab at position 3
'       b at position 4
```

L'exemple suivant utilise des constructions de regroupement nommées pour capturer des sous-chaînes dans une chaîne qui contient des données au format « NOM_DONNÉES:VALEUR », que l'expression régulière fractionne au niveau du symbole deux-points (:).

```csharp
Regex r = new Regex("^(?<name>\\w+):(?<value>\\w+)");
Match m = r.Match("Section1:119900");
Console.WriteLine(m.Groups["name"].Value);
Console.WriteLine(m.Groups["value"].Value);
// The example displays the following output:
//       Section1
//       119900
```

```vb
Dim r As New Regex("^(?<name>\w+):(?<value>\w+)")
Dim m As Match = r.Match("Section1:119900")
Console.WriteLine(m.Groups("name").Value)
Console.WriteLine(m.Groups("value").Value)
' The example displays the following output:
'       Section1
'       119900
```

Le modèle d'expression régulière `^(?<name>\w+):(?<value>\w+)` est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`^` | Commencer la correspondance au début de la chaîne d'entrée.
`(?<name>\w+)` | Mettre en correspondance un ou plusieurs caractères alphabétiques. Le nom de ce groupe de capture est « name ».
`:` | Mettre en correspondance un symbole deux-points.
`(?<value>\w+)` | Mettre en correspondance un ou plusieurs caractères alphabétiques. Le nom de ce groupe de capture est « value ».
 
Les propriétés de la classe [Group](xref:System.Text.RegularExpressions.Group) fournissent des informations sur le groupe capturé : la propriété `Group.Value` contient la sous-chaîne capturée, la propriété `Group.Index` indique la position de début du groupe capturé dans le texte d’entrée, la propriété `Group.Length` contient la longueur du texte capturé et la propriété `Group.Success` indique si une correspondance a été trouvée entre une sous-chaîne et le modèle défini par le groupe de capture.

L’application de quantificateurs à un groupe (pour plus d’informations, consultez [Quantificateurs dans les expressions régulières](quantifiers.md)) modifie la relation d’une capture par groupe de capture de deux façons :

* Si le quantificateur __*__ ou __*?__ (qui spécifie zéro correspondance, ou plus) est appliqué à un groupe, un groupe de capture peut ne pas avoir de correspondance dans la chaîne d’entrée. En l’absence de texte capturé, les propriétés de l’objet [Group](xref:System.Text.RegularExpressions.Group) sont définies comme indiqué dans le tableau suivant.

  Propriété de groupe | Valeur
  -------------- | ----- 
  `Success` | `false`
  `Value` | [String.Empty](xref:System.String.Empty) 
  `Length` | 0
 
  L'exemple suivant illustre cette situation. Dans le modèle d'expression régulière `aaa(bbb)*ccc`, le premier groupe de capture (la sous-chaîne « bbb ») peut être mis en correspondance zéro fois, ou plus. Comme la chaîne d’entrée « aaaccc » correspond au modèle, le groupe de capture ne possède pas de correspondance.

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     public static void Main()
     {
        string pattern = "aaa(bbb)*ccc";
        string input = "aaaccc";
        Match match = Regex.Match(input, pattern);
        Console.WriteLine("Match value: {0}", match.Value);
        if (match.Groups[1].Success)
           Console.WriteLine("Group 1 value: {0}", match.Groups[1].Value);
        else
           Console.WriteLine("The first capturing group has no match.");
     }
  }
  // The example displays the following output:
  //       Match value: aaaccc
  //       The first capturing group has no match.
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim pattern As String = "aaa(bbb)*ccc"
        Dim input As String = "aaaccc"
        Dim match As Match = Regex.Match(input, pattern)
        Console.WriteLine("Match value: {0}", match.Value)
        If match.Groups(1).Success Then
           Console.WriteLine("Group 1 value: {0}", match.Groups(1).Value)
        Else
           Console.WriteLine("The first capturing group has no match.")
       End If   
     End Sub
  End Module
  ' The example displays the following output:
  '       Match value: aaaccc
  '       The first capturing group has no match.
  ```

* Les quantificateurs peuvent mettre en correspondance plusieurs occurrences d’un modèle défini par un groupe de capture. Dans ce cas, les propriétés `Value` et `Length` d’un objet [Group](xref:System.Text.RegularExpressions.Group) ne contiennent des informations que sur la dernière sous-chaîne capturée. Par exemple, l'expression régulière suivante met en correspondance une phrase unique qui se termine par un point. Elle utilise deux constructions de regroupement : la première capture des mots individuels ainsi qu'un espace blanc, tandis que la seconde capture des mots individuels. Comme le montre le résultat de l'exemple, bien que l'expression régulière parvienne à capturer une phrase entière, le second groupe capture uniquement le dernier mot.

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     public static void Main()
     {
        string pattern = @"\b((\w+)\s?)+\.";
        string input = "This is a sentence. This is another sentence.";
        Match match = Regex.Match(input, pattern);
        if (match.Success)
        {
           Console.WriteLine("Match: " + match.Value);
           Console.WriteLine("Group 2: " + match.Groups[2].Value);
        }   
     }
  }
  // The example displays the following output:
  //       Match: This is a sentence.
  //       Group 2: sentence
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim pattern As String = "\b((\w+)\s?)+\."
        Dim input As String = "This is a sentence. This is another sentence."
        Dim match As Match = Regex.Match(input, pattern)
        If match.Success Then
           Console.WriteLine("Match: " + match.Value)
           Console.WriteLine("Group 2: " + match.Groups(2).Value)
        End If   
     End Sub
  End Module
  ' The example displays the following output:
  '       Match: This is a sentence.
  '       Group 2: sentence
  ```

## <a name="the-capture-collection"></a>Collection de captures

L’objet [Group](xref:System.Text.RegularExpressions.Group) ne contient des informations que sur la dernière capture. Toutefois, l’ensemble complet des captures effectuées par un groupe de capture est récupérable de l’objet [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) retourné par la propriété [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures). Chaque membre de la collection est un objet [Capture](xref:System.Text.RegularExpressions.Capture) qui représente une capture effectuée par ce groupe de capture, dans l’ordre dans lequel ils ont été capturés (donc, dans l’ordre dans lequel les chaînes capturées ont été mises en correspondance de la gauche vers la droite dans la chaîne d’entrée). Vous pouvez récupérer des objets [Capture](xref:System.Text.RegularExpressions.Capture) spécifiques de la collection de deux façons : 

* En itérant la collection à l’aide d’une construction telle que `foreach` (en C#) ou `For Each` (en Visual Basic).

* En utilisant la propriété [CaptureCollection.Item](xref:System.Text.RegularExpressions.CaptureCollection.Item(System.Int32)) pour récupérer un objet spécifique en fonction de son index. La propriété Item représente l’indexeur (en C#) ou la propriété par défaut de l’objet [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) (en Visual Basic).


Si aucun quantificateur n’est appliqué à un groupe de capture, l’objet [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) contient un objet [Capture](xref:System.Text.RegularExpressions.Capture) unique qui présente peu d’intérêt, car il fournit des informations sur la même correspondance que son objet [Group](xref:System.Text.RegularExpressions.Group). Si un quantificateur est appliqué à un groupe de capture, l’objet [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) contient toutes les captures effectuées par le groupe de capture, et le dernier membre de la collection représente la même capture que l’objet [Group](xref:System.Text.RegularExpressions.Group). 

Par exemple, si vous utilisez le modèle d’expression régulière `((a(b))c)+` (où le quantificateur `+` spécifie une ou plusieurs correspondances) pour capturer des correspondances dans la chaîne « abcabcabc », l’objet [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) de chaque objet [Group](xref:System.Text.RegularExpressions.Group) contient trois membres.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "((a(b))c)+";
      string input = "abcabcabc";

      Match match = Regex.Match(input, pattern);
      if (match.Success)
      {
         Console.WriteLine("Match: '{0}' at position {1}",  
                           match.Value, match.Index);
         GroupCollection groups = match.Groups;
         for (int ctr = 0; ctr < groups.Count; ctr++) {
            Console.WriteLine("   Group {0}: '{1}' at position {2}", 
                              ctr, groups[ctr].Value, groups[ctr].Index);
            CaptureCollection captures = groups[ctr].Captures;
            for (int ctr2 = 0; ctr2 < captures.Count; ctr2++) {
               Console.WriteLine("      Capture {0}: '{1}' at position {2}", 
                                 ctr2, captures[ctr2].Value, captures[ctr2].Index);
            }                     
         }
      }
   }
}
// The example displays the following output:
//       Match: 'abcabcabc' at position 0
//          Group 0: 'abcabcabc' at position 0
//             Capture 0: 'abcabcabc' at position 0
//          Group 1: 'abc' at position 6
//             Capture 0: 'abc' at position 0
//             Capture 1: 'abc' at position 3
//             Capture 2: 'abc' at position 6
//          Group 2: 'ab' at position 6
//             Capture 0: 'ab' at position 0
//             Capture 1: 'ab' at position 3
//             Capture 2: 'ab' at position 6
//          Group 3: 'b' at position 7
//             Capture 0: 'b' at position 1
//             Capture 1: 'b' at position 4
//             Capture 2: 'b' at position 7
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "((a(b))c)+"
      Dim input As STring = "abcabcabc"

      Dim match As Match = Regex.Match(input, pattern)
      If match.Success Then
         Console.WriteLine("Match: '{0}' at position {1}", _ 
                           match.Value, match.Index)
         Dim groups As GroupCollection = match.Groups
         For ctr As Integer = 0 To groups.Count - 1
            Console.WriteLine("   Group {0}: '{1}' at position {2}", _
                              ctr, groups(ctr).Value, groups(ctr).Index)
            Dim captures As CaptureCollection = groups(ctr).Captures
            For ctr2 As Integer = 0 To captures.Count - 1
               Console.WriteLine("      Capture {0}: '{1}' at position {2}", _
                                 ctr2, captures(ctr2).Value, captures(ctr2).Index)
            Next
         Next
      End If
   End Sub
End Module
' The example dosplays the following output:
'       Match: 'abcabcabc' at position 0
'          Group 0: 'abcabcabc' at position 0
'             Capture 0: 'abcabcabc' at position 0
'          Group 1: 'abc' at position 6
'             Capture 0: 'abc' at position 0
'             Capture 1: 'abc' at position 3
'             Capture 2: 'abc' at position 6
'          Group 2: 'ab' at position 6
'             Capture 0: 'ab' at position 0
'             Capture 1: 'ab' at position 3
'             Capture 2: 'ab' at position 6
'          Group 3: 'b' at position 7
'             Capture 0: 'b' at position 1
'             Capture 1: 'b' at position 4
'             Capture 2: 'b' at position 7
```

L'exemple suivant utilise l'expression régulière `(Abc)+` pour trouver une ou plusieurs occurrences consécutives de la chaîne « Abc » dans la chaîne « XYZAbcAbcAbcXYZAbcAb ». L’exemple montre comment utiliser la propriété [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) pour retourner plusieurs groupes de sous-chaînes capturées.

```csharp
{
   int counter;
   Match m;
   CaptureCollection cc;
   GroupCollection gc;

   // Look for groupings of "Abc".
   Regex r = new Regex("(Abc)+"); 
   // Define the string to search.
   m = r.Match("XYZAbcAbcAbcXYZAbcAb"); 
   gc = m.Groups;

   // Display the number of groups.
   Console.WriteLine("Captured groups = " + gc.Count.ToString());

   // Loop through each group.
   for (int i=0; i < gc.Count; i++) 
   {
      cc = gc[i].Captures;
      counter = cc.Count;

      // Display the number of captures in this group.
      Console.WriteLine("Captures count = " + counter.ToString());

      // Loop through each capture in the group.
      for (int ii = 0; ii < counter; ii++) 
      {
         // Display the capture and its position.
         Console.WriteLine(cc[ii] + "   Starts at character " + 
              cc[ii].Index);
      }
   }
}
// The example displays the following output:
//       Captured groups = 2
//       Captures count = 1
//       AbcAbcAbc   Starts at character 3
//       Captures count = 3
//       Abc   Starts at character 3
//       Abc   Starts at character 6
//       Abc   Starts at character 9  
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "((a(b))c)+"
      Dim input As STring = "abcabcabc"

      Dim match As Match = Regex.Match(input, pattern)
      If match.Success Then
         Console.WriteLine("Match: '{0}' at position {1}", _ 
                           match.Value, match.Index)
         Dim groups As GroupCollection = match.Groups
         For ctr As Integer = 0 To groups.Count - 1
            Console.WriteLine("   Group {0}: '{1}' at position {2}", _
                              ctr, groups(ctr).Value, groups(ctr).Index)
            Dim captures As CaptureCollection = groups(ctr).Captures
            For ctr2 As Integer = 0 To captures.Count - 1
               Console.WriteLine("      Capture {0}: '{1}' at position {2}", _
                                 ctr2, captures(ctr2).Value, captures(ctr2).Index)
            Next
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Match: 'abcabcabc' at position 0
'          Group 0: 'abcabcabc' at position 0
'             Capture 0: 'abcabcabc' at position 0
'          Group 1: 'abc' at position 6
'             Capture 0: 'abc' at position 0
'             Capture 1: 'abc' at position 3
'             Capture 2: 'abc' at position 6
'          Group 2: 'ab' at position 6
'             Capture 0: 'ab' at position 0
'             Capture 1: 'ab' at position 3
'             Capture 2: 'ab' at position 6
'          Group 3: 'b' at position 7
'             Capture 0: 'b' at position 1
'             Capture 1: 'b' at position 4
'             Capture 2: 'b' at position 7
```

## <a name="the-individual-capture"></a>Capture individuelle

La classe [Capture](xref:System.Text.RegularExpressions.Capture) contient le résultat d’une capture de sous-expression unique. La propriété [Capture.Value](xref:System.Text.RegularExpressions.Capture.Value) contient le texte mis en correspondance, tandis que la propriété [Capture.Index](xref:System.Text.RegularExpressions.Capture.Index) indique la position, en base zéro, dans la chaîne d’entrée à laquelle commence la sous-chaîne mise en correspondance. 

L'exemple suivant analyse une chaîne d'entrée pour récupérer la température de certaines villes. Une virgule (« , ») sépare chaque ville de sa température, tandis qu'un point-virgule (« ; ») sépare les données de chaque ville. La chaîne d'entrée entière représente une correspondance unique. Dans le modèle d'expression régulière `((\w+(\s\w+)*),(\d+);)+`, qui permet d'analyser la chaîne, le nom de la ville est affecté au deuxième groupe de capture, tandis que la température est attribuée au quatrième groupe de capture.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "Miami,78;Chicago,62;New York,67;San Francisco,59;Seattle,58;"; 
      string pattern = @"((\w+(\s\w+)*),(\d+);)+";
      Match match = Regex.Match(input, pattern);
      if (match.Success)
      {
         Console.WriteLine("Current temperatures:");
         for (int ctr = 0; ctr < match.Groups[2].Captures.Count; ctr++)
            Console.WriteLine("{0,-20} {1,3}", match.Groups[2].Captures[ctr].Value, 
                              match.Groups[4].Captures[ctr].Value);
      }
   }
}
// The example displays the following output:
//       Current temperatures:
//       Miami                 78
//       Chicago               62
//       New York              67
//       San Francisco         59
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "Miami,78;Chicago,62;New York,67;San Francisco,59;Seattle,58;" 
      Dim pattern As String = "((\w+(\s\w+)*),(\d+);)+"
      Dim match As Match = Regex.Match(input, pattern)
      If match.Success Then
         Console.WriteLine("Current temperatures:")
         For ctr As Integer = 0 To match.Groups(2).Captures.Count - 1
            Console.WriteLine("{0,-20} {1,3}", match.Groups(2).Captures(ctr).Value, _
                              match.Groups(4).Captures(ctr).Value)
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Current temperatures:
'       Miami                 78
'       Chicago               62
'       New York              67
'       San Francisco         59
```

L'expression régulière est définie comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`\w+` | Mettre en correspondance un ou plusieurs caractères alphabétiques.
`(\s\w+)*` | Mettre en correspondance zéro occurrence, ou plus, d'un espace blanc suivi d'un ou plusieurs caractères alphabétiques. Ce modèle met en correspondance les noms de ville composés de plusieurs mots. Il s'agit du troisième groupe de capture.
`(\w+(\s\w+)*)` | Mettre en correspondance un ou plusieurs caractères alphabétiques suivis de zéro occurrence, ou plus, d'un espace blanc et d'un ou plusieurs caractères alphabétiques. Il s'agit du deuxième groupe de capture.
`,` | Mettre en correspondance une virgule.
`(\d+)` | Mettre en correspondance un ou plusieurs chiffres. Il s'agit du quatrième groupe de capture.
`;` | Mettre en correspondance un point-virgule.
`((\w+(\s\w+)*),(\d+);)+` | Mettre en correspondance le modèle représentant un mot suivi d’un nombre quelconque de mots supplémentaires, d’une virgule, d’un ou plusieurs chiffres et d’un point-virgule, une ou plusieurs fois. Il s'agit du premier groupe de capture. 
 
## <a name="see-also"></a>Voir aussi

[System.Text.RegularExpressions](xref:System.Text.RegularExpressions)

[Expressions régulières .NET](regular-expressions.md)

[Langage des expressions régulières - Aide-mémoire](quick-ref.md)




<!--HONumber=Nov16_HO3-->


