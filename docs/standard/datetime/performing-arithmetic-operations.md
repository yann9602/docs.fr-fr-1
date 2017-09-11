---
title: "Exécution d’opérations arithmétiques avec des dates et heures"
description: "Exécution d’opérations arithmétiques avec des dates et heures"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 589ac5ec-8365-4a0d-bc38-72183718110c
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: b872cc4c2b799ddafc9df263795d860754d1ec17
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="performing-arithmetic-operations-with-dates-and-times"></a><span data-ttu-id="b16f2-104">Exécution d’opérations arithmétiques avec des dates et heures</span><span class="sxs-lookup"><span data-stu-id="b16f2-104">Performing arithmetic operations with dates and times</span></span>

<span data-ttu-id="b16f2-105">Même si les structures [System.DateTime](xref:System.DateTime) et [System.DateTimeOffset](xref:System.DateTimeOffset) fournissent des membres qui exécutent des opérations arithmétiques sur leurs valeurs, les résultats des opérations arithmétiques sont très différents.</span><span class="sxs-lookup"><span data-stu-id="b16f2-105">Although both the [System.DateTime](xref:System.DateTime) and the [System.DateTimeOffset](xref:System.DateTimeOffset) structures provide members that perform arithmetic operations on their values, the results of arithmetic operations are very different.</span></span> <span data-ttu-id="b16f2-106">Cet article examine ces différences, les met en rapport avec les degrés de prise en charge des fuseaux horaires dans les données de date et d’heure, et explique comment exécuter des opérations prenant pleinement en charge les fuseaux horaires à l’aide de données de date et d’heure.</span><span class="sxs-lookup"><span data-stu-id="b16f2-106">This article examines those differences, relates them to degrees of time zone awareness in date and time data, and discusses how to perform fully time zone aware operations using date and time data.</span></span>

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a><span data-ttu-id="b16f2-107">Comparaisons et opérations arithmétiques avec des valeurs DateTime</span><span class="sxs-lookup"><span data-stu-id="b16f2-107">Comparisons and Arithmetic Operations with DateTime Values</span></span>

