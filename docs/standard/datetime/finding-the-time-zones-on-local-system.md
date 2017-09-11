---
title: "Recherche des fuseaux horaires définis sur un système local"
description: "Recherche des fuseaux horaires définis sur un système local"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3a6ee323-f3cf-486d-aa0c-103931f1eba9
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: e61017e2a0e26295c3be7e8265674b1a5d2ae5a3
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="finding-the-time-zones-defined-on-a-local-system"></a><span data-ttu-id="b6fa1-104">Recherche des fuseaux horaires définis sur un système local</span><span class="sxs-lookup"><span data-stu-id="b6fa1-104">Finding the time zones defined on a local system</span></span>

<span data-ttu-id="b6fa1-105">La classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) n’expose pas de constructeur public.</span><span class="sxs-lookup"><span data-stu-id="b6fa1-105">The [System.TimeZoneInfo](xref:System.TimeZoneInfo) class does not expose a public constructor.</span></span> <span data-ttu-id="b6fa1-106">En conséquence, le mot clé `new` ne peut pas être utilisé pour créer un objet [TimeZoneInfo](xref:System.TimeZoneInfo).</span><span class="sxs-lookup"><span data-stu-id="b6fa1-106">As a result, the `new` keyword cannot be used to create a new [TimeZoneInfo](xref:System.TimeZoneInfo) object.</span></span> <span data-ttu-id="b6fa1-107">À la place, pour instancier des objets [TimeZoneInfo](xref:System.TimeZoneInfo), vous devez récupérer des informations sur les fuseaux horaires prédéfinis à partir du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="b6fa1-107">Instead, [TimeZoneInfo](xref:System.TimeZoneInfo) objects are instantiated by retrieving information on predefined time zones from the operating system.</span></span> <span data-ttu-id="b6fa1-108">Cette rubrique explique comment instancier un fuseau horaire à partir de données stockées par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="b6fa1-108">This topic discusses instantiating a time zone from data stored by the operating system.</span></span> <span data-ttu-id="b6fa1-109">En outre, les propriétés `static` (`Shared` en Visual Basic) de la classe [TimeZoneInfo](xref:System.TimeZoneInfo) permettent d’accéder au temps universel coordonné (UTC) et au fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="b6fa1-109">In addition, `static` (`Shared` in Visual Basic) properties of the [TimeZoneInfo](xref:System.TimeZoneInfo) class provide access to Coordinated Universal Time (UTC) and the local time zone.</span></span>

## <a name="accessing-individual-time-zones"></a><span data-ttu-id="b6fa1-110">Accès aux fuseaux horaires individuels</span><span class="sxs-lookup"><span data-stu-id="b6fa1-110">Accessing Individual Time Zones</span></span>

<span data-ttu-id="b6fa1-111">La classe [TimeZoneInfo](xref:System.TimeZoneInfo) fournit deux objets de fuseau horaire prédéfinis qui représentent l’heure UTC et le fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="b6fa1-111">The [TimeZoneInfo](xref:System.TimeZoneInfo) class provides two predefined time zone objects that represent the UTC time and the local time zone.</span></span> <span data-ttu-id="b6fa1-112">Ils sont disponibles à partir des propriétés [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) et [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local), respectivement.</span><span class="sxs-lookup"><span data-stu-id="b6fa1-112">They are available from the [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) and [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) properties, respectively.</span></span> <span data-ttu-id="b6fa1-113">Pour savoir comment accéder aux fuseaux horaires UTC ou locaux, consultez [Guide pratique : accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis](access-utc-and-local.md).</span><span class="sxs-lookup"><span data-stu-id="b6fa1-113">For instructions on accessing the UTC or local time zones, see [How to: access the predefined UTC and local time zone objects](access-utc-and-local.md).</span></span> 

<span data-ttu-id="b6fa1-114">Vous pouvez également instancier un objet [TimeZoneInfo](xref:System.TimeZoneInfo) qui représente tout fuseau horaire défini par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="b6fa1-114">You can also instantiate a [TimeZoneInfo](xref:System.TimeZoneInfo) object that represents any time zone defined by the operating system.</span></span> <span data-ttu-id="b6fa1-115">Pour obtenir des instructions sur l’instanciation d’un objet de fuseau horaire spécifique, consultez [Guide pratique : instancier un objet TimeZoneInfo](instantiate-time-zone-info.md).</span><span class="sxs-lookup"><span data-stu-id="b6fa1-115">For instructions on instantiating a specific time zone object, see [How to: instantiate a TimeZoneInfo object](instantiate-time-zone-info.md).</span></span>

## <a name="time-zone-identifiers"></a><span data-ttu-id="b6fa1-116">Identificateurs de fuseau horaire</span><span class="sxs-lookup"><span data-stu-id="b6fa1-116">Time Zone Identifiers</span></span>

<span data-ttu-id="b6fa1-117">L'identificateur de fuseau horaire est un champ clé qui identifie le fuseau horaire de manière unique.</span><span class="sxs-lookup"><span data-stu-id="b6fa1-117">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="b6fa1-118">Alors que la plupart des clés sont relativement courtes, l'identificateur de fuseau horaire est long.</span><span class="sxs-lookup"><span data-stu-id="b6fa1-118">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="b6fa1-119">Dans la plupart des cas, sa valeur correspond à la propriété [TimeZoneInfo.StandardName](xref:System.TimeZoneInfo.StandardName) qui est utilisée pour fournir le nom de l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="b6fa1-119">In most cases, its value corresponds to the [TimeZoneInfo.StandardName](xref:System.TimeZoneInfo.StandardName) property, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="b6fa1-120">Toutefois, il existe des exceptions.</span><span class="sxs-lookup"><span data-stu-id="b6fa1-120">However, there are exceptions.</span></span> <span data-ttu-id="b6fa1-121">Pour vous assurer que l'identificateur fourni est valide, la meilleure façon consiste à énumérer les fuseaux horaires disponibles sur votre système et à noter les identificateurs associés.</span><span class="sxs-lookup"><span data-stu-id="b6fa1-121">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note their associated identifiers.</span></span> <span data-ttu-id="b6fa1-122">Pour obtenir des instructions sur l’énumération des fuseaux horaires, consultez [Guide pratique : énumérer les fuseaux horaires d’un ordinateur](enumerate-time-zones.md).</span><span class="sxs-lookup"><span data-stu-id="b6fa1-122">For instructions on enumerating time zones, see [How to: enumerate time zones present on a computer](enumerate-time-zones.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b6fa1-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6fa1-123">See Also</span></span>

[<span data-ttu-id="b6fa1-124">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="b6fa1-124">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="b6fa1-125">Guide pratique pour accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis</span><span class="sxs-lookup"><span data-stu-id="b6fa1-125">How to: access the predefined UTC and local time zone objects</span></span>](access-utc-and-local.md)

[<span data-ttu-id="b6fa1-126">Guide pratique pour instancier un objet TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="b6fa1-126">How to: instantiate a TimeZoneInfo object</span></span>](instantiate-time-zone-info.md)

[<span data-ttu-id="b6fa1-127">Guide pratique pour énumérer les fuseaux horaires d’un ordinateur</span><span class="sxs-lookup"><span data-stu-id="b6fa1-127">How to: enumerate time zones present on a computer</span></span>](enumerate-time-zones.md)

[<span data-ttu-id="b6fa1-128">Conversion d’heures entre fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="b6fa1-128">Converting times between time zones</span></span>](converting-between-time-zones.md)
