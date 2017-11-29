---
title: "Comment : utiliser un dictionnaire pour stocker des instances d'événements (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0304f04233151d35c8ee18fe09feac91fbd0879b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a><span data-ttu-id="b2d60-102">Comment : utiliser un dictionnaire pour stocker des instances d'événements (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="b2d60-102">How to: Use a Dictionary to Store Event Instances (C# Programming Guide)</span></span>
<span data-ttu-id="b2d60-103">Une des façons d’utiliser `accessor-declarations` consiste à exposer un grand nombre d’événements sans allouer de champ à chaque événement, mais en utilisant à la place un dictionnaire pour stocker les instances d’événements.</span><span class="sxs-lookup"><span data-stu-id="b2d60-103">One use for `accessor-declarations` is to expose many events without allocating a field for each event, but instead using a Dictionary to store the event instances.</span></span> <span data-ttu-id="b2d60-104">Cette méthode n’est utile qu’en présence d’un grand nombre d’événements dont la plupart ne seront pas implémentés.</span><span class="sxs-lookup"><span data-stu-id="b2d60-104">This is only useful if you have many events, but you expect most of the events will not be implemented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2d60-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="b2d60-105">Example</span></span>  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b2d60-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2d60-106">See Also</span></span>  
 [<span data-ttu-id="b2d60-107">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b2d60-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b2d60-108">Événements</span><span class="sxs-lookup"><span data-stu-id="b2d60-108">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="b2d60-109">Délégués</span><span class="sxs-lookup"><span data-stu-id="b2d60-109">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
