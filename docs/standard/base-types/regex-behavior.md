---
title: "Comportement détaillé des expressions régulières"
description: "Comportement détaillé des expressions régulières"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 6f11047f-45a4-4caf-a259-18abe08cc0d2
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: fa0513a5b450742995bd86fca495ba9904e7361b

---

# <a name="details-of-regular-expression-behavior"></a>Comportement détaillé des expressions régulières


Le moteur d’expression régulière .NET est un analyseur d’expression régulière rétroactive qui incorpore un moteur NFA (Nondeterministic Finite Automaton) tel que celui utilisé par Perl, Python, Emacs et Tcl. Cette particularité le distingue des moteurs d’expression régulière pure DFA (Deterministic Finite Automaton) plus rapides, mais plus limités, comme ceux d’awk, egrep ou lex. Elle le distingue également des moteurs NFA POSIX standardisés, mais plus lents. La section suivante décrit les trois types de moteurs d’expression régulière et explique pourquoi les expressions régulières dans .NET sont implémentées à l’aide d’un moteur NFA classique.

## <a name="benefits-of-the-nfa-engine"></a>Avantages du moteur NFA

Quand les moteurs DFA exécutent des critères spéciaux, leur ordre de traitement est piloté par la chaîne d’entrée. Les moteurs commencent au début de la chaîne d’entrée et continuent de manière séquentielle pour déterminer si le caractère suivant correspond au modèle d’expression régulière. Ils peuvent garantir une correspondance avec la chaîne la plus longue possible. Étant donné qu’ils ne testent jamais le même caractère deux fois, les moteurs DFA ne prennent pas en charge la rétroaction. Toutefois, étant donné qu’un moteur DFA contient uniquement un état fini, il ne peut pas rechercher un modèle avec des références arrière, et comme il ne construit pas d’expansion explicite, il ne peut pas capturer de sous-expressions.

Contrairement aux moteurs DFA, quand les moteurs NFA classiques exécutent des critères spéciaux, leur ordre de traitement est piloté par le modèle d’expression régulière. Lorsqu’il traite un élément de langage particulier, le moteur utilise une correspondance gourmande ; autrement dit, il cherche la chaîne d’entrée la plus longue possible. Mais il enregistre également son état après avoir trouvé la correspondance correcte d’une sous-expression. Si une correspondance finit par échouer, le moteur peut revenir à un état enregistré pour tenter d’autres correspondances. Ce processus consistant à abandonner une correspondance réussie de sous-expression pour que les éléments de langage ultérieurs dans l’expression régulière puissent également correspondre est appelé rétroaction. Les moteurs NFA utilisent la rétroaction pour tester toutes les expansions possibles d’une expression régulière dans un ordre spécifique et accepter la première correspondance. Comme un moteur NFA classique construit une expansion spécifique de l’expression régulière pour obtenir une correspondance correcte, il peut capturer des correspondances de sous-expressions et des références arrière correspondantes. Toutefois, comme un moteur NFA classique utilise la rétroaction, il peut visiter le même état plusieurs fois s’il y parvient par différents chemins. Par conséquent, il peut s’exécuter lentement de façon exponentielle dans le pire des cas. Comme un moteur NFA classique accepte la première correspondance trouvée, il peut également en négliger d’autres (éventuellement plus longues).

Les moteurs NFA POSIX sont comme les moteurs NFA classiques, sauf qu’ils poursuivent la rétroaction jusqu’à garantir qu’ils ont trouvé la correspondance la plus longue possible. Ainsi, un moteur NFA POSIX est plus lent qu’un moteur NFA classique. Quand vous utilisez un moteur NFA POSIX, vous ne pouvez pas favoriser une correspondance plus courte au détriment d’une plus longue en modifiant l’ordre de la recherche rétroactive. 

Les moteurs NFA classiques ont la préférence des programmeurs, car ils offrent un meilleur contrôle sur la mise en correspondance de chaînes que les moteurs DFA ou NFA POSIX. Même si, dans le pire des cas, ils peuvent s’exécuter lentement, vous pouvez les amener à trouver des correspondances sur des durées linéaires ou polynomiales à l’aide de modèles qui réduisent les ambiguïtés et limitent la rétroaction. En d’autres termes, même si les moteurs NFA privilégient la puissance et la flexibilité au détriment des performances, ils offrent souvent des performances bonnes à acceptables si une expression régulière est bien écrite et évite les cas dans lesquels la rétroaction dégrade exponentiellement les performances.

