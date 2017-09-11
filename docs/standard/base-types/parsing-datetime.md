---
title: "Analyse des chaînes de date et d’heure dans .NET"
description: "Analyse des chaînes de date et d’heure dans .NET"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e61514cd-5329-4eb8-b122-482fffb54ab7
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: f0131baa0874880b6697458426da5ae9ce1705b7
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="parsing-date-and-time-strings-in-net"></a><span data-ttu-id="05f42-104">Analyse des chaînes de date et d’heure dans .NET</span><span class="sxs-lookup"><span data-stu-id="05f42-104">Parsing date and time strings in .NET</span></span>

<span data-ttu-id="05f42-105">Les méthodes d’analyse convertissent la représentation sous forme de chaîne d’une date et heure en un objet [DateTime](xref:System.DateTime) équivalent.</span><span class="sxs-lookup"><span data-stu-id="05f42-105">Parsing methods convert the string representation of a date and time to an equivalent [DateTime](xref:System.DateTime) object.</span></span> <span data-ttu-id="05f42-106">Les méthodes [Parse](xref:System.DateTime.Parse(System.String)) et [TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) convertissent l’une des nombreuses représentations communes de date et heure.</span><span class="sxs-lookup"><span data-stu-id="05f42-106">The [Parse](xref:System.DateTime.Parse(System.String)) and [TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) methods convert any of several common representations of a date and time.</span></span> <span data-ttu-id="05f42-107">Les méthodes[ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) et [TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@)) convertissent une représentation sous forme de chaîne conforme au modèle spécifié par une chaîne de format de date et d’heure.</span><span class="sxs-lookup"><span data-stu-id="05f42-107">The [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) and [TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@)) methods convert a string representation that conforms to the pattern specified by a date and time format string.</span></span> <span data-ttu-id="05f42-108">(Consultez les rubriques sur les [chaînes de format de date et d’heure standard](standard-datetime.md) et les [chaînes de format de date et d’heure personnalisées](custom-datetime.md).)</span><span class="sxs-lookup"><span data-stu-id="05f42-108">(See the topics on [standard date and time format strings](standard-datetime.md) and [custom date and time format strings](custom-datetime.md).)</span></span> 