<span data-ttu-id="b16f2-108">Les valeurs [System.DateTime](xref:System.DateTime) possèdent un degré limité de prise en charge des fuseaux horaires.</span><span class="sxs-lookup"><span data-stu-id="b16f2-108">[System.DateTime](xref:System.DateTime) values possess a limited degree of time zone awareness.</span></span> <span data-ttu-id="b16f2-109">La propriété [DateTime.Kind](xref:System.DateTime.Kind) permet d’assigner une valeur [System.DateTimeKind](xref:System.DateTimeKind) à la date et à l’heure pour indiquer si elle représente l’heure locale, le temps universel coordonné (UTC) ou l’heure dans un fuseau horaire non spécifié.</span><span class="sxs-lookup"><span data-stu-id="b16f2-109">The [DateTime.Kind](xref:System.DateTime.Kind) property allows a [System.DateTimeKind](xref:System.DateTimeKind) value to be assigned to the date and time to indicate whether it represents local time, Coordinated Universal Time (UTC), or the time in an unspecified time zone.</span></span> <span data-ttu-id="b16f2-110">Toutefois, ces informations limitées de fuseau horaire sont ignorées lors de la comparaison ou de l’exécution d’opérations arithmétiques avec des dates et des heures sur des valeurs [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="b16f2-110">However, this limited time zone information is ignored when comparing or performing date and time arithmetic on [DateTime](xref:System.DateTime) values.</span></span> <span data-ttu-id="b16f2-111">Ceci est illustré dans l’exemple suivant, qui compare l’heure locale actuelle à l’heure UTC actuelle.</span><span class="sxs-lookup"><span data-stu-id="b16f2-111">The following example, which compares the current local time with the current UTC time, illustrates this.</span></span>

```csharp
using System;

public enum TimeComparison
{
   EarlierThan = -1,
   TheSameAs = 0,
   LaterThan = 1
}

public class DateManipulation
{
   public static void Main()
   {
      DateTime localTime = DateTime.Now;
      DateTime utcTime = DateTime.UtcNow;

      Console.WriteLine("Difference between {0} and {1} time: {2}:{3} hours", 
                        localTime.Kind.ToString(), 
                        utcTime.Kind.ToString(), 
                        (localTime - utcTime).Hours, 
                        (localTime - utcTime).Minutes);
      Console.WriteLine("The {0} time is {1} the {2} time.", 
                        localTime.Kind.ToString(), 
                        Enum.GetName(typeof(TimeComparison), localTime.CompareTo(utcTime)), 
                        utcTime.Kind.ToString());  
   }
}
// If run in the U.S. Pacific Standard Time zone, the example displays 
// the following output to the console:
//    Difference between Local and Utc time: -7:0 hours
//    The Local time is EarlierThan the Utc time.
```

```vb
Public Enum TimeComparison As Integer
   EarlierThan = -1
   TheSameAs = 0
   LaterThan = 1
End Enum

Module DateManipulation
   Public Sub Main()
      Dim localTime As Date = Date.Now
      Dim utcTime As Date = Date.UtcNow

      Console.WriteLine("Difference between {0} and {1} time: {2}:{3} hours", _
                        localTime.Kind.ToString(), _
                        utcTime.Kind.ToString(), _
                        (localTime - utcTime).Hours, _
                        (localTime - utcTime).Minutes)
      Console.WriteLine("The {0} time is {1} the {2} time.", _
                        localTime.Kind.ToString(), _ 
                        [Enum].GetName(GetType(TimeComparison), localTime.CompareTo(utcTime)), _
                        utcTime.Kind.ToString())  
      ' If run in the U.S. Pacific Standard Time zone, the example displays 
      ' the following output to the console:
      '    Difference between Local and Utc time: -7:0 hours
      '    The Local time is EarlierThan the Utc time.                                                    
   End Sub
End Module
```

<span data-ttu-id="b16f2-112">La méthode [DateTime.CompareTo(DateTime, DateTime)](xref:System.DateTime.Compare(System.DateTime,System.DateTime)) signale que l’heure locale est antérieure (ou inférieure) à l’heure UTC, et l’opération de soustraction indique que la différence entre l’heure UTC et l’heure locale pour un système dans le fuseau horaire du Pacifique est de sept heures.</span><span class="sxs-lookup"><span data-stu-id="b16f2-112">The [DateTime.CompareTo(DateTime, DateTime)](xref:System.DateTime.Compare(System.DateTime,System.DateTime)) method reports that the local time is earlier than (or less than) the UTC time, and the subtraction operation indicates that the difference between UTC and the local time for a system in the U.S. Pacific Standard Time zone is seven hours.</span></span> <span data-ttu-id="b16f2-113">Toutefois, comme ces deux valeurs donnent des représentations différentes d’un même point dans le temps, il apparaît clairement dans ce cas que cet intervalle de temps est totalement attribuable au décalage du fuseau horaire local par rapport à l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="b16f2-113">But because these two values provide different representations of a single point in time, it is clear in this case that this time interval is completely attributable to the local time zone's offset from UTC.</span></span> 

<span data-ttu-id="b16f2-114">En règle générale, la propriété [DateTimeKind](xref:System.DateTimeKind) n’affecte pas les résultats retournés par les méthodes de comparaison et d’arithmétique [DateTime](xref:System.DateTime) (comme la comparaison de deux points identiques dans le temps l’indique), mais elle peut affecter l’interprétation de ces résultats.</span><span class="sxs-lookup"><span data-stu-id="b16f2-114">More generally, the [DateTimeKind](xref:System.DateTimeKind) property does not affect the results returned by [DateTime](xref:System.DateTime) comparison and arithmetic methods (as the comparison of two identical points in time indicates), although it can affect the interpretation of those results.</span></span> <span data-ttu-id="b16f2-115">Exemple :</span><span class="sxs-lookup"><span data-stu-id="b16f2-115">For example:</span></span>

* <span data-ttu-id="b16f2-116">Le résultat de toute opération arithmétique exécutée sur deux valeurs de date et d’heure dont les propriétés [DateTimeKind](xref:System.DateTimeKind) sont égales à [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) reflète l’intervalle de temps effectif entre ces deux valeurs.</span><span class="sxs-lookup"><span data-stu-id="b16f2-116">The result of any arithmetic operation performed on two date and time values whose [DateTimeKind](xref:System.DateTimeKind) properties both equal [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) reflects the actual time interval between the two values.</span></span> <span data-ttu-id="b16f2-117">De même, la comparaison de deux valeurs de date et d’heure de ce type indique précisément la relation entre les heures.</span><span class="sxs-lookup"><span data-stu-id="b16f2-117">Similarly, the comparison of two such date and time values accurately reflects the relationship between times.</span></span>

* <span data-ttu-id="b16f2-118">Le résultat de toute opération arithmétique ou de comparaison exécutée sur deux valeurs de date et d’heure dont les propriétés [DateTimeKind](xref:System.DateTimeKind) sont égales à [DateTimeKind.Local](xref:System.DateTimeKind.Local) ou sur deux valeurs de date et d’heure dont les propriétés [DateTimeKind](xref:System.DateTimeKind) ont des valeurs différentes reflète la différence de temps horloge entre ces deux valeurs.</span><span class="sxs-lookup"><span data-stu-id="b16f2-118">The result of any arithmetic or comparison operation performed on two date and time values whose [DateTimeKind](xref:System.DateTimeKind) properties both equal [DateTimeKind.Local](xref:System.DateTimeKind.Local) or on two date and time values with different [DateTimeKind](xref:System.DateTimeKind) property values reflects the difference in clock time between the two values.</span></span> 

* <span data-ttu-id="b16f2-119">Les opérations arithmétiques ou de comparaison sur des valeurs de date et d’heure locales ne prennent pas en compte le fait qu’une valeur particulière soit ambiguë ou non valide, ni l’incidence de règles d’ajustement quelconques résultant du passage du fuseau horaire local à l’heure d’été ou à l’heure d’hiver.</span><span class="sxs-lookup"><span data-stu-id="b16f2-119">Arithmetic or comparison operations on local date and time values do not consider whether a particular value is ambiguous or invalid, nor do they take account of the effect of any adjustment rules that result from the local time zone's transition to or from daylight saving time.</span></span>

* <span data-ttu-id="b16f2-120">Toute opération qui compare ou calcule la différence entre l’heure UTC et une heure locale inclut dans le résultat un intervalle de temps égal au décalage du fuseau horaire local par rapport à l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="b16f2-120">Any operation that compares or calculates the difference between UTC and a local time includes a time interval equal to the local time zone's offset from UTC in the result.</span></span> 

* <span data-ttu-id="b16f2-121">Toute opération qui compare ou calcule la différence entre une heure non spécifiée et l’heure UTC ou l’heure locale reflète le temps horloge simple.</span><span class="sxs-lookup"><span data-stu-id="b16f2-121">Any operation that compares or calculates the difference between an unspecified time and either UTC or the local time reflects simple clock time.</span></span> <span data-ttu-id="b16f2-122">Les décalages entre les fuseaux horaires ne sont pas pris en compte et le résultat ne reflète pas l’application des règles d’ajustement des fuseaux horaires.</span><span class="sxs-lookup"><span data-stu-id="b16f2-122">Time zone differences are not considered, and the result does not reflect the application of time zone adjustment rules.</span></span> 

* <span data-ttu-id="b16f2-123">Toute opération qui compare ou calcule la différence entre deux heures non spécifiées peut inclure un intervalle inconnu qui reflète la différence d’heure entre deux fuseaux horaires différents.</span><span class="sxs-lookup"><span data-stu-id="b16f2-123">Any operation that compares or calculates the difference between two unspecified times may include an unknown interval that reflects the difference between the time in two different time zones.</span></span>

<span data-ttu-id="b16f2-124">Il existe de nombreux scénarios dans lesquels les différences entre les fuseaux horaires n’affectent pas les calculs des dates et des heures ou dans lesquels le contexte des données de date et d’heure définit la signification des opérations arithmétiques ou de comparaison.</span><span class="sxs-lookup"><span data-stu-id="b16f2-124">There are many scenarios in which time zone differences do not affect date and time calculations or in which the context of the date and time data defines the meaning of comparison or arithmetic operations.</span></span> <span data-ttu-id="b16f2-125">Pour une présentation de certains d’entre eux, consultez [Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](choosing-between-datetime.md).</span><span class="sxs-lookup"><span data-stu-id="b16f2-125">For a discussion of some of these, see [Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](choosing-between-datetime.md).</span></span>

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a><span data-ttu-id="b16f2-126">Comparaisons et opérations arithmétiques avec des valeurs DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="b16f2-126">Comparisons and Arithmetic Operations with DateTimeOffset Values</span></span>

<span data-ttu-id="b16f2-127">Une valeur [System.DateTimeOffset](xref:System.DateTimeOffset) inclut non seulement une date et une heure, mais également un décalage qui définit clairement cette date et cette heure par rapport à l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="b16f2-127">A [System.DateTimeOffset](xref:System.DateTimeOffset) value includes not only a date and time, but also an offset that unambiguously defines that date and time relative to UTC.</span></span> <span data-ttu-id="b16f2-128">Cela permet de définir une égalité d’une manière quelque peu différente de celle des valeurs [System.DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="b16f2-128">This makes it possible to define equality somewhat differently than for [System.DateTime](xref:System.DateTime) values.</span></span> <span data-ttu-id="b16f2-129">Les valeurs [DateTime](xref:System.DateTime) sont égales lorsqu’elles ont la même valeur de date et d’heure, alors que les valeurs [DateTimeOffset](xref:System.DateTimeOffset) sont égales lorsqu’elles font toutes les deux référence au même point dans le temps.</span><span class="sxs-lookup"><span data-stu-id="b16f2-129">Whereas [DateTime](xref:System.DateTime) values are equal if they have the same date and time value, [DateTimeOffset](xref:System.DateTimeOffset) values are equal if they both refer to the same point in time.</span></span> <span data-ttu-id="b16f2-130">Une valeur [DateTimeOffset](xref:System.DateTimeOffset) est de ce fait plus précise et nécessite une interprétation moindre lorsqu’elle est utilisée dans des comparaisons ou dans la plupart des opérations arithmétiques qui déterminent l’intervalle entre deux dates et heures.</span><span class="sxs-lookup"><span data-stu-id="b16f2-130">This makes a [DateTimeOffset](xref:System.DateTimeOffset) value more accurate and less in need of interpretation when used in comparisons and in most arithmetic operations that determine the interval between two dates and times.</span></span> <span data-ttu-id="b16f2-131">Cette différence de comportement est illustrée dans l’exemple suivant, qui est l’équivalent [DateTimeOffset](xref:System.DateTimeOffset) de l’exemple précédent, qui comparait des valeurs DateTime d’heure locale et d’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="b16f2-131">The following example, which is the [DateTimeOffset](xref:System.DateTimeOffset) equivalent to the previous example that compared local and UTC DateTime values, illustrates this difference in behavior.</span></span>

```csharp
using System;

public enum TimeComparison
{
   EarlierThan = -1,
   TheSameAs = 0,
   LaterThan = 1
}

public class DateTimeOffsetManipulation
{
   public static void Main()
   {
      DateTimeOffset localTime = DateTimeOffset.Now;
      DateTimeOffset utcTime = DateTimeOffset.UtcNow;

      Console.WriteLine("Difference between local time and UTC: {0}:{1:D2} hours", 
                        (localTime - utcTime).Hours, 
                        (localTime - utcTime).Minutes);
      Console.WriteLine("The local time is {0} UTC.", 
                        Enum.GetName(typeof(TimeComparison), localTime.CompareTo(utcTime)));  
   }
}
// Regardless of the local time zone, the example displays 
// the following output to the console:
//    Difference between local time and UTC: 0:00 hours.
//    The local time is TheSameAs UTC.
```

```vb
Public Enum TimeComparison As Integer
   EarlierThan = -1
   TheSameAs = 0
   LaterThan = 1
End Enum

Module DateTimeOffsetManipulation
   Public Sub Main()
      Dim localTime As DateTimeOffset = DateTimeOffset.Now
      Dim utcTime As DateTimeOffset = DateTimeOffset.UtcNow

      Console.WriteLine("Difference between local time and UTC: {0}:{1:D2} hours.", _
                        (localTime - utcTime).Hours, _
                        (localTime - utcTime).Minutes)
      Console.WriteLine("The local time is {0} UTC.", _
                        [Enum].GetName(GetType(TimeComparison), localTime.CompareTo(utcTime)))  
   End Sub
End Module
' Regardless of the local time zone, the example displays 
' the following output to the console:
'    Difference between local time and UTC: 0:00 hours.
'    The local time is TheSameAs UTC.
'          Console.WriteLine(e.GetType().Name)
```

<span data-ttu-id="b16f2-132">Dans cet exemple, la méthode [DateTimeOffset.CompareTo](xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)) indique que l’heure locale actuelle et l’heure UTC actuelle sont égales, et la soustraction des valeurs [DateTimeOffset](xref:System.DateTimeOffset) indique que la différence entre les deux heures est [TimeSpan.Zero](xref:System.TimeSpan.Zero).</span><span class="sxs-lookup"><span data-stu-id="b16f2-132">In this example, the [DateTimeOffset.CompareTo](xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)) method indicates that the current local time and the current UTC time are equal, and subtraction of [DateTimeOffset](xref:System.DateTimeOffset) values indicates that the difference between the two times is [TimeSpan.Zero](xref:System.TimeSpan.Zero).</span></span> 

