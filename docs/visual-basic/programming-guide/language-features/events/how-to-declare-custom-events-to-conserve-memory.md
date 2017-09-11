---
title: "Comment : déclarer des événements personnalisés pour économiser la mémoire (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declaring events, custom
- events [Visual Basic], custom
- custom events
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
caps.latest.revision: 11
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
ms.openlocfilehash: 130cbda875d6a56f826aefea341d233ea4b3731d
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="2fbbe-102">Comment : déclarer des événements personnalisés pour économiser la mémoire (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2fbbe-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="2fbbe-103">Il existe plusieurs cas où il est important qu’une application limiter son utilisation de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="2fbbe-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="2fbbe-104">Événements personnalisés permettent à l’application d’utiliser la mémoire uniquement pour les événements qu’il gère.</span><span class="sxs-lookup"><span data-stu-id="2fbbe-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="2fbbe-105">Par défaut, lorsqu’une classe déclare un événement, le compilateur alloue la mémoire pour un champ stocker les informations d’événement.</span><span class="sxs-lookup"><span data-stu-id="2fbbe-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="2fbbe-106">Si une classe comporte plusieurs événements inutilisés, leur mémoire inutilement.</span><span class="sxs-lookup"><span data-stu-id="2fbbe-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="2fbbe-107">Au lieu d’utiliser l’implémentation par défaut d’événements Visual Basic, vous pouvez utiliser des événements personnalisés pour gérer l’utilisation de la mémoire plus attentivement.</span><span class="sxs-lookup"><span data-stu-id="2fbbe-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fbbe-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="2fbbe-108">Example</span></span>  
 <span data-ttu-id="2fbbe-109">Dans cet exemple, la classe utilise une instance de la <xref:System.ComponentModel.EventHandlerList>(classe), stockée dans le `Events` champ pour stocker des informations sur les événements en cours d’utilisation.</xref:System.ComponentModel.EventHandlerList></span><span class="sxs-lookup"><span data-stu-id="2fbbe-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="2fbbe-110">Le <xref:System.ComponentModel.EventHandlerList>est une classe de liste optimisée conçue pour contenir des délégués.</xref:System.ComponentModel.EventHandlerList></span><span class="sxs-lookup"><span data-stu-id="2fbbe-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="2fbbe-111">Tous les événements de la classe utilisent le `Events` afin de suivre les méthodes qui gèrent chaque événement.</span><span class="sxs-lookup"><span data-stu-id="2fbbe-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 <span data-ttu-id="2fbbe-112">[!code-vb[VbVbalrEvents&#22;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2fbbe-112">[!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fbbe-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fbbe-113">See Also</span></span>  
 <span data-ttu-id="2fbbe-114"><xref:System.ComponentModel.EventHandlerList></xref:System.ComponentModel.EventHandlerList></span><span class="sxs-lookup"><span data-stu-id="2fbbe-114"><xref:System.ComponentModel.EventHandlerList></span></span>   
<span data-ttu-id="2fbbe-115"> [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="2fbbe-115"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md) </span></span>  
<span data-ttu-id="2fbbe-116"> [Guide pratique : déclarer des événements personnalisés pour éviter les blocages](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)</span><span class="sxs-lookup"><span data-stu-id="2fbbe-116"> [How to: Declare Custom Events To Avoid Blocking](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)</span></span>
