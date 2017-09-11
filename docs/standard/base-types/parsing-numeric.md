---
title: "Analyse de chaînes numériques dans .NET"
description: "Analyse de chaînes numériques dans .NET"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e393430a-731a-49fa-83de-ff7ed52d5704
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 85cd57d33b03f7a2105ee3f770b2f8bcc0a57ee4
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="parsing-numeric-strings-in-net"></a><span data-ttu-id="eaf60-104">Analyse de chaînes numériques dans .NET</span><span class="sxs-lookup"><span data-stu-id="eaf60-104">Parsing numeric strings in .NET</span></span>

<span data-ttu-id="eaf60-105">Tous les types numériques disposent de deux méthodes d’analyse statiques, `Parse` et `TryParse`, que vous pouvez utiliser pour convertir la représentation sous forme de chaîne d’un nombre en type numérique.</span><span class="sxs-lookup"><span data-stu-id="eaf60-105">All numeric types have two static parsing methods, `Parse` and `TryParse`, that you can use to convert the string representation of a number into a numeric type.</span></span> <span data-ttu-id="eaf60-106">Ces méthodes vous permettent d’analyser les chaînes qui ont été générées à l’aide de chaînes de format documentées dans [Chaînes de format numériques standard](standard-numeric.md) et [Chaînes de format numériques personnalisées](custom-numeric.md).</span><span class="sxs-lookup"><span data-stu-id="eaf60-106">These methods enable you to parse strings that were produced by using the format strings documented in [Standard Numeric Format Strings](standard-numeric.md) and [Custom Numeric Format Strings](custom-numeric.md).</span></span> <span data-ttu-id="eaf60-107">Par défaut, les méthodes `Parse` et `TryParse` peuvent convertir correctement les chaînes qui contiennent uniquement des chiffres décimaux intégraux en valeurs entières.</span><span class="sxs-lookup"><span data-stu-id="eaf60-107">By default, the `Parse` and `TryParse` methods can successfully convert strings that contain integral decimal digits only to integer values.</span></span> <span data-ttu-id="eaf60-108">Ils peuvent convertir correctement les chaînes qui contiennent des chiffres décimaux intégraux et fractionnaires, des séparateurs de groupe et un séparateur décimal en valeurs à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="eaf60-108">They can successfully convert strings that contain integral and fractional decimal digits, group separators, and a decimal separator to floating-point values.</span></span> <span data-ttu-id="eaf60-109">La méthode `Parse` lève une exception si l’opération échoue, tandis que la méthode `TryParse` retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="eaf60-109">The `Parse` method throws an exception if the operation fails, whereas the `TryParse` method returns `false`.</span></span>

## <a name="parsing-and-format-providers"></a><span data-ttu-id="eaf60-110">Analyse et fournisseurs de format</span><span class="sxs-lookup"><span data-stu-id="eaf60-110">Parsing and format providers</span></span>

<span data-ttu-id="eaf60-111">En général, les représentations sous forme de chaîne de valeurs numériques varient selon la culture.</span><span class="sxs-lookup"><span data-stu-id="eaf60-111">Typically, the string representations of numeric values differ by culture.</span></span> <span data-ttu-id="eaf60-112">Les éléments des chaînes numériques, tels que les symboles monétaires, les séparateurs de groupes (ou de milliers) et les séparateurs décimaux, varient selon la culture.</span><span class="sxs-lookup"><span data-stu-id="eaf60-112">Elements of numeric strings such as currency symbols, group (or thousands) separators, and decimal separators all vary by culture.</span></span> <span data-ttu-id="eaf60-113">Les méthodes d’analyse utilisent implicitement ou explicitement un fournisseur de format qui identifie ces variantes spécifiques à la culture.</span><span class="sxs-lookup"><span data-stu-id="eaf60-113">Parsing methods either implicitly or explicitly use a format provider that recognizes these culture-specific variations.</span></span> <span data-ttu-id="eaf60-114">Si aucun fournisseur de format n’est spécifié dans un appel à la méthode `Parse` ou `TryParse`, le fournisseur de format associé à la culture du thread actuel (l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) retourné par la propriété [NumberFormatInfo.CurrentInfo](xref:System.Globalization.NumberFormatInfo.CurrentInfo)) est utilisé.</span><span class="sxs-lookup"><span data-stu-id="eaf60-114">If no format provider is specified in a call to the `Parse` or `TryParse` method, the format provider associated with the current thread culture (the [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object returned by the [NumberFormatInfo.CurrentInfo](xref:System.Globalization.NumberFormatInfo.CurrentInfo) property) is used.</span></span> 

<span data-ttu-id="eaf60-115">Un fournisseur de format est représenté par une implémentation [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo).</span><span class="sxs-lookup"><span data-stu-id="eaf60-115">A format provider is represented by an [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) implementation.</span></span> <span data-ttu-id="eaf60-116">Cette interface a un seul membre, la méthode [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)), dont l’unique paramètre est un objet [Type](xref:System.Type) qui représente le type à mettre en forme.</span><span class="sxs-lookup"><span data-stu-id="eaf60-116">This interface has a single member, the [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) method, whose single parameter is a [Type](xref:System.Type) object that represents the type to be formatted.</span></span> <span data-ttu-id="eaf60-117">Cette méthode retourne l’objet qui fournit des informations de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="eaf60-117">This method returns the object that provides formatting information.</span></span> <span data-ttu-id="eaf60-118">.NET prend en charge les deux implémentations [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) suivantes pour analyser les chaînes numériques :</span><span class="sxs-lookup"><span data-stu-id="eaf60-118">.NET supports the following two [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) implementations for parsing numeric strings:</span></span>

