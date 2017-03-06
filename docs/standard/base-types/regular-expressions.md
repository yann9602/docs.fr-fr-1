---
title: "Expressions régulières dans .NET"
description: "Expressions régulières dans .NET"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: d1a640cf-09ca-48f7-800c-a627a6d549c9
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: ac26821819b22aa3ea47e6945bb5c8575dcd9807
ms.lasthandoff: 03/02/2017

---

# <a name="regular-expressions-in-net"></a>Expressions régulières dans .NET

Les expressions régulières permettent de traiter un texte de façon puissante, souple et efficace. Grâce à la syntaxe complète des expressions régulières pour la recherche de correspondance avec un modèle, vous pouvez rapidement analyser des volumes importants de texte pour rechercher des modèles de caractères spécifiques, valider le texte pour vous assurer qu'il correspond à un modèle prédéfini (tel qu'une adresse e-mail), extraire, modifier, remplacer ou supprimer des sous-chaînes de texte et ajouter les chaînes extraites à une collection afin de générer un rapport. Pour de nombreuses applications qui traitent des chaînes ou qui analysent de grands blocs de texte, les expressions régulières constituent un outil indispensable.

## <a name="how-regular-expressions-work"></a>Fonctionnement des expressions régulières

La pièce maîtresse du traitement d’un texte avec des expressions régulières est le moteur d’expression régulière, représenté par l’objet [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) dans .NET. Au minimum, vous devez fournir au moteur d'expression régulière les deux éléments d'information suivants pour traiter un texte à l'aide d'expressions régulières :

* Le modèle d’expression régulière à identifier dans le texte. 
  
  Dans .NET, les modèles d’expression régulière sont définis par un langage ou une syntaxe spécifique, qui est compatible avec les expressions régulières Perl 5 et ajoute certaines fonctionnalités comme la mise en correspondance de la droite vers la gauche. Pour plus d’informations, consultez [Langage des expressions régulières - Aide-mémoire](quick-ref.md).
  
* Le texte à analyser pour le modèle d’expression régulière.

Les méthodes de la classe [Regex](xref:System.Text.RegularExpressions.Regex) vous permettent d’effectuer les opérations suivantes :

* Déterminer si le modèle d’expression régulière est présent dans le texte d’entrée en appelant la méthode [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)). Pour obtenir un exemple d’utilisation de la méthode [IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) pour valider un texte, consultez [Guide pratique : vérifier que des chaînes sont dans un format d’adresse e-mail valide](verify-format.md).

* Récupérer une occurrence, ou toutes les occurrences, de texte qui correspondent au modèle d’expression régulière en appelant la méthode [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) ou [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)). La première méthode retourne un objet [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) qui fournit des informations sur le texte correspondant. La seconde retourne un objet [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) qui contient un objet [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) pour chaque correspondance trouvée dans le texte analysé. 

* Remplacer le texte qui correspond au modèle d’expression régulière en appelant la méthode [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)). Pour obtenir des exemples d’utilisation de la méthode [Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) pour modifier des formats de date et supprimer des caractères non valides d’une chaîne, consultez [Guide pratique : supprimer des caractères non valides d’une chaîne](strip-characters.md) et [Exemple d’expression régulière : modification des formats de date](changing-formats.md).

Pour obtenir une vue d’ensemble du modèle objet d’expression régulière, consultez [Modèle objet d’expression régulière](object-model.md).

Pour plus d’informations sur le langage des expressions régulières, consultez [Langage des expressions régulières - Aide-mémoire](quick-ref.md).

## <a name="regular-expression-examples"></a>Exemples d'expressions régulières

La classe [String](xref:System.String) comprend de nombreuses méthodes de recherche et de remplacement de chaîne qui vous permettent de trouver des chaînes littérales dans une chaîne plus grande. Les expressions régulières sont particulièrement utiles quand vous souhaitez trouver une sous-chaîne spécifique dans une chaîne plus grande ou identifier des modèles dans une chaîne, comme le montrent les exemples suivants. 

### <a name="example-1-replacing-substrings"></a>Exemple 1 : remplacement de sous-chaînes

