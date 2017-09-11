---
title: "Guide pratique : résoudre des heures ambiguës"
description: "Guide pratique pour résoudre des heures ambiguës"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e86050c6-d16d-405e-8bba-7205945c9a81
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: f4ab3b4bf3487e70be7e885e9b8a2281927eb30e
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="3a274-104">Guide pratique : résoudre des heures ambiguës</span><span class="sxs-lookup"><span data-stu-id="3a274-104">How to: resolve ambiguous times</span></span>

<span data-ttu-id="3a274-105">Une heure ambiguë est une heure qui correspond à plusieurs heures UTC.</span><span class="sxs-lookup"><span data-stu-id="3a274-105">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="3a274-106">Cela se produit lorsque l’heure de l’horloge est retardée, comme lors du passage à l’heure d’hiver dans un fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3a274-106">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="3a274-107">Lorsque vous gérez une heure ambiguë, vous pouvez procéder de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="3a274-107">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="3a274-108">Proposez une méthode de mappage à l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="3a274-108">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="3a274-109">Par exemple, vous pouvez supposer qu’une heure ambiguë est toujours exprimée dans le cadre de l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3a274-109">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

* <span data-ttu-id="3a274-110">Si l’heure ambiguë est un élément de données entré par l’utilisateur, vous pouvez laisser l’utilisateur résoudre l’ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="3a274-110">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="3a274-111">Cet article indique comment résoudre une heure ambiguë en supposant qu’elle correspond à l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3a274-111">This article shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

## <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="3a274-112">Pour mapper une heure ambiguë à l’heure d’hiver d’un fuseau horaire</span><span class="sxs-lookup"><span data-stu-id="3a274-112">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="3a274-113">Appelez la méthode [System.TimeZoneInfo.IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) ou [System.TimeZoneInfo.IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) pour déterminer si l’heure est ambiguë.</span><span class="sxs-lookup"><span data-stu-id="3a274-113">Call the [System.TimeZoneInfo.IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) or [System.TimeZoneInfo.IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="3a274-114">Si l’heure est ambiguë, soustrayez l’heure de l’objet [TimeSpan](xref:System.TimeSpan) retourné par la propriété [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3a274-114">If the time is ambiguous, subtract the time from the [TimeSpan](xref:System.TimeSpan) object returned by the time zone's [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) property.</span></span>

3. <span data-ttu-id="3a274-115">Appelez la méthode `static` (`Shared` en Visual Basic) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) pour affecter la valeur [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) à la propriété [Kind](xref:System.DateTime.Kind) de la valeur de date et d’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="3a274-115">Call the `static` (`Shared` in Visual Basic) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) method to set the UTC date and time value's [Kind](xref:System.DateTime.Kind) property to [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span></span>

## <a name="example"></a><span data-ttu-id="3a274-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="3a274-116">Example</span></span>

<span data-ttu-id="3a274-117">L’exemple suivant illustre comment convertir une heure [DateTime](xref:System.DateTime) ambiguë en heure UTC en supposant qu’elle représente l’heure d’hiver du fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="3a274-117">The following example illustrates how to convert an ambiguous [DateTime](xref:System.DateTime) to UTC by assuming that it represents the local time zone's standard time.</span></span> 

```csharp
private DateTime ResolveAmbiguousTime(DateTime ambiguousTime)
{
   // Time is not ambiguous
   if (! TimeZoneInfo.Local.IsAmbiguousTime(ambiguousTime))
   { 
      return ambiguousTime; 
   }
   // Time is ambiguous
   else
   {
      DateTime utcTime = DateTime.SpecifyKind(ambiguousTime - TimeZoneInfo.Local.BaseUtcOffset, 
                                              DateTimeKind.Utc);      
      Console.WriteLine("{0} local time corresponds to {1} {2}.", 
                        ambiguousTime, utcTime, utcTime.Kind.ToString());
      return utcTime;            
   }   
}
```

```vb
Private Function ResolveAmbiguousTime(ambiguousTime As Date) As Date
   ' Time is not ambiguous
   If Not TimeZoneInfo.Local.IsAmbiguousTime(ambiguousTime) Then 
      Return TimeZoneInfo.ConvertTimeToUtc(ambiguousTime) 
   ' Time is ambiguous
   Else
      Dim utcTime As Date = DateTime.SpecifyKind(ambiguousTime - TimeZoneInfo.Local.BaseUtcOffset, DateTimeKind.Utc)      
      Console.WriteLine("{0} local time corresponds to {1} {2}.", ambiguousTime, utcTime, utcTime.Kind.ToString())
      Return utcTime            
   End If   
End Function
```

<span data-ttu-id="3a274-118">Cet exemple comprend une méthode nommée `ResolveAmbiguousTime`, qui détermine si la valeur [DateTime](xref:System.DateTime) qui lui est transmise est ambiguë ou non.</span><span class="sxs-lookup"><span data-stu-id="3a274-118">The example consists of a method named `ResolveAmbiguousTime` that determines whether the [DateTime](xref:System.DateTime) value passed to it is ambiguous.</span></span> <span data-ttu-id="3a274-119">Si la valeur est ambiguë, la méthode retourne une valeur [DateTime](xref:System.DateTime) qui représente l’heure UTC correspondante.</span><span class="sxs-lookup"><span data-stu-id="3a274-119">If the value is ambiguous, the method returns a [DateTime](xref:System.DateTime) value that represents the corresponding UTC time.</span></span> <span data-ttu-id="3a274-120">La méthode gère cette conversion en soustrayant de l’heure locale la valeur de la propriété [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) du fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="3a274-120">The method handles this conversion by subtracting the value of the local time zone's [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) property from the local time.</span></span> 

<span data-ttu-id="3a274-121">En règle générale, il est possible de gérer une heure ambiguë en appelant la méthode [GetAmbiguousTimeOffsets](xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets(System.DateTime)) pour récupérer un tableau des objets [TimeSpan](xref:System.TimeSpan) qui contiennent les décalages possibles de l’heure ambiguë par rapport à l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="3a274-121">Ordinarily, an ambiguous time is handled by calling the [GetAmbiguousTimeOffsets](xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets(System.DateTime)) method to retrieve an array of [TimeSpan](xref:System.TimeSpan) objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="3a274-122">Toutefois, cet exemple émet l’hypothèse arbitraire qu’une heure ambiguë devrait toujours être mappée à l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3a274-122">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="3a274-123">La propriété [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) retourne le décalage entre l’heure UTC et l’heure d’hiver d’un fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3a274-123">The [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) property returns the offset between UTC and a time zone's standard time.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a274-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a274-124">See Also</span></span>

[<span data-ttu-id="3a274-125">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="3a274-125">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="3a274-126">Guide pratique pour permettre aux utilisateurs de résoudre des heures ambiguës</span><span class="sxs-lookup"><span data-stu-id="3a274-126">How to: let users resolve ambiguous times</span></span>](let-users-resolve-ambiguous-times.md)


