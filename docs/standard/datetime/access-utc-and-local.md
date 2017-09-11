---
title: "Guide pratique : accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis"
description: "Guide pratique pour accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/11/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 13454d47-d957-421b-9ecd-940058b8835e
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: fcc48e40cdad25c6142dbc3a86513b816378fa4b
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="25eeb-104">Guide pratique : accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis</span><span class="sxs-lookup"><span data-stu-id="25eeb-104">How to: access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="25eeb-105">La classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) fournit deux propriétés, `Utc` et `Local`, qui permettent à votre code d’accéder à des objets de fuseau horaire prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="25eeb-105">The [System.TimeZoneInfo](xref:System.TimeZoneInfo) class provides two properties, `Utc` and `Local`, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="25eeb-106">Cette rubrique explique comment accéder aux objets `TimeZoneInfo` retournés par ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="25eeb-106">This topic discusses how to access the `TimeZoneInfo` objects returned by those properties.</span></span>

## <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="25eeb-107">Pour accéder à l’objet TimeZoneInfo de temps universel coordonné (UTC)</span><span class="sxs-lookup"><span data-stu-id="25eeb-107">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="25eeb-108">Utilisez la propriété **static** (**Shared** en Visual Basic) [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) pour accéder au temps universel coordonné.</span><span class="sxs-lookup"><span data-stu-id="25eeb-108">Use the **static** (**Shared** in Visual Basic) [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="25eeb-109">Au lieu d’affecter l’objet [TimeZoneInfo](xref:System.TimeZoneInfo) retourné par la propriété à une variable d’objet, continuez à accéder au temps universel coordonné via la propriété [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc).</span><span class="sxs-lookup"><span data-stu-id="25eeb-109">Rather than assigning the [TimeZoneInfo](xref:System.TimeZoneInfo) object returned by the property to an object variable, continue to access Coordinated Universal Time through the [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) property.</span></span>


## <a name="to-access-the-local-time-zone"></a><span data-ttu-id="25eeb-110">Pour accéder au fuseau horaire local</span><span class="sxs-lookup"><span data-stu-id="25eeb-110">To access the local time zone</span></span>

1. <span data-ttu-id="25eeb-111">Utilisez la propriété **static** (**Shared** en Visual Basic) [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) pour accéder au fuseau horaire local du système.</span><span class="sxs-lookup"><span data-stu-id="25eeb-111">Use the **static** (**Shared** in Visual Basic) [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) property to access the local system time zone.</span></span>

2. <span data-ttu-id="25eeb-112">Au lieu d’affecter l’objet [TimeZoneInfo](xref:System.TimeZoneInfo) retourné par la propriété à une variable d’objet, continuez à accéder au fuseau horaire local via la propriété [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local).</span><span class="sxs-lookup"><span data-stu-id="25eeb-112">Rather than assigning the [TimeZoneInfo](xref:System.TimeZoneInfo) object returned by the property to an object variable, continue to access the local time zone through the [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) property.</span></span>

## <a name="example"></a><span data-ttu-id="25eeb-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="25eeb-113">Example</span></span>

<span data-ttu-id="25eeb-114">Le code suivant utilise les propriétés [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) et [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) pour convertir une heure du fuseau horaire Est (États-Unis et Canada), ainsi que pour afficher le nom du fuseau horaire sur la console.</span><span class="sxs-lookup"><span data-stu-id="25eeb-114">The following code uses the [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) and [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

```csharp
// Create Eastern Standard Time value and TimeZoneInfo object      
DateTime estTime = new DateTime(2007, 1, 1, 00, 00, 00);
string timeZoneName = "Eastern Standard Time";
try
{
   TimeZoneInfo est = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName);

   // Convert EST to local time
   DateTime localTime = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Local);
   Console.WriteLine("At {0} {1}, the local time is {2} {3}.", 
           estTime, 
           est, 
           localTime, 
           TimeZoneInfo.Local.IsDaylightSavingTime(localTime) ?
                     TimeZoneInfo.Local.DaylightName : 
                     TimeZoneInfo.Local.StandardName);

   // Convert EST to UTC
   DateTime utcTime = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Utc);
   Console.WriteLine("At {0} {1}, the time is {2} {3}.", 
           estTime, 
           est, 
           utcTime, 
           TimeZoneInfo.Utc.StandardName);
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The {0} zone cannot be found in the registry.", 
                     timeZoneName);
}
catch (InvalidTimeZoneException)
{
   Console.WriteLine("The registry contains invalid data for the {0} zone.", 
                     timeZoneName);
}
```

```vb
' Create Eastern Standard Time value and TimeZoneInfo object      
Dim estTime As Date = #01/01/2007 00:00:00#
Dim timeZoneName As String = "Eastern Standard Time"
Try
   Dim est As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName)

   ' Convert EST to local time
   Dim localTime As Date = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Local)
   Console.WriteLine("At {0} {1}, the local time is {2} {3}.", _
           estTime, _
           est, _
           localTime, _
           IIf(TimeZoneInfo.Local.IsDaylightSavingTime(localTime), _
               TimeZoneInfo.Local.DaylightName, _
               TimeZoneInfo.Local.StandardName))

   ' Convert EST to UTC
   Dim utcTime As Date = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Utc)
   Console.WriteLine("At {0} {1}, the time is {2} {3}.", _
           estTime, _
           est, _
           utcTime, _
           TimeZoneInfo.Utc.StandardName)
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The {0} zone cannot be found in the registry.", _
                     timeZoneName)
Catch e As InvalidTimeZoneException
   Console.WriteLine("The registry contains invalid data for the {0} zone.", _
                     timeZoneName)
End Try
```

<span data-ttu-id="25eeb-115">Vous devez toujours accéder au fuseau horaire local via la propriété [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) plutôt qu’en affectant le fuseau horaire local à une variable d’objet [TimeZoneInfo](xref:System.TimeZoneInfo).</span><span class="sxs-lookup"><span data-stu-id="25eeb-115">You should always access the local time zone through the [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) property rather than assigning the local time zone to a [TimeZoneInfo](xref:System.TimeZoneInfo) object variable.</span></span> <span data-ttu-id="25eeb-116">De même, vous devez toujours accéder au temps universel coordonné via la propriété [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) plutôt qu’en affectant le fuseau horaire UTC à une variable d’objet [TimeZoneInfo](xref:System.TimeZoneInfo).</span><span class="sxs-lookup"><span data-stu-id="25eeb-116">Similarly, you should always access Coordinated Universal Time through the [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) property rather than assigning the UTC zone to a [TimeZoneInfo](xref:System.TimeZoneInfo) object variable.</span></span> <span data-ttu-id="25eeb-117">Cela empêche la variable d’objet [TimeZoneInfo](xref:System.TimeZoneInfo) d’être invalidée par une méthode externe.</span><span class="sxs-lookup"><span data-stu-id="25eeb-117">This prevents the [TimeZoneInfo](xref:System.TimeZoneInfo) object variable from being invalidated by an external method.</span></span>


## <a name="see-also"></a><span data-ttu-id="25eeb-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25eeb-118">See Also</span></span>

[<span data-ttu-id="25eeb-119">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="25eeb-119">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="25eeb-120">Recherche des fuseaux horaires définis sur un système local</span><span class="sxs-lookup"><span data-stu-id="25eeb-120">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)

