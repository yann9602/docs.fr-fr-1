---
title: "Guide pratique : utiliser des fuseaux horaires dans des opérations arithmétiques de date et d’heure"
description: "Guide pratique pour utiliser des fuseaux horaires dans des opérations arithmétiques de date et d’heure"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 26870cdc-1709-4978-831b-ff2a2f24856f
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: a86471972d42adcbc412cc8eeb300410ca8a9c42
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a><span data-ttu-id="a88ac-104">Guide pratique : utiliser des fuseaux horaires dans des opérations arithmétiques de date et d’heure</span><span class="sxs-lookup"><span data-stu-id="a88ac-104">How to: use time zones in date and time arithmetic</span></span>

<span data-ttu-id="a88ac-105">En règle générale, lorsque vous effectuez des opérations arithmétiques de date et d’heure à l’aide de valeurs [System.DateTimeOffset](xref:System.DateTimeOffset), le résultat ne reflète pas les règles d’ajustement d’un fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="a88ac-105">Ordinarily, when you perform date and time arithmetic using [System.DateTimeOffset](xref:System.DateTimeOffset) values, the result does not reflect any time zone adjustment rules.</span></span> <span data-ttu-id="a88ac-106">Cela est vrai même lorsque le fuseau horaire de la valeur de date et d’heure est clairement identifiable.</span><span class="sxs-lookup"><span data-stu-id="a88ac-106">This is true even when the time zone of the date and time value is clearly identifiable.</span></span> <span data-ttu-id="a88ac-107">Cet article montre comment effectuer des opérations arithmétiques sur des valeurs de date et d’heure qui appartiennent à un fuseau horaire particulier.</span><span class="sxs-lookup"><span data-stu-id="a88ac-107">This article shows how to perform arithmetic operations on date and time values that belong to a particular time zone.</span></span> <span data-ttu-id="a88ac-108">Les résultats de ces opérations arithmétiques reflètent les règles d’ajustement du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="a88ac-108">The results of the arithmetic operations will reflect the time zone's adjustment rules.</span></span>

## <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a><span data-ttu-id="a88ac-109">Pour appliquer des règles d’ajustement dans les opérations arithmétiques de date et d’heure</span><span class="sxs-lookup"><span data-stu-id="a88ac-109">To apply adjustment rules to date and time arithmetic</span></span>

1. <span data-ttu-id="a88ac-110">Implémentez une méthode de couplage étroit d’une valeur de date et d’heure avec le fuseau horaire auquel elle appartient.</span><span class="sxs-lookup"><span data-stu-id="a88ac-110">Implement some method of closely coupling a date and time value with the time zone to which it belongs.</span></span> <span data-ttu-id="a88ac-111">Par exemple, déclarez une structure qui inclut à la fois la valeur de date et d’heure et son fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="a88ac-111">For example, declare a structure that includes both the date and time value and its time zone.</span></span> <span data-ttu-id="a88ac-112">L’exemple suivant utilise cette approche pour lier une valeur [DateTimeOffset](xref:System.DateTimeOffset) et son fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="a88ac-112">The following example uses this approach to link a [DateTimeOffset](xref:System.DateTimeOffset) value with its time zone.</span></span>

    ```csharp
    // Define a structure for DateTime values for internal use only
    internal struct TimeWithTimeZone
    {
    TimeZoneInfo TimeZone;
    DateTimeOffset Time;
    }
    ```

    ```vb
    ' Define a structure for DateTime values for internal use only
    Friend Structure TimeWithTimeZone
       Dim TimeZone As TimeZoneInfo
       Dim Time As Date
    End Structure
    ```
    
2. <span data-ttu-id="a88ac-113">Convertissez une heure en temps universel coordonné (UTC) en appelant la méthode [TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)).</span><span class="sxs-lookup"><span data-stu-id="a88ac-113">Convert a time to Coordinated Universal Time (UTC) by calling the [TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) method.</span></span>

3. <span data-ttu-id="a88ac-114">Effectuez l’opération arithmétique sur l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="a88ac-114">Perform the arithmetic operation on the UTC time.</span></span>

4. <span data-ttu-id="a88ac-115">Convertissez l’heure UTC dans le fuseau horaire associé à l’heure d’origine en appelant la méthode [TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)).</span><span class="sxs-lookup"><span data-stu-id="a88ac-115">Convert the time from UTC to the original time's associated time zone by calling the [TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) method.</span></span> 