<span data-ttu-id="05f42-109">L’analyse est influencée par les propriétés d’un fournisseur de format qui donne des informations telles que les chaînes utilisées pour les séparateurs de date et d’heure, et les noms de mois, jours et ères.</span><span class="sxs-lookup"><span data-stu-id="05f42-109">Parsing is influenced by the properties of a format provider that supplies information such as the strings used for date and time separators, and the names of months, days, and eras.</span></span> <span data-ttu-id="05f42-110">Le fournisseur de format est l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) actuel, qui est fourni implicitement par la culture du thread actuel ou explicitement par le paramètre [IFormatProvider](xref:System.IFormatProvider) d’une méthode d’analyse.</span><span class="sxs-lookup"><span data-stu-id="05f42-110">The format provider is the current [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object, which is provided implicitly by the current thread culture or explicitly by the [IFormatProvider](xref:System.IFormatProvider) parameter of a parsing method.</span></span> <span data-ttu-id="05f42-111">Pour le paramètre [IFormatProvider](xref:System.IFormatProvider), spécifiez un objet [CultureInfo](xref:System.Globalization.CultureInfo) qui représente une culture, ou un objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo).</span><span class="sxs-lookup"><span data-stu-id="05f42-111">For the [IFormatProvider](xref:System.IFormatProvider) parameter, specify a [CultureInfo](xref:System.Globalization.CultureInfo) object, which represents a culture, or a [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object.</span></span> 

<span data-ttu-id="05f42-112">La représentation sous forme de chaîne d’une date à analyser doit inclure le mois et au moins un jour ou une année.</span><span class="sxs-lookup"><span data-stu-id="05f42-112">The string representation of a date to be parsed must include the month and at least a day or year.</span></span> <span data-ttu-id="05f42-113">La représentation d’une heure sous forme de chaîne doit inclure l’heure et au moins les minutes ou l’indicateur AM/PM.</span><span class="sxs-lookup"><span data-stu-id="05f42-113">The string representation of a time must include the hour and at least minutes or the AM/PM designator.</span></span> <span data-ttu-id="05f42-114">Toutefois, si possible, l’analyse fournit des valeurs par défaut pour les composants omis.</span><span class="sxs-lookup"><span data-stu-id="05f42-114">However, parsing supplies default values for omitted components if possible.</span></span> <span data-ttu-id="05f42-115">Une date manquante a comme valeur par défaut la date du jour, une année manquante a comme valeur par défaut l’année en cours, un jour manquant du mois a comme valeur par défaut le premier jour du mois, et une heure manquante a comme valeur par défaut minuit.</span><span class="sxs-lookup"><span data-stu-id="05f42-115">A missing date defaults to the current date, a missing year defaults to the current year, a missing day of the month defaults to the first day of the month, and a missing time defaults to midnight.</span></span> 

<span data-ttu-id="05f42-116">Si la représentation sous forme de chaîne spécifie uniquement une heure, l’analyse retourne un objet [DateTime](xref:System.DateTime) dont les propriétés [Year](xref:System.DateTime.Year), [Month](xref:System.DateTime.Month) et [Day](xref:System.DateTime.Day) sont définies sur les valeurs correspondantes de la propriété [Today](xref:System.DateTime.Today).</span><span class="sxs-lookup"><span data-stu-id="05f42-116">If the string representation specifies only a time, parsing returns a [DateTime](xref:System.DateTime) object with its [Year](xref:System.DateTime.Year), [Month](xref:System.DateTime.Month), and [Day](xref:System.DateTime.Day) properties set to the corresponding values of the [Today](xref:System.DateTime.Today) property.</span></span> <span data-ttu-id="05f42-117">Toutefois, si la constante [DateTimeStyles.NoCurrentDateDefault](xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault) est spécifiée dans la méthode d’analyse, les propriétés d’année, mois et jour résultantes ont la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="05f42-117">However, if the [DateTimeStyles.NoCurrentDateDefault](xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault) constant is specified in the parsing method, the resulting year, month, and day properties are set to the value 1.</span></span>

<span data-ttu-id="05f42-118">Outre le composant de date et d’heure, la représentation sous forme de chaîne d’une date et d’une heure peut inclure un offset qui indique le décalage horaire par rapport au temps universel coordonné (UTC, Coordinated Universal Time).</span><span class="sxs-lookup"><span data-stu-id="05f42-118">In addition to a date and a time component, the string representation of a date and time can include an offset that indicates how much the time differs from Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="05f42-119">Par exemple, la chaîne « 2/14/2007 5:32:00 -7:00 » définit une heure qui est sept heures plus tôt que l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="05f42-119">For example, the string "2/14/2007 5:32:00 -7:00" defines a time that is seven hours earlier than UTC.</span></span> <span data-ttu-id="05f42-120">Si la représentation d’une heure sous forme de chaîne n’inclut pas d’offset, l’analyse retourne un objet [DateTime](xref:System.DateTime) dont la propriété [Kind](xref:System.DateTime.Kind) a la valeur [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified).</span><span class="sxs-lookup"><span data-stu-id="05f42-120">If an offset is omitted from the string representation of a time, parsing returns a [DateTime](xref:System.DateTime) object with its [Kind](xref:System.DateTime.Kind) property set to [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified).</span></span> <span data-ttu-id="05f42-121">Si un offset est spécifié, l’analyse retourne un objet [DateTime](xref:System.DateTime) dont la propriété [Kind](xref:System.DateTime.Kind) a la valeur [Local](xref:System.DateTimeKind.Local) et dont la valeur est ajustée en fonction du fuseau horaire local de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="05f42-121">If an offset is specified, parsing returns a [DateTime](xref:System.DateTime) object with its [Kind](xref:System.DateTime.Kind) property set to [Local](xref:System.DateTimeKind.Local) and its value adjusted to the local time zone of your machine.</span></span> <span data-ttu-id="05f42-122">Vous pouvez modifier ce comportement en utilisant une constante [DateTimeStyles](xref:System.Globalization.DateTimeStyles) avec la méthode d’analyse.</span><span class="sxs-lookup"><span data-stu-id="05f42-122">You can modify this behavior by using a [DateTimeStyles](xref:System.Globalization.DateTimeStyles) constant with the parsing method.</span></span>

<span data-ttu-id="05f42-123">Le fournisseur de format est également utilisé pour interpréter une date numérique ambiguë.</span><span class="sxs-lookup"><span data-stu-id="05f42-123">The format provider is also used to interpret an ambiguous numeric date.</span></span> <span data-ttu-id="05f42-124">Par exemple, il n’est pas évident de savoir quels composants de la date représentée par la chaîne « 02/03/04 » correspondent au mois, au jour et à l’année.</span><span class="sxs-lookup"><span data-stu-id="05f42-124">For example, it is not clear which components of the date represented by the string "02/03/04" are the month, day, and year.</span></span> <span data-ttu-id="05f42-125">Dans ce cas, les composants sont interprétés d’après l’ordre des formats de date similaires dans le fournisseur de format.</span><span class="sxs-lookup"><span data-stu-id="05f42-125">In this case, the components are interpreted according to the order of similar date formats in the format provider.</span></span> 

## <a name="parse"></a><span data-ttu-id="05f42-126">Parse</span><span class="sxs-lookup"><span data-stu-id="05f42-126">Parse</span></span>

<span data-ttu-id="05f42-127">L’exemple de code suivant illustre l’utilisation de la méthode `Parse` pour convertir une chaîne en `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="05f42-127">The following code example illustrates the use of the `Parse` method to convert a string into a `DateTime`.</span></span> <span data-ttu-id="05f42-128">Cet exemple fait appel à la culture associée au thread actuel pour effectuer l’analyse.</span><span class="sxs-lookup"><span data-stu-id="05f42-128">This example uses the culture associated with the current thread to perform the parse.</span></span> <span data-ttu-id="05f42-129">Si l’objet [CultureInfo](xref:System.Globalization.CultureInfo) associé à la culture actuelle ne peut pas analyser la chaîne d’entrée, une exception [FormatException](xref:System.FormatException) est levée.</span><span class="sxs-lookup"><span data-stu-id="05f42-129">If the [CultureInfo](xref:System.Globalization.CultureInfo) associated with the current culture cannot parse the input string, a [FormatException](xref:System.FormatException) is thrown.</span></span>

```csharp
string MyString = "Jan 1, 2009";
DateTime MyDateTime = DateTime.Parse(MyString);
Console.WriteLine(MyDateTime);
// Displays the following output on a system whose culture is en-US:
//       1/1/2009 12:00:00 AM
```

```vb
Dim MyString As String = "Jan 1, 2009"
Dim MyDateTime As DateTime = DateTime.Parse(MyString)
Console.WriteLine(MyDateTime)
' Displays the following output on a system whose culture is en-US:
'       1/1/2009 12:00:00 AM
```

<span data-ttu-id="05f42-130">Vous pouvez également spécifier un objet `CultureInfo` qui prend la valeur d’une des cultures qu’il a définies ou spécifier l’un des objets [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) standard retournés par la propriété [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat).</span><span class="sxs-lookup"><span data-stu-id="05f42-130">You can also specify a `CultureInfo` set to one of the cultures defined by that object, or you can specify one of the standard [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) objects returned by the [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) property.</span></span> <span data-ttu-id="05f42-131">L’exemple de code suivant utilise un fournisseur de format pour analyser une chaîne en allemand dans `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="05f42-131">The following code example uses a format provider to parse a German string into a `DateTime`.</span></span> <span data-ttu-id="05f42-132">Un `CultureInfo` représentant la culture de-DE est défini et passé avec la chaîne analysée pour que l’analyse de cette chaîne particulière aboutisse.</span><span class="sxs-lookup"><span data-stu-id="05f42-132">A `CultureInfo` representing the de-DE culture is defined and passed with the string being parsed to ensure successful parsing of this particular string.</span></span> <span data-ttu-id="05f42-133">Ceci exclut tous les paramètres contenus dans `CurrentCulture` de `CurrentThread`.</span><span class="sxs-lookup"><span data-stu-id="05f42-133">This precludes whatever setting is in the `CurrentCulture` of the `CurrentThread`.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      CultureInfo MyCultureInfo = new CultureInfo("de-DE");
      string MyString = "12 Juni 2008";
      DateTime MyDateTime = DateTime.Parse(MyString, MyCultureInfo);
      Console.WriteLine(MyDateTime);
   }
}
// The example displays the following output:
//       6/12/2008 12:00:00 AM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim MyCultureInfo As CultureInfo = new CultureInfo("de-DE")
      Dim MyString As String = "12 Juni 2008"
      Dim MyDateTime As DateTime = DateTime.Parse(MyString, MyCultureInfo)
      Console.WriteLine(MyDateTime)
   End Sub
