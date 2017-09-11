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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: ac26821819b22aa3ea47e6945bb5c8575dcd9807
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="regular-expressions-in-net"></a><span data-ttu-id="9c755-104">Expressions régulières dans .NET</span><span class="sxs-lookup"><span data-stu-id="9c755-104">Regular expressions in .NET</span></span>

<span data-ttu-id="9c755-105">Les expressions régulières permettent de traiter un texte de façon puissante, souple et efficace.</span><span class="sxs-lookup"><span data-stu-id="9c755-105">Regular expressions provide a powerful, flexible, and efficient method for processing text.</span></span> <span data-ttu-id="9c755-106">Grâce à la syntaxe complète des expressions régulières pour la recherche de correspondance avec un modèle, vous pouvez rapidement analyser des volumes importants de texte pour rechercher des modèles de caractères spécifiques, valider le texte pour vous assurer qu'il correspond à un modèle prédéfini (tel qu'une adresse e-mail), extraire, modifier, remplacer ou supprimer des sous-chaînes de texte et ajouter les chaînes extraites à une collection afin de générer un rapport.</span><span class="sxs-lookup"><span data-stu-id="9c755-106">The extensive pattern-matching notation of regular expressions enables you to quickly parse large amounts of text to find specific character patterns; to validate text to ensure that it matches a predefined pattern (such as an e-mail address); to extract, edit, replace, or delete text substrings; and to add the extracted strings to a collection in order to generate a report.</span></span> <span data-ttu-id="9c755-107">Pour de nombreuses applications qui traitent des chaînes ou qui analysent de grands blocs de texte, les expressions régulières constituent un outil indispensable.</span><span class="sxs-lookup"><span data-stu-id="9c755-107">For many applications that deal with strings or that parse large blocks of text, regular expressions are an indispensable tool.</span></span>

## <a name="how-regular-expressions-work"></a><span data-ttu-id="9c755-108">Fonctionnement des expressions régulières</span><span class="sxs-lookup"><span data-stu-id="9c755-108">How Regular Expressions Work</span></span>

<span data-ttu-id="9c755-109">La pièce maîtresse du traitement d’un texte avec des expressions régulières est le moteur d’expression régulière, représenté par l’objet [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) dans .NET.</span><span class="sxs-lookup"><span data-stu-id="9c755-109">The centerpiece of text processing with regular expressions is the regular expression engine, which is represented by the [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) object in .NET.</span></span> <span data-ttu-id="9c755-110">Au minimum, vous devez fournir au moteur d'expression régulière les deux éléments d'information suivants pour traiter un texte à l'aide d'expressions régulières :</span><span class="sxs-lookup"><span data-stu-id="9c755-110">At a minimum, processing text using regular expressions requires that the regular expression engine be provided with the following two items of information:</span></span>

* <span data-ttu-id="9c755-111">Le modèle d’expression régulière à identifier dans le texte.</span><span class="sxs-lookup"><span data-stu-id="9c755-111">The regular expression pattern to identify in the text.</span></span> 
  
  <span data-ttu-id="9c755-112">Dans .NET, les modèles d’expression régulière sont définis par un langage ou une syntaxe spécifique, qui est compatible avec les expressions régulières Perl 5 et ajoute certaines fonctionnalités comme la mise en correspondance de la droite vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="9c755-112">In .NET, regular expression patterns are defined by a special syntax or language, which is compatible with Perl 5 regular expressions and adds some additional features such as right-to-left matching.</span></span> <span data-ttu-id="9c755-113">Pour plus d’informations, consultez [Langage des expressions régulières - Aide-mémoire](quick-ref.md).</span><span class="sxs-lookup"><span data-stu-id="9c755-113">For more information, see [Regular Expression Language - Quick Reference](quick-ref.md).</span></span>
  
* <span data-ttu-id="9c755-114">Le texte à analyser pour le modèle d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="9c755-114">The text to parse for the regular expression pattern.</span></span>

