---
title: Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo
description: Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/11/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 2dd84ee8-9f0f-4054-9537-155857a460cd
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: aeb1928be32584ee4b6acf7c9a4f4330daedc590
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a><span data-ttu-id="f5984-104">Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="f5984-104">Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>

<span data-ttu-id="f5984-105">Les applications .NET qui utilisent des informations de date et d’heure sont très diverses et peuvent utiliser ces informations de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="f5984-105">.NET applications that use date and time information are very diverse and can use that information in several ways.</span></span> <span data-ttu-id="f5984-106">Les utilisations les plus courantes des informations de date et d'heure sont une ou plusieurs parmi les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5984-106">The more common uses of date and time information include one or more of the following:</span></span>

* <span data-ttu-id="f5984-107">Pour refléter seulement une date, les informations d'heure n'étant pas importantes.</span><span class="sxs-lookup"><span data-stu-id="f5984-107">To reflect a date only, so that time information is not important.</span></span>

* <span data-ttu-id="f5984-108">Pour refléter seulement une heure, les informations de date n'étant pas importantes.</span><span class="sxs-lookup"><span data-stu-id="f5984-108">To reflect a time only, so that date information is not important.</span></span>

* <span data-ttu-id="f5984-109">Pour refléter une date et une heure abstraites, qui ne sont pas liées à un moment et un endroit spécifiques (par exemple, la plupart des magasins d'une chaîne internationale ouvrent en semaine à 9h00).</span><span class="sxs-lookup"><span data-stu-id="f5984-109">To reflect an abstract date and time that is not tied to a specific time and place (for example, most stores in an international chain open on weekdays at 9:00 A.M.).</span></span>

* <span data-ttu-id="f5984-110">Pour récupérer des informations de date et d’heure à partir de sources externes à l’application .NET, en général lorsque les informations de date et d’heure sont stockées dans un type de données simple.</span><span class="sxs-lookup"><span data-stu-id="f5984-110">To retrieve date and time information from sources outside of the .NET application, typically where date and time information is stored in a simple data type.</span></span>

* <span data-ttu-id="f5984-111">Pour identifier de façon univoque et non ambiguë un point unique dans le temps.</span><span class="sxs-lookup"><span data-stu-id="f5984-111">To uniquely and unambiguously identify a single point in time.</span></span> <span data-ttu-id="f5984-112">Certaines applications requièrent qu'une date/heure soit ambiguë seulement sur le système hôte. D'autres requièrent qu'elle soit non ambiguë entre les systèmes (autrement dit, une date sérialisée sur un système peut être désérialisée de manière significative et utilisée sur un autre système n'importe où dans le monde).</span><span class="sxs-lookup"><span data-stu-id="f5984-112">Some applications require that a date and time be unambiguous only on the host system; others require that it be unambiguous across systems (that is, a date serialized on one system can be meaningfully deserialized and used on another system anywhere in the world).</span></span> 

* <span data-ttu-id="f5984-113">Pour conserver plusieurs dates/heures ayant un lien les unes avec les autres (comme la date/heure locale du demandeur et la date/heure de réception par le serveur d'une demande web).</span><span class="sxs-lookup"><span data-stu-id="f5984-113">To preserve multiple related times (such as the requestor's local time and the server's time of receipt for a Web request).</span></span>

* <span data-ttu-id="f5984-114">Pour effectuer des calculs de date et d'heure, éventuellement avec un résultat qui identifie de façon univoque et non ambiguë un point unique dans le temps.</span><span class="sxs-lookup"><span data-stu-id="f5984-114">To perform date and time arithmetic, possibly with a result that uniquely and unambiguously identifies a single point in time.</span></span> 

<span data-ttu-id="f5984-115">.NET inclut les types [System.DateTime](xref:System.DateTime), [System.DateTimeOffset](xref:System.DateTimeOffset), [System.TimeSpan](xref:System.TimeSpan) et [System.TimeZoneInfo](xref:System.TimeZoneInfo), qui permettent tous de créer des applications qui fonctionnent avec des dates et des heures.</span><span class="sxs-lookup"><span data-stu-id="f5984-115">.NET includes the [System.DateTime](xref:System.DateTime), [System.DateTimeOffset](xref:System.DateTimeOffset), [System.TimeSpan](xref:System.TimeSpan), and [System.TimeZoneInfo](xref:System.TimeZoneInfo) types, all of which can be used to build applications that work with dates and times.</span></span> 

> [!NOTE]
> <span data-ttu-id="f5984-116">Cette rubrique ne traite pas du type `TimeZone` plus ancien, car ses fonctionnalités sont presque totalement intégrées dans la classe [System.TimeZoneInfo](xref:System.TimeZoneInfo).</span><span class="sxs-lookup"><span data-stu-id="f5984-116">This topic does not discuss the older `TimeZone` type, because its functionality is almost entirely incorporated in the [System.TimeZoneInfo](xref:System.TimeZoneInfo) class.</span></span> <span data-ttu-id="f5984-117">Chaque fois que possible, les développeurs doivent utiliser la classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) à la place de la classe `TimeZone`.</span><span class="sxs-lookup"><span data-stu-id="f5984-117">Whenever possible, developers should use the [System.TimeZoneInfo](xref:System.TimeZoneInfo) class instead of the `TimeZone` class.</span></span>


