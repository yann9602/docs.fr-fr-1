---
title: "Guide pratique pour utiliser un dictionnaire servant à stocker des instances d'événements (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bca140ee4d7519f67d6e896757b3187ac169de1f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a><span data-ttu-id="462a1-102">Guide pratique pour utiliser un dictionnaire servant à stocker des instances d'événements (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="462a1-102">How to: Use a Dictionary to Store Event Instances (C# Programming Guide)</span></span>
<span data-ttu-id="462a1-103">Une des façons d’utiliser `accessor-declarations` consiste à exposer un grand nombre d’événements sans allouer de champ à chaque événement, mais en utilisant à la place un dictionnaire pour stocker les instances d’événements.</span><span class="sxs-lookup"><span data-stu-id="462a1-103">One use for `accessor-declarations` is to expose many events without allocating a field for each event, but instead using a Dictionary to store the event instances.</span></span> <span data-ttu-id="462a1-104">Cette méthode n’est utile qu’en présence d’un grand nombre d’événements dont la plupart ne seront pas implémentés.</span><span class="sxs-lookup"><span data-stu-id="462a1-104">This is only useful if you have many events, but you expect most of the events will not be implemented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="462a1-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="462a1-105">Example</span></span>  
 <span data-ttu-id="462a1-106">[!code-cs[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="462a1-106">[!code-cs[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="462a1-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="462a1-107">See Also</span></span>  
 <span data-ttu-id="462a1-108">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="462a1-108">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="462a1-109">[Événements](../../../csharp/programming-guide/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="462a1-109">[Events](../../../csharp/programming-guide/events/index.md) </span></span>  
 [<span data-ttu-id="462a1-110">Délégués</span><span class="sxs-lookup"><span data-stu-id="462a1-110">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)

