---
title: "Substitutions dans les expressions régulières"
description: "Substitutions dans les expressions régulières"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 0fded615-1021-4468-a644-b491814305c6
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 3e02d18d6566c67c7fff7003671f340f97b0dfce

---

# <a name="substitutions-in-regular-expressions"></a>Substitutions dans les expressions régulières

Les substitutions sont des éléments de langage reconnus uniquement dans des modèles de remplacement. Elles utilisent un modèle d'expression régulière pour définir tout ou partie du texte qui doit remplacer le texte correspondant dans la chaîne d'entrée. Le modèle de remplacement peut se composer d’une ou plusieurs substitutions avec des caractères littéraux. Des modèles de remplacement sont fournis aux surcharges de la méthode [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions)) ayant un paramètre de *remplacement* et à la méthode [Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)). Les méthodes remplacent le modèle correspondant par le modèle défini par le paramètre de *remplacement*.

.NET définit les éléments de substitution répertoriés dans le tableau suivant.

Substitution | Description
------------ | ----------- 
**$**_nombre_ | Inclut la dernière sous-chaîne correspondant au groupe de capture identifié par *nombre*, où *nombre* est une valeur décimale, dans la chaîne de remplacement. Pour plus d’informations, consultez [Substitution d’un groupe numéroté](#substituting-a-numbered-group).
**${**_nom_**}** | Inclut la dernière sous-chaîne correspondant au groupe nommé désigné par **(?<**_nom_**>)** dans la chaîne de remplacement. Pour plus d’informations, consultez [Substitution d’un groupe nommé](#substituting-a-named-group).
**$$** | Inclut un littéral « $ » unique dans la chaîne de remplacement. Pour plus d’informations, consultez [Substitution d’un caractère « $ »](#substituting-a--character).
**$&** | Inclut une copie de la correspondance entière dans la chaîne de remplacement. Pour plus d’informations, consultez [Substitution de la correspondance entière](#substituting-the-entire-match).
**$`** | Inclut tout le texte de la chaîne d'entrée avant la correspondance dans la chaîne de remplacement. Pour plus d’informations, consultez [Substitution du texte avant la correspondance](#substituting-the-text-before-the-match).
**$'** | Inclut tout le texte de la chaîne d'entrée après la correspondance dans la chaîne de remplacement. Pour plus d’informations, consultez [Substitution du texte après la correspondance](#substituting-the-text-after-the-match). 
**$+** | Inclut le dernier groupe capturé dans la chaîne de remplacement. Pour plus d’informations, consultez [Substitution du dernier groupe capturé](#substituting-the-last-captured-group).
**$_** | Inclut la chaîne d'entrée entière dans la chaîne de remplacement. Pour plus d’informations, consultez [Substitution de la chaîne d’entrée entière](#substituting-the-entire-input-string).
 
## <a name="substitution-elements-and-replacement-patterns"></a>Éléments de substitution et modèles de remplacement

Les substitutions sont les seules constructions particulières acceptées dans un modèle de remplacement. Aucun des autres éléments de langage d’expression régulière, notamment les caractères d’échappement et le point (**.**), qui correspond à n’importe quel caractère, n’est pris en charge. De la même façon, les éléments de langage de substitution sont reconnus uniquement dans les modèles de remplacement et ne sont jamais valides dans les modèles d’expressions régulières. 

Le seul caractère qui peut apparaître dans un modèle d’expression régulière ou dans une substitution est le caractère **$**, bien qu’il ait une signification différente dans chaque contexte. Dans un modèle d’expression régulière, **$** est une ancre qui correspond à la fin de la chaîne. Dans un modèle de remplacement, **$** indique le début d’une substitution. 

> [!NOTE]
> Pour les fonctionnalités semblables à un modèle de remplacement dans une expression régulière, utilisez une référence arrière. Pour plus d’informations sur les références arrière, consultez [Constructions de références arrière](backreference.md).
 
## <a name="substituting-a-numbered-group"></a>Substitution d’un groupe numéroté

L’élément de langage **$**_nombre_ inclut la dernière sous-chaîne correspondant au groupe de capture nombre dans la chaîne de remplacement, où *nombre* est l’index du groupe de capture. Par exemple, le modèle de remplacement `$1` indique que la sous-chaîne correspondante sera remplacée par le premier groupe capturé. Pour plus d’informations sur les groupes de capture numérotés, consultez [Constructions de regroupement dans les expressions régulières](grouping.md).

Tous les chiffres qui suivent **$** sont interprétés comme appartenant au groupe nombre. Si ce n'est pas votre intention, vous pouvez remplacer un groupe nommé à la place. Par exemple, vous pouvez utiliser la chaîne de remplacement **${1}1** au lieu de **$11** pour définir la chaîne de remplacement comme la valeur du premier groupe capturé avec le numéro « 1 ». Pour plus d’informations, consultez [Substitution d’un groupe nommé](#substituting-a-named-group). 

Les groupes de capture auxquels des noms ne sont pas explicitement assignés à l’aide de la syntaxe **(?<**_nom-**>)** sont numérotés de gauche à droite en commençant à un. Les groupes nommés sont également numérotés de gauche à droite, en démarrant à un numéro de plus que l'index du dernier groupe sans nom. Par exemple, dans l'expression régulière `(\w)(?<digit>\d)`, l'index du groupe nommé `digit` est 2.

Si *nombre* ne spécifie pas un groupe de capture valide défini dans le modèle d’expression régulière, **$**_nombre_ est interprété comme une séquence de caractères littéraux utilisée pour remplacer chaque correspondance.

L’exemple suivant utilise la substitution **$**_nombre_ pour supprimer le symbole monétaire d’une valeur décimale. Elle supprime les symboles monétaires trouvés au début ou à la fin d'une valeur monétaire, et reconnaît les deux séparateurs décimaux les plus courants (« . » et « , »). 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*";
      string replacement = "$1";
      string input = "$16.32 12.19 £16.29 €18.29  €18,29";
      string result = Regex.Replace(input, pattern, replacement);
      Console.WriteLine(result);
   }
}
// The example displays the following output:
//       16.32 12.19 16.29 18.29  18,29
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*"
      Dim replacement As String = "$1"
      Dim input As String = "$16.32 12.19 £16.29 €18.29  €18,29"
      Dim result As String = Regex.Replace(input, pattern, replacement)
      Console.WriteLine(result)
   End Sub
End Module
' The example displays the following output:
'       16.32 12.19 16.29 18.29  18,29
```

Le modèle d'expression régulière `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`\p{Sc}*` | Mettre en correspondance zéro ou plusieurs caractères de symbole monétaire.
`\s?` | Mettre en correspondance zéro ou des espaces blancs.
`\d+` | Mettre en correspondance un ou plusieurs chiffres décimaux.
`[.,]?` | Mettre en correspondance zéro ou un point ou une virgule.
`\d*` | Met en correspondance zéro ou plusieurs chiffres décimaux.
`(\s?\d+[.,]?\d*)` | Mettre en correspondance un espace blanc suivi par un ou plusieurs chiffres décimaux, suivi par zéro ou un point ou une virgule, suivi par zéro ou plusieurs chiffres décimaux. Il s'agit du premier groupe de capture. Étant donné que le modèle de remplacement est `$1`, l’appel à la méthode [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions)) remplace l’intégralité de la sous-chaîne correspondante par ce groupe capturé. 
 
## <a name="substituting-a-named-group"></a>Substitution d’un groupe nommé

L’élément de langage **${**_nom_**}** substitue la dernière sous-chaîne correspondante au groupe de capture *nom*, où *nom* est le nom d’un groupe de capture défini par l’élément de langage **(?<**_nom_**>)**. Pour plus d’informations sur les groupes de capture nommés, consultez [Constructions de regroupement dans les expressions régulières](grouping.md).

Si *nom* ne spécifie pas de groupe de capture nommé valide défini dans le modèle d’expression régulière mais se compose de chiffres, **${**_nom_**}** est interprété comme groupe numéroté. 

Si *nom* ne spécifie ni un groupe de capture nommé valide ni un groupe de capture numéroté valide défini dans le modèle d’expression régulière, **${**_nom_**}** est interprété comme une séquence de caractères littéraux utilisée pour remplacer chaque correspondance.

L’exemple suivant utilise la substitution **${**_nom_**}** pour supprimer le symbole monétaire d’une valeur décimale. Elle supprime les symboles monétaires trouvés au début ou à la fin d'une valeur monétaire, et reconnaît les deux séparateurs décimaux les plus courants (« . » et « , »).

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\p{Sc}*(?<amount>\s?\d+[.,]?\d*)\p{Sc}*";
      string replacement = "${amount}";
      string input = "$16.32 12.19 £16.29 €18.29  €18,29";
      string result = Regex.Replace(input, pattern, replacement);
      Console.WriteLine(result);
   }
}
// The example displays the following output:
//       16.32 12.19 16.29 18.29  18,29
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\p{Sc}*(?<amount>\s?\d+[.,]?\d*)\p{Sc}*"
      Dim replacement As String = "${amount}"
      Dim input As String = "$16.32 12.19 £16.29 €18.29  €18,29"
      Dim result As String = Regex.Replace(input, pattern, replacement)
      Console.WriteLine(result)
   End Sub
End Module
' The example displays the following output:
'       16.32 12.19 16.29 18.29  18,29
```

Le modèle d'expression régulière `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` est défini comme indiqué dans le tableau suivant. 

Modèle | Description
------- | -----------
`\p{Sc}*` | Mettre en correspondance zéro ou plusieurs caractères de symbole monétaire.
`\s?` | Mettre en correspondance zéro ou des espaces blancs.
`\d+` | Mettre en correspondance un ou plusieurs chiffres décimaux.
`[.,]?` | Mettre en correspondance zéro ou un point ou une virgule.
`\d*` | Met en correspondance zéro ou plusieurs chiffres décimaux.
`(?<amount>\s?\d[.,]?\d*)` | Mettre en correspondance un espace blanc, suivi par un ou plusieurs chiffres décimaux, suivi par zéro ou un point ou une virgule, suivi par zéro ou plusieurs chiffres décimaux. C’est le groupe de capture nommé amount. Étant donné que le modèle de remplacement est `${amount}`, l’appel à la méthode [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions)) remplace l’intégralité de la sous-chaîne correspondante par ce groupe capturé. 
 
## <a name="substituting-a-character"></a>Substitution d’un caractère $

La substitution **$$** insère un caractère « $ » littéral dans la chaîne remplacée. 

L’exemple suivant utilise l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) pour déterminer le symbole monétaire de la culture actuelle et son positionnement dans une chaîne monétaire. Il génère alors à la fois dynamiquement un modèle d’expression régulière et un modèle de remplacement. Si l'exemple est exécuté sur un ordinateur dont la culture actuelle est en-US, il génère le modèle d'expression régulière `\b(\d+)(\.(\d+))?` et le modèle de remplacement `$$ $1$2`. Le modèle de remplacement remplace le texte correspondant par un symbole monétaire et un espace suivi par les premier et second groupes capturés.

```csharp
using System;
using System.Globalization;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      // Define array of decimal values.
      string[] values= { "16.35", "19.72", "1234", "0.99"};
      // Determine whether currency precedes (True) or follows (False) number.
      bool precedes = NumberFormatInfo.CurrentInfo.CurrencyPositivePattern % 2 == 0;
      // Get decimal separator.
      string cSeparator = NumberFormatInfo.CurrentInfo.CurrencyDecimalSeparator;
      // Get currency symbol.
      string symbol = NumberFormatInfo.CurrentInfo.CurrencySymbol;
      // If symbol is a "$", add an extra "$".
      if (symbol == "$") symbol = "$$";

      // Define regular expression pattern and replacement string.
      string pattern = @"\b(\d+)(" + cSeparator + @"(\d+))?"; 
      string replacement = "$1$2";
      replacement = precedes ? symbol + " " + replacement : replacement + " " + symbol;
      foreach (string value in values)
         Console.WriteLine("{0} --> {1}", value, Regex.Replace(value, pattern, replacement));
   }
}
// The example displays the following output:
//       16.35 --> $ 16.35
//       19.72 --> $ 19.72
//       1234 --> $ 1234
//       0.99 --> $ 0.99
```

```vb
Imports System.Globalization
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      ' Define array of decimal values.
      Dim values() As String = { "16.35", "19.72", "1234", "0.99"}
      ' Determine whether currency precedes (True) or follows (False) number.
      Dim precedes As Boolean = (NumberFormatInfo.CurrentInfo.CurrencyPositivePattern Mod 2 = 0)
      ' Get decimal separator.
      Dim cSeparator As String = NumberFormatInfo.CurrentInfo.CurrencyDecimalSeparator
      ' Get currency symbol.
      Dim symbol As String = NumberFormatInfo.CurrentInfo.CurrencySymbol
      ' If symbol is a "$", add an extra "$".
      If symbol = "$" Then symbol = "$$"

      ' Define regular expression pattern and replacement string.
      Dim pattern As String = "\b(\d+)(" + cSeparator + "(\d+))?" 
      Dim replacement As String = "$1$2"
      replacement = If(precedes, symbol + " " + replacement, replacement + " " + symbol)
      For Each value In values
         Console.WriteLine("{0} --> {1}", value, Regex.Replace(value, pattern, replacement))
      Next
   End Sub