Supposons qu'une liste de diffusion contient des noms complets, constitués d'un prénom, d'un nom et, parfois, d'un titre (Mr, Mme ou Mlle). Si vous ne souhaitez pas inclure les titres quand vous générez les étiquettes des enveloppes à partir de la liste, vous pouvez utiliser une expression régulière pour supprimer les titres, comme le montre l'exemple suivant.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "(Mr\\.? |Mrs\\.? |Miss |Ms\\.? )";
      string[] names = { "Mr. Henry Hunt", "Ms. Sara Samuels", 
                         "Abraham Adams", "Ms. Nicole Norris" };
      foreach (string name in names)
         Console.WriteLine(Regex.Replace(name, pattern, String.Empty));
   }
}
// The example displays the following output:
//    Henry Hunt
//    Sara Samuels
//    Abraham Adams
//    Nicole Norris
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(Mr\.? |Mrs\.? |Miss |Ms\.? )"
      Dim names() As String = { "Mr. Henry Hunt", "Ms. Sara Samuels", _
                                "Abraham Adams", "Ms. Nicole Norris" }
      For Each name As String In names
         Console.WriteLine(Regex.Replace(name, pattern, String.Empty))
      Next                                
   End Sub
End Module
' The example displays the following output:
'    Henry Hunt
'    Sara Samuels
'    Abraham Adams
'    Nicole Norris
```

Le modèle d’expression régulière `(Mr\.? |Mrs\.? |Miss |Ms\.? )` trouve toute occurrence de « Mr  », « Mr.  », « Mrs  », « Mrs.  », « Miss  », « Ms  » ou « Ms.  ». L’appel de la méthode [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) remplace la chaîne mise en correspondance par [String.Empty](xref:System.String.Empty) ; en d’autres termes, il la supprime de la chaîne d’origine.

### <a name="example-2-identifying-duplicated-words"></a>Exemple 2 : identification des mots en double

La répétition d'un mot est une erreur de rédaction courante. Vous pouvez utiliser une expression régulière pour identifier les mots en double, comme le montre l'exemple suivant.

```csharp
using System;
using System.Text.RegularExpressions;

public class Class1
{
   public static void Main()
   {
      string pattern = @"\b(\w+?)\s\1\b";
      string input = "This this is a nice day. What about this? This tastes good. I saw a a dog.";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
         Console.WriteLine("{0} (duplicates '{1}') at position {2}", 
                           match.Value, match.Groups[1].Value, match.Index);
   }
}
// The example displays the following output:
//       This this (duplicates 'This)' at position 0
//       a a (duplicates 'a)' at position 66
```

```vb
Imports System.Text.RegularExpressions

