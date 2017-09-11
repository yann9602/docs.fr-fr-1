---
title: AddHandler (instruction) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
dev_langs:
- VB
helpviewer_keywords:
- AddHandler statement
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
caps.latest.revision: 15
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
ms.openlocfilehash: cd821a568a35f33c722c1631eb7fbaf8f877cf4f
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="addhandler-statement"></a><span data-ttu-id="4114c-102">AddHandler, instruction</span><span class="sxs-lookup"><span data-stu-id="4114c-102">AddHandler Statement</span></span>
<span data-ttu-id="4114c-103">Associe un événement à un gestionnaire d’événements au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="4114c-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4114c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4114c-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="4114c-105">Composants</span><span class="sxs-lookup"><span data-stu-id="4114c-105">Parts</span></span>  
 `event`  
 <span data-ttu-id="4114c-106">Le nom de l’événement à gérer.</span><span class="sxs-lookup"><span data-stu-id="4114c-106">The name of the event to handle.</span></span>  
  
 `eventhandler`  
 <span data-ttu-id="4114c-107">Le nom d’une procédure qui gère l’événement.</span><span class="sxs-lookup"><span data-stu-id="4114c-107">The name of a procedure that handles the event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4114c-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="4114c-108">Remarks</span></span>  
 <span data-ttu-id="4114c-109">Le `AddHandler` et `RemoveHandler` vous permettent de démarrer et arrêter la gestion des événements à tout moment pendant l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="4114c-109">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="4114c-110">La signature de la `eventhandler` procédure doit correspondre à la signature de l’événement `event`.</span><span class="sxs-lookup"><span data-stu-id="4114c-110">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="4114c-111">Le mot clé `Handles` et l'instruction `AddHandler` vous permettent de spécifier que des procédures particulières gèrent des événements particuliers, mais il existe des différences.</span><span class="sxs-lookup"><span data-stu-id="4114c-111">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="4114c-112">L'instruction `AddHandler` connecte les procédures aux événements au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="4114c-112">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="4114c-113">Utilisez le mot clé `Handles` quand vous définissez une procédure pour indiquer qu'elle gère un événement particulier.</span><span class="sxs-lookup"><span data-stu-id="4114c-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="4114c-114">Pour plus d’informations, consultez [gère](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4114c-114">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4114c-115">Pour les événements personnalisés, les `AddHandler` instruction appelle l’événement `AddHandler` accesseur.</span><span class="sxs-lookup"><span data-stu-id="4114c-115">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="4114c-116">Pour plus d’informations sur les événements personnalisés, consultez la page [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4114c-116">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4114c-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="4114c-117">Example</span></span>  
 <span data-ttu-id="4114c-118">[!code-vb[VbVbalrEvents&#17;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4114c-118">[!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4114c-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4114c-119">See Also</span></span>  
 <span data-ttu-id="4114c-120">[RemoveHandler (instruction)](../../../visual-basic/language-reference/statements/removehandler-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4114c-120">[RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) </span></span>  
<span data-ttu-id="4114c-121"> [Gère](../../../visual-basic/language-reference/statements/handles-clause.md) </span><span class="sxs-lookup"><span data-stu-id="4114c-121"> [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) </span></span>  
<span data-ttu-id="4114c-122"> [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4114c-122"> [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="4114c-123"> [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="4114c-123"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
