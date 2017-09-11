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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 26be324eb5d58b94a71e89aba213f107cf8dfd1e
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="instantiating-a-datetimeoffset-object"></a><span data-ttu-id="e8a03-104">Instanciation d’un objet DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="e8a03-104">Instantiating a DateTimeOffset object</span></span>

<span data-ttu-id="e8a03-105">La structure [System.DateTimeOffset](xref:System.DateTimeOffset) offre plusieurs façons de créer de nouvelles valeurs [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="e8a03-105">The [System.DateTimeOffset](xref:System.DateTimeOffset) structure offers a number of ways to create new [DateTimeOffset](xref:System.DateTimeOffset) values.</span></span> <span data-ttu-id="e8a03-106">La plupart d’entre elles correspondent directement aux méthodes disponibles pour instancier de nouvelles valeurs [System.DateTime](xref:System.DateTime), avec des améliorations qui vous permettent de spécifier le décalage de la valeur de date et d’heure par rapport au temps universel coordonné (UTC).</span><span class="sxs-lookup"><span data-stu-id="e8a03-106">Many of them correspond directly to the methods available for instantiating new [System.DateTime](xref:System.DateTime) values, with enhancements that allow you to specify the date and time value's offset from Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="e8a03-107">En particulier, vous pouvez instancier une valeur [DateTimeOffset](xref:System.DateTimeOffset) comme suit :</span><span class="sxs-lookup"><span data-stu-id="e8a03-107">In particular, you can instantiate a [DateTimeOffset](xref:System.DateTimeOffset) value in the following ways:</span></span>

* <span data-ttu-id="e8a03-108">En appelant un constructeur [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="e8a03-108">By calling a [DateTimeOffset](xref:System.DateTimeOffset) constructor.</span></span>

* <span data-ttu-id="e8a03-109">En convertissant implicitement une valeur en valeur [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="e8a03-109">By implicitly converting a value to [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span>

* <span data-ttu-id="e8a03-110">En analysant la représentation sous forme de chaîne d’une date et d’une heure.</span><span class="sxs-lookup"><span data-stu-id="e8a03-110">By parsing the string representation of a date and time.</span></span>

## <a name="date-and-time-literals"></a><span data-ttu-id="e8a03-111">Littéraux de date et d’heure</span><span class="sxs-lookup"><span data-stu-id="e8a03-111">Date and Time Literals</span></span>

<span data-ttu-id="e8a03-112">Pour les langages qui la prennent en charge, l’une des façons les plus courantes d’instancier une valeur [DateTime](xref:System.DateTime) consiste à fournir la date et l’heure sous la forme d’une valeur littérale codée en dur.</span><span class="sxs-lookup"><span data-stu-id="e8a03-112">For languages that support it, one of the most common ways to instantiate a [DateTime](xref:System.DateTime) value is to provide the date and time as a hard-coded literal value.</span></span> <span data-ttu-id="e8a03-113">Par exemple, le code Visual Basic suivant crée un objet [DateTime](xref:System.DateTime) dont la valeur est le 1er janvier 2008 à 10:00.</span><span class="sxs-lookup"><span data-stu-id="e8a03-113">For example, the following Visual Basic code creates a [DateTime](xref:System.DateTime) object whose value is January 1, 2008, at 10:00 AM.</span></span>

```vb
Dim literalDate1 As Date = #05/01/2008 8:06:32 AM#
Console.WriteLine(literalDate1.ToString())
' Displays:
'              5/1/2008 8:06:32 AM
```

<span data-ttu-id="e8a03-114">Les valeurs [DateTimeOffset](xref:System.DateTimeOffset) peuvent également être initialisées à l’aide de littéraux de date et d’heure lors de l’utilisation de langages qui prennent en charge les littéraux [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="e8a03-114">[DateTimeOffset](xref:System.DateTimeOffset) values can also be initialized using date and time literals when using languages that support [DateTime](xref:System.DateTime) literals.</span></span> <span data-ttu-id="e8a03-115">Par exemple, le code Visual Basic suivant crée un objet [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="e8a03-115">For example, the following Visual Basic code creates a [DateTimeOffset](xref:System.DateTimeOffset) object.</span></span>

```vb
Dim literalDate As DateTimeOffset = #05/01/2008 8:06:32 AM#
Console.WriteLine(literalDate.ToString())
' Displays:
'              5/1/2008 8:06:32 AM -07:00
```

<span data-ttu-id="e8a03-116">Comme le montre la sortie de la console, la valeur [DateTimeOffset](xref:System.DateTimeOffset) créée de cette façon se voit assigner le décalage du fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="e8a03-116">As the console output shows, the [DateTimeOffset](xref:System.DateTimeOffset) value created in this way is assigned the offset of the local time zone.</span></span> <span data-ttu-id="e8a03-117">Cela signifie qu’une valeur [DateTimeOffset](xref:System.DateTimeOffset) affectée à l’aide d’un littéral de caractère n’identifie pas un point unique dans le temps si le code est exécuté sur des ordinateurs différents.</span><span class="sxs-lookup"><span data-stu-id="e8a03-117">This means that a [DateTimeOffset](xref:System.DateTimeOffset) value assigned using a character literal does not identify a single point of time if the code is run on different computers.</span></span>

## <a name="datetimeoffset-constructors"></a><span data-ttu-id="e8a03-118">Constructeurs DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="e8a03-118">DateTimeOffset Constructors</span></span>

<span data-ttu-id="e8a03-119">Le type [System.DateTimeOffset](xref:System.DateTimeOffset) définit cinq constructeurs.</span><span class="sxs-lookup"><span data-stu-id="e8a03-119">The [System.DateTimeOffset](xref:System.DateTimeOffset) type defines five constructors.</span></span> <span data-ttu-id="e8a03-120">Trois d’entre eux correspondent directement aux constructeurs [DateTime](xref:System.DateTime), avec un paramètre supplémentaire du type [System.TimeSpan](xref:System.TimeSpan) qui définit le décalage de date et d’heure par rapport à l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="e8a03-120">Three of them correspond directly to [DateTime](xref:System.DateTime) constructors, with an additional parameter of type [System.TimeSpan](xref:System.TimeSpan) that defines the date and time's offset from UTC.</span></span> <span data-ttu-id="e8a03-121">Ils vous permettent de définir une valeur [DateTimeOffset](xref:System.DateTimeOffset) basée sur la valeur de ses composants individuels de date et d’heure.</span><span class="sxs-lookup"><span data-stu-id="e8a03-121">These allow you to define a [DateTimeOffset](xref:System.DateTimeOffset) value based on the value of its individual date and time components.</span></span> <span data-ttu-id="e8a03-122">Par exemple, le code suivant utilise ces trois constructeurs pour instancier les objets [DateTimeOffset](xref:System.DateTimeOffset) avec des valeurs identiques de 7/1/2008 12:05 AM + 01:00.</span><span class="sxs-lookup"><span data-stu-id="e8a03-122">For example, the following code uses these three constructors to instantiate [DateTimeOffset](xref:System.DateTimeOffset) objects with identical values of 7/1/2008 12:05 AM +01:00.</span></span>

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

<span data-ttu-id="e8a03-123">Notez que, lorsque la valeur de l’objet [DateTimeOffset](xref:System.DateTimeOffset) instancié à l’aide d’un objet [PersianCalendar](xref:System.Globalization.PersianCalendar) comme l’un des arguments de son constructeur est affichée dans la console, elle est exprimée sous la forme d’une date du calendrier grégorien plutôt que du calendrier persan.</span><span class="sxs-lookup"><span data-stu-id="e8a03-123">Note that, when the value of the [DateTimeOffset](xref:System.DateTimeOffset) object instantiated using a [PersianCalendar](xref:System.Globalization.PersianCalendar) object as one of the arguments to its constructor is displayed to the console, it is expressed as a date in the Gregorian rather than the Persian calendar.</span></span> 

<span data-ttu-id="e8a03-124">Les deux autres constructeurs créent un objet [DateTimeOffset](xref:System.DateTimeOffset) à partir d’une valeur DateTime.</span><span class="sxs-lookup"><span data-stu-id="e8a03-124">The other two constructors create a [DateTimeOffset](xref:System.DateTimeOffset) object from a DateTime value.</span></span> <span data-ttu-id="e8a03-125">Le premier d’entre eux a un seul paramètre, la valeur [DateTime](xref:System.DateTime) à convertir en valeur [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="e8a03-125">The first of these has a single parameter, the [DateTime](xref:System.DateTime) value to convert to a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> <span data-ttu-id="e8a03-126">Le décalage de la valeur [DateTimeOffset](xref:System.DateTimeOffset) obtenue dépend de la propriété [Kind](xref:System.DateTime.Kind) de l’unique paramètre [DateTime](xref:System.DateTime) du constructeur.</span><span class="sxs-lookup"><span data-stu-id="e8a03-126">The offset of the resulting [DateTimeOffset](xref:System.DateTimeOffset) value depends on the [Kind](xref:System.DateTime.Kind) property of the constructor's single [DateTime](xref:System.DateTime) parameter.</span></span> <span data-ttu-id="e8a03-127">Si sa valeur est [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), le décalage est défini sur [TimeSpan.Zero](xref:System.TimeSpan.Zero).</span><span class="sxs-lookup"><span data-stu-id="e8a03-127">If its value is [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), the offset is set equal to [TimeSpan.Zero](xref:System.TimeSpan.Zero).</span></span> <span data-ttu-id="e8a03-128">Sinon, son décalage est défini comme égal à celui du fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="e8a03-128">Otherwise, its offset is set equal to that of the local time zone.</span></span> <span data-ttu-id="e8a03-129">L’exemple suivant illustre l’utilisation de ce constructeur pour instancier des objets [DateTimeOffset](xref:System.DateTimeOffset) qui représentent l’heure UTC et le fuseau horaire local :</span><span class="sxs-lookup"><span data-stu-id="e8a03-129">The following example illustrates the use of this constructor to instantiate [DateTimeOffset](xref:System.DateTimeOffset) objects representing UTC and the local time zone:</span></span>

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
> <span data-ttu-id="e8a03-130">Appeler la surcharge du constructeur [DateTimeOffset](xref:System.DateTimeOffset) qui a un seul paramètre [DateTime](xref:System.DateTime) équivaut à effectuer une conversion implicite d’une valeur [DateTime](xref:System.DateTime) en une valeur [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="e8a03-130">Calling the overload of the [DateTimeOffset](xref:System.DateTimeOffset) constructor that has a single [DateTime](xref:System.DateTime) parameter is equivalent to performing an implicit conversion of a [DateTime](xref:System.DateTime) value to a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span>

<span data-ttu-id="e8a03-131">Le deuxième constructeur qui crée un objet [DateTimeOffset](xref:System.DateTimeOffset) à partir d’une valeur [DateTime](xref:System.DateTime) possède deux paramètres : la valeur [DateTime](xref:System.DateTime) à convertir et une valeur [TimeSpan](xref:System.TimeSpan) représentant le décalage de date et d’heure par rapport à l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="e8a03-131">The second constructor that creates a [DateTimeOffset](xref:System.DateTimeOffset) object from a [DateTime](xref:System.DateTime) value has two parameters: the [DateTime](xref:System.DateTime) value to convert, and a [TimeSpan](xref:System.TimeSpan) value representing the date and time's offset from UTC.</span></span> <span data-ttu-id="e8a03-132">Cette valeur de décalage doit correspondre à la propriété [Kind](xref:System.DateTime.Kind) du premier paramètre du constructeur ou une exception [System.ArgumentException](xref:System.ArgumentException) est levée.</span><span class="sxs-lookup"><span data-stu-id="e8a03-132">This offset value must correspond to the [Kind](xref:System.DateTime.Kind) property of the constructor's first parameter or an [System.ArgumentException](xref:System.ArgumentException) is thrown.</span></span> <span data-ttu-id="e8a03-133">Si la propriété [Kind](xref:System.DateTime.Kind) du premier paramètre est [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), la valeur du deuxième paramètre doit être [TimeSpan.Zero](xref:System.TimeSpan.Zero).</span><span class="sxs-lookup"><span data-stu-id="e8a03-133">If the [Kind](xref:System.DateTime.Kind) property of the first parameter is [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), the value of the second parameter must be [TimeSpan.Zero](xref:System.TimeSpan.Zero).</span></span> <span data-ttu-id="e8a03-134">Si la propriété [Kind](xref:System.DateTime.Kind) du premier paramètre est [DateTimeKind.Local](xref:System.DateTimeKind.Local), la valeur du deuxième paramètre doit correspondre au décalage du fuseau horaire du système local.</span><span class="sxs-lookup"><span data-stu-id="e8a03-134">If the [Kind](xref:System.DateTime.Kind) property of the first parameter is [DateTimeKind.Local](xref:System.DateTimeKind.Local), the value of the second parameter must be the offset of the local system's time zone.</span></span> <span data-ttu-id="e8a03-135">Si la propriété [Kind](xref:System.DateTime.Kind) du premier paramètre est [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), le décalage peut être égal à n’importe quelle valeur valide.</span><span class="sxs-lookup"><span data-stu-id="e8a03-135">If the [Kind](xref:System.DateTime.Kind) property of the first parameter is [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), the offset can be any valid value.</span></span> <span data-ttu-id="e8a03-136">Le code suivant illustre les appels à ce constructeur pour convertir des valeurs [DateTime](xref:System.DateTime) en valeurs [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="e8a03-136">The following code illustrates calls to this constructor to convert [DateTime](xref:System.DateTime) to [DateTimeOffset](xref:System.DateTimeOffset) values.</span></span>

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

## <a name="implicit-type-conversion"></a><span data-ttu-id="e8a03-137">Conversion de type implicite</span><span class="sxs-lookup"><span data-stu-id="e8a03-137">Implicit Type Conversion</span></span>
 
<span data-ttu-id="e8a03-138">Le type [System.DateTimeOffset](xref:System.DateTimeOffset) prend en charge une conversion de type implicite : d’une valeur [System.DateTime](xref:System.DateTime) vers une valeur [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="e8a03-138">The [System.DateTimeOffset](xref:System.DateTimeOffset) type supports one implicit type conversion: from a [System.DateTime](xref:System.DateTime) value to a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> <span data-ttu-id="e8a03-139">(Une conversion de type implicite est une conversion d’un type vers un autre qui ne nécessite pas de cast explicite (en C#) ni de conversion (en Visual Basic), et qui ne perd pas d’informations.</span><span class="sxs-lookup"><span data-stu-id="e8a03-139">(An implicit type conversion is a conversion from one type to another that does not require an explicit cast (in C#) or conversion (in Visual Basic) and that does not lose information.</span></span> <span data-ttu-id="e8a03-140">Elle permet d’utiliser un code similaire au suivant.)</span><span class="sxs-lookup"><span data-stu-id="e8a03-140">It makes code like the following possible.</span></span>

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

<span data-ttu-id="e8a03-141">Le décalage de la valeur [DateTimeOffset](xref:System.DateTimeOffset) obtenue dépend de la valeur de la propriété DateTime.Kind](xref:System.DateTime.Kind).</span><span class="sxs-lookup"><span data-stu-id="e8a03-141">The offset of the resulting [DateTimeOffset](xref:System.DateTimeOffset) value depends on the DateTime.Kind](xref:System.DateTime.Kind) property value.</span></span> <span data-ttu-id="e8a03-142">Si sa valeur est [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), le décalage est défini sur [TimeSpan.Zero](xref:System.TimeSpan.Zero).</span><span class="sxs-lookup"><span data-stu-id="e8a03-142">If its value is [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), the offset is set equal to [TimeSpan.Zero](xref:System.TimeSpan.Zero).</span></span> <span data-ttu-id="e8a03-143">Si sa valeur est [DateTimeKind.Local](xref:System.DateTimeKind.Local) ou [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), le décalage est défini comme égal à celui du fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="e8a03-143">If its value is either [DateTimeKind.Local](xref:System.DateTimeKind.Local) or [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), the offset is set equal to that of the local time zone.</span></span>

## <a name="parsing-the-string-representation-of-a-date-and-time"></a><span data-ttu-id="e8a03-144">Analyse de la représentation sous forme de chaîne d’une date et d’une heure</span><span class="sxs-lookup"><span data-stu-id="e8a03-144">Parsing the String Representation of a Date and Time</span></span>

<span data-ttu-id="e8a03-145">Le type [System.DateTimeOffset](xref:System.DateTimeOffset) prend en charge quatre méthodes qui vous permettent de convertir la représentation sous forme de chaîne d’une date et d’une heure en une valeur [DateTimeOffset](xref:System.DateTimeOffset) :</span><span class="sxs-lookup"><span data-stu-id="e8a03-145">The [System.DateTimeOffset](xref:System.DateTimeOffset) type supports four methods that allow you to convert the string representation of a date and time into a [DateTimeOffset](xref:System.DateTimeOffset) value:</span></span>

* <span data-ttu-id="e8a03-146">[Parse](xref:System.DateTimeOffset.Parse(System.String)), qui essaie de convertir la représentation sous forme de chaîne d’une date et d’une heure en une valeur [DateTimeOffset](xref:System.DateTimeOffset) et lève une exception si la conversion échoue.</span><span class="sxs-lookup"><span data-stu-id="e8a03-146">[Parse](xref:System.DateTimeOffset.Parse(System.String)), which tries to convert the string representation of a date and time to a [DateTimeOffset](xref:System.DateTimeOffset) value and throws an exception if the conversion fails.</span></span>

* <span data-ttu-id="e8a03-147">[TryParse](xref:System.DateTimeOffset.TryParse(System.String,System.DateTimeOffset@)), qui essaie de convertir la représentation sous forme de chaîne d’une date et d’une heure en une valeur [DateTimeOffset](xref:System.DateTimeOffset) et retourne `false` si la conversion échoue.</span><span class="sxs-lookup"><span data-stu-id="e8a03-147">[TryParse](xref:System.DateTimeOffset.TryParse(System.String,System.DateTimeOffset@)), which tries to convert the string representation of a date and time to a [DateTimeOffset](xref:System.DateTimeOffset) value and returns `false` if the conversion fails.</span></span>

* <span data-ttu-id="e8a03-148">[ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)), qui essaie de convertir la représentation sous forme de chaîne d’une date et d’une heure dans un format spécifié en une valeur [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="e8a03-148">[ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)), which tries to convert the string representation of a date and time in a specified format to a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> <span data-ttu-id="e8a03-149">La méthode lève une exception si la conversion échoue.</span><span class="sxs-lookup"><span data-stu-id="e8a03-149">The method throws an exception if the conversion fails.</span></span>

* <span data-ttu-id="e8a03-150">[TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)), qui essaie de convertir la représentation sous forme de chaîne d’une date et d’une heure dans un format spécifié en une valeur [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="e8a03-150">[TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)), which tries to convert the string representation of a date and time in a specified format to a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> <span data-ttu-id="e8a03-151">La méthode retourne `false` si la conversion échoue.</span><span class="sxs-lookup"><span data-stu-id="e8a03-151">The method returns `false` if the conversion fails.</span></span>

<span data-ttu-id="e8a03-152">L’exemple suivant illustre des appels à ces quatre méthodes de conversion de chaîne pour instancier une valeur [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="e8a03-152">The following example illustrates calls to each of these four string conversion methods to instantiate a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e8a03-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8a03-153">See Also</span></span>

[<span data-ttu-id="e8a03-154">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="e8a03-154">Dates, times, and time zones</span></span>](index.md)


