---
title: "Instanciation d’un objet DateTimeOffset"
description: "Instanciation d’un objet DateTimeOffset"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 476fe67b-6be4-4435-88ab-ced37304f1d1
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 26be324eb5d58b94a71e89aba213f107cf8dfd1e
ms.lasthandoff: 03/02/2017

---

# <a name="instantiating-a-datetimeoffset-object"></a>Instanciation d’un objet DateTimeOffset

La structure [System.DateTimeOffset](xref:System.DateTimeOffset) offre plusieurs façons de créer de nouvelles valeurs [DateTimeOffset](xref:System.DateTimeOffset). La plupart d’entre elles correspondent directement aux méthodes disponibles pour instancier de nouvelles valeurs [System.DateTime](xref:System.DateTime), avec des améliorations qui vous permettent de spécifier le décalage de la valeur de date et d’heure par rapport au temps universel coordonné (UTC). En particulier, vous pouvez instancier une valeur [DateTimeOffset](xref:System.DateTimeOffset) comme suit :

* En appelant un constructeur [DateTimeOffset](xref:System.DateTimeOffset).

* En convertissant implicitement une valeur en valeur [DateTimeOffset](xref:System.DateTimeOffset).

* En analysant la représentation sous forme de chaîne d’une date et d’une heure.

## <a name="date-and-time-literals"></a>Littéraux de date et d’heure

Pour les langages qui la prennent en charge, l’une des façons les plus courantes d’instancier une valeur [DateTime](xref:System.DateTime) consiste à fournir la date et l’heure sous la forme d’une valeur littérale codée en dur. Par exemple, le code Visual Basic suivant crée un objet [DateTime](xref:System.DateTime) dont la valeur est le 1er janvier 2008 à 10:00.

```vb
Dim literalDate1 As Date = #05/01/2008 8:06:32 AM#
Console.WriteLine(literalDate1.ToString())
' Displays:
'              5/1/2008 8:06:32 AM
```

Les valeurs [DateTimeOffset](xref:System.DateTimeOffset) peuvent également être initialisées à l’aide de littéraux de date et d’heure lors de l’utilisation de langages qui prennent en charge les littéraux [DateTime](xref:System.DateTime). Par exemple, le code Visual Basic suivant crée un objet [DateTimeOffset](xref:System.DateTimeOffset).

```vb
Dim literalDate As DateTimeOffset = #05/01/2008 8:06:32 AM#
Console.WriteLine(literalDate.ToString())
' Displays:
'              5/1/2008 8:06:32 AM -07:00
```

Comme le montre la sortie de la console, la valeur [DateTimeOffset](xref:System.DateTimeOffset) créée de cette façon se voit assigner le décalage du fuseau horaire local. Cela signifie qu’une valeur [DateTimeOffset](xref:System.DateTimeOffset) affectée à l’aide d’un littéral de caractère n’identifie pas un point unique dans le temps si le code est exécuté sur des ordinateurs différents.

## <a name="datetimeoffset-constructors"></a>Constructeurs DateTimeOffset

Le type [System.DateTimeOffset](xref:System.DateTimeOffset) définit cinq constructeurs. Trois d’entre eux correspondent directement aux constructeurs [DateTime](xref:System.DateTime), avec un paramètre supplémentaire du type [System.TimeSpan](xref:System.TimeSpan) qui définit le décalage de date et d’heure par rapport à l’heure UTC. Ils vous permettent de définir une valeur [DateTimeOffset](xref:System.DateTimeOffset) basée sur la valeur de ses composants individuels de date et d’heure. Par exemple, le code suivant utilise ces trois constructeurs pour instancier les objets [DateTimeOffset](xref:System.DateTimeOffset) avec des valeurs identiques de 7/1/2008 12:05 AM + 01:00.

