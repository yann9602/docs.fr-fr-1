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
ms.openlocfilehash: 4f8ce32a3b4da411a73010119283ce9661b82a6c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>Comment : déclarer des événements personnalisés pour économiser la mémoire (Visual Basic)
Il existe plusieurs cas où il est important qu’une application limiter son utilisation de la mémoire. Événements personnalisés permettent à l’application d’utiliser la mémoire uniquement pour les événements qu’il gère.  
  
 Par défaut, lorsqu’une classe déclare un événement, le compilateur alloue la mémoire pour un champ stocker les informations d’événement. Si une classe comporte plusieurs événements inutilisés, leur mémoire inutilement.  
  
 Au lieu d’utiliser l’implémentation par défaut d’événements Visual Basic, vous pouvez utiliser des événements personnalisés pour gérer l’utilisation de la mémoire plus attentivement.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la classe utilise une instance de la <xref:System.ComponentModel.EventHandlerList>(classe), stockée dans le `Events` champ pour stocker des informations sur les événements en cours d’utilisation.</xref:System.ComponentModel.EventHandlerList> Le <xref:System.ComponentModel.EventHandlerList>est une classe de liste optimisée conçue pour contenir des délégués.</xref:System.ComponentModel.EventHandlerList>  
  
 Tous les événements de la classe utilisent le `Events` afin de suivre les méthodes qui gèrent chaque événement.  
  
 [!code-vb[VbVbalrEvents&#22;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ComponentModel.EventHandlerList></xref:System.ComponentModel.EventHandlerList>   
 [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md)   
 [Guide pratique : déclarer des événements personnalisés pour éviter les blocages](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
