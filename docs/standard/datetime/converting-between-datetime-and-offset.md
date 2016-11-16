---
title: Conversion entre DateTime et DateTimeOffset
description: Conversion entre DateTime et DateTimeOffset
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: fab3af5b-5d0f-4384-a40a-1b5d99b30dd1
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 312ac8cb7e901c4ceeff2e428620c2c4c615ca3d

---

# <a name="converting-between-datetime-and-datetimeoffset"></a>Conversion entre DateTime et DateTimeOffset

La structure [System.DateTimeOffset](xref:System.DateTimeOffset) fournit un degré supérieur de prise en compte du fuseau horaire que la structure [System.DateTime](xref:System.DateTime), mais les paramètres [DateTime](xref:System.DateTime) sont plus fréquemment utilisés dans les appels de méthode. Pour cette raison, l’aptitude à convertir des valeurs [DateTimeOffset](xref:System.DateTimeOffset) en valeurs [DateTime](xref:System.DateTime) et vice versa est particulièrement importante. Cet article montre comment effectuer ces conversions de façon à conserver autant d’informations de fuseau horaire que possible.

> [!NOTE]
> Les types [DateTime](xref:System.DateTime) et [DateTimeOffset](xref:System.DateTimeOffset) présentent tous les deux certaines restrictions lors de la représentation des heures dans des fuseaux horaires. Avec sa propriété [Kind](xref:System.DateTime.Kind), [DateTime](xref:System.DateTime) peut refléter uniquement le temps universel coordonné (UTC) et le fuseau horaire local du système. [DateTimeOffset](xref:System.DateTimeOffset) reflète un décalage horaire par rapport à l’heure UTC, mais ne reflète pas le fuseau horaire réel auquel ce décalage appartient. Pour plus d’informations sur les valeurs de date/heure et la prise en charge des fuseaux horaires, consultez [Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Conversions de DateTime en DateTimeOffset

La structure [DateTimeOffset](xref:System.DateTimeOffset) fournit deux moyens équivalents de convertir des données [DateTime](xref:System.DateTime) en données [DateTimeOffset](xref:System.DateTimeOffset), qui conviennent à la plupart des conversions :

* Le constructeur [DateTimeOffset(DateTime)](xref:System.DateTimeOffset), qui crée un nouvel objet [DateTimeOffset](xref:System.DateTimeOffset) basé sur une valeur [DateTime](xref:System.DateTime).

* L’opérateur de conversion implicite, qui vous permet d’attribuer une valeur [DateTime](xref:System.DateTime) à un objet [DateTimeOffset](xref:System.DateTimeOffset).

Pour les valeurs [DateTime](xref:System.DateTime) UTC et locales, la propriété [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) de la valeur [DateTimeOffset](xref:System.DateTimeOffset) résultante reflète précisément le décalage du fuseau horaire UTC ou local. Par exemple, le code suivant convertit une heure UTC vers sa valeur [DateTimeOffset](xref:System.DateTimeOffset) équivalente. 

```csharp
DateTime utcTime1 = new DateTime(2008, 6, 19, 7, 0, 0);
utcTime1 = DateTime.SpecifyKind(utcTime1, DateTimeKind.Utc);
DateTimeOffset utcTime2 = utcTime1;
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", 
                  utcTime1, 
                  utcTime1.Kind.ToString(), 
                  utcTime2);
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Utc to a DateTimeOffset value of 6/19/2008 7:00:00 AM +00:00
```

```vb
Dim utcTime1 As Date = Date.SpecifyKind(#06/19/2008 7:00AM#, _
                                        DateTimeKind.Utc)
Dim utcTime2 As DateTimeOffset = utcTime1
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", _
                  utcTime1, _
                  utcTime1.Kind.ToString(), _
                  utcTime2)
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Utc to a DateTimeOffset value of 6/19/2008 7:00:00 AM  +00:00
```

Dans ce cas, le décalage de la variable `utcTime2` est 00:00. De même, le code suivant convertit une heure locale en une valeur [DateTimeOffset](xref:System.DateTimeOffset) équivalente.

```csharp
DateTime localTime1 = new DateTime(2008, 6, 19, 7, 0, 0);
localTime1 = DateTime.SpecifyKind(localTime1, DateTimeKind.Local);
DateTimeOffset localTime2 = localTime1;
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", 
                  localTime1, 
                  localTime1.Kind.ToString(), 
                  localTime2);
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Local to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

```vb
Dim localTime1 As Date = Date.SpecifyKind(#06/19/2008 7:00AM#, DateTimeKind.Local)
Dim localTime2 As DateTimeOffset = localTime1
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", _
                  localTime1, _
                  localTime1.Kind.ToString(), _
                  localTime2)
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Local to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

Toutefois, pour les valeurs [DateTime](xref:System.DateTime) dont la propriété [Kind](xref:System.DateTime.Kind) est [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), ces deux méthodes de conversion produisent une valeur [DateTimeOffset](xref:System.DateTimeOffset) dont le décalage est celui du fuseau horaire local. Cela est illustré dans l’exemple suivant, qui se déroule dans le fuseau horaire Pacifique (É.-U.).

```csharp
DateTime time1 = new DateTime(2008, 6, 19, 7, 0, 0);  // Kind is DateTimeKind.Unspecified
DateTimeOffset time2 = time1;
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", 
                  time1, 
                  time1.Kind.ToString(), 
                  time2);
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

```vb
Dim time1 As Date = #06/19/2008 7:00AM#      ' Kind is DateTimeKind.Unspecified
Dim time2 As DateTimeOffset = time1
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", _
                  time1, _
                  time1.Kind.ToString(), _
                  time2)
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