End Module
' The example displays the following output:
'       16.35 --> $ 16.35
'       19.72 --> $ 19.72
'       1234 --> $ 1234
'       0.99 --> $ 0.99
```

Le modèle d'expression régulière `\b(\d+)(\.(\d+))?` est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`\b` | Démarrer la correspondance au début d'une limite de mot.
`(\d+)` | Mettre en correspondance un ou plusieurs chiffres décimaux. Il s'agit du premier groupe de capture.
`\.` | Mettre en correspondance un point (le séparateur décimal).
`(\d+)` | Mettre en correspondance un ou plusieurs chiffres décimaux. Il s'agit du troisième groupe de capture.
`(\.(\d+))?` | Mettre en correspondance zéro ou une occurrence d'un point suivi par un ou plusieurs chiffres décimaux. Il s'agit du deuxième groupe de capture.
 
## <a name="substituting-the-entire-match"></a>Substitution de la correspondance entière

La substitution **$&** inclut la correspondance entière dans la chaîne de remplacement. Souvent, elle est utilisée pour ajouter une sous-chaîne au début ou à la fin de la chaîne correspondante. Par exemple, le modèle de remplacement `($&)` ajoute des parenthèses au début et à la fin de chaque correspondance. S’il n’y a pas de correspondance, la substitution **$&** n’a aucun effet.

L’exemple suivant utilise la substitution **$&** pour ajouter des guillemets au début et à la fin de titres de livres stockés dans un tableau de chaînes.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"^(\w+\s?)+$";
      string[] titles = { "A Tale of Two Cities", 
                          "The Hound of the Baskervilles", 
                          "The Protestant Ethic and the Spirit of Capitalism", 
                          "The Origin of Species" };
      string replacement = "\"$&\"";
      foreach (string title in titles)
         Console.WriteLine(Regex.Replace(title, pattern, replacement));
   }
}
// The example displays the following output:
//       "A Tale of Two Cities"
//       "The Hound of the Baskervilles"
//       "The Protestant Ethic and the Spirit of Capitalism"
//       "The Origin of Species"
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "^(\w+\s?)+$"
      Dim titles() As String = { "A Tale of Two Cities", _
                                 "The Hound of the Baskervilles", _
                                 "The Protestant Ethic and the Spirit of Capitalism", _
                                 "The Origin of Species" }
      Dim replacement As String = """$&"""
      For Each title As String In titles
         Console.WriteLine(Regex.Replace(title, pattern, replacement))
      Next  
   End Sub
End Module
' The example displays the following output:
'       "A Tale of Two Cities"
'       "The Hound of the Baskervilles"
'       "The Protestant Ethic and the Spirit of Capitalism"
'       "The Origin of Species"
```