## <a name="example"></a><span data-ttu-id="a88ac-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="a88ac-116">Example</span></span>

<span data-ttu-id="a88ac-117">L’exemple suivant ajoute deux heures et trente minutes à 9 mars 2008, à 1:30 A.M.,</span><span class="sxs-lookup"><span data-stu-id="a88ac-117">The following example adds two hours and thirty minutes to March 9, 2008, at 1:30 A.M.</span></span> <span data-ttu-id="a88ac-118">heure du Centre des États-Unis.</span><span class="sxs-lookup"><span data-stu-id="a88ac-118">Central Standard Time.</span></span> <span data-ttu-id="a88ac-119">Le passage du fuseau horaire à l’heure d’été se produit trente minutes plus tard, à 2:00,</span><span class="sxs-lookup"><span data-stu-id="a88ac-119">The time zone's transition to daylight saving time occurs thirty minutes later, at 2:00 A.M.</span></span> <span data-ttu-id="a88ac-120">le 9 mars 2008.</span><span class="sxs-lookup"><span data-stu-id="a88ac-120">on March 9, 2008.</span></span> <span data-ttu-id="a88ac-121">Étant donné que cet exemple suit les quatre étapes répertoriées à la section précédente, il signale correctement l’heure obtenue, soit 5:00,</span><span class="sxs-lookup"><span data-stu-id="a88ac-121">Because the example follows the four steps listed in the previous section, it correctly reports the resulting time as 5:00 A.M.</span></span> <span data-ttu-id="a88ac-122">le 9 mars 2008.</span><span class="sxs-lookup"><span data-stu-id="a88ac-122">on March 9, 2008.</span></span> 

```csharp
using System;

public struct TimeZoneTime
{
   public TimeZoneInfo TimeZone;
   public DateTimeOffset Time;

   public TimeZoneTime(TimeZoneInfo tz, DateTimeOffset time)
   {
      if (tz == null) 
         throw new ArgumentNullException("The time zone cannot be a null reference.");

      this.TimeZone = tz;
      this.Time = time;   
   }

   public TimeZoneTime AddTime(TimeSpan interval)
   {
      // Convert time to UTC
      DateTimeOffset utcTime = TimeZoneInfo.ConvertTime(this.Time, TimeZoneInfo.Utc);      
      // Add time interval to time
      utcTime = utcTime.Add(interval);
      // Convert time back to time in time zone
      return new TimeZoneTime(this.TimeZone, TimeZoneInfo.ConvertTime(utcTime, this.TimeZone));
   }
}

public class TimeArithmetic
{
   public const string tzName = "Central Standard Time";

   public static void Main()
   {
      try
      {
         TimeZoneTime cstTime1, cstTime2;

         TimeZoneInfo cst = TimeZoneInfo.FindSystemTimeZoneById(tzName);
         DateTime time1 = new DateTime(2008, 3, 9, 1, 30, 0);          
         TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

         cstTime1 = new TimeZoneTime(cst, 
                        new DateTimeOffset(time1, cst.GetUtcOffset(time1)));
         cstTime2 = cstTime1.AddTime(twoAndAHalfHours);
         Console.WriteLine("{0} + {1} hours = {2}", cstTime1.Time, 
                                                    twoAndAHalfHours.ToString(),  
                                                    cstTime2.Time);
      }
      catch
      {
         Console.WriteLine("Unable to find {0}.", tzName);
      }
   }
}
```

```vb
Public Structure TimeZoneTime
   Public TimeZone As TimeZoneInfo
   Public Time As Date

   Public Sub New(tz As TimeZoneInfo, time As Date)
      If tz Is Nothing Then _
         Throw New ArgumentNullException("The time zone cannot be a null reference.")

      Me.TimeZone = tz
      Me.Time = time
   End Sub

   Public Function AddTime(interval As TimeSpan) As TimeZoneTime
      ' Convert time to UTC
      Dim utcTime As DateTime = TimeZoneInfo.ConvertTimeToUtc(Me.Time, _
                                                              Me.TimeZone)      
      ' Add time interval to time
      utcTime = utcTime.Add(interval)
      ' Convert time back to time in time zone
      Return New TimeZoneTime(Me.TimeZone, TimeZoneInfo.ConvertTime(utcTime, _
                              TimeZoneInfo.Utc, Me.TimeZone))
   End Function
End Structure

Module TimeArithmetic
   Public Const tzName As String = "Central Standard Time"

   Public Sub Main()
      Try
         Dim cstTime1, cstTime2 As TimeZoneTime

         Dim cst As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(tzName)
         Dim time1 As Date = #03/09/2008 1:30AM#
         Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

         cstTime1 = New TimeZoneTime(cst, time1)
         cstTime2 = cstTime1.AddTime(twoAndAHalfHours)

         Console.WriteLine("{0} + {1} hours = {2}", cstTime1.Time, _
                                                    twoAndAHalfHours.ToString(), _ 
                                                    cstTime2.Time)  
      Catch
         Console.WriteLine("Unable to find {0}.", tzName)
      End Try   
   End Sub   
End Module
```

