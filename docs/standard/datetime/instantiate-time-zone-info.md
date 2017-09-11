---
title: "Guide pratique : instancier un objet TimeZoneInfo"
description: Guide pratique pour instancier un objet TimeZoneInfo
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: bff137e5-d550-44c3-b460-b3f2dabd4035
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: f2584d446c92d2df2f6d74533ef07fe96888d36a
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="how-to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="b583b-104">Guide pratique : instancier un objet TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="b583b-104">How to: instantiate a TimeZoneInfo object</span></span>

<span data-ttu-id="b583b-105">La façon la plus courante d’instancier un objet [TimeZoneInfo](xref:System.TimeZoneInfo) consiste à récupérer les informations le concernant à partir du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="b583b-105">The most common way to instantiate a [TimeZoneInfo](xref:System.TimeZoneInfo) object is to retrieve information about it from the operating system.</span></span> <span data-ttu-id="b583b-106">Cette rubrique explique comment instancier un objet [TimeZoneInfo](xref:System.TimeZoneInfo) à partir du système local.</span><span class="sxs-lookup"><span data-stu-id="b583b-106">This topic discusses how to instantiate a [TimeZoneInfo](xref:System.TimeZoneInfo) object from the local system.</span></span>

## <a name="to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="b583b-107">Pour instancier un objet TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="b583b-107">To instantiate a TimeZoneInfo Object</span></span>

1. <span data-ttu-id="b583b-108">Déclarez un objet [TimeZoneInfo](xref:System.TimeZoneInfo).</span><span class="sxs-lookup"><span data-stu-id="b583b-108">Declare a [TimeZoneInfo](xref:System.TimeZoneInfo) object.</span></span>

2. <span data-ttu-id="b583b-109">Appelez la méthode `static` (`Shared` en Visual Basic) [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)).</span><span class="sxs-lookup"><span data-stu-id="b583b-109">Call the `static` (`Shared` in Visual Basic) [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) method.</span></span>

3. <span data-ttu-id="b583b-110">Gérez toutes les exceptions éventuelles levées par la méthode.</span><span class="sxs-lookup"><span data-stu-id="b583b-110">Handle any exceptions thrown by the method.</span></span>

## <a name="example"></a><span data-ttu-id="b583b-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="b583b-111">Example</span></span>

<span data-ttu-id="b583b-112">Le code suivant récupère un objet [TimeZoneInfo](xref:System.TimeZoneInfo) qui représente le fuseau horaire EST et affiche l’heure EST qui correspond à l’heure locale.</span><span class="sxs-lookup"><span data-stu-id="b583b-112">The following code retrieves a [TimeZoneInfo](xref:System.TimeZoneInfo) object that represents the Eastern Standard Time zone and displays the Eastern Standard time that corresponds to the local time.</span></span>

```csharp
DateTime timeNow = DateTime.Now;
try
{
   TimeZoneInfo easternZone = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time");
   DateTime easternTimeNow = TimeZoneInfo.ConvertTime(timeNow, TimeZoneInfo.Local, 
                                                   easternZone);
   Console.WriteLine("{0} {1} corresponds to {2} {3}.",
                     timeNow, 
                     TimeZoneInfo.Local.IsDaylightSavingTime(timeNow) ?
                               TimeZoneInfo.Local.DaylightName : 
                               TimeZoneInfo.Local.StandardName,
                     easternTimeNow, 
                     easternZone.IsDaylightSavingTime(easternTimeNow) ?
                                 easternZone.DaylightName : 
                                 easternZone.StandardName);
}
// Handle exception
//
// As an alternative to simply displaying an error message, an alternate Eastern
// Standard Time TimeZoneInfo object could be instantiated here either by restoring
// it from a serialized string or by providing the necessary data to the
// CreateCustomTimeZone method.
catch (InvalidTimeZoneException)
{
   Console.WriteLine("The Eastern Standard Time Zone contains invalid or missing data.");
}
catch (SecurityException)
{
   Console.WriteLine("The application lacks permission to read time zone information from the registry.");
}
catch (OutOfMemoryException)
{
   Console.WriteLine("Not enough memory is available to load information on the Eastern Standard Time zone.");
}
// If we weren't passing FindSystemTimeZoneById a literal string, we also 
// would handle an ArgumentNullException.
```

