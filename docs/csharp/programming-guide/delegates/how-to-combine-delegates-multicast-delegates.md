---
title: "Guide pratique pour combiner des délégués (délégués multicast) (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
caps.latest.revision: 17
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
ms.openlocfilehash: 617af10d3fb5f9371d5893b87a91a48639d44a53
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="84dbf-102">Guide pratique pour combiner des délégués (délégués multicast) (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="84dbf-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="84dbf-103">Cet exemple explique comment créer des délégués multicast.</span><span class="sxs-lookup"><span data-stu-id="84dbf-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="84dbf-104">Une propriété utile des objets [délégués](../../../csharp/language-reference/keywords/delegate.md) est que plusieurs objets peuvent être assignés à une instance de délégué à l’aide de l’opérateur `+`.</span><span class="sxs-lookup"><span data-stu-id="84dbf-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="84dbf-105">Le délégué multicast contient une liste des délégués assignés.</span><span class="sxs-lookup"><span data-stu-id="84dbf-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="84dbf-106">Quand le délégué multicast est appelé, il appelle les délégués dans la liste, dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="84dbf-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="84dbf-107">Seuls des délégués de même type peuvent être combinés.</span><span class="sxs-lookup"><span data-stu-id="84dbf-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="84dbf-108">Vous pouvez utiliser l’opérateur `-` pour supprimer un délégué de composant d’un délégué multicast.</span><span class="sxs-lookup"><span data-stu-id="84dbf-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84dbf-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="84dbf-109">Example</span></span>  
 <span data-ttu-id="84dbf-110">[!code-cs[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="84dbf-110">[!code-cs[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84dbf-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84dbf-111">See Also</span></span>  
 <span data-ttu-id="84dbf-112"><xref:System.MulticastDelegate></span><span class="sxs-lookup"><span data-stu-id="84dbf-112"><xref:System.MulticastDelegate></span></span>   
 <span data-ttu-id="84dbf-113">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="84dbf-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="84dbf-114">Événements</span><span class="sxs-lookup"><span data-stu-id="84dbf-114">Events</span></span>](../../../csharp/programming-guide/events/index.md)