Si la valeur [DateTime](xref:System.DateTime) reflète la date et l’heure dans autre chose que le fuseau horaire local ou UTC, vous pouvez la convertir en une valeur [DateTimeOffset](xref:System.DateTimeOffset) et conserver ses informations de fuseau horaire en appelant le constructeur surchargé [DateTimeOffset(DateTime, TimeSpan)](xref:System.DateTimeOffset). Par exemple, l’exemple suivant instancie un objet [DateTimeOffset](xref:System.DateTimeOffset) qui reflète l’heure du centre.

```csharp
DateTime time1 = new DateTime(2008, 6, 19, 7, 0, 0);     // Kind is DateTimeKind.Unspecified
try
{
   DateTimeOffset time2 = new DateTimeOffset(time1, 
                  TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(time1)); 
   Console.WriteLine("Converted {0} {1} to a DateTime value of {2}", 
                     time1, 
                     time1.Kind.ToString(), 
                     time2);
}
// Handle exception if time zone is not defined in registry
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("Unable to identify target time zone for conversion.");
}
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTime value of 6/19/2008 7:00:00 AM -05:00
```

```vb
Dim time1 As Date = #06/19/2008 7:00AM#      ' Kind is DateTimeKind.Unspecified
Try
   Dim time2 As New DateTimeOffset(time1, _
                    TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(time1)) 
   Console.WriteLine("Converted {0} {1} to a DateTime value of {2}", _
                     time1, _
                     time1.Kind.ToString(), _
                     time2)
' Handle exception if time zone is not defined in registry
Catch e As TimeZoneNotFoundException
   Console.WriteLine("Unable to identify target time zone for conversion.")
End Try
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTime value of 6/19/2008 7:00:00 AM -05:00
```

Le deuxième paramètre de cette surcharge de constructeur, un objet [System.TimeSpan](xref:System.TimeSpan) qui représente le décalage horaire à partir de l’heure UTC, doit être récupéré en appelant la méthode [TimeZoneInfo.GetUtcOffset(DateTime)](xref:System.TimeZoneInfo) du fuseau horaire correspondant de l’heure. Le paramètre unique de la méthode est la valeur [DateTime](xref:System.DateTime) qui représente la date et l’heure à convertir. Si le fuseau horaire prend en charge l’heure d’été, ce paramètre permet à la méthode de déterminer le décalage approprié pour cette date et cette heure particulières.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>Conversions de DateTimeOffset vers DateTime