```csharp
DateTimeOffset dateAndTime;

// Instantiate date and time using years, months, days, 
// hours, minutes, and seconds
dateAndTime = new DateTimeOffset(2008, 5, 1, 8, 6, 32, 
                                 new TimeSpan(1, 0, 0));
Console.WriteLine(dateAndTime);
// Instantiate date and time using years, months, days,
// hours, minutes, seconds, and milliseconds
dateAndTime = new DateTimeOffset(2008, 5, 1, 8, 6, 32, 545, 
                                 new TimeSpan(1, 0, 0));
Console.WriteLine("{0} {1}", dateAndTime.ToString("G"), 
                             dateAndTime.ToString("zzz"));

// Instantiate date and time using number of ticks
// 05/01/2008 8:06:32 AM is 633,452,259,920,000,000 ticks
dateAndTime = new DateTimeOffset(633452259920000000, new TimeSpan(1, 0, 0));  
Console.WriteLine(dateAndTime);
// The example displays the following output to the console:
//       5/1/2008 8:06:32 AM +01:00
//       5/1/2008 8:06:32 AM +01:00
//       5/1/2008 8:06:32 AM +01:00
```

```vb
Dim dateAndTime As DateTimeOffset

' Instantiate date and time using years, months, days, 
' hours, minutes, and seconds
dateAndTime = New DateTimeOffset(2008, 5, 1, 8, 6, 32, _
                                 New TimeSpan(1, 0, 0))
Console.WriteLine(dateAndTime)
' Instantiate date and time using years, months, days,
' hours, minutes, seconds, and milliseconds
dateAndTime = New DateTimeOffset(2008, 5, 1, 8, 6, 32, 545, _
                                 New TimeSpan(1, 0, 0))
Console.WriteLine("{0} {1}", dateAndTime.ToString("G"), _
                             dateAndTime.ToString("zzz"))

' Instantiate date and time using Persian calendar with years,
' months, days, hours, minutes, seconds, and milliseconds
dateAndTime = New DateTimeOffset(1387, 2, 12, 8, 6, 32, 545, New PersianCalendar, New TimeSpan(1, 0, 0))
' Note that the console output displays the date in the Gregorian
' calendar, not the Persian calendar. 
Console.WriteLine("{0} {1}", dateAndTime.ToString("G"), _
                             dateAndTime.ToString("zzz"))

' Instantiate date and time using number of ticks
' 05/01/2008 8:06:32 AM is 633,452,259,920,000,000 ticks
dateAndTime = New DateTimeOffset(633452259920000000, New TimeSpan(1, 0, 0))  
Console.WriteLine(dateAndTime)
' The example displays the following output to the console:
'       5/1/2008 8:06:32 AM +01:00
'       5/1/2008 8:06:32 AM +01:00
'       5/1/2008 8:06:32 AM +01:00
'       5/1/2008 8:06:32 AM +01:00
```

Notez que, lorsque la valeur de l’objet [DateTimeOffset](xref:System.DateTimeOffset) instancié à l’aide d’un objet [PersianCalendar](xref:System.Globalization.PersianCalendar) comme l’un des arguments de son constructeur est affichée dans la console, elle est exprimée sous la forme d’une date du calendrier grégorien plutôt que du calendrier persan. 

Les deux autres constructeurs créent un objet [DateTimeOffset](xref:System.DateTimeOffset) à partir d’une valeur DateTime. Le premier d’entre eux a un seul paramètre, la valeur [DateTime](xref:System.DateTime) à convertir en valeur [DateTimeOffset](xref:System.DateTimeOffset). Le décalage de la valeur [DateTimeOffset](xref:System.DateTimeOffset) obtenue dépend de la propriété [Kind](xref:System.DateTime.Kind) de l’unique paramètre [DateTime](xref:System.DateTime) du constructeur. Si sa valeur est [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), le décalage est défini sur [TimeSpan.Zero](xref:System.TimeSpan.Zero). Sinon, son décalage est défini comme égal à celui du fuseau horaire local. L’exemple suivant illustre l’utilisation de ce constructeur pour instancier des objets [DateTimeOffset](xref:System.DateTimeOffset) qui représentent l’heure UTC et le fuseau horaire local :