* <span data-ttu-id="eaf60-119">Un objet [CultureInfo](xref:System.Globalization.CultureInfo) dont la méthode [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) retourne un objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) qui fournit des informations de mise en forme propres à la culture.</span><span class="sxs-lookup"><span data-stu-id="eaf60-119">A [CultureInfo](xref:System.Globalization.CultureInfo) object whose [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) method returns a [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object that provides culture-specific formatting information.</span></span>

* <span data-ttu-id="eaf60-120">Un objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) dont la méthode [NumberFormatInfo.GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) se retourne elle-même.</span><span class="sxs-lookup"><span data-stu-id="eaf60-120">A [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object whose [NumberFormatInfo.GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) method returns itself.</span></span>

<span data-ttu-id="eaf60-121">L’exemple suivant essaie de convertir chaque chaîne d’un tableau en une valeur [Double](xref:System.Double).</span><span class="sxs-lookup"><span data-stu-id="eaf60-121">The following example tries to convert each string in an array to a [Double](xref:System.Double) value.</span></span> <span data-ttu-id="eaf60-122">Il commence par essayer d’analyser la chaîne à l’aide d’un fournisseur de format qui reflète les conventions de la culture anglophone (États-Unis).</span><span class="sxs-lookup"><span data-stu-id="eaf60-122">It first tries to parse the string by using a format provider that reflects the conventions of the English (United States) culture.</span></span> <span data-ttu-id="eaf60-123">Si cette opération lève une exception [FormatException](xref:System.FormatException), il tente d’analyser la chaîne à l’aide d’un fournisseur de format qui reflète les conventions de la culture française (France).</span><span class="sxs-lookup"><span data-stu-id="eaf60-123">If this operation throws a [FormatException](xref:System.FormatException), it tries to parse the string by using a format provider that reflects the conventions of the French (France) culture.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string[] values = { "1,304.16", "$1,456.78", "1,094", "152", 
                          "123,45 €", "1 304,16", "Ae9f" };
      double number;
      CultureInfo culture = null;

      foreach (string value in values) {
         try {
            culture = CultureInfo.CreateSpecificCulture("en-US");
            number = Double.Parse(value, culture);
            Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number);
         }   
         catch (FormatException) {
            Console.WriteLine("{0}: Unable to parse '{1}'.", 
                              culture.Name, value);
            culture = CultureInfo.CreateSpecificCulture("fr-FR");
            try {
               number = Double.Parse(value, culture);
               Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number);
            }
            catch (FormatException) {
               Console.WriteLine("{0}: Unable to parse '{1}'.", 
                                 culture.Name, value);
            }
         }
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//    en-US: 1,304.16 --> 1304.16
//    
//    en-US: Unable to parse '$1,456.78'.
//    fr-FR: Unable to parse '$1,456.78'.
//    
//    en-US: 1,094 --> 1094
//    
//    en-US: 152 --> 152
//    
//    en-US: Unable to parse '123,45 €'.
//    fr-FR: Unable to parse '123,45 €'.
//    
//    en-US: Unable to parse '1 304,16'.
//    fr-FR: 1 304,16 --> 1304.16
//    
//    en-US: Unable to parse 'Ae9f'.
//    fr-FR: Unable to parse 'Ae9f'.
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim values() As String = { "1,304.16", "$1,456.78", "1,094", "152", 
                                 "123,45 €", "1 304,16", "Ae9f" }
      Dim number As Double
      Dim culture As CultureInfo = Nothing

      For Each value As String In values
         Try
            culture = CultureInfo.CreateSpecificCulture("en-US")
            number = Double.Parse(value, culture)
            Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number)
         Catch e As FormatException
            Console.WriteLine("{0}: Unable to parse '{1}'.", 
                              culture.Name, value)
            culture = CultureInfo.CreateSpecificCulture("fr-FR")
            Try
               number = Double.Parse(value, culture)
               Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number)
            Catch ex As FormatException
               Console.WriteLine("{0}: Unable to parse '{1}'.", 
                                 culture.Name, value)
            End Try
         End Try
         Console.WriteLine()
      Next
   End Sub
