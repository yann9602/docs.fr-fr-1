---
title: "Classes de caractères dans les expressions régulières"
description: "Classes de caractères dans les expressions régulières"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: c7a9305f-7144-4fe8-80e8-a727bf7d223f
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: f8ebb1db670669e2e8666cd5ef90f72237c105e4

---

# <a name="character-classes-in-regular-expressions"></a>Classes de caractères dans les expressions régulières

Une classe de caractères définit un jeu de caractères, chacun d'entre eux pouvant apparaître dans une chaîne d'entrée pour aboutir à une correspondance. Le langage d’expression régulière dans .NET prend en charge les classes de caractères suivantes :

* Groupes de caractères positifs. Un caractère de la chaîne d'entrée doit correspondre à l'un des jeux de caractères spécifié. Pour plus d’informations, consultez [Groupe de caractères positif](#positive-character-group--).

* Groupes de caractères négatifs. Un caractère de la chaîne d'entrée ne doit pas correspondre à l'un des jeux de caractères spécifié. Pour plus d’informations, consultez [Groupe de caractères négatif](#negative-character-group-).

* N'importe quel caractère. Le fichier caractère . (point) inclus dans une expression régulière est un caractère générique qui correspond à n’importe quel caractère sauf **\n**. Pour plus d’informations, consultez [N’importe quel caractère](#any-character-). 

* Catégorie Unicode générale ou bloc nommé. Un caractère de la chaîne d'entrée doit être membre d'une catégorie Unicode particulière ou doit figurer dans une plage contiguë de caractères Unicode pour aboutir à une correspondance. Pour plus d’informations, consultez [Catégorie Unicode ou bloc Unicode](#unicode-category-or-unicode-block-p).

* Catégorie Unicode générale négative ou bloc nommé. Un caractère de la chaîne d'entrée ne doit pas être membre d'une catégorie Unicode particulière ou ne doit pas figurer dans une plage contiguë de caractères Unicode pour aboutir à une correspondance. Pour plus d’informations, consultez [Catégorie ou bloc Unicode négatifs](#negative-unicode-category-or-unicode-block-p).

* Caractère de mot. Un caractère de la chaîne d'entrée peut appartenir à l'une des catégories Unicode appropriées aux caractères contenus dans les mots. Pour plus d’informations, consultez [Caractère de mot](#word-character-w).

* Caractère autre qu'un caractère de mot. Un caractère de la chaîne d'entrée peut appartenir à n'importe quelle catégorie Unicode qui n'est pas un caractère de mot. Pour plus d’informations, consultez [Caractère autre qu’un caractère de mot](#non-word-character-w).

* Espace blanc. Un caractère de la chaîne d'entrée peut être n'importe quel caractère Unicode de séparation, ainsi que n'importe quel nombre de caractères de contrôle. Pour plus d’informations, consultez [Espace blanc](#white-space-character-s).

* Caractère autre qu'un espace blanc. Un caractère de la chaîne d'entrée peut être n'importe quel caractère qui n'est pas un espace blanc. Pour plus d’informations, consultez [Caractère autre qu’un espace blanc](#non-white-space-character-s).

* Chiffre décimal. Un caractère de la chaîne d'entrée peut être n'importe quel nombre de caractères classifiés en tant que chiffres décimaux Unicode. Pour plus d’informations, consultez [Chiffre décimal](#decimal-digit-character-d).

* Chiffre non décimal. Un caractère de la chaîne d'entrée peut correspondre à autre chose qu'un chiffre décimal Unicode. Pour plus d’informations, consultez [Chiffre non décimal](#non-digit-character-d).


.NET prend en charge les expressions de soustraction de classe de caractères, ce qui vous permet de définir un jeu de caractères comme résultat de l’exclusion d’une classe de caractères d’une autre classe de caractères. Pour plus d’informations, consultez [Soustraction de classe de caractères](#character-class-subtraction).

## <a name="positive-character-group-"></a>Groupe de caractères positif : [ ]

Un groupe de caractères positif spécifie une liste de caractères, chacun d'entre eux pouvant apparaître dans une chaîne d'entrée pour produire une correspondance. Cette liste de caractères peut être spécifiée individuellement, comme une plage, ou les deux à la fois. 

La syntaxe de la spécification d'une liste de différents caractères est comme suit : 

[*groupe*_*caractères*]

où *groupe_caractères* est la liste des différents caractères pouvant apparaître dans la chaîne d’entrée pour qu’une correspondance soit établie. *groupe*_*caractères* peut être constitué de n’importe quelle combinaison d’un ou de plusieurs caractères littéraux, de [caractères d’échappement](escapes.md) ou de classes de caractères. 

La syntaxe de la spécification d'une plage de caractères est comme suit :

```
[firstCharacter-lastCharacter]
```

où *premierCaractère* est le caractère qui commence la plage et *dernierCaractère* est celui qui la termine. Une plage de caractères est une série contiguë de caractères définie par la spécification du premier caractère de la série, d'un trait d'union (-), puis du dernier caractère de la série. Deux caractères sont contigus s'ils présentent des points de code Unicode adjacents.

Quelques modèles d'expressions régulières courants qui contiennent des classes de caractères positifs apparaissent dans le tableau suivant.

Motif | Description
------- | ----------- 
`[aeiou]` | Mettre en correspondance toutes les voyelles.
`[\p{P}\d]` | Mettre en correspondance tous les signes de ponctuation et chiffres décimaux.
`[\s\p{P}]` | Mettre en correspondance tous les espaces blancs et signes de ponctuation.
 
L'exemple suivant définit un groupe de caractères positif qui contient les caractères « a » et « e » afin que la chaîne d'entrée contienne les mots « grey » ou « gray » suivis par un autre mot pour produire une correspondance.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"gr[ae]y\s\S+?[\s\p{P}]";
      string input = "The gray wolf jumped over the grey wall.";
      MatchCollection matches = Regex.Matches(input, pattern);
      foreach (Match match in matches)
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       gray wolf
//       grey wall.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "gr[ae]y\s\S+?[\s\p{P}]"
      Dim input As String = "The gray wolf jumped over the grey wall."
      Dim matches As MatchCollection = Regex.Matches(input, pattern)
      For Each match As Match In matches
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       gray wolf
'       grey wall.
```

L'expression régulière `gr[ae]y\s\S+?[\s|\p{P}]` est définie comme suit :

Motif | Description
------- | ----------- 
`gr` | Mettre en correspondance les caractères littéraux « gr ».
`[ae]` | Mettre en correspondance un « a » ou un « e ».
`y\s` | Mettre en correspondance le caractère littéral « y » suivi d'un espace blanc.
`\S+?` | Mettre en correspondance un ou plusieurs caractères autres que des espaces blancs, mais le moins possible.
`[\s\p{P}]` | Mettre en correspondance un espace blanc ou un signe de ponctuation.
 
L'exemple suivant correspond aux mots qui commencent par une majuscule. Il utilise la sous-expression `[A-Z]` pour représenter la plage de majuscules de A à Z. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b[A-Z]\w*\b";
      string input = "A city Albany Zulu maritime Marseilles";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       A
//       Albany
//       Zulu
//       Marseilles
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b[A-Z]\w*\b"
      Dim input As String = "A city Albany Zulu maritime Marseilles"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
```

L'expression régulière `\b[A-Z]\w*\b` est définie comme indiqué dans le tableau suivant.

Motif | Description
------- | ----------- 
`\b` | Commencer à la limite d'un mot.
`[A-Z]` | Mettre en correspondance une majuscule de A à Z.
`\w*` | Mettre en correspondance zéro, un ou plusieurs caractères alphabétiques.
`\b` | Mettre en correspondance la limite d'un mot.

## <a name="negative-character-group-"></a>Groupe de caractères négatif : [^]

Un groupe de caractères négatifs spécifie une liste de caractères qui ne doivent pas s'afficher dans une chaîne d'entrée pour produire une correspondance. La liste de caractères peut être spécifiée individuellement, comme une plage, ou les deux à la fois. 

La syntaxe de la spécification d'une liste de différents caractères est comme suit :

[^*groupe*_*caractères*]

où *groupe_caractères* est la liste des différents caractères qui ne peuvent pas apparaître dans la chaîne d’entrée pour qu’une correspondance soit établie. *groupe*_*caractères* peut être constitué de n’importe quelle combinaison d’un ou de plusieurs caractères littéraux, de [caractères d’échappement](escapes.md) ou de classes de caractères. 

La syntaxe de la spécification d'une plage de caractères est comme suit :

[^*premierCaractère-dernierCaractère*]

où *premierCaractère* est le caractère qui commence la plage et *dernierCaractère* est celui qui la termine. Une plage de caractères est une série contiguë de caractères définie par la spécification du premier caractère de la série, d'un trait d'union (-), puis du dernier caractère de la série. Deux caractères sont contigus s'ils présentent des points de code Unicode adjacents.

Deux ou plusieurs plages de caractères peuvent être concaténées. Par exemple, pour spécifier la plage de chiffres décimaux de « 0 » à « 9 », la plage de lettres minuscules de « a » à « f » et la plage de lettres majuscules de « A » à « F », utilisez `[0-9a-fA-F]`.

Le premier caret (^) d’un groupe de caractères négatif est obligatoire et indique que le groupe de caractères est un groupe de caractères négatif et non positif.

> [!IMPORTANT]
> Un groupe de caractères négatifs d’un plus grand modèle d’expressions régulières n’est pas une assertion de largeur nulle. Autrement dit, après avoir évalué le groupe de caractères négatif, le moteur des expressions régulières avance d'un caractère dans la chaîne d'entrée.

Quelques modèles d'expressions régulières courants qui contiennent des groupes de caractères négatifs apparaissent dans le tableau suivant.

Motif | Description
------- | ----------- 
`[^aeiou]` | Mettre en correspondance tous les caractères, à l'exception des voyelles.
`[^\p{P}\d]` | Mettre en correspondance tous les caractères, à l'exception des signes de ponctuation et des chiffres décimaux.
 
L'exemple suivant correspond à un mot commençant par les caractères « th » et n'étant pas suivi d'un « o ». 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\bth[^o]\w+\b";
      string input = "thought thing though them through thus thorough this";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       thing
//       them
//       through
//       thus
//       this
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\bth[^o]\w+\b"
      Dim input As String = "thought thing though them through thus " + _
                            "thorough this"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       thing
'       them
'       through
'       thus
'       this
```

L'expression régulière `\bth[^o]\w+\b` est définie comme indiqué dans le tableau suivant.

Motif | Description
------- | ----------- 
`\b` | Commencer à la limite d'un mot.
`th` | Mettre en correspondance les caractères littéraux « th ».
`[^o]` | Mettre en correspondance n'importe quel caractère autre que « o ».
`\w+` | Mettre en correspondance un ou plusieurs caractères alphabétiques.
`\b` | Terminer à une limite de mot.

## <a name="any-character-"></a>N’importe quel caractère : .

Le point (.) correspond à n’importe quel caractère à l’exception de **\n** (caractère de saut de ligne, **\u000A**), avec les deux qualifications suivantes :

* Si un modèle d’expression régulière est modifié par l’option [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline), ou si la partie du modèle qui contient la classe de caractères . est modifiée par l’option **s**, . correspond à n’importe quel caractère. Pour plus d’informations, consultez [Options des expressions régulières](options.md).

  L’exemple suivant illustre le comportement différent de la classe de caractères . par défaut avec l’option [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline). L'expression régulière `^.+` commence au début de la chaîne et correspond à tous les caractères. Par défaut, la correspondance se termine à la fin de la première ligne ; le modèle d’expression régulière correspond au retour chariot, **\r** ou **\u000D**, mais il ne correspond pas à **\n**. Étant donné que l’option [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) interprète la chaîne d’entrée entière comme une ligne unique, il correspond à chaque caractère de la chaîne d’entrée, notamment **\n**.

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

  > [!NOTE]
  > Étant donné qu’elle correspond à n’importe quel caractère sauf **\n**, la classe de caractères . correspond également à **\r** (retour chariot, **\u000D**).
 
* Dans un groupe de caractères négatif ou positif, un point est traité comme un caractère littéral de point, et non pas comme une classe de caractères. Pour plus d’informations, consultez [Groupe de caractères positif](#positive-character-group--) ou [Groupe de caractères négatif](#negative-character-group-) plus haut dans cette rubrique. L’exemple suivant en propose une illustration. Il définit une expression régulière qui inclut le point (**.**) à la fois comme classe de caractères et comme membre d’un groupe de caractères positif. L'expression régulière `\b.*[.?!;:](\s|\z)` commence à une limite de mot, correspond à n'importe quel caractère tant qu'elle ne rencontre pas un des quatre signes de ponctuation, y compris le point, puis correspond à un espace blanc ou à la fin de la chaîne.

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     public static void Main()
     {
        string pattern = @"\b.*[.?!;:](\s|\z)";
        string input = "this. what: is? go, thing.";
        foreach (Match match in Regex.Matches(input, pattern))
           Console.WriteLine(match.Value);
     }
  }
  // The example displays the following output:
  //       this. what: is? go, thing.
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim pattern As STring = "\b.*[.?!;:](\s|\z)"
        Dim input As String = "this. what: is? go, thing."
        For Each match As Match In Regex.Matches(input, pattern)
           Console.WriteLine(match.Value)
        Next   
     End Sub
  End Module
  ' The example displays the following output:
  '       this. what: is? go, thing.
  ```

  > [!NOTE]
  > Étant donné qu’il correspond à n’importe quel caractère, l’élément de langage . est souvent utilisé avec un quantificateur paresseux si un modèle d’expression régulière essaie de correspondre plusieurs fois à n’importe quel caractère. Pour plus d’informations, consultez [Quantificateurs dans les expressions régulières](quantifiers.md). 
 
## <a name="unicode-category-or-unicode-block-p"></a>Catégorie Unicode ou bloc Unicode : \p{}

La norme Unicode assigne une catégorie générale à chaque caractère. Par exemple, un caractère particulier peut être une lettre majuscule (représentée par la catégorie **Lu**), un chiffre décimal (catégorie **Nd**), un symbole mathématique (catégorie **Sm**) ou un séparateur de paragraphe (catégorie **Zl**). Les jeux de caractères spécifiques de la norme Unicode occupent également une plage spécifique ou un bloc de points de code consécutifs. Par exemple, l’alphabet latin de base se trouve de **\u0000** à **\u007F**, alors que le jeu de caractères arabe se trouve de **\u0600** à **\u06FF**. 

La construction d'expression régulière

**\p{**_nom_**}**

correspond à n’importe quel caractère qui appartient à une catégorie Unicode générale ou à un bloc nommé, où nom est l’abréviation de la catégorie ou le nom du bloc nommé. Pour obtenir la liste des abréviations des catégories, consultez la section [Catégories générales Unicode prises en charge](#supported-unicode-general-categories) plus loin dans cette rubrique. Pour obtenir la liste des blocs nommés, consultez la section [Blocs nommés pris en charge](#supported-named-blocks) plus loin dans cette rubrique. 

L’exemple suivant utilise la construction **\p{**_nom_**}** pour mettre en correspondance une catégorie Unicode générale (dans ce cas, la catégorie **Pd** ou Punctuation,Dash) et un bloc nommé (les blocs nommés **IsGreek** et **IsBasicLatin**).

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+";
      string input = "?ata ?a??a??? - The Gospel of Matthew";

      Console.WriteLine(Regex.IsMatch(input, pattern));        // Displays True.
   }
}
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+"
      Dim input As String = "Κατα Μαθθαίον - The Gospel of Matthew"

      Console.WriteLine(Regex.IsMatch(input, pattern))         ' Displays True.
   End Sub
End Module
```

L'expression régulière `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` est définie comme indiqué dans le tableau suivant.

Motif | Description
------- | ----------- 
`\b` | Commencer à la limite d'un mot.
`\p{IsGreek}+` | Mettre en correspondance un ou plusieurs caractères grecs.
`(\s)?` | Mettre en correspondance zéro ou un espace blanc.
`(\p{IsGreek}+(\s)?)+` | Mettre en correspondance le modèle d’un ou plusieurs caractères grecs, suivis de zéro ou d’un espace blanc, une ou plusieurs fois. 
`\p{Pd}` | Mettre en correspondance un signe de ponctuation tiret.
`\s` | Mettre en correspondance un espace blanc.
`\p{IsBasicLatin}+` | Mettre en correspondance un ou plusieurs caractères latins de base.
`(\s)?` | Mettre en correspondance zéro ou un espace blanc.
`(\p{IsBasicLatin}+(\s)?)+` | Mettre en correspondance un ou plusieurs caractères latins de base suivis de zéro ou d’un espace blanc, une ou plusieurs fois.

## <a name="negative-unicode-category-or-unicode-block-p"></a>Catégorie Unicode négative ou bloc Unicode : \P{}

La norme Unicode assigne une catégorie générale à chaque caractère. Par exemple, un caractère particulier peut être une lettre majuscule (représentée par la catégorie **Lu**), un chiffre décimal (catégorie **Nd**), un symbole mathématique (catégorie **Sm**) ou un séparateur de paragraphe (catégorie **Zl**). Les jeux de caractères spécifiques de la norme Unicode occupent également une plage spécifique ou un bloc de points de code consécutifs. Par exemple, l’alphabet latin de base se trouve de **\u0000** à **\u007F**, alors que le jeu de caractères arabe se trouve de **\u0600** à **\u06FF**. 

La construction d'expression régulière

**\P{**_nom_**}**

correspond à n’importe quel caractère qui appartient à une catégorie Unicode générale ou à un bloc nommé, où nom est l’abréviation de la catégorie ou le nom du bloc nommé. Pour obtenir la liste des abréviations des catégories, consultez la section [Catégories générales Unicode prises en charge](#supported-unicode-general-categories) plus loin dans cette rubrique. Pour obtenir la liste des blocs nommés, consultez la section [Blocs nommés pris en charge](#supported-named-blocks) plus loin dans cette rubrique.

L’exemple suivant utilise la construction **\P{**_nom_**}** pour supprimer tous les symboles monétaires (dans ce cas, la catégorie **Sc** ou Symbol, Currency) des chaînes numériques.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(\P{Sc})+";

      string[] values = { "$164,091.78", "£1,073,142.68", "73¢", "€120" };
      foreach (string value in values)
         Console.WriteLine(Regex.Match(value, pattern).Value);
   }
}
// The example displays the following output:
//       164,091.78
//       1,073,142.68
//       73
//       120
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(\P{Sc})+"

      Dim values() As String = { "$164,091.78", "£1,073,142.68", "73¢", "€120"}
      For Each value As String In values
         Console.WriteLine(Regex.Match(value, pattern).Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       164,091.78
'       1,073,142.68
'       73
'       120
```

Le modèle d'expression régulière `(\P{Sc})+` correspond à un ou plusieurs caractères qui ne sont pas des symboles monétaires ; il supprime efficacement tout symbole monétaire de la chaîne du résultat.

## <a name="word-character-w"></a>Caractère de mot : \w

**\w** correspond à n’importe quel caractère de mot. Un caractère de mot est un membre d'une des catégories Unicode répertoriées dans le tableau suivant. 

Catégorie | Description
-------- | ----------- 
Ll | Letter, Lowercase
Lu | Letter, Uppercase
Lt | Letter, Titlecase
Lo | Letter, Other
Lm | Letter, Modifier
Mn | Mark, Nonspacing
Nd | Number, Decimal Digit
Pc | Punctuation, Connector. Cette catégorie inclut dix caractères dont le plus souvent utilisé est le caractère LOWLINE (_), u+005F.
 
Si le comportement ECMAScript est spécifié, **\w** est équivalent à `[a-zA-Z_0-9]`. Pour plus d’informations sur les expressions régulières ECMAScript, consultez la section [Comportement de correspondance ECMAScript](options.md#ecmascript-matching-behavior) dans [Options des expressions régulières](options.md). 

> [!NOTE]
> Étant donné qu’il correspond à n’importe quel caractère de mot, l’élément de langage \w est souvent utilisé avec un quantificateur paresseux si un modèle d’expression régulière essaie de correspondre plusieurs fois à n’importe quel caractère de mot, suivi d’un caractère de mot spécifique. Pour plus d’informations, consultez [Quantificateurs dans les expressions régulières](quantifiers.md).

L’exemple suivant utilise l’élément de langage **\w** pour qu’il corresponde aux caractères en double dans un mot. L’exemple définit un modèle d’expression régulière, **(\w)\1**, qui peut être interprété comme suit.

Élément | Description
------- | -----------
(\w) | Mettre en correspondance un caractère de mot. Il s'agit du premier groupe de capture.
\1 | Mettre en correspondance la valeur de la première capture. 
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(\w)\1";
      string[] words = { "trellis", "seer", "latter", "summer", 
                         "hoarse", "lesser", "aardvark", "stunned" };
      foreach (string word in words)
      {
         Match match = Regex.Match(word, pattern);
         if (match.Success)
            Console.WriteLine("'{0}' found in '{1}' at position {2}.", 
                              match.Value, word, match.Index);
         else
            Console.WriteLine("No double characters in '{0}'.", word);
      }                                                  
   }
}
// The example displays the following output:
//       'll' found in 'trellis' at position 3.
//       'ee' found in 'seer' at position 1.
//       'tt' found in 'latter' at position 2.
//       'mm' found in 'summer' at position 2.
//       No double characters in 'hoarse'.
//       'ss' found in 'lesser' at position 2.
//       'aa' found in 'aardvark' at position 0.
//       'nn' found in 'stunned' at position 3.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(\w)\1"
      Dim words() As String = { "trellis", "seer", "latter", "summer", _
                                "hoarse", "lesser", "aardvark", "stunned" }
      For Each word As String In words
         Dim match As Match = Regex.Match(word, pattern)
         If match.Success Then
            Console.WriteLine("'{0}' found in '{1}' at position {2}.", _
                              match.Value, word, match.Index)
         Else
            Console.WriteLine("No double characters in '{0}'.", word)
         End If
      Next                                                  
   End Sub
End Module
' The example displays the following output:
'       'll' found in 'trellis' at position 3.
'       'ee' found in 'seer' at position 1.
'       'tt' found in 'latter' at position 2.
'       'mm' found in 'summer' at position 2.
'       No double characters in 'hoarse'.
'       'ss' found in 'lesser' at position 2.
'       'aa' found in 'aardvark' at position 0.
'       'nn' found in 'stunned' at position 3.
```

## <a name="nonword-character-w"></a>Caractère autre qu’un mot : \W

**\W** correspond à n’importe quel caractère autre qu’un mot. L’élément de langage **\W** est équivalent à la classe de caractères suivante :

```
[^\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]
```

En d’autres termes, il correspond à n’importe quel caractère à l’exception de ceux inclus dans les catégories Unicode répertoriées dans le tableau suivant.

Catégorie | Description
-------- | -----------
Ll | Letter, Lowercase
Lu | Letter, Uppercase
Lt | Letter, Titlecase
Lo | Letter, Other
Lm | Letter, Modifier
Mn | Mark, Nonspacing
Nd | Number, Decimal Digit
Pc | Punctuation, Connector. Cette catégorie inclut dix caractères dont le plus souvent utilisé est le caractère LOWLINE (_), u+005F.
 
Si le comportement ECMAScript est spécifié, **\w** est équivalent à `[^a-zA-Z_0-9]`. Pour plus d’informations sur les expressions régulières ECMAScript, consultez la section [Comportement de correspondance ECMAScript](options.md#ecmascript-matching-behavior) dans [Options des expressions régulières](options.md). 

> [!NOTE]
> Étant donné qu’il correspond à n’importe quel caractère de mot, l’élément de langage \w est souvent utilisé avec un quantificateur paresseux si un modèle d’expression régulière essaie de correspondre plusieurs fois à n’importe quel caractère de mot, suivi d’un caractère de mot spécifique. Pour plus d’informations, consultez [Quantificateurs dans les expressions régulières](quantifiers.md). 

L’exemple suivant illustre la classe de caractères **\W**. Il définit un modèle d'expression régulière, `\b(\w+)(\W){1,2}`, qui correspond à un mot suivi d'un ou deux caractères non alphabétiques, comme un espace ou un signe de ponctuation. L'expression régulière est interprétée comme indiqué dans le tableau suivant.

Élément | Description
------- | ----------- 
\b | Commencer la correspondance à la limite d'un mot.
(\w+) | Mettre en correspondance un ou plusieurs caractères alphabétiques. Il s'agit du premier groupe de capture.
(\W){1,2} | Mettre en correspondance un caractère autre qu'un mot une ou deux fois. Il s'agit du deuxième groupe de capture.
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\w+)(\W){1,2}";
      string input = "The old, grey mare slowly walked across the narrow, green pasture.";
      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine(match.Value);
         Console.Write("   Non-word character(s):");
         CaptureCollection captures = match.Groups[2].Captures;
         for (int ctr = 0; ctr < captures.Count; ctr++)
             Console.Write(@"'{0}' (\u{1}){2}", captures[ctr].Value, 
                           Convert.ToUInt16(captures[ctr].Value[0]).ToString("X4"), 
                           ctr < captures.Count - 1 ? ", " : "");
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//       The
//          Non-word character(s):' ' (\u0020)
//       old,
//          Non-word character(s):',' (\u002C), ' ' (\u0020)
//       grey
//          Non-word character(s):' ' (\u0020)
//       mare
//          Non-word character(s):' ' (\u0020)
//       slowly
//          Non-word character(s):' ' (\u0020)
//       walked
//          Non-word character(s):' ' (\u0020)
//       across
//          Non-word character(s):' ' (\u0020)
//       the
//          Non-word character(s):' ' (\u0020)
//       narrow,
//          Non-word character(s):',' (\u002C), ' ' (\u0020)
//       green
//          Non-word character(s):' ' (\u0020)
//       pasture.
//          Non-word character(s):'.' (\u002E)
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\w+)(\W){1,2}"
      Dim input As String = "The old, grey mare slowly walked across the narrow, green pasture."
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
         Console.Write("   Non-word character(s):")
         Dim captures As CaptureCollection = match.Groups(2).Captures
         For ctr As Integer = 0 To captures.Count - 1
             Console.Write("'{0}' (\u{1}){2}", captures(ctr).Value, _
                           Convert.ToUInt16(captures(ctr).Value.Chars(0)).ToString("X4"), _
                           If(ctr < captures.Count - 1, ", ", ""))
         Next
         Console.WriteLine()
      Next
   End Sub
End Module
' The example displays the following output:
'       The
'          Non-word character(s):' ' (\u0020)
'       old,
'          Non-word character(s):',' (\u002C), ' ' (\u0020)
'       grey
'          Non-word character(s):' ' (\u0020)
'       mare
'          Non-word character(s):' ' (\u0020)
'       slowly
'          Non-word character(s):' ' (\u0020)
'       walked
'          Non-word character(s):' ' (\u0020)
'       across
'          Non-word character(s):' ' (\u0020)
'       the
'          Non-word character(s):' ' (\u0020)
'       narrow,
'          Non-word character(s):',' (\u002C), ' ' (\u0020)
'       green
'          Non-word character(s):' ' (\u0020)
'       pasture.
'          Non-word character(s):'.' (\u002E)
```

Étant donné que l'objet `Group` du deuxième groupe de capture ne contient qu'un seul caractère autre qu'un mot capturé, l'exemple extrait tous les caractères autres que des mots capturés de l'objet `CaptureCollection` retourné par la propriété `Group.Captures`.

## <a name="whitespace-character-s"></a>Espace blanc : \s

**\s** correspond à tout espace blanc. Il est équivalent aux séquences d'échappement et catégories Unicode répertoriées dans le tableau suivant. 

Catégorie | Description
-------- | ----------- 
**\f** | Saut de page, \u000C.
**\n** | Saut de ligne, \u000A.
**\r** | Retour chariot, \u000D.
**\t** | Tabulation, \u0009.
**\v** | Tabulation verticale, \u000B.
**\x85** | Points de suspension ou caractère À LA LIGNE (NEL) (…), \u0085.
**\p{Z}** | Correspond à n'importe quel caractère de séparation.
 

Si le comportement ECMAScript est spécifié, **\s** est équivalent à `[ \f\n\r\t\v]`.  Pour plus d’informations sur les expressions régulières ECMAScript, consultez la section [Comportement de correspondance ECMAScript](options.md#ecmascript-matching-behavior) dans [Options des expressions régulières](options.md). 

L’exemple suivant illustre la classe de caractères \s. Il définit un modèle d'expression régulière, `\b\w+(e)?s(\s|$)`, qui correspond à un mot se terminant par "s" ou par "es", suivi d'un espace ou de la fin de la chaîne d'entrée. L'expression régulière est interprétée comme indiqué dans le tableau suivant.

Élément | Description
------- | -----------
\b | Commencer la correspondance à la limite d'un mot.
\w+ | Mettre en correspondance un ou plusieurs caractères alphabétiques. 
(e)? | Mettre en correspondance un « e » zéro ou une fois.
s | Mettre en correspondance un « s ».
(\s&#124;$) | Mettre en correspondance un espace blanc ou la fin de la chaîne d'entrée.
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b\w+(e)?s(\s|$)";
      string input = "matches stores stops leave leaves";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       matches
//       stores
//       stops
//       leaves
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b\w+(e)?s(\s|$)"
      Dim input As String = "matches stores stops leave leaves"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)      
      Next
   End Sub
End Module
' The example displays the following output:
'       matches
'       stores
'       stops
'       leaves
```

## <a name="nonwhitespace-character-s"></a>Caractère autre qu’un espace blanc : \S

**\S** correspond à n’importe quel caractère autre qu’un espace blanc. Il est équivalent au modèle d’expression régulière `[^\f\n\r\t\v\x85\p{Z}]` ou à l’opposé du modèle d’expression régulière qui est équivalent à **\s**, qui met en correspondance des espaces blancs. Pour plus d’informations, consultez la section précédente, « Espace blanc : \s ».

Si le comportement ECMAScript est spécifié, **\S** est équivalent à `[^ \f\n\r\t\v]`. Pour plus d’informations sur les expressions régulières ECMAScript, consultez la section [Comportement de correspondance ECMAScript](options.md#ecmascript-matching-behavior) dans [Options des expressions régulières](options.md).

L’exemple suivant illustre l’élément de langage **\S**. Le modèle d’expression régulière \b(\S+)\s? met en correspondance des chaînes délimitées par des espaces blancs. Le deuxième élément de l’objet GroupCollection de la correspondance contient la chaîne correspondante. L'expression régulière peut être interprétée comme indiqué dans le tableau suivant.

Élément | Description
------- | ----------- 
`\b` | Commencer la correspondance à la limite d'un mot.
`(\S+)` | Mettre en correspondance un ou plusieurs caractères autres que des espaces blancs. Il s'agit du premier groupe de capture.
`\s?` | Mettre en correspondance zéro ou un espace blanc. 
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\S+)\s?";
      string input = "This is the first sentence of the first paragraph. " + 
                            "This is the second sentence.\n" + 
                            "This is the only sentence of the second paragraph.";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Groups[1]);
   }
}
// The example displays the following output:
//    This
//    is
//    the
//    first
//    sentence
//    of
//    the
//    first
//    paragraph.
//    This
//    is
//    the
//    second
//    sentence.
//    This
//    is
//    the
//    only
//    sentence
//    of
//    the
//    second
//    paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\S+)\s?"
      Dim input As String = "This is the first sentence of the first paragraph. " + _
                            "This is the second sentence." + vbCrLf + _
                            "This is the only sentence of the second paragraph."
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Groups(1))
      Next
   End Sub
End Module
' The example displays the following output:
'    This
'    is
'    the
'    first
'    sentence
'    of
'    the
'    first
'    paragraph.
'    This
'    is
'    the
'    second
'    sentence.
'    This
'    is
'    the
'    only
'    sentence
'    of
'    the
'    second
'    paragraph.
```

## <a name="decimal-digit-character-d"></a>Caractère numérique décimal : \d

**\d** correspond à n’importe quel chiffre décimal. Il est équivalent au modèle d'expression régulière `\\p{Nd}`, qui inclut les chiffres décimaux standard de 0 à 9, ainsi que les chiffres décimaux de plusieurs autres jeux de caractères.

Si le comportement ECMAScript est spécifié, **\d** est équivalent à `[0-9]`. Pour plus d’informations sur les expressions régulières ECMAScript, consultez la section [Comportement de correspondance ECMAScript](options.md#ecmascript-matching-behavior) dans [Options des expressions régulières](options.md).

L’exemple suivant illustre l’élément de langage **\d**. Il teste si une chaîne d'entrée représente un numéro de téléphone valide aux États-Unis et au Canada. Le modèle d'expression régulière `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` est défini comme indiqué dans le tableau suivant.

Élément | Description
------- | ----------- 
`^` | Commencer la correspondance au début de la chaîne d'entrée.
`\(?` | Mettre en correspondance zéro ou un caractère littéral « ( ». 
`\d{3}` | Mettre en correspondance trois chiffres décimaux. 
`\)?` | Mettre en correspondance zéro ou un caractère littéral « ) ».
`[\s-]` | Mettre en correspondance un trait d'union ou un espace blanc.
`(\(?\d{3}\)?[\s-])?` | Mettre en correspondance une parenthèse ouvrante facultative suivie de trois chiffres décimaux, d'une parenthèse fermante facultative et d'un espace blanc ou d'un tiret, zéro ou une fois. Il s'agit du premier groupe de capture.
`\d{3}-\d{4}` | Mettre en correspondance trois chiffres décimaux suivis d'un trait d'union et de quatre chiffres décimaux supplémentaires.
`$` | Mettre en correspondance la fin de la chaîne d'entrée.
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$";
      string[] inputs = { "111 111-1111", "222-2222", "222 333-444", 
                          "(212) 111-1111", "111-AB1-1111", 
                          "212-111-1111", "01 999-9999" };

      foreach (string input in inputs)
      {
         if (Regex.IsMatch(input, pattern)) 
            Console.WriteLine(input + ": matched");
         else
            Console.WriteLine(input + ": match failed");
      }
   }
}
// The example displays the following output:
//       111 111-1111: matched
//       222-2222: matched
//       222 333-444: match failed
//       (212) 111-1111: matched
//       111-AB1-1111: match failed
//       212-111-1111: matched
//       01 999-9999: match failed
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$"
      Dim inputs() As String = { "111 111-1111", "222-2222", "222 333-444", _
                                 "(212) 111-1111", "111-AB1-1111", _
                                 "212-111-1111", "01 999-9999" }

      For Each input As String In inputs
         If Regex.IsMatch(input, pattern) Then 
            Console.WriteLine(input + ": matched")
         Else
            Console.WriteLine(input + ": match failed")
         End If   
      Next
   End Sub
End Module
' The example displays the following output:
'       111 111-1111: matched
'       222-2222: matched
'       222 333-444: match failed
'       (212) 111-1111: matched
'       111-AB1-1111: match failed
'       212-111-1111: matched
'       01 999-9999: match failed
```

## <a name="nondigit-character-d"></a>Caractère autre qu’un chiffre : \D

**\D** correspond à n’importe quel caractère autre qu’un chiffre. Il est équivalent au modèle d'expression régulière `\P{Nd}`.

Si le comportement ECMAScript est spécifié, **\D** est équivalent à `[^0-9]`. Pour plus d’informations sur les expressions régulières ECMAScript, consultez la section [Comportement de correspondance ECMAScript](options.md#ecmascript-matching-behavior) dans [Options des expressions régulières](options.md).

L’exemple suivant illustre l’élément de langage **\D**. Il teste si une chaîne telle qu'un numéro de référence se compose de la combinaison appropriée de caractères décimaux et autres que des décimaux. Le modèle d'expression régulière `^\D\d{1,5}\D*$` est défini comme indiqué dans le tableau suivant.

Élément | Description
------- | ----------- 
`^` | Commencer la correspondance au début de la chaîne d'entrée.
`\D` | Mettre en correspondance un caractère autre qu'un chiffre. 
`\d{1,5}` | Mettre en correspondance de un à cinq chiffres décimaux. 
`\D*` | Mettre en correspondance zéro, un ou plusieurs caractères non décimaux. 
`$` | Mettre en correspondance la fin de la chaîne d'entrée.
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"^\D\d{1,5}\D*$"; 
      string[] inputs = { "A1039C", "AA0001", "C18A", "Y938518" }; 

      foreach (string input in inputs)
      {
         if (Regex.IsMatch(input, pattern))
            Console.WriteLine(input + ": matched");
         else
            Console.WriteLine(input + ": match failed");
      }
   }
}
// The example displays the following output:
//       A1039C: matched
//       AA0001: match failed
//       C18A: matched
//       Y938518: match failed
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "^\D\d{1,5}\D*$" 
      Dim inputs() As String = { "A1039C", "AA0001", "C18A", "Y938518" } 

      For Each input As String In inputs
         If Regex.IsMatch(input, pattern) Then
            Console.WriteLine(input + ": matched")
         Else
            Console.WriteLine(input + ": match failed")
         End If   
      Next
   End Sub
End Module
' The example displays the following output:
```

## <a name="supported-unicode-general-categories"></a>Catégories générales Unicode prises en charge

La norme Unicode définit les catégories générales répertoriées dans le tableau suivant. Pour plus d’informations, consultez les sous-rubriques « Format de fichier UCD » et « Valeurs des catégories générales » dans la [Base de données de caractères Unicode](http://www.unicode.org/reports/tr44/).

Catégorie | Description
-------- | -----------
**Lu** | Letter, Uppercase
**Ll** | Letter, Lowercase
**Lt** | Letter, Titlecase
**Lm** | Letter, Modifier
**Lo** | Letter, Other
**L** | Toutes les lettres. Sont inclus les caractères **Lu**, **Ll**, **Lt**, **Lm** et **Lo**.
**Mn** | Mark, Nonspacing
**Mc** | Mark, Spacing Combining
**Me** | Mark, Enclosing
**M** | Toutes les signes diacritiques. Sont incluses les catégories **Mn**, **Mc** et **Me**.
**Nd** | Number, Decimal Digit
**Nl** | Number, Letter
**No** | Number, Other
**N** | Tous les nombres. Sont incluses les catégories **Nd**, **Nl** et **No**.
**Pc** | Punctuation, Connector
**Pd** | Punctuation, Dash
**Ps** | Punctuation, Open
**Pe** | Punctuation, Close
**Pi** | Punctuation, Initial quote (peut se comporter comme Ps ou Pe selon l'utilisation)
**Pf** | Punctuation, Final quote (peut se comporter comme Ps ou Pe selon l'utilisation)
**Po** | Punctuation, Other
**P** | Tous les caractères de ponctuation. Sont incluses les catégories **Pc**, **Pd**, **Ps**, **Pe**, **Pi**, **Pf** et **Po**.
**Sm** | Symbol, Math
**Sc** | Symbol, Currency
**Sk** | Symbol, Modifier
**So** | Symbol, Other
**S** | Tous les symboles. Sont incluses les catégories **Sm**, **Sc**, **Sk** et **So**.
**Zs** | Separator, Space
**Zl** | Separator, Line
**Zp** | Separator, Paragraph
**Z** | Tous les caractères de séparation. Sont incluses les catégories **Zs**, **Zl** et **Zp**.
**Cc** | Other, Control
**Cf** | Other, Format
**Cs** | Other, Surrogate
**Co** | Other, Private Use
**Cn** | Other, Not Assigned (aucun caractère n'a cette propriété)
**C** | Tous les caractères de contrôle. Sont incluses les catégories **Cc**, **Cf**, **Cs**, **Co** et **Cn**.
 
##<a name="supported-named-blocks"></a>Blocs nommés pris en charge

.NET fournit les blocs nommés répertoriés dans le tableau suivant. Le jeu de blocs nommés pris en charge est basé sur Unicode 4.0 et Perl 5.6.

Plage de points de code | Nom du bloc
---------------- | ---------- 
0000 - 007F | **IsBasicLatin**
0080 - 00FF | **IsLatin-1Supplement**
0100 - 017F | **IsLatinExtended-A**
0180 - 024F | **IsLatinExtended-B**
0250 - 02AF | **IsIPAExtensions**
02B0 - 02FF | **IsSpacingModifierLetters**
0300 - 036F | **IsCombiningDiacriticalMarks**
0370 - 03FF | **IsGreek** -ou- **IsGreekandCoptic**
0400 - 04FF | **IsCyrillic**
0500 - 052F | **IsCyrillicSupplement**
0530 - 058F | **IsArmenian**
0590 - 05FF | **IsHebrew**
0600 - 06FF | **IsArabic**
0700 - 074F | **IsSyriac**
0780 - 07BF | **IsThaana**
0900 - 097F | **IsDevanagari**
0980 - 09FF | **IsBengali**
0A00 - 0A7F | **IsGurmukhi**
0A80 - 0AFF | **IsGujarati**
0B00 - 0B7F | **IsOriya**
0B80 - 0BFF | **IsTamil**
0C00 - 0C7F | **IsTelugu**
0C80 - 0CFF | **IsKannada**
0D00 - 0D7F | **IsMalayalam**
0D80 - 0DFF | **IsSinhala**
0E00 - 0E7F | **IsThai**
0E80 - 0EFF | **IsLao**
0F00 - 0FFF | **IsTibetan**
1000 - 109F | **IsMyanmar**
10A0 - 10FF | **IsGeorgian**
1100 - 11FF | **IsHangulJamo**
1200 - 137F | **IsEthiopic**
13A0 - 13FF | **IsCherokee**
1400 - 167F | **IsUnifiedCanadianAboriginalSyllabics**
1680 - 169F | **IsOgham**
16A0 - 16FF | **IsRunic**
1700 - 171F | **IsTagalog**
1720 - 173F | **IsHanunoo**
1740 - 175F | **IsBuhid**
1760 - 177F | **IsTagbanwa**
1780 - 17FF | **IsKhmer**
1800 - 18AF | **IsMongolian**
1900 - 194F | **IsLimbu**
1950 - 197F | **IsTaiLe**
19E0 - 19FF | **IsKhmerSymbols**
1D00 - 1D7F | **IsPhoneticExtensions**
1E00 - 1EFF | **IsLatinExtendedAdditional**
1F00 - 1FFF | **IsGreekExtended**
2000 - 206F | **IsGeneralPunctuation**
2070 - 209F | **IsSuperscriptsandSubscripts**
20A0 - 20CF | **IsCurrencySymbols**
20D0 - 20FF | **IsCombiningDiacriticalMarksforSymbols** -ou- **IsCombiningMarksforSymbols**
2100 - 214F | **IsLetterlikeSymbols**
2150 - 218F | **IsNumberForms**
2190 - 21FF | **IsArrows**
2200 - 22FF | **IsMathematicalOperators**
2300 - 23FF | **IsMiscellaneousTechnical**
2400 - 243F | **IsControlPictures**
2440 - 245F | **IsOpticalCharacterRecognition**
2460 - 24FF | **IsEnclosedAlphanumerics**
2500 - 257F | **IsBoxDrawing**
2580 - 259F | **IsBlockElements**
25A0 - 25FF | **IsGeometricShapes**
2600 - 26FF | **IsMiscellaneousSymbols**
2700 - 27BF | **IsDingbats**
27C0 - 27EF | **IsMiscellaneousMathematicalSymbols-A**
27F0 - 27FF | **IsSupplementalArrows-A**
2800 - 28FF | **IsBraillePatterns**
2900 - 297F | **IsSupplementalArrows-B**
2980 - 29FF | **IsMiscellaneousMathematicalSymbols-B**
2A00 - 2AFF | **IsSupplementalMathematicalOperators**
2B00 - 2BFF | **IsMiscellaneousSymbolsandArrows**
2E80 - 2EFF | **IsCJKRadicalsSupplement**
2F00 - 2FDF | **IsKangxiRadicals**
2FF0 - 2FFF | **IsIdeographicDescriptionCharacters**
3000 - 303F | **IsCJKSymbolsandPunctuation**
3040 - 309F | **IsHiragana**
30A0 - 30FF | **IsKatakana**
3100 - 312F | **IsBopomofo**
3130 - 318F | **IsHangulCompatibilityJamo**
3190 - 319F | **IsKanbun**
31A0 - 31BF | **IsBopomofoExtended**
31F0 - 31FF | **IsKatakanaPhoneticExtensions**
3200 - 32FF | **IsEnclosedCJKLettersandMonths**
3300 - 33FF | **IsCJKCompatibility**
3400 - 4DBF | **IsCJKUnifiedIdeographsExtensionA**
4DC0 - 4DFF | **IsYijingHexagramSymbols**
4E00 - 9FFF | **IsCJKUnifiedIdeographs**
A000 - A48F | **IsYiSyllables**
A490 - A4CF | **IsYiRadicals**
AC00 - D7AF | **IsHangulSyllables**
D800 - DB7F | **IsHighSurrogates**
DB80 - DBFF | **IsHighPrivateUseSurrogates**
DC00 - DFFF | **IsLowSurrogates**
E000 - F8FF | **IsPrivateUse** ou **IsPrivateUseArea**
F900 - FAFF | **IsCJKCompatibilityIdeographs**
FB00 - FB4F | **IsAlphabeticPresentationForms** 
FB50 - FDFF | **IsArabicPresentationForms-A** 
FE00 - FE0F | **IsVariationSelectors** 
FE20 - FE2F | **IsCombiningHalfMarks** 
FE30 - FE4F | **IsCJKCompatibilityForms** 
FE50 - FE6F | **IsSmallFormVariants**
FE70 - FEFF | **IsArabicPresentationForms-B** 
FF00 - FFEF | **IsHalfwidthandFullwidthForms** 
FFF0 - FFFF | **IsSpecials**
 
<a name="character-class-subtraction"></a>
## <a name="character-class-subtraction-basegroup-excludedgroup"></a>Soustraction de classe de caractères : [groupe_base - [groupe_exclu]]

Une classe de caractères définit un jeu de caractères. La soustraction de classe de caractères produit un jeu de caractères qui est le résultat de l'exclusion des caractères d'une classe de caractères d'une autre classe de caractères. 

Une expression de soustraction de classe de caractères a la forme suivante :

__[__*groupe*_*base*-__[__*groupe*_*exclu*__]]--

Les crochets (**[]**) et le trait d’union (-) sont obligatoires. Le *groupe_base* est un groupe de caractères positif ou négatif. Le composant *groupe_exclu* est un autre groupe de caractères positif ou négatif, ou une autre expression de soustraction de classe de caractères (autrement dit, vous pouvez imbriquer des expressions de soustraction de classe de caractères). 

Par exemple, supposons que vous disposiez d'un groupe de base composé de la plage de caractères « a » à « z ». Pour définir le jeu de caractères composé du groupe de base, à l'exception du caractère « m », utilisez `[a-z-[m]]`. Pour définir le jeu de caractères composé du groupe de base, à l'exception du jeu de caractères « d », « j » et « p », utilisez `[a-z-[djp]]`. Pour définir le jeu de caractères composé du groupe de base, à l'exception de la plage de caractères allant de « m » à « p », utilisez `[a-z-[m-p]]`. 

Prenons l'exemple de l'expression de soustraction de classe de caractères imbriquée, `[a-z-[d-w-[m-o]]]`. L'expression est évaluée à partir de la plage de caractères la plus profonde, vers l'extérieur. Tout d'abord, la plage de caractères « m » à « o » est soustraite de la plage de caractères « d » à « w », ce qui génère le jeu de caractères « d » à « l » et « p » à « w ». Ce jeu est ensuite soustrait de la plage de caractères allant de « a » à « z », ce qui produit le jeu de caractères `[abcmnoxyz]`.

Vous pouvez utiliser n'importe quelle classe de caractères avec la soustraction de classe de caractères. Pour définir le jeu de caractères qui se compose de tous les caractères Unicode de \u0000 à \uFFFF, à l’exception des espaces blancs (**\s**), des caractères de la catégorie générale de ponctuation (**\p{P}**), des caractères du bloc nommé **IsGreek** (**\p{IsGreek}**) et du caractère de contrôle LIGNE SUIVANTE Unicode (\x85), utilisez `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`.

Choisissez des classes de caractères pour une expression de soustraction de classe de caractères qui produira des résultats utiles. Évitez toute expression produisant un jeu de caractères vide, n'ayant aucune correspondance ou toute expression équivalant au groupe de base d'origine. Par exemple, le jeu vide résulte de l’expression `[\p{IsBasicLatin}-[\x00-\x7F]]`, qui soustrait tous les caractères compris dans la plage de caractères **IsBasicLatin** de la catégorie générale **IsBasicLatin**. De même, le groupe de base d'origine résulte de l'expression `[a-z-[0-9]]`. Cela est dû au fait que le groupe de base, c'est-à-dire la plage de caractères des lettres de « a » à « z », ne contient aucun caractère dans le groupe exclu, c'est-à-dire la plage de caractères des chiffres décimaux de « 0 » à « 9 ». 

L'exemple suivant définit une expression régulière, `^[0-9-[2468]]+$`, qui correspond à zéro et aux nombres impairs d'une chaîne d'entrée. L'expression régulière est interprétée comme indiqué dans le tableau suivant.

Élément | Description
------- | ----------- 
`^` | Commencer la correspondance au démarrage de la chaîne d'entrée.
`[0-9-[2468]]+` | Mettre en correspondance une ou plusieurs occurrences de n'importe quel caractère de 0 à 9 à l'exception de 2, 4, 6 et 8. En d'autres termes, mettre en correspondance une ou plusieurs occurrences de zéro ou d'un chiffre impair.
`$` | Terminer la correspondance à la fin de la chaîne d'entrée.
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "123", "13579753", "3557798", "335599901" };
      string pattern = @"^[0-9-[2468]]+$";

      foreach (string input in inputs)
      {
         Match match = Regex.Match(input, pattern);
         if (match.Success) 
            Console.WriteLine(match.Value);
      }      
   }
}
// The example displays the following output:
//       13579753
//       335599901
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "123", "13579753", "3557798", "335599901" }
      Dim pattern As String = "^[0-9-[2468]]+$"

      For Each input As String In inputs
         Dim match As Match = Regex.Match(input, pattern)
         If match.Success Then Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       13579753
'       335599901
```

## <a name="see-also"></a>Voir aussi

[Options des expressions régulières](options.md)


<!--HONumber=Nov16_HO1-->


