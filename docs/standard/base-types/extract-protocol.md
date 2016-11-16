---
title: "Guide pratique : extraire un protocole et un numéro de port d’une URL"
description: "Guide pratique pour extraire un protocole et un numéro de port d’une URL"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: d2462fb4-6d61-44ab-8466-73f1f06c3058
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 9c86a77271ac0b239e92f415bd7b26d51d762dd8

---

# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Guide pratique : extraire un protocole et un numéro de port d’une URL

L’exemple suivant montre comment extraire un protocole et un numéro de port d’une URL. 

## <a name="example"></a>Exemple

L’exemple utilise la méthode [Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)) pour retourner le protocole, suivi d’un signe deux-points, lui-même suivi du numéro de port. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string url = "http://www.contoso.com:8080/letters/readme";

      Regex r = new Regex(@"^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/",
                          RegexOptions.None, TimeSpan.FromMilliseconds(150));
      Match m = r.Match(url);
      if (m.Success)
         Console.WriteLine(r.Match(url).Result("${proto}${port}")); 
   }
}
// The example displays the following output:
//       http:8080
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim url As String = "http://www.contoso.com:8080/letters/readme.html" 
      Dim r As New Regex("^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/",
                         RegexOptions.None, TimeSpan.FromMilliseconds(150))

      Dim m As Match = r.Match(url)
      If m.Success Then
         Console.WriteLine(r.Match(url).Result("${proto}${port}"))
      End If   
   End Sub
End Module
' The example displays the following output:
'       http:8080
```

Le modèle d’expression régulière `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` peut être interprété comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`^` | Commence la recherche de correspondance au début de la chaîne.
`(?<proto>\w+)` | Mettre en correspondance un ou plusieurs caractères alphabétiques. Nommer ce groupe « proto ».
`://` | Mettre en correspondance un signe deux-points suivi de deux barres obliques.
`[^/]+?` | Mettre en correspondance une ou plusieurs occurrences (mais le moins possible) de tout caractère autre qu’une barre oblique.
`(?<port>:\d+)?` | Mettre en correspondance zéro ou une occurrence d’un signe deux-points suivi d’un ou de plusieurs caractères de chiffre. Nommer ce groupe « port ».
`/` | Mettre en correspondance une barre oblique.
 
La méthode [Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)) étend la séquence de remplacement `${proto}${port}`, qui concatène la valeur des deux groupes nommés capturés dans le modèle d’expression régulière. Elle est plus pratique que la concaténation explicite des chaînes récupérées de l’objet de collection retourné par la propriété [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups).

L’exemple utilise la méthode [Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)) avec deux substitutions, `${proto}` et `${port}`, pour inclure les groupes capturés dans la chaîne de sortie. Vous pouvez à la place récupérer les groupes capturés de l’objet [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) de la mise en correspondance, comme le montre le code suivant.

```csharp
Console.WriteLine(m.Groups["proto"].Value + m.Groups["port"].Value); 
```

```vb
Console.WriteLine(m.Groups("proto").Value + m.Groups("port").Value)
```

## <a name="see-also"></a>Voir aussi

[Expressions régulières .NET](regular-expressions.md)

[Exemples d’expressions régulières](regex-examples.md)



<!--HONumber=Nov16_HO1-->