```csharp
// Declare date; Kind property is DateTimeKind.Unspecified
DateTime sourceDate = new DateTime(2008, 5, 1, 8, 30, 0);
DateTimeOffset targetTime;

// Instantiate a DateTimeOffset value from a UTC time 
DateTime utcTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Utc);
targetTime = new DateTimeOffset(utcTime);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM +00:00
// Because the Kind property is DateTimeKind.Utc, 
// the offset is TimeSpan.Zero.

// Instantiate a DateTimeOffset value from a UTC time with a zero offset
targetTime = new DateTimeOffset(utcTime, TimeSpan.Zero);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM +00:00
// Because the Kind property is DateTimeKind.Utc, 
// the call to the constructor succeeds

// Instantiate a DateTimeOffset value from a UTC time with a negative offset
try
{
   targetTime = new DateTimeOffset(utcTime, new TimeSpan(-2, 0, 0));
   Console.WriteLine(targetTime);
}
catch (ArgumentException)
{
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", 
                      targetTime);
}   
// Throws exception and displays the following to the console:
//   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM +00:00 failed.

// Instantiate a DateTimeOffset value from a local time
DateTime localTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Local);
targetTime = new DateTimeOffset(localTime);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM -07:00
// Because the Kind property is DateTimeKind.Local, 
// the offset is that of the local time zone.

// Instantiate a DateTimeOffset value from an unspecified time
targetTime = new DateTimeOffset(sourceDate);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM -07:00
// Because the Kind property is DateTimeKind.Unspecified, 
// the offset is that of the local time zone.
```

```vb
' Declare date; Kind property is DateTimeKind.Unspecified
Dim sourceDate As Date = #5/1/2008 8:30 AM#
Dim targetTime As DateTimeOffset

' Instantiate a DateTimeOffset value from a UTC time 
Dim utcTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Utc)
targetTime = New DateTimeOffset(utcTime)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM +00:00
' Because the Kind property is DateTimeKind.Utc, 
' the offset is TimeSpan.Zero.


' Instantiate a DateTimeOffset value from a local time
Dim localTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Local)
targetTime = New DateTimeOffset(localTime)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM -07:00
' Because the Kind property is DateTimeKind.Local, 
' the offset is that of the local time zone.

' Instantiate a DateTimeOffset value from an unspecified time
targetTime = New DateTimeOffset(sourceDate)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM -07:00
' Because the Kind property is DateTimeKind.Unspecified, 
' the offset is that of the local time zone.
```

> [!NOTE]
> Appeler la surcharge du constructeur [DateTimeOffset](xref:System.DateTimeOffset) qui a un seul paramètre [DateTime](xref:System.DateTime) équivaut à effectuer une conversion implicite d’une valeur [DateTime](xref:System.DateTime) en une valeur [DateTimeOffset](xref:System.DateTimeOffset).

Le deuxième constructeur qui crée un objet [DateTimeOffset](xref:System.DateTimeOffset) à partir d’une valeur [DateTime](xref:System.DateTime) possède deux paramètres : la valeur [DateTime](xref:System.DateTime) à convertir et une valeur [TimeSpan](xref:System.TimeSpan) représentant le décalage de date et d’heure par rapport à l’heure UTC. Cette valeur de décalage doit correspondre à la propriété [Kind](xref:System.DateTime.Kind) du premier paramètre du constructeur ou une exception [System.ArgumentException](xref:System.ArgumentException) est levée. Si la propriété [Kind](xref:System.DateTime.Kind) du premier paramètre est [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), la valeur du deuxième paramètre doit être [TimeSpan.Zero](xref:System.TimeSpan.Zero). Si la propriété [Kind](xref:System.DateTime.Kind) du premier paramètre est [DateTimeKind.Local](xref:System.DateTimeKind.Local), la valeur du deuxième paramètre doit correspondre au décalage du fuseau horaire du système local. Si la propriété [Kind](xref:System.DateTime.Kind) du premier paramètre est [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), le décalage peut être égal à n’importe quelle valeur valide. Le code suivant illustre les appels à ce constructeur pour convertir des valeurs [DateTime](xref:System.DateTime) en valeurs [DateTimeOffset](xref:System.DateTimeOffset).

