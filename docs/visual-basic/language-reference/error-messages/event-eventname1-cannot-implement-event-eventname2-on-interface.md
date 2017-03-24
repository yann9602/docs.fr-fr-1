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
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: b6253b3e9ad07c3715c55a8cfd0891792b45a452
ms.lasthandoff: 03/13/2017

---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a>Événements «&lt;eventname1&gt;'ne peut pas implémenter d’événement'&lt;eventname2&gt;« sur l’interface'&lt;interface&gt;' car leurs types' délégués&lt;delegate1&gt;'et'&lt;delegate2&gt;» ne correspondent pas
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Impossible d’implémenter un événement, car le type délégué de l’événement ne correspond pas au type de délégué de l’événement dans l’interface. Cette erreur peut se produire quand vous définissez plusieurs événements dans une interface et essayez ensuite de les implémenter ensemble avec le même événement. Un événement peut implémenter deux événements ou plus seulement si tous les événements implémentés sont déclarés à l’aide de la syntaxe `As` et s’ils spécifient le même type délégué.  
  
 **ID d’erreur :** BC31423  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Implémentez les événements séparément.  
  
     - ou -  
  
-   Définissez les événements dans l’interface à l’aide du `As` syntaxe et spécifient le même type délégué.  
  
## <a name="see-also"></a>Voir aussi  
 [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Delegate, instruction](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)
