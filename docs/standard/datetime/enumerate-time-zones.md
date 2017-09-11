---
title: "Guide pratique : énumérer les fuseaux horaires d’un ordinateur"
description: "Guide pratique pour énumérer les fuseaux horaires d’un ordinateur"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c5ae4a6c-1790-4355-b5b1-879aaf956129
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: f30ba2a483ff7e5867417969946c2774175d5e3d
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a><span data-ttu-id="03392-104">Guide pratique : énumérer les fuseaux horaires d’un ordinateur</span><span class="sxs-lookup"><span data-stu-id="03392-104">How to: enumerate time zones present on a computer</span></span>

<span data-ttu-id="03392-105">Pour utiliser correctement un fuseau horaire désigné, le système doit pouvoir accéder aux informations le concernant.</span><span class="sxs-lookup"><span data-stu-id="03392-105">Successfully working with a designated time zone requires that information about that time zone be available to the system.</span></span> <span data-ttu-id="03392-106">Par exemple, le système d’exploitation Windows stocke ces informations dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="03392-106">For example, the Windows operating system stores this information in the registry.</span></span> <span data-ttu-id="03392-107">Il existe de nombreux fuseaux horaires dans le monde, mais le Registre contient des informations sur un sous-ensemble de ces fuseaux horaires uniquement.</span><span class="sxs-lookup"><span data-stu-id="03392-107">However, although the total number of time zones that exist throughout the world is large, the registry contains information about only a subset of them.</span></span> <span data-ttu-id="03392-108">De plus, le Registre est une structure dynamique dont le contenu peut être modifié délibérément ou accidentellement.</span><span class="sxs-lookup"><span data-stu-id="03392-108">In addition, the registry itself is a dynamic structure whose contents are subject to both deliberate and accidental change.</span></span> <span data-ttu-id="03392-109">Par conséquent, une application ne peut pas toujours supposer qu’un fuseau horaire particulier est défini et disponible sur un système.</span><span class="sxs-lookup"><span data-stu-id="03392-109">As a result, an application cannot always assume that a particular time zone is defined and available on a system.</span></span> <span data-ttu-id="03392-110">Pour de nombreuses applications qui utilisent des informations de fuseau horaire, il convient en premier lieu de déterminer si les fuseaux horaires requis sont disponibles sur le système local ou de fournir à l’utilisateur la liste des fuseaux horaires qu’il peut sélectionner.</span><span class="sxs-lookup"><span data-stu-id="03392-110">The first step for many applications that use time zone information applications is to determine whether required time zones are available on the local system, or to give the user a list of time zones from which to select.</span></span> <span data-ttu-id="03392-111">Il faut donc qu’une application énumère les fuseaux horaires définis sur un système local.</span><span class="sxs-lookup"><span data-stu-id="03392-111">This requires that an application enumerate the time zones defined on a local system.</span></span> 

## <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a><span data-ttu-id="03392-112">Pour énumérer les fuseaux horaires présents sur le système local</span><span class="sxs-lookup"><span data-stu-id="03392-112">To enumerate the time zones present on the local system</span></span>

1. <span data-ttu-id="03392-113">Appelez la méthode [TimeZoneInfo.GetSystemTimeZones](xref:System.TimeZoneInfo.GetSystemTimeZones).</span><span class="sxs-lookup"><span data-stu-id="03392-113">Call the [TimeZoneInfo.GetSystemTimeZones](xref:System.TimeZoneInfo.GetSystemTimeZones) method.</span></span> <span data-ttu-id="03392-114">La méthode retourne une collection générique [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) d’objets [TimeZoneInfo](xref:System.TimeZoneInfo).</span><span class="sxs-lookup"><span data-stu-id="03392-114">The method returns a generic [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) collection of [TimeZoneInfo](xref:System.TimeZoneInfo) objects.</span></span> <span data-ttu-id="03392-115">Les entrées présentes dans la collection sont triées par leur propriété [DisplayName](xref:System.TimeZoneInfo.DisplayName).</span><span class="sxs-lookup"><span data-stu-id="03392-115">The entries in the collection are sorted by their [DisplayName](xref:System.TimeZoneInfo.DisplayName) property.</span></span> <span data-ttu-id="03392-116">Exemple :</span><span class="sxs-lookup"><span data-stu-id="03392-116">For example:</span></span>

    ```csharp
    ReadOnlyCollection<TimeZoneInfo> tzCollection;
    tzCollection = TimeZoneInfo.GetSystemTimeZones();
    ```

    ```vb
    Dim tzCollection As ReadOnlyCollection(Of TimeZoneInfo) = TimeZoneInfo.GetSystemTimeZones
    ```

2. <span data-ttu-id="03392-117">Énumérez les objets [TimeZoneInfo](xref:System.TimeZoneInfo) individuels qui figurent dans la collection en utilisant une boucle `foreach` (en C#) ou `For Each…Next` (en Visual Basic), et exécutez tout les traitements nécessaires sur chaque objet.</span><span class="sxs-lookup"><span data-stu-id="03392-117">Enumerate the individual [TimeZoneInfo](xref:System.TimeZoneInfo) objects in the collection by using a `foreach` loop (in C#) or a `For Each…Next` loop (in Visual Basic), and perform any necessary processing on each object.</span></span> <span data-ttu-id="03392-118">Par exemple, le code suivant énumère la collection [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) d’objets [TimeZoneInfo](xref:System.TimeZoneInfo) retournée à l’étape 1 et répertorie le nom complet de chaque fuseau horaire sur la console.</span><span class="sxs-lookup"><span data-stu-id="03392-118">For example, the following code enumerates the [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) collection of [TimeZoneInfo](xref:System.TimeZoneInfo) objects returned in step 1 and lists the display name of each time zone on the console.</span></span>

    ```csharp
    foreach (TimeZoneInfo timeZone in tzCollection)
    Console.WriteLine("   {0}: {1}", timeZone.Id, timeZone.DisplayName);
    ```

    ```vb
    For Each timeZone As TimeZoneInfo In tzCollection
        Console.WriteLine("   {0}: {1}", timeZone.Id, timeZone.DisplayName)
    Next
    ```

## <a name="see-also"></a><span data-ttu-id="03392-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03392-119">See Also</span></span>

[<span data-ttu-id="03392-120">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="03392-120">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="03392-121">Recherche des fuseaux horaires définis sur un système local</span><span class="sxs-lookup"><span data-stu-id="03392-121">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)


