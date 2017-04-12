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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0e70fca6a0608df5db43156f70196b4e5c9b2339
ms.lasthandoff: 03/13/2017

---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>Le modificateur 'Custom' n’est pas valide pour les événements déclarés sans types délégués explicites
Contrairement à un événement non personnalisé, un `Custom Event` déclaration nécessite une `As` clause après le nom de l’événement qui spécifie explicitement le type délégué pour l’événement.  
  
 Les événements non personnalisés peuvent être défini à l’aide un `As` clause et explicite type délégué, ou avec un paramètre de liste immédiatement après le nom de l’événement.  
  
 **ID d’erreur :** BC31122  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Définissez un délégué avec la même liste de paramètres que l’événement personnalisé.  
  
     Par exemple, si le `Custom Event` a été défini par `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, puis le délégué correspondant est le suivant.  
  
     [!code-vb[VbVbalrEventError&#18;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  Remplacez la liste des paramètres de l’événement personnalisé avec un `As` clause qui spécifie le type délégué.  
  
     L’exemple, `Custom Event` déclaration réécrite comme suit.  
  
     [!code-vb[VbVbalrEventError n °&19;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a>Exemple  
 Cet exemple déclare un `Custom Event` et spécifie les `As` clause avec un type délégué.  
  
 [!code-vb[VbVbalrEventError n °&2;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Delegate, instruction](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)
