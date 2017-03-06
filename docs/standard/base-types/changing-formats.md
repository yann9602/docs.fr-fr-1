---
title: "Exemple d’expression régulière : modification des formats de date"
description: "Exemple d’expression régulière : modification des formats de date"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3e196697-981c-4c1d-93dd-c3b236ef36dd
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f801e8761ad2dfe80915cc4425c359cfae99949e
ms.lasthandoff: 03/02/2017

---

# <a name="regular-expression-example-changing-date-formats"></a>Exemple d’expression régulière : modification des formats de date

L’exemple de code suivant utilise la méthode [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) pour remplacer les dates au format *mm/jj/aa* par des dates au format *jj-mm-aa*.

## <a name="example"></a>Exemple

```csharp
static string MDYToDMY(string input) 
{
   try {
      return Regex.Replace(input, 
            "\\b(?<month>\\d{1,2})/(?<day>\\d{1,2})/(?<year>\\d{2,4})\\b",
            "${day}-${month}-${year}", RegexOptions.None,
            TimeSpan.FromMilliseconds(150));
   }         
   catch (RegexMatchTimeoutException) {
      return input;
   }
}
```

```vb
Function MDYToDMY(input As String) As String
   Try
      Return Regex.Replace(input, _
             "\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b", _
             "${day}-${month}-${year}", RegexOptions.None,
             TimeSpan.FromMilliseconds(150))
    Catch e As RegexMatchTimeoutException
       Return input
    End Try         
End Function
```

Le code suivant montre comment la méthode `MDYToDMY` peut être appelée dans une application. 

```csharp
using System;
using System.Globalization;
using System.Text.RegularExpressions;

public class Class1
{
   public static void Main()
   {
      string dateString = DateTime.Today.ToString("d", 
                                        DateTimeFormatInfo.InvariantInfo);
      string resultString = MDYToDMY(dateString);
      Console.WriteLine("Converted {0} to {1}.", dateString, resultString);
   }

   static string MDYToDMY(string input) 
   {
      try {
         return Regex.Replace(input, 
               "\\b(?<month>\\d{1,2})/(?<day>\\d{1,2})/(?<year>\\d{2,4})\\b",
               "${day}-${month}-${year}", RegexOptions.None,
               TimeSpan.FromMilliseconds(150));
      }         
      catch (RegexMatchTimeoutException) {
         return input;
      }
   }

}
// The example displays the following output to the console if run on 8/21/2007:
//      Converted 08/21/2007 to 21-08-2007.
```

```vb
Imports System.Globalization
Imports System.Text.RegularExpressions

Module DateFormatReplacement
   Public Sub Main()
      Dim dateString As String = Date.Today.ToString("d", _
                                           DateTimeFormatInfo.InvariantInfo)
      Dim resultString As String = MDYToDMY(dateString)
      Console.WriteLine("Converted {0} to {1}.", dateString, resultString)
   End Sub

    Function MDYToDMY(input As String) As String
       Try
          Return Regex.Replace(input, _
                 "\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b", _
                 "${day}-${month}-${year}", RegexOptions.None,
                 TimeSpan.FromMilliseconds(150))
        Catch e As RegexMatchTimeoutException
           Return input
        End Try         
    End Function
End Module
' The example displays the following output to the console if run on 8/21/2007:
'      Converted 08/21/2007 to 21-08-2007.
```

## <a name="comments"></a>Commentaires

Le modèle d'expression régulière `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` est interprété comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`\b` | Commencer la correspondance à la limite d'un mot.
`(?<month>\d{1,2})` | Mettre en correspondance un ou deux chiffres décimaux. Il s’agit du groupe capturé `month`.
`/` | Mettre en correspondance la barre oblique.
`(?<day>\d{1,2})` | Mettre en correspondance un ou deux chiffres décimaux. Il s’agit du groupe capturé `day`.
`/` | Mettre en correspondance la barre oblique.
`(?<year>\d{2,4})` | Mettre en correspondance de deux à quatre chiffres décimaux. Il s’agit du groupe capturé `year`.
`\b` | Terminer la correspondance à la limite d'un mot.
 
Le modèle `${day}-${month}-${year}` définit la chaîne de remplacement comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`$(day)` | Ajouter la chaîne capturée par le groupe de capture `day`.
`-` | Ajouter un trait d’union.
`$(month)` | Ajouter la chaîne capturée par le groupe de capture `month`.
`-` | Ajouter un trait d’union.
`$(year)` | Ajouter la chaîne capturée par le groupe de capture `year`.
 
## <a name="see-also"></a>Voir aussi

[Expressions régulières .NET](regular-expressions.md)

[Exemples d’expressions régulières](regex-examples.md)