## <a name="the-datetime-structure"></a><span data-ttu-id="f5984-118">La structure DateTime</span><span class="sxs-lookup"><span data-stu-id="f5984-118">The DateTime structure</span></span>

<span data-ttu-id="f5984-119">Une valeur [System.DateTime](xref:System.DateTime) définit une date et une heure spécifiques.</span><span class="sxs-lookup"><span data-stu-id="f5984-119">A [System.DateTime](xref:System.DateTime) value defines a particular date and time.</span></span> <span data-ttu-id="f5984-120">Elle inclut une propriété [Kind](xref:System.DateTime.Kind) qui fournit des informations limitées sur le fuseau horaire auquel appartiennent cette date et cette heure.</span><span class="sxs-lookup"><span data-stu-id="f5984-120">It includes a [Kind](xref:System.DateTime.Kind) property that provides limited information about the time zone to which that date and time belongs.</span></span> <span data-ttu-id="f5984-121">La valeur [DateTimeKind](xref:System.DateTimeKind) retournée par la propriété [Kind](xref:System.DateTime.Kind) indique si la valeur [DateTime](xref:System.DateTime) représente l’heure locale [DateTimeKind.Local](xref:System.DateTimeKind.Local), le temps universel coordonné (UTC) [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) ou une heure non spécifiée [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified).</span><span class="sxs-lookup"><span data-stu-id="f5984-121">The [DateTimeKind](xref:System.DateTimeKind) value returned by the [Kind](xref:System.DateTime.Kind) property indicates whether the [DateTime](xref:System.DateTime) value represents the local time [DateTimeKind.Local](xref:System.DateTimeKind.Local)), Coordinated Universal Time (UTC) [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), or an unspecified time [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified).</span></span>

<span data-ttu-id="f5984-122">La structure [DateTime](xref:System.DateTime) convient pour les applications qui :</span><span class="sxs-lookup"><span data-stu-id="f5984-122">The [DateTime](xref:System.DateTime) structure is suitable for applications that do the following:</span></span> 

* <span data-ttu-id="f5984-123">Utilisent seulement des dates.</span><span class="sxs-lookup"><span data-stu-id="f5984-123">Work with dates only.</span></span>

* <span data-ttu-id="f5984-124">Utilisent seulement des heures.</span><span class="sxs-lookup"><span data-stu-id="f5984-124">Work with times only.</span></span>

* <span data-ttu-id="f5984-125">Utilisent des dates et des heures abstraites.</span><span class="sxs-lookup"><span data-stu-id="f5984-125">Work with abstract dates and times.</span></span>

* <span data-ttu-id="f5984-126">Utilisent des dates et des heures pour lesquelles les informations de fuseau horaire sont manquantes.</span><span class="sxs-lookup"><span data-stu-id="f5984-126">Work with dates and times for which time zone information is missing.</span></span> 

* <span data-ttu-id="f5984-127">Utilisent seulement des dates et des heures UTC.</span><span class="sxs-lookup"><span data-stu-id="f5984-127">Work with UTC dates and times only.</span></span> 