La propriété [DateTime](xref:System.DateTime) est généralement utilisée pour effectuer la conversion de [DateTimeOffset](xref:System.DateTimeOffset) vers [DateTime](xref:System.DateTime). Toutefois, elle retourne une valeur [DateTime](xref:System.DateTime) dont la propriété [Kind](xref:System.DateTime.Kind) est [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), comme l’illustre l’exemple suivant. 

```csharp
DateTime baseTime = new DateTime(2008, 6, 19, 7, 0, 0);
DateTimeOffset sourceTime;
DateTime targetTime;

// Convert UTC to DateTime value
sourceTime = new DateTimeOffset(baseTime, TimeSpan.Zero);
targetTime = sourceTime.DateTime;
Console.WriteLine("{0} converts to {1} {2}", 
                  sourceTime, 
                  targetTime, 
                  targetTime.Kind.ToString());

// Convert local time to DateTime value
sourceTime = new DateTimeOffset(baseTime, 
                                TimeZoneInfo.Local.GetUtcOffset(baseTime));
targetTime = sourceTime.DateTime;
Console.WriteLine("{0} converts to {1} {2}", 
                  sourceTime, 
                  targetTime, 
                  targetTime.Kind.ToString());

// Convert Central Standard Time to a DateTime value
try
{
   TimeSpan offset = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(baseTime);
   sourceTime = new DateTimeOffset(baseTime, offset);
   targetTime = sourceTime.DateTime;
   Console.WriteLine("{0} converts to {1} {2}", 
                     sourceTime, 
                     targetTime, 
                     targetTime.Kind.ToString());
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("Unable to create DateTimeOffset based on U.S. Central Standard Time.");
} 
// This example displays the following output to the console:
//    6/19/2008 7:00:00 AM +00:00 converts to 6/19/2008 7:00:00 AM Unspecified
//    6/19/2008 7:00:00 AM -07:00 converts to 6/19/2008 7:00:00 AM Unspecified
//    6/19/2008 7:00:00 AM -05:00 converts to 6/19/2008 7:00:00 AM Unspecified 
```

```vb
Const baseTime As Date = #06/19/2008 7:00AM#
Dim sourceTime As DateTimeOffset
Dim targetTime As Date

' Convert UTC to DateTime value
sourceTime = New DateTimeOffset(baseTime, TimeSpan.Zero)
targetTime = sourceTime.DateTime
Console.WriteLine("{0} converts to {1} {2}", _
                  sourceTime, _
                  targetTime, _
                  targetTime.Kind.ToString())

' Convert local time to DateTime value
sourceTime = New DateTimeOffset(baseTime, _
                                TimeZoneInfo.Local.GetUtcOffset(baseTime))
targetTime = sourceTime.DateTime
Console.WriteLine("{0} converts to {1} {2}", _
                  sourceTime, _
                  targetTime, _
                  targetTime.Kind.ToString())

' Convert Central Standard Time to a DateTime value
Try
   Dim offset As TimeSpan = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(baseTime)
   sourceTime = New DateTimeOffset(baseTime, offset)
   targetTime = sourceTime.DateTime
Console.WriteLine("{0} converts to {1} {2}", _
                  sourceTime, _
                  targetTime, _
                  targetTime.Kind.ToString())
Catch e As TimeZoneNotFoundException
   Console.WriteLine("Unable to create DateTimeOffset based on U.S. Central Standard Time.")
End Try 
' This example displays the following output to the console:
'    6/19/2008 7:00:00 AM +00:00 converts to 6/19/2008 7:00:00 AM Unspecified
'    6/19/2008 7:00:00 AM -07:00 converts to 6/19/2008 7:00:00 AM Unspecified
'    6/19/2008 7:00:00 AM -05:00 converts to 6/19/2008 7:00:00 AM Unspecified 
```