<span data-ttu-id="b16f2-133">L’utilisation de valeurs [DateTimeOffset](xref:System.DateTimeOffset) dans des opérations arithmétiques de date et d’heure présente une limitation majeure : les valeurs [DateTimeOffset](xref:System.DateTimeOffset) prennent partiellement en charge les fuseaux horaires, et non pas pleinement.</span><span class="sxs-lookup"><span data-stu-id="b16f2-133">The chief limitation of using [DateTimeOffset](xref:System.DateTimeOffset) values in date and time arithmetic is that although [DateTimeOffset](xref:System.DateTimeOffset) values have some time zone awareness, they are not fully time zone aware.</span></span> <span data-ttu-id="b16f2-134">Même si le décalage de la valeur [DateTimeOffset](xref:System.DateTimeOffset) reflète le décalage d’un fuseau horaire par rapport à l’heure UTC lorsqu’une valeur est assignée initialement à une variable [DateTimeOffset](xref:System.DateTimeOffset), il se dissocie par la suite du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="b16f2-134">Although the [DateTimeOffset](xref:System.DateTimeOffset) value's offset reflects a time zone's offset from UTC when a [DateTimeOffset](xref:System.DateTimeOffset) variable is first assigned a value, it becomes disassociated from the time zone thereafter.</span></span> <span data-ttu-id="b16f2-135">Comme il n’est plus directement associé à une heure identifiable, l’addition et la soustraction d’intervalles de dates et d’heures ne prennent pas en compte les règles d’ajustement des fuseaux horaires.</span><span class="sxs-lookup"><span data-stu-id="b16f2-135">Because it is no longer directly associated with an identifiable time, the addition and subtraction of date and time intervals does not consider a time zone's adjustment rules.</span></span> 