Module modMain
   Public Sub Main()
      Dim pattern As String = "\b(\w+?)\s\1\b"
      Dim input As String = "This this is a nice day. What about this? This tastes good. I saw a a dog."
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
         Console.WriteLine("{0} (duplicates '{1}') at position {2}", _
                           match.Value, match.Groups(1).Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       This this (duplicates 'This)' at position 0
'       a a (duplicates 'a)' at position 66
```

Le modèle d'expression régulière `\b(\w+?)\s\1\b` peut être interprété comme suit :

Syntaxe | Signification
------ | -------
`\b` | Commencer à la limite d'un mot.
`(\w+?)` | Correspond à un ou plusieurs caractères alphabétiques, mais le moins de caractères possible. Ensemble, ils forment un groupe identifiable par `\1`.
`\s` | Mettre en correspondance un espace blanc.
`\1` | Mettre en correspondance la sous-chaîne égale au groupe nommé `\1`.
`\b` | Mettre en correspondance la limite d'un mot.

La méthode [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) est appelée avec les options d’expression régulière définies sur [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase). Ainsi, l'opération de mise en correspondance ne fait pas la distinction entre minuscules et majuscules, et l'exemple identifie la sous-chaîne « This this » comme étant une duplication.

Notez que la chaîne d'entrée comprend la sous-chaîne « this? This ». Toutefois, en raison du signe de ponctuation intermédiaire, cette sous-chaîne n'est pas identifiée comme étant une duplication.

### <a name="example-3-dynamically-building-a-culture-sensitive-regular-expression"></a>Exemple 3 : création dynamique d'une expression régulière dépendante de la culture

L’exemple suivant illustre la puissance des expressions régulières combinée à la souplesse offerte par les fonctionnalités de globalisation de .NET. Il utilise l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) pour déterminer le format de la devise dans la culture actuelle du système. Ensuite, à partir de cette information, il construit dynamiquement une expression régulière qui extrait du texte les valeurs en devise. Pour chaque correspondance, il extrait le sous-groupe qui contient uniquement la chaîne numérique, le convertit en une valeur [Decimal](xref:System.Decimal), puis calcule un total cumulé. 

```csharp
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      // Define text to be parsed.
      string input = "Office expenses on 2/13/2008:\n" + 
                     "Paper (500 sheets)                      $3.95\n" + 
                     "Pencils (box of 10)                     $1.00\n" + 
                     "Pens (box of 10)                        $4.49\n" + 
                     "Erasers                                 $2.19\n" + 
                     "Ink jet printer                        $69.95\n\n" + 
                     "Total Expenses                        $ 81.58\n"; 

      // Get current culture's NumberFormatInfo object.
      NumberFormatInfo nfi = CultureInfo.CurrentCulture.NumberFormat;
      // Assign needed property values to variables.
      string currencySymbol = nfi.CurrencySymbol;
      bool symbolPrecedesIfPositive = nfi.CurrencyPositivePattern % 2 == 0;
      string groupSeparator = nfi.CurrencyGroupSeparator;
      string decimalSeparator = nfi.CurrencyDecimalSeparator;

      // Form regular expression pattern.
      string pattern = Regex.Escape( symbolPrecedesIfPositive ? currencySymbol : "") + 
                       @"\s*[-+]?" + "([0-9]{0,3}(" + groupSeparator + "[0-9]{3})*(" + 
                       Regex.Escape(decimalSeparator) + "[0-9]+)?)" + 
                       (! symbolPrecedesIfPositive ? currencySymbol : ""); 
      Console.WriteLine( "The regular expression pattern is:");
      Console.WriteLine("   " + pattern);      

      // Get text that matches regular expression pattern.
      MatchCollection matches = Regex.Matches(input, pattern, 
                                              RegexOptions.IgnorePatternWhitespace);               
      Console.WriteLine("Found {0} matches.", matches.Count); 

      // Get numeric string, convert it to a value, and add it to List object.
      List<decimal> expenses = new List<Decimal>();

      foreach (Match match in matches)
         expenses.Add(Decimal.Parse(match.Groups[1].Value));      

      // Determine whether total is present and if present, whether it is correct.
      decimal total = 0;
      foreach (decimal value in expenses)
         total += value;

      if (total / 2 == expenses[expenses.Count - 1]) 
         Console.WriteLine("The expenses total {0:C2}.", expenses[expenses.Count - 1]);
      else
         Console.WriteLine("The expenses total {0:C2}.", total);
   }  
}
// The example displays the following output:
//       The regular expression pattern is:
//          \$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)
//       Found 6 matches.
//       The expenses total $81.58.
```

```vb
Imports System.Collections.Generic
Imports System.Globalization
Imports System.Text.RegularExpressions

Public Module Example
   Public Sub Main()
      ' Define text to be parsed.
      Dim input As String = "Office expenses on 2/13/2008:" + vbCrLf + _
                            "Paper (500 sheets)                      $3.95" + vbCrLf + _
                            "Pencils (box of 10)                     $1.00" + vbCrLf + _
                            "Pens (box of 10)                        $4.49" + vbCrLf + _
                            "Erasers                                 $2.19" + vbCrLf + _
                            "Ink jet printer                        $69.95" + vbCrLf + vbCrLf + _
                            "Total Expenses                        $ 81.58" + vbCrLf
      ' Get current culture's NumberFormatInfo object.
      Dim nfi As NumberFormatInfo = CultureInfo.CurrentCulture.NumberFormat
      ' Assign needed property values to variables.
      Dim currencySymbol As String = nfi.CurrencySymbol
      Dim symbolPrecedesIfPositive As Boolean = CBool(nfi.CurrencyPositivePattern Mod 2 = 0)
      Dim groupSeparator As String = nfi.CurrencyGroupSeparator
      Dim decimalSeparator As String = nfi.CurrencyDecimalSeparator

      ' Form regular expression pattern.
      Dim pattern As String = Regex.Escape(CStr(IIf(symbolPrecedesIfPositive, currencySymbol, ""))) + _
                              "\s*[-+]?" + "([0-9]{0,3}(" + groupSeparator + "[0-9]{3})*(" + _
                              Regex.Escape(decimalSeparator) + "[0-9]+)?)" + _
                              CStr(IIf(Not symbolPrecedesIfPositive, currencySymbol, "")) 
      Console.WriteLine("The regular expression pattern is: ")
      Console.WriteLine("   " + pattern)      

      ' Get text that matches regular expression pattern.
      Dim matches As MatchCollection = Regex.Matches(input, pattern, RegexOptions.IgnorePatternWhitespace)               
      Console.WriteLine("Found {0} matches. ", matches.Count)

      ' Get numeric string, convert it to a value, and add it to List object.
      Dim expenses As New List(Of Decimal)

      For Each match As Match In matches
         expenses.Add(Decimal.Parse(match.Groups.Item(1).Value))      
      Next

      ' Determine whether total is present and if present, whether it is correct.
      Dim total As Decimal
      For Each value As Decimal In expenses
         total += value
      Next

      If total / 2 = expenses(expenses.Count - 1) Then
         Console.WriteLine("The expenses total {0:C2}.", expenses(expenses.Count - 1))
      Else
         Console.WriteLine("The expenses total {0:C2}.", total)
      End If   
   End Sub