Cela signifie que toutes les informations sur la relation entre la valeur [DateTimeOffset](xref:System.DateTimeOffset) et l’heure UTC sont perdues par la conversion lorsque la propriété [DateTime](xref:System.DateTime) est utilisée. Cela affecte les valeurs [DateTimeOffset](xref:System.DateTimeOffset) qui correspondent à l’heure UTC ou à l’heure locale du système, car la structure [DateTime](xref:System.DateTime) reflète uniquement ces deux fuseaux horaires dans sa propriété [Kind](xref:System.DateTime.Kind).

Pour conserver autant d’informations de fuseau horaire que possible lorsque vous convertissez une valeur [DateTimeOffset](xref:System.DateTimeOffset) en valeur [DateTime](xref:System.DateTime), vous pouvez utiliser les propriétés [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) et [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime). 

## <a name="converting-a-utc-time"></a>Conversion d’une heure UTC

Pour indiquer qu’une valeur [DateTime](xref:System.DateTime) convertie est l’heure UTC, vous pouvez récupérer la valeur de la propriété [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime). Elle diffère de la propriété [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) de deux façons :

* Elle retourne une valeur [DateTime](xref:System.DateTime) dont la propriété [Kind](xref:System.DateTime.Kind) est [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).

* Si la valeur de propriété [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) n’est pas égale à [TimeSpan.Zero](xref:System.TimeSpan.Zero), elle convertit l’heure en heure UTC.

> [!NOTE]
> Si votre application exige que les valeurs converties [DateTime](xref:System.DateTime) identifient clairement un point unique dans le temps, vous devez envisager d’utiliser la propriété [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) pour gérer toutes les conversions de [DateTimeOffset](xref:System.DateTimeOffset) vers [DateTime](xref:System.DateTime).

Le code suivant utilise la propriété [UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) pour convertir une valeur [DateTimeOffset](xref:System.DateTimeOffset) dont le décalage est égal à [TimeSpan.Zero](xref:System.TimeSpan.Zero) vers une valeur [DateTime](xref:System.DateTime).

```csharp
DateTimeOffset utcTime1 = new DateTimeOffset(2008, 6, 19, 7, 0, 0, TimeSpan.Zero);
DateTime utcTime2 = utcTime1.UtcDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  utcTime1, 
                  utcTime2, 
                  utcTime2.Kind.ToString());
// The example displays the following output to the console:
//   6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
```

```vb
Dim utcTime1 As New DateTimeOffset(#06/19/2008 7:00AM#, TimeSpan.Zero)
Dim utcTime2 As Date = utcTime1.UtcDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  utcTime1, _
                  utcTime2, _
                  utcTime2.Kind.ToString())
' The example displays the following output to the console:
'   6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
```

Le code suivant utilise la propriété UtcDateTime pour effectuer une conversion de fuseau horaire et une conversion de type sur une valeur [DateTimeOffset](xref:System.DateTimeOffset).

```csharp
DateTimeOffset originalTime = new DateTimeOffset(2008, 6, 19, 7, 0, 0, new TimeSpan(5, 0, 0));
DateTime utcTime = originalTime.UtcDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  originalTime, 
                  utcTime, 
                  utcTime.Kind.ToString());
// The example displays the following output to the console:
//       6/19/2008 7:00:00 AM +05:00 converted to 6/19/2008 2:00:00 AM Utc
```

```vb
Dim originalTime As New DateTimeOffset(#6/19/2008 7:00AM#, _
                                       New TimeSpan(5, 0, 0))
Dim utcTime As Date = originalTime.UtcDateTime
Console.WriteLine("{0} converted to {1} {2}", _ 
                  originalTime, _
                  utcTime, _
                  utcTime.Kind.ToString())
' The example displays the following output to the console:
'       6/19/2008 7:00:00 AM +05:00 converted to 6/19/2008 2:00:00 AM Utc
```