> [!NOTE]
> Pour plus d’informations sur la baisse des performances due à la rétroaction excessive et sur les moyens de créer une expression régulière pour y remédier, consultez [Rétroaction dans les expressions régulières](backtracking.md).
 
## <a name="net-framework-engine-capabilities"></a>Fonctionnalités du moteur .NET Framework

Pour tirer parti des avantages d’un moteur NFA classique, le moteur d’expression régulière .NET inclut un ensemble complet de constructions pour permettre aux programmeurs de diriger le moteur de rétroaction. Ces constructions peuvent être utilisées pour rechercher des correspondances plus rapidement ou pour favoriser des expansions spécifiques par rapport à d’autres.

Les autres fonctionnalités du moteur d’expression régulière .NET sont les suivantes : 

### <a name="lazy-quantifiers"></a>Quantificateurs paresseux

Quantificateurs paresseux : **??**, __*?__, **+?**, **{**_n_**,**_m_**}?**. Ces constructions indiquent au moteur de rétroaction de rechercher d’abord le nombre minimal de répétitions. Par opposition, les quantificateurs gourmands ordinaires essaient de trouver d’abord le nombre maximal de répétitions. L’exemple suivant illustre la différence entre les deux. Une expression régulière correspond à une phrase se terminant par un nombre qu’un groupe de capture est destiné à extraire. L’expression régulière `.+(\d+)\.` inclut le quantificateur gourmand `.+`, qui amène le moteur d’expression régulière à capturer uniquement le dernier chiffre du nombre. Par opposition, l’expression régulière `.+?(\d+)\.` inclut le quantificateur paresseux `.+?`, qui amène le moteur d’expression régulière à capturer le nombre entier.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string greedyPattern = @".+(\d+)\.";
      string lazyPattern = @".+?(\d+)\.";
      string input = "This sentence ends with the number 107325.";
      Match match;

      // Match using greedy quantifier .+.
      match = Regex.Match(input, greedyPattern);
      if (match.Success)
         Console.WriteLine("Number at end of sentence (greedy): {0}", 
                           match.Groups[1].Value);
      else
         Console.WriteLine("{0} finds no match.", greedyPattern);
       // Match using lazy quantifier .+?.
      match = Regex.Match(input, lazyPattern);
      if (match.Success)
         Console.WriteLine("Number at end of sentence (lazy): {0}", 
                           match.Groups[1].Value);
      else
         Console.WriteLine("{0} finds no match.", lazyPattern);
   }
}
// The example displays the following output:
//       Number at end of sentence (greedy): 5
//       Number at end of sentence (lazy): 107325
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim greedyPattern As String = ".+(\d+)\."
      Dim lazyPattern As String = ".+?(\d+)\."
      Dim input As String = "This sentence ends with the number 107325."
      Dim match As Match

      ' Match using greedy quantifier .+.
      match = Regex.Match(input, greedyPattern)
      If match.Success Then
         Console.WriteLine("Number at end of sentence (greedy): {0}", 
                           match.Groups(1).Value)
      Else
         Console.WriteLine("{0} finds no match.", greedyPattern)
      End If

      ' Match using lazy quantifier .+?.
      match = Regex.Match(input, lazyPattern)
      If match.Success Then
         Console.WriteLine("Number at end of sentence (lazy): {0}", 
                           match.Groups(1).Value)
      Else
         Console.WriteLine("{0} finds no match.", lazyPattern)
      End If
   End Sub
