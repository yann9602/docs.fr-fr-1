---
title: "Chaînes de format de date et d’heure personnalisées"
description: "Chaînes de format de date et d’heure personnalisées"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 45f286f5-92c9-4150-957c-fa6d394bc29b
translationtype: Human Translation
ms.sourcegitcommit: 28625def4199a660fe0ea04ab75f4f65d2e0c9c4
ms.openlocfilehash: 285e4bfd6a53d576ce4538b09a2561065c93e399
ms.lasthandoff: 02/23/2017

---

# <a name="custom-date-and-time-format-strings"></a>Chaînes de format de date et d’heure personnalisées

Une chaîne de format de date et d’heure définit la représentation textuelle d’une valeur [DateTime](xref:System.DateTime) ou [DateTimeOffset](xref:System.DateTimeOffset) qui résulte d’une opération de mise en forme. Elle peut également définir la représentation d'une valeur de date et d'heure qui est requise dans une opération d'analyse afin de convertir correctement la chaîne sous forme de date et d'heure. Une chaîne de format personnalisée se compose d'un ou de plusieurs spécificateurs de format de date et d'heure personnalisés. Toute chaîne autre qu’une [chaîne de format de date et d’heure standard](standard-datetime.md) est interprétée comme une chaîne de format de date et d’heure personnalisée. 

Les chaînes de format de date et d’heure personnalisées peuvent être utilisées avec les valeurs [DateTime](xref:System.DateTime) et [DateTimeOffset](xref:System.DateTimeOffset).

Dans les opérations de mise en forme, les chaînes de format de date et d'heure personnalisées peuvent être utilisées avec la méthode `ToString` d'une instance de date et d'heure ou avec une méthode qui prend en charge la mise en forme composite. L'exemple suivant illustre ces deux types d'utilisation. 

```csharp
DateTime thisDate1 = new DateTime(2011, 6, 10);
Console.WriteLine("Today is " + thisDate1.ToString("MMMM dd, yyyy") + ".");

DateTimeOffset thisDate2 = new DateTimeOffset(2011, 6, 10, 15, 24, 16, 
                                              TimeSpan.Zero);
Console.WriteLine("The current date and time: {0:MM/dd/yy H:mm:ss zzz}", 
                   thisDate2); 
// The example displays the following output:
//    Today is June 10, 2011.
//    The current date and time: 06/10/11 15:24:16 +00:00
```

```vb
Dim thisDate1 As Date = #6/10/2011#
Console.WriteLine("Today is " + thisDate1.ToString("MMMM dd, yyyy") + ".")

Dim thisDate2 As New DateTimeOffset(2011, 6, 10, 15, 24, 16, TimeSpan.Zero)
Console.WriteLine("The current date and time: {0:MM/dd/yy H:mm:ss zzz}", 
                   thisDate2) 
' The example displays the following output:
'    Today is June 10, 2011.
'    The current date and time: 06/10/11 15:24:16 +00:00
```

Dans les opérations d’analyse, les chaînes de format de date et d’heure personnalisées peuvent être utilisées avec les méthodes [DateTime.ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)), [DateTime.TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@)), [DateTimeOffset.ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)) et [DateTimeOffset.TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)). Pour que l’opération d’analyse aboutisse, ces méthodes requièrent qu’une chaîne d’entrée se conforme exactement à un modèle particulier. L’exemple suivant illustre un appel à la méthode [DateTimeOffset.ParseExact(String, String, IFormatProvider)](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)) pour analyser une date qui doit comprendre un jour, un mois et une année sur deux chiffres.

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string[] dateValues = { "30-12-2011", "12-30-2011", 
                              "30-12-11", "12-30-11" };
      string pattern = "MM-dd-yy";
      DateTime parsedDate;

      foreach (var dateValue in dateValues) {
         if (DateTime.TryParseExact(dateValue, pattern, null, 
                                   DateTimeStyles.None, out parsedDate))
            Console.WriteLine("Converted '{0}' to {1:d}.", 
                              dateValue, parsedDate);
         else
            Console.WriteLine("Unable to convert '{0}' to a date and time.", 
                              dateValue);
      }
   }
}
// The example displays the following output:
//    Unable to convert '30-12-2011' to a date and time.
//    Unable to convert '12-30-2011' to a date and time.
//    Unable to convert '30-12-11' to a date and time.
//    Converted '12-30-11' to 12/30/2011.
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim dateValues() As String = { "30-12-2011", "12-30-2011", 
                                      "30-12-11", "12-30-11" }
      Dim pattern As String = "MM-dd-yy"
      Dim parsedDate As Date

      For Each dateValue As String In dateValues
         If DateTime.TryParseExact(dateValue, pattern, Nothing, 
                                   DateTimeStyles.None, parsedDate) Then
            Console.WriteLine("Converted '{0}' to {1:d}.", 
                              dateValue, parsedDate)
         Else
            Console.WriteLine("Unable to convert '{0}' to a date and time.", 
                              dateValue)
         End If                                                         
      Next
   End Sub