<span data-ttu-id="9c755-115">Les méthodes de la classe [Regex](xref:System.Text.RegularExpressions.Regex) vous permettent d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9c755-115">The methods of the [Regex](xref:System.Text.RegularExpressions.Regex) class let you perform the following operations:</span></span>

* <span data-ttu-id="9c755-116">Déterminer si le modèle d’expression régulière est présent dans le texte d’entrée en appelant la méthode [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)).</span><span class="sxs-lookup"><span data-stu-id="9c755-116">Determine whether the regular expression pattern occurs in the input text by calling the [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) method.</span></span> <span data-ttu-id="9c755-117">Pour obtenir un exemple d’utilisation de la méthode [IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) pour valider un texte, consultez [Guide pratique : vérifier que des chaînes sont dans un format d’adresse e-mail valide](verify-format.md).</span><span class="sxs-lookup"><span data-stu-id="9c755-117">For an example that uses the [IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) method for validating text, see [How to: Verify that Strings Are in Valid Email Format](verify-format.md).</span></span>

* <span data-ttu-id="9c755-118">Récupérer une occurrence, ou toutes les occurrences, de texte qui correspondent au modèle d’expression régulière en appelant la méthode [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) ou [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)).</span><span class="sxs-lookup"><span data-stu-id="9c755-118">Retrieve one or all occurrences of text that matches the regular expression pattern by calling the [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) or [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) method.</span></span> <span data-ttu-id="9c755-119">La première méthode retourne un objet [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) qui fournit des informations sur le texte correspondant.</span><span class="sxs-lookup"><span data-stu-id="9c755-119">The former method returns a [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) object that provides information about the matching text.</span></span> <span data-ttu-id="9c755-120">La seconde retourne un objet [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) qui contient un objet [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) pour chaque correspondance trouvée dans le texte analysé.</span><span class="sxs-lookup"><span data-stu-id="9c755-120">The latter returns a [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) object that contains one [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) object for each match found in the parsed text.</span></span> 

* <span data-ttu-id="9c755-121">Remplacer le texte qui correspond au modèle d’expression régulière en appelant la méthode [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)).</span><span class="sxs-lookup"><span data-stu-id="9c755-121">Replace text that matches the regular expression pattern by calling the [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) method.</span></span> <span data-ttu-id="9c755-122">Pour obtenir des exemples d’utilisation de la méthode [Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) pour modifier des formats de date et supprimer des caractères non valides d’une chaîne, consultez [Guide pratique : supprimer des caractères non valides d’une chaîne](strip-characters.md) et [Exemple d’expression régulière : modification des formats de date](changing-formats.md).</span><span class="sxs-lookup"><span data-stu-id="9c755-122">For examples that use the [Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) method to change date formats and remove invalid characters from a string, see [How to: Strip Invalid Characters from a String](strip-characters.md) and [Regular Expression Example: Changing Date Formats](changing-formats.md).</span></span>

<span data-ttu-id="9c755-123">Pour obtenir une vue d’ensemble du modèle objet d’expression régulière, consultez [Modèle objet d’expression régulière](object-model.md).</span><span class="sxs-lookup"><span data-stu-id="9c755-123">For an overview of the regular expression object model, see [The Regular Expression Object Model](object-model.md).</span></span>

<span data-ttu-id="9c755-124">Pour plus d’informations sur le langage des expressions régulières, consultez [Langage des expressions régulières - Aide-mémoire](quick-ref.md).</span><span class="sxs-lookup"><span data-stu-id="9c755-124">For more information about the regular expression language, see [Regular Expression Language - Quick Reference](quick-ref.md).</span></span>

## <a name="regular-expression-examples"></a><span data-ttu-id="9c755-125">Exemples d'expressions régulières</span><span class="sxs-lookup"><span data-stu-id="9c755-125">Regular Expression Examples</span></span>