* <span data-ttu-id="f5984-128">Récupèrent des informations de date et d’heure auprès de sources externes au .NET Framework, comme des bases de données SQL.</span><span class="sxs-lookup"><span data-stu-id="f5984-128">Retrieve date and time information from sources outside the .NET Framework, such as SQL databases.</span></span> <span data-ttu-id="f5984-129">En règle générale, ces sources stockent les informations de date et d’heure dans un format simple qui est compatible avec la structure [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="f5984-129">Typically, these sources store date and time information in a simple format that is compatible with the [DateTime](xref:System.DateTime) structure.</span></span>

* <span data-ttu-id="f5984-130">Effectuent des calculs de dates et d'heures, mais sont surtout concernées par des résultats d'ordre général.</span><span class="sxs-lookup"><span data-stu-id="f5984-130">Perform date and time arithmetic, but are concerned with general results.</span></span> <span data-ttu-id="f5984-131">Par exemple, dans une opération d'addition qui ajoute six mois à une date/heure, il n'est souvent pas important que le résultat soit ajusté pour l'heure d'été.</span><span class="sxs-lookup"><span data-stu-id="f5984-131">For example, in an addition operation that adds six months to a particular date and time, it is often not important whether the result is adjusted for daylight saving time.</span></span>

<span data-ttu-id="f5984-132">Sauf si une valeur [DateTime](xref:System.DateTime) particulière représente le temps UTC, cette valeur de date et d’heure est souvent ambiguë ou limitée en termes de portabilité.</span><span class="sxs-lookup"><span data-stu-id="f5984-132">Unless a particular [DateTime](xref:System.DateTime) value represents UTC, that date and time value is often ambiguous or limited in its portability.</span></span> <span data-ttu-id="f5984-133">Par exemple, si une valeur [DateTime](xref:System.DateTime) représente l’heure locale, elle est portable dans ce fuseau horaire local (c’est-à-dire que si la valeur est désérialisée sur un autre système dans le même fuseau horaire, cette valeur continue d’identifier de façon non ambiguë un point unique dans le temps).</span><span class="sxs-lookup"><span data-stu-id="f5984-133">For example, if a [DateTime](xref:System.DateTime) value represents the local time, it is portable within that local time zone (that is, if the value is deserialized on another system in the same time zone, that value still unambiguously identifies a single point in time).</span></span> <span data-ttu-id="f5984-134">En dehors du fuseau horaire local, cette valeur [DateTime](xref:System.DateTime) peut être interprétée de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="f5984-134">Outside the local time zone, that [DateTime](xref:System.DateTime) value can have multiple interpretations.</span></span> <span data-ttu-id="f5984-135">Si la propriété [Kind](xref:System.DateTime.Kind) de la valeur est [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), elle est encore moins portable : elle est maintenant ambiguë dans le même fuseau horaire, voire même sur le système où elle a été sérialisée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="f5984-135">If the value's [Kind](xref:System.DateTime.Kind) property is [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), it is even less portable: it is now ambiguous within the same time zone and possibly even on the same system on which it was first serialized.</span></span> <span data-ttu-id="f5984-136">Seulement dans le cas où une valeur [DateTime](xref:System.DateTime) représente le temps UTC, celle-ci identifie de façon non ambiguë un point unique dans le temps, indépendamment du système ou du fuseau horaire où la valeur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="f5984-136">Only if a [DateTime](xref:System.DateTime) value represents UTC does that value unambiguously identify a single point in time regardless of the system or time zone in which the value is used.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f5984-137">Lors de l’enregistrement ou du partage de données [DateTime](xref:System.DateTime), le temps UTC doit être utilisé et la propriété [Kind](xref:System.DateTime.Kind) de la valeur [DateTime](xref:System.DateTime) doit être définie sur [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span><span class="sxs-lookup"><span data-stu-id="f5984-137">When saving or sharing [DateTime](xref:System.DateTime) data, UTC should be used and the [DateTime](xref:System.DateTime) value's [Kind](xref:System.DateTime.Kind) property should be set to [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span></span>

## <a name="the-datetimeoffset-structure"></a><span data-ttu-id="f5984-138">La structure DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="f5984-138">The DateTimeOffset structure</span></span>

<span data-ttu-id="f5984-139">La structure [System.DateTimeOffset](xref:System.DateTimeOffset) représente une valeur de date et d’heure, ainsi qu’un décalage qui indique de combien cette valeur diffère du temps UTC.</span><span class="sxs-lookup"><span data-stu-id="f5984-139">The [System.DateTimeOffset](xref:System.DateTimeOffset) structure represents a date and time value, together with an offset that indicates how much that value differs from UTC.</span></span> <span data-ttu-id="f5984-140">Ainsi, la valeur toujours identifie toujours de façon non ambiguë un point unique dans le temps.</span><span class="sxs-lookup"><span data-stu-id="f5984-140">Thus, the value always unambiguously identifies a single point in time.</span></span> 

<span data-ttu-id="f5984-141">Le type [DateTimeOffset](xref:System.DateTimeOffset) comprend toutes les fonctionnalités du type [DateTime](xref:System.DateTime), ainsi que la gestion des fuseaux horaires.</span><span class="sxs-lookup"><span data-stu-id="f5984-141">The [DateTimeOffset](xref:System.DateTimeOffset) type includes all of the functionality of the [DateTime](xref:System.DateTime) type along with time zone awareness.</span></span> <span data-ttu-id="f5984-142">Il convient donc pour les applications qui :</span><span class="sxs-lookup"><span data-stu-id="f5984-142">This makes it is suitable for applications that do the following:</span></span> 

* <span data-ttu-id="f5984-143">Identifient de façon univoque et non ambiguë un point unique dans le temps.</span><span class="sxs-lookup"><span data-stu-id="f5984-143">Uniquely and unambiguously identify a single point in time.</span></span> <span data-ttu-id="f5984-144">Le type [DateTimeOffset](xref:System.DateTimeOffset) peut être utilisé pour définir de façon non ambiguë la signification de « maintenant », pour consigner les dates/heures des transactions, pour consigner les dates/heures des événements système ou des événements d’une application, et pour enregistrer les dates/heures de création et de modification des fichiers.</span><span class="sxs-lookup"><span data-stu-id="f5984-144">The [DateTimeOffset](xref:System.DateTimeOffset) type can be used to unambiguously define the meaning of "now", to log transaction times, to log the times of system or application events, and to record file creation and modification times.</span></span> 

* <span data-ttu-id="f5984-145">Effectuent des calculs de date et d'heure.</span><span class="sxs-lookup"><span data-stu-id="f5984-145">Perform general date and time arithmetic.</span></span>

* <span data-ttu-id="f5984-146">Conservent plusieurs dates/heures ayant un lien entre elles, comme les dates/heures qui sont stockées sous la forme de deux valeurs distinctes ou de deux membres d'une structure.</span><span class="sxs-lookup"><span data-stu-id="f5984-146">Preserve multiple related times, as long as those times are stored as two separate values or as two members of a structure.</span></span>

> [!NOTE]
> <span data-ttu-id="f5984-147">Ces utilisations pour des valeurs [DateTimeOffset](xref:System.DateTimeOffset) sont beaucoup plus courantes que celles pour les valeurs [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="f5984-147">These uses for [DateTimeOffset](xref:System.DateTimeOffset) values are much more common than those for [DateTime](xref:System.DateTime) values.</span></span> <span data-ttu-id="f5984-148">Par conséquent, [DateTimeOffset](xref:System.DateTimeOffset) doit être considéré comme le type de date et d’heure par défaut pour le développement d’applications.</span><span class="sxs-lookup"><span data-stu-id="f5984-148">As a result, [DateTimeOffset](xref:System.DateTimeOffset) should be considered the default date and time type for application development.</span></span>

<span data-ttu-id="f5984-149">Une valeur [DateTimeOffset](xref:System.DateTimeOffset) n’est pas liée à un fuseau horaire particulier, mais peut provenir de n’importe quel fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="f5984-149">A [DateTimeOffset](xref:System.DateTimeOffset) value is not tied to a particular time zone, but can originate from any of a variety of time zones.</span></span> <span data-ttu-id="f5984-150">Pour illustrer cela, l’exemple suivant répertorie les fuseaux horaires auxquels plusieurs valeurs [DateTimeOffset](xref:System.DateTimeOffset) (y compris une heure locale du Pacifique) peuvent appartenir.</span><span class="sxs-lookup"><span data-stu-id="f5984-150">To illustrate this, the following example lists the time zones to which a number of [DateTimeOffset](xref:System.DateTimeOffset) values (including a local Pacific Standard Time) can belong.</span></span>

```csharp
using System;
using System.Collections.ObjectModel;

public class TimeOffsets
{
   public static void Main()
   {
      DateTime thisDate = new DateTime(2007, 3, 10, 0, 0, 0);
      DateTime dstDate = new DateTime(2007, 6, 10, 0, 0, 0);
      DateTimeOffset thisTime;

      thisTime = new DateTimeOffset(dstDate, new TimeSpan(-7, 0, 0));
      ShowPossibleTimeZones(thisTime);

      thisTime = new DateTimeOffset(thisDate, new TimeSpan(-6, 0, 0));  
      ShowPossibleTimeZones(thisTime);

      thisTime = new DateTimeOffset(thisDate, new TimeSpan(+1, 0, 0));
      ShowPossibleTimeZones(thisTime);
   }

   private static void ShowPossibleTimeZones(DateTimeOffset offsetTime)
   {
      TimeSpan offset = offsetTime.Offset;
      ReadOnlyCollection<TimeZoneInfo> timeZones;

      Console.WriteLine("{0} could belong to the following time zones:", 
                        offsetTime.ToString());
      // Get all time zones defined on local system
      timeZones = TimeZoneInfo.GetSystemTimeZones();     
      // Iterate time zones 
      foreach (TimeZoneInfo timeZone in timeZones)
      {
         // Compare offset with offset for that date in that time zone
         if (timeZone.GetUtcOffset(offsetTime.DateTime).Equals(offset))
            Console.WriteLine("   {0}", timeZone.DisplayName);
      }
      Console.WriteLine();
   } 
}
// This example displays the following output to the console:
//       6/10/2007 12:00:00 AM -07:00 could belong to the following time zones:
//          (GMT-07:00) Arizona
//          (GMT-08:00) Pacific Time (US & Canada)
//          (GMT-08:00) Tijuana, Baja California
//       
//       3/10/2007 12:00:00 AM -06:00 could belong to the following time zones:
//          (GMT-06:00) Central America
//          (GMT-06:00) Central Time (US & Canada)
//          (GMT-06:00) Guadalajara, Mexico City, Monterrey - New
//          (GMT-06:00) Guadalajara, Mexico City, Monterrey - Old
//          (GMT-06:00) Saskatchewan
//       
//       3/10/2007 12:00:00 AM +01:00 could belong to the following time zones:
//          (GMT+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna
//          (GMT+01:00) Belgrade, Bratislava, Budapest, Ljubljana, Prague
//          (GMT+01:00) Brussels, Copenhagen, Madrid, Paris
//          (GMT+01:00) Sarajevo, Skopje, Warsaw, Zagreb
//          (GMT+01:00) West Central Africa
```

```vb
Imports System.Collections.ObjectModel

Module TimeOffsets
   Public Sub Main()
      Dim thisTime As DateTimeOffset 

      thisTime = New DateTimeOffset(#06/10/2007#, New TimeSpan(-7, 0, 0))
      ShowPossibleTimeZones(thisTime) 

      thisTime = New DateTimeOffset(#03/10/2007#, New TimeSpan(-6, 0, 0))  
      ShowPossibleTimeZones(thisTime)

      thisTime = New DateTimeOffset(#03/10/2007#, New TimeSpan(+1, 0, 0))
      ShowPossibleTimeZones(thisTime)
   End Sub

   Private Sub ShowPossibleTimeZones(offsetTime As DateTimeOffset)
      Dim offset As TimeSpan = offsetTime.Offset
      Dim timeZones As ReadOnlyCollection(Of TimeZoneInfo)

      Console.WriteLine("{0} could belong to the following time zones:", _
                        offsetTime.ToString())
      ' Get all time zones defined on local system
      timeZones = TimeZoneInfo.GetSystemTimeZones()     
      ' Iterate time zones
      For Each timeZone As TimeZoneInfo In timeZones
         ' Compare offset with offset for that date in that time zone
         If timeZone.GetUtcOffset(offsetTime.DateTime).Equals(offset) Then
            Console.WriteLine("   {0}", timeZone.DisplayName)
         End If   
      Next
      Console.WriteLine()
   End Sub
End Module
' This example displays the following output to the console:
'       6/10/2007 12:00:00 AM -07:00 could belong to the following time zones:
'          (GMT-07:00) Arizona
'          (GMT-08:00) Pacific Time (US & Canada)
'          (GMT-08:00) Tijuana, Baja California
'       
'       3/10/2007 12:00:00 AM -06:00 could belong to the following time zones:
'          (GMT-06:00) Central America
'          (GMT-06:00) Central Time (US & Canada)
'          (GMT-06:00) Guadalajara, Mexico City, Monterrey - New
'          (GMT-06:00) Guadalajara, Mexico City, Monterrey - Old
'          (GMT-06:00) Saskatchewan
'       
'       3/10/2007 12:00:00 AM +01:00 could belong to the following time zones:
'          (GMT+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna
'          (GMT+01:00) Belgrade, Bratislava, Budapest, Ljubljana, Prague
'          (GMT+01:00) Brussels, Copenhagen, Madrid, Paris
'          (GMT+01:00) Sarajevo, Skopje, Warsaw, Zagreb
'          (GMT+01:00) West Central Africa
```

<span data-ttu-id="f5984-151">La sortie montre que chaque valeur de date et d'heure de cet exemple peut appartenir à au moins trois fuseaux horaires différents.</span><span class="sxs-lookup"><span data-stu-id="f5984-151">The output shows that each date and time value in this example can belong to at least three different time zones.</span></span> <span data-ttu-id="f5984-152">La valeur [DateTimeOffset](xref:System.DateTimeOffset) de 6/10/2007 indique que si une valeur de date/heure représente une heure d’été, son décalage par rapport à l’heure UTC ne correspond pas nécessairement au décalage UTC de base du fuseau horaire d’origine ni au décalage par rapport à l’heure UTC indiquée dans son nom d’affichage.</span><span class="sxs-lookup"><span data-stu-id="f5984-152">The [DateTimeOffset](xref:System.DateTimeOffset) value of 6/10/2007 shows that if a date and time value represents a daylight saving time, its offset from UTC does not even necessarily correspond to the originating time zone's base UTC offset or to the offset from UTC found in its display name.</span></span> <span data-ttu-id="f5984-153">Cela signifie que, comme une valeur [DateTimeOffset](xref:System.DateTimeOffset) individuelle n’est pas fortement couplée avec son fuseau horaire, elle ne peut pas refléter la transition d’un fuseau horaire vers et depuis l’heure d’été.</span><span class="sxs-lookup"><span data-stu-id="f5984-153">This means that, because a single [DateTimeOffset](xref:System.DateTimeOffset)  value is not tightly coupled with its time zone, it cannot reflect a time zone's transition to and from daylight saving time.</span></span> <span data-ttu-id="f5984-154">Ceci peut être particulièrement problématique quand des calculs de date et d’heure sont utilisés pour manipuler une valeur [DateTimeOffset](xref:System.DateTimeOffset).</span><span class="sxs-lookup"><span data-stu-id="f5984-154">This can be particularly problematic when date and time arithmetic is used to manipulate a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> <span data-ttu-id="f5984-155">(Pour une présentation de la façon d’effectuer des opérations arithmétiques avec des dates et des heures en prenant en compte les règles d’ajustement d’un fuseau horaire, consultez [Exécution d’opérations arithmétiques avec des dates et heures](performing-arithmetic-operations.md).</span><span class="sxs-lookup"><span data-stu-id="f5984-155">For a discussion of how to perform date and time arithmetic in a way that takes account of a time zone's adjustment rules, see [Performing arithmetic operations with dates and times](performing-arithmetic-operations.md).</span></span>

## <a name="the-timespan-structure"></a><span data-ttu-id="f5984-156">La structure TimeSpan</span><span class="sxs-lookup"><span data-stu-id="f5984-156">The TimeSpan structure</span></span>

<span data-ttu-id="f5984-157">La structure [System.TimeSpan](xref:System.TimeSpan) représente un intervalle de temps.</span><span class="sxs-lookup"><span data-stu-id="f5984-157">The [System.TimeSpan](xref:System.TimeSpan) structure represents a time interval.</span></span> <span data-ttu-id="f5984-158">Ses deux utilisations courantes sont :</span><span class="sxs-lookup"><span data-stu-id="f5984-158">Its two typical uses are:</span></span> 

* <span data-ttu-id="f5984-159">Refléter un intervalle de temps entre deux valeurs de date/heure.</span><span class="sxs-lookup"><span data-stu-id="f5984-159">Reflecting the time interval between two date and time values.</span></span> <span data-ttu-id="f5984-160">Par exemple, la soustraction d’une valeur [DateTime](xref:System.DateTime) d’une autre retourne une valeur [TimeSpan](xref:System.TimeSpan).</span><span class="sxs-lookup"><span data-stu-id="f5984-160">For example, subtracting one [DateTime](xref:System.DateTime) value from another returns a [TimeSpan](xref:System.TimeSpan) value.</span></span> 

* <span data-ttu-id="f5984-161">Mesurer un temps écoulé.</span><span class="sxs-lookup"><span data-stu-id="f5984-161">Measuring elapsed time.</span></span> <span data-ttu-id="f5984-162">Par exemple, la propriété [Stopwatch.Elapsed](xref:System.Diagnostics.Stopwatch.Elapsed) retourne une valeur [TimeSpan](xref:System.TimeSpan) qui reflète l’intervalle de temps écoulé depuis l’appel à l’une des méthodes [System.Diagnostics.Stopwatch](xref:System.Diagnostics.Stopwatch), qui commence à mesurer le temps écoulé.</span><span class="sxs-lookup"><span data-stu-id="f5984-162">For example, the [Stopwatch.Elapsed](xref:System.Diagnostics.Stopwatch.Elapsed) property returns a [TimeSpan](xref:System.TimeSpan) value that reflects the time interval that has elapsed since the call to one of the [System.Diagnostics.Stopwatch](xref:System.Diagnostics.Stopwatch) methods that begins to measure elapsed time.</span></span>

<span data-ttu-id="f5984-163">Une valeur [TimeSpan](xref:System.TimeSpan) peut également être utilisée en remplacement d’une valeur [DateTime](xref:System.DateTime) quand cette valeur reflète un moment sans référence à une heure précise de la journée.</span><span class="sxs-lookup"><span data-stu-id="f5984-163">A [TimeSpan](xref:System.TimeSpan) value can also be used as a replacement for a [DateTime](xref:System.DateTime) value when that value reflects a time without reference to a particular time of day.</span></span> <span data-ttu-id="f5984-164">Cette utilisation est similaire aux propriétés [DateTime.TimeOfDay](xref:System.DateTime.TimeOfDay) et [DateTimeOffset.TimeOfDay](xref:System.DateTimeOffset.TimeOfDay), qui retournent une valeur [TimeSpan](xref:System.TimeSpan) représentant l’heure sans référence à une date.</span><span class="sxs-lookup"><span data-stu-id="f5984-164">This usage is similar to the [DateTime.TimeOfDay](xref:System.DateTime.TimeOfDay) and [DateTimeOffset.TimeOfDay](xref:System.DateTimeOffset.TimeOfDay) properties, which return a [TimeSpan](xref:System.TimeSpan) value that represents the time without reference to a date.</span></span> <span data-ttu-id="f5984-165">Par exemple, la structure [TimeSpan](xref:System.TimeSpan) peut être utilisée pour refléter les heures d’ouverture ou de fermeture quotidiennes d’un magasin, ou elle peut être utilisée pour représenter l’heure où se produit un événement régulier.</span><span class="sxs-lookup"><span data-stu-id="f5984-165">For example, the [TimeSpan](xref:System.TimeSpan) structure can be used to reflect a store's daily opening or closing time, or it can be used to represent the time at which any regular event occurs.</span></span>

<span data-ttu-id="f5984-166">L’exemple suivant définit une structure `StoreInfo` qui inclut des objets [TimeSpan](xref:System.TimeSpan) pour les heures d’ouverture et de fermeture d’un magasin, ainsi qu’un objet [TimeZoneInfo](xref:System.TimeZoneInfo) qui représente le fuseau horaire du magasin.</span><span class="sxs-lookup"><span data-stu-id="f5984-166">The following example defines a `StoreInfo` structure that includes [TimeSpan](xref:System.TimeSpan) objects for store opening and closing times, as well as a [TimeZoneInfo](xref:System.TimeZoneInfo) object that represents the store's time zone.</span></span> <span data-ttu-id="f5984-167">La structure comprend également deux méthodes, `IsOpenNow` et `IsOpenAt`, qui indiquent si le magasin est ouvert à une heure spécifiée par l'utilisateur, qui est supposé être dans le fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="f5984-167">The structure also includes two methods, `IsOpenNow` and `IsOpenAt`, that indicates whether the store is open at a time specified by the user, who is assumed to be in the local time zone.</span></span>  

```csharp
using System;

public struct StoreInfo
{
   public String store;
   public TimeZoneInfo tz;
   public TimeSpan open;
   public TimeSpan close;

   public bool IsOpenNow()
   {
      return IsOpenAt(DateTime.TimeOfDay);
   }

   public bool IsOpenAt(TimeSpan time)
   {
      TimeZoneInfo local = TimeZoneInfo.Local;
      TimeSpan offset = TimeZoneInfo.BaseUtcOffset;

      // Is the store in the same time zone?
      if (tz.Equals(local)) {
         return time >= open & time <= close;
      }
   }
}
```

```vb
Public Structure StoreInfo
   Dim store As String
   Dim tz As TimeZoneInfo
   Dim open As TimeSpan
   Dim close As TimeSpan

   Public Function IsOpenNow() As Boolean
      Return IsOpenAt(Date.Now.TimeOfDay)
   End Function

   Public Function IsOpenAt(time As TimeSpan) As Boolean
      Dim local As TimeZoneInfo = TimeZoneInfo.Local
      Dim offset As TimeSpan = TimeZoneInfo.Local.BaseUtcOffset

      ' Is the store in the same time zone?
      If tz.Equals(local) Then
         Return time >= open And time <= close
      Else
         Dim delta As TimeSpan = TimeSpan.Zero
         Dim storeDelta As TimeSpan = TimeSpan.Zero

         ' Is it daylight saving time in either time zone?
         If local.IsDaylightSavingTime(Date.Now.Date + time) Then
            delta = local.GetAdjustmentRules(local.GetAdjustmentRules().Length - 1).DaylightDelta
         End If
         If tz.IsDaylightSavingTime(TimeZoneInfo.ConvertTime(Date.Now.Date + time, local, tz))
            storeDelta = tz.GetAdjustmentRules(local.GetAdjustmentRules().Length - 1).DaylightDelta
         End If
         Dim comparisonTime As TimeSpan = time + (offset - tz.BaseUtcOffset).Negate() + (delta - storeDelta).Negate
         Return (comparisonTime >= open And comparisonTime <= close)
      End If
   End Function
End Structure
```

<span data-ttu-id="f5984-168">La structure `StoreInfo` peut ensuite être utilisée par le code du client comme ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="f5984-168">The `StoreInfo` structure can then be used by client code like the following.</span></span> 

```csharp
public class Example
{
   public static void Main()
   {
      // Instantiate a StoreInfo object.
      var store103 = new StoreInfo();
      store103.store = "Store #103";
      store103.tz = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time");
      // Store opens at 8:00.
      store103.open = new TimeSpan(8, 0, 0);
      // Store closes at 9:30.
      store103.close = new TimeSpan(21, 30, 0);

      Console.WriteLine("Store is open now at {0}: {1}",
                        DateTime.TimeOfDay, store103.IsOpenNow());
      TimeSpan[] times = { new TimeSpan(8, 0, 0), new TimeSpan(21, 0, 0),
                           new TimeSpan(4, 59, 0), new TimeSpan(18, 31, 0) };
      foreach (var time in times)
         Console.WriteLine("Store is open at {0}: {1}",
                           time, store103.IsOpenAt(time));
   }
}
// The example displays the following output:
//       Store is open now at 15:29:01.6129911: True
//       Store is open at 08:00:00: True
//       Store is open at 21:00:00: False
//       Store is open at 04:59:00: False
//       Store is open at 18:31:00: False
```

```vb
Module Example
   Public Sub Main()
      ' Instantiate a StoreInfo object.
      Dim store103 As New StoreInfo()
      store103.store = "Store #103"
      store103.tz = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time")
      ' Store opens at 8:00.
      store103.open = new TimeSpan(8, 0, 0)
      ' Store closes at 9:30.
      store103.close = new TimeSpan(21, 30, 0)

      Console.WriteLine("Store is open now at {0}: {1}",
                        Date.Now.TimeOfDay, store103.IsOpenNow())
      Dim times() As TimeSpan = { New TimeSpan(8, 0, 0),
                                  New TimeSpan(21, 0, 0),
                                  New TimeSpan(4, 59, 0),
                                  New TimeSpan(18, 31, 0) }
      For Each time In times
         Console.WriteLine("Store is open at {0}: {1}",
                           time, store103.IsOpenAt(time))
      Next
   End Sub
End Module
' The example displays the following output:
'       Store is open now at 15:29:01.6129911: True
'       Store is open at 08:00:00: True
'       Store is open at 21:00:00: False
'       Store is open at 04:59:00: False
'       Store is open at 18:31:00: False
```

## <a name="the-timezoneinfo-class"></a><span data-ttu-id="f5984-169">La classe TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="f5984-169">The TimeZoneInfo class</span></span>

<span data-ttu-id="f5984-170">La classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) représente les fuseaux horaires de la terre et permet la conversion de toute date/heure dans un fuseau horaire en son équivalent dans un autre fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="f5984-170">The [System.TimeZoneInfo](xref:System.TimeZoneInfo) class represents any of the earth's time zones, and enables the conversion of any date and time in one time zone to its equivalent in another time zone.</span></span> <span data-ttu-id="f5984-171">La classe [TimeZoneInfo](xref:System.TimeZoneInfo) permet de travailler avec des dates et des heures de façon à ce qu’une valeur de date/heure identifie d’une manière non ambiguë un point unique dans le temps.</span><span class="sxs-lookup"><span data-stu-id="f5984-171">The [TimeZoneInfo](xref:System.TimeZoneInfo) class makes it possible to work with dates and times so that any date and time value unambiguously identifies a single point in time.</span></span>

<span data-ttu-id="f5984-172">Dans certains cas, tirer parti de la classe [TimeZoneInfo](xref:System.TimeZoneInfo) peut nécessiter des efforts de développement supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="f5984-172">In some cases, taking full advantage of the [TimeZoneInfo](xref:System.TimeZoneInfo) class may require further development work.</span></span> <span data-ttu-id="f5984-173">Les valeurs de date et d’heure ne sont pas étroitement couplées avec les fuseaux horaires auxquels elles appartiennent.</span><span class="sxs-lookup"><span data-stu-id="f5984-173">Date and time values are not tightly coupled with the time zones to which they belong.</span></span> <span data-ttu-id="f5984-174">Par conséquent, à moins que votre application ne fournisse un mécanisme permettant de lier une date/heure avec son fuseau horaire associé, une valeur de date/heure peut être facilement dissociée de son fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="f5984-174">As a result, unless your application provides some mechanism for linking a date and time with its associated time zone, it is easy for a particular date and time value to become disassociated from its time zone.</span></span> <span data-ttu-id="f5984-175">Une méthode pour lier ces informations consiste à définir une classe ou une structure qui contient à la fois la date/heure et son objet de fuseau horaire associé.</span><span class="sxs-lookup"><span data-stu-id="f5984-175">One method of linking this information is to define a class or structure that contains both the date and time value and its associated time zone object.</span></span>

<span data-ttu-id="f5984-176">Tirer parti de la prise en charge des fuseaux horaires dans .NET est possible seulement si le fuseau horaire auquel appartient une valeur de date/heure est connu quand cet objet de date/heure est instancié.</span><span class="sxs-lookup"><span data-stu-id="f5984-176">Taking advantage of time zone support in .NET is possible only if the time zone to which a date and time value belongs is known when that date and time object is instantiated.</span></span> <span data-ttu-id="f5984-177">Ce n'est pas souvent le cas, en particulier dans les applications web ou réseau.</span><span class="sxs-lookup"><span data-stu-id="f5984-177">This is often not the case, particularly in Web or network applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5984-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5984-178">See Also</span></span>

[<span data-ttu-id="f5984-179">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="f5984-179">Dates, times, and time zones</span></span>](index.md)
