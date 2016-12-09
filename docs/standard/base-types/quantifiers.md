---
title: "Quantificateurs dans les expressions régulières"
description: "Quantificateurs dans les expressions régulières"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 8e5124c4-20b5-4c57-ab68-301d1d7311c4
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 79637972770d3ab5d954d40285dc4f07e58d233f

---

# <a name="quantifiers-in-regular-expressions"></a>Quantificateurs dans les expressions régulières

Les quantificateurs spécifient le nombre d’instances d’un caractère, groupe ou classe de caractères devant être présentes dans l’entrée pour qu’une correspondance soit trouvée. Le tableau suivant répertorie les quantificateurs pris en charge par .NET.

Quantificateur gourmand | Quantificateur paresseux | Description
----------------- | --------------- | ----------- 
**\*** | **\*?** | Mettre en correspondance zéro occurrence ou plus.
**+** | **+?** | Mettre en correspondance une ou plusieurs occurrences.
**?** | **??** | Mettre en correspondance zéro ou une occurrence.
**{**_n_**}** | **{**_n_**}?** | Mettre en correspondance exactement n occurrences.
**{**_n_**,}** | **{**_n_**,}?** | Mettre en correspondance au moins n occurrences.
**{**_n_**,**_m_**}** | **{**_n_**,**_m_**}?** | Mettre en correspondance de n à m occurrences.
 