<span data-ttu-id="9c755-126">La classe [String](xref:System.String) comprend de nombreuses méthodes de recherche et de remplacement de chaîne qui vous permettent de trouver des chaînes littérales dans une chaîne plus grande.</span><span class="sxs-lookup"><span data-stu-id="9c755-126">The [String](xref:System.String) class includes a number of string search and replacement methods that you can use when you want to locate literal strings in a larger string.</span></span> <span data-ttu-id="9c755-127">Les expressions régulières sont particulièrement utiles quand vous souhaitez trouver une sous-chaîne spécifique dans une chaîne plus grande ou identifier des modèles dans une chaîne, comme le montrent les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="9c755-127">Regular expressions are most useful either when you want to locate one of several substrings in a larger string, or when you want to identify patterns in a string, as the following examples illustrate.</span></span> 

### <a name="example-1-replacing-substrings"></a><span data-ttu-id="9c755-128">Exemple 1 : remplacement de sous-chaînes</span><span class="sxs-lookup"><span data-stu-id="9c755-128">Example 1: Replacing Substrings</span></span>

<span data-ttu-id="9c755-129">Supposons qu'une liste de diffusion contient des noms complets, constitués d'un prénom, d'un nom et, parfois, d'un titre (Mr, Mme ou Mlle).</span><span class="sxs-lookup"><span data-stu-id="9c755-129">Assume that a mailing list contains names that sometimes include a title (Mr., Mrs., Miss, or Ms.) along with a first and last name.</span></span> <span data-ttu-id="9c755-130">Si vous ne souhaitez pas inclure les titres quand vous générez les étiquettes des enveloppes à partir de la liste, vous pouvez utiliser une expression régulière pour supprimer les titres, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9c755-130">If you do not want to include the titles when you generate envelope labels from the list, you can use a regular expression to remove the titles, as the following example illustrates.</span></span>

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

<span data-ttu-id="9c755-131">Le modèle d’expression régulière `(Mr\.? |Mrs\.? |Miss |Ms\.? )` trouve toute occurrence de « Mr  », « Mr.  », « Mrs  », « Mrs.  », « Miss  », « Ms  » ou « Ms.  ».</span><span class="sxs-lookup"><span data-stu-id="9c755-131">The regular expression pattern `(Mr\.? |Mrs\.? |Miss |Ms\.? )` matches any occurrence of "Mr ", "Mr. ", "Mrs ", "Mrs. ", "Miss ", "Ms or "Ms. ".</span></span> <span data-ttu-id="9c755-132">L’appel de la méthode [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) remplace la chaîne mise en correspondance par [String.Empty](xref:System.String.Empty) ; en d’autres termes, il la supprime de la chaîne d’origine.</span><span class="sxs-lookup"><span data-stu-id="9c755-132">The call to the [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) method replaces the matched string with [String.Empty](xref:System.String.Empty); in other words, it removes it from the original string.</span></span>

### <a name="example-2-identifying-duplicated-words"></a><span data-ttu-id="9c755-133">Exemple 2 : identification des mots en double</span><span class="sxs-lookup"><span data-stu-id="9c755-133">Example 2: Identifying Duplicated Words</span></span>

<span data-ttu-id="9c755-134">La répétition d'un mot est une erreur de rédaction courante.</span><span class="sxs-lookup"><span data-stu-id="9c755-134">Accidentally duplicating words is a common error that writers make.</span></span> <span data-ttu-id="9c755-135">Vous pouvez utiliser une expression régulière pour identifier les mots en double, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9c755-135">A regular expression can be used to identify duplicated words, as the following example shows.</span></span>

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

<span data-ttu-id="9c755-136">Le modèle d'expression régulière `\b(\w+?)\s\1\b` peut être interprété comme suit :</span><span class="sxs-lookup"><span data-stu-id="9c755-136">The regular expression pattern `\b(\w+?)\s\1\b` can be interpreted as follows:</span></span>