End Module
' The example displays the following output:
'    en-US: 1,304.16 --> 1304.16
'    
'    en-US: Unable to parse '$1,456.78'.
'    fr-FR: Unable to parse '$1,456.78'.
'    
'    en-US: 1,094 --> 1094
'    
'    en-US: 152 --> 152
'    
'    en-US: Unable to parse '123,45 €'.
'    fr-FR: Unable to parse '123,45 €'.
'    
'    en-US: Unable to parse '1 304,16'.
'    fr-FR: 1 304,16 --> 1304.16
'    
'    en-US: Unable to parse 'Ae9f'.
'    fr-FR: Unable to parse 'Ae9f'.
```

## <a name="parsing-and-numberstyles-values"></a><span data-ttu-id="eaf60-124">Analyse et valeurs NumberStyles</span><span class="sxs-lookup"><span data-stu-id="eaf60-124">Parsing and NumberStyles values</span></span>

<span data-ttu-id="eaf60-125">Les éléments de style (tels que les espaces blancs, les séparateurs de groupe et le séparateur décimal) que l’opération d’analyse peut gérer sont définis par une valeur d’énumération [NumberStyles](xref:System.Globalization.NumberStyles).</span><span class="sxs-lookup"><span data-stu-id="eaf60-125">The style elements (such as white space, group separators, and decimal separator) that the parse operation can handle are defined by a [NumberStyles](xref:System.Globalization.NumberStyles) enumeration value.</span></span> <span data-ttu-id="eaf60-126">Par défaut, les chaînes qui représentent des valeurs entières sont analysées à l’aide de la valeur [NumberStyles.Integer](xref:System.Globalization.NumberStyles.Integer), qui autorise uniquement les chiffres numériques, les espaces blancs de début et de fin et un signe de début.</span><span class="sxs-lookup"><span data-stu-id="eaf60-126">By default, strings that represent integer values are parsed by using the [NumberStyles.Integer](xref:System.Globalization.NumberStyles.Integer) value, which permits only numeric digits, leading and trailing white space, and a leading sign.</span></span> <span data-ttu-id="eaf60-127">Les chaînes qui représentent des valeurs à virgule flottante sont analysées à l’aide d’une combinaison des valeurs [NumberStyles.Float](xref:System.Globalization.NumberStyles.Float) et [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands). Ce style composite autorise les chiffres décimaux avec un espace blanc de début et de fin, un signe de début, un séparateur décimal, un séparateur de groupes et un exposant.</span><span class="sxs-lookup"><span data-stu-id="eaf60-127">Strings that represent floating-point values are parsed using a combination of the [NumberStyles.Float](xref:System.Globalization.NumberStyles.Float) and [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) values; this composite style permits decimal digits along with leading and trailing white space, a leading sign, a decimal separator, a group separator, and an exponent.</span></span> <span data-ttu-id="eaf60-128">Quand vous appelez une surcharge de la méthode `Parse` ou `TryParse` qui inclut un paramètre de type [NumberStyles](xref:System.Globalization.NumberStyles) et que vous définissez un ou plusieurs indicateurs [NumberStyles](xref:System.Globalization.NumberStyles), vous pouvez contrôler les éléments de style pouvant être présents dans la chaîne pour que l’opération d’analyse aboutisse.</span><span class="sxs-lookup"><span data-stu-id="eaf60-128">By calling an overload of the `Parse` or `TryParse` method that includes a parameter of type [NumberStyles](xref:System.Globalization.NumberStyles) and setting one or more [NumberStyles](xref:System.Globalization.NumberStyles) flags, you can control the style elements that can be present in the string for the parse operation to succeed.</span></span> 

<span data-ttu-id="eaf60-129">Par exemple, une chaîne qui contient un séparateur de groupes ne peut pas être convertie en valeur [Int32](xref:System.Int32) à l’aide de la méthode [Int32.Parse(String)](xref:System.Int32.Parse(System.String)).</span><span class="sxs-lookup"><span data-stu-id="eaf60-129">For example, a string that contains a group separator cannot be converted to an [Int32](xref:System.Int32) value by using the [Int32.Parse(String)](xref:System.Int32.Parse(System.String)) method.</span></span> <span data-ttu-id="eaf60-130">Toutefois, la conversion réussit si vous utilisez l’indicateur [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands), comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="eaf60-130">However, the conversion succeeds if you use the [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) flag, as the following example illustrates.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string value = "1,304";
      int number;
      IFormatProvider provider = CultureInfo.CreateSpecificCulture("en-US");
      if (Int32.TryParse(value, out number))
         Console.WriteLine("{0} --> {1}", value, number);
      else
         Console.WriteLine("Unable to convert '{0}'", value);

      if (Int32.TryParse(value, NumberStyles.Integer | NumberStyles.AllowThousands, 
                        provider, out number))
         Console.WriteLine("{0} --> {1}", value, number);
      else
         Console.WriteLine("Unable to convert '{0}'", value);
   }
}
// The example displays the following output:
//       Unable to convert '1,304'
//       1,304 --> 1304
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim value As String = "1,304"
      Dim number As Integer
      Dim provider As IFormatProvider = CultureInfo.CreateSpecificCulture("en-US")
      If Int32.TryParse(value, number) Then
         Console.WriteLine("{0} --> {1}", value, number)
      Else
         Console.WriteLine("Unable to convert '{0}'", value)
      End If

      If Int32.TryParse(value, NumberStyles.Integer Or NumberStyles.AllowThousands, 
                        provider, number) Then
         Console.WriteLine("{0} --> {1}", value, number)
      Else
         Console.WriteLine("Unable to convert '{0}'", value)
      End If
   End Sub
End Module
' The example displays the following output:
'       Unable to convert '1,304'
'       1,304 --> 1304
```