```csharp
DateTime sourceDate = new DateTime(2008, 5, 1, 8, 30, 0);
DateTimeOffset targetTime;

// Instantiate a DateTimeOffset value from a UTC time with a zero offset.
DateTime utcTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Utc);
targetTime = new DateTimeOffset(utcTime, TimeSpan.Zero);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM +00:00
// Because the Kind property is DateTimeKind.Utc,  
// the call to the constructor succeeds

// Instantiate a DateTimeOffset value from a UTC time with a non-zero offset.
try
{
   targetTime = new DateTimeOffset(utcTime, new TimeSpan(-2, 0, 0));
   Console.WriteLine(targetTime);
}
catch (ArgumentException)
{
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", 
                      utcTime);
}   
// Throws exception and displays the following to the console:
//   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM failed.

// Instantiate a DateTimeOffset value from a local time with 
// the offset of the local time zone
DateTime localTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Local);
targetTime = new DateTimeOffset(localTime, 
                                TimeZoneInfo.Local.GetUtcOffset(localTime));
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM -07:00
// Because the Kind property is DateTimeKind.Local and the offset matches
// that of the local time zone, the call to the constructor succeeds.

// Instantiate a DateTimeOffset value from a local time with a zero offset.
try
{
   targetTime = new DateTimeOffset(localTime, TimeSpan.Zero);
   Console.WriteLine(targetTime);
}
catch (ArgumentException)
{
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", 
                      localTime);
}   
// Throws exception and displays the following to the console:
//   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM failed.

// Instantiate a DateTimeOffset value with an arbitary time zone. 
string timeZoneName = "Central Standard Time";
TimeSpan offset = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName). 
                         GetUtcOffset(sourceDate); 
targetTime = new DateTimeOffset(sourceDate, offset);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM -05:00
```

```vb
Dim sourceDate As Date = #5/1/2008 8:30 AM#
Dim targetTime As DateTimeOffset

' Instantiate a DateTimeOffset value from a UTC time with a zero offset.
Dim utcTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Utc)
targetTime = New DateTimeOffset(utcTime, TimeSpan.Zero)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM +00:00
' Because the Kind property is DateTimeKind.Utc,  
' the call to the constructor succeeds.

' Instantiate a DateTimeOffset value from a UTC time with a non-zero offset.
Try
   targetTime = New DateTimeOffset(utcTime, New TimeSpan(-2, 0, 0))
   Console.WriteLine(targetTime)
Catch e As ArgumentException
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", _
                      utcTime)
End Try   
' Throws exception and displays the following to the console:
'   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM failed.

' Instantiate a DateTimeOffset value from a local time with 
' the offset of the local time zone.
Dim localTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Local)
targetTime = New DateTimeOffset(localTime, _
                                TimeZoneInfo.Local.GetUtcOffset(localTime))
Console.WriteLine(targetTime)
' Because the Kind property is DateTimeKind.Local and the offset matches
' that of the local time zone, the call to the constructor succeeds.

' Instantiate a DateTimeOffset value from a local time with a zero offset.
Try
   targetTime = New DateTimeOffset(localTime, TimeSpan.Zero)
   Console.WriteLine(targetTime)
Catch e As ArgumentException
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", _
                      localTime)
End Try   
' Throws exception and displays the following to the console:
'   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM failed.

' Instantiate a DateTimeOffset value with an arbitary time zone. 
Dim timeZoneName As String = "Central Standard Time"
Dim offset As TimeSpan = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName). _
                         GetUtcOffset(sourceDate) 
targetTime = New DateTimeOffset(sourceDate, offset)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM -05:00
```

