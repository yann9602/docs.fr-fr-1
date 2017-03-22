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
ms.openlocfilehash: 728d8393c44d777f9cc016d9cf66030036582ae4
ms.lasthandoff: 03/13/2017

---
# <a name="addhandler-statement"></a>AddHandler, instruction
Associe un événement à un gestionnaire d’événements au moment de l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Composants  
 `event`  
 Le nom de l’événement à gérer.  
  
 `eventhandler`  
 Le nom d’une procédure qui gère l’événement.  
  
## <a name="remarks"></a>Remarques  
 Le `AddHandler` et `RemoveHandler` vous permettent de démarrer et arrêter la gestion des événements à tout moment pendant l’exécution du programme.  
  
 La signature de la `eventhandler` procédure doit correspondre à la signature de l’événement `event`.  
  
 Le mot clé `Handles` et l'instruction `AddHandler` vous permettent de spécifier que des procédures particulières gèrent des événements particuliers, mais il existe des différences. L'instruction `AddHandler` connecte les procédures aux événements au moment de l'exécution. Utilisez le mot clé `Handles` quand vous définissez une procédure pour indiquer qu'elle gère un événement particulier. Pour plus d’informations, consultez [gère](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
>  Pour les événements personnalisés, les `AddHandler` instruction appelle l’événement `AddHandler` accesseur. Pour plus d’informations sur les événements personnalisés, consultez la page [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbalrEvents&#17;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [RemoveHandler (instruction)](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [Gère](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)