End Module
' The example displays the following output:
'    Unable to convert '30-12-2011' to a date and time.
'    Unable to convert '12-30-2011' to a date and time.
'    Unable to convert '30-12-11' to a date and time.
'    Converted '12-30-11' to 12/30/2011.
```

Le tableau suivant décrit les spécificateurs de format de date et d'heure personnalisés et affiche une chaîne de résultat produite par chaque spécificateur de format. Par défaut, les chaînes de résultat reflètent les conventions de mise en forme de la culture en-US. Si un spécificateur de format particulier produit une chaîne de résultat localisée, l'exemple indique également la culture à laquelle la chaîne de résultat s'applique. Pour plus d'informations sur l'utilisation de chaînes de format de date et d'heure personnalisées, consultez la section Remarques.

Spécificateur de format | Description | Exemples
---------------- | ----------- | --------
"d" | Jour du mois, de 1 à 31. | `2019-06-01T13:45:30 -> 1`; `2019-06-15T13:45:30 -> 15`
"dd" | Jour du mois, de 01 à 31. | `2019-06-01T13:45:30 -> 1`; `2019-06-15T13:45:30 -> 15`
"ddd" | Nom abrégé du jour de la semaine. | `2019-06-15T13:45:30 -> Mon (en-US)`; `2019-06-15T13:45:30 -> Пн (ru-RU)`; `2019-06-15T13:45:30 -> lun. (fr-FR)`
"dddd" | Nom complet du jour de la semaine. | `2019-06-15T13:45:30 -> Monday (en-US)`; `2019-06-15T13:45:30 -> понедельник (ru-RU)`; `2019-06-15T13:45:30 -> lundi (fr-FR)`
"f" | Dixièmes de seconde dans une valeur de date et d'heure. | `2019-06-15T13:45:30.6170000 -> 6`; `2019-06-15T13:45:30.05 -> 0` 
"ff" | Centièmes de seconde dans une valeur de date et d'heure. | `2019-06-15T13:45:30.6170000 -> 61`; `2019-06-15T13:45:30.0050000 -> 00`
"fff" | Millisecondes dans une valeur de date et d'heure. | `6/15/2019 13:45:30.617 -> 617`; `6/15/2019 13:45:30.0005 -> 000`
"ffff" | Dix millièmes de seconde dans une valeur de date et d'heure. | `2019-06-15T13:45:30.6175000 -> 6175`; `2019-06-15T13:45:30.0000500 -> 0000`
"fffff" | Cent millièmes de seconde dans une valeur de date et d'heure. | `2019-06-15T13:45:30.6175400 -> 61754`; `6/15/2019 13:45:30.000005 -> 00000`
"ffffff" | Millionièmes de seconde dans une valeur de date et d'heure. | `2019-06-15T13:45:30.6175420 -> 617542`; `2019-06-15T13:45:30.0000005 -> 000000`
"fffffff" | Dix millionièmes de seconde dans une valeur de date et d'heure. | `2019-06-15T13:45:30.6175425 -> 6175425`;`2019-06-15T13:45:30.0001150 -> 0001150`
"F" | Si la valeur est différente de zéro, elle représente les dixièmes de seconde dans une valeur de date et d'heure. | `2019-06-15T13:45:30.6170000 -> 6`; `2019-06-15T13:45:30.0500000 -> (no output)`
"FF" | Si la valeur est différente de zéro, elle représente les centièmes de seconde dans une valeur de date et d'heure. | `2019-06-15T13:45:30.6170000 -> 61`; `2019-06-15T13:45:30.0050000 -> (no output)`
"FFF" | Si la valeur est différente de zéro, elle représente les millisecondes dans une valeur de date et d'heure. | `2019-06-15T13:45:30.6170000 -> 617`; `2019-06-15T13:45:30.0005000 -> (no output)`
"FFFF" | Si la valeur est différente de zéro, elle représente les dix millièmes de seconde dans une valeur de date et d'heure. | `2019-06-15T13:45:30.5275000 -> 5275`; `2019-06-15T13:45:30.0000500 -> (no output)`
"FFFFF" | Si la valeur est différente de zéro, elle représente les cent millièmes de seconde dans une valeur de date et d'heure. | `2019-06-15T13:45:30.6175400 -> 61754`; `2019-06-15T13:45:30.0000050 -> (no output)`
"FFFFFF" | Si la valeur est différente de zéro, elle représente les millionièmes de seconde dans une valeur de date et d'heure. | `2019-06-15T13:45:30.6175420 -> 617542`; `2019-06-15T13:45:30.0000005 -> (no output)`
"FFFFFFF" | Si la valeur est différente de zéro, elle représente les dix millionièmes de seconde dans une valeur de date et d'heure. | `2019-06-15T13:45:30.6175425 -> 6175425`; `2019-06-15T13:45:30.0001150 -> 000115`
"g", "gg" | Période ou ère. | `2019-06-15T13:45:30.6170000 -> A.D.`
"h" | Heure, au format de 12 heures, de 1 à 12. | `2019-06-15T01:45:30 -> 1`; `2019-06-15T13:45:30 -> 1`
"hh" | Heure, au format de 12 heures, de 01 à 12. | `2019-06-15T01:45:30 -> 01`; `2019-06-15T13:45:30 -> 01`
"H" | Heure, au format de 24 heures, de 0 à 23. | `2019-06-15T01:45:30 -> 1`; `2019-06-15T13:45:30 -> 13`
"HH" | Heure, au format de 24 heures, de 00 à 23. | `2019-06-15T01:45:30 -> 01`; `2019-06-15T13:45:30 -> 13`
"K" | Informations de fuseau horaire. | Avec les valeurs [DateTime](xref:System.DateTime) : `2019-06-15T13:45:30, Kind Unspecified ->`; `2019-06-15T13:45:30, Kind Utc -> Z`; `2019-06-15T13:45:30, Kind Local -> -07:00 (depends on local computer settings)`; Avec les valeurs [DateTimeOffset](xref:System.DateTimeOffset) : `2019-06-15T01:45:30-07:00 --> -07:00`; `2019-06-15T08:45:30+00:00 --> +00:00`
"m" | Minute, définie entre 0 et 59. | `2019-06-15T01:09:30 -> 9`; `2019-06-15T13:29:30 -> 29`
"mm" | Minute, définie entre 00 et 59. | `2019-06-15T01:09:30 -> 09`; `2019-06-15T01:45:30 -> 45`
"M" | Mois, de 1 à 12. | `2019-06-15T13:45:30 -> 6`
"MM" | Mois, de 01 à 12. | `2019-06-15T13:45:30 -> 06`
"MMM" | Nom abrégé du mois. | `2019-06-15T13:45:30 -> Jun (en-US)`; `2019-06-15T13:45:30 -> juin (fr-FR)`; `2019-06-15T13:45:30 -> Jun (zu-ZA)`
"MMMM" | Nom complet du mois. | `2019-06-15T13:45:30 -> June (en-US)`; `2019-06-15T13:45:30 -> juni (da-DK)`; `2019-06-15T13:45:30 -> uJuni (zu-ZA)`
"s" | Seconde, de 0 à 59. | `2019-06-15T13:45:09 -> 9`
"ss" | Seconde, de 00 à 59. | `2019-06-15T13:45:09 -> 09`
"t" | Premier caractère de l'indicateur AM/PM. | `2019-06-15T13:45:30 -> P (en-US)`; `2019-06-15T13:45:30 -> 午 (ja-JP)`; `2019-06-15T13:45:30 -> (fr-FR)`
"tt" | Indicateur AM/PM. | `2019-06-15T13:45:30 -> PM (en-US)`; `2019-06-15T13:45:30 -> 午後 (ja-JP)`; `2019-06-15T13:45:30 -> (fr-FR)`
"y" | Année, de 0 à 99. | `0001-01-01T00:00:00 -> 1`; `0900-01-01T00:00:00 -> 0`; `1900-01-01T00:00:00 -> 0`; `2019-06-15T13:45:30 -> 9`; `2019-06-15T13:45:30 -> 19`
"yy" | Année, de 00 à 99. | `0001-01-01T00:00:00 -> 01`; `0900-01-01T00:00:00 -> 00`; `1900-01-01T00:00:00 -> 00`; `2019-06-15T13:45:30 -> 19`
"yyy" | Année, avec au minimum trois chiffres. | `0001-01-01T00:00:00 -> 001`; `0900-01-01T00:00:00 -> 900`; `1900-01-01T00:00:00 -> 1900`; `2019-06-15T13:45:30 -> 2019`
"yyyy" | Année, en tant que nombre à quatre chiffres. | `0001-01-01T00:00:00 -> 0001`; `0900-01-01T00:00:00 -> 0900`; `1900-01-01T00:00:00 -> 1900`; `2019-06-15T13:45:30 -> 2019`
"yyyyy" | Année, en tant que nombre à cinq chiffres. | `0001-01-01T00:00:00 -> 00001`; `2019-06-15T13:45:30 -> 02019`
"z" | Décalage horaire par rapport à l'heure UTC, sans zéro non significatif. | `2019-06-15T13:45:30-07:00 -> -7`
"zz" | Décalage horaire par rapport à l'heure UTC, avec un zéro non significatif pour une valeur à un seul chiffre. | `2019-06-15T13:45:30-07:00 -> -07`
"zzz" | Décalage horaire par rapport à l'heure UTC, en heures et minutes. | `2019-06-15T13:45:30-07:00 -> -07:00`
":" | Séparateur horaire. | `2019-06-15T13:45:30 -> : (en-US)`; `2019-06-15T13:45:30 -> . (it-IT)`; `2019-06-15T13:45:30 -> : (ja-JP)`
"/" | Séparateur de date. | `2019-06-15T13:45:30 -> / (en-US)`; `2019-06-15T13:45:30 -> - (ar-DZ)`; `2019-06-15T13:45:30 -> . (tr-TR)`
"chaîne", 'chaîne' | Délimiteur de chaîne littérale. | `2019-06-15T13:45:30 ("arr:" h:m t) -> arr: 1:45 P`; `2019-06-15T13:45:30 ('arr:' h:m t) -> arr: 1:45 P`
% | Définit le caractère suivant comme spécificateur de format personnalisé. | `2019-06-15T13:45:30 (%h) -> 1`
\ | Caractère d'échappement. | `2019-06-15T13:45:30 (h \h) -> 1 h`
N'importe quel autre caractère | Le caractère est copié inchangé dans la chaîne de résultat. | `2019-06-15T01:45:30 (arr hh:mm t) -> arr 01:45 A`

Les sections suivantes fournissent des informations supplémentaires sur chaque spécificateur de format de date et d'heure personnalisé. Sauf indication contraire, chaque spécificateur produit une représentation sous forme de chaîne identique, qu’il soit utilisé avec une valeur [DateTime](xref:System.DateTime) ou une valeur [DateTimeOffset](xref:System.DateTimeOffset). 

## <a name="the-d-custom-format-specifier"></a>Spécificateur de format personnalisé "d"

Le spécificateur de format personnalisé "d" représente le jour du mois sous la forme d'un nombre compris entre 1 et 31. Un jour à un seul chiffre est mis en forme sans zéro non significatif. 

Si le spécificateur de format "d" est utilisé sans autre spécificateur de format personnalisé, il est interprété comme le spécificateur de format de date et d'heure standard "d". Pour plus d’informations sur l’utilisation d’un spécificateur de format unique, consultez [Utilisation de spécificateurs de format personnalisés uniques](#using-single-custom-format-specifiers), plus loin dans cette rubrique.

L'exemple suivant inclut le spécificateur de format personnalisé "d" dans plusieurs chaînes de format. 

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15); 

Console.WriteLine(date1.ToString("d, M", 
                  CultureInfo.InvariantCulture)); 
// Displays 29, 8

Console.WriteLine(date1.ToString("d MMMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays 29 August
Console.WriteLine(date1.ToString("d MMMM", 
                  CultureInfo.CreateSpecificCulture("es-MX")));
// Displays 29 agosto  
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("d, M", _
                  CultureInfo.InvariantCulture)) 
' Displays 29, 8

Console.WriteLine(date1.ToString("d MMMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays 29 August
Console.WriteLine(date1.ToString("d MMMM", _
                  CultureInfo.CreateSpecificCulture("es-MX")))
' Displays 29 agosto 
```

## <a name="the-dd-custom-format-specifier"></a>Spécificateur de format personnalisé "dd"

Le spécificateur de format personnalisé "dd" représente le jour du mois sous la forme d'un nombre compris entre 01 et 31. Un jour à un seul chiffre est mis en forme avec un zéro non significatif. 

L'exemple suivant inclut le spécificateur de format personnalisé "dd" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(2008, 1, 2, 6, 30, 15);

Console.WriteLine(date1.ToString("dd, MM", 
                  CultureInfo.InvariantCulture)); 
// 02, 01
```

```vb
Dim date1 As Date = #1/2/2008 6:30:15AM#

Console.WriteLine(date1.ToString("dd, MM", _
                  CultureInfo.InvariantCulture)) 