Les quantités *n* et *m* sont des constantes entières. Habituellement, les quantificateurs sont gourmands ; ils obligent le moteur d’expression régulière à faire correspondre autant d’occurrences de modèles particuliers que possible. L’ajout du caractère `?` à un quantificateur le rend paresseux ; le moteur d’expression régulière fait alors correspondre aussi peu d’occurrences que possible. Pour une description complète de la différence entre quantificateurs gourmands et paresseux, consultez la section [Quantificateurs gourmands et paresseux](#greedy-and-lazy-quantifiers) plus loin dans cette rubrique.

> [!IMPORTANT]
> L’imbrication des quantificateurs (par exemple, comme le fait le modèle d’expression régulière `(a*)*`) peut augmenter le nombre de comparaisons que le moteur d’expression régulière doit exécuter, comme une fonction exponentielle du nombre de caractères dans la chaîne d’entrée. Pour plus d’informations sur ce comportement et ses solutions de contournement, consultez [Rétroaction dans les expressions régulières](backtracking.md).

## <a name="regular-expression-quantifiers"></a>Quantificateurs d’expression régulière

Les sections suivantes présentent les quantificateurs pris en charge par les expressions régulières .NET. 

> [!NOTE]
> Si les caractères \*, +, ?, { et } sont rencontrés dans un modèle d’expressions régulières, le moteur d’expression régulière les interprète comme des quantificateurs ou partie de constructions de quantificateur à moins qu’ils ne soient inclus dans une [classe de caractères](classes.md). Pour les interpréter comme des caractères littéraux en dehors d’une classe de caractères, vous devez les placer dans une séquence d’échappement en les faisant précéder d’une barre oblique inverse. Par exemple, la chaîne `\*` dans un modèle d’expression régulière est interprétée comme un caractère astérisque (« * ») littéral.

### <a name="match-zero-or-more-times-"></a>Mettre en correspondance zéro occurrence ou plus : \*

Le quantificateur \* correspond zéro fois, ou plus, à l’élément qui précède. Il équivaut au quantificateur **{0},**. **\*** est un quantificateur gourmand dont l’équivalent paresseux est **\*?**.

L’exemple suivant illustre cette expression régulière. La chaîne d’entrée comporte neuf chiffres dont cinq correspondent au modèle et quatre (`95`, `929`, `9129` et `9919`) n’y correspondent pas.

```csharp
string pattern = @"\b91*9*\b";   
string input = "99 95 919 929 9119 9219 999 9919 91119";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

// The example displays the following output:   
//       '99' found at position 0.
//       '919' found at position 6.
//       '9119' found at position 14.
//       '999' found at position 24.
//       '91119' found at position 33.
```

```vb
Dim pattern As String = "\b91*9*\b"   
Dim input As String = "99 95 919 929 9119 9219 999 9919 91119"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next     
' The example displays the following output:   
'       '99' found at position 0.
'       '919' found at position 6.
'       '9119' found at position 14.
'       '999' found at position 24.
'       '91119' found at position 33.
```

Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`\b` | Commencer à la limite d'un mot.
`91*` | Mettre en correspondance un « 9 » suivi de zéro, ou plus, caractère « 1 ».
`9*` | Mettre en correspondance zéro, ou plus, caractère « 9 ».
`\b` | Terminer à une limite de mot.
 
### <a name="match-one-or-more-times-"></a>Mettre en correspondance un ou plusieurs chiffres : +

Le quantificateur **+** correspond une ou plusieurs fois à l’élément qui précède. Il équivaut à **{1,}**. **+** est un quantificateur gourmand dont l’équivalent paresseux est **+?**.

Par exemple, l’expression régulière `\ban+\w*?\b` tente d’établir une correspondance avec les mots entiers qui commencent par la lettre `a` suivie d’une ou de plusieurs instances de la lettre `n`. L’exemple suivant illustre cette expression régulière. L’expression régulière établit une correspondance avec les mots `an`, `annual`, `announcement` et `antique`, et pas avec les mots `autumn` et `all`.

```csharp
string pattern = @"\ban+\w*?\b";

string input = "Autumn is a great time for an annual announcement to all antique collectors.";
foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

// The example displays the following output:   
//       'an' found at position 27.
//       'annual' found at position 30.
//       'announcement' found at position 37.
//       'antique' found at position 57.      
```

```vb
Dim pattern As String = "\ban+\w*?\b"

Dim input As String = "Autumn is a great time for an annual announcement to all antique collectors."
For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next   
' The example displays the following output:   
'       'an' found at position 27.
'       'annual' found at position 30.
'       'announcement' found at position 37.
'       'antique' found at position 57. 
```

Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`\b` | Commencer à la limite d'un mot.
`an+` | Mettre en correspondance un « a » suivi d’un ou plusieurs caractères « n ». 
`\w*?` | Mettre en correspondance un caractère alphabétique zéro, une ou plusieurs fois, mais le moins de fois possible.
`\b` | Terminer à une limite de mot.
 
### <a name="match-zero-or-one-time-"></a>Mettre en correspondance zéro ou une occurrence : ?

Le quantificateur **?** correspond zéro ou une fois à l’élément qui précède. Il équivaut à **{0,1}**. **?** est un quantificateur gourmand dont l’équivalent paresseux est **??**.

Par exemple, l’expression régulière `\ban?\b` tente d’établir une correspondance avec les mots entiers qui commencent par la lettre `a` suivie de zéro ou une instance de la lettre `n`. En d’autres termes, elle tente d’établir une correspondance avec les mots `a` et `an`. L’exemple suivant illustre cette expression régulière.

```csharp
string pattern = @"\ban?\b";
string input = "An amiable animal with a large snount and an animated nose.";
foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

// The example displays the following output:   
//        'An' found at position 0.
//        'a' found at position 23.
//        'an' found at position 42.
```

```vb
Dim pattern As String = "\ban?\b"
Dim input As String = "An amiable animal with a large snount and an animated nose."
For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next  
' The example displays the following output:   
'       'An' found at position 0.
'       'a' found at position 23.
'       'an' found at position 42.
```

Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`\b` | Commencer à la limite d'un mot.
`an?` | Mettre en correspondance un « a » suivi de zéro ou un caractère « n ». 
`\b` | Terminer à une limite de mot.
 
### <a name="match-exactly-n-times-n"></a>Mettre en correspondance exactement n occurrences : {n}

Le quantificateur **{**_n_**}** correspond à l’élément qui précède exactement *n* fois, où *n* est un entier. **{**_n_**}** est un quantificateur gourmand dont l’équivalent paresseux est **{**_n_**}?**.

Par exemple, l’expression régulière `\b\d+\,\d{3}\b` tente d’établir une correspondance avec une limite de mot suivie d’un ou de plusieurs chiffres décimaux suivis de trois chiffres décimaux suivis d’une limite de mot. L’exemple suivant illustre cette expression régulière. 

```csharp
string pattern = @"\b\d+\,\d{3}\b";
string input = "Sales totaled 103,524 million in January, " + 
                      "106,971 million in February, but only " + 
                      "943 million in March.";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:   
//        '103,524' found at position 14.
//        '106,971' found at position 45.
```

```vb
Dim pattern As String = "\b\d+\,\d{3}\b"
Dim input As String = "Sales totaled 103,524 million in January, " + _
                      "106,971 million in February, but only " + _
                      "943 million in March."
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next     
' The example displays the following output:   
'       '103,524' found at position 14.
'       '106,971' found at position 45.
```

Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`\b` | Commencer à la limite d'un mot.
`\d+` | Mettre en correspondance un ou plusieurs chiffres décimaux. 
`\,` | Mettre en correspondance une virgule.
`\d{3}` | Mettre en correspondance trois chiffres décimaux.
`\b` | Terminer à une limite de mot.
 
### <a name="match-at-least-n-times-n"></a>Mettre en correspondance au moins n occurrences : {n,}

Le quantificateur **{**_n_**,}** correspond à l’élément qui précède au moins *n* fois, où *n* est un entier. **{**_n_**,}** est un quantificateur gourmand dont l’équivalent paresseux est **{**_n_**}?**.

Par exemple, l’expression régulière `\b\d{2,}\b\D+` tente d’établir une correspondance avec une limite de mot suivie d’au moins deux chiffres suivis d’une limite de mot et d’un caractère non numérique. L’exemple suivant illustre cette expression régulière. L’expression régulière ne peut pas établir de correspondance avec l’expression « 7 days », car elle ne contient qu’un chiffre. En revanche, une correspondance est établie avec « 10 weeks and 300 years ».

```csharp
string pattern = @"\b\d{2,}\b\D+";   
string input = "7 days, 10 weeks, 300 years";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        '10 weeks, ' found at position 8.
// 
``` 

```vb
Dim pattern As String = "\b\d{2,}\b\D+"  
 Dim input As String = "7 days, 10 weeks, 300 years"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       '10 weeks, ' found at position 8.
'       '300 years' found at position 18.
      '300 years' found at position 18.
```

Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`\b` | Commencer à la limite d'un mot.
`\d{2,}` | Mettre en correspondance au moins deux chiffres décimaux. 
`\b` | Mettre en correspondance la limite d'un mot.
`\D+` | Mettre en correspondance au moins un chiffre non décimal.
 
### <a name="match-between-n-and-m-times-nm"></a>Mettre en correspondance entre n et m fois : {n, m}

Le quantificateur **{**_n_**,**_m_**}** correspond à l’élément qui précède au moins *n* fois, mais pas plus de *m* fois, où *n* et *m* sont des entiers. **{**_n_**,**_m_**}** est un quantificateur gourmand dont l’équivalent paresseux est **{**_n_**,**_m_**}?**.

Dans l’exemple suivant, l’expression régulière `(00\s){2,4}` tente d’établir une correspondance entre deux et quatre occurrences de deux zéros suivis d’un espace. Notez que la partie finale de la chaîne d’entrée inclut ce modèle cinq fois au lieu du maximum de quatre. Toutefois, seule la partie initiale de cette sous-chaîne (jusqu’à l’espace et la cinquième paire de zéros) correspond au modèle d’expression régulière.

```csharp
string pattern = @"(00\s){2,4}";
string input = "0x00 FF 00 00 18 17 FF 00 00 00 21 00 00 00 00 00";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        '00 00 ' found at position 8.
//        '00 00 00 ' found at position 23.
//        '00 00 00 00 ' found at position 35.
```

```vb
Dim pattern As String = "(00\s){2,4}"
Dim input As String = "0x00 FF 00 00 18 17 FF 00 00 00 21 00 00 00 00 00"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       '00 00 ' found at position 8.
'       '00 00 00 ' found at position 23.
'       '00 00 00 00 ' found at position 35.
```

### <a name="match-zero-or-more-times-lazy-match-"></a>Mettre en correspondance zéro occurrence ou plus (correspondance paresseuse) : \*?

Le quantificateur **\*?** établit zéro, une ou plusieurs correspondances avec l’élément qui précède, mais le moins de fois possible. Il s’agit de l’équivalent paresseux du quantificateur gourmand **\***.

Dans l’exemple suivant, l’expression régulière `\b\w*?oo\w*?\b` correspond à tous les mots qui contiennent la chaîne `oo`. 

```csharp
 string pattern = @"\b\w*?oo\w*?\b";
 string input = "woof root root rob oof woo woe";
 foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
    Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

 //  The example displays the following output:
//        'woof' found at position 0.
//        'root' found at position 5.
//        'root' found at position 10.
//        'oof' found at position 19.
//        'woo' found at position 23.
```

```vb
Dim pattern As String = "\b\w*?oo\w*?\b"
 Dim input As String = "woof root root rob oof woo woe"
 For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
    Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
 Next 
 ' The example displays the following output:
'       'woof' found at position 0.
'       'root' found at position 5.
'       'root' found at position 10.
'       'oof' found at position 19.
'       'woo' found at position 23.
```

Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`\b` | Commencer à la limite d'un mot.
`\w*?` | Correspond à zéro, un ou plusieurs caractères alphabétiques, mais le moins de caractères possible. 
`oo` | Mettre en correspondance la chaîne « oo ».
`\w*?` | Correspond à zéro, un ou plusieurs caractères alphabétiques, mais le moins de caractères possible.
`\b` | Terminer sur une limite de mot.
 
### <a name="match-one-or-more-times-lazy-match-"></a>Mettre en correspondance une ou plusieurs occurrences (correspondance paresseuse) : +?

Le quantificateur **+?** établit une ou plusieurs correspondances avec l’élément qui précède, mais le moins de fois possible. Il s’agit de l’équivalent paresseux du quantificateur gourmand **+**.

Par exemple, l’expression régulière `\b\w+?\b` établit une correspondance avec un ou plusieurs caractères séparés par des limites de mot. L’exemple suivant illustre cette expression régulière.

```csharp
string pattern = @"\b\w+?\b";
string input = "Aa Bb Cc Dd Ee Ff";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        'Aa' found at position 0.
//        'Bb' found at position 3.
//        'Cc' found at position 6.
//        'Dd' found at position 9.
//        'Ee' found at position 12.
//        'Ff' found at position 15.
```

```vb
Dim pattern As String = "\b\w+?\b"
 Dim input As String = "Aa Bb Cc Dd Ee Ff"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       'Aa' found at position 0.
'       'Bb' found at position 3.
'       'Cc' found at position 6.
'       'Dd' found at position 9.
'       'Ee' found at position 12.
'       'Ff' found at position 15.
```

### <a name="match-zero-or-one-time-lazy-match-"></a>Mettre en correspondance zéro ou une occurrence (correspondance paresseuse) : ??

Le quantificateur **??** établit zéro ou une correspondance avec l’élément qui précède, mais le moins de fois possible. Il s’agit de l’équivalent paresseux du quantificateur gourmand **?**.

Par exemple, l’expression régulière `^\s*(System.)??Console.Write(Line)??\(??` tente d’établir une correspondance avec les chaînes « Console.Write » ou « Console.WriteLine ». La chaîne peut également comprendre « System. » avant « Console », et elle peut être suivie par une parenthèse ouvrante. Elle doit se trouver au début d’une ligne, mais peut être précédée d’un espace blanc. L’exemple suivant illustre cette expression régulière.

```csharp
string pattern = @"^\s*(System.)??Console.Write(Line)??\(??";
string input = "System.Console.WriteLine(\"Hello!\")\n" + 
                      "Console.Write(\"Hello!\")\n" + 
                      "Console.WriteLine(\"Hello!\")\n" + 
                      "Console.ReadLine()\n" + 
                      "   Console.WriteLine";
foreach (Match match in Regex.Matches(input, pattern, 
                                      RegexOptions.IgnorePatternWhitespace | 
                                      RegexOptions.IgnoreCase | 
                                      RegexOptions.Multiline))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        'System.Console.Write' found at position 0.
//        'Console.Write' found at position 36.
//        'Console.Write' found at position 61.
//        '   Console.Write' found at position 110.
```

```vb
Dim pattern As String = "^\s*(System.)??Console.Write(Line)??\(??"
Dim input As String = "System.Console.WriteLine(""Hello!"")" + vbCrLf + _
                      "Console.Write(""Hello!"")" + vbCrLf + _
                      "Console.WriteLine(""Hello!"")" + vbCrLf + _
                      "Console.ReadLine()" + vbCrLf + _
                      "   Console.WriteLine"
For Each match As Match In Regex.Matches(input, pattern, _
                                         RegexOptions.IgnorePatternWhitespace Or RegexOptions.IgnoreCase Or RegexOptions.MultiLine)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       'System.Console.Write' found at position 0.
'       'Console.Write' found at position 36.
'       'Console.Write' found at position 61.
'       '   Console.Write' found at position 110.
```

Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`^` | Mettre en correspondance le début du flux d’entrée.
`\s*` | Correspond à zéro, un ou plusieurs espaces blancs.
`(System.)??` | Mettre en correspondance zéro ou une occurrence de la chaîne « System. ».
`Console.Write` | Mettre en correspondance la chaîne « Console.Write ».
`(Line)??` | Mettre en correspondance zéro ou une occurrence de la chaîne « Line ».
`\(??` | Mettre en correspondance zéro occurrence, ou plus, de la parenthèse ouvrante.
 
### <a name="match-exactly-n-times-lazy-match-n"></a>Mettre en correspondance exactement n occurrences (correspondance paresseuse) : {n}?

Le quantificateur **{**_n_**}?** correspond à l’élément qui précède exactement *n* fois, où *n* est un entier. Il s’agit de l’équivalent paresseux du quantificateur gourmand **{**_n_**}+**.

Dans l’exemple suivant, l’expression régulière `\b(\w{3,}?\.){2}?\w{3,}?\b` est utilisée pour identifier une adresse de site web. Notez qu’elle établit une correspondance avec « www.microsoft.com » et « msdn.microsoft.com », mais pas avec « mywebsite » ou « mycompany.com ».

```csharp
string pattern = @"\b(\w{3,}?\.){2}?\w{3,}?\b";
string input = "www.microsoft.com msdn.microsoft.com mywebsite mycompany.com";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        'www.microsoft.com' found at position 0.
//        'msdn.microsoft.com' found at position 18.
```

```vb
Dim pattern As String = "\b(\w{3,}?\.){2}?\w{3,}?\b"
 Dim input As String = "www.microsoft.com msdn.microsoft.com mywebsite mycompany.com"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next     
' The example displays the following output:
'       'www.microsoft.com' found at position 0.
'       'msdn.microsoft.com' found at position 18.
```

Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`\b` | Commencer à la limite d'un mot.
`(\w{3,}?\.)` | Mettre en correspondance au moins 3 caractères alphabétiques, mais le moins de caractères possible, suivis d’un point ou d’un point final. Il s'agit du premier groupe de capture.
`(\w{3,}?\.){2}?` | Mettre en correspondance le modèle dans le premier groupe deux fois, mais le moins de fois possible.
`\b` | Terminer la correspondance à la limite d'un mot.
 
### <a name="match-at-least-n-times-lazy-match-n"></a>Mettre en correspondance au moins n occurrences (correspondance paresseuse) : {n,}?

Le quantificateur **{**_n_**,}?** correspond à l’élément qui précède au moins *n* fois, où *n* est un entier, mais aussi peu de fois que possible. Il s’agit de l’équivalent paresseux du quantificateur gourmand **{**_n_**,}**.

Consultez l’exemple pour le quantificateur **{**_n_**}?** dans la section précédente pour une illustration. L’expression régulière de cet exemple utilise le quantificateur **{**_n_**,}** pour établir une correspondance avec une chaîne comportant au moins trois caractères suivis d’un point.

### <a name="match-between-n-and-m-times-lazy-match-nm"></a>Mettre en correspondance entre n et m fois (correspondance paresseuse) : {n,m}?

Le quantificateur **{**_n_**,**_m_**}?** correspond à l’élément qui précède entre *n* et *m* fois, où *n* et *m* sont des entiers, mais aussi peu de fois que possible. Il s’agit de l’équivalent paresseux du quantificateur gourmand **{**_n_**,**_m_**}**.

Dans l’exemple suivant, l’expression régulière `\b[A-Z](\w*\s+){1,10}?[.!?]` correspond aux phrases qui contiennent entre un et dix mots. Elle établit une correspondance avec toutes les phrases de la chaîne d’entrée à l’exception d’une phrase qui contient 18 mots.

```csharp
string pattern = @"\b[A-Z](\w*?\s*?){1,10}[.!?]";
string input = "Hi. I am writing a short note. Its purpose is " + 
                      "to test a regular expression that attempts to find " + 
                      "sentences with ten or fewer words. Most sentences " + 
                      "in this note are short.";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        'Hi.' found at position 0.
//        'I am writing a short note.' found at position 4.
//        'Most sentences in this note are short.' found at position 132.
```

```vb
Dim pattern As String = "\b[A-Z](\w*\s?){1,10}?[.!?]"
Dim input As String = "Hi. I am writing a short note. Its purpose is " + _
                      "to test a regular expression that attempts to find " + _
                      "sentences with ten or fewer words. Most sentences " + _
                      "in this note are short."
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       'Hi.' found at position 0.
'       'I am writing a short note.' found at position 4.
'       'Most sentences in this note are short.' found at position 132.
```

Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`\b` | Commencer à la limite d'un mot.
`[A-Z]` | Mettre en correspondance une majuscule de A à Z.
`(\w*\s+)` | Mettre en correspondance zéro, un ou plusieurs caractères alphabétiques, suivis d’un ou plusieurs espaces blancs. Il s’agit du premier groupe de capture.
`{1,10}?` | Mettre en correspondance le modèle précédent entre 1 et 10 fois, mais le moins de fois possible.
`[.!?]` | Mettre en correspondance un signe de ponctuation « . », « ! » ou « ? ».
 
## <a name="greedy-and-lazy-quantifiers"></a>Quantificateurs gourmands et paresseux

De nombreux quantificateurs existent en deux versions : 

* Une version gourmande. 

  Un quantificateur gourmand essaie de correspondre à un élément autant de fois que possible. 


* •Une version non gourmande (ou paresseuse). 

 Un quantificateur non gourmand essaie de correspondre à un élément aussi peu de fois que possible. Vous pouvez changer un quantificateur gourmand en quantificateur paresseux en ajoutant simplement un **?**.

Considérez une expression régulière simple censée extraire les quatre derniers chiffres d’une chaîne de nombres telle qu’un numéro de carte de crédit. La version de l’expression régulière qui utilise le quantificateur gourmand **\*** est `\b.*([0-9]{4})\b`. Toutefois, si une chaîne contient deux nombres, cette expression régulière correspond uniquement aux quatre derniers chiffres du deuxième nombre, comme le montre l’exemple suivant.

```csharp
string greedyPattern = @"\b.*([0-9]{4})\b";
string input1 = "1112223333 3992991999";
foreach (Match match in Regex.Matches(input1, greedyPattern))
   Console.WriteLine("Account ending in ******{0}.", match.Groups[1].Value);

// The example displays the following output:
//       Account ending in ******1999.
```

```vb
Dim greedyPattern As String = "\b.*([0-9]{4})\b"
Dim input1 As String = "1112223333 3992991999"
For Each match As Match In Regex.Matches(input1, greedypattern)
   Console.WriteLine("Account ending in ******{0}.", match.Groups(1).Value)
Next
' The example displays the following output:
'       Account ending in ******1999.
```

L’expression régulière ne parvient pas à établir de correspondance avec le premier nombre ; en effet, comme le quantificateur **\*** tente d’établir une correspondance autant de fois que possible avec l’élément qui précède dans la totalité de la chaîne, il trouve une correspondance à la fin de celle-ci.

Il ne s’agit pas du comportement souhaité. À la place, vous pouvez utiliser le quantificateur paresseux **\*?** pour extraire les chiffres des deux nombres, comme le montre l’exemple suivant.

```csharp
string lazyPattern = @"\b.*?([0-9]{4})\b";
string input2 = "1112223333 3992991999";
foreach (Match match in Regex.Matches(input2, lazyPattern))
   Console.WriteLine("Account ending in ******{0}.", match.Groups[1].Value);

// The example displays the following output:
//       Account ending in ******3333.
//       Account ending in ******1999.
```

```vb
Dim lazyPattern As String = "\b.*?([0-9]{4})\b"
Dim input2 As String = "1112223333 3992991999"
For Each match As Match In Regex.Matches(input2, lazypattern)
   Console.WriteLine("Account ending in ******{0}.", match.Groups(1).Value)
Next     
' The example displays the following output:
'       Account ending in ******3333.
'       Account ending in ******1999.
```

Dans la plupart des cas, les expressions régulières avec des quantificateurs gourmands et paresseux retournent les mêmes correspondances. Elles retournent le plus souvent des résultats différents quand elles sont utilisées avec le métacaractère (**.**) générique, qui correspond à n’importe quel caractère. 

## <a name="quantifiers-and-empty-matches"></a>Quantificateurs et correspondances vides

Les quantificateurs **\***, **+** et **{**_n_**,**_m_**}** et leurs équivalents paresseux s’arrêtent systématiquement après une correspondance vide quand le nombre minimal de captures a été récupéré. Cette règle empêche les quantificateurs d’entrer dans des boucles infinies sur des correspondances de sous-expressions vides quand le nombre maximal de captures de groupe possibles est infini ou proche de l’infini.

Par exemple, le code suivant montre le résultat d’un appel de la méthode [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) avec le modèle d’expression régulière `(a?)*,` qui correspond à zéro ou un caractère « a », zéro, une ou plusieurs fois. Notez que le seul groupe de capture capture chaque « a », ainsi que [String.Empty](xref:System.String.Empty), mais qu’il n’existe aucune deuxième correspondance vide, car la première correspondance vide entraîne l’arrêt de la répétition du quantificateur.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "(a?)*";
      string input = "aaabbb";
      Match match = Regex.Match(input, pattern);
      Console.WriteLine("Match: '{0}' at index {1}", 
                        match.Value, match.Index);
      if (match.Groups.Count > 1) {
         GroupCollection groups = match.Groups;
         for (int grpCtr = 1; grpCtr <= groups.Count - 1; grpCtr++) {
            Console.WriteLine("   Group {0}: '{1}' at index {2}", 
                              grpCtr, 
                              groups[grpCtr].Value,
                              groups[grpCtr].Index);
            int captureCtr = 0;
            foreach (Capture capture in groups[grpCtr].Captures) {
               captureCtr++;
               Console.WriteLine("      Capture {0}: '{1}' at index {2}", 
                                 captureCtr, capture.Value, capture.Index);
            }
         } 
      }   
   }
}
// The example displays the following output:
//       Match: 'aaa' at index 0
//          Group 1: '' at index 3
//             Capture 1: 'a' at index 0
//             Capture 2: 'a' at index 1
//             Capture 3: 'a' at index 2
//             Capture 4: '' at index 3
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(a?)*"
      Dim input As String = "aaabbb"
      Dim match As Match = Regex.Match(input, pattern)
      Console.WriteLine("Match: '{0}' at index {1}", 
                        match.Value, match.Index)
      If match.Groups.Count > 1 Then
         Dim groups As GroupCollection = match.Groups
         For grpCtr As Integer = 1 To groups.Count - 1
            Console.WriteLine("   Group {0}: '{1}' at index {2}", 
                              grpCtr, 
                              groups(grpCtr).Value,
                              groups(grpCtr).Index)
            Dim captureCtr As Integer = 0
            For Each capture As Capture In groups(grpCtr).Captures
               captureCtr += 1
               Console.WriteLine("      Capture {0}: '{1}' at index {2}", 
                                 captureCtr, capture.Value, capture.Index)
            Next
         Next 
      End If   
   End Sub