Le modèle d'expression régulière `^(\w+\s?)+$` est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`^` | Commencer la correspondance au début de la chaîne d'entrée.
`(\w+\s?)+` | Mettre en correspondance le modèle d'un ou plusieurs caractères de mot, suivis de zéro ou d'un espace blanc, une ou plusieurs fois. 
`$` | Mettre en correspondance la fin de la chaîne d'entrée.

Le modèle de remplacement `"$&"` ajoute un guillemet littéral au début et à la fin de chaque correspondance.

## <a name="substituting-the-text-before-the-match"></a>Substitution du texte avant la correspondance

La substitution **$`** substitution replaces the matched string with the entire input string before the match. That is, it duplicates the input string up to the match while removing the matched text. Any text that follows the matched text is unchanged in the result string. If there are multiple matches in an input string, the replacement text is derived from the original input string, rather than from the string in which text has been replaced by earlier matches. (The example provides an illustration.) If there is no match, the **$`** n’a aucun effet.

L'exemple suivant utilise le modèle d'expression régulière `\d+` pour faire correspondre une séquence d'un ou de plusieurs chiffres décimaux dans la chaîne d'entrée. La chaîne de remplacement **$`** remplace ces chiffres par le texte qui précède la correspondance. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "aa1bb2cc3dd4ee5";
      string pattern = @"\d+";
      string substitution = "$`";
      Console.WriteLine("Matches:");
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);

      Console.WriteLine("Input string:  {0}", input);
      Console.WriteLine("Output string: " + 
                        Regex.Replace(input, pattern, substitution));
   }
}
// The example displays the following output:
//    Matches:
//       1 at position 2
//       2 at position 5
//       3 at position 8
//       4 at position 11
//       5 at position 14
//    Input string:  aa1bb2cc3dd4ee5
//    Output string: aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddeeaa1bb2cc3dd4ee
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "aa1bb2cc3dd4ee5"
      Dim pattern As String = "\d+"
      Dim substitution As String = "$`"
      Console.WriteLine("Matches:")
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
      Console.WriteLine("Input string:  {0}", input)
      Console.WriteLine("Output string: " + _
                        Regex.Replace(input, pattern, substitution))
   End Sub