' 02, 01
```

## <a name="the-ddd-custom-format-specifier"></a>Spécificateur de format personnalisé "ddd"

Le spécificateur de format personnalisé "ddd" représente le nom abrégé du jour de la semaine. Le nom abrégé localisé du jour de la semaine est récupéré de la propriété [DateTimeFormatInfo.AbbreviatedDayNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames) de la culture actuelle ou spécifiée. 

L'exemple suivant inclut le spécificateur de format personnalisé "ddd" dans une chaîne de format personnalisée. 

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15);

Console.WriteLine(date1.ToString("ddd d MMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Fri 29 Aug
Console.WriteLine(date1.ToString("ddd d MMM", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays ven. 29 août    
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("ddd d MMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Fri 29 Aug
Console.WriteLine(date1.ToString("ddd d MMM", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays ven. 29 août
```

## <a name="the-dddd-custom-format-specifier"></a>Spécificateur de format personnalisé "dddd"

Le spécificateur de format personnalisé "dddd" (plus n'importe quel nombre de spécificateurs "d" supplémentaires) représente le nom complet du jour de la semaine. Le nom localisé du jour de la semaine est récupéré de la propriété [DateTimeFormatInfo.DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) de la culture actuelle ou spécifiée. 

L'exemple suivant inclut le spécificateur de format personnalisé "dddd" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15);

Console.WriteLine(date1.ToString("dddd dd MMMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Friday 29 August
Console.WriteLine(date1.ToString("dddd dd MMMM", 
                  CultureInfo.CreateSpecificCulture("it-IT")));
// Displays venerdì 29 agosto    
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("dddd dd MMMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Friday 29 August
Console.WriteLine(date1.ToString("dddd dd MMMM", _
                  CultureInfo.CreateSpecificCulture("it-IT")))
' Displays venerdì 29 agosto                                          
```

## <a name="the-f-custom-format-specifier"></a>Spécificateur de format personnalisé "f"

Le spécificateur de format personnalisé "f" représente le chiffre le plus significatif de la fraction de seconde ; autrement dit, il représente les dixièmes de seconde dans une valeur de date et d'heure.

Si le spécificateur de format "f" est utilisé sans autre spécificateur de format, il est interprété comme le spécificateur de format de date et d'heure standard "f". Pour plus d’informations sur l’utilisation d’un spécificateur de format unique, consultez [Utilisation de spécificateurs de format personnalisés uniques](#using-single-custom-format-specifiers), plus loin dans cette rubrique.

Quand vous utilisez le spécificateur de format "f" dans le cadre d’une chaîne de format fournie à la méthode [DateTime.ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)), [DateTime.TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@)), [DateTimeOffset.ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)) ou [DateTimeOffset.TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)), le nombre de spécificateurs de format "f" utilisés indique le nombre des chiffres les plus significatifs de la fraction de seconde nécessaires pour analyser correctement la chaîne.

L'exemple suivant inclut le spécificateur de format personnalisé "f" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-ff-custom-format-specifier"></a>Spécificateur de format personnalisé "ff"

Le spécificateur de format personnalisé "ff" représente les deux chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les centièmes de seconde dans une valeur de date et d'heure. 

L’exemple suivant inclut le spécificateur de format personnalisé "ff" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-fff-custom-format-specifier"></a>Spécificateur de format personnalisé "fff"

Le spécificateur de format personnalisé "fff" représente les trois chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les millisecondes dans une valeur de date et d'heure. 

L'exemple suivant inclut le spécificateur de format personnalisé "fff" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-ffff-custom-format-specifier"></a>Spécificateur de format personnalisé "ffff"

Le spécificateur de format personnalisé "ffff" représente les quatre chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les dix millièmes de seconde dans une valeur de date et d'heure.

Bien qu'il soit possible d'afficher les dix millièmes du composant "secondes" d'une valeur d'heure, cette valeur peut ne pas être significative. La précision des valeurs de date et d’heure dépend de la résolution de l’horloge système.

## <a name="the-fffff-custom-format-specifier"></a>Spécificateur de format personnalisé "fffff"

Le spécificateur de format personnalisé "fffff" représente les cinq chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les cent millièmes de seconde dans une valeur de date et d'heure.

Bien qu'il soit possible d'afficher les cent millièmes du composant "secondes" d'une valeur d'heure, cette valeur peut ne pas être significative. La précision des valeurs de date et d’heure dépend de la résolution de l’horloge système. 

## <a name="the-ffffff-custom-format-specifier"></a>Spécificateur de format personnalisé "ffffff"

Le spécificateur de format personnalisé "ffffff" représente les six chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les millionièmes de seconde dans une valeur de date et d'heure.

Bien qu'il soit possible d'afficher les millionièmes du composant "secondes" d'une valeur d'heure, cette valeur peut ne pas être significative. La précision des valeurs de date et d’heure dépend de la résolution de l’horloge système. 

## <a name="the-fffffff-custom-format-specifier"></a>Spécificateur de format personnalisé "fffffff"

Le spécificateur de format personnalisé "fffffff" représente les sept chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les dix millionièmes de seconde dans une valeur de date et d'heure.

Bien qu'il soit possible d'afficher les dix millionièmes du composant "secondes" d'une valeur d'heure, cette valeur peut ne pas être significative. La précision des valeurs de date et d’heure dépend de la résolution de l’horloge système. 

## <a name="the-f-custom-format-specifier"></a>Spécificateur de format personnalisé "F"

Le spécificateur de format personnalisé "F" représente le chiffre le plus significatif de la fraction de seconde ; autrement dit, il représente les dixièmes de seconde dans une valeur de date et d'heure. Rien ne s'affiche si le chiffre est zéro. 

Si le spécificateur de format "F" est utilisé sans autre spécificateur de format, il est interprété comme le spécificateur de format de date et d'heure standard "F". Pour plus d’informations sur l’utilisation d’un spécificateur de format unique, consultez [Utilisation de spécificateurs de format personnalisés uniques](#using-single-custom-format-specifiers), plus loin dans cette rubrique.

Le nombre de spécificateurs de format "f" utilisés avec la méthode [DateTime.ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)), [DateTime.TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@)), [DateTimeOffset.ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)), ou [DateTimeOffset.TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)) indique le nombre maximal de chiffres les plus significatifs de la fraction de seconde pouvant être présents pour analyser correctement la chaîne.

L'exemple suivant inclut le spécificateur de format personnalisé "F" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-ff-custom-format-specifier"></a>Spécificateur de format personnalisé "FF"

Le spécificateur de format personnalisé "FF" représente les deux chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les centièmes de seconde dans une valeur de date et d'heure. Toutefois, les zéros de fin ou deux chiffres zéro ne sont pas affichés. 

L'exemple suivant inclut le spécificateur de format personnalisé "FF" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-fff-custom-format-specifier"></a>Spécificateur de format personnalisé "FFF"

Le spécificateur de format personnalisé "FFF" représente les trois chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les millisecondes dans une valeur de date et d'heure. Toutefois, les zéros de fin ou trois chiffres zéro ne sont pas affichés. 

L'exemple suivant inclut le spécificateur de format personnalisé "FFF" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
````

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-ffff-custom-format-specifier"></a>Spécificateur de format personnalisé "FFFF"

Le spécificateur de format personnalisé "FFFF" représente les quatre chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les dix millièmes de seconde dans une valeur de date et d'heure. Toutefois, les zéros de fin ou quatre chiffres zéro ne sont pas affichés.

Bien qu'il soit possible d'afficher les dix millièmes du composant "secondes" d'une valeur d'heure, cette valeur peut ne pas être significative. La précision des valeurs de date et d’heure dépend de la résolution de l’horloge système.

## <a name="the-fffff-custom-format-specifier"></a>Spécificateur de format personnalisé "FFFFF"

Le spécificateur de format personnalisé "FFFFF" représente les cinq chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les cent millièmes de seconde dans une valeur de date et d'heure. Toutefois, les zéros de fin ou cinq chiffres zéro ne sont pas affichés.

Bien qu'il soit possible d'afficher les cent millièmes du composant "secondes" d'une valeur d'heure, cette valeur peut ne pas être significative. La précision des valeurs de date et d’heure dépend de la résolution de l’horloge système.

## <a name="the-ffffff-custom-format-specifier"></a>Spécificateur de format personnalisé "FFFFFF"

Le spécificateur de format personnalisé "FFFFFF" représente les six chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les millionièmes de seconde dans une valeur de date et d'heure. Toutefois, les zéros de fin ou six chiffres zéro ne sont pas affichés.

Bien qu'il soit possible d'afficher les millionièmes du composant "secondes" d'une valeur d'heure, cette valeur peut ne pas être significative. La précision des valeurs de date et d’heure dépend de la résolution de l’horloge système.

## <a name="the-fffffff-custom-format-specifier"></a>Spécificateur de format personnalisé "FFFFFFF"

Le spécificateur de format personnalisé "FFFFFFF" représente les sept chiffres les plus significatifs de la fraction de seconde ; autrement dit, il représente les dix millionièmes de seconde dans une valeur de date et d'heure. Toutefois, les zéros de fin ou sept chiffres zéro ne sont pas affichés.

Bien qu'il soit possible d'afficher les dix millionièmes du composant "secondes" d'une valeur d'heure, cette valeur peut ne pas être significative. La précision des valeurs de date et d’heure dépend de la résolution de l’horloge système.

## <a name="the-g-or-gg-custom-format-specifier"></a>Spécificateur de format personnalisé "g" ou "gg"

Les spécificateurs de format personnalisés "g" ou "gg" (plus n'importe quel nombre de spécificateurs "g" supplémentaires) représentent la période ou l'ère, par exemple après J.-C. L'opération de mise en forme ignore ce spécificateur si la date à mettre en forme n'est associée à aucune chaîne de période ou d'ère. 

Si le spécificateur de format "g" est utilisé sans autre spécificateur de format personnalisé, il est interprété comme le spécificateur de format de date et d'heure standard "g". Pour plus d’informations sur l’utilisation d’un spécificateur de format unique, consultez [Utilisation de spécificateurs de format personnalisés uniques](#using-single-custom-format-specifiers), plus loin dans cette rubrique.

L'exemple suivant inclut le spécificateur de format personnalisé "g" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(70, 08, 04);

Console.WriteLine(date1.ToString("MM/dd/yyyy g", 
                  CultureInfo.InvariantCulture));
// Displays 08/04/0070 A.D.                        
Console.WriteLine(date1.ToString("MM/dd/yyyy g", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));                         
// Displays 08/04/0070 ap. J.-C.
```

```vb
Dim date1 As Date = #08/04/0070#

Console.WriteLine(date1.ToString("MM/dd/yyyy g", _
                  CultureInfo.InvariantCulture))
' Displays 08/04/0070 A.D.                        
Console.WriteLine(date1.ToString("MM/dd/yyyy g", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))                         
' Displays 08/04/0070 ap. J.-C.
```

## <a name="the-h-custom-format-specifier"></a>Spécificateur de format personnalisé "h"

Le spécificateur de format personnalisé "h" représente l'heure sous la forme d'un nombre compris entre 1 et 12 ; autrement dit, l'heure est représentée au format de 12 heures qui compte les heures entières depuis minuit ou midi. Une heure après minuit se présente de la même manière que la même heure après midi. L'heure n'est pas arrondie et une heure à un seul chiffre est mise en forme sans zéro non significatif. Par exemple, si on considère l'heure 5:43 du matin ou de l'après-midi, ce spécificateur de format personnalisé affiche "5". 

Si le spécificateur de format "h" est utilisé sans autre spécificateur de format personnalisé, il est interprété comme un spécificateur de format de date et d’heure standard et lève un [FormatException](xref:System.FormatException). Pour plus d’informations sur l’utilisation d’un spécificateur de format unique, consultez [Utilisation de spécificateurs de format personnalisés uniques](#using-single-custom-format-specifiers), plus loin dans cette rubrique.

L'exemple suivant inclut le spécificateur de format personnalisé "h" dans une chaîne de format personnalisée.

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1 µ                        
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1.5 µ
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1 µ                        
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1.5 µ
```

## <a name="the-hh-custom-format-specifier"></a>Spécificateur de format personnalisé "hh"

Le spécificateur de format personnalisé "hh" (plus n'importe quel nombre de spécificateurs "h" supplémentaires) représente l'heure sous la forme d'un nombre compris entre 01 et 12 ; autrement dit, l'heure est représentée au format de 12 heures qui compte les heures entières depuis minuit ou midi. Une heure après minuit se présente de la même manière que la même heure après midi. L'heure n'est pas arrondie et une heure à un seul chiffre est mise en forme avec un zéro non significatif. Par exemple, si on considère l'heure 5:43 du matin ou de l'après-midi, ce spécificateur de format affiche "05".

L'exemple suivant inclut le spécificateur de format personnalisé "hh" dans une chaîne de format personnalisée.

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01 du.
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01.50 du.
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01 du.
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01.50 du.
```

## <a name="the-h-custom-format-specifier"></a>Spécificateur de format personnalisé "H"

Le spécificateur de format personnalisé "H" représente l'heure sous la forme d'un nombre compris entre 0 et 23 ; autrement dit, l'heure est représentée au format de 24 heures de base zéro qui compte les heures depuis minuit. Une heure à un seul chiffre est mise en forme sans zéro non significatif. 

Si le spécificateur de format "H" est utilisé sans autre spécificateur de format personnalisé, il est interprété comme un spécificateur de format de date et d’heure standard et lève un [FormatException](xref:System.FormatException). Pour plus d’informations sur l’utilisation d’un spécificateur de format unique, consultez [Utilisation de spécificateurs de format personnalisés uniques](#using-single-custom-format-specifiers), plus loin dans cette rubrique.

L'exemple suivant inclut le spécificateur de format personnalisé "H" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(2008, 1, 1, 6, 9, 1);
Console.WriteLine(date1.ToString("H:mm:ss", 
                  CultureInfo.InvariantCulture));
// Displays 6:09:01 
```

```vb
Dim date1 As Date = #6:09:01AM#
Console.WriteLine(date1.ToString("H:mm:ss", _
                  CultureInfo.InvariantCulture))
' Displays 6:09:01 
```

## <a name="the-hh-custom-format-specifier"></a>Spécificateur de format personnalisé "HH"

Le spécificateur de format personnalisé "HH" (plus n'importe quel nombre de spécificateurs "H" supplémentaires) représente l'heure sous la forme d'un nombre compris entre 00 et 23 ; autrement dit, l'heure est représentée au format de 24 heures de base zéro qui compte les heures depuis minuit. Une heure à un seul chiffre est mise en forme avec un zéro non significatif. 

L'exemple suivant inclut le spécificateur de format personnalisé "HH" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(2008, 1, 1, 6, 9, 1);
Console.WriteLine(date1.ToString("HH:mm:ss", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01                        
```

```vb
Dim date1 As Date = #6:09:01AM#
Console.WriteLine(date1.ToString("HH:mm:ss", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01
```

## <a name="the-k-custom-format-specifier"></a>Spécificateur de format personnalisé "K"

Le spécificateur de format personnalisé "K" représente les informations de fuseau horaire d'une valeur de date et d'heure. Quand ce spécificateur de format est utilisé avec les valeurs [DateTime](xref:System.DateTime), la chaîne de résultat est définie par la valeur de la propriété [DateTime.Kind](xref:System.DateTime.Kind) : 
 
* Pour le fuseau horaire local (une valeur de propriété [DateTime.Kind](xref:System.DateTime.Kind) de [DateTimeKind.Local](xref:System.DateTimeKind.Local)), ce spécificateur est équivalent au spécificateur "zzz" et produit une chaîne de résultat contenant l’offset local par rapport au temps universel coordonné (UTC, Universal Time Coordinated) ; par exemple, "-07:00". 

* Pour une heure UTC (une valeur de propriété [DateTime.Kind](xref:System.DateTime.Kind) de [DateTimeKind.Utc](xref:System.DateTimeKind.Utc)), la chaîne de résultat inclut un caractère "Z" pour représenter une date UTC. 

* Pour une heure d’un fuseau horaire non spécifié (une heure dont la propriété [DateTime.Kind](xref:System.DateTime.Kind) a la valeur [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified)), le résultat est équivalent à [String.Empty](xref:System.String#System_String_Empty). 

Pour les valeurs [DateTimeOffset](xref:System.DateTimeOffset), le spécificateur de format "K" est équivalent au spécificateur de format "zz", et produit une chaîne de résultat contenant l’offset de la valeur[DateTimeOffset](xref:System.DateTimeOffset) par rapport à l’heure UTC. 

Si le spécificateur de format "K" est utilisé sans autre spécificateur de format personnalisé, il est interprété comme un spécificateur de format de date et d’heure standard et lève un [FormatException](xref:System.FormatException). Pour plus d’informations sur l’utilisation d’un spécificateur de format unique, consultez [Utilisation de spécificateurs de format personnalisés uniques](#using-single-custom-format-specifiers), plus loin dans cette rubrique.

L’exemple suivant affiche la chaîne qui résulte de l’utilisation du spécificateur de format personnalisé "K" avec différentes valeurs [DateTime](xref:System.DateTime) et [DateTimeOffset](xref:System.DateTimeOffset) sur un système situé dans le fuseau horaire Pacifique (États-Unis).

```csharp
Console.WriteLine(DateTime.Now.ToString("%K"));
// Displays -07:00
Console.WriteLine(DateTime.UtcNow.ToString("%K"));
// Displays Z      
Console.WriteLine("'{0}'", 
                  DateTime.SpecifyKind(DateTime.Now, 
                       DateTimeKind.Unspecified).ToString("%K"));
// Displays ''      
Console.WriteLine(DateTimeOffset.Now.ToString("%K"));
// Displays -07:00
Console.WriteLine(DateTimeOffset.UtcNow.ToString("%K"));
// Displays +00:00
Console.WriteLine(new DateTimeOffset(2008, 5, 1, 6, 30, 0, 
                      new TimeSpan(5, 0, 0)).ToString("%K"));
// Displays +05:00  
```

```vb
Console.WriteLine(Date.Now.ToString("%K"))
' Displays -07:00
Console.WriteLine(Date.UtcNow.ToString("%K"))
' Displays Z      
Console.WriteLine("'{0}'", _
                  Date.SpecifyKind(Date.Now, _
                                   DateTimeKind.Unspecified). _
                  ToString("%K"))
' Displays ''      
Console.WriteLine(DateTimeOffset.Now.ToString("%K"))
' Displays -07:00
Console.WriteLine(DateTimeOffset.UtcNow.ToString("%K"))
' Displays +00:00
Console.WriteLine(New DateTimeOffset(2008, 5, 1, 6, 30, 0, _
                                     New TimeSpan(5, 0, 0)). _
                  ToString("%K"))
' Displays +05:00 
```

## <a name="the-m-custom-format-specifier"></a>Spécificateur de format personnalisé "m"

Le spécificateur de format personnalisé "m" représente la minute sous la forme d'un nombre compris entre 0 et 59. La minute représente les minutes entières qui se sont écoulées depuis la dernière heure. Une minute à un seul chiffre est mise en forme sans zéro non significatif. 

Si le spécificateur de format "m" est utilisé sans autre spécificateur de format personnalisé, il est interprété comme le spécificateur de format de date et d'heure standard "m". Pour plus d’informations sur l’utilisation d’un spécificateur de format unique, consultez [Utilisation de spécificateurs de format personnalisés uniques](#using-single-custom-format-specifiers), plus loin dans cette rubrique. 

L'exemple suivant inclut le spécificateur de format personnalisé "m" dans une chaîne de format personnalisée.

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1 µ                        
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1.5 µ
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1 µ                        
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1.5 µ
```

## <a name="the-mm-custom-format-specifier"></a>Spécificateur de format personnalisé "mm"

Le spécificateur de format personnalisé "mm" (plus n'importe quel nombre de spécificateurs "m" supplémentaires) représente la minute sous la forme d'un nombre compris entre 00 et 59. La minute représente les minutes entières qui se sont écoulées depuis la dernière heure. Une minute à un seul chiffre est mise en forme avec un zéro non significatif. 

L'exemple suivant inclut le spécificateur de format personnalisé "mm" dans une chaîne de format personnalisée.

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01 du.
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01.50 du.
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01 du.
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01.50 du.
```

## <a name="the-m-custom-format-specifier"></a>Spécificateur de format personnalisé "M"

Le spécificateur de format personnalisé "M" représente le mois comme un nombre compris entre 1 et 12 (ou entre 1 et 13 pour les calendriers de 13 mois). Un mois à un seul chiffre est mis en forme sans zéro non significatif. 

Si le spécificateur de format "M" est utilisé sans autre spécificateur de format personnalisé, il est interprété comme le spécificateur de format de date et d'heure standard "M". Pour plus d’informations sur l’utilisation d’un spécificateur de format unique, consultez [Utilisation de spécificateurs de format personnalisés uniques](#using-single-custom-format-specifiers), plus loin dans cette rubrique.

L'exemple suivant inclut le spécificateur de format personnalisé "M" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(2008, 8, 18);
Console.WriteLine(date1.ToString("(M) MMM, MMMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays (8) Aug, August
Console.WriteLine(date1.ToString("(M) MMM, MMMM", 
                  CultureInfo.CreateSpecificCulture("nl-NL")));                       
// Displays (8) aug, augustus
Console.WriteLine(date1.ToString("(M) MMM, MMMM", 
                  CultureInfo.CreateSpecificCulture("lv-LV")));                        
// Displays (8) Aug, augusts
```

```vb
Dim date1 As Date = #8/18/2008#
Console.WriteLine(date1.ToString("(M) MMM, MMMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays (8) Aug, August
Console.WriteLine(date1.ToString("(M) MMM, MMMM", _
                  CultureInfo.CreateSpecificCulture("nl-NL")))                        
' Displays (8) aug, augustus
Console.WriteLine(date1.ToString("(M) MMM, MMMM", _
                  CultureInfo.CreateSpecificCulture("lv-LV")))                        
' Displays (8) Aug, augusts 
```

## <a name="the-mm-custom-format-specifier"></a>Spécificateur de format personnalisé "MM"

Le spécificateur de format personnalisé "MM" représente le mois comme un nombre compris entre 01 et 12 (ou entre 01 et 13 pour les calendriers de 13 mois). Un mois à un seul chiffre est mis en forme avec un zéro non significatif. 

L'exemple suivant inclut le spécificateur de format personnalisé "MM" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(2008, 1, 2, 6, 30, 15);

Console.WriteLine(date1.ToString("dd, MM", 
                  CultureInfo.InvariantCulture)); 
// 02, 01
```

```vb
Dim date1 As Date = #1/2/2008 6:30:15AM#

Console.WriteLine(date1.ToString("dd, MM", _
                  CultureInfo.InvariantCulture)) 
' 02, 01
```

## <a name="the-mmm-custom-format-specifier"></a>Spécificateur de format personnalisé "MMM"

Le spécificateur de format personnalisé "MMM" représente le nom abrégé du mois. Le nom abrégé localisé du mois est récupéré de la propriété [DateTimeFormatInfo.AbbreviatedMonthNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames) de la culture actuelle ou spécifiée.

L'exemple suivant inclut le spécificateur de format personnalisé "MMM" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15);

Console.WriteLine(date1.ToString("ddd d MMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Fri 29 Aug
Console.WriteLine(date1.ToString("ddd d MMM", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays ven. 29 août
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("ddd d MMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Fri 29 Aug
Console.WriteLine(date1.ToString("ddd d MMM", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays ven. 29 août
```

## <a name="the-mmmm-custom-format-specifier"></a>Spécificateur de format personnalisé "MMMM"

Le spécificateur de format personnalisé "MMMM" représente le nom complet du mois. Le nom localisé du mois est récupéré de la propriété [DateTimeFormatInfo.MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) de la culture actuelle ou spécifiée. 

L'exemple suivant inclut le spécificateur de format personnalisé "MMMM" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15);

Console.WriteLine(date1.ToString("dddd dd MMMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Friday 29 August
Console.WriteLine(date1.ToString("dddd dd MMMM", 
                  CultureInfo.CreateSpecificCulture("it-IT")));
// Displays venerdì 29 agosto 
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("dddd dd MMMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Friday 29 August
Console.WriteLine(date1.ToString("dddd dd MMMM", _
                  CultureInfo.CreateSpecificCulture("it-IT")))
' Displays venerdì 29 agosto  
```

## <a name="the-s-custom-format-specifier"></a>Spécificateur de format personnalisé "s"

Le spécificateur de format personnalisé "s" représente les secondes sous la forme d'un nombre compris entre 0 et 59. Le résultat représente les secondes entières qui se sont écoulées depuis la dernière minute. Une seconde à un seul chiffre est mise en forme sans zéro non significatif. 

Si le spécificateur de format "s" est utilisé sans autre spécificateur de format personnalisé, il est interprété comme le spécificateur de format de date et d'heure standard "s". Pour plus d’informations sur l’utilisation d’un spécificateur de format unique, consultez [Utilisation de spécificateurs de format personnalisés uniques](#using-single-custom-format-specifiers), plus loin dans cette rubrique. 

L'exemple suivant inclut le spécificateur de format personnalisé "s" dans une chaîne de format personnalisée.

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1 µ                        
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1.5 µ
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1 µ                        
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1.5 µ
```

## <a name="the-ss-custom-format-specifier"></a>Spécificateur de format personnalisé "ss"

Le spécificateur de format personnalisé "ss" (plus n'importe quel nombre de spécificateurs "s" supplémentaires) représente les secondes sous la forme d'un nombre compris entre 00 et 59. Le résultat représente les secondes entières qui se sont écoulées depuis la dernière minute. Une seconde à un seul chiffre est mise en forme avec un zéro non significatif. 

L'exemple suivant inclut le spécificateur de format personnalisé "ss" dans une chaîne de format personnalisée.

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01 du.
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01.50 du.
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01 du.
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01.50 du.
```

## <a name="the-t-custom-format-specifier"></a>Spécificateur de format personnalisé "t"

Le spécificateur de format personnalisé "t" représente le premier caractère de l'indicateur AM/PM. L’indicateur localisé approprié est récupéré de la propriété [DateTimeFormatInfo.AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) ou [DateTimeFormatInfo.PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) de la culture actuelle ou spécifique. L'indicateur AM est utilisé pour toutes les heures comprises entre 0:00:00 (minuit) et 11:59:59.999. L'indicateur PM est utilisé pour toutes les heures comprises entre 12:00:00 (midi) et 23:59:59.999. 

Si le spécificateur de format "t" est utilisé sans autre spécificateur de format personnalisé, il est interprété comme le spécificateur de format de date et d'heure standard "t". Pour plus d’informations sur l’utilisation d’un spécificateur de format unique, consultez [Utilisation de spécificateurs de format personnalisés uniques](#using-single-custom-format-specifiers), plus loin dans cette rubrique.

L'exemple suivant inclut le spécificateur de format personnalisé "t" dans une chaîne de format personnalisée.

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1 µ                        
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1.5 µ
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1 µ                        
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1.5 µ
```

## <a name="the-tt-custom-format-specifier"></a>Spécificateur de format personnalisé "tt"

Le spécificateur de format personnalisé "tt" (plus n'importe quel nombre de spécificateurs "t" supplémentaires) représente l'intégralité de l'indicateur AM/PM. L’indicateur localisé approprié est récupéré de la propriété [DateTimeFormatInfo.AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) ou [DateTimeFormatInfo.PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) de la culture actuelle ou spécifique. L'indicateur AM est utilisé pour toutes les heures comprises entre 0:00:00 (minuit) et 11:59:59.999. L'indicateur PM est utilisé pour toutes les heures comprises entre 12:00:00 (midi) et 23:59:59.999.

Veillez à utiliser le spécificateur "tt" pour les langues pour lesquelles il est nécessaire de maintenir la distinction entre AM et PM. Un exemple est illustré par la langue japonaise, pour laquelle les indicateurs AM/PM se distinguent dans le deuxième caractère au lieu du premier.

L'exemple suivant inclut le spécificateur de format personnalisé "tt" dans une chaîne de format personnalisée.

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01 du.
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01.50 du.
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01 du.
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01.50 du.
```

## <a name="the-y-custom-format-specifier"></a>Spécificateur de format personnalisé "y"

Le spécificateur de format personnalisé "y" représente l'année sous la forme d'un nombre à un chiffre ou à deux chiffres. Si l'année comporte plus de deux chiffres, seuls les deux chiffres de poids faible apparaissent dans le résultat. Si le premier chiffre d'une année sur deux chiffres commence par un zéro (par exemple, 2008), le nombre est mis en forme sans zéro non significatif. 

Si le spécificateur de format "y" est utilisé sans autre spécificateur de format personnalisé, il est interprété comme le spécificateur de format de date et d'heure standard "y". Pour plus d’informations sur l’utilisation d’un spécificateur de format unique, consultez [Utilisation de spécificateurs de format personnalisés uniques](#using-single-custom-format-specifiers), plus loin dans cette rubrique.

L'exemple suivant inclut le spécificateur de format personnalisé "y" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010
```

## <a name="the-yy-custom-format-specifier"></a>Spécificateur de format personnalisé "yy"

Le spécificateur de format personnalisé "yy" représente l'année sous la forme d'un nombre à deux chiffres. Si l'année comporte plus de deux chiffres, seuls les deux chiffres de poids faible apparaissent dans le résultat. Si l'année à deux chiffres comporte moins de deux chiffres significatifs, le nombre est complété avec des zéros non significatifs pour qu'il possède deux chiffres.

Dans une opération d’analyse, une année à deux chiffres qui est analysée avec le spécificateur de format personnalisé "yy" est interprétée sur la base de la propriété [Calendar.TwoDigitYearMax](xref:System.Globalization.Calendar.TwoDigitYearMax) du calendrier actuel du fournisseur de format. L'exemple suivant analyse la représentation sous forme de chaîne d'une date ayant une année à deux chiffres, en utilisant le calendrier grégorien par défaut de la culture en-US, laquelle représente la culture actuelle. Il remplace ensuite l’objet [CultureInfo](xref:System.Globalization.CultureInfo) de la culture actuelle afin d’utiliser un objet [GregorianCalendar](xref:System.Globalization.GregorianCalendar) dont la propriété [TwoDigitYearMax](xref:System.Globalization.GregorianCalendar.TwoDigitYearMax) a été modifiée.

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string fmt = "dd-MMM-yy";
      string value = "24-Jan-49";

      Calendar cal = (Calendar) CultureInfo.CurrentCulture.Calendar.Clone();
      Console.WriteLine("Two Digit Year Range: {0} - {1}", 
                        cal.TwoDigitYearMax - 99, cal.TwoDigitYearMax);

      Console.WriteLine("{0:d}", DateTime.ParseExact(value, fmt, null));
      Console.WriteLine();

      cal.TwoDigitYearMax = 2099;
      CultureInfo culture = (CultureInfo) CultureInfo.CurrentCulture.Clone();
      culture.DateTimeFormat.Calendar = cal;
      Thread.CurrentThread.CurrentCulture = culture;

      Console.WriteLine("Two Digit Year Range: {0} - {1}", 
                        cal.TwoDigitYearMax - 99, cal.TwoDigitYearMax);
      Console.WriteLine("{0:d}", DateTime.ParseExact(value, fmt, null));
   }
}
// The example displays the following output:
//       Two Digit Year Range: 1930 - 2029
//       1/24/1949
//       
//       Two Digit Year Range: 2000 - 2099
//       1/24/2049
```

```vb
Imports System.Globalization
Imports System.Threading

Module Example
   Public Sub Main()
      Dim fmt As String = "dd-MMM-yy"
      Dim value As String = "24-Jan-49"

      Dim cal As Calendar = CType(CultureInfo.CurrentCulture.Calendar.Clone(), Calendar)
      Console.WriteLine("Two Digit Year Range: {0} - {1}", 
                        cal.TwoDigitYearMax - 99, cal.TwoDigitYearMax)

      Console.WriteLine("{0:d}", DateTime.ParseExact(value, fmt, Nothing))
      Console.WriteLine()

      cal.TwoDigitYearMax = 2099
      Dim culture As CultureInfo = CType(CultureInfo.CurrentCulture.Clone(), CultureInfo)
      culture.DateTimeFormat.Calendar = cal
      Thread.CurrentThread.CurrentCulture = culture

      Console.WriteLine("Two Digit Year Range: {0} - {1}", 
                        cal.TwoDigitYearMax - 99, cal.TwoDigitYearMax)
      Console.WriteLine("{0:d}", DateTime.ParseExact(value, fmt, Nothing))
   End Sub
End Module
' The example displays the following output:
'       Two Digit Year Range: 1930 - 2029
'       1/24/1949
'       
'       Two Digit Year Range: 2000 - 2099
'       1/24/2049
```

L'exemple suivant inclut le spécificateur de format personnalisé "yy" dans une chaîne de format personnalisé.

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010
```

## <a name="the-yyy-custom-format-specifier"></a>Spécificateur de format personnalisé "yyy"

Le spécificateur de format personnalisé "yyy" représente l'année avec un minimum de trois chiffres. Si l'année comporte plus de trois chiffres significatifs, ils sont inclus dans la chaîne résultante. Si l'année comporte moins de trois chiffres, le nombre est rempli avec des zéros non significatifs pour produire trois chiffres.

> [!NOTE]
> Pour le calendrier bouddhiste thaïlandais, qui peut comporter des années à cinq chiffres, ce spécificateur de format affiche tous les chiffres significatifs.

L'exemple suivant inclut le spécificateur de format personnalisé "yyy" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010      
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010 
```

## <a name="the-yyyy-custom-format-specifier"></a>Spécificateur de format personnalisé "yyyy"

Le spécificateur de format personnalisé "yyyy" représente l'année avec un minimum de quatre chiffres. Si l'année comporte plus de quatre chiffres significatifs, ils sont inclus dans la chaîne résultante. Si l'année comporte moins de quatre chiffres, le nombre est rempli à l'aide de zéros non significatifs pour produire quatre chiffres.

> [!NOTE]
> Pour le calendrier bouddhiste thaïlandais, qui peut comporter des années à cinq chiffres, ce spécificateur de format affiche tous les chiffres significatifs.

L'exemple suivant inclut le spécificateur de format personnalisé "yyyy" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010 
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010
```

## <a name="the-yyyyy-custom-format-specifier"></a>Spécificateur de format personnalisé "yyyyy"

Le spécificateur de format personnalisé "yyyyy" (plus tout nombre de spécificateurs "y" supplémentaires) représente l'année avec au minimum cinq chiffres. Si l'année comporte plus de cinq chiffres significatifs, ils sont inclus dans la chaîne résultante. Si l'année comporte moins de cinq chiffres, le nombre est rempli avec des zéros non significatifs pour produire cinq chiffres.

S'il existe des spécificateurs "y" supplémentaires, le nombre est rempli avec autant de zéros non significatifs que nécessaire pour produire le nombre de spécificateurs "y". 

L'exemple suivant inclut le spécificateur de format personnalisé "yyyyy" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010 
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010 
```

## <a name="the-z-custom-format-specifier"></a>Spécificateur de format personnalisé "z"

Avec les valeurs [DateTime](xref:System.DateTime), le spécificateur de format personnalisé "z" représente l’offset signé du fuseau horaire du système d’exploitation local par rapport à l’heure UTC (Coordinated Universal Time, temps universel coordonné), mesurée en heures. Il ne reflète pas la valeur de la propriété [DateTime.Kind](xref:System.DateTime.Kind) d’une instance. C’est pourquoi il n’est pas recommandé d’utiliser le spécificateur de format "z" avec les valeurs [DateTime](xref:System.DateTime).

Avec les valeurs [DateTimeOffset](xref:System.DateTimeOffset), ce spécificateur de format représente l’offset de la valeur [DateTimeOffset](xref:System.DateTimeOffset) par rapport à l’heure UTC, en heures. 

L'offset est toujours affiché avec un signe de début. Un signe plus (+) indique les heures avant l'heure UTC, et un signe moins (-) indique les heures après l'heure UTC. Un offset à un seul chiffre est mis en forme sans zéro non significatif. 

Si le spécificateur de format "z" est utilisé sans autre spécificateur de format personnalisé, il est interprété comme un spécificateur de format de date et d’heure standard et lève un [FormatException](xref:System.FormatException). Pour plus d’informations sur l’utilisation d’un spécificateur de format unique, consultez [Utilisation de spécificateurs de format personnalisés uniques](#using-single-custom-format-specifiers), plus loin dans cette rubrique. 

L'exemple suivant inclut le spécificateur de format personnalisé "z" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = DateTime.UtcNow;
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date1));
// Displays -7, -07, -07:00                     

DateTimeOffset date2 = new DateTimeOffset(2008, 8, 1, 0, 0, 0, 
                                          new TimeSpan(6, 0, 0));
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date2));
// Displays +6, +06, +06:00
```

```vb
Dim date1 As Date = Date.UtcNow
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date1))
' Displays -7, -07, -07:00                     

Dim date2 As New DateTimeOffset(2008, 8, 1, 0, 0, 0, _
                                New Timespan(6, 0, 0))
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date2))                                     
' Displays +6, +06, +06:00
```

## <a name="the-zz-custom-format-specifier"></a>Spécificateur de format personnalisé "zz"

Avec les valeurs [DateTime](xref:System.DateTime), le spécificateur de format personnalisé "zz" représente l’offset signé du fuseau horaire du système d’exploitation local par rapport à l’heure UTC (Coordinated Universal Time, temps universel coordonné), mesurée en heures. Il ne reflète pas la valeur de la propriété [DateTime.Kind](xref:System.DateTime.Kind) d’une instance. C’est pourquoi il n’est pas recommandé d’utiliser le spécificateur de format "zz" avec les valeurs [DateTime](xref:System.DateTime).

Avec les valeurs [DateTimeOffset](xref:System.DateTimeOffset), ce spécificateur de format représente l’offset de la valeur [DateTimeOffset](xref:System.DateTimeOffset) par rapport à l’heure UTC, en heures.

L'offset est toujours affiché avec un signe de début. Un signe plus (+) indique les heures avant l'heure UTC, et un signe moins (-) indique les heures après l'heure UTC. Un offset à un seul chiffre est mis en forme avec un zéro non significatif. 

L'exemple suivant inclut le spécificateur de format personnalisé "zz" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = DateTime.UtcNow;
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date1));
// Displays -7, -07, -07:00                     

DateTimeOffset date2 = new DateTimeOffset(2008, 8, 1, 0, 0, 0, 
                                          new TimeSpan(6, 0, 0));
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date2));
// Displays +6, +06, +06:00
```

```vb
Dim date1 As Date = Date.UtcNow
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date1))
' Displays -7, -07, -07:00                     

Dim date2 As New DateTimeOffset(2008, 8, 1, 0, 0, 0, _
                                New Timespan(6, 0, 0))
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date2))                                     
' Displays +6, +06, +06:00
```

## <a name="the-zzz-custom-format-specifier"></a>Spécificateur de format personnalisé "zzz"

Avec les valeurs [DateTime](xref:System.DateTime), le spécificateur de format personnalisé "zzz" représente l’offset signé du fuseau horaire du système d’exploitation local par rapport à l’heure UTC (Coordinated Universal Time, temps universel coordonné), mesurée en heures. Il ne reflète pas la valeur de la propriété [DateTime.Kind](xref:System.DateTime.Kind) d’une instance. C’est pourquoi il n’est pas recommandé d’utiliser le spécificateur de format "zzz" avec les valeurs [DateTime](xref:System.DateTime).

Avec les valeurs [DateTimeOffset](xref:System.DateTimeOffset), ce spécificateur de format représente l’offset de la valeur [DateTimeOffset](xref:System.DateTimeOffset) par rapport à l’heure UTC, en heures.

L'offset est toujours affiché avec un signe de début. Un signe plus (+) indique les heures avant l'heure UTC, et un signe moins (-) indique les heures après l'heure UTC. Un offset à un seul chiffre est mis en forme avec un zéro non significatif. 

L'exemple suivant inclut le spécificateur de format personnalisé "zzz" dans une chaîne de format personnalisée.

```csharp
DateTime date1 = DateTime.UtcNow;
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date1));
// Displays -7, -07, -07:00                     

DateTimeOffset date2 = new DateTimeOffset(2008, 8, 1, 0, 0, 0, 
                                          new TimeSpan(6, 0, 0));
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date2));
// Displays +6, +06, +06:00
```

```vb
Dim date1 As Date = Date.UtcNow
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date1))
' Displays -7, -07, -07:00                     

Dim date2 As New DateTimeOffset(2008, 8, 1, 0, 0, 0, _
                                New Timespan(6, 0, 0))
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date2))                                     
' Displays +6, +06, +06:00
```

## <a name="the--custom-format-specifier"></a>Spécificateur de format personnalisé ":"

Le spécificateur de format personnalisé ":" représente le séparateur d'heure, lequel est utilisé pour différencier les heures, les minutes et les secondes. 

Si le spécificateur de format ":" est utilisé sans autre spécificateur de format personnalisé, il est interprété comme un spécificateur de format de date et d’heure standard et lève un [FormatException](xref:System.FormatException). Pour plus d’informations sur l’utilisation d’un spécificateur de format unique, consultez [Utilisation de spécificateurs de format personnalisés uniques](#using-single-custom-format-specifiers), plus loin dans cette rubrique.

## <a name="the--custom-format-specifier"></a>Spécificateur de format personnalisé "/"

Le spécificateur de format personnalisé "/" représente le séparateur de date, lequel est utilisé pour différencier les années, les mois et les jours. 

Si le spécificateur de format "/" est utilisé sans autre spécificateur de format personnalisé, il est interprété comme un spécificateur de format de date et d’heure standard et lève un [FormatException](xref:System.FormatException). Pour plus d’informations sur l’utilisation d’un spécificateur de format unique, consultez [Utilisation de spécificateurs de format personnalisés uniques](#using-single-custom-format-specifiers), plus loin dans cette rubrique.

## <a name="character-literals"></a>Littéraux de caractère

Les caractères suivants dans une chaîne de format de date et d’heure standard ou personnalisée sont réservés et sont toujours interprétés comme des caractères de mise en forme ou, dans le cas de ", ', / et \, comme des caractères spéciaux. 

  |   |   |   |      
- | - | - | - | -
F | H | K | M | d
f | g | h | m | s
o | o | e | % | :
/ | " | ' | \ |
  |   |   |   |
  
Tous les autres caractères sont toujours interprétés comme des caractères littéraux et, dans une opération de mise en forme, sont inclus inchangés dans la chaîne de résultat. Dans une opération d’analyse, ils doivent correspondre exactement aux caractères présents dans la chaîne d’entrée. La comparaison respecte la casse. 

L’exemple suivant inclut les caractères littéraux « PST » (pour Pacific Standard Time, heure normale du Pacifique) et « PDT » (pour Pacific Daylight Time, heure d’été du Pacifique) pour représenter le fuseau horaire local dans une chaîne de format. Notez que la chaîne est incluse dans la chaîne de résultat, et qu’une chaîne qui inclut la chaîne du fuseau horaire local est également analysée avec succès. 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      String[] formats = { "dd MMM yyyy hh:mm tt PST", 
                           "dd MMM yyyy hh:mm tt PDT" };
      var dat = new DateTime(2016, 8, 18, 16, 50, 0);
      // Display the result string. 
      Console.WriteLine(dat.ToString(formats[1]));

      // Parse a string. 
      String value = "25 Dec 2016 12:00 pm PST";
      DateTime newDate;
      if (DateTime.TryParseExact(value, formats, null, 
                                 DateTimeStyles.None, out newDate)) 
         Console.WriteLine(newDate);
      else
         Console.WriteLine("Unable to parse '{0}'", value);
   }
}
// The example displays the following output:
//       18 Aug 2016 04:50 PM PDT
//       12/25/2016 12:00:00 PM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim formats() As String = { "dd MMM yyyy hh:mm tt PST", 
                                  "dd MMM yyyy hh:mm tt PDT" }
      Dim dat As New Date(2016, 8, 18, 16, 50, 0)
      ' Display the result string. 
      Console.WriteLine(dat.ToString(formats(1)))

      ' Parse a string. 
      Dim value As String = "25 Dec 2016 12:00 pm PST"
      Dim newDate As Date
      If Date.TryParseExact(value, formats, Nothing, 
                            DateTimeStyles.None, newDate) Then 
         Console.WriteLine(newDate)
      Else
         Console.WriteLine("Unable to parse '{0}'", value)
      End If                               
   End Sub
End Module
' The example displays the following output:
'       18 Aug 2016 04:50 PM PDT
'       12/25/2016 12:00:00 PM
```

Il existe deux façons d’indiquer que les caractères doivent être interprétés comme des caractères littéraux, et non comme des caractères réservés, pour qu’ils puissent être inclus dans une chaîne de résultat ou analysés correctement dans une chaîne d’entrée :

* En plaçant chaque caractère réservé dans une séquence d’échappement. Pour plus d’informations, consultez [Utilisation du caractère d’échappement](#using-the-escape-character). 
  
  L’exemple suivant inclut les caractères littéraux « pst » (pour Pacific Standard Time, heure normale du Pacifique) pour représenter le fuseau horaire local dans une chaîne de format. Étant donné que « s » et « t » sont des chaînes de format personnalisées, les deux caractères doivent être placés dans des séquences d’échappement pour être interprétés comme des littéraux de caractères. 
  
```csharp
using System;
using System.Globalization;

public class Example
{
  public static void Main()
  {
      String format = "dd MMM yyyy hh:mm tt p\\s\\t";
      var dat = new DateTime(2016, 8, 18, 16, 50, 0);
      // Display the result string. 
      Console.WriteLine(dat.ToString(format));

      // Parse a string. 
      String value = "25 Dec 2016 12:00 pm pst";
      DateTime newDate;
      if (DateTime.TryParseExact(value, format, null, 
                                  DateTimeStyles.None, out newDate)) 
          Console.WriteLine(newDate);
      else
          Console.WriteLine("Unable to parse '{0}'", value);
  }
}
// The example displays the following output:
//       18 Aug 2016 04:50 PM PDT
//       12/25/2016 12:00:00 PM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim fmt As String = "dd MMM yyyy hh:mm tt p\s\t" 
      Dim dat As New Date(2016, 8, 18, 16, 50, 0)
      ' Display the result string. 
      Console.WriteLine(dat.ToString(fmt))

      ' Parse a string. 
      Dim value As String = "25 Dec 2016 12:00 pm pst"
      Dim newDate As Date
      If Date.TryParseExact(value, fmt, Nothing, 
                            DateTimeStyles.None, newDate) Then 
         Console.WriteLine(newDate)
      Else
         Console.WriteLine("Unable to parse '{0}'", value)
      End If                               
   End Sub
End Module
' The example displays the following output:
'       18 Aug 2016 04:50 PM pst
'       12/25/2016 12:00:00 PM
```
  
* En plaçant la totalité de la chaîne littérale entre guillemets ou apostrophes. L’exemple suivant est semblable au précédent, excepté que « pst » est placé entre guillemets pour indiquer que la totalité de la chaîne délimitée doit être interprétée comme des littéraux de caractères. 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      String format = "dd MMM yyyy hh:mm tt \"pst\"";
      var dat = new DateTime(2016, 8, 18, 16, 50, 0);
      // Display the result string. 
      Console.WriteLine(dat.ToString(format));

      // Parse a string. 
      String value = "25 Dec 2016 12:00 pm pst";
      DateTime newDate;
      if (DateTime.TryParseExact(value, format, null, 
                                 DateTimeStyles.None, out newDate)) 
         Console.WriteLine(newDate);
      else
         Console.WriteLine("Unable to parse '{0}'", value);
   }
}
// The example displays the following output:
//       18 Aug 2016 04:50 PM PDT
//       12/25/2016 12:00:00 PM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim fmt As String = "dd MMM yyyy hh:mm tt ""pst"""  
      Dim dat As New Date(2016, 8, 18, 16, 50, 0)
      ' Display the result string. 
      Console.WriteLine(dat.ToString(fmt))

      ' Parse a string. 
      Dim value As String = "25 Dec 2016 12:00 pm pst"
      Dim newDate As Date
      If Date.TryParseExact(value, fmt, Nothing, 
                            DateTimeStyles.None, newDate) Then 
         Console.WriteLine(newDate)
      Else
         Console.WriteLine("Unable to parse '{0}'", value)
      End If                               
   End Sub
End Module
' The example displays the following output:
'       18 Aug 2016 04:50 PM pst
'       12/25/2016 12:00:00 PM
```

## <a name="notes"></a>Notes


### <a name="using-single-custom-format-specifiers"></a>Utilisation de spécificateurs de format personnalisés uniques

Une chaîne de format de date et d'heure personnalisée se compose d'au moins deux caractères. Les méthodes de mise en forme de la date et de l'heure interprètent toute chaîne à un caractère comme une chaîne de format de date et d'heure standard. Si elles ne reconnaissent pas le caractère comme un spécificateur de format valide, elles lèvent un [FormatException](xref:System.FormatException). Par exemple, une chaîne de format qui se compose uniquement du spécificateur "h" est interprétée comme une chaîne de format de date et d'heure standard. Toutefois, dans ce cas particulier, une exception est levée, car il n’existe aucun spécificateur de format de date et d’heure standard "h". 

Pour utiliser tout spécificateur de format de date et d'heure personnalisé comme seul spécificateur dans une chaîne de format (autrement dit, utiliser le spécificateur de format personnalisé "d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":" ou "/" tout seul), incluez un espace avant ou après le spécificateur, ou incluez un spécificateur de format pourcentage ("%") avant le spécificateur de date et d'heure personnalisé unique.

Par exemple, "`%h`" est interprété comme chaîne de format de date et d’heure personnalisée qui affiche l’heure représentée par la valeur de date et d’heure actuelle. Vous pouvez également utiliser la chaîne de format "h" ou "h", bien que cela inclue un espace avec l'heure dans la chaîne de résultat. L'exemple suivant illustre ces trois chaînes de format.


```csharp
DateTime dat1 = new DateTime(2009, 6, 15, 13, 45, 0);

Console.WriteLine("'{0:%h}'", dat1);
Console.WriteLine("'{0: h}'", dat1);
Console.WriteLine("'{0:h }'", dat1);
// The example displays the following output:
//       '1'
//       ' 1'
//       '1 '
```

```vb
Dim dat1 As Date = #6/15/2009 1:45PM#

Console.WriteLine("'{0:%h}'", dat1)
Console.WriteLine("'{0: h}'", dat1)
Console.WriteLine("'{0:h }'", dat1)
' The example displays the following output:
'       '1'
'       ' 1'
'       '1 '
```

### <a name="using-the-escape-character"></a>Utilisation du caractère d’échappement

Les caractères "d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":" ou "/" dans une chaîne de format sont interprétés comme des spécificateurs de format personnalisés plutôt que comme des caractères littéraux. Pour éviter qu’un caractère soit interprété comme un spécificateur de format, vous pouvez le faire précéder d’une barre oblique inverse (\), qui est le caractère d’échappement. Le caractère d'échappement signifie que le caractère suivant est un caractère littéral qui doit être inclus inchangé dans la chaîne de résultat.

Pour inclure une barre oblique inverse dans une chaîne de résultat, vous devez la placer dans une séquence d'échappement avec une autre barre oblique inverse (`\\`).

> [!NOTE]
> Certains compilateurs, tels que le compilateur C#, peuvent également interpréter une barre oblique inverse unique comme un caractère d’échappement. Pour garantir l’interprétation correcte d’une chaîne lors de la mise en forme, vous pouvez utiliser le caractère littéral de chaîne textuelle (le caractère @) avant la chaîne, ou ajouter une autre barre oblique inverse avant chaque barre oblique inverse. L'exemple C# suivant illustre ces deux approches.

L'exemple suivant utilise le caractère d'échappement pour empêcher l'opération de mise en forme d'interpréter les caractères "h" et "m" comme des spécificateurs de format. 

```csharp
DateTime date = new DateTime(2009, 06, 15, 13, 45, 30, 90);
string fmt1 = "h \\h m \\m";
string fmt2 = @"h \h m \m";

Console.WriteLine("{0} ({1}) -> {2}", date, fmt1, date.ToString(fmt1));
Console.WriteLine("{0} ({1}) -> {2}", date, fmt2, date.ToString(fmt2));
// The example displays the following output:
//       6/15/2009 1:45:30 PM (h \h m \m) -> 1 h 45 m
//       6/15/2009 1:45:30 PM (h \h m \m) -> 1 h 45 m
```

```vb
Dim date1 As Date = #6/15/2009 13:45#
Dim fmt As String = "h \h m \m"

Console.WriteLine("{0} ({1}) -> {2}", date1, fmt, date1.ToString(fmt))
' The example displays the following output:
'       6/15/2009 1:45:00 PM (h \h m \m) -> 1 h 45 m 
```

### <a name="datetimeformatinfo-properties"></a>Propriétés DateTimeFormatInfo

La mise en forme dépend des propriétés de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) actif, qui est fourni implicitement par la culture de thread actuelle ou explicitement par le paramètre [IFormatProvider](xref:System.IFormatProvider) de la méthode qui appelle la mise en forme. Pour le paramètre [IFormatProvider](xref:System.IFormatProvider), vous devez spécifier un objet [CultureInfo](xref:System.Globalization.CultureInfo) qui représente une culture, ou un objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo). 

La chaîne de résultat produite par la plupart des spécificateurs de format de date et d’heure personnalisés dépend également des propriétés de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) actif. Votre application peut modifier le résultat produit par certains spécificateurs de format de date et d’heure personnalisés en modifiant la propriété [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) correspondante. Par exemple, le spécificateur de format "ddd" ajoute à la chaîne de résultat le nom abrégé d’un jour de la semaine trouvé dans le tableau de chaînes [AbbreviatedDayNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames). De la même façon, le spécificateur de format "MMMM" ajoute à la chaîne de résultat un nom de mois complet trouvé dans le tableau de chaînes [MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames).

## <a name="see-also"></a>Voir aussi

[System.DateTime](xref:System.DateTime)

[System.IFormatProvider](xref:System.IFormatProvider)

[Mise en forme des types](formatting-types.md)

[Chaînes de format de date et d’heure standard](standard-datetime.md)