> <span data-ttu-id="eaf60-131">**Avertissement**</span><span class="sxs-lookup"><span data-stu-id="eaf60-131">**Warning**</span></span>
>
> <span data-ttu-id="eaf60-132">L’opération d’analyse utilise toujours les conventions de mise en forme d’une culture particulière.</span><span class="sxs-lookup"><span data-stu-id="eaf60-132">The parse operation always uses the formatting conventions of a particular culture.</span></span> <span data-ttu-id="eaf60-133">Si vous ne spécifiez pas de culture en passant un objet [CultureInfo](xref:System.Globalization.CultureInfo) ou [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo), la culture associée au thread actuel est utilisée.</span><span class="sxs-lookup"><span data-stu-id="eaf60-133">If you do not specify a culture by passing a [CultureInfo](xref:System.Globalization.CultureInfo) or [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object, the culture associated with the current thread is used.</span></span>
 
<span data-ttu-id="eaf60-134">Le tableau suivant répertorie les membres de l’énumération [NumberStyles](xref:System.Globalization.NumberStyles) et décrit l’effet qu’ils ont sur l’opération d’analyse.</span><span class="sxs-lookup"><span data-stu-id="eaf60-134">The following table lists the members of the [NumberStyles](xref:System.Globalization.NumberStyles) enumeration and describes the effect that they have on the parsing operation.</span></span>

<span data-ttu-id="eaf60-135">Valeur NumberStyles</span><span class="sxs-lookup"><span data-stu-id="eaf60-135">NumberStyles value</span></span> | <span data-ttu-id="eaf60-136">Effet sur la chaîne à analyser</span><span class="sxs-lookup"><span data-stu-id="eaf60-136">Effect on the string to be parsed</span></span>
------------------ | --------------------------------- 
[<span data-ttu-id="eaf60-137">NumberStyles.None</span><span class="sxs-lookup"><span data-stu-id="eaf60-137">NumberStyles.None</span></span>](xref:System.Globalization.NumberStyles.None) | <span data-ttu-id="eaf60-138">Seuls les chiffres sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="eaf60-138">Only numeric digits are permitted.</span></span>
[<span data-ttu-id="eaf60-139">NumberStyles.AllowDecimalPoint</span><span class="sxs-lookup"><span data-stu-id="eaf60-139">NumberStyles.AllowDecimalPoint</span></span>](xref:System.Globalization.NumberStyles.AllowDecimalPoint) | <span data-ttu-id="eaf60-140">Le séparateur décimal et les chiffres fractionnaires sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="eaf60-140">The decimal separator and fractional digits are permitted.</span></span> <span data-ttu-id="eaf60-141">Pour les valeurs entières, le seul chiffre fractionnaire autorisé est zéro.</span><span class="sxs-lookup"><span data-stu-id="eaf60-141">For integer values, only zero is permitted as a fractional digit.</span></span> <span data-ttu-id="eaf60-142">Les séparateurs décimaux valides sont déterminés par la propriété [NumberFormatInfo.NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) ou [NumberFormatInfo.CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator).</span><span class="sxs-lookup"><span data-stu-id="eaf60-142">Valid decimal separators are determined by the [NumberFormatInfo.NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) or [NumberFormatInfo.CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) property.</span></span>
[<span data-ttu-id="eaf60-143">NumberStyles.AllowExponent</span><span class="sxs-lookup"><span data-stu-id="eaf60-143">NumberStyles.AllowExponent</span></span>](xref:System.Globalization.NumberStyles.AllowExponent) | <span data-ttu-id="eaf60-144">Les caractères « e » ou « E » peuvent être utilisés pour indiquer une notation exponentielle.</span><span class="sxs-lookup"><span data-stu-id="eaf60-144">The "e" or "E" character can be used to indicate exponential notation.</span></span>
[<span data-ttu-id="eaf60-145">NumberStyles.AllowLeadingWhite</span><span class="sxs-lookup"><span data-stu-id="eaf60-145">NumberStyles.AllowLeadingWhite</span></span>](xref:System.Globalization.NumberStyles.AllowLeadingWhite) | <span data-ttu-id="eaf60-146">L’espace blanc de début est autorisé.</span><span class="sxs-lookup"><span data-stu-id="eaf60-146">Leading white space is permitted.</span></span>
[<span data-ttu-id="eaf60-147">NumberStyles.AllowTrailingWhite</span><span class="sxs-lookup"><span data-stu-id="eaf60-147">NumberStyles.AllowTrailingWhite</span></span>](xref:System.Globalization.NumberStyles.AllowTrailingWhite) | <span data-ttu-id="eaf60-148">L’espace blanc de fin est autorisé.</span><span class="sxs-lookup"><span data-stu-id="eaf60-148">Trailing white space is permitted.</span></span>
[<span data-ttu-id="eaf60-149">NumberStyles.AllowLeadingSign</span><span class="sxs-lookup"><span data-stu-id="eaf60-149">NumberStyles.AllowLeadingSign</span></span>](xref:System.Globalization.NumberStyles.AllowLeadingSign) | <span data-ttu-id="eaf60-150">Un signe positif ou négatif peut précéder les chiffres.</span><span class="sxs-lookup"><span data-stu-id="eaf60-150">A positive or negative sign can precede numeric digits.</span></span>
[<span data-ttu-id="eaf60-151">NumberStyles.AllowTrailingSign</span><span class="sxs-lookup"><span data-stu-id="eaf60-151">NumberStyles.AllowTrailingSign</span></span>](xref:System.Globalization.NumberStyles.AllowTrailingSign) | <span data-ttu-id="eaf60-152">Un signe positif ou négatif peut suivre les chiffres.</span><span class="sxs-lookup"><span data-stu-id="eaf60-152">A positive or negative sign can follow numeric digits.</span></span>
[<span data-ttu-id="eaf60-153">NumberStyles.AllowParentheses</span><span class="sxs-lookup"><span data-stu-id="eaf60-153">NumberStyles.AllowParentheses</span></span>](xref:System.Globalization.NumberStyles.AllowParentheses) | <span data-ttu-id="eaf60-154">Les parenthèses peuvent être utilisées pour indiquer des valeurs négatives.</span><span class="sxs-lookup"><span data-stu-id="eaf60-154">Parentheses can be used to indicate negative values.</span></span>
[<span data-ttu-id="eaf60-155">NumberStyles.AllowThousands</span><span class="sxs-lookup"><span data-stu-id="eaf60-155">NumberStyles.AllowThousands</span></span>](xref:System.Globalization.NumberStyles.AllowThousands) | <span data-ttu-id="eaf60-156">Le séparateur de groupes est autorisé.</span><span class="sxs-lookup"><span data-stu-id="eaf60-156">The group separator is permitted.</span></span> <span data-ttu-id="eaf60-157">Le caractère de séparation de groupe est déterminé par la propriété [NumberFormatInfo.NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) ou [NumberFormatInfo.CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator).</span><span class="sxs-lookup"><span data-stu-id="eaf60-157">The group separator character is determined by the [NumberFormatInfo.NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) or [NumberFormatInfo.CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) property.</span></span>
[<span data-ttu-id="eaf60-158">NumberStyles.AllowCurrencySymbol</span><span class="sxs-lookup"><span data-stu-id="eaf60-158">NumberStyles.AllowCurrencySymbol</span></span>](xref:System.Globalization.NumberStyles.AllowCurrencySymbol) | <span data-ttu-id="eaf60-159">Le symbole monétaire est autorisé.</span><span class="sxs-lookup"><span data-stu-id="eaf60-159">The currency symbol is permitted.</span></span> <span data-ttu-id="eaf60-160">Le symbole monétaire est défini par la propriété [NumberFormatInfo.CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol).</span><span class="sxs-lookup"><span data-stu-id="eaf60-160">The currency symbol is defined by the [NumberFormatInfo.CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) property.</span></span>
[<span data-ttu-id="eaf60-161">NumberStyles.AllowHexSpecifier</span><span class="sxs-lookup"><span data-stu-id="eaf60-161">NumberStyles.AllowHexSpecifier</span></span>](xref:System.Globalization.NumberStyles.AllowHexSpecifier) | <span data-ttu-id="eaf60-162">La chaîne à analyser est interprétée comme un nombre hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="eaf60-162">The string to be parsed is interpreted as a hexadecimal number.</span></span> <span data-ttu-id="eaf60-163">Elle peut inclure les chiffres hexadécimaux 0-9, A-F et a-f.</span><span class="sxs-lookup"><span data-stu-id="eaf60-163">It can include the hexadecimal digits 0-9, A-F, and a-f.</span></span> <span data-ttu-id="eaf60-164">Cet indicateur peut être utilisé uniquement pour analyser des valeurs entières.</span><span class="sxs-lookup"><span data-stu-id="eaf60-164">This flag can be used only to parse integer values.</span></span>
 
<span data-ttu-id="eaf60-165">En outre, l’énumération [NumberStyles](xref:System.Globalization.NumberStyles) fournit les styles composites suivants, qui comprennent plusieurs indicateurs [NumberStyles](xref:System.Globalization.NumberStyles).</span><span class="sxs-lookup"><span data-stu-id="eaf60-165">In addition, the [NumberStyles](xref:System.Globalization.NumberStyles) enumeration provides the following composite styles, which include multiple [NumberStyles](xref:System.Globalization.NumberStyles) flags.</span></span> 

<span data-ttu-id="eaf60-166">Valeur NumberStyles composite</span><span class="sxs-lookup"><span data-stu-id="eaf60-166">Composite NumberStyles value</span></span> | <span data-ttu-id="eaf60-167">Membres</span><span class="sxs-lookup"><span data-stu-id="eaf60-167">Includes members</span></span>
---------------------------- | ---------------- 
[<span data-ttu-id="eaf60-168">NumberStyles.Integer</span><span class="sxs-lookup"><span data-stu-id="eaf60-168">NumberStyles.Integer</span></span>](xref:System.Globalization.NumberStyles.Integer) | <span data-ttu-id="eaf60-169">Comprend les styles [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite) et [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign).</span><span class="sxs-lookup"><span data-stu-id="eaf60-169">Includes the [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), and [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign) styles.</span></span> <span data-ttu-id="eaf60-170">Il s’agit du style par défaut utilisé pour analyser des valeurs entières.</span><span class="sxs-lookup"><span data-stu-id="eaf60-170">This is the default style used to parse integer values.</span></span>
[<span data-ttu-id="eaf60-171">NumberStyles.Number</span><span class="sxs-lookup"><span data-stu-id="eaf60-171">NumberStyles.Number</span></span>](xref:System.Globalization.NumberStyles.Number) | <span data-ttu-id="eaf60-172">Comprend les styles [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign), [NumberStyles.AllowTrailingSign](xref:System.Globalization.NumberStyles.AllowTrailingSign), [NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint) et [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands).</span><span class="sxs-lookup"><span data-stu-id="eaf60-172">Includes the [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign), [NumberStyles.AllowTrailingSign](xref:System.Globalization.NumberStyles.AllowTrailingSign), [NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint), and [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) styles.</span></span>
[<span data-ttu-id="eaf60-173">NumberStyles.Float</span><span class="sxs-lookup"><span data-stu-id="eaf60-173">NumberStyles.Float</span></span>](xref:System.Globalization.NumberStyles.Float) | <span data-ttu-id="eaf60-174">Comprend les styles [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign), [NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint) et [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent).</span><span class="sxs-lookup"><span data-stu-id="eaf60-174">Includes the [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign), [NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint), and [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) styles.</span></span>
[<span data-ttu-id="eaf60-175">NumberStyles.Currency</span><span class="sxs-lookup"><span data-stu-id="eaf60-175">NumberStyles.Currency</span></span>](xref:System.Globalization.NumberStyles.Currency) | <span data-ttu-id="eaf60-176">Comprend tous les styles, à l’exception de [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) et [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).</span><span class="sxs-lookup"><span data-stu-id="eaf60-176">Includes all styles except [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) and [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).</span></span>
[<span data-ttu-id="eaf60-177">NumberStyles.Any</span><span class="sxs-lookup"><span data-stu-id="eaf60-177">NumberStyles.Any</span></span>](xref:System.Globalization.NumberStyles.Any) | <span data-ttu-id="eaf60-178">Comprend tous les styles, à l’exception de [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).</span><span class="sxs-lookup"><span data-stu-id="eaf60-178">Includes all styles except [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).</span></span>
[<span data-ttu-id="eaf60-179">NumberStyles.HexNumber</span><span class="sxs-lookup"><span data-stu-id="eaf60-179">NumberStyles.HexNumber</span></span>](xref:System.Globalization.NumberStyles.HexNumber) | <span data-ttu-id="eaf60-180">Comprend les styles [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite) et [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).</span><span class="sxs-lookup"><span data-stu-id="eaf60-180">Includes the [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), and [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) styles.</span></span>
 
## <a name="parsing-and-unicode-digits"></a><span data-ttu-id="eaf60-181">Analyse et chiffres Unicode</span><span class="sxs-lookup"><span data-stu-id="eaf60-181">Parsing and Unicode digits</span></span>

<span data-ttu-id="eaf60-182">La norme Unicode définit des points de code pour les chiffres dans différents systèmes d’écriture.</span><span class="sxs-lookup"><span data-stu-id="eaf60-182">The Unicode standard defines code points for digits in various writing systems.</span></span> <span data-ttu-id="eaf60-183">Par exemple, les points de code U+0030 à U+0039 représentent les chiffres latins de base 0 à 9, les points de code de U+09E6 à U+09EF représentent les chiffres bengalis compris entre 0 et 9, et les points de code U+FF10 à U+FF19 représentent les chiffres pleine chasse compris entre 0 et 9.</span><span class="sxs-lookup"><span data-stu-id="eaf60-183">For example, code points from U+0030 to U+0039 represent the basic Latin digits 0 through 9, code points from U+09E6 to U+09EF represent the Bangla digits 0 through 9, and code points from U+FF10 to U+FF19 represent the Fullwidth digits 0 through 9.</span></span> <span data-ttu-id="eaf60-184">Toutefois, les seuls chiffres identifiés par les méthodes d’analyse sont les chiffres latins de base 0 à 9 avec des points de code compris entre U+0030 et U+0039.</span><span class="sxs-lookup"><span data-stu-id="eaf60-184">However, the only numeric digits recognized by parsing methods are the basic Latin digits 0-9 with code points from U+0030 to U+0039.</span></span> <span data-ttu-id="eaf60-185">Si une chaîne contenant tout autre chiffre est passée à une méthode d’analyse numérique, celle-ci lève une exception [FormatException](xref:System.FormatException).</span><span class="sxs-lookup"><span data-stu-id="eaf60-185">If a numeric parsing method is passed a string that contains any other digits, the method throws a [FormatException](xref:System.FormatException).</span></span>

<span data-ttu-id="eaf60-186">L’exemple suivant utilise la méthode [Int32.Parse](xref:System.Int32.Parse(System.String)) pour analyser des chaînes composées de chiffres dans différents systèmes d’écriture.</span><span class="sxs-lookup"><span data-stu-id="eaf60-186">The following example uses the [Int32.Parse](xref:System.Int32.Parse(System.String)) method to parse strings that consist of digits in different writing systems.</span></span> <span data-ttu-id="eaf60-187">Comme l’indique le résultat de l’exemple, la tentative d’analyse des chiffres latins de base réussit, mais la tentative d’analyse des chiffres pleine chasse, arabe-hindi et bengali échoue.</span><span class="sxs-lookup"><span data-stu-id="eaf60-187">As the output from the example shows, the attempt to parse the basic Latin digits succeeds, but the attempt to parse the Fullwidth, Arabic-Indic, and Bangla digits fails.</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string value;
      // Define a string of basic Latin digits 1-5.
      value = "\u0031\u0032\u0033\u0034\u0035";
      ParseDigits(value);

      // Define a string of Fullwidth digits 1-5.
      value = "\uFF11\uFF12\uFF13\uFF14\uFF15";
      ParseDigits(value);

      // Define a string of Arabic-Indic digits 1-5.
      value = "\u0661\u0662\u0663\u0664\u0665";
      ParseDigits(value);

      // Define a string of Bangla digits 1-5.
      value = "\u09e7\u09e8\u09e9\u09ea\u09eb";
      ParseDigits(value);
   }

   static void ParseDigits(string value)
   {
      try {
         int number = Int32.Parse(value);
         Console.WriteLine("'{0}' --> {1}", value, number);
      }   
      catch (FormatException) {
         Console.WriteLine("Unable to parse '{0}'.", value);      
      }     
   }
}
// The example displays the following output:
//       '12345' --> 12345
//       Unable to parse '１２３４５'.
//       Unable to parse '١٢٣٤٥'.
//       Unable to parse '১২৩৪৫'.
```

```vb
Module Example
   Public Sub Main()
      Dim value As String
      ' Define a string of basic Latin digits 1-5.
      value = ChrW(&h31) + ChrW(&h32) + ChrW(&h33) + ChrW(&h34) + ChrW(&h35)
      ParseDigits(value)

      ' Define a string of Fullwidth digits 1-5.
      value = ChrW(&hff11) + ChrW(&hff12) + ChrW(&hff13) + ChrW(&hff14) + ChrW(&hff15)
      ParseDigits(value)

      ' Define a string of Arabic-Indic digits 1-5.
      value = ChrW(&h661) + ChrW(&h662) + ChrW(&h663) + ChrW(&h664) + ChrW(&h665)
      ParseDigits(value)

      ' Define a string of Bangla digits 1-5.
      value = ChrW(&h09e7) + ChrW(&h09e8) + ChrW(&h09e9) + ChrW(&h09ea) + ChrW(&h09eb)
      ParseDigits(value)
   End Sub

   Sub ParseDigits(value As String)
      Try
         Dim number As Integer = Int32.Parse(value)
         Console.WriteLine("'{0}' --> {1}", value, number)
      Catch e As FormatException
         Console.WriteLine("Unable to parse '{0}'.", value)      
      End Try     
   End Sub
End Module
' The example displays the following output:
'       '12345' --> 12345
'       Unable to parse '１２３４５'.
'       Unable to parse '١٢٣٤٥'.
'       Unable to parse '১২৩৪৫'.
```

## <a name="see-also"></a><span data-ttu-id="eaf60-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eaf60-188">See also</span></span>

[<span data-ttu-id="eaf60-189">System.Globalization.NumberStyles</span><span class="sxs-lookup"><span data-stu-id="eaf60-189">System.Globalization.NumberStyles</span></span>](xref:System.Globalization.NumberStyles)

[<span data-ttu-id="eaf60-190">Analyse de chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="eaf60-190">Parsing strings in .NET</span></span>](parsing-strings.md)

[<span data-ttu-id="eaf60-191">Mise en forme des types dans .NET</span><span class="sxs-lookup"><span data-stu-id="eaf60-191">Formatting types in .NET</span></span>](formatting-types.md)


