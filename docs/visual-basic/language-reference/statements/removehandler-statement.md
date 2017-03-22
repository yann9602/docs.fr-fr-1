---
title: RemoveHandler (instruction) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
dev_langs:
- VB
helpviewer_keywords:
- RemoveHandler keyword
- RemoveHandler statement
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
caps.latest.revision: 14
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
ms.openlocfilehash: d35de576bd9e267800acc2a9bfd5761dd977622f
ms.lasthandoff: 03/13/2017

---
# <a name="removehandler-statement"></a>RemoveHandler, instruction
Supprime l’association entre un événement et un gestionnaire d’événements.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`event`|Le nom de l’événement géré.|  
|`eventhandler`|Le nom de la procédure en gérant l’événement.|  
  
## <a name="remarks"></a>Remarques  
 Le `AddHandler` et `RemoveHandler` vous permettent de démarrer et arrêter la gestion d’un événement spécifique à tout moment pendant l’exécution du programme.  
  
> [!NOTE]
>  Pour les événements personnalisés, les `RemoveHandler` instruction appelle l’événement `RemoveHandler` accesseur. Pour plus d’informations sur les événements personnalisés, consultez la page [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbalrEvents&#17;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [AddHandler (instruction)](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [Gère](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)
