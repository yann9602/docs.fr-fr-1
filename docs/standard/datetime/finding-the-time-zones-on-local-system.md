---
title: "Recherche des fuseaux horaires définis sur un système local"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zones [.NET Framework], local
- time zones [.NET Framework], finding local system time zones
- time zone identifiers [.NET Framework]
- local time zone access
- time zones [.NET Framework], retrieving
- UTC times, finding local system time zones
- time zones [.NET Framework], UTC
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c86932455301d15621c03d4440a8a16e44575bac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a><span data-ttu-id="97613-102">Recherche des fuseaux horaires définis sur un système local</span><span class="sxs-lookup"><span data-stu-id="97613-102">Finding the time zones defined on a local system</span></span>

<span data-ttu-id="97613-103">La classe <xref:System.TimeZoneInfo> n'expose pas de constructeur public.</span><span class="sxs-lookup"><span data-stu-id="97613-103">The <xref:System.TimeZoneInfo> class does not expose a public constructor.</span></span> <span data-ttu-id="97613-104">En conséquence, le mot clé `new` ne peut pas être utilisé pour créer un objet <xref:System.TimeZoneInfo>.</span><span class="sxs-lookup"><span data-stu-id="97613-104">As a result, the `new` keyword cannot be used to create a new <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="97613-105">Pour instancier des objets <xref:System.TimeZoneInfo>, vous devez donc soit récupérer dans le Registre des informations sur les fuseaux horaires prédéfinis, soit créer un fuseau horaire personnalisé.</span><span class="sxs-lookup"><span data-stu-id="97613-105">Instead, <xref:System.TimeZoneInfo> objects are instantiated either by retrieving information on predefined time zones from the registry or by creating a custom time zone.</span></span> <span data-ttu-id="97613-106">Cette rubrique explique comment instancier un fuseau horaire à partir de données stockées dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="97613-106">This topic discusses instantiating a time zone from data stored in the registry.</span></span> <span data-ttu-id="97613-107">En outre, les propriétés `static` (`shared` en Visual Basic) de la classe <xref:System.TimeZoneInfo> permettent d'accéder au temps universel coordonné (UTC) et au fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="97613-107">In addition, `static` (`shared` in Visual Basic) properties of the <xref:System.TimeZoneInfo> class provide access to Coordinated Universal Time (UTC) and the local time zone.</span></span>

> [!NOTE]
> <span data-ttu-id="97613-108">Si les fuseaux horaires ne sont pas définis dans le Registre, vous pouvez créer des fuseaux horaires personnalisés en appelant les surcharges de la méthode <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>.</span><span class="sxs-lookup"><span data-stu-id="97613-108">For time zones that are not defined in the registry, you can create custom time zones by calling the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="97613-109">Création d’un fuseau horaire personnalisé est décrite dans le [Comment : créer des fuseaux horaires sans règles d’ajustement](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) et [Comment : créer des fuseaux horaires avec des règles d’ajustement](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) rubriques.</span><span class="sxs-lookup"><span data-stu-id="97613-109">Creating a custom time zone is discussed in the [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) topics.</span></span> <span data-ttu-id="97613-110">Vous pouvez également instancier un objet <xref:System.TimeZoneInfo> en le restaurant à partir d'une chaîne sérialisée à l'aide de la méthode <xref:System.TimeZoneInfo.FromSerializedString%2A>.</span><span class="sxs-lookup"><span data-stu-id="97613-110">In addition, you can instantiate a <xref:System.TimeZoneInfo> object by restoring it from a serialized string with the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span> <span data-ttu-id="97613-111">Sérialiser et désérialiser un <xref:System.TimeZoneInfo> objet est décrite dans le [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) et [Comment : restaurer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) rubriques.</span><span class="sxs-lookup"><span data-stu-id="97613-111">Serializing and deserializing a <xref:System.TimeZoneInfo> object is discussed in the [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) and [How to: Restore Time Zones from an Embedded Resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) topics.</span></span>

## <a name="accessing-individual-time-zones"></a><span data-ttu-id="97613-112">L’accès aux fuseaux horaires individuels</span><span class="sxs-lookup"><span data-stu-id="97613-112">Accessing individual time zones</span></span>

<span data-ttu-id="97613-113">La classe <xref:System.TimeZoneInfo> fournit deux objets de fuseaux horaires prédéfinis qui représentent l'heure UTC et le fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="97613-113">The <xref:System.TimeZoneInfo> class provides two predefined time zone objects that represent the UTC time and the local time zone.</span></span> <span data-ttu-id="97613-114">Ils sont disponibles dans les propriétés <xref:System.TimeZoneInfo.Utc%2A> et <xref:System.TimeZoneInfo.Local%2A>, respectivement.</span><span class="sxs-lookup"><span data-stu-id="97613-114">They are available from the <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A> properties, respectively.</span></span> <span data-ttu-id="97613-115">Pour obtenir des instructions sur l’accès à l’heure UTC ou les fuseaux horaires, consultez [Comment : accéder aux objets de zone prédéfinis UTC et l’heure locale](../../../docs/standard/datetime/access-utc-and-local.md).</span><span class="sxs-lookup"><span data-stu-id="97613-115">For instructions on accessing the UTC or local time zones, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md).</span></span>

<span data-ttu-id="97613-116">Vous pouvez également instancier un objet <xref:System.TimeZoneInfo> qui représente tout fuseau horaire défini dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="97613-116">You can also instantiate a <xref:System.TimeZoneInfo> object that represents any time zone defined in the registry.</span></span> <span data-ttu-id="97613-117">Pour obtenir des instructions sur l’instanciation d’un objet de fuseau horaire spécifique, consultez [Comment : instancier un objet TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span><span class="sxs-lookup"><span data-stu-id="97613-117">For instructions on instantiating a specific time zone object, see [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

## <a name="time-zone-identifiers"></a><span data-ttu-id="97613-118">Identificateurs de fuseau horaire</span><span class="sxs-lookup"><span data-stu-id="97613-118">Time zone identifiers</span></span>

<span data-ttu-id="97613-119">L'identificateur de fuseau horaire est un champ clé qui identifie le fuseau horaire de manière unique.</span><span class="sxs-lookup"><span data-stu-id="97613-119">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="97613-120">Alors que la plupart des clés sont relativement courtes, l'identificateur de fuseau horaire est long.</span><span class="sxs-lookup"><span data-stu-id="97613-120">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="97613-121">Dans la plupart des cas, sa valeur correspond à la propriété <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType>, utilisée pour fournir le nom de l'heure standard du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="97613-121">In most cases, its value corresponds to the <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> property, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="97613-122">Toutefois, il existe des exceptions.</span><span class="sxs-lookup"><span data-stu-id="97613-122">However, there are exceptions.</span></span> <span data-ttu-id="97613-123">Pour vous assurer que l'identificateur fourni est valide, la meilleure façon consiste à énumérer les fuseaux horaires disponibles sur votre système et à noter les identificateurs associés.</span><span class="sxs-lookup"><span data-stu-id="97613-123">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note their associated identifiers.</span></span>

## <a name="see-also"></a><span data-ttu-id="97613-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97613-124">See also</span></span>

<span data-ttu-id="97613-125">[Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
[Comment : accéder aux objets de zone prédéfinis UTC et l’heure locale](../../../docs/standard/datetime/access-utc-and-local.md)
[Comment : instancier un objet TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md) 
 [Conversion d’heures entre fuseaux horaires](../../../docs/standard/datetime/converting-between-time-zones.md)</span><span class="sxs-lookup"><span data-stu-id="97613-125">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md)
[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md)
[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md)</span></span>