End Module
' The example displays the following output:
'    Matches:
'       1 at position 2
'       2 at position 5
'       3 at position 8
'       4 at position 11
'       5 at position 14
'    Input string:  aa1bb2cc3dd4ee5
'    Output string: aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddeeaa1bb2cc3dd4ee
```

Dans cet exemple, la chaîne d'entrée `"aa1bb2cc3dd4ee5"` contient cinq correspondances. Le tableau suivant illustre la manière dont la substitution $` entraîne le remplacement de chaque correspondance dans la chaîne d’entrée par le moteur d’expression régulière. Le texte inséré est affiché en gras dans la colonne de résultats.

Faire correspondre à | Position | Chaîne avant la correspondance | Chaîne de résultat
----- | -------- | ------------------- | -------------
1 | 2 | aa | aa**aa**bb2cc3dd4ee5
2 | 5 | aa1bb | aaaabb**aa1bb**cc3dd4ee5
3 | 8 | aa1bb2cc | aaaabbaa1bbcc**aa1bb2cc**dd4ee5
4 | 11 | aa1bb2cc3dd | aaaabbaa1bbccaa1bb2ccdd**aa1bb2cc3dd**ee5
5 | 14 | aa1bb2cc3dd4ee | aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddee **aa1bb2cc3dd4ee**
 