<span data-ttu-id="b16f2-136">Pour illustrer cela, la passage à l’heure d’été dans le fuseau horaire du Centre (États-Unis) se produit à 2:00,</span><span class="sxs-lookup"><span data-stu-id="b16f2-136">To illustrate, the transition to daylight saving time in the U.S. Central Standard Time zone occurs at 2:00 A.M.</span></span> <span data-ttu-id="b16f2-137">le 9 mars 2008.</span><span class="sxs-lookup"><span data-stu-id="b16f2-137">on March 9, 2008.</span></span> <span data-ttu-id="b16f2-138">Cela signifie que l’ajout d’un intervalle de deux heures trente à l’heure de 1:30 dans le fuseau horaire du Centre des États-Unis,</span><span class="sxs-lookup"><span data-stu-id="b16f2-138">This means that adding a two and a half hour interval to a Central Standard time of 1:30 A.M.</span></span> <span data-ttu-id="b16f2-139">le 9 mars 2008, doit avoir pour résultat 5:00,</span><span class="sxs-lookup"><span data-stu-id="b16f2-139">on March 9, 2008, should produce a date and time of 5:00 A.M.</span></span> <span data-ttu-id="b16f2-140">le 9 mars 2008.</span><span class="sxs-lookup"><span data-stu-id="b16f2-140">on March 9, 2008.</span></span> <span data-ttu-id="b16f2-141">Toutefois, comme le montre l’exemple suivant, le résultat de l’addition est 4:00,</span><span class="sxs-lookup"><span data-stu-id="b16f2-141">However, as the following example shows, the result of the addition is 4:00 A.M.</span></span> <span data-ttu-id="b16f2-142">le 9 mars 2008.</span><span class="sxs-lookup"><span data-stu-id="b16f2-142">on March 9, 2008.</span></span> <span data-ttu-id="b16f2-143">Notez que le résultat de cette opération représente l’heure correcte, même s’il ne s’agit pas de l’heure dans le fuseau horaire qui nous intéresse (autrement dit, elle n’a pas le décalage horaire attendu).</span><span class="sxs-lookup"><span data-stu-id="b16f2-143">Note that this result of this operation does represent the correct point in time, although it is not the time in the time zone in which we are interested (that is, it does not have the expected time zone offset).</span></span>