End Module
' The example displays the following output:
'       Number at end of sentence (greedy): 5
'       Number at end of sentence (lazy): 107325
```

Les versions gourmande et paresseuse de cette expression régulière sont définies comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`.+` (quantificateur gourmand) | Mettre en correspondance au moins une occurrence de n’importe quel caractère. Le moteur d’expression régulière recherche alors la chaîne entière, puis effectue une rétroaction si nécessaire pour trouver le reste du modèle.
`.+?` (quantificateur paresseux) | Mettre en correspondance au moins une occurrence de n’importe quel caractère, mais une quantité la plus petite possible.
`(\d+)` | Mettre en correspondance au moins un caractère numérique et l’assigner au premier groupe de capture.
`\.` | Mettre en correspondance un point.
 
Pour plus d’informations sur les quantificateurs paresseux, consultez [Quantificateurs dans les expressions régulières](quantifiers.md).

### <a name="positive-lookahead"></a>Préanalyse positive

Préanalyse positive : **(?**=_sous-expression_**)**. Cette fonctionnalité permet au moteur de rétroaction de revenir au même endroit dans le texte après avoir mis en correspondance une sous-expression. Elle s’avère utile pour effectuer une recherche dans le texte en vérifiant plusieurs modèles qui démarrent à la même position. Elle permet également au moteur de vérifier qu’une sous-chaîne existe à la fin de la correspondance sans inclure cette sous-chaîne dans le texte correspondant. L’exemple suivant utilise la préanalyse positive pour extraire les mots d’une phrase qui ne sont pas suivis de symboles de ponctuation.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b[A-Z]+\b(?=\P{P})";
      string input = "If so, what comes next?";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       If
//       what
//       comes
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b[A-Z]+\b(?=\P{P})"
      Dim input As String = "If so, what comes next?"
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
         Console.WriteLine(match.Value)
      Next   
   End Sub
End Module
' The example displays the following output:
'       If
'       what
'       comes
```

L'expression régulière `\b[A-Z]+\b(?=\P{P})` est définie comme indiqué dans le tableau suivant.

Motif | Description
------- | -----------
`\b` | Commencer la correspondance à la limite d'un mot.
`[A-Z]+` | Mettre en correspondance un caractère alphabétique une ou plusieurs fois. Étant donné que la méthode [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) est appelée avec l’option [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase), la comparaison ne respecte pas la casse. 
`\b` | Terminer la correspondance à la limite d'un mot.
`(?=\P{P})` | Préanalyser pour déterminer si le caractère suivant est un symbole de ponctuation. Dans la négative, la correspondance réussit.

Pour plus d’informations sur les assertions de préanalyse positive, consultez [Constructions de regroupement dans les expressions régulières](grouping.md).

### <a name="negative-lookahead"></a>Préanalyse négative

Préanalyse négative : **(?!**_sous-expression_**)**. Cette fonctionnalité ajoute la possibilité de mettre en correspondance une expression uniquement si une sous-expression ne correspond pas. Elle s’avère particulièrement efficace pour affiner une recherche, car il est souvent plus simple de fournir une expression pour un cas à éliminer qu’une expression pour les cas à inclure. Par exemple, il est difficile d’écrire une expression pour les mots qui ne commencent pas par « non ». L’exemple suivant utilise la préanalyse négative pour les exclure.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(?!non)\w+\b";
      string input = "Nonsense is not always non-functional.";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       is