## <a name="substituting-the-text-after-the-match"></a>Substitution du texte après la correspondance

La substitution **$'** remplace la chaîne correspondante par la chaîne d’entrée entière après la correspondance. Autrement dit, elle duplique la chaîne d'entrée après la correspondance en supprimant le texte correspondant. N'importe quel texte qui précède le texte correspondant est inchangé dans la chaîne de résultat. S’il n’y a pas de correspondance, la substitution **$'** n’a aucun effet.

L'exemple suivant utilise le modèle d'expression régulière `\d+` pour faire correspondre une séquence d'un ou de plusieurs chiffres décimaux dans la chaîne d'entrée. La chaîne de remplacement **$'** remplace ces chiffres par le texte qui suit la correspondance. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "aa1bb2cc3dd4ee5";
      string pattern = @"\d+";
      string substitution = "$'";
      Console.WriteLine("Matches:");
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
      Console.WriteLine("Input string:  {0}", input);
      Console.WriteLine("Output string: " + 
                        Regex.Replace(input, pattern, substitution));
   }
}
// The example displays the following output:
//    Matches:
//       1 at position 2
//       2 at position 5
//       3 at position 8
//       4 at position 11
//       5 at position 14
//    Input string:  aa1bb2cc3dd4ee5
//    Output string: aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddeeaa1bb2cc3dd4ee
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "aa1bb2cc3dd4ee5"
      Dim pattern As String = "\d+"
      Dim substitution As String = "$'"
      Console.WriteLine("Matches:")
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
      Console.WriteLine("Input string:  {0}", input)
      Console.WriteLine("Output string: " + _
                        Regex.Replace(input, pattern, substitution))
   End Sub