```csharp
using System;

public class IntervalArithmetic
{
   public static void Main()
   {
      DateTime generalTime = new DateTime(2008, 3, 9, 1, 30, 0);
      const string tzName = "Central Standard Time";
      TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

      // Instantiate DateTimeOffset value to have correct CST offset
      try
      {
         DateTimeOffset centralTime1 = new DateTimeOffset(generalTime, 
                    TimeZoneInfo.FindSystemTimeZoneById(tzName).GetUtcOffset(generalTime));

         // Add two and a half hours      
         DateTimeOffset centralTime2 = centralTime1.Add(twoAndAHalfHours);
         // Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, 
                                                    twoAndAHalfHours.ToString(), 
                                                    centralTime2);  
      }
      catch (TimeZoneNotFoundException)
      {
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.");
      }
   }
}
// The example displays the following output to the console:
//    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 4:00:00 AM -06:00
```

```vb
Module IntervalArithmetic
   Public Sub Main()
      Dim generalTime As Date = #03/09/2008 1:30AM#
      Const tzName As String = "Central Standard Time"
      Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

      ' Instantiate DateTimeOffset value to have correct CST offset
      Try
         Dim centralTime1 As New DateTimeOffset(generalTime, _
                    TimeZoneInfo.FindSystemTimeZoneById(tzName).GetUtcOffset(generalTime))

         ' Add two and a half hours      
         Dim centralTime2 As DateTimeOffset = centralTime1.Add(twoAndAHalfHours)
         ' Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, _
                                                    twoAndAHalfHours.ToString(), _
                                                    centralTime2)   
      Catch e As TimeZoneNotFoundException
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.")
      End Try
   End Sub
End Module
' The example displays the following output to the console:
'    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 4:00:00 AM -06:00
```