## <a name="converting-a-local-time"></a>Conversion d’une heure locale

Pour indiquer qu’une valeur [DateTimeOffset](xref:System.DateTimeOffset) représente l’heure locale, vous pouvez transmettre la valeur [DateTime](xref:System.DateTime) retournée par la propriété [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) à la méthode statique [DateTime.SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)). La méthode retourne la date et l’heure qui lui sont transmises comme premier paramètre, mais définit la propriété [Kind](xref:System.DateTime.Kind) sur la valeur spécifiée par son deuxième paramètre. Le code suivant utilise la méthode [SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) lors de la conversion d’une valeur [DateTimeOffset](xref:System.DateTimeOffset) dont le décalage correspond à celui du fuseau horaire local.

```csharp
DateTime sourceDate = new DateTime(2008, 6, 19, 7, 0, 0);
DateTimeOffset utcTime1 = new DateTimeOffset(sourceDate, 
                          TimeZoneInfo.Local.GetUtcOffset(sourceDate));
DateTime utcTime2 = utcTime1.DateTime;
if (utcTime1.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(utcTime1.DateTime))) 
   utcTime2 = DateTime.SpecifyKind(utcTime2, DateTimeKind.Local);

Console.WriteLine("{0} converted to {1} {2}", 
                  utcTime1, 
                  utcTime2, 
                  utcTime2.Kind.ToString());
// The example displays the following output to the console:
//   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
```

```vb
Dim sourceDate As Date = #06/19/2008 7:00AM#
Dim utcTime1 As New DateTimeOffset(sourceDate, _
                                   TimeZoneInfo.Local.GetUtcOffset(sourceDate))
Dim utcTime2 As Date = utcTime1.DateTime
If utcTime1.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(utcTime1.DateTime)) Then
   utcTime2 = DateTime.SpecifyKind(utcTime2, DateTimeKind.Local)
End If   
Console.WriteLine("{0} converted to {1} {2}", _
                  utcTime1, _
                  utcTime2, _
                  utcTime2.Kind.ToString())
' The example displays the following output to the console:
'   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
```

Vous pouvez également utiliser la propriété [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) pour convertir une valeur [DateTimeOffset](xref:System.DateTimeOffset) en une valeur locale [DateTime](xref:System.DateTime). La propriété [Kind](xref:System.DateTime.Kind) de la valeur [DateTime](xref:System.DateTime) retournée est [DateTimeKind.Local](xref:System.DateTimeKind.Local). Le code suivant utilise la propriété [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) lors de la conversion d’une valeur [DateTimeOffset](xref:System.DateTimeOffset) dont le décalage correspond à celui du fuseau horaire local.

```csharp
DateTime sourceDate = new DateTime(2008, 6, 19, 7, 0, 0);
DateTimeOffset localTime1 = new DateTimeOffset(sourceDate, 
                          TimeZoneInfo.Local.GetUtcOffset(sourceDate));
DateTime localTime2 = localTime1.LocalDateTime;

Console.WriteLine("{0} converted to {1} {2}", 
                  localTime1, 
                  localTime2, 
                  localTime2.Kind.ToString());
// The example displays the following output to the console:
//   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
```

```vb
Dim sourceDate As Date = #06/19/2008 7:00AM#
Dim localTime1 As New DateTimeOffset(sourceDate, _
                                   TimeZoneInfo.Local.GetUtcOffset(sourceDate))
Dim localTime2 As Date = localTime1.LocalDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  localTime1, _
                  localTime2, _
                  localTime2.Kind.ToString())
' The example displays the following output to the console:
'   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local 
```