End Module
' The example displays the following output:
'       6/12/2008 12:00:00 AM
```

<span data-ttu-id="05f42-134">Toutefois, bien que vous puissiez utiliser les surcharges de la méthode [Parse](xref:System.DateTime.Parse(System.String)) pour spécifier des fournisseurs de format personnalisé, la méthode ne prend pas en charge l’utilisation de fournisseurs de format non standard.</span><span class="sxs-lookup"><span data-stu-id="05f42-134">However, although you can use overloads of the [Parse](xref:System.DateTime.Parse(System.String)) method to specify custom format providers, the method does not support the use of non-standard format providers.</span></span> <span data-ttu-id="05f42-135">Pour analyser une date et une heure exprimées dans un format non standard, faites plutôt appel à la méthode [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)).</span><span class="sxs-lookup"><span data-stu-id="05f42-135">To parse a date and time expressed in a non-standard format, use the [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) method instead.</span></span>

<span data-ttu-id="05f42-136">L’exemple de code suivant utilise l’énumération [DateTimeStyles](xref:System.Globalization.DateTimeStyles) pour indiquer que les informations de date et d’heure actuelles ne doivent pas être ajoutées à `DateTime` pour les champs que la chaîne ne définit pas.</span><span class="sxs-lookup"><span data-stu-id="05f42-136">The following code example uses the [DateTimeStyles](xref:System.Globalization.DateTimeStyles) enumeration to specify that the current date and time information should not be added to the `DateTime` for fields that the string does not define.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      CultureInfo MyCultureInfo = new CultureInfo("de-DE");
      string MyString = "12 Juni 2008";
      DateTime MyDateTime = DateTime.Parse(MyString, MyCultureInfo, 
                                           DateTimeStyles.NoCurrentDateDefault);
      Console.WriteLine(MyDateTime);
   }
}
// The example displays the following output if the current culture is en-US:
//      6/12/2008 12:00:00 AM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim MyCultureInfo As CultureInfo = new CultureInfo("de-DE")
      Dim MyString As String = "12 Juni 2008"
      Dim MyDateTime As DateTime = DateTime.Parse(MyString, MyCultureInfo)
      Console.WriteLine(MyDateTime)
   End Sub
End Module
' The example displays the following output:
'       6/12/2008 12:00:00 AM
```