End Module
' The example displays the following output:
'    Matches:
'       1 at position 2
'       2 at position 5
'       3 at position 8
'       4 at position 11
'       5 at position 14
'    Input string:  aa1bb2cc3dd4ee5
'    Output string: aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddeeaa1bb2cc3dd4ee
```

Dans cet exemple, la chaîne d'entrée `"aa1bb2cc3dd4ee5"` contient cinq correspondances. Le tableau suivant illustre la manière dont la substitution **$'** entraîne le remplacement de chaque correspondance dans la chaîne d’entrée par le moteur d’expression régulière. Le texte inséré est affiché en gras dans la colonne de résultats.

Faire correspondre à | Position | Chaîne avant la correspondance | Chaîne de résultat
----- | -------- | ------------------- | -------------
1 | 2 | bb2cc3dd4ee5 | aa**bb2cc3dd4ee5**bb2cc3dd4ee5
2 | 5 | cc3dd4ee5 | aabb2cc3dd4ee5bb**cc3dd4ee5**cc3dd4ee5
3 | 8 | dd4ee5 | aabb2cc3dd4ee5bbcc3dd4ee5cc**dd4ee5**dd4ee5
4 | 11 | ee5 | aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5dd**ee5**ee5
5 | 14 | [String.Empty](xref:System.String.Empty) | aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5ddee5ee
 
## <a name="substituting-the-last-captured-group"></a>Substitution du dernier groupe capturé

La substitution **$+** remplace la chaîne correspondante par le dernier groupe capturé. S’il n’y a pas de groupes capturés ou si la valeur du dernier groupe capturé est [String.Empty](xref:System.String.Empty), la substitution **$+** n’a aucun effet.

L’exemple suivant identifie des mots en double dans une chaîne et utilise la substitution **$+** pour les remplacer par une occurrence unique du mot. L’option [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) est utilisée pour vérifier que les mots, qui diffèrent en termes de casse mais qui sont identiques par ailleurs, sont considérés comme des doublons.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\w+)\s\1\b";
      string substitution = "$+";
      string input = "The the dog jumped over the fence fence.";
      Console.WriteLine(Regex.Replace(input, pattern, substitution, 
                        RegexOptions.IgnoreCase));
   }
}
// The example displays the following output:
//      The dog jumped over the fence.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\w+)\s\1\b"
      Dim substitution As String = "$+"
      Dim input As String = "The the dog jumped over the fence fence."
      Console.WriteLine(Regex.Replace(input, pattern, substitution, _
                                      RegexOptions.IgnoreCase))
   End Sub
End Module
' The example displays the following output:
'      The dog jumped over the fence.
```

Le modèle d'expression régulière `\b(\w+)\s\1\b` est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`\b` | Commencer la correspondance à la limite d'un mot.
`(\w+)` | Mettre en correspondance un ou plusieurs caractères alphabétiques. Il s'agit du premier groupe de capture.
`\s` | Mettre en correspondance un espace blanc.
`\1` | Mettre en correspondance le premier groupe capturé.
`\b` | Terminer la correspondance à la limite d'un mot.
 
## <a name="substituting-the-entire-input-string"></a>Substitution de la chaîne d’entrée entière

La substitution **$_** remplace la chaîne correspondante par la chaîne d’entrée entière. Autrement dit, elle supprime le texte correspondant et le remplace par la chaîne entière, notamment le texte correspondant.

L'exemple suivant correspond à un ou plusieurs chiffres décimaux dans la chaîne d'entrée. Il utilise la substitution **$_** pour les remplacer par la chaîne d’entrée entière.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "ABC123DEF456";
      string pattern = @"\d+";
      string substitution = "$_";
      Console.WriteLine("Original string:          {0}", input);
      Console.WriteLine("String with substitution: {0}", 
                        Regex.Replace(input, pattern, substitution));      
   }
}
// The example displays the following output:
//       Original string:          ABC123DEF456
//       String with substitution: ABCABC123DEF456DEFABC123DEF456
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "ABC123DEF456"
      Dim pattern As String = "\d+"
      Dim substitution As String = "$_"
      Console.WriteLine("Original string:          {0}", input)
      Console.WriteLine("String with substitution: {0}", _
                        Regex.Replace(input, pattern, substitution))      
   End Sub
End Module
' The example displays the following output:
'       Original string:          ABC123DEF456
'       String with substitution: ABCABC123DEF456DEFABC123DEF456
```

Dans cet exemple, la chaîne d'entrée `"ABC123DEF456"` contient deux correspondances. Le tableau suivant illustre la manière dont la substitution **$_** entraîne le remplacement de chaque correspondance dans la chaîne d’entrée par le moteur d’expression régulière. Le texte inséré est affiché en gras dans la colonne de résultats.

Faire correspondre à | Position | Chaîne avant la correspondance | Chaîne de résultat
----- | -------- | ------------------- | -------------
1 | 3 | 123 | ABC**ABC123DEF456**DEF456
2 | 5 | 456 | ABCABC123DEF456DEF**ABC123DEF456**
 
## <a name="see-also"></a>Voir aussi

[Langage des expressions régulières - Aide-mémoire](quick-ref.md)




<!--HONumber=Nov16_HO1-->


