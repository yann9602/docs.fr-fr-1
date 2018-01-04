---
title: "Comment : créer des fuseaux horaires avec des règles d’ajustement"
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
- time zones [.NET Framework], creating
- time zones [.NET Framework], and adjustment rules
- adjustment rule [.NET Framework]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eddc1d400f5f63cb2790fc4c660b70ebfdd0efc1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a><span data-ttu-id="aac9c-102">Comment : créer des fuseaux horaires avec des règles d’ajustement</span><span class="sxs-lookup"><span data-stu-id="aac9c-102">How to: Create time zones with adjustment rules</span></span>

<span data-ttu-id="aac9c-103">Les informations de fuseau horaire précises requises par une application ne peuvent pas être présentes sur un système particulier pour plusieurs raisons :</span><span class="sxs-lookup"><span data-stu-id="aac9c-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

* <span data-ttu-id="aac9c-104">Le fuseau horaire n’a jamais été défini dans le Registre du système local.</span><span class="sxs-lookup"><span data-stu-id="aac9c-104">The time zone has never been defined in the local system's registry.</span></span>

* <span data-ttu-id="aac9c-105">Données sur le fuseau horaire a été modifiées ou supprimées à partir du Registre.</span><span class="sxs-lookup"><span data-stu-id="aac9c-105">Data about the time zone has been modified or removed from the registry.</span></span>