//       not
//       always
//       functional
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(?!non)\w+\b"
      Dim input As String = "Nonsense is not always non-functional."
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       is
'       not
'       always
'       functional
```

Le modèle d'expression régulière `\b(?!non)\w+\b` est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`\b` | Commencer la correspondance à la limite d'un mot.
`(?!non)` | Préanalyser pour garantir que la chaîne actuelle ne commence pas par « non ». Si c’est le cas, la correspondance échoue.
`(\w+)` | Mettre en correspondance un ou plusieurs caractères alphabétiques.
`\b` | Terminer la correspondance à la limite d'un mot.
 
Pour plus d’informations sur les assertions de préanalyse négative, consultez [Constructions de regroupement dans les expressions régulières](grouping.md).

### <a name="conditional-evaluation"></a>Évaluation conditionnelle

Évaluation conditionnelle : **(?(**_expression_**)**_oui_&#124;_non_**)** et**(?(**_nom_**)**_oui_&#124;_non_**)**, où *expression* est une sous-expression à trouver, *nom* est le nom d’un groupe de capture, *oui* est la chaîne à trouver si *expression* est trouvée ou *nom* est un groupe capturé valide et non vide, et *non* est la sous-expression à trouver si *expression* est introuvable ou *nom* n’est pas un groupe capturé valide et non vide. Grâce à cette fonctionnalité, le moteur peut rechercher à l’aide de plusieurs autres modèles, selon le résultat d’une correspondance de sous-expression précédente ou le résultat d’une assertion de largeur nulle. Cette fonctionnalité permet une forme plus puissante de référence arrière qui permet, par exemple, de rechercher une sous-expression en fonction d’une sous-expression précédente trouvée. L’expression régulière utilisée dans l’exemple suivant trouve les paragraphes destinés à une utilisation à la fois interne et publique. Les paragraphes destinés à un usage interne uniquement commencent par une balise `<PRIVATE>`. Le modèle d’expression régulière `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` utilise une évaluation conditionnelle pour assigner le contenu des paragraphes destinés à une utilisation publique et interne à des groupes de capture distincts. Ces paragraphes peuvent ensuite être gérés différemment.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "<PRIVATE> This is not for public consumption." + Environment.NewLine + 
                     "But this is for public consumption." + Environment.NewLine + 
                     "<PRIVATE> Again, this is confidential.\n";  
      string pattern = @"^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$";
      string publicDocument = null, privateDocument = null;

      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.Multiline))
      {
         if (match.Groups[1].Success) {
            privateDocument += match.Groups[1].Value + "\n";
         }
         else {
            publicDocument += match.Groups[3].Value + "\n";   
            privateDocument += match.Groups[3].Value + "\n";
         }  
      }

      Console.WriteLine("Private Document:");
      Console.WriteLine(privateDocument);
      Console.WriteLine("Public Document:");
      Console.WriteLine(publicDocument);
   }
}
// The example displays the following output:
//    Private Document:
//    This is not for public consumption.
//    But this is for public consumption.
//    Again, this is confidential.
//    
//    Public Document:
//    But this is for public consumption.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "<PRIVATE> This is not for public consumption." + vbCrLf + _
                            "But this is for public consumption." + vbCrLf + _
                            "<PRIVATE> Again, this is confidential." + vbCrLf
      Dim pattern As String = "^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$"
      Dim publicDocument As String = Nothing
      Dim privateDocument As String = Nothing

      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.Multiline)
         If match.Groups(1).Success Then
            privateDocument += match.Groups(1).Value + vbCrLf
         Else
            publicDocument += match.Groups(3).Value + vbCrLf   
            privateDocument += match.Groups(3).Value + vbCrLf
         End If  
      Next

      Console.WriteLine("Private Document:")
      Console.WriteLine(privateDocument)
      Console.WriteLine("Public Document:")
      Console.WriteLine(publicDocument)
   End Sub
End Module
' The example displays the following output:
'    Private Document:
'    This is not for public consumption.
'    But this is for public consumption.
'    Again, this is confidential.
'    
'    Public Document:
'    But this is for public consumption.
```

Le modèle d’expression régulière est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`^` | Commencer la correspondance au début d’une ligne.
`(?<Pvt>\<PRIVATE\>\s)?` | Mettre en correspondance zéro ou une occurrence de la chaîne `<PRIVATE>` suivie d’un espace blanc. Assigner la correspondance à un groupe de capture nommé Pvt.
`(?(Pvt)((\w+\p{P}?\s)+)` | Si le groupe de capture `Pvt` existe, mettre en correspondance une ou plusieurs occurrences d’un ou plusieurs caractères de mot suivis de zéro ou un séparateur de ponctuation suivi d’un espace blanc. Assigner la sous-chaîne au premier groupe de capture.
`&#124;((\w+\p{P}?\s)+))` | Si le groupe de capture `Pvt` n’existe pas, mettre en correspondance une ou plusieurs occurrences d’un ou plusieurs caractères de mot suivis de zéro ou un séparateur de ponctuation suivi d’un espace blanc. Assigner la sous-chaîne au troisième groupe de capture.
`\r?$` | Mettre en correspondance la fin d’une ligne ou la fin de la chaîne.
 
Pour plus d’informations sur l’évaluation conditionnelle, consultez [Constructions d’alternative dans les expressions régulières](alternation.md).

### <a name="balancing-group-definitions"></a>Définitions de groupe d'équilibrage

Définitions de groupe d’équilibrage : **(?<**_nom1-nom2_**>** _sous-expression_**)**. Cette fonctionnalité permet au moteur d’expression régulière d’effectuer un suivi des constructions imbriquées telles que les parenthèses ou les crochets ouvrants et fermants. Pour obtenir un exemple, consultez [Constructions de regroupement dans les expressions régulières](grouping.md).

