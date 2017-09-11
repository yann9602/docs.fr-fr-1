---
title: Conversion entre DateTime et DateTimeOffset
description: Conversion entre DateTime et DateTimeOffset
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: fab3af5b-5d0f-4384-a40a-1b5d99b30dd1
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 2ba70e9ea39148d040bdb46d5e00ea50dcbb8980
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="converting-between-datetime-and-datetimeoffset"></a><span data-ttu-id="d09cc-104">Conversion entre DateTime et DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="d09cc-104">Converting between DateTime and DateTimeOffset</span></span>

<span data-ttu-id="d09cc-105">La structure [System.DateTimeOffset](xref:System.DateTimeOffset) fournit un degré supérieur de prise en compte du fuseau horaire que la structure [System.DateTime](xref:System.DateTime), mais les paramètres [DateTime](xref:System.DateTime) sont plus fréquemment utilisés dans les appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="d09cc-105">Although the [System.DateTimeOffset](xref:System.DateTimeOffset) structure provides a greater degree of time zone awareness than the [System.DateTime](xref:System.DateTime) structure, [DateTime](xref:System.DateTime) parameters are used more commonly in method calls.</span></span> <span data-ttu-id="d09cc-106">Pour cette raison, l’aptitude à convertir des valeurs [DateTimeOffset](xref:System.DateTimeOffset) en valeurs [DateTime](xref:System.DateTime) et vice versa est particulièrement importante.</span><span class="sxs-lookup"><span data-stu-id="d09cc-106">Because of this, the ability to convert [DateTimeOffset](xref:System.DateTimeOffset) values to [DateTime](xref:System.DateTime) values and vice versa is particularly important.</span></span> <span data-ttu-id="d09cc-107">Cet article montre comment effectuer ces conversions de façon à conserver autant d’informations de fuseau horaire que possible.</span><span class="sxs-lookup"><span data-stu-id="d09cc-107">This article shows how to perform these conversions in a way that preserves as much time zone information as possible.</span></span>

> [!NOTE]
> <span data-ttu-id="d09cc-108">Les types [DateTime](xref:System.DateTime) et [DateTimeOffset](xref:System.DateTimeOffset) présentent tous les deux certaines restrictions lors de la représentation des heures dans des fuseaux horaires.</span><span class="sxs-lookup"><span data-stu-id="d09cc-108">Both the [DateTime](xref:System.DateTime) and the [DateTimeOffset](xref:System.DateTimeOffset) types have some limitations when representing times in time zones.</span></span> <span data-ttu-id="d09cc-109">Avec sa propriété [Kind](xref:System.DateTime.Kind), [DateTime](xref:System.DateTime) peut refléter uniquement le temps universel coordonné (UTC) et le fuseau horaire local du système.</span><span class="sxs-lookup"><span data-stu-id="d09cc-109">With its [Kind](xref:System.DateTime.Kind) property, [DateTime](xref:System.DateTime) is able to reflect only Coordinated Universal Time (UTC) and the system's local time zone.</span></span> <span data-ttu-id="d09cc-110">[DateTimeOffset](xref:System.DateTimeOffset) reflète un décalage horaire par rapport à l’heure UTC, mais ne reflète pas le fuseau horaire réel auquel ce décalage appartient.</span><span class="sxs-lookup"><span data-stu-id="d09cc-110">[DateTimeOffset](xref:System.DateTimeOffset) reflects a time's offset from UTC, but it does not reflect the actual time zone to which that offset belongs.</span></span> <span data-ttu-id="d09cc-111">Pour plus d’informations sur les valeurs de date/heure et la prise en charge des fuseaux horaires, consultez [Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](choosing-between-datetime.md).</span><span class="sxs-lookup"><span data-stu-id="d09cc-111">For details about time values and support for time zones, see [Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](choosing-between-datetime.md).</span></span>

## <a name="conversions-from-datetime-to-datetimeoffset"></a><span data-ttu-id="d09cc-112">Conversions de DateTime en DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="d09cc-112">Conversions from DateTime to DateTimeOffset</span></span>