## <a name="arithmetic-operations-with-times-in-time-zones"></a><span data-ttu-id="b16f2-144">Opérations arithmétiques avec des heures dans des fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="b16f2-144">Arithmetic Operations with Times in Time Zones</span></span>

<span data-ttu-id="b16f2-145">La classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) ne fournit aucune méthode appliquant automatiquement des règles d’ajustement lorsque vous effectuez des opérations arithmétiques de date et d’heure.</span><span class="sxs-lookup"><span data-stu-id="b16f2-145">The [System.TimeZoneInfo](xref:System.TimeZoneInfo) class does not provide any methods that automatically apply adjustment rules when you perform date and time arithmetic.</span></span> <span data-ttu-id="b16f2-146">Toutefois, vous pouvez convertir l’heure d’un fuseau horaire en heure UTC, effectuer l’opération arithmétique, puis reconvertir l’heure UTC dans l’heure du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="b16f2-146">However, you can do this by converting the time in a time zone to UTC, performing the arithmetic operation, and then converting from UTC back to the time in the time zone.</span></span> <span data-ttu-id="b16f2-147">Pour plus d’informations, consultez [Guide pratique : utiliser des fuseaux horaires dans des opérations arithmétiques de date et d’heure](use-time-zones-in-arithmetic.md).</span><span class="sxs-lookup"><span data-stu-id="b16f2-147">For details, see [How to: Use Time Zones in Date and Time Arithmetic](use-time-zones-in-arithmetic.md).</span></span>

