---
title: "Constructions diverses dans les expressions régulières"
description: "Constructions diverses dans les expressions régulières"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 478901dc-db6c-4d90-9d3b-f5cfdca2cbf5
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 4205d2a318849a7b24ac0f1fd65f7e8a23ec7f55

---

# <a name="miscellaneous-constructs-in-regular-expressions"></a>Constructions diverses dans les expressions régulières


Les expressions régulières dans .NET incluent trois constructions de langage diverses. L’une d’elles vous permet d’activer ou de désactiver des options de mise en correspondance particulières au milieu d’un modèle d’expression régulière. Grâce aux deux autres, vous pouvez inclure des commentaires dans une expression régulière.

## <a name="inline-options"></a>Options inline

Vous pouvez définir ou désactiver des options de mise en correspondance de modèle spécifiques pour une partie d’une expression régulière en utilisant la syntaxe suivante :

```
(?imnsx-imnsx)
```

Vous répertoriez les options à activer après le point d’interrogation et les options à désactiver après le signe moins. Le tableau suivant décrit chaque option. Pour plus d’informations sur chaque option, consultez [Options des expressions régulières](options.md).

Option | Description
------ | ----------- 
**i** | Correspondance qui ne respecte pas la casse.
**m** | Mode multiligne.
**n** | Captures explicites uniquement. (Les parenthèses ne font pas office de groupes de capture.)
**s** | Mode à ligne simple.
**x** | Ignorer un espace blanc sans séquence d’échappement et autoriser les commentaires en mode x. 
 
Toute modification des options d’expression régulière définies par la construction **(?imnsx-imnsx)** reste en vigueur jusqu’à la fin du groupe englobant.

> [!NOTE]
> La construction de regroupement **(?imnsx-imnsx**:_sous-expression_**)** fournit une fonctionnalité identique pour une sous-expression. Pour plus d’informations, consultez [Constructions de regroupement dans les expressions régulières](grouping.md).
 
L’exemple suivant utilise les options **i**, **n** et **x** pour activer le non-respect de la casse et les captures explicites, et pour ignorer l’espace blanc dans le modèle d’expression régulière au milieu d’une expression régulière. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern; 
      string input = "double dare double Double a Drooling dog The Dreaded Deep";

      pattern = @"\b(D\w+)\s(d\w+)\b";
      // Match pattern using default options.
      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine(match.Value);
         if (match.Groups.Count > 1)
            for (int ctr = 1; ctr < match.Groups.Count; ctr++) 
               Console.WriteLine("   Group {0}: {1}", ctr, match.Groups[ctr].Value);
      }
      Console.WriteLine();

      // Change regular expression pattern to include options.
      pattern = @"\b(D\w+)(?ixn) \s (d\w+) \b";
      // Match new pattern with options. 
      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine(match.Value);
         if (match.Groups.Count > 1)
            for (int ctr = 1; ctr < match.Groups.Count; ctr++) 
               Console.WriteLine("   Group {0}: '{1}'", ctr, match.Groups[ctr].Value);
      }
   }
}
// The example displays the following output:
//       Drooling dog
//          Group 1: Drooling
//          Group 2: dog
//       
//       Drooling dog
//          Group 1: 'Drooling'
//       Dreaded Deep
//          Group 1: 'Dreaded'
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String 
      Dim input As String = "double dare double Double a Drooling dog The Dreaded Deep"

      pattern = "\b(D\w+)\s(d\w+)\b"
      ' Match pattern using default options.
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
         If match.Groups.Count > 1 Then
            For ctr As Integer = 1 To match.Groups.Count - 1 
               Console.WriteLine("   Group {0}: {1}", ctr, match.Groups(ctr).Value)
            Next
         End If
      Next
      Console.WriteLine()

      ' Change regular expression pattern to include options.
      pattern = "\b(D\w+)(?ixn) \s (d\w+) \b"
      ' Match new pattern with options. 
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
         If match.Groups.Count > 1 Then
            For ctr As Integer = 1 To match.Groups.Count - 1 
               Console.WriteLine("   Group {0}: '{1}'", ctr, match.Groups(ctr).Value)
            Next
         End If
      Next
   End Sub