<span data-ttu-id="d09cc-113">La structure [DateTimeOffset](xref:System.DateTimeOffset) fournit deux moyens équivalents de convertir des données [DateTime](xref:System.DateTime) en données [DateTimeOffset](xref:System.DateTimeOffset), qui conviennent à la plupart des conversions :</span><span class="sxs-lookup"><span data-stu-id="d09cc-113">The [DateTimeOffset](xref:System.DateTimeOffset) structure provides two equivalent ways to perform [DateTime](xref:System.DateTime) to [DateTimeOffset](xref:System.DateTimeOffset) conversion that are suitable for most conversions:</span></span>

* <span data-ttu-id="d09cc-114">Le constructeur [DateTimeOffset(DateTime)](xref:System.DateTimeOffset), qui crée un nouvel objet [DateTimeOffset](xref:System.DateTimeOffset) basé sur une valeur [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="d09cc-114">The [DateTimeOffset(DateTime)](xref:System.DateTimeOffset) constructor, which creates a new [DateTimeOffset](xref:System.DateTimeOffset) object based on a [DateTime](xref:System.DateTime) value.</span></span>

* <span data-ttu-id="d09cc-115">L’opérateur de conversion implicite, qui vous permet d’attribuer une valeur [DateTime](xref:System.DateTime) à un objet [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="d09cc-115">The implicit conversion operator, which allows you to assign a [DateTime](xref:System.DateTime) value to a [DateTimeOffset](xref:System.DateTimeOffset) object.</span></span>

<span data-ttu-id="d09cc-116">Pour les valeurs [DateTime](xref:System.DateTime) UTC et locales, la propriété [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) de la valeur [DateTimeOffset](xref:System.DateTimeOffset) résultante reflète précisément le décalage du fuseau horaire UTC ou local.</span><span class="sxs-lookup"><span data-stu-id="d09cc-116">For UTC and local [DateTime](xref:System.DateTime) values, the [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) property of the resulting [DateTimeOffset](xref:System.DateTimeOffset) value accurately reflects the UTC or local time zone offset.</span></span> <span data-ttu-id="d09cc-117">Par exemple, le code suivant convertit une heure UTC vers sa valeur [DateTimeOffset](xref:System.DateTimeOffset) équivalente.</span><span class="sxs-lookup"><span data-stu-id="d09cc-117">For example, the following code converts a UTC time to its equivalent [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> 

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

<span data-ttu-id="d09cc-118">Dans ce cas, le décalage de la variable `utcTime2` est 00:00.</span><span class="sxs-lookup"><span data-stu-id="d09cc-118">In this case, the offset of the `utcTime2` variable is 00:00.</span></span> <span data-ttu-id="d09cc-119">De même, le code suivant convertit une heure locale en une valeur [DateTimeOffset](xref:System.DateTimeOffset) équivalente.</span><span class="sxs-lookup"><span data-stu-id="d09cc-119">Similarly, the following code converts a local time to its equivalent [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span>

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

<span data-ttu-id="d09cc-120">Toutefois, pour les valeurs [DateTime](xref:System.DateTime) dont la propriété [Kind](xref:System.DateTime.Kind) est [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), ces deux méthodes de conversion produisent une valeur [DateTimeOffset](xref:System.DateTimeOffset) dont le décalage est celui du fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="d09cc-120">However, for [DateTime](xref:System.DateTime) values whose [Kind](xref:System.DateTime.Kind) property is [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), these two conversion methods produce a [DateTimeOffset](xref:System.DateTimeOffset) value whose offset is that of the local time zone.</span></span> <span data-ttu-id="d09cc-121">Cela est illustré dans l’exemple suivant, qui se déroule dans le fuseau horaire Pacifique (É.-U.).</span><span class="sxs-lookup"><span data-stu-id="d09cc-121">This is shown in the following example, which is run in the U.S. Pacific Standard Time zone.</span></span>

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

<span data-ttu-id="d09cc-122">Si la valeur [DateTime](xref:System.DateTime) reflète la date et l’heure dans autre chose que le fuseau horaire local ou UTC, vous pouvez la convertir en une valeur [DateTimeOffset](xref:System.DateTimeOffset) et conserver ses informations de fuseau horaire en appelant le constructeur surchargé [DateTimeOffset(DateTime, TimeSpan)](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="d09cc-122">If the [DateTime](xref:System.DateTime) value reflects the date and time in something other than the local time zone or UTC, you can convert it to a [DateTimeOffset](xref:System.DateTimeOffset) value and preserve its time zone information by calling the overloaded [DateTimeOffset(DateTime, TimeSpan)](xref:System.DateTimeOffset) constructor.</span></span> <span data-ttu-id="d09cc-123">Par exemple, l’exemple suivant instancie un objet [DateTimeOffset](xref:System.DateTimeOffset) qui reflète l’heure du centre.</span><span class="sxs-lookup"><span data-stu-id="d09cc-123">For example, the following example instantiates a [DateTimeOffset](xref:System.DateTimeOffset) object that reflects Central Standard Time.</span></span>

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

<span data-ttu-id="d09cc-124">Le deuxième paramètre de cette surcharge de constructeur, un objet [System.TimeSpan](xref:System.TimeSpan) qui représente le décalage horaire à partir de l’heure UTC, doit être récupéré en appelant la méthode [TimeZoneInfo.GetUtcOffset(DateTime)](xref:System.TimeZoneInfo) du fuseau horaire correspondant de l’heure.</span><span class="sxs-lookup"><span data-stu-id="d09cc-124">The second parameter to this constructor overload, a [System.TimeSpan](xref:System.TimeSpan) object that represents the time's offset from UTC, should be retrieved by calling the [TimeZoneInfo.GetUtcOffset(DateTime)](xref:System.TimeZoneInfo) method of the time's corresponding time zone.</span></span> <span data-ttu-id="d09cc-125">Le paramètre unique de la méthode est la valeur [DateTime](xref:System.DateTime) qui représente la date et l’heure à convertir.</span><span class="sxs-lookup"><span data-stu-id="d09cc-125">The method's single parameter is the [DateTime](xref:System.DateTime) value that represents the date and time to be converted.</span></span> <span data-ttu-id="d09cc-126">Si le fuseau horaire prend en charge l’heure d’été, ce paramètre permet à la méthode de déterminer le décalage approprié pour cette date et cette heure particulières.</span><span class="sxs-lookup"><span data-stu-id="d09cc-126">If the time zone supports daylight saving time, this parameter allows the method to determine the appropriate offset for that particular date and time.</span></span>

## <a name="conversions-from-datetimeoffset-to-datetime"></a><span data-ttu-id="d09cc-127">Conversions de DateTimeOffset vers DateTime</span><span class="sxs-lookup"><span data-stu-id="d09cc-127">Conversions from DateTimeOffset to DateTime</span></span>

<span data-ttu-id="d09cc-128">La propriété [DateTime](xref:System.DateTime) est généralement utilisée pour effectuer la conversion de [DateTimeOffset](xref:System.DateTimeOffset) vers [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="d09cc-128">The [DateTime](xref:System.DateTime) property is most commonly used to perform [DateTimeOffset](xref:System.DateTimeOffset) to [DateTime](xref:System.DateTime) conversion.</span></span> <span data-ttu-id="d09cc-129">Toutefois, elle retourne une valeur [DateTime](xref:System.DateTime) dont la propriété [Kind](xref:System.DateTime.Kind) est [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), comme l’illustre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d09cc-129">However, it returns a [DateTime](xref:System.DateTime) value whose [Kind](xref:System.DateTime.Kind) property is [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), as the following example illustrates.</span></span> 

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

<span data-ttu-id="d09cc-130">Cela signifie que toutes les informations sur la relation entre la valeur [DateTimeOffset](xref:System.DateTimeOffset) et l’heure UTC sont perdues par la conversion lorsque la propriété [DateTime](xref:System.DateTime) est utilisée.</span><span class="sxs-lookup"><span data-stu-id="d09cc-130">This means that any information about the [DateTimeOffset](xref:System.DateTimeOffset) value's relationship to UTC is lost by the conversion when the [DateTime](xref:System.DateTime) property is used.</span></span> <span data-ttu-id="d09cc-131">Cela affecte les valeurs [DateTimeOffset](xref:System.DateTimeOffset) qui correspondent à l’heure UTC ou à l’heure locale du système, car la structure [DateTime](xref:System.DateTime) reflète uniquement ces deux fuseaux horaires dans sa propriété [Kind](xref:System.DateTime.Kind).</span><span class="sxs-lookup"><span data-stu-id="d09cc-131">This affects [DateTimeOffset](xref:System.DateTimeOffset) values that correspond to UTC time or to the system's local time because the [DateTime](xref:System.DateTime) structure reflects only those two time zones in its [Kind](xref:System.DateTime.Kind) property.</span></span>

<span data-ttu-id="d09cc-132">Pour conserver autant d’informations de fuseau horaire que possible lorsque vous convertissez une valeur [DateTimeOffset](xref:System.DateTimeOffset) en valeur [DateTime](xref:System.DateTime), vous pouvez utiliser les propriétés [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) et [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime).</span><span class="sxs-lookup"><span data-stu-id="d09cc-132">To preserve as much time zone information as possible when converting a [DateTimeOffset](xref:System.DateTimeOffset) to a [DateTime](xref:System.DateTime) value, you can use the [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) and [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) properties.</span></span> 

## <a name="converting-a-utc-time"></a><span data-ttu-id="d09cc-133">Conversion d’une heure UTC</span><span class="sxs-lookup"><span data-stu-id="d09cc-133">Converting a UTC Time</span></span>

<span data-ttu-id="d09cc-134">Pour indiquer qu’une valeur [DateTime](xref:System.DateTime) convertie est l’heure UTC, vous pouvez récupérer la valeur de la propriété [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime).</span><span class="sxs-lookup"><span data-stu-id="d09cc-134">To indicate that a converted [DateTime](xref:System.DateTime) value is the UTC time, you can retrieve the value of the [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) property.</span></span> <span data-ttu-id="d09cc-135">Elle diffère de la propriété [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) de deux façons :</span><span class="sxs-lookup"><span data-stu-id="d09cc-135">It differs from the [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) property in two ways:</span></span>

* <span data-ttu-id="d09cc-136">Elle retourne une valeur [DateTime](xref:System.DateTime) dont la propriété [Kind](xref:System.DateTime.Kind) est [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span><span class="sxs-lookup"><span data-stu-id="d09cc-136">It returns a [DateTime](xref:System.DateTime) value whose [Kind](xref:System.DateTime.Kind) property is [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span></span>

* <span data-ttu-id="d09cc-137">Si la valeur de propriété [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) n’est pas égale à [TimeSpan.Zero](xref:System.TimeSpan.Zero), elle convertit l’heure en heure UTC.</span><span class="sxs-lookup"><span data-stu-id="d09cc-137">If the [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) property value does not equal [TimeSpan.Zero](xref:System.TimeSpan.Zero), it converts the time to UTC.</span></span>

> [!NOTE]
> <span data-ttu-id="d09cc-138">Si votre application exige que les valeurs converties [DateTime](xref:System.DateTime) identifient clairement un point unique dans le temps, vous devez envisager d’utiliser la propriété [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) pour gérer toutes les conversions de [DateTimeOffset](xref:System.DateTimeOffset) vers [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="d09cc-138">If your application requires that converted [DateTime](xref:System.DateTime) values unambiguously identify a single point in time, you should consider using the [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) property to handle all [DateTimeOffset](xref:System.DateTimeOffset) to [DateTime](xref:System.DateTime) conversions.</span></span>

<span data-ttu-id="d09cc-139">Le code suivant utilise la propriété [UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) pour convertir une valeur [DateTimeOffset](xref:System.DateTimeOffset) dont le décalage est égal à [TimeSpan.Zero](xref:System.TimeSpan.Zero) vers une valeur [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="d09cc-139">The following code uses the [UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) property to convert a [DateTimeOffset](xref:System.DateTimeOffset) value whose offset equals [TimeSpan.Zero](xref:System.TimeSpan.Zero) to a [DateTime](xref:System.DateTime) value.</span></span>

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

<span data-ttu-id="d09cc-140">Le code suivant utilise la propriété UtcDateTime pour effectuer une conversion de fuseau horaire et une conversion de type sur une valeur [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="d09cc-140">The following code uses the UtcDateTime property to perform both a time zone conversion and a type conversion on a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span>

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

## <a name="converting-a-local-time"></a><span data-ttu-id="d09cc-141">Conversion d’une heure locale</span><span class="sxs-lookup"><span data-stu-id="d09cc-141">Converting a Local Time</span></span>

<span data-ttu-id="d09cc-142">Pour indiquer qu’une valeur [DateTimeOffset](xref:System.DateTimeOffset) représente l’heure locale, vous pouvez transmettre la valeur [DateTime](xref:System.DateTime) retournée par la propriété [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) à la méthode statique [DateTime.SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)).</span><span class="sxs-lookup"><span data-stu-id="d09cc-142">To indicate that a [DateTimeOffset](xref:System.DateTimeOffset) value represents the local time, you can pass the [DateTime](xref:System.DateTime) value returned by the [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) property to the static [DateTime.SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) method.</span></span> <span data-ttu-id="d09cc-143">La méthode retourne la date et l’heure qui lui sont transmises comme premier paramètre, mais définit la propriété [Kind](xref:System.DateTime.Kind) sur la valeur spécifiée par son deuxième paramètre.</span><span class="sxs-lookup"><span data-stu-id="d09cc-143">The method returns the date and time passed to it as its first parameter, but sets the [Kind](xref:System.DateTime.Kind) property to the value specified by its second parameter.</span></span> <span data-ttu-id="d09cc-144">Le code suivant utilise la méthode [SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) lors de la conversion d’une valeur [DateTimeOffset](xref:System.DateTimeOffset) dont le décalage correspond à celui du fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="d09cc-144">The following code uses the [SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) method when converting a [DateTimeOffset](xref:System.DateTimeOffset) value whose offset corresponds to that of the local time zone.</span></span>

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

<span data-ttu-id="d09cc-145">Vous pouvez également utiliser la propriété [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) pour convertir une valeur [DateTimeOffset](xref:System.DateTimeOffset) en une valeur locale [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="d09cc-145">You can also use the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property to convert a [DateTimeOffset](xref:System.DateTimeOffset) value to a local [DateTime](xref:System.DateTime) value.</span></span> <span data-ttu-id="d09cc-146">La propriété [Kind](xref:System.DateTime.Kind) de la valeur [DateTime](xref:System.DateTime) retournée est [DateTimeKind.Local](xref:System.DateTimeKind.Local).</span><span class="sxs-lookup"><span data-stu-id="d09cc-146">The [Kind](xref:System.DateTime.Kind) property of the returned [DateTime](xref:System.DateTime) value is [DateTimeKind.Local](xref:System.DateTimeKind.Local).</span></span> <span data-ttu-id="d09cc-147">Le code suivant utilise la propriété [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) lors de la conversion d’une valeur [DateTimeOffset](xref:System.DateTimeOffset) dont le décalage correspond à celui du fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="d09cc-147">The following code uses the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property when converting a [DateTimeOffset](xref:System.DateTimeOffset) value whose offset corresponds to that of the local time zone.</span></span>

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

<span data-ttu-id="d09cc-148">Lorsque vous récupérez une valeur [DateTime](xref:System.DateTime) à l’aide de la propriété [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime), l’accesseur `get` de la propriété convertit d’abord la valeur [DateTimeOffset](xref:System.DateTimeOffset) en heure UTC, puis en heure locale en appelant la méthode [DateTimeOffset.ToLocalTime](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="d09cc-148">When you retrieve a [DateTime](xref:System.DateTime) value using the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property, the property's `get` accessor first converts the [DateTimeOffset](xref:System.DateTimeOffset) value to UTC, then converts it to local time by calling the [DateTimeOffset.ToLocalTime](xref:System.DateTimeOffset) method.</span></span> <span data-ttu-id="d09cc-149">Cela signifie que vous pouvez récupérer une valeur à partir de la propriété [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) pour effectuer une conversion de fuseau horaire en même temps que vous effectuez une conversion de type.</span><span class="sxs-lookup"><span data-stu-id="d09cc-149">This means that you can retrieve a value from the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property to perform a time zone conversion at the same time that you perform a type conversion.</span></span> <span data-ttu-id="d09cc-150">Cela signifie également que les règles d’ajustement du fuseau horaire local sont appliquées lors de la conversion.</span><span class="sxs-lookup"><span data-stu-id="d09cc-150">It also means that the local time zone's adjustment rules are applied in performing the conversion.</span></span> <span data-ttu-id="d09cc-151">Le code suivant illustre l’utilisation de la propriété [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) pour effectuer à la fois une conversion de fuseau horaire et une conversion de type.</span><span class="sxs-lookup"><span data-stu-id="d09cc-151">The following code illustrates the use of the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property to perform both a type and a time zone conversion.</span></span>

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

## <a name="a-general-purpose-conversion-method"></a><span data-ttu-id="d09cc-152">Méthode de conversion à usage général</span><span class="sxs-lookup"><span data-stu-id="d09cc-152">A General-Purpose Conversion Method</span></span>

<span data-ttu-id="d09cc-153">L’exemple suivant définit une méthode nommée `ConvertFromDateTimeOffset` qui convertit des valeurs [DateTimeOffset](xref:System.DateTimeOffset) en valeurs [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="d09cc-153">The following example defines a method named `ConvertFromDateTimeOffset` that converts [DateTimeOffset](xref:System.DateTimeOffset) values to [DateTime](xref:System.DateTime) values.</span></span> <span data-ttu-id="d09cc-154">En fonction de son décalage, elle détermine si la valeur [DateTimeOffset](xref:System.DateTimeOffset) est une heure UTC, une heure locale ou autre, et elle définit la propriété [Kind](xref:System.DateTime.Kind) de la valeur de date et d’heure retournée, en conséquence.</span><span class="sxs-lookup"><span data-stu-id="d09cc-154">Based on its offset, it determines whether the [DateTimeOffset](xref:System.DateTimeOffset) value is a UTC time, a local time, or some other time, and defines the returned date and time value's [Kind](xref:System.DateTime.Kind) property accordingly.</span></span> 

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

<span data-ttu-id="d09cc-155">L’exemple suivant appelle la méthode `ConvertFromDateTimeOffset` pour convertir des valeurs [DateTimeOffset](xref:System.DateTimeOffset) qui représentent une heure UTC, une heure locale et une heure dans le fuseau horaire Centre des États-Unis.</span><span class="sxs-lookup"><span data-stu-id="d09cc-155">The follow example calls the `ConvertFromDateTimeOffset` method to convert [DateTimeOffset](xref:System.DateTimeOffset) values that represent a UTC time, a local time, and a time in the U.S. Central Standard Time zone.</span></span>

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

<span data-ttu-id="d09cc-156">Notez que ce code part de deux hypothèses qui, selon l’application et la source de ses valeurs de date et d’heure, peuvent ne pas toujours être valides :</span><span class="sxs-lookup"><span data-stu-id="d09cc-156">Note that this code makes two assumptions that, depending on the application and the source of its date and time values, may not always be valid:</span></span>

* <span data-ttu-id="d09cc-157">Il suppose qu’une valeur de date et d’heure dont le décalage est [TimeSpan.Zero](xref:System.TimeSpan.Zero) représente une heure UTC.</span><span class="sxs-lookup"><span data-stu-id="d09cc-157">It assumes that a date and time value whose offset is [TimeSpan.Zero](xref:System.TimeSpan.Zero) represents UTC.</span></span> <span data-ttu-id="d09cc-158">En fait, l’heure UTC n’est pas une heure dans un fuseau horaire particulier, mais l’heure par rapport à laquelle les heures des fuseaux horaires du monde sont normalisées.</span><span class="sxs-lookup"><span data-stu-id="d09cc-158">In fact, UTC is not a time in a particular time zone, but the time in relation to which the times in the world's time zones are standardized.</span></span> <span data-ttu-id="d09cc-159">Les fuseaux horaires peuvent également avoir un décalage égal à [zéro](xref:System.TimeSpan.Zero).</span><span class="sxs-lookup"><span data-stu-id="d09cc-159">Time zones can also have an offset of [Zero](xref:System.TimeSpan.Zero).</span></span>

* <span data-ttu-id="d09cc-160">Il suppose qu’une date et une heure dont le décalage est égal à celui du fuseau horaire local représentent le fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="d09cc-160">It assumes that a date and time whose offset equals that of the local time zone represents the local time zone.</span></span> <span data-ttu-id="d09cc-161">Étant donné que les valeurs de date et d’heure sont dissociées de leur fuseau horaire d’origine, cela peut ne pas être le cas ; la date et l’heure peuvent provenir d’un autre fuseau horaire affichant le même décalage.</span><span class="sxs-lookup"><span data-stu-id="d09cc-161">Because date and time values are disassociated from their original time zone, this may not be the case; the date and time can have originated in another time zone with the same offset.</span></span>

## <a name="see-also"></a><span data-ttu-id="d09cc-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d09cc-162">See Also</span></span>

[<span data-ttu-id="d09cc-163">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="d09cc-163">Dates, times, and time zones</span></span>](index.md)