End Module
' The example displays the following output:
'       Match: 'aaa' at index 0
'          Group 1: '' at index 3
'             Capture 1: 'a' at index 0
'             Capture 2: 'a' at index 1
'             Capture 3: 'a' at index 2
'             Capture 4: '' at index 3
```

Pour voir la différence pratique entre un groupe de capture qui définit un nombre minimal et un nombre maximal de captures et un groupe de capture qui définit un nombre fixe de captures, examinez les modèles d’expressions régulières `(a\1|(?(1)\1)){0,2}` et `(a\1|(?(1)\1)){2}`. Les deux expressions régulières se composent d’un seul groupe de capture, qui est défini comme indiqué dans le tableau suivant. 

Modèle | Description
------- | -----------
`(a\1` | Mettre en correspondance « a » avec la valeur du premier groupe capturé …
`&#124;(?(1)` | … ou tester si le premier groupe capturé a été défini. (Notez que la construction **(?(1)** ne définit pas un groupe de capture.)
`\1))` | Si le premier groupe capturé existe, établir une correspondance avec sa valeur. Si le groupe n’existe pas, le groupe correspond à [String.Empty](xref:System.String.Empty). 
 
La première expression régulière essaie de correspondre à ce modèle entre zéro et deux fois ; la deuxième, exactement deux fois. Étant donné que le premier modèle atteint son nombre minimal de captures avec sa première capture de [String.Empty](xref:System.String.Empty), il ne se répète jamais pour essayer d’établir une correspondance avec `a\1;` ; le quantificateur `{0,2}` autorise uniquement les correspondances vides dans la dernière itération. En revanche, la seconde expression régulière établit une correspondance avec « a », car elle évalue `a\1` une deuxième fois ; le nombre minimal d’itérations, 2, entraîne la répétition du moteur après une correspondance vide.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern, input;

      pattern = @"(a\1|(?(1)\1)){0,2}";
      input = "aaabbb"; 

      Console.WriteLine("Regex pattern: {0}", pattern);
      Match match = Regex.Match(input, pattern);
      Console.WriteLine("Match: '{0}' at position {1}.", 
                        match.Value, match.Index);
      if (match.Groups.Count > 1) {
         for (int groupCtr = 1; groupCtr <= match.Groups.Count - 1; groupCtr++)
         {
            Group group = match.Groups[groupCtr];         
            Console.WriteLine("   Group: {0}: '{1}' at position {2}.", 
                              groupCtr, group.Value, group.Index);
            int captureCtr = 0;
            foreach (Capture capture in group.Captures) {
               captureCtr++;
               Console.WriteLine("      Capture: {0}: '{1}' at position {2}.", 
                                 captureCtr, capture.Value, capture.Index);
            }   
         }
      }
      Console.WriteLine();

      pattern = @"(a\1|(?(1)\1)){2}";
      Console.WriteLine("Regex pattern: {0}", pattern);
      match = Regex.Match(input, pattern);
         Console.WriteLine("Matched '{0}' at position {1}.", 
                           match.Value, match.Index);
      if (match.Groups.Count > 1) {
         for (int groupCtr = 1; groupCtr <= match.Groups.Count - 1; groupCtr++)
         {
            Group group = match.Groups[groupCtr];         
            Console.WriteLine("   Group: {0}: '{1}' at position {2}.", 
                              groupCtr, group.Value, group.Index);
            int captureCtr = 0;
            foreach (Capture capture in group.Captures) {
               captureCtr++;
               Console.WriteLine("      Capture: {0}: '{1}' at position {2}.", 
                                 captureCtr, capture.Value, capture.Index);
            }   
         }
      }
   }
}
// The example displays the following output:
//       Regex pattern: (a\1|(?(1)\1)){0,2}
//       Match: '' at position 0.
//          Group: 1: '' at position 0.
//             Capture: 1: '' at position 0.
//       
//       Regex pattern: (a\1|(?(1)\1)){2}
//       Matched 'a' at position 0.
//          Group: 1: 'a' at position 0.
//             Capture: 1: '' at position 0.
//             Capture: 2: 'a' at position 0.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern, input As String

      pattern = "(a\1|(?(1)\1)){0,2}"
      input = "aaabbb" 

      Console.WriteLine("Regex pattern: {0}", pattern)
      Dim match As Match = Regex.Match(input, pattern)
      Console.WriteLine("Match: '{0}' at position {1}.", 
                        match.Value, match.Index)
      If match.Groups.Count > 1 Then
         For groupCtr As Integer = 1 To match.Groups.Count - 1
            Dim group As Group = match.Groups(groupCtr)         
            Console.WriteLine("   Group: {0}: '{1}' at position {2}.", 
                              groupCtr, group.Value, group.Index)
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               captureCtr += 1
               Console.WriteLine("      Capture: {0}: '{1}' at position {2}.", 
                                 captureCtr, capture.Value, capture.Index)
            Next   
         Next
      End If
      Console.WriteLine()

      pattern = "(a\1|(?(1)\1)){2}"
      Console.WriteLine("Regex pattern: {0}", pattern)
      match = Regex.Match(input, pattern)
         Console.WriteLine("Matched '{0}' at position {1}.", 
                           match.Value, match.Index)
      If match.Groups.Count > 1 Then
         For groupCtr As Integer = 1 To match.Groups.Count - 1
            Dim group As Group = match.Groups(groupCtr)         
            Console.WriteLine("   Group: {0}: '{1}' at position {2}.", 
                              groupCtr, group.Value, group.Index)
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               captureCtr += 1
               Console.WriteLine("      Capture: {0}: '{1}' at position {2}.", 
                                 captureCtr, capture.Value, capture.Index)
            Next   
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Regex pattern: (a\1|(?(1)\1)){0,2}
'       Match: '' at position 0.
'          Group: 1: '' at position 0.
'             Capture: 1: '' at position 0.
'       
'       Regex pattern: (a\1|(?(1)\1)){2}
'       Matched 'a' at position 0.
'          Group: 1: 'a' at position 0.
'             Capture: 1: '' at position 0.
'             Capture: 2: 'a' at position 0.
```

## <a name="see-also"></a>Voir aussi

[Langage des expressions régulières - Aide-mémoire](quick-ref.md)

[Retour sur trace dans les expressions régulières](backtracking.md)




<!--HONumber=Nov16_HO3-->