End Module
' The example displays the following output:
'       Drooling dog
'          Group 1: Drooling
'          Group 2: dog
'       
'       Drooling dog
'          Group 1: 'Drooling'
'       Dreaded Deep
'          Group 1: 'Dreaded'
```

L’exemple définit deux expressions régulières. La première, `\b(D\w+)\s(d\w+)\b`, correspond à deux mots consécutifs qui commencent par un « D » majuscule et un « d » minuscule. La seconde expression régulière, `\b(D\w+)(?ixn) \s (d\w+) \b`, utilise des options inline pour modifier ce modèle, comme décrit dans le tableau suivant. Une comparaison des résultats confirme l’effet de la construction `(?ixn)`.

Modèle | Description
------- | ----------- 
`\b` | Commencer à la limite d'un mot.
`(D\w+)` | Mettre en correspondance un « D » majuscule suivi d’un ou de plusieurs caractères alphabétiques. Il s’agit du premier groupe de capture.
`(?ixn)` | À partir de ce point, effectuer des comparaisons sans respect de la casse, effectuer seulement des captures explicites et ignorer l’espace blanc dans le modèle d’expression régulière.
`\s` | Mettre en correspondance un espace blanc.
`(d\w+)` | Mettre en correspondance un « d » majuscule ou minuscule suivi d’un ou de plusieurs caractères alphabétiques. Ce groupe n’est pas capturé, car l’option n (capture explicite) a été activée.
`\b` | Mettre en correspondance la limite d'un mot.
 
## <a name="inline-comment"></a>Commentaire inline

La construction **(?#** _commentaire_**)** vous permet d’inclure un commentaire inline dans une expression régulière. Le moteur d’expression régulière n’utilise aucune partie du commentaire dans la mise en correspondance du modèle, bien que le commentaire soit inclus dans la chaîne retournée par la méthode [Regex.ToString](xref:System.Text.RegularExpressions.Regex.Unescape(System.String)). Le commentaire se termine à la première parenthèse fermante.

L’exemple suivant répète le premier modèle d’expression régulière de l’exemple de la section précédente. Il ajoute deux commentaires inline à l’expression régulière pour indiquer si la comparaison respecte la casse. Le modèle d’expression régulière, `\b((?# case-sensitive comparison)D\w+)\s((?#case-insensitive comparison)d\w+)\b`, est défini comme suit.

Modèle | Description
------- | ----------- 
`\b` | Commencer à la limite d'un mot.
`(?# case-sensitive comparison)` | Un commentaire. Il n’affecte pas le comportement de mise correspondance du modèle.
`(D\w+)` | Mettre en correspondance un « D » majuscule suivi d’un ou de plusieurs caractères alphabétiques. Il s'agit du premier groupe de capture.
`\s` | Mettre en correspondance un espace blanc.
`(?ixn)` |À partir de ce point, effectuer des comparaisons sans respect de la casse, effectuer seulement des captures explicites et ignorer l’espace blanc dans le modèle d’expression régulière.
`(?#case-insensitive comparison)` | Un commentaire. Il n’affecte pas le comportement de mise correspondance du modèle. 
`(d\w+)` | Mettre en correspondance un « d » majuscule ou minuscule suivi d’un ou de plusieurs caractères alphabétiques. Il s’agit du deuxième groupe de capture.
`\b` | Mettre en correspondance la limite d'un mot.
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b((?# case sensitive comparison)D\w+)\s(?ixn)((?#case insensitive comparison)d\w+)\b";
      Regex rgx = new Regex(pattern);
      string input = "double dare double Double a Drooling dog The Dreaded Deep";

      Console.WriteLine("Pattern: " + pattern.ToString());
      // Match pattern using default options.
      foreach (Match match in rgx.Matches(input))
      {
         Console.WriteLine(match.Value);
         if (match.Groups.Count > 1)
         {
            for (int ctr = 1; ctr <match.Groups.Count; ctr++) 
               Console.WriteLine("   Group {0}: {1}", ctr, match.Groups[ctr].Value);
         }
      }
   }
}
// The example displays the following output:
//    Pattern: \b((?# case sensitive comparison)D\w+)\s(?ixn)((?#case insensitive comp
//    arison)d\w+)\b
//    Drooling dog
//       Group 1: Drooling
//    Dreaded Deep
//       Group 1: Dreaded
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b((?# case sensitive comparison)D\w+)\s(?ixn)((?#case insensitive comparison)d\w+)\b"
      Dim rgx As New Regex(pattern)
      Dim input As String = "double dare double Double a Drooling dog The Dreaded Deep"

      Console.WriteLine("Pattern: " + pattern.ToString())
      ' Match pattern using default options.
      For Each match As Match In rgx.Matches(input)
         Console.WriteLine(match.Value)
         If match.Groups.Count > 1 Then
            For ctr As Integer = 1 To match.Groups.Count - 1 
               Console.WriteLine("   Group {0}: {1}", ctr, match.Groups(ctr).Value)
            Next
         End If
      Next
   End Sub
End Module
' The example displays the following output:
'    Pattern: \b((?# case sensitive comparison)D\w+)\s(?ixn)((?#case insensitive comp
'    arison)d\w+)\b
'    Drooling dog
'       Group 1: Drooling
'    Dreaded Deep
'       Group 1: Dreaded
```

## <a name="end-of-line-comment"></a>Commentaire de fin de ligne

Un signe dièse (**#**) marque un commentaire en mode x, lequel démarre au caractère # sans séquence d’échappement à la fin du modèle d’expression régulière et continue jusqu’à la fin de la ligne. Pour utiliser cette construction, vous devez activer l’option **x** (par le biais d’options inline) ou fournir la valeur [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) au paramètre *option* au moment de l’instanciation de l’objet [Regex](xref:System.Text.RegularExpressions.Regex) ou de l’appel de la méthode [Regex](xref:System.Text.RegularExpressions.Regex) statique. 

L’exemple suivant illustre la construction du commentaire de fin de ligne. Il détermine si une chaîne est une chaîne de format composite qui inclut au moins un élément de format. Le tableau suivant décrit les constructions dans le modèle d’expression régulière : 

`\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item`. 

Modèle | Description
------- | ----------- 
`\{` | Mettre en correspondance une accolade ouvrante.
`\d+` | Mettre en correspondance un ou plusieurs chiffres décimaux.
`(,-*\d+)*` | Mettre en correspondance zéro ou une occurrence d’une virgule, suivie d’un signe moins facultatif, suivi par un ou plusieurs chiffres décimaux.
`(\:\w{1,4}?)*` | Mettre en correspondance zéro ou une occurrence d’un signe deux-points, suivi par un à quatre espaces blancs, mais le moins possible.
`(?#case insensitive comparison)` | Un commentaire inline. Il n’a aucun effet sur le comportement de la mise en correspondance du modèle.
`\}` | Mettre en correspondance une accolade fermante.
`(?x)` | Activer l’option permettant d’ignorer l’espace blanc dans le modèle, afin que le commentaire de fin de ligne soit reconnu.
`# Looks for a composite format item.` | Un commentaire de fin de ligne.
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.";
      string input = "{0,-3:F}";
      Console.WriteLine("'{0}':", input);
      if (Regex.IsMatch(input, pattern))
         Console.WriteLine("   contains a composite format item.");
      else
         Console.WriteLine("   does not contain a composite format item.");
   }
}
// The example displays the following output:
//       '{0,-3:F}':
//          contains a composite format item.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item."
      Dim input As String = "{0,-3:F}"
      Console.WriteLine("'{0}':", input)
      If Regex.IsMatch(input, pattern) Then
         Console.WriteLine("   contains a composite format item.")
      Else
         Console.WriteLine("   does not contain a composite format item.")
      End If
   End Sub
End Module
' The example displays the following output:
'       '{0,-3:F}':
'          contains a composite format item.
```

Notez que, au lieu de fournir la construction `(?x)` dans l’expression régulière, le commentaire aurait également pu être reconnu en appelant la méthode [Regex.IsMatch(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) et en lui passant la valeur d’énumération [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace).

## <a name="see-also"></a>Voir aussi

[Langage des expressions régulières - Aide-mémoire](quick-ref.md)




<!--HONumber=Nov16_HO3-->