Lorsque vous récupérez une valeur [DateTime](xref:System.DateTime) à l’aide de la propriété [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime), l’accesseur `get` de la propriété convertit d’abord la valeur [DateTimeOffset](xref:System.DateTimeOffset) en heure UTC, puis en heure locale en appelant la méthode [DateTimeOffset.ToLocalTime](xref:System.DateTimeOffset). Cela signifie que vous pouvez récupérer une valeur à partir de la propriété [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) pour effectuer une conversion de fuseau horaire en même temps que vous effectuez une conversion de type. Cela signifie également que les règles d’ajustement du fuseau horaire local sont appliquées lors de la conversion. Le code suivant illustre l’utilisation de la propriété [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) pour effectuer à la fois une conversion de fuseau horaire et une conversion de type.

```csharp
DateTimeOffset originalDate;
DateTime localDate;

// Convert time originating in a different time zone
originalDate = new DateTimeOffset(2008, 6, 18, 7, 0, 0, 
                                  new TimeSpan(-5, 0, 0));
localDate = originalDate.LocalDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  originalDate, 
                  localDate, 
                  localDate.Kind.ToString());
// Convert time originating in a different time zone 
// so local time zone's adjustment rules are applied
originalDate = new DateTimeOffset(2007, 11, 4, 4, 0, 0, 
                                  new TimeSpan(-5, 0, 0));
localDate = originalDate.LocalDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  originalDate, 
                  localDate, 
                  localDate.Kind.ToString());
// The example displays the following output to the console:
//       6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 5:00:00 AM Local
//       11/4/2007 4:00:00 AM -05:00 converted to 11/4/2007 1:00:00 AM Local
```

```vb
Dim originalDate As DateTimeOffset
Dim localDate As Date

' Convert time originating in a different time zone
originalDate = New DateTimeOffset(#06/19/2008 7:00AM#, _
                                  New TimeSpan(-5, 0, 0))
localDate = originalDate.LocalDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  originalDate, _
                  localDate, _
                  localDate.Kind.ToString())
' Convert time originating in a different time zone 
' so local time zone's adjustment rules are applied
originalDate = New DateTimeOffset(#11/04/2007 4:00AM#, _
                                  New TimeSpan(-5, 0, 0))
localDate = originalDate.LocalDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  originalDate, _
                  localDate, _
                  localDate.Kind.ToString())
' The example displays the following output to the console:
'       6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 5:00:00 AM Local
'       11/4/2007 4:00:00 AM -05:00 converted to 11/4/2007 1:00:00 AM Local
```

## <a name="a-generalpurpose-conversion-method"></a>Méthode de conversion à usage général

L’exemple suivant définit une méthode nommée `ConvertFromDateTimeOffset` qui convertit des valeurs [DateTimeOffset](xref:System.DateTimeOffset) en valeurs [DateTime](xref:System.DateTime). En fonction de son décalage, elle détermine si la valeur [DateTimeOffset](xref:System.DateTimeOffset) est une heure UTC, une heure locale ou autre, et elle définit la propriété [Kind](xref:System.DateTime.Kind) de la valeur de date et d’heure retournée, en conséquence. 

```csharp
static DateTime ConvertFromDateTimeOffset(DateTimeOffset dateTime)
{
   if (dateTime.Offset.Equals(TimeSpan.Zero))
      return dateTime.UtcDateTime;
   else if (dateTime.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(dateTime.DateTime)))
      return DateTime.SpecifyKind(dateTime.DateTime, DateTimeKind.Local);
   else
      return dateTime.DateTime;   
}
```

```vb
Function ConvertFromDateTimeOffset(dateTime As DateTimeOffset) As Date
   If dateTime.Offset.Equals(TimeSpan.Zero) Then
      Return dateTime.UtcDateTime
   ElseIf dateTime.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(dateTime.DateTime))
      Return Date.SpecifyKind(dateTime.DateTime, DateTimeKind.Local)
   Else
      Return dateTime.DateTime   
   End If
```