```vb
Dim timeNow As Date = Date.Now
Try
   Dim easternZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time")
   Dim easternTimeNow As Date = TimeZoneInfo.ConvertTime(timeNow, TimeZoneInfo.Local, easternZone)
   Console.WriteLine("{0} {1} corresponds to {2} {3}.", _
                     timeNow, _
                     IIf(TimeZoneInfo.Local.IsDaylightSavingTime(timeNow), _
                         TimeZoneInfo.Local.DaylightName, TimeZoneInfo.Local.StandardName), _
                     easternTimeNow, _
                     IIf(easternZone.IsDaylightSavingTime(easternTimeNow), _
                         easternZone.DaylightName, easternZone.StandardName))
' Handle exception
'
' As an alternative to simply displaying an error message, an alternate Eastern
' Standard Time TimeZoneInfo object could be instantiated here either by restoring
' it from a serialized string or by providing the necessary data to the
' CreateCustomTimeZone method.
Catch e As InvalidTimeZoneException
   Console.WriteLine("The Eastern Standard Time Zone contains invalid or missing data.")   
Catch e As SecurityException
   Console.WriteLine("The application lacks permission to read time zone information from the registry.")
Catch e As OutOfMemoryException
   Console.WriteLine("Not enough memory is available to load information on the Eastern Standard Time zone.")
' If we weren't passing FindSystemTimeZoneById a literal string, we also 
' would handle an ArgumentNullException.
End
``` 

<span data-ttu-id="b583b-113">Le paramètre unique de la méthode [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) est l’identificateur du fuseau horaire que vous souhaitez récupérer, qui correspond à la propriété [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id) de l’objet.</span><span class="sxs-lookup"><span data-stu-id="b583b-113">The [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) method's single parameter is the identifier of the time zone that you want to retrieve, which corresponds to the object's [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id) property.</span></span> <span data-ttu-id="b583b-114">L'identificateur de fuseau horaire est un champ clé qui identifie le fuseau horaire de manière unique.</span><span class="sxs-lookup"><span data-stu-id="b583b-114">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="b583b-115">Alors que la plupart des clés sont relativement courtes, l'identificateur de fuseau horaire est long.</span><span class="sxs-lookup"><span data-stu-id="b583b-115">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="b583b-116">Dans la plupart des cas, sa valeur correspond à la propriété [StandardName](xref:System.TimeZoneInfo.StandardName) d’un objet [TimeZoneInfo](xref:System.TimeZoneInfo), qui est utilisée pour fournir le nom de l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="b583b-116">In most cases, its value corresponds to the [StandardName](xref:System.TimeZoneInfo.StandardName) property of a [TimeZoneInfo](xref:System.TimeZoneInfo) object, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="b583b-117">Toutefois, il existe des exceptions.</span><span class="sxs-lookup"><span data-stu-id="b583b-117">However, there are exceptions.</span></span> <span data-ttu-id="b583b-118">Pour vous assurer que l’identificateur fourni est valide, il est recommandé d’énumérer les fuseaux horaires disponibles sur votre système et de noter les identificateurs associés.</span><span class="sxs-lookup"><span data-stu-id="b583b-118">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note the identifiers of the time zones present on them.</span></span> <span data-ttu-id="b583b-119">Pour voir une illustration, consultez [Guide pratique : énumérer les fuseaux horaires d’un ordinateur](enumerate-time-zones.md).</span><span class="sxs-lookup"><span data-stu-id="b583b-119">For an illustration, see [How to: enumerate time zones present on a computer](enumerate-time-zones.md).</span></span> <span data-ttu-id="b583b-120">La rubrique [Recherche des fuseaux horaires définis sur un système local](finding-the-time-zones-on-local-system.md) contient également la liste des identificateurs de fuseau horaire sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="b583b-120">The [Finding the time zones defined on a local system](finding-the-time-zones-on-local-system.md) topic also contains a list of selected time zone identifiers.</span></span>

<span data-ttu-id="b583b-121">Si le fuseau horaire est trouvé, la méthode retourne son objet [TimeZoneInfo](xref:System.TimeZoneInfo).</span><span class="sxs-lookup"><span data-stu-id="b583b-121">If the time zone is found, the method returns its [TimeZoneInfo](xref:System.TimeZoneInfo) object.</span></span> <span data-ttu-id="b583b-122">Si le fuseau horaire est trouvé, mais que ses données sont endommagées ou incomplètes, la méthode lève une exception [InvalidTimeZoneException](xref:System.InvalidTimeZoneException).</span><span class="sxs-lookup"><span data-stu-id="b583b-122">If the time zone is found but its data is corrupted or incomplete, the method throws an [InvalidTimeZoneException](xref:System.InvalidTimeZoneException).</span></span> 

## <a name="see-also"></a><span data-ttu-id="b583b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b583b-123">See Also</span></span>

[<span data-ttu-id="b583b-124">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="b583b-124">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="b583b-125">Recherche des fuseaux horaires définis sur un système local</span><span class="sxs-lookup"><span data-stu-id="b583b-125">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)
