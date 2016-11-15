---
title: "Exemple d’expression régulière : recherche de valeurs HREF"
description: "Exemple d’expression régulière : recherche de valeurs HREF"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: d6484880-bdac-47cd-b5e5-9419c9ed14cd
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 8951e4ca82c0148bae7e8279681920ffabb523be

---

# <a name="regular-expression-example-scanning-for-hrefs"></a>Exemple d’expression régulière : recherche de valeurs HREF

L’exemple suivant recherche une chaîne d’entrée et affiche toutes les valeurs href="…" et leurs emplacements dans la chaîne. 

## <a name="the-regex-object"></a>Objet Regex

Étant donné que la méthode `DumpHRefs` peut être appelée plusieurs fois à partir du code utilisateur, la méthode `static` [Regex.Match(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) est utilisée. Ainsi, le moteur d’expression régulière peut mettre en cache l’expression régulière et éviter le traitement de l’instanciation d’un nouvel objet [Regex](xref:System.Text.RegularExpressions.Regex) chaque fois que la méthode est appelée. Un objet [Match](xref:System.Text.RegularExpressions.Match) est alors utilisé pour effectuer une itération dans toutes les correspondances dans la chaîne. 

```csharp
private static void DumpHRefs(string inputString) 
{
   Match m;
   string HRefPattern = "href\\s*=\\s*(?:[\"'](?<1>[^\"']*)[\"']|(?<1>\\S+))";

   try {
      m = Regex.Match(inputString, HRefPattern, 
                      RegexOptions.IgnoreCase | RegexOptions.Compiled, 
                      TimeSpan.FromSeconds(1));
      while (m.Success)
      {
         Console.WriteLine("Found href " + m.Groups[1] + " at " 
            + m.Groups[1].Index);
         m = m.NextMatch();
      }   
   }
   catch (RegexMatchTimeoutException) {
      Console.WriteLine("The matching operation timed out.");
   }
}
```

```vb
Private Sub DumpHRefs(inputString As String) 
   Dim m As Match
   Dim HRefPattern As String = "href\s*=\s*(?:[""'](?<1>[^""']*)[""']|(?<1>\S+))"

   Try
      m = Regex.Match(inputString, HRefPattern, _ 
                      RegexOptions.IgnoreCase Or RegexOptions.Compiled,
                      TimeSpan.FromSeconds(1))
      Do While m.Success
         Console.WriteLine("Found href {0} at {1}.", _
                           m.Groups(1), m.Groups(1).Index)
         m = m.NextMatch()
      Loop   
   Catch e As RegexMatchTimeoutException
      Console.WriteLine("The matching operation timed out.")
   End Try
End Sub
```

L’exemple suivant illustre un appel à la méthode `DumpHRefs`.

```csharp
public static void Main()
{
   string inputString = "My favorite web sites include:</P>" +
                        "<A HREF=\"http://msdn2.microsoft.com\">" +
                        "MSDN Home Page</A></P>" +
                        "<A HREF=\"http://www.microsoft.com\">" +
                        "Microsoft Corporation Home Page</A></P>" +
                        "<A HREF=\"http://blogs.msdn.com/bclteam\">" +
                        ".NET Base Class Library blog</A></P>";
   DumpHRefs(inputString);                     

}
// The example displays the following output:
//       Found href http://msdn2.microsoft.com at 43
//       Found href http://www.microsoft.com at 102
//       Found href http://blogs.msdn.com/bclteam at 176
```

```vb
Public Sub Main()
   Dim inputString As String = "My favorite web sites include:</P>" & _
                               "<A HREF=""http://msdn2.microsoft.com"">" & _
                               "MSDN Home Page</A></P>" & _
                               "<A HREF=""http://www.microsoft.com"">" & _
                               "Microsoft Corporation Home Page</A></P>" & _
                               "<A HREF=""http://blogs.msdn.com/bclteam"">" & _
                               ".NET Base Class Library blog</A></P>"
   DumpHRefs(inputString)                     
End Sub
' The example displays the following output:
'       Found href http://msdn2.microsoft.com at 43
'       Found href http://www.microsoft.com at 102
'       Found href http://blogs.msdn.com/bclteam/) at 176
```

Le modèle d'expression régulière `href\s*=\s*(?:["']&#40;?<1>[^"']*)["']|(?<1>\S+))` est interprété comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`href` | Correspond à la chaîne littérale « href ». La recherche de correspondance ne respecte pas la casse.
`\s*` | Correspond à zéro, un ou plusieurs espaces blancs.
`=` |Correspond au signe égal.
`\s*` | Correspond à zéro, un ou plusieurs espaces blancs.
`(?:["']&#40;?<1>[^"']*)"&#124;(?<1>\S+))` | Correspond à l’un des éléments suivants sans assigner le résultat à un groupe capturé : un guillemet ou une apostrophe, suivi(e) de zéro, une ou plusieurs occurrences de tout caractère autre qu’un guillemet ou une apostrophe, suivie(s) d’un guillemet ou une apostrophe. Le groupe nommé `1` est inclus dans ce modèle. -ou- Un ou plusieurs caractères autres que des espaces blancs. Le groupe nommé `1` est inclus dans ce modèle.
`(?<1>[^"']*)` | Affecte zéro, une ou plusieurs occurrences de tout caractère autre qu’un guillemet ou une apostrophe au groupe de capture nommé `1`.
`"(?<1>\S+)` | Affecte un ou plusieurs caractères non espace blanc au groupe de capture nommé `1`.
 
## <a name="match-result-class"></a>Classe de résultats Match

Les résultats d’une recherche sont stockés dans la classe [Match](xref:System.Text.RegularExpressions.Match), qui donne accès à toutes les sous-chaînes extraites par la recherche. Cette classe mémorise également la chaîne recherchée et l’expression régulière utilisée, pour pouvoir appeler la méthode [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) afin d’effectuer une nouvelle recherche qui commence là où la dernière s’est terminée.

## <a name="explicitly-named-captures"></a>Captures explicitement nommées

Dans les expressions régulières classiques, les parenthèses de capture sont automatiquement numérotées dans l’ordre. Cela génère deux problèmes. Tout d’abord, si une expression régulière est modifiée par l’insertion ou la suppression d’un jeu de parenthèses, tout code qui fait référence aux captures numérotées doit être réécrit pour refléter la nouvelle numérotation. Ensuite, étant donné que différents jeux de parenthèses sont souvent utilisés pour fournir deux expressions différentes pour une correspondance acceptable, il peut s’avérer difficile de déterminer laquelle des deux expressions en fait retourné un résultat.

Pour résoudre ces problèmes, la classe [Regex](xref:System.Text.RegularExpressions.Regex) prend en charge la syntaxe `(?<name>…)` pour capturer une correspondance dans un emplacement spécifié (l’emplacement peut être nommé à l’aide d’une chaîne ou d’un entier ; les entiers peuvent être rappelés plus rapidement). Ainsi, les autres correspondances de la même chaîne peuvent toutes être dirigées vers le même emplacement. En cas de conflit, la dernière correspondance placée dans un emplacement est la correspondance correcte. (Toutefois, la liste complète des différentes correspondances pour un seul emplacement est disponible. Consultez la collection [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) pour plus d’informations.)

## <a name="see-also"></a>Voir aussi

[Expressions régulières .NET](regular-expressions.md)

[Exemples d’expressions régulières](regex-examples.md)




<!--HONumber=Nov16_HO1-->


