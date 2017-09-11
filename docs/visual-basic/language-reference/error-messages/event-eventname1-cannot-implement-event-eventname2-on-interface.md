---
title: "Événements «&lt;eventname1&gt;&quot;ne peut pas implémenter d’événement&quot;&lt;eventname2&gt;« sur l’interface&quot;&lt;interface&gt;&quot; car leurs types&quot; délégués&lt;delegate1&gt;&quot;et&quot;&lt;delegate2&gt;» ne correspondent pas | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
dev_langs:
- VB
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 340547d3673b651e988a6c1167bf7043360b04e4
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a><span data-ttu-id="1ee3d-102">Événements «&lt;eventname1&gt;'ne peut pas implémenter d’événement'&lt;eventname2&gt;« sur l’interface'&lt;interface&gt;' car leurs types' délégués&lt;delegate1&gt;'et'&lt;delegate2&gt;» ne correspondent pas</span><span class="sxs-lookup"><span data-stu-id="1ee3d-102">Event &#39;&lt;eventname1&gt;&#39; cannot implement event &#39;&lt;eventname2&gt;&#39; on interface &#39;&lt;interface&gt;&#39; because their delegate types &#39;&lt;delegate1&gt;&#39; and &#39;&lt;delegate2&gt;&#39; do not match</span></span>
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="1ee3d-103">Impossible d’implémenter un événement, car le type délégué de l’événement ne correspond pas au type de délégué de l’événement dans l’interface.</span><span class="sxs-lookup"><span data-stu-id="1ee3d-103"> cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="1ee3d-104">Cette erreur peut se produire quand vous définissez plusieurs événements dans une interface et essayez ensuite de les implémenter ensemble avec le même événement.</span><span class="sxs-lookup"><span data-stu-id="1ee3d-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="1ee3d-105">Un événement peut implémenter deux événements ou plus seulement si tous les événements implémentés sont déclarés à l’aide de la syntaxe `As` et s’ils spécifient le même type délégué.</span><span class="sxs-lookup"><span data-stu-id="1ee3d-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="1ee3d-106">**ID d’erreur :** BC31423</span><span class="sxs-lookup"><span data-stu-id="1ee3d-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1ee3d-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="1ee3d-107">To correct this error</span></span>  
  
-   <span data-ttu-id="1ee3d-108">Implémentez les événements séparément.</span><span class="sxs-lookup"><span data-stu-id="1ee3d-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="1ee3d-109">- ou -</span><span class="sxs-lookup"><span data-stu-id="1ee3d-109">—or—</span></span>  
  
-   <span data-ttu-id="1ee3d-110">Définissez les événements dans l’interface à l’aide du `As` syntaxe et spécifient le même type délégué.</span><span class="sxs-lookup"><span data-stu-id="1ee3d-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ee3d-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ee3d-111">See Also</span></span>  
 <span data-ttu-id="1ee3d-112">[Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="1ee3d-112">[Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="1ee3d-113"> [Delegate, instruction](../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="1ee3d-113"> [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="1ee3d-114"> [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="1ee3d-114"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