<span data-ttu-id="9c755-137">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c755-137">Syntax</span></span> | <span data-ttu-id="9c755-138">Signification</span><span class="sxs-lookup"><span data-stu-id="9c755-138">Meaning</span></span>
------ | -------
`\b` | <span data-ttu-id="9c755-139">Commencer à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="9c755-139">Start at a word boundary.</span></span>
`(\w+?)` | <span data-ttu-id="9c755-140">Correspond à un ou plusieurs caractères alphabétiques, mais le moins de caractères possible.</span><span class="sxs-lookup"><span data-stu-id="9c755-140">Match one or more word characters, but as few characters as possible.</span></span> <span data-ttu-id="9c755-141">Ensemble, ils forment un groupe identifiable par `\1`.</span><span class="sxs-lookup"><span data-stu-id="9c755-141">Together, they form a group that can be referred to as `\1`.</span></span>
`\s` | <span data-ttu-id="9c755-142">Mettre en correspondance un espace blanc.</span><span class="sxs-lookup"><span data-stu-id="9c755-142">Match a white-space character.</span></span>
`\1` | <span data-ttu-id="9c755-143">Mettre en correspondance la sous-chaîne égale au groupe nommé `\1`.</span><span class="sxs-lookup"><span data-stu-id="9c755-143">Match the substring that is equal to the group named `\1`.</span></span>
`\b` | <span data-ttu-id="9c755-144">Mettre en correspondance la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="9c755-144">Match a word boundary.</span></span>

<span data-ttu-id="9c755-145">La méthode [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) est appelée avec les options d’expression régulière définies sur [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase).</span><span class="sxs-lookup"><span data-stu-id="9c755-145">The [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) method is called with regular expression options set to [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase).</span></span> <span data-ttu-id="9c755-146">Ainsi, l'opération de mise en correspondance ne fait pas la distinction entre minuscules et majuscules, et l'exemple identifie la sous-chaîne « This this » comme étant une duplication.</span><span class="sxs-lookup"><span data-stu-id="9c755-146">Therefore, the match operation is case-insensitive, and the example identifies the substring "This this" as a duplication.</span></span>

<span data-ttu-id="9c755-147">Notez que la chaîne d'entrée comprend la sous-chaîne « this?</span><span class="sxs-lookup"><span data-stu-id="9c755-147">Note that the input string includes the substring "this?</span></span> <span data-ttu-id="9c755-148">This ».</span><span class="sxs-lookup"><span data-stu-id="9c755-148">This".</span></span> <span data-ttu-id="9c755-149">Toutefois, en raison du signe de ponctuation intermédiaire, cette sous-chaîne n'est pas identifiée comme étant une duplication.</span><span class="sxs-lookup"><span data-stu-id="9c755-149">However, because of the intervening punctuation mark, it is not identified as a duplication.</span></span>

### <a name="example-3-dynamically-building-a-culture-sensitive-regular-expression"></a><span data-ttu-id="9c755-150">Exemple 3 : création dynamique d'une expression régulière dépendante de la culture</span><span class="sxs-lookup"><span data-stu-id="9c755-150">Example 3: Dynamically Building a Culture-Sensitive Regular Expression</span></span>

<span data-ttu-id="9c755-151">L’exemple suivant illustre la puissance des expressions régulières combinée à la souplesse offerte par les fonctionnalités de globalisation de .NET.</span><span class="sxs-lookup"><span data-stu-id="9c755-151">The following example illustrates the power of regular expressions combined with the flexibility offered by .NET's globalization features.</span></span> <span data-ttu-id="9c755-152">Il utilise l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) pour déterminer le format de la devise dans la culture actuelle du système.</span><span class="sxs-lookup"><span data-stu-id="9c755-152">It uses the [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object to determine the format of currency values in the system's current culture.</span></span> <span data-ttu-id="9c755-153">Ensuite, à partir de cette information, il construit dynamiquement une expression régulière qui extrait du texte les valeurs en devise.</span><span class="sxs-lookup"><span data-stu-id="9c755-153">It then uses that information to dynamically construct a regular expression that extracts currency values from the text.</span></span> <span data-ttu-id="9c755-154">Pour chaque correspondance, il extrait le sous-groupe qui contient uniquement la chaîne numérique, le convertit en une valeur [Decimal](xref:System.Decimal), puis calcule un total cumulé.</span><span class="sxs-lookup"><span data-stu-id="9c755-154">For each match, it extracts the subgroup that contains the numeric string only, converts it to a [Decimal](xref:System.Decimal) value, and calculates a running total.</span></span> 

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

