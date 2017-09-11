---
title: "Le modificateur &quot;Custom&quot; n’est pas valide pour les événements déclarés sans types délégués explicites | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31122
- bc31122
dev_langs:
- VB
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
caps.latest.revision: 9
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
ms.openlocfilehash: 449e5a690f06ce35d1ccc799daf5f2c1ad1c6dac
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="f6056-102">Le modificateur 'Custom' n’est pas valide pour les événements déclarés sans types délégués explicites</span><span class="sxs-lookup"><span data-stu-id="f6056-102">&#39;Custom&#39; modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="f6056-103">Contrairement à un événement non personnalisé, un `Custom Event` déclaration nécessite une `As` clause après le nom de l’événement qui spécifie explicitement le type délégué pour l’événement.</span><span class="sxs-lookup"><span data-stu-id="f6056-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="f6056-104">Les événements non personnalisés peuvent être défini à l’aide un `As` clause et explicite type délégué, ou avec un paramètre de liste immédiatement après le nom de l’événement.</span><span class="sxs-lookup"><span data-stu-id="f6056-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="f6056-105">**ID d’erreur :** BC31122</span><span class="sxs-lookup"><span data-stu-id="f6056-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f6056-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="f6056-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="f6056-107">Définissez un délégué avec la même liste de paramètres que l’événement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f6056-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="f6056-108">Par exemple, si le `Custom Event` a été défini par `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, puis le délégué correspondant est le suivant.</span><span class="sxs-lookup"><span data-stu-id="f6056-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     <span data-ttu-id="f6056-109">[!code-vb[VbVbalrEventError&#18;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f6056-109">[!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]</span></span>  
  
2.  <span data-ttu-id="f6056-110">Remplacez la liste des paramètres de l’événement personnalisé avec un `As` clause qui spécifie le type délégué.</span><span class="sxs-lookup"><span data-stu-id="f6056-110">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="f6056-111">L’exemple, `Custom Event` déclaration réécrite comme suit.</span><span class="sxs-lookup"><span data-stu-id="f6056-111">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     <span data-ttu-id="f6056-112">[!code-vb[VbVbalrEventError n °&19;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="f6056-112">[!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6056-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="f6056-113">Example</span></span>  
 <span data-ttu-id="f6056-114">Cet exemple déclare un `Custom Event` et spécifie les `As` clause avec un type délégué.</span><span class="sxs-lookup"><span data-stu-id="f6056-114">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 <span data-ttu-id="f6056-115">[!code-vb[VbVbalrEventError n °&2;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="f6056-115">[!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6056-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6056-116">See Also</span></span>  
 <span data-ttu-id="f6056-117">[Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="f6056-117">[Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="f6056-118"> [Delegate, instruction](../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="f6056-118"> [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="f6056-119"> [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="f6056-119"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