## <a name="parseexact"></a><span data-ttu-id="05f42-137">ParseExact</span><span class="sxs-lookup"><span data-stu-id="05f42-137">ParseExact</span></span>

<span data-ttu-id="05f42-138">La méthode [DateTime.ParseExact]((xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) convertit une chaîne conforme à un modèle de chaîne spécifié en objet `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="05f42-138">The [DateTime.ParseExact]((xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) method converts a string that conforms to a specified string pattern to a `DateTime` object.</span></span> <span data-ttu-id="05f42-139">Quand une chaîne dans un format autre que celui spécifié est passée à cette méthode, une [FormatException](xref:System.FormatException) est levée.</span><span class="sxs-lookup"><span data-stu-id="05f42-139">When a string that is not of the form specified is passed to this method, a [FormatException](xref:System.FormatException) is thrown.</span></span> <span data-ttu-id="05f42-140">Vous pouvez spécifier un des spécificateurs de format standard de date et d’heure ou une combinaison limitée de spécificateurs de format personnalisé de date et d’heure.</span><span class="sxs-lookup"><span data-stu-id="05f42-140">You can specify one of the standard date and time format specifiers or a limited combination of the custom date and time format specifiers.</span></span> <span data-ttu-id="05f42-141">En utilisant les spécificateurs de format personnalisé, vous pouvez construire une chaîne de reconnaissance personnalisée.</span><span class="sxs-lookup"><span data-stu-id="05f42-141">Using the custom format specifiers, it is possible for you to construct a custom recognition string.</span></span> <span data-ttu-id="05f42-142">Pour obtenir une explication des spécificateurs, consultez les rubriques relatives aux [chaînes de format de date et d’heure standard](standard-datetime.md) et aux [chaînes de format de date et d’heure personnalisées](custom-datetime.md).</span><span class="sxs-lookup"><span data-stu-id="05f42-142">For an explanation of the specifiers, see the topics on [standard date and time format strings](standard-datetime.md) and [custom date and time format strings](custom-datetime.md).</span></span> 

<span data-ttu-id="05f42-143">Chaque surcharge de la méthode [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) a également un paramètre [IFormatProvider](xref:System.IFormatProvider) qui fournit généralement des informations spécifiques à la culture sur la mise en forme de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="05f42-143">Each overload of the [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) method also has an [IFormatProvider](xref:System.IFormatProvider) parameter that typically provides culture-specific information about the formatting of the string.</span></span> <span data-ttu-id="05f42-144">En général, cet objet [IFormatProvider](xref:System.IFormatProvider) est un objet [CultureInfo](xref:System.Globalization.CultureInfo) qui représente une culture standard ou un objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui est retourné par la propriété [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat).</span><span class="sxs-lookup"><span data-stu-id="05f42-144">Typically, this [IFormatProvider](xref:System.IFormatProvider) object is a [CultureInfo](xref:System.Globalization.CultureInfo) object that represents a standard culture or a [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object that is returned by the [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) property.</span></span> <span data-ttu-id="05f42-145">Toutefois, contrairement aux autres fonctions d’analyse de date et d’heure, cette méthode prend également en charge [IFormatProvider](xref:System.IFormatProvider) qui définit un format de date et d’heure non standard.</span><span class="sxs-lookup"><span data-stu-id="05f42-145">However, unlike the other date and time parsing functions, this method also supports an [IFormatProvider](xref:System.IFormatProvider) that defines a non-standard date and time format.</span></span> 

<span data-ttu-id="05f42-146">Dans l’exemple de code suivant, la méthode `ParseExact` reçoit un objet chaîne à analyser, puis un spécificateur de format, puis un objet `CultureInfo`.</span><span class="sxs-lookup"><span data-stu-id="05f42-146">In the following code example, the `ParseExact` method is passed a string object to parse, followed by a format specifier, followed by a `CultureInfo` object.</span></span> <span data-ttu-id="05f42-147">Cette méthode `ParseExact` peut uniquement analyser des chaînes qui exhibent le format de date longue dans la culture en-US.</span><span class="sxs-lookup"><span data-stu-id="05f42-147">This `ParseExact` method can only parse strings that exhibit the long date pattern in the en-US culture.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      CultureInfo MyCultureInfo = new CultureInfo("en-US");
      string[] MyString = {" Friday, April 10, 2009", "Friday, April 10, 2009"};
      foreach (string dateString in MyString)
      {
         try {
            DateTime MyDateTime = DateTime.ParseExact(dateString, "D", MyCultureInfo);
            Console.WriteLine(MyDateTime);
         }
         catch (FormatException) {
            Console.WriteLine("Unable to parse '{0}'", dateString);
         }
      }
   }
}
// The example displays the following output:
//       Unable to parse ' Friday, April 10, 2009'
//       4/10/2009 12:00:00 AM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim MyCultureInfo As CultureInfo = new CultureInfo("en-US")
      Dim MyString() As String = {" Friday, April 10, 2009", "Friday, April 10, 2009"}
      For Each dateString As String In MyString
         Try
            Dim MyDateTime As DateTime = DateTime.ParseExact(dateString, "D", _
                                                             MyCultureInfo)
            Console.WriteLine(MyDateTime)
         Catch e As FormatException
            Console.WriteLine("Unable to parse '{0}'", dateString)
         End Try
      Next
   End Sub
End Module
' The example displays the following output:
'       Unable to parse ' Friday, April 10, 2009'
'       4/10/2009 12:00:00 AM
```

## <a name="see-also"></a><span data-ttu-id="05f42-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05f42-148">See Also</span></span>

[<span data-ttu-id="05f42-149">Analyse de chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="05f42-149">Parsing strings in .NET</span></span>](parsing-strings.md)

[<span data-ttu-id="05f42-150">Mise en forme des types dans .NET</span><span class="sxs-lookup"><span data-stu-id="05f42-150">Formatting types in .NET</span></span>](formatting-types.md)

[<span data-ttu-id="05f42-151">Conversion de type dans .NET</span><span class="sxs-lookup"><span data-stu-id="05f42-151">Type conversion in .NET</span></span>](type-conversion.md)