## <a name="implicit-type-conversion"></a>Conversion de type implicite
 
Le type [System.DateTimeOffset](xref:System.DateTimeOffset) prend en charge une conversion de type implicite : d’une valeur [System.DateTime](xref:System.DateTime) vers une valeur [DateTimeOffset](xref:System.DateTimeOffset). (Une conversion de type implicite est une conversion d’un type vers un autre qui ne nécessite pas de cast explicite (en C#) ni de conversion (en Visual Basic), et qui ne perd pas d’informations. Elle permet d’utiliser un code similaire au suivant.)

```csharp
DateTimeOffset targetTime;

// The Kind property of sourceDate is DateTimeKind.Unspecified
DateTime sourceDate = new DateTime(2008, 5, 1, 8, 30, 0);
targetTime = sourceDate;
Console.WriteLine(targetTime);   
// Displays 5/1/2008 8:30:00 AM -07:00

// define a UTC time (Kind property is DateTimeKind.Utc)
DateTime utcTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Utc);
targetTime = utcTime;
Console.WriteLine(targetTime);   
// Displays 5/1/2008 8:30:00 AM +00:00

// Define a local time (Kind property is DateTimeKind.Local)
DateTime localTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Local);
targetTime = localTime;
Console.WriteLine(targetTime);      
// Displays 5/1/2008 8:30:00 AM -07:00
```

```vb
Dim targetTime As DateTimeOffset

' The Kind property of sourceDate is DateTimeKind.Unspecified
Dim sourceDate As Date = #5/1/2008 8:30 AM#
targetTime = sourceDate
Console.WriteLine(targetTime)   
' Displays 5/1/2008 8:30:00 AM -07:00

' define a UTC time (Kind property is DateTimeKind.Utc)
Dim utcTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Utc)
targetTime = utcTime
Console.WriteLine(targetTime)   
' Displays 5/1/2008 8:30:00 AM +00:00

' Define a local time (Kind property is DateTimeKind.Local)
Dim localTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Local)
targetTime = localTime
Console.WriteLine(targetTime)      
' Displays 5/1/2008 8:30:00 AM -07:00
```

Le décalage de la valeur [DateTimeOffset](xref:System.DateTimeOffset) obtenue dépend de la valeur de la propriété DateTime.Kind](xref:System.DateTime.Kind). Si sa valeur est [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), le décalage est défini sur [TimeSpan.Zero](xref:System.TimeSpan.Zero). Si sa valeur est [DateTimeKind.Local](xref:System.DateTimeKind.Local) ou [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), le décalage est défini comme égal à celui du fuseau horaire local.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Analyse de la représentation sous forme de chaîne d’une date et d’une heure

Le type [System.DateTimeOffset](xref:System.DateTimeOffset) prend en charge quatre méthodes qui vous permettent de convertir la représentation sous forme de chaîne d’une date et d’une heure en une valeur [DateTimeOffset](xref:System.DateTimeOffset) :

* [Parse](xref:System.DateTimeOffset.Parse(System.String)), qui essaie de convertir la représentation sous forme de chaîne d’une date et d’une heure en une valeur [DateTimeOffset](xref:System.DateTimeOffset) et lève une exception si la conversion échoue.

* [TryParse](xref:System.DateTimeOffset.TryParse(System.String,System.DateTimeOffset@)), qui essaie de convertir la représentation sous forme de chaîne d’une date et d’une heure en une valeur [DateTimeOffset](xref:System.DateTimeOffset) et retourne `false` si la conversion échoue.

* [ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)), qui essaie de convertir la représentation sous forme de chaîne d’une date et d’une heure dans un format spécifié en une valeur [DateTimeOffset](xref:System.DateTimeOffset). La méthode lève une exception si la conversion échoue.

* [TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)), qui essaie de convertir la représentation sous forme de chaîne d’une date et d’une heure dans un format spécifié en une valeur [DateTimeOffset](xref:System.DateTimeOffset). La méthode retourne `false` si la conversion échoue.