End Module
' The example displays the following output:
'       The regular expression pattern is:
'          \$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)
'       Found 6 matches.
'       The expenses total $81.58.
```

Sur un ordinateur dont la culture actuelle est anglais-États-Unis (en-US), l'exemple crée dynamiquement l'expression régulière `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`. Ce modèle d’expression régulière peut être interprété comme suit :

Syntaxe | Signification
------ | -------
`\$` | Rechercher une occurrence unique du symbole dollar ($) dans la chaîne d'entrée. La chaîne du modèle d'expression régulière comprend une barre oblique inverse pour indiquer que le symbole dollar doit être interprété littéralement et non comme une ancre d'expression régulière. (Le symbole $ seul indiquerait au moteur d'expression régulière de débuter la recherche de correspondance à la fin d'une chaîne.) Pour que le symbole de devise de la culture actuelle ne soit pas interprété à tort comme un symbole d’expression régulière, l’exemple appelle la méthode [Escape](xref:System.Text.RegularExpressions.Regex.Escape(System.String)) pour placer le caractère dans une séquence d’échappement.
`\s*` | Rechercher zéro occurrence, ou plus, d'un espace blanc.
`[-+]?` | Rechercher zéro ou une occurrence d'un signe positif ou d'un signe négatif.
`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)` | Les parenthèses externes de cette expression définissent celle-ci en tant que groupe de capture ou que sous-expression. Si une correspondance est trouvée, les informations sur cette partie de la chaîne correspondante peuvent être récupérées à partir du deuxième objet [Group](xref:System.Text.RegularExpressions.Group) dans l’objet [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) retourné par la propriété [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups). (Le premier élément de la collection représente la correspondance entière.)
`[0-9]{0,3}` | Rechercher entre zéro et trois occurrences des chiffres décimaux allant de 0 à 9.
`(,[0-9]{3})*` | Rechercher zéro occurrence, ou plus, d'un séparateur de groupes suivi de trois chiffres décimaux.
`\.` | Rechercher une occurrence unique du séparateur décimal.
`[0-9]+` | Rechercher un ou plusieurs chiffres décimaux.
`(\.[0-9]+)?` | Rechercher zéro ou une occurrence du séparateur décimal suivie d'au moins un chiffre décimal.

## <a name="related-topics"></a>Rubriques connexes

Titre | Description
----- | -----------
[Langage des expressions régulières - Aide-mémoire](quick-ref.md) | Fournit des informations sur le jeu de caractères, d'opérateurs et de constructions permettant de définir des expressions régulières.
[Modèle objet d’expression régulière](object-model.md) | Fournit des informations et des exemples de code illustrant l'utilisation des classes d'expression régulière.
[Comportement détaillé des expressions régulières](regex-behavior.md) | Fournit des informations sur les fonctionnalités et le comportement des expressions régulières .NET.
[Exemples d’expressions régulières](regex-examples.md) | Fournit des exemples de code illustrant des utilisations courantes des expressions régulières.


## <a name="reference"></a>Référence

[System.Text.RegularExpressions](xref:System.Text.RegularExpressions)

[System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex)