<span data-ttu-id="9c755-155">Sur un ordinateur dont la culture actuelle est anglais-États-Unis (en-US), l'exemple crée dynamiquement l'expression régulière `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`.</span><span class="sxs-lookup"><span data-stu-id="9c755-155">On a computer whose current culture is English - United States (en-US), the example dynamically builds the regular expression `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`.</span></span> <span data-ttu-id="9c755-156">Ce modèle d’expression régulière peut être interprété comme suit :</span><span class="sxs-lookup"><span data-stu-id="9c755-156">This regular expression pattern can be interpreted as follows:</span></span>

<span data-ttu-id="9c755-157">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c755-157">Syntax</span></span> | <span data-ttu-id="9c755-158">Signification</span><span class="sxs-lookup"><span data-stu-id="9c755-158">Meaning</span></span>
------ | -------
`\$` | <span data-ttu-id="9c755-159">Rechercher une occurrence unique du symbole dollar ($) dans la chaîne d'entrée.</span><span class="sxs-lookup"><span data-stu-id="9c755-159">Look for a single occurrence of the dollar symbol ($) in the input string.</span></span> <span data-ttu-id="9c755-160">La chaîne du modèle d'expression régulière comprend une barre oblique inverse pour indiquer que le symbole dollar doit être interprété littéralement et non comme une ancre d'expression régulière.</span><span class="sxs-lookup"><span data-stu-id="9c755-160">The regular expression pattern string includes a backslash to indicate that the dollar symbol is to be interpreted literally rather than as a regular expression anchor.</span></span> <span data-ttu-id="9c755-161">(Le symbole $ seul indiquerait au moteur d'expression régulière de débuter la recherche de correspondance à la fin d'une chaîne.) Pour que le symbole de devise de la culture actuelle ne soit pas interprété à tort comme un symbole d’expression régulière, l’exemple appelle la méthode [Escape](xref:System.Text.RegularExpressions.Regex.Escape(System.String)) pour placer le caractère dans une séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="9c755-161">(The $ symbol alone would indicate that the regular expression engine should try to begin its match at the end of a string.) To ensure that the current culture's currency symbol is not misinterpreted as a regular expression symbol, the example calls the [Escape](xref:System.Text.RegularExpressions.Regex.Escape(System.String)) method to escape the character.</span></span>
`\s*` | <span data-ttu-id="9c755-162">Rechercher zéro occurrence, ou plus, d'un espace blanc.</span><span class="sxs-lookup"><span data-stu-id="9c755-162">Look for zero or more occurrences of a white-space character.</span></span>
`[-+]?` | <span data-ttu-id="9c755-163">Rechercher zéro ou une occurrence d'un signe positif ou d'un signe négatif.</span><span class="sxs-lookup"><span data-stu-id="9c755-163">Look for zero or one occurrence of either a positive sign or a negative sign.</span></span>
`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)` | <span data-ttu-id="9c755-164">Les parenthèses externes de cette expression définissent celle-ci en tant que groupe de capture ou que sous-expression.</span><span class="sxs-lookup"><span data-stu-id="9c755-164">The outer parentheses around this expression define it as a capturing group or a subexpression.</span></span> <span data-ttu-id="9c755-165">Si une correspondance est trouvée, les informations sur cette partie de la chaîne correspondante peuvent être récupérées à partir du deuxième objet [Group](xref:System.Text.RegularExpressions.Group) dans l’objet [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) retourné par la propriété [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups).</span><span class="sxs-lookup"><span data-stu-id="9c755-165">If a match is found, information about this part of the matching string can be retrieved from the second [Group](xref:System.Text.RegularExpressions.Group) object in the [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) object returned by the [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) property.</span></span> <span data-ttu-id="9c755-166">(Le premier élément de la collection représente la correspondance entière.)</span><span class="sxs-lookup"><span data-stu-id="9c755-166">(The first element in the collection represents the entire match.)</span></span>
`[0-9]{0,3}` | <span data-ttu-id="9c755-167">Rechercher entre zéro et trois occurrences des chiffres décimaux allant de 0 à 9.</span><span class="sxs-lookup"><span data-stu-id="9c755-167">Look for zero to three occurrences of the decimal digits 0 through 9.</span></span>
`(,[0-9]{3})*` | <span data-ttu-id="9c755-168">Rechercher zéro occurrence, ou plus, d'un séparateur de groupes suivi de trois chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="9c755-168">Look for zero or more occurrences of a group separator followed by three decimal digits.</span></span>
`\.` | <span data-ttu-id="9c755-169">Rechercher une occurrence unique du séparateur décimal.</span><span class="sxs-lookup"><span data-stu-id="9c755-169">Look for a single occurrence of the decimal separator.</span></span>
`[0-9]+` | <span data-ttu-id="9c755-170">Rechercher un ou plusieurs chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="9c755-170">Look for one or more decimal digits.</span></span>
`(\.[0-9]+)?` | <span data-ttu-id="9c755-171">Rechercher zéro ou une occurrence du séparateur décimal suivie d'au moins un chiffre décimal.</span><span class="sxs-lookup"><span data-stu-id="9c755-171">Look for zero or one occurrence of the decimal separator followed by at least one decimal digit.</span></span>

