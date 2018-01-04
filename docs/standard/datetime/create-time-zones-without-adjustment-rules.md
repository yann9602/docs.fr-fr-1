---
title: "Comment : créer des fuseaux horaires sans règles d’ajustement"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 14c5e02ce5af03d063260af19e9dd1a970a93ab6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="3bc4d-102">Comment : créer des fuseaux horaires sans règles d’ajustement</span><span class="sxs-lookup"><span data-stu-id="3bc4d-102">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="3bc4d-103">Les informations de fuseau horaire précises requises par une application ne peuvent pas être présentes sur un système particulier pour plusieurs raisons :</span><span class="sxs-lookup"><span data-stu-id="3bc4d-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

* <span data-ttu-id="3bc4d-104">Le fuseau horaire n’a jamais été défini dans le Registre du système local.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-104">The time zone has never been defined in the local system's registry.</span></span>

* <span data-ttu-id="3bc4d-105">Données sur le fuseau horaire a été modifiées ou supprimées à partir du Registre.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-105">Data about the time zone has been modified or removed from the registry.</span></span>

* <span data-ttu-id="3bc4d-106">Le fuseau horaire existe, mais ne dispose pas des informations précises sur l’ajustement de fuseau horaire pour une période donnée.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-106">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="3bc4d-107">Dans ce cas, vous pouvez appeler la <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> méthode pour définir le fuseau horaire requis par votre application.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="3bc4d-108">Vous pouvez utiliser les surcharges de cette méthode pour créer un fuseau horaire avec ou sans règles d’ajustement.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="3bc4d-109">Si le fuseau horaire prend en charge l’heure d’été, vous pouvez définir des ajustements avec deux règles d’ajustement fixe ou flottant.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="3bc4d-110">(Pour les définitions de ces termes, consultez la section « Terminologie de fuseau horaire » dans [vue d’ensemble du fuseau horaire](../../../docs/standard/datetime/time-zone-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="3bc4d-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](../../../docs/standard/datetime/time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3bc4d-111">Fuseaux horaires personnalisés créés en appelant le <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> méthode ne sont pas ajoutés au Registre.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="3bc4d-112">Au lieu de cela, ils sont accessibles uniquement par le biais de la référence d’objet retournée par la <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="3bc4d-113">Cette rubrique montre comment créer un fuseau horaire sans règles d’ajustement.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-113">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="3bc4d-114">Pour créer un fuseau horaire qui prend en charge les règles d’ajustement de l’heure d’été, consultez [Comment : créer des fuseaux horaires avec des règles d’ajustement](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="3bc4d-114">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="3bc4d-115">Pour créer un fuseau horaire sans règles d’ajustement</span><span class="sxs-lookup"><span data-stu-id="3bc4d-115">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="3bc4d-116">Définir le nom d’affichage du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-116">Define the time zone's display name.</span></span>

   <span data-ttu-id="3bc4d-117">Le nom complet respecte un format relativement standard dans lequel l’offset du fuseau horaire par rapport au temps universel coordonné (UTC) est placée entre parenthèses et est suivie par une chaîne qui identifie le fuseau horaire, une ou plusieurs des villes dans le fuseau horaire, ou l’un ou plusieurs du parmi gra ou des régions dans le fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-117">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="3bc4d-118">Définir le nom de l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-118">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="3bc4d-119">En règle générale, cette chaîne est également utilisée comme identificateur de fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-119">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="3bc4d-120">Si vous souhaitez utiliser un autre identificateur que le nom de standard du fuseau horaire, définissez l’identificateur de fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-120">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="3bc4d-121">Instancier une <xref:System.TimeSpan> objet qui définit le décalage du fuseau horaire à l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-121">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="3bc4d-122">Fuseaux horaires avec les heures sont ultérieures à l’heure UTC présentent un offset positif.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-122">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="3bc4d-123">Fuseaux horaires avec les heures sont antérieures à l’heure UTC présentent un offset négatif.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-123">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="3bc4d-124">Appelez le <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> méthode pour instancier le nouveau fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-124">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="3bc4d-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="3bc4d-125">Example</span></span>

<span data-ttu-id="3bc4d-126">L’exemple suivant définit un fuseau horaire personnalisé pour Mawson, en Antarctique aucune règle d’ajustement.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-126">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="3bc4d-127">La chaîne assignée à la <xref:System.TimeZoneInfo.DisplayName%2A> propriété suit un format standard dans lequel décalage du fuseau horaire à l’heure UTC est suivi d’une description conviviale du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-127">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="3bc4d-128">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="3bc4d-128">Compiling the code</span></span>

<span data-ttu-id="3bc4d-129">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="3bc4d-129">This example requires:</span></span>

* <span data-ttu-id="3bc4d-130">Une référence à System.Core.dll à ajouter au projet.</span><span class="sxs-lookup"><span data-stu-id="3bc4d-130">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="3bc4d-131">Que les espaces de noms suivants soient importés :</span><span class="sxs-lookup"><span data-stu-id="3bc4d-131">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="3bc4d-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3bc4d-132">See also</span></span>

<span data-ttu-id="3bc4d-133">[Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
[vue d’ensemble du fuseau horaire](../../../docs/standard/datetime/time-zone-overview.md)
[Comment : créer des fuseaux horaires avec des règles d’ajustement](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)</span><span class="sxs-lookup"><span data-stu-id="3bc4d-133">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)</span></span>