<span data-ttu-id="a88ac-123">Notez que si cet ajout est effectué simplement sur la valeur [DateTimeOffset](xref:System.DateTimeOffset) sans conversion préalable de cette valeur en heure UTC, le résultat indique le point correct dans le temps, mais son décalage ne reflète pas celui du fuseau horaire désigné pour cette heure.</span><span class="sxs-lookup"><span data-stu-id="a88ac-123">Note that if this addition is simply performed on the [DateTimeOffset](xref:System.DateTimeOffset) value without first converting it to UTC, the result reflects the correct point in time but its offset does not reflect that of the designated time zone for that time.</span></span> 

<span data-ttu-id="a88ac-124">Les valeurs [DateTimeOffset](xref:System.DateTimeOffset) sont dissociées de tout fuseau horaire auquel elles peuvent appartenir.</span><span class="sxs-lookup"><span data-stu-id="a88ac-124">[DateTimeOffset](xref:System.DateTimeOffset) values are disassociated from any time zone to which they might belong.</span></span> <span data-ttu-id="a88ac-125">Pour effectuer des opérations arithmétiques de date et d’heure d’une manière qui applique automatiquement les règles d’ajustement d’un fuseau horaire, le fuseau horaire auquel toute valeur de date et d’heure appartient doit être identifiable immédiatement.</span><span class="sxs-lookup"><span data-stu-id="a88ac-125">To perform date and time arithmetic in a way that automatically applies a time zone's adjustment rules, the time zone to which any date and time value belongs must be immediately identifiable.</span></span> <span data-ttu-id="a88ac-126">Cela signifie qu’une date et une heure et leur fuseau horaire associé doivent être étroitement couplés.</span><span class="sxs-lookup"><span data-stu-id="a88ac-126">This means that a date and time and its associated time zone must be tightly coupled.</span></span> <span data-ttu-id="a88ac-127">Il existe plusieurs manières de procéder, dont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a88ac-127">There are several ways to do this, which include the following:</span></span>

* <span data-ttu-id="a88ac-128">Supposez que toutes les heures utilisées dans une application appartiennent à un fuseau horaire particulier.</span><span class="sxs-lookup"><span data-stu-id="a88ac-128">Assume that all times used in an application belong to a particular time zone.</span></span> <span data-ttu-id="a88ac-129">Bien qu’appropriée dans certains cas, cette approche présente une souplesse limitée et une portabilité éventuellement limitée.</span><span class="sxs-lookup"><span data-stu-id="a88ac-129">Although appropriate in some cases, this approach offers limited flexibility and possibly limited portability.</span></span>

* <span data-ttu-id="a88ac-130">Définissez un type qui couple étroitement une valeur de date et d’heure avec son fuseau horaire associé en incluant les deux comme champs.</span><span class="sxs-lookup"><span data-stu-id="a88ac-130">Define a type that tightly couples a date and time with its associated time zone by including both as fields of the type.</span></span> <span data-ttu-id="a88ac-131">Cette approche est utilisée dans l’exemple de code qui définit une structure pour stocker la date et l’heure, et le fuseau horaire, dans deux champs membres.</span><span class="sxs-lookup"><span data-stu-id="a88ac-131">This approach is used in the code example, which defines a structure to store the date and time and the time zone in two member fields.</span></span>

## <a name="see-also"></a><span data-ttu-id="a88ac-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a88ac-132">See Also</span></span>

[<span data-ttu-id="a88ac-133">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="a88ac-133">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="a88ac-134">Exécution d’opérations arithmétiques avec des dates et heures</span><span class="sxs-lookup"><span data-stu-id="a88ac-134">Performing arithmetic operations with dates and times</span></span>](performing-arithmetic-operations.md)