## <a name="related-topics"></a><span data-ttu-id="9c755-172">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="9c755-172">Related Topics</span></span>

<span data-ttu-id="9c755-173">Titre</span><span class="sxs-lookup"><span data-stu-id="9c755-173">Title</span></span> | <span data-ttu-id="9c755-174">Description</span><span class="sxs-lookup"><span data-stu-id="9c755-174">Description</span></span>
----- | -----------
[<span data-ttu-id="9c755-175">Langage des expressions régulières - Aide-mémoire</span><span class="sxs-lookup"><span data-stu-id="9c755-175">Regular expression language - quick reference</span></span>](quick-ref.md) | <span data-ttu-id="9c755-176">Fournit des informations sur le jeu de caractères, d'opérateurs et de constructions permettant de définir des expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="9c755-176">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>
[<span data-ttu-id="9c755-177">Modèle objet d’expression régulière</span><span class="sxs-lookup"><span data-stu-id="9c755-177">The regular expression object model</span></span>](object-model.md) | <span data-ttu-id="9c755-178">Fournit des informations et des exemples de code illustrant l'utilisation des classes d'expression régulière.</span><span class="sxs-lookup"><span data-stu-id="9c755-178">Provides information and code examples that illustrate how to use the regular expression classes.</span></span>
[<span data-ttu-id="9c755-179">Comportement détaillé des expressions régulières</span><span class="sxs-lookup"><span data-stu-id="9c755-179">Details of regular expression behavior</span></span>](regex-behavior.md) | <span data-ttu-id="9c755-180">Fournit des informations sur les fonctionnalités et le comportement des expressions régulières .NET.</span><span class="sxs-lookup"><span data-stu-id="9c755-180">Provides information about the capabilities and behavior of .NETregular expressions.</span></span>
[<span data-ttu-id="9c755-181">Exemples d’expressions régulières</span><span class="sxs-lookup"><span data-stu-id="9c755-181">Regular expression examples</span></span>](regex-examples.md) | <span data-ttu-id="9c755-182">Fournit des exemples de code illustrant des utilisations courantes des expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="9c755-182">Provides code examples that illustrate typical uses of regular expressions.</span></span>


## <a name="reference"></a><span data-ttu-id="9c755-183">Référence</span><span class="sxs-lookup"><span data-stu-id="9c755-183">Reference</span></span>

[<span data-ttu-id="9c755-184">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="9c755-184">System.Text.RegularExpressions</span></span>](xref:System.Text.RegularExpressions)

[<span data-ttu-id="9c755-185">System.Text.RegularExpressions.Regex</span><span class="sxs-lookup"><span data-stu-id="9c755-185">System.Text.RegularExpressions.Regex</span></span>](xref:System.Text.RegularExpressions.Regex)