### <a name="nonbacktracking-subexpressions"></a>Sous-expressions non rétroactives

Sous-expressions non rétroactives (également appelées sous-expressions gourmandes) : **(?>**_sous-expression_**)**. Cette fonctionnalité permet au moteur de rétroaction de garantir qu’une sous-expression correspond uniquement à la première correspondance trouvée pour cette sous-expression, comme si l’expression s’exécutait indépendamment de l’expression qui la contient. Si vous n’utilisez pas cette construction, les recherches rétroactives à partir de la plus grande expression peuvent modifier le comportement d’une sous-expression. Par exemple, l’expression régulière `(a+)\w` trouve un ou plusieurs caractères « a », ainsi qu’un caractère de mot qui suit la séquence de caractères « a », puis assigne la séquence de caractères « a » au premier groupe de capture. Toutefois, si le dernier caractère de la chaîne d’entrée est également un « a », il est mis en correspondance par l’élément de langage `\w` et n’est pas inclus dans le groupe capturé.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "aaaaa", "aaaaab" };
      string backtrackingPattern = @"(a+)\w";
      Match match;

      foreach (string input in inputs) {
         Console.WriteLine("Input: {0}", input);
         match = Regex.Match(input, backtrackingPattern);
         Console.WriteLine("   Pattern: {0}", backtrackingPattern);
         if (match.Success) { 
            Console.WriteLine("      Match: {0}", match.Value);
            Console.WriteLine("      Group 1: {0}", match.Groups[1].Value);
         }
         else {
            Console.WriteLine("      Match failed.");
         }   
      }
      Console.WriteLine();            
   }
}
// The example displays the following output:
//       Input: aaaaa
//          Pattern: (a+)\w
//             Match: aaaaa
//             Group 1: aaaa
//       Input: aaaaab
//          Pattern: (a+)\w
//             Match: aaaaab
//             Group 1: aaaaa
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "aaaaa", "aaaaab" }
      Dim backtrackingPattern As String = "(a+)\w"
      Dim match As Match

      For Each input As String In inputs
         Console.WriteLine("Input: {0}", input)
         match = Regex.Match(input, backtrackingPattern)
         Console.WriteLine("   Pattern: {0}", backtrackingPattern)
         If match.Success Then 
            Console.WriteLine("      Match: {0}", match.Value)
            Console.WriteLine("      Group 1: {0}", match.Groups(1).Value)
         Else 
            Console.WriteLine("      Match failed.")
         End If   
      Next
      Console.WriteLine()            
   End Sub
End Module
' The example displays the following output:
'       Input: aaaaa
'          Pattern: (a+)\w
'             Match: aaaaa
'             Group 1: aaaa
'       Input: aaaaab
'          Pattern: (a+)\w
'             Match: aaaaab
'             Group 1: aaaaa
```

L’expression régulière `((?>a+))\w` empêche ce comportement. Étant donné que tous les caractères « a » consécutifs sont trouvés sans rétroaction, le premier groupe de capture inclut tous les caractères « a » consécutifs. Si les caractères « a » ne sont pas suivis d’au moins un caractère autre que « a », la correspondance échoue.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "aaaaa", "aaaaab" };
      string nonbacktrackingPattern = @"((?>a+))\w";
      Match match;

      foreach (string input in inputs) {
         Console.WriteLine("Input: {0}", input);
         match = Regex.Match(input, nonbacktrackingPattern);
         Console.WriteLine("   Pattern: {0}", nonbacktrackingPattern);
         if (match.Success) { 
            Console.WriteLine("      Match: {0}", match.Value);
            Console.WriteLine("      Group 1: {0}", match.Groups[1].Value);
         }
         else {
            Console.WriteLine("      Match failed.");
         }   
      }
      Console.WriteLine();            
   }
}
// The example displays the following output:
//       Input: aaaaa
//          Pattern: ((?>a+))\w
//             Match failed.
//       Input: aaaaab
//          Pattern: ((?>a+))\w
//             Match: aaaaab
//             Group 1: aaaaa
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "aaaaa", "aaaaab" }
      Dim nonbacktrackingPattern As String = "((?>a+))\w"
      Dim match As Match

      For Each input As String In inputs
         Console.WriteLine("Input: {0}", input)
         match = Regex.Match(input, nonbacktrackingPattern)
         Console.WriteLine("   Pattern: {0}", nonbacktrackingPattern)
         If match.Success Then 
            Console.WriteLine("      Match: {0}", match.Value)
            Console.WriteLine("      Group 1: {0}", match.Groups(1).Value)
         Else 
            Console.WriteLine("      Match failed.")
         End If   
      Next
      Console.WriteLine()            
   End Sub
End Module
' The example displays the following output:
'       Input: aaaaa
'          Pattern: ((?>a+))\w
'             Match failed.
'       Input: aaaaab
'          Pattern: ((?>a+))\w
'             Match: aaaaab
'             Group 1: aaaaa
```