L’exemple suivant illustre des appels à ces quatre méthodes de conversion de chaîne pour instancier une valeur [DateTimeOffset](xref:System.DateTimeOffset).

```csharp
string timeString; 
DateTimeOffset targetTime;

timeString = "05/01/2008 8:30 AM +01:00";
try
{
   targetTime = DateTimeOffset.Parse(timeString);
   Console.WriteLine(targetTime);
}
catch (FormatException)
{
   Console.WriteLine("Unable to parse {0}.", timeString);   
}   

timeString = "05/01/2008 8:30 AM";
if (DateTimeOffset.TryParse(timeString, out targetTime))
   Console.WriteLine(targetTime);
else
   Console.WriteLine("Unable to parse {0}.", timeString);   

timeString = "Thursday, 01 May 2008 08:30";
try
{
   targetTime = DateTimeOffset.ParseExact(timeString, "f", 
                CultureInfo.InvariantCulture);
   Console.WriteLine(targetTime);
}
catch (FormatException)
{
   Console.WriteLine("Unable to parse {0}.", timeString);   
}   

timeString = "Thursday, 01 May 2008 08:30 +02:00";
string formatString; 
formatString = CultureInfo.InvariantCulture.DateTimeFormat.LongDatePattern +
                " " +
                CultureInfo.InvariantCulture.DateTimeFormat.ShortTimePattern +
                " zzz"; 
if (DateTimeOffset.TryParseExact(timeString, 
                                formatString, 
                                CultureInfo.InvariantCulture, 
                                DateTimeStyles.AllowLeadingWhite, 
                                out targetTime))
   Console.WriteLine(targetTime);
else
   Console.WriteLine("Unable to parse {0}.", timeString);
// The example displays the following output to the console:
//    5/1/2008 8:30:00 AM +01:00
//    5/1/2008 8:30:00 AM -07:00
//    5/1/2008 8:30:00 AM -07:00
//    5/1/2008 8:30:00 AM +02:00
```

```vb
Dim timeString As String 
Dim targetTime As DateTimeOffset

timeString = "05/01/2008 8:30 AM +01:00"
Try
   targetTime = DateTimeOffset.Parse(timeString)
   Console.WriteLine(targetTime)
Catch e As FormatException
   Console.WriteLine("Unable to parse {0}.", timeString)   
End Try   

timeString = "05/01/2008 8:30 AM"
If DateTimeOffset.TryParse(timeString, targetTime) Then
   Console.WriteLine(targetTime)
Else
   Console.WriteLine("Unable to parse {0}.", timeString)   
End If

timeString = "Thursday, 01 May 2008 08:30"
Try
   targetTime = DateTimeOffset.ParseExact(timeString, "f", _
                CultureInfo.InvariantCulture)
   Console.WriteLine(targetTime)
Catch e As FormatException
   Console.WriteLine("Unable to parse {0}.", timeString)   
End Try   

timeString = "Thursday, 01 May 2008 08:30 +02:00"
Dim formatString As String 
formatString = CultureInfo.InvariantCulture.DateTimeFormat.LongDatePattern & _
                " " & _
                CultureInfo.InvariantCulture.DateTimeFormat.ShortTimePattern & _
                " zzz" 
If DateTimeOffset.TryParseExact(timeString, _
                                formatString, _
                                CultureInfo.InvariantCulture, _
                                DateTimeStyles.AllowLeadingWhite, _
                                targetTime) Then
   Console.WriteLine(targetTime)
Else
   Console.WriteLine("Unable to parse {0}.", timeString)
End If      
' The example displays the following output to the console:
'    5/1/2008 8:30:00 AM +01:00
'    5/1/2008 8:30:00 AM -07:00
'    5/1/2008 8:30:00 AM -07:00
'    5/1/2008 8:30:00 AM +02:00
```

## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](index.md)