L’exemple suivant appelle la méthode `ConvertFromDateTimeOffset` pour convertir des valeurs [DateTimeOffset](xref:System.DateTimeOffset) qui représentent une heure UTC, une heure locale et une heure dans le fuseau horaire Centre des États-Unis.

```csharp
DateTime timeComponent = new DateTime(2008, 6, 19, 7, 0, 0);
DateTime returnedDate; 

// Convert UTC time
DateTimeOffset utcTime = new DateTimeOffset(timeComponent, TimeSpan.Zero);
returnedDate = ConvertFromDateTimeOffset(utcTime); 
Console.WriteLine("{0} converted to {1} {2}", 
                  utcTime, 
                  returnedDate, 
                  returnedDate.Kind.ToString());

// Convert local time
DateTimeOffset localTime = new DateTimeOffset(timeComponent, 
                           TimeZoneInfo.Local.GetUtcOffset(timeComponent)); 
returnedDate = ConvertFromDateTimeOffset(localTime);                                          
Console.WriteLine("{0} converted to {1} {2}", 
                  localTime, 
                  returnedDate, 
                  returnedDate.Kind.ToString());

// Convert Central Standard Time
DateTimeOffset cstTime = new DateTimeOffset(timeComponent, 
               TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(timeComponent));
returnedDate = ConvertFromDateTimeOffset(cstTime);
Console.WriteLine("{0} converted to {1} {2}", 
                  cstTime, 
                  returnedDate, 
                  returnedDate.Kind.ToString());
// The example displays the following output to the console:
//    6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
//    6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
//    6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 7:00:00 AM Unspecified
```

```vb
Dim timeComponent As Date = #06/19/2008 7:00AM#
Dim returnedDate As Date 

' Convert UTC time
Dim utcTime As New DateTimeOffset(timeComponent, TimeSpan.Zero)
returnedDate = ConvertFromDateTimeOffset(utcTime) 
Console.WriteLine("{0} converted to {1} {2}", _
                  utcTime, _
                  returnedDate, _
                  returnedDate.Kind.ToString())

' Convert local time
Dim localTime As New DateTimeOffset(timeComponent, _
                                    TimeZoneInfo.Local.GetUtcOffset(timeComponent)) 
returnedDate = ConvertFromDateTimeOffset(localTime)                                                                  
Console.WriteLine("{0} converted to {1} {2}", _
                  localTime, _
                  returnedDate, _
                  returnedDate.Kind.ToString())

' Convert Central Standard Time
Dim cstTime As New DateTimeOffset(timeComponent, _
               TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(timeComponent))
returnedDate = ConvertFromDateTimeOffset(cstTime)                                                                  
Console.WriteLine("{0} converted to {1} {2}", _
                  cstTime, _
                  returnedDate, _
                  returnedDate.Kind.ToString())
' The example displays the following output to the console:
'    6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
'    6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
'    6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 7:00:00 AM Unspecified
```

Notez que ce code part de deux hypothèses qui, selon l’application et la source de ses valeurs de date et d’heure, peuvent ne pas toujours être valides :

* Il suppose qu’une valeur de date et d’heure dont le décalage est [TimeSpan.Zero](xref:System.TimeSpan.Zero) représente une heure UTC. En fait, l’heure UTC n’est pas une heure dans un fuseau horaire particulier, mais l’heure par rapport à laquelle les heures des fuseaux horaires du monde sont normalisées. Les fuseaux horaires peuvent également avoir un décalage égal à [zéro](xref:System.TimeSpan.Zero).

* Il suppose qu’une date et une heure dont le décalage est égal à celui du fuseau horaire local représentent le fuseau horaire local. Étant donné que les valeurs de date et d’heure sont dissociées de leur fuseau horaire d’origine, cela peut ne pas être le cas ; la date et l’heure peuvent provenir d’un autre fuseau horaire affichant le même décalage.

## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](index.md)







<!--HONumber=Nov16_HO1-->


