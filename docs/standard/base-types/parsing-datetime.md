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
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 8b0c5a64db50163d196017ebb410e454eb5a6af9

---

# <a name="parsing-date-and-time-strings-in-net"></a>Analyse des chaînes de date et d’heure dans .NET

Les méthodes d’analyse convertissent la représentation sous forme de chaîne d’une date et heure en un objet [DateTime](xref:System.DateTime) équivalent. Les méthodes [Parse](xref:System.DateTime.Parse(System.String)) et [TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) convertissent l’une des nombreuses représentations communes de date et heure. Les méthodes[ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) et [TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@)) convertissent une représentation sous forme de chaîne conforme au modèle spécifié par une chaîne de format de date et d’heure. (Consultez les rubriques sur les [chaînes de format de date et d’heure standard](standard-datetime.md) et les [chaînes de format de date et d’heure personnalisées](custom-datetime.md).) 

L’analyse est influencée par les propriétés d’un fournisseur de format qui donne des informations telles que les chaînes utilisées pour les séparateurs de date et d’heure, et les noms de mois, jours et ères. Le fournisseur de format est l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) actuel, qui est fourni implicitement par la culture du thread actuel ou explicitement par le paramètre [IFormatProvider](xref:System.IFormatProvider) d’une méthode d’analyse. Pour le paramètre [IFormatProvider](xref:System.IFormatProvider), spécifiez un objet [CultureInfo](xref:System.Globalization.CultureInfo) qui représente une culture, ou un objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo). 

La représentation sous forme de chaîne d’une date à analyser doit inclure le mois et au moins un jour ou une année. La représentation d’une heure sous forme de chaîne doit inclure l’heure et au moins les minutes ou l’indicateur AM/PM. Toutefois, si possible, l’analyse fournit des valeurs par défaut pour les composants omis. Une date manquante a comme valeur par défaut la date du jour, une année manquante a comme valeur par défaut l’année en cours, un jour manquant du mois a comme valeur par défaut le premier jour du mois, et une heure manquante a comme valeur par défaut minuit. 

Si la représentation sous forme de chaîne spécifie uniquement une heure, l’analyse retourne un objet [DateTime](xref:System.DateTime) dont les propriétés [Year](xref:System.DateTime.Year), [Month](xref:System.DateTime.Month) et [Day](xref:System.DateTime.Day) sont définies sur les valeurs correspondantes de la propriété [Today](xref:System.DateTime.Today). Toutefois, si la constante [DateTimeStyles.NoCurrentDateDefault](xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault) est spécifiée dans la méthode d’analyse, les propriétés d’année, mois et jour résultantes ont la valeur 1.

Outre le composant de date et d’heure, la représentation sous forme de chaîne d’une date et d’une heure peut inclure un offset qui indique le décalage horaire par rapport au temps universel coordonné (UTC, Coordinated Universal Time). Par exemple, la chaîne « 2/14/2007 5:32:00 -7:00 » définit une heure qui est sept heures plus tôt que l’heure UTC. Si la représentation d’une heure sous forme de chaîne n’inclut pas d’offset, l’analyse retourne un objet [DateTime](xref:System.DateTime) dont la propriété [Kind](xref:System.DateTime.Kind) a la valeur [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified). Si un offset est spécifié, l’analyse retourne un objet [DateTime](xref:System.DateTime) dont la propriété [Kind](xref:System.DateTime.Kind) a la valeur [Local](xref:System.DateTimeKind.Local) et dont la valeur est ajustée en fonction du fuseau horaire local de votre ordinateur. Vous pouvez modifier ce comportement en utilisant une constante [DateTimeStyles](xref:System.Globalization.DateTimeStyles) avec la méthode d’analyse.

Le fournisseur de format est également utilisé pour interpréter une date numérique ambiguë. Par exemple, il n’est pas évident de savoir quels composants de la date représentée par la chaîne « 02/03/04 » correspondent au mois, au jour et à l’année. Dans ce cas, les composants sont interprétés d’après l’ordre des formats de date similaires dans le fournisseur de format. 

## <a name="parse"></a>Parse

L’exemple de code suivant illustre l’utilisation de la méthode `Parse` pour convertir une chaîne en `DateTime`. Cet exemple fait appel à la culture associée au thread actuel pour effectuer l’analyse. Si l’objet [CultureInfo](xref:System.Globalization.CultureInfo) associé à la culture actuelle ne peut pas analyser la chaîne d’entrée, une exception [FormatException](xref:System.FormatException) est levée.

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

Vous pouvez également spécifier un objet `CultureInfo` qui prend la valeur d’une des cultures qu’il a définies ou spécifier l’un des objets [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) standard retournés par la propriété [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat). L’exemple de code suivant utilise un fournisseur de format pour analyser une chaîne en allemand dans `DateTime`. Un `CultureInfo` représentant la culture de-DE est défini et passé avec la chaîne analysée pour que l’analyse de cette chaîne particulière aboutisse. Ceci exclut tous les paramètres contenus dans `CurrentCulture` de `CurrentThread`.

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

Toutefois, bien que vous puissiez utiliser les surcharges de la méthode [Parse](xref:System.DateTime.Parse(System.String)) pour spécifier des fournisseurs de format personnalisé, la méthode ne prend pas en charge l’utilisation de fournisseurs de format non standard. Pour analyser une date et une heure exprimées dans un format non standard, faites plutôt appel à la méthode [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)).

L’exemple de code suivant utilise l’énumération [DateTimeStyles](xref:System.Globalization.DateTimeStyles) pour indiquer que les informations de date et d’heure actuelles ne doivent pas être ajoutées à `DateTime` pour les champs que la chaîne ne définit pas.

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

## <a name="parseexact"></a>ParseExact

La méthode [DateTime.ParseExact]((xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) convertit une chaîne conforme à un modèle de chaîne spécifié en objet `DateTime`. Quand une chaîne dans un format autre que celui spécifié est passée à cette méthode, une [FormatException](xref:System.FormatException) est levée. Vous pouvez spécifier un des spécificateurs de format standard de date et d’heure ou une combinaison limitée de spécificateurs de format personnalisé de date et d’heure. En utilisant les spécificateurs de format personnalisé, vous pouvez construire une chaîne de reconnaissance personnalisée. Pour obtenir une explication des spécificateurs, consultez les rubriques relatives aux [chaînes de format de date et d’heure standard](standard-datetime.md) et aux [chaînes de format de date et d’heure personnalisées](custom-datetime.md). 

Chaque surcharge de la méthode [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) a également un paramètre [IFormatProvider](xref:System.IFormatProvider) qui fournit généralement des informations spécifiques à la culture sur la mise en forme de la chaîne. En général, cet objet [IFormatProvider](xref:System.IFormatProvider) est un objet [CultureInfo](xref:System.Globalization.CultureInfo) qui représente une culture standard ou un objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui est retourné par la propriété [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat). Toutefois, contrairement aux autres fonctions d’analyse de date et d’heure, cette méthode prend également en charge [IFormatProvider](xref:System.IFormatProvider) qui définit un format de date et d’heure non standard. 

Dans l’exemple de code suivant, la méthode `ParseExact` reçoit un objet chaîne à analyser, puis un spécificateur de format, puis un objet `CultureInfo`. Cette méthode `ParseExact` peut uniquement analyser des chaînes qui exhibent le format de date longue dans la culture en-US.

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

## <a name="see-also"></a>Voir aussi

[Analyse de chaînes dans .NET](parsing-strings.md)

[Mise en forme des types dans .NET](formatting-types.md)

[Conversion de type dans .NET](type-conversion.md)




<!--HONumber=Nov16_HO3-->