Pour plus d’informations sur les sous-expressions non rétroactives, consultez [Constructions de regroupement dans les expressions régulières](grouping.md).

### <a name="right-to-left-matching"></a>Mise en correspondance de droite à gauche

La mise en correspondance de droite à gauche est spécifiée en fournissant l’option [RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft) à une méthode de mise en correspondance de constructeur de classe ou d’instance statique [Regex](xref:System.Text.RegularExpressions.Regex). Cette fonctionnalité s’avère utile lors de la recherche de droite à gauche au lieu de gauche à droite, ou dans les cas où il est plus efficace de commencer une correspondance dans la partie droite du modèle plutôt que la partie gauche. Comme l’illustre l’exemple suivant, l’utilisation de la mise en correspondance de droite à gauche peut modifier le comportement des quantificateurs gourmands. L’exemple effectue deux recherches d’une phrase qui se termine par un nombre. La recherche de gauche à droite qui utilise le quantificateur gourmand `+` trouve l’un des six chiffres dans la phrase, tandis que la recherche de droite à gauche trouve les six chiffres. Pour obtenir la description du modèle d’expression régulière, consultez l’exemple qui illustre les quantificateurs paresseux plus haut dans cette section.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string greedyPattern = @".+(\d+)\.";
      string input = "This sentence ends with the number 107325.";
      Match match;

      // Match from left-to-right using lazy quantifier .+?.
      match = Regex.Match(input, greedyPattern);
      if (match.Success)
         Console.WriteLine("Number at end of sentence (left-to-right): {0}", 
                           match.Groups[1].Value);
      else
         Console.WriteLine("{0} finds no match.", greedyPattern);

      // Match from right-to-left using greedy quantifier .+.
      match = Regex.Match(input, greedyPattern, RegexOptions.RightToLeft);
      if (match.Success)
         Console.WriteLine("Number at end of sentence (right-to-left): {0}", 
                           match.Groups[1].Value);
      else
         Console.WriteLine("{0} finds no match.", greedyPattern);
   }
}
// The example displays the following output:
//       Number at end of sentence (left-to-right): 5
//       Number at end of sentence (right-to-left): 107325
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim greedyPattern As String = ".+(\d+)\."
      Dim input As String = "This sentence ends with the number 107325."
      Dim match As Match

      ' Match from left-to-right using lazy quantifier .+?.
      match = Regex.Match(input, greedyPattern)
      If match.Success Then
         Console.WriteLine("Number at end of sentence (left-to-right): {0}", 
                           match.Groups(1).Value)
      Else
         Console.WriteLine("{0} finds no match.", greedyPattern)
      End If

      ' Match from right-to-left using greedy quantifier .+.
      match = Regex.Match(input, greedyPattern, RegexOptions.RightToLeft)
      If match.Success Then
         Console.WriteLine("Number at end of sentence (right-to-left): {0}", 
                           match.Groups(1).Value)
      Else
         Console.WriteLine("{0} finds no match.", greedyPattern)
      End If
   End Sub
