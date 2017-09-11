---
title: Dates, heures et fuseaux horaires | Microsoft Docs
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zone objects [.NET Framework]
- date and time data [.NET Framework]
- time zones [.NET Framework]
- times [.NET Framework], time zones
- time [.NET Framework], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a6e7e748f67cf9d2dbfe5dd9bb9b14ecf2d8c331
ms.contentlocale: fr-fr
ms.lasthandoff: 05/03/2017

---

# <a name="dates-times-and-time-zones"></a><span data-ttu-id="82b85-102">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="82b85-102">Dates, times, and time zones</span></span>

<span data-ttu-id="82b85-103">Outre la structure <xref:System.DateTime> élémentaire, .NET fournit les classes suivantes qui prennent en charge l’utilisation des fuseaux horaires :</span><span class="sxs-lookup"><span data-stu-id="82b85-103">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <span data-ttu-id="82b85-104"><xref:System.TimeZone></span><span class="sxs-lookup"><span data-stu-id="82b85-104"><xref:System.TimeZone></span></span>

  <span data-ttu-id="82b85-105">Utilisez cette classe pour utiliser le fuseau horaire local du système et le temps universel coordonné (UTC, Coordinated Universal Time). Les fonctionnalités de la classe <xref:System.TimeZone> sont en grande partie remplacées par la classe <xref:System.TimeZoneInfo>.</span><span class="sxs-lookup"><span data-stu-id="82b85-105">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <span data-ttu-id="82b85-106"><xref:System.TimeZoneInfo></span><span class="sxs-lookup"><span data-stu-id="82b85-106"><xref:System.TimeZoneInfo></span></span>

  <span data-ttu-id="82b85-107">Utilisez cette classe pour travailler avec tout fuseau horaire prédéfini sur un système, créer des fuseaux horaires et convertir facilement des dates et des heures d'un fuseau horaire à un autre.</span><span class="sxs-lookup"><span data-stu-id="82b85-107">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="82b85-108">Pour tout nouveau développement, utilisez la classe <xref:System.TimeZoneInfo> au lieu de la classe <xref:System.TimeZone>.</span><span class="sxs-lookup"><span data-stu-id="82b85-108">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <span data-ttu-id="82b85-109"><xref:System.DateTimeOffset></span><span class="sxs-lookup"><span data-stu-id="82b85-109"><xref:System.DateTimeOffset></span></span>

  <span data-ttu-id="82b85-110">Utilisez cette structure pour travailler avec des dates et heures dont le décalage (ou différence) par rapport à l'heure UTC est connu.</span><span class="sxs-lookup"><span data-stu-id="82b85-110">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="82b85-111">La structure <xref:System.DateTimeOffset> associe une valeur de date et d’heure au décalage de cette heure par rapport à l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="82b85-111">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="82b85-112">En raison de sa relation avec l’heure UTC, une valeur individuelle de date et d’heure identifie de façon univoque un point unique dans le temps.</span><span class="sxs-lookup"><span data-stu-id="82b85-112">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="82b85-113">Cela rend une valeur <xref:System.DateTimeOffset> plus portable d’un ordinateur à un autre qu’une valeur <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="82b85-113">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="82b85-114">Cette section de la documentation fournit les informations dont vous avez besoin pour travailler avec les fuseaux horaires et pour créer des applications prenant en charge les fuseaux horaires, qui peuvent convertir des dates et des heures d’un fuseau horaire à un autre.</span><span class="sxs-lookup"><span data-stu-id="82b85-114">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="82b85-115">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="82b85-115">In this section</span></span>