<span data-ttu-id="b16f2-148">Par exemple, le code suivant est semblable au code précédent qui ajoutait deux heures trente à 2:00,</span><span class="sxs-lookup"><span data-stu-id="b16f2-148">For example, the following code is similar to the previous code that added two-and-a-half hours to 2:00 A.M.</span></span> <span data-ttu-id="b16f2-149">le 9 mars 2008.</span><span class="sxs-lookup"><span data-stu-id="b16f2-149">on March 9, 2008.</span></span> <span data-ttu-id="b16f2-150">Toutefois, comme il convertit l’heure du Centre des États-Unis en heure UTC avant d’effectuer les opérations arithmétiques de date et d’heure, puis reconvertit le résultat UTC en heure du Centre, l’heure résultante reflète le passage du fuseau horaire du Centre des États-Unis à l’heure d’été.</span><span class="sxs-lookup"><span data-stu-id="b16f2-150">However, because it converts a Central Standard time to UTC before it performs date and time arithmetic, and then converts the result from UTC back to Central Standard time, the resulting time reflects the Central Standard Time Zone's transition to daylight saving time.</span></span>

```csharp
using System;

public class TimeZoneAwareArithmetic
{
   public static void Main()
   {
      const string tzName = "Central Standard Time";

      DateTime generalTime = new DateTime(2008, 3, 9, 1, 30, 0);
      TimeZoneInfo cst = TimeZoneInfo.FindSystemTimeZoneById(tzName);
      TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

      // Instantiate DateTimeOffset value to have correct CST offset
      try
      {
         DateTimeOffset centralTime1 = new DateTimeOffset(generalTime, 
                                       cst.GetUtcOffset(generalTime));

         // Add two and a half hours
         DateTimeOffset utcTime = centralTime1.ToUniversalTime();
         utcTime += twoAndAHalfHours;

         DateTimeOffset centralTime2 = TimeZoneInfo.ConvertTime(utcTime, cst);
         // Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, 
                                                    twoAndAHalfHours.ToString(), 
                                                    centralTime2);  
      }
      catch (TimeZoneNotFoundException)
      {
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.");
      }
   }
}
// The example displays the following output to the console:
//    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 5:00:00 AM -05:00
```

```vb
Module TimeZoneAwareArithmetic
   Public Sub Main()
      Const tzName As String = "Central Standard Time"

      Dim generalTime As Date = #03/09/2008 1:30AM#
      Dim cst As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(tzName) 
      Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

      ' Instantiate DateTimeOffset value to have correct CST offset
      Try
         Dim centralTime1 As New DateTimeOffset(generalTime, _
                    cst.GetUtcOffset(generalTime))

         ' Add two and a half hours 
         Dim utcTime As DateTimeOffset = centralTime1.ToUniversalTime()
         utcTime += twoAndAHalfHours

         Dim centralTime2 As DateTimeOffset = TimeZoneInfo.ConvertTime(utcTime, cst)
         ' Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, _
                                                    twoAndAHalfHours.ToString(), _
                                                    centralTime2)   
      Catch e As TimeZoneNotFoundException
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.")
      End Try
   End Sub
End Module
' The example displays the following output to the console:
'    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 5:00:00 AM -05:00
```

## <a name="see-also"></a><span data-ttu-id="b16f2-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b16f2-151">See Also</span></span>

[<span data-ttu-id="b16f2-152">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="b16f2-152">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="b16f2-153">Guide pratique pour utiliser des fuseaux horaires dans des opérations arithmétiques de date et d’heure</span><span class="sxs-lookup"><span data-stu-id="b16f2-153">How to: use time zones in date and time arithmetic</span></span>](use-time-zones-in-arithmetic.md)