* <span data-ttu-id="aac9c-106">Le fuseau horaire ne dispose pas des informations précises sur l’ajustement de fuseau horaire pour une période donnée.</span><span class="sxs-lookup"><span data-stu-id="aac9c-106">The time zone does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="aac9c-107">Dans ce cas, vous pouvez appeler la <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> méthode pour définir le fuseau horaire requis par votre application.</span><span class="sxs-lookup"><span data-stu-id="aac9c-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="aac9c-108">Vous pouvez utiliser les surcharges de cette méthode pour créer un fuseau horaire avec ou sans règles d’ajustement.</span><span class="sxs-lookup"><span data-stu-id="aac9c-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="aac9c-109">Si le fuseau horaire prend en charge l’heure d’été, vous pouvez définir des ajustements avec deux règles d’ajustement fixe ou flottant.</span><span class="sxs-lookup"><span data-stu-id="aac9c-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="aac9c-110">(Pour les définitions de ces termes, consultez la section « Terminologie de fuseau horaire » dans [vue d’ensemble du fuseau horaire](../../../docs/standard/datetime/time-zone-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="aac9c-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](../../../docs/standard/datetime/time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aac9c-111">Fuseaux horaires personnalisés créés en appelant le <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> méthode ne sont pas ajoutés au Registre.</span><span class="sxs-lookup"><span data-stu-id="aac9c-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="aac9c-112">Au lieu de cela, ils sont accessibles uniquement par le biais de la référence d’objet retournée par la <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="aac9c-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="aac9c-113">Cette rubrique montre comment créer un fuseau horaire avec des règles d’ajustement.</span><span class="sxs-lookup"><span data-stu-id="aac9c-113">This topic shows how to create a time zone with adjustment rules.</span></span> <span data-ttu-id="aac9c-114">Pour créer un fuseau horaire qui ne prend pas en charge les règles d’ajustement de l’heure d’été, consultez [Comment : créer des fuseaux horaires sans règles ajustement](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="aac9c-114">To create a time zone that does not support daylight saving time adjustment rules, see [How to: Create Time Zones Without Adjustment Rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a><span data-ttu-id="aac9c-115">Pour créer un fuseau horaire avec flottante des règles d’ajustement</span><span class="sxs-lookup"><span data-stu-id="aac9c-115">To create a time zone with floating adjustment rules</span></span>

1. <span data-ttu-id="aac9c-116">Pour chaque ajustement (c'est-à-dire, pour chaque transition d’et heure standard pour revenir sur un intervalle de temps particulier), procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="aac9c-116">For each adjustment (that is, for each transition away from and back to standard time over a particular time interval), do the following:</span></span>

    1. <span data-ttu-id="aac9c-117">Définir la durée de transition de départ pour l’ajustement de fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="aac9c-117">Define the starting transition time for the time zone adjustment.</span></span>

       <span data-ttu-id="aac9c-118">Vous devez appeler la <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> méthode et lui passer une <xref:System.DateTime> valeur qui définit la durée de la transition, une valeur entière qui définit le mois de la transition, une valeur entière qui définit la semaine où la transition se produit, et un <xref:System.DayOfWeek> valeur qui définit le jour de la semaine où la transition se produit.</span><span class="sxs-lookup"><span data-stu-id="aac9c-118">You must call the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> method and pass it a <xref:System.DateTime> value that defines the time of the transition, an integer value that defines the month of the transition, an integer value that defines the week on which the transition occurs, and a <xref:System.DayOfWeek> value that defines the day of the week on which the transition occurs.</span></span> <span data-ttu-id="aac9c-119">Cet appel de méthode instancie un <xref:System.TimeZoneInfo.TransitionTime> objet.</span><span class="sxs-lookup"><span data-stu-id="aac9c-119">This method call instantiates a <xref:System.TimeZoneInfo.TransitionTime> object.</span></span>

    2. <span data-ttu-id="aac9c-120">Définir la durée de transition de fin de l’ajustement de fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="aac9c-120">Define the ending transition time for the time zone adjustment.</span></span> <span data-ttu-id="aac9c-121">Cela nécessite un autre appel à la <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="aac9c-121">This requires another call to the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="aac9c-122">Cet appel de méthode instancie une seconde <xref:System.TimeZoneInfo.TransitionTime> objet.</span><span class="sxs-lookup"><span data-stu-id="aac9c-122">This method call instantiates a second <xref:System.TimeZoneInfo.TransitionTime> object.</span></span>

    3. <span data-ttu-id="aac9c-123">Appelez le <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> (méthode) et lui passer la date de début effective et de fin de l’ajustement, un <xref:System.TimeSpan> objet qui définit la durée de la transition et les deux <xref:System.TimeZoneInfo.TransitionTime> objets qui définissent quand les transitions vers et à partir de l’heure d’été temps se produisent.</span><span class="sxs-lookup"><span data-stu-id="aac9c-123">Call the <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> method and pass it the effective start and end dates of the adjustment, a <xref:System.TimeSpan> object that defines the amount of time in the transition, and the two <xref:System.TimeZoneInfo.TransitionTime> objects that define when the transitions to and from daylight saving time occur.</span></span> <span data-ttu-id="aac9c-124">Cet appel de méthode instancie un <xref:System.TimeZoneInfo.AdjustmentRule> objet.</span><span class="sxs-lookup"><span data-stu-id="aac9c-124">This method call instantiates a <xref:System.TimeZoneInfo.AdjustmentRule> object.</span></span>

    4. <span data-ttu-id="aac9c-125">Affecter le <xref:System.TimeZoneInfo.AdjustmentRule> objet vers un tableau de <xref:System.TimeZoneInfo.AdjustmentRule> objets.</span><span class="sxs-lookup"><span data-stu-id="aac9c-125">Assign the <xref:System.TimeZoneInfo.AdjustmentRule> object to an array of <xref:System.TimeZoneInfo.AdjustmentRule> objects.</span></span>

2. <span data-ttu-id="aac9c-126">Définir le nom d’affichage du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="aac9c-126">Define the time zone's display name.</span></span> <span data-ttu-id="aac9c-127">Le nom complet respecte un format relativement standard dans lequel l’offset du fuseau horaire par rapport au temps universel coordonné (UTC) est placée entre parenthèses et est suivie par une chaîne qui identifie le fuseau horaire, une ou plusieurs des villes dans le fuseau horaire, ou l’un ou plusieurs du parmi gra ou des régions dans le fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="aac9c-127">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

3. <span data-ttu-id="aac9c-128">Définir le nom de l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="aac9c-128">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="aac9c-129">En règle générale, cette chaîne est également utilisée comme identificateur de fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="aac9c-129">Typically, this string is also used as the time zone's identifier.</span></span>

4. <span data-ttu-id="aac9c-130">Définir le nom de l’heure d’été du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="aac9c-130">Define the name of the time zone's daylight time.</span></span>

5. <span data-ttu-id="aac9c-131">Si vous souhaitez utiliser un autre identificateur que le nom de standard du fuseau horaire, définissez l’identificateur de fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="aac9c-131">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

6. <span data-ttu-id="aac9c-132">Instancier une <xref:System.TimeSpan> objet qui définit le décalage du fuseau horaire à l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="aac9c-132">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="aac9c-133">Fuseaux horaires avec les heures sont ultérieures à l’heure UTC présentent un offset positif.</span><span class="sxs-lookup"><span data-stu-id="aac9c-133">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="aac9c-134">Fuseaux horaires avec les heures sont antérieures à l’heure UTC présentent un offset négatif.</span><span class="sxs-lookup"><span data-stu-id="aac9c-134">Time zones with times that are earlier than UTC have a negative offset.</span></span>

7. <span data-ttu-id="aac9c-135">Appelez le <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> méthode pour instancier le nouveau fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="aac9c-135">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="aac9c-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="aac9c-136">Example</span></span>

<span data-ttu-id="aac9c-137">L’exemple suivant définit un fuseau horaire Standard Central pour les États-Unis qui inclut des règles d’ajustement pour une variété d’intervalles de temps à partir de 1918 du présent.</span><span class="sxs-lookup"><span data-stu-id="aac9c-137">The following example defines a Central Standard Time zone for the United States that includes adjustment rules for a variety of time intervals from 1918 to the present.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

<span data-ttu-id="aac9c-138">Le fuseau horaire créé dans cet exemple comporte plusieurs règles d’ajustement.</span><span class="sxs-lookup"><span data-stu-id="aac9c-138">The time zone created in this example has multiple adjustment rules.</span></span> <span data-ttu-id="aac9c-139">Veillez à vous assurer que les dates de fin de toute règle d’ajustement de début et de fin ne se chevauchent pas avec les dates d’une autre règle d’ajustement.</span><span class="sxs-lookup"><span data-stu-id="aac9c-139">Care must be taken to ensure that the effective start and end dates of any adjustment rule do not overlap with the dates of another adjustment rule.</span></span> <span data-ttu-id="aac9c-140">S’il existe un chevauchement, un <xref:System.InvalidTimeZoneException> est levée.</span><span class="sxs-lookup"><span data-stu-id="aac9c-140">If there is an overlap, an <xref:System.InvalidTimeZoneException> is thrown.</span></span>

<span data-ttu-id="aac9c-141">Pour les règles d’ajustement de date flottante, la valeur 5 est passée à la `week` paramètre de la <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> méthode pour indiquer que la transition se produit la dernière semaine d’un mois donné.</span><span class="sxs-lookup"><span data-stu-id="aac9c-141">For floating adjustment rules, the value 5 is passed to the `week` parameter of the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> method to indicate that the transition occurs on the last week of a particular month.</span></span>

<span data-ttu-id="aac9c-142">Dans la création d’un tableau de <xref:System.TimeZoneInfo.AdjustmentRule> objets à utiliser dans le <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> appel de méthode, le code peut initialiser le tableau à la taille requise par le nombre d’ajustements à créer pour le fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="aac9c-142">In creating the array of <xref:System.TimeZoneInfo.AdjustmentRule> objects to use in the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> method call, the code could initialize the array to the size required by the number of adjustments to be created for the time zone.</span></span> <span data-ttu-id="aac9c-143">Au lieu de cela, cet exemple de code appelle la <xref:System.Collections.Generic.List%601.Add%2A> méthode pour ajouter chaque règle d’ajustement générique <xref:System.Collections.Generic.List%601> collection de <xref:System.TimeZoneInfo.AdjustmentRule> objets.</span><span class="sxs-lookup"><span data-stu-id="aac9c-143">Instead, this code example calls the <xref:System.Collections.Generic.List%601.Add%2A> method to add each adjustment rule to a generic <xref:System.Collections.Generic.List%601> collection of <xref:System.TimeZoneInfo.AdjustmentRule> objects.</span></span> <span data-ttu-id="aac9c-144">Le code appelle ensuite la <xref:System.Collections.Generic.List%601.CopyTo%2A> méthode pour copier les membres de cette collection dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="aac9c-144">The code then calls the <xref:System.Collections.Generic.List%601.CopyTo%2A> method to copy the members of this collection to the array.</span></span>

<span data-ttu-id="aac9c-145">L’exemple utilise également la <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> méthode pour définir des ajustements de date fixe.</span><span class="sxs-lookup"><span data-stu-id="aac9c-145">The example also uses the <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> method to define fixed-date adjustments.</span></span> <span data-ttu-id="aac9c-146">Cela ressemble à appeler le <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> (méthode), à ceci près qu’il requiert uniquement l’heure, le mois et le jour des paramètres de transition.</span><span class="sxs-lookup"><span data-stu-id="aac9c-146">This is similar to calling the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> method, except that it requires only the time, month, and day of the transition parameters.</span></span>

<span data-ttu-id="aac9c-147">L’exemple peut être testé à l’aide de code semblable au suivant :</span><span class="sxs-lookup"><span data-stu-id="aac9c-147">The example can be tested using code such as the following:</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a><span data-ttu-id="aac9c-148">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="aac9c-148">Compiling the code</span></span>

<span data-ttu-id="aac9c-149">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="aac9c-149">This example requires:</span></span>

* <span data-ttu-id="aac9c-150">Une référence à System.Core.dll à ajouter au projet.</span><span class="sxs-lookup"><span data-stu-id="aac9c-150">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="aac9c-151">Que les espaces de noms suivants soient importés :</span><span class="sxs-lookup"><span data-stu-id="aac9c-151">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="aac9c-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aac9c-152">See also</span></span>

<span data-ttu-id="aac9c-153">[Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
[vue d’ensemble du fuseau horaire](../../../docs/standard/datetime/time-zone-overview.md)
[Comment : créer des fuseaux horaires sans règles d’ajustement](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)</span><span class="sxs-lookup"><span data-stu-id="aac9c-153">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)</span></span>
