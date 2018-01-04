---
title: "Comment : accéder aux objets de zone prédéfinis UTC et l’heure locale"
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
- time zones [.NET Framework], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET Framework], retrieving
- time zones [.NET Framework], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 600dbb98264c4750db1ffb98b757ad191eaf4fe5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="b9ca2-102">Comment : accéder aux objets de zone prédéfinis UTC et l’heure locale</span><span class="sxs-lookup"><span data-stu-id="b9ca2-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="b9ca2-103">Le <xref:System.TimeZoneInfo> classe fournit deux propriétés, <xref:System.TimeZoneInfo.Utc%2A> et <xref:System.TimeZoneInfo.Local%2A>, qui donnent accès de votre code à des objets de fuseaux horaires prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="b9ca2-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="b9ca2-104">Cette rubrique explique comment accéder aux objets <xref:System.TimeZoneInfo> retournés par ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="b9ca2-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="b9ca2-105">Pour accéder à l’objet TimeZoneInfo de temps universel coordonné (UTC)</span><span class="sxs-lookup"><span data-stu-id="b9ca2-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="b9ca2-106">Utilisez le `static` (`Shared` en Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriété pour accéder au temps universel coordonné.</span><span class="sxs-lookup"><span data-stu-id="b9ca2-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="b9ca2-107">Plutôt que d’attribuer le <xref:System.TimeZoneInfo> objet retourné par la propriété à une variable objet, continuer à accéder au temps universel via la <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="b9ca2-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="b9ca2-108">Pour accéder au fuseau horaire local</span><span class="sxs-lookup"><span data-stu-id="b9ca2-108">To access the local time zone</span></span>

1. <span data-ttu-id="b9ca2-109">Utilisez le `static` (`Shared` en Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriété pour accéder au fuseau horaire de système local.</span><span class="sxs-lookup"><span data-stu-id="b9ca2-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="b9ca2-110">Plutôt que d’attribuer le <xref:System.TimeZoneInfo> objet retourné par la propriété à une variable objet, continuer à accéder au fuseau horaire local via le <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="b9ca2-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="b9ca2-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="b9ca2-111">Example</span></span>

<span data-ttu-id="b9ca2-112">Le code suivant utilise la <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> et <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriétés pour convertir une heure du fuseau horaire des États-Unis et Canada est Standard, ainsi que pour afficher le nom du fuseau horaire dans la console.</span><span class="sxs-lookup"><span data-stu-id="b9ca2-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="b9ca2-113">Vous devez toujours accéder au fuseau horaire local via la <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriété au lieu d’affecter l’heure locale de la zone à une <xref:System.TimeZoneInfo> variable objet.</span><span class="sxs-lookup"><span data-stu-id="b9ca2-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="b9ca2-114">De même, vous devez toujours accéder temps universel via la <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriété au lieu d’affecter l’heure UTC de la zone à une <xref:System.TimeZoneInfo> variable objet.</span><span class="sxs-lookup"><span data-stu-id="b9ca2-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="b9ca2-115">Cela empêche le <xref:System.TimeZoneInfo> variable objet est invalidée par un appel à la <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="b9ca2-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="b9ca2-116">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b9ca2-116">Compiling the code</span></span>

<span data-ttu-id="b9ca2-117">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="b9ca2-117">This example requires:</span></span>

* <span data-ttu-id="b9ca2-118">Une référence à System.Core.dll à ajouter au projet.</span><span class="sxs-lookup"><span data-stu-id="b9ca2-118">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="b9ca2-119">Que le <xref:System> espace de noms importés avec le `using` instruction (requise en code c#).</span><span class="sxs-lookup"><span data-stu-id="b9ca2-119">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="b9ca2-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9ca2-120">See also</span></span>

<span data-ttu-id="b9ca2-121">[Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
[recherche des fuseaux horaires définis sur un système local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[Comment : instancier un objet TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)</span><span class="sxs-lookup"><span data-stu-id="b9ca2-121">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md)</span></span>
