---
title: "Comment : déclarer des événements personnalisés pour éviter les blocages (Visual Basic) | Documents Microsoft"
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
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: 12
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
ms.openlocfilehash: 52181d1c307e4e312f4511719e540fd6d5bfcfa8
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="743d6-102">Comment : déclarer des événements personnalisés pour éviter les blocages (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="743d6-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="743d6-103">Il existe plusieurs cas où il est important de ce gestionnaire d’un événements ne bloque pas les gestionnaires d’événements suivants.</span><span class="sxs-lookup"><span data-stu-id="743d6-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="743d6-104">Événements personnalisés permettent à l’événement à appeler ses gestionnaires d’événements de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="743d6-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="743d6-105">Par défaut, le champ du magasin de stockage pour une déclaration d’événement est un délégué multicast qui associe en série tous les gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="743d6-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="743d6-106">Cela signifie que si un gestionnaire met un certain temps, il bloque les autres gestionnaires jusqu'à la fin.</span><span class="sxs-lookup"><span data-stu-id="743d6-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="743d6-107">(Gestionnaires d’événements valides doivent jamais exécuter des opérations longues ou potentielles de blocage).</span><span class="sxs-lookup"><span data-stu-id="743d6-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="743d6-108">Au lieu d’utiliser l’implémentation par défaut d’événements Visual Basic, vous pouvez utiliser un événement personnalisé pour exécuter les gestionnaires d’événements de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="743d6-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="743d6-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="743d6-109">Example</span></span>  
 <span data-ttu-id="743d6-110">Dans cet exemple, le `AddHandler` accesseur ajoute le délégué pour chaque gestionnaire de la `Click` événement un <xref:System.Collections.ArrayList>stockés dans le `EventHandlerList` champ.</xref:System.Collections.ArrayList></span><span class="sxs-lookup"><span data-stu-id="743d6-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="743d6-111">Lorsque le code déclenche le `Click` événement, le `RaiseEvent` accesseur appelle tous les délégués de gestionnaires d’événements de façon asynchrone à l’aide de la <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>méthode.</xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A></span><span class="sxs-lookup"><span data-stu-id="743d6-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="743d6-112">Cette méthode appelle chaque gestionnaire sur un thread de travail et retourne immédiatement, donc les gestionnaires ne peut pas se bloquer mutuellement.</span><span class="sxs-lookup"><span data-stu-id="743d6-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 <span data-ttu-id="743d6-113">[!code-vb[27 VbVbalrEvents](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="743d6-113">[!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="743d6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="743d6-114">See Also</span></span>  
 <span data-ttu-id="743d6-115"><xref:System.Collections.ArrayList></xref:System.Collections.ArrayList></span><span class="sxs-lookup"><span data-stu-id="743d6-115"><xref:System.Collections.ArrayList></span></span>   
 <span data-ttu-id="743d6-116"><xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A></xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A></span><span class="sxs-lookup"><span data-stu-id="743d6-116"><xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A></span></span>   
<span data-ttu-id="743d6-117"> [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="743d6-117"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md) </span></span>  
<span data-ttu-id="743d6-118"> [Guide pratique : déclarer des événements personnalisés pour économiser la mémoire](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)</span><span class="sxs-lookup"><span data-stu-id="743d6-118"> [How to: Declare Custom Events To Conserve Memory](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)</span></span>
