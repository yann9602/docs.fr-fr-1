---
title: "Comment : résoudre des heures ambiguës"
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
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e3706747848dbcd29d4ed2e81d5b7447a127a653
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="b6adc-102">Comment : résoudre des heures ambiguës</span><span class="sxs-lookup"><span data-stu-id="b6adc-102">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="b6adc-103">Une heure ambiguë est une heure qui correspond à plusieurs heures UTC.</span><span class="sxs-lookup"><span data-stu-id="b6adc-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="b6adc-104">Cela se produit lorsque l’heure de l’horloge est retardée, comme lors du passage à l’heure d’hiver dans un fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="b6adc-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="b6adc-105">Lorsque vous gérez une heure ambiguë, vous pouvez procéder de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="b6adc-105">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="b6adc-106">Proposez une méthode de mappage à l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="b6adc-106">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="b6adc-107">Par exemple, vous pouvez supposer qu’une heure ambiguë est toujours exprimée dans le cadre de l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="b6adc-107">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

* <span data-ttu-id="b6adc-108">Si l’heure ambiguë est un élément de données entré par l’utilisateur, vous pouvez laisser l’utilisateur résoudre l’ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="b6adc-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="b6adc-109">Cette rubrique montre comment résoudre une heure ambiguë en supposant qu’elle représente l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="b6adc-109">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="b6adc-110">Pour mapper une heure ambiguë à l’heure d’hiver d’un fuseau horaire</span><span class="sxs-lookup"><span data-stu-id="b6adc-110">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="b6adc-111">Appelez le <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> méthode pour déterminer si l’heure est ambiguë.</span><span class="sxs-lookup"><span data-stu-id="b6adc-111">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="b6adc-112">Si l’heure est ambiguë, soustrayez l’heure de la <xref:System.TimeSpan> objet retourné par du fuseau horaire <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="b6adc-112">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="b6adc-113">Appelez le `static` (`Shared` dans Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> pour définir la date et l’heure valeur UTC <xref:System.DateTime.Kind%2A> propriété <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b6adc-113">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="b6adc-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6adc-114">Example</span></span>

<span data-ttu-id="b6adc-115">L’exemple suivant illustre comment convertir une heure ambiguë en heure UTC en supposant qu’elle représente l’heure d’hiver du fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="b6adc-115">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="b6adc-116">L’exemple se compose d’une méthode nommée `ResolveAmbiguousTime` qui détermine si le <xref:System.DateTime> valeur passée est ambiguë.</span><span class="sxs-lookup"><span data-stu-id="b6adc-116">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="b6adc-117">Si la valeur est ambiguë, la méthode retourne un <xref:System.DateTime> valeur qui représente l’heure UTC correspondante.</span><span class="sxs-lookup"><span data-stu-id="b6adc-117">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="b6adc-118">La méthode gère cette conversion en soustrayant la valeur du fuseau horaire local <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriété à partir de l’heure locale.</span><span class="sxs-lookup"><span data-stu-id="b6adc-118">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="b6adc-119">En règle générale, une heure ambiguë est contrôlée en appelant le <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> méthode pour récupérer un tableau de <xref:System.TimeSpan> offsets d’objets qui contiennent des UTC possibles de l’heure ambiguë.</span><span class="sxs-lookup"><span data-stu-id="b6adc-119">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="b6adc-120">Toutefois, cet exemple émet l’hypothèse arbitraire qu’une heure ambiguë devrait toujours être mappée à l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="b6adc-120">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="b6adc-121">Le <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriété retourne le décalage entre l’heure UTC et l’heure d’hiver d’un fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="b6adc-121">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="b6adc-122">Dans cet exemple, toutes les références dans le fuseau horaire local sont effectuées via le <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriété ; l’heure locale zone n’est jamais assigné à une variable objet.</span><span class="sxs-lookup"><span data-stu-id="b6adc-122">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="b6adc-123">Ceci est une pratique recommandée, car un appel à la <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> méthode invalide le fuseau horaire local est attribué à tous les objets.</span><span class="sxs-lookup"><span data-stu-id="b6adc-123">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="b6adc-124">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b6adc-124">Compiling the code</span></span>

<span data-ttu-id="b6adc-125">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="b6adc-125">This example requires:</span></span>

* <span data-ttu-id="b6adc-126">Une référence à System.Core.dll à ajouter au projet.</span><span class="sxs-lookup"><span data-stu-id="b6adc-126">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="b6adc-127">Que le <xref:System> espace de noms importés avec le `using` instruction (requise en code c#).</span><span class="sxs-lookup"><span data-stu-id="b6adc-127">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="b6adc-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6adc-128">See also</span></span>

<span data-ttu-id="b6adc-129">[Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
[Comment : permettre aux utilisateurs de résoudre des heures ambiguës](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)</span><span class="sxs-lookup"><span data-stu-id="b6adc-129">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)</span></span>