End Module
' The example displays the following output:
'       Number at end of sentence (left-to-right): 5
'       Number at end of sentence (right-to-left): 107325
```

Pour plus d’informations sur la mise en correspondance de droite à gauche, consultez [Options des expressions régulières](options.md).

### <a name="positive-and-negative-lookbehind"></a>Postanalyse positive et négative

Postanalyse positive et négative : **(?<**=_sous-expression_**)** pour une postanalyse positive et **(?<!**_sous-expression_**)** pour une postanalyse négative. Cette fonctionnalité est semblable à la préanalyse décrite précédemment dans cette rubrique. Comme le moteur d’expression régulière autorise une mise en correspondance complète de droite à gauche, les expressions régulières autorisent les postanalyses illimitées. La postanalyse positive et négative peut également servir à éviter d’imbriquer des quantificateurs lorsque la sous-expression imbriquée est un sur-ensemble d’une expression externe. Les expressions régulières comportant ces quantificateurs imbriqués offrent souvent des performances médiocres. L’exemple suivant vérifie qu’une chaîne commence et se termine par un caractère alphanumérique et que tout autre caractère contenu dans la chaîne fait partie d’un sur-ensemble plus grand. Il forme une partie de l’expression régulière utilisée pour valider des adresses e-mail. Pour plus d’informations, consultez [Guide pratique : vérifier que des chaînes sont dans un format d’adresse e-mail valide](verify-format.md).

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "jack.sprat", "dog#", "dog#1", "me.myself", 
                          "me.myself!" };
      string pattern = @"^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$";
      foreach (string input in inputs) {
         if (Regex.IsMatch(input, pattern, RegexOptions.IgnoreCase))
            Console.WriteLine("{0}: Valid", input);
         else
            Console.WriteLine("{0}: Invalid", input);
      }
   }
}
// The example displays the following output:
//       jack.sprat: Valid
//       dog#: Invalid
//       dog#1: Valid
//       me.myself: Valid
//       me.myself!: Invalid
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "jack.sprat", "dog#", "dog#1", "me.myself", 
                                 "me.myself!" }
      Dim pattern As String = "^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$"
      For Each input As String In inputs
         If Regex.IsMatch(input, pattern, RegexOptions.IgnoreCase) Then
            Console.WriteLine("{0}: Valid", input)
         Else
            Console.WriteLine("{0}: Invalid", input)
         End If   
      Next
   End Sub
End Module
' The example displays the following output:
'       jack.sprat: Valid
'       dog#: Invalid
'       dog#1: Valid
'       me.myself: Valid
'       me.myself!: Invalid
```

L'expression régulière `^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$` est définie comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`^` | Commencer la correspondance au début de la chaîne.
`[A-Z0-9]` | Mettre en correspondance n’importe quel caractère numérique ou alphanumérique. (La comparaison respecte la casse.)
`([-!#$%&'.*+/=?^`{}&#124;~\w])*` | Mettre en correspondance zéro, une ou plusieurs occurrences de n’importe quel caractère de mot ou de l’un des caractères suivants : -, !, #, $, %, &, ', ., *, +, /, =, ?, ^, `, {, }, &#124;, ou ~.
`(?<=[A-Z0-9])` | Postanalyser jusqu’au caractère précédent, qui doit être numérique ou alphanumérique. (La comparaison respecte la casse.)
`$` | Termine la correspondance à la fin de la chaîne.
 
Pour plus d’informations sur la postanalyse positive et négative, consultez [Constructions de regroupement dans les expressions régulières](grouping.md).


## <a name="related-topics"></a>Rubriques connexes

Titre | Description
----- | ----------- 
[Rétroaction](backtracking.md) | Fournit des informations sur la manière dont la rétroaction d’expression régulière se ramifie pour trouver d’autres correspondances.
[Compilation et réutilisation](compilation.md) | Fournit des informations sur la compilation et la réutilisation des expressions régulières pour augmenter les performances.
[Cohérence de thread](thread-safety.md) | Fournit des informations sur la sécurité des threads d’expression régulière et explique quand vous devez synchroniser l’accès aux objets d’expression régulière.
[Expressions régulières .NET](regular-expressions.md) | Fournit une vue d’ensemble de l’aspect du langage de programmation des expressions régulières.
[Modèle objet d’expression régulière](object-model.md) | Fournit des informations et des exemples de code illustrant l’utilisation des classes d’expression régulière.
[Exemples d’expressions régulières](regex-examples.md) | Contient des exemples de code qui illustrent l’utilisation des expressions régulières dans des applications courantes.
[Langage des expressions régulières - Aide-mémoire](quick-ref.md) | Fournit des informations sur le jeu de caractères, d’opérateurs et de constructions permettant de définir des expressions régulières.
 
## <a name="reference"></a>Référence

[System.Text.RegularExpressions](xref:System.Text.RegularExpressions)




<!--HONumber=Nov16_HO3-->