<span data-ttu-id="82b85-116">[Vue d’ensemble des fuseaux horaires](../../../docs/standard/datetime/time-zone-overview.md)
 Décrit la terminologie, les concepts et les problèmes impliqués dans la création d’applications prenant en charge les fuseaux horaires.</span><span class="sxs-lookup"><span data-stu-id="82b85-116">[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
 Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="82b85-117">[Choix entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)
 Explique quand utiliser les types <xref:System.DateTime>, <xref:System.DateTimeOffset> et <xref:System.TimeZoneInfo> lorsque vous travaillez avec des données de date et d’heure.</span><span class="sxs-lookup"><span data-stu-id="82b85-117">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)
 Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="82b85-118">[Recherche des fuseaux horaires définis sur un système local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
 Décrit comment énumérer les fuseaux horaires trouvés sur un système local.</span><span class="sxs-lookup"><span data-stu-id="82b85-118">[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
 Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="82b85-119">[Guide pratique pour énumérer les fuseaux horaires d’un ordinateur](../../../docs/standard/datetime/enumerate-time-zones.md)
 Fournit des exemples qui énumèrent les fuseaux horaires définis dans le Registre d’un ordinateur et qui permettent aux utilisateurs de sélectionner un fuseau horaire prédéfini dans une liste.</span><span class="sxs-lookup"><span data-stu-id="82b85-119">[How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md)
 Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="82b85-120">[Guide pratique pour accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis](../../../docs/standard/datetime/access-utc-and-local.md)
 Décrit comment accéder au temps universel coordonné et au fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="82b85-120">[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md)
 Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="82b85-121">[Guide pratique pour instancier un objet TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)
 Décrit comment instancier un objet <xref:System.TimeZoneInfo> à partir du Registre du système local.</span><span class="sxs-lookup"><span data-stu-id="82b85-121">[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md)
 Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="82b85-122">[Instanciation d’un objet DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md)
 Décrit comment un objet <xref:System.DateTimeOffset> peut être instancié et comment une valeur <xref:System.DateTime> peut être convertie en valeur <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="82b85-122">[Instantiating a DateTimeOffset object](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md)
 Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="82b85-123">[Guide pratique pour créer des fuseaux horaires sans règles d’ajustement](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
 Explique comment créer un fuseau horaire personnalisé qui ne prend pas en charge la transition vers et depuis l’heure d’été.</span><span class="sxs-lookup"><span data-stu-id="82b85-123">[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
 Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="82b85-124">[Guide pratique pour créer des fuseaux horaires avec des règles d’ajustement](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
 Explique comment créer un fuseau horaire personnalisé qui prend en charge une ou plusieurs transitions vers et depuis l’heure d’été.</span><span class="sxs-lookup"><span data-stu-id="82b85-124">[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
 Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="82b85-125">[Enregistrement et restauration de fuseaux horaires](../../../docs/standard/datetime/saving-and-restoring-time-zones.md)
 Décrit la prise en charge de <xref:System.TimeZoneInfo> pour la sérialisation et la désérialisation des données de fuseau horaire et présente certains des scénarios dans lesquels ces fonctionnalités peuvent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="82b85-125">[Saving and restoring time zones](../../../docs/standard/datetime/saving-and-restoring-time-zones.md)
 Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="82b85-126">[Guide pratique pour enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
 Explique comment créer un fuseau horaire personnalisé et enregistrer ses informations dans un fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="82b85-126">[How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
 Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="82b85-127">[Guide pratique pour restaurer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
 Explique comment instancier des fuseaux horaires personnalisés qui ont été enregistrés dans un fichier de ressources incorporées.</span><span class="sxs-lookup"><span data-stu-id="82b85-127">[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
 Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="82b85-128">[Exécution d’opérations arithmétiques avec des dates et heures](../../../docs/standard/datetime/performing-arithmetic-operations.md)
 Traite les problèmes liés à l’ajout, la soustraction et la comparaison de valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="82b85-128">[Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md)
 Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="82b85-129">[Guide pratique pour utiliser des fuseaux horaires dans des opérations arithmétiques de date et d’heure](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
 Explique comment effectuer des opérations arithmétiques de date et d’heure qui reflètent les règles d’ajustement d’un fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="82b85-129">[How to: Use time zones in date and time arithmetic](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
 Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="82b85-130">[Conversion entre DateTime et DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md)
 Explique comment convertir des valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="82b85-130">[Converting between DateTime and DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md)
 Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="82b85-131">[Conversion d’heures entre fuseaux horaires](../../../docs/standard/datetime/converting-between-time-zones.md)
 Décrit comment convertir les heures d’un fuseau horaire dans un autre fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="82b85-131">[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md)
 Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="82b85-132">[Guide pratique pour résoudre des heures ambiguës](../../../docs/standard/datetime/resolve-ambiguous-times.md)
 Décrit comment résoudre une heure ambiguë en la mappant à l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="82b85-132">[How to: Resolve ambiguous times](../../../docs/standard/datetime/resolve-ambiguous-times.md)
 Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="82b85-133">[Guide pratique pour permettre aux utilisateurs de résoudre des heures ambiguës](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
 Décrit comment permettre à un utilisateur de déterminer le mappage entre une heure locale ambiguë et le temps universel coordonné.</span><span class="sxs-lookup"><span data-stu-id="82b85-133">[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
 Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="82b85-134">Référence</span><span class="sxs-lookup"><span data-stu-id="82b85-134">Reference</span></span>

<span data-ttu-id="82b85-135"><xref:System.TimeZoneInfo?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="82b85-135"><xref:System.TimeZoneInfo?displayProperty=fullName></span></span>
