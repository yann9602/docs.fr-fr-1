---
title: "AddHandler Statement | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.AddHandlerMethod"
  - "addhandler"
  - "vb.addhandler"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "AddHandler statement"
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# AddHandler Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Associe un événement à un gestionnaire d'événements au moment de l'exécution.  
  
## Syntaxe  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## Composants  
 `event`  
 Nom de l'événement à gérer.  
  
 `eventhandler`  
 Nom de la procédure qui gère l'événement.  
  
## Notes  
 Les instructions `AddHandler` et `RemoveHandler` vous permettent de débuter et d'arrêter la gestion d'un événement à tout moment au cours de l'exécution du programme.  
  
 La signature de la procédure `eventhandler` doit correspondre à celle de l'événement `event`.  
  
 Le mot clé `Handles` et l'instruction `AddHandler` permettent de spécifier que des procédures particulières gèrent des événements particuliers, mais il existe des différences.  L'instruction `AddHandler` connecte les procédures aux événements au moment de l'exécution.  Utilisez le mot clé `Handles` lors de la définition d'une procédure pour spécifier qu'il gère un événement particulier.  Pour plus d'informations, consultez [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
>  Pour les événements personnalisés, l'instruction `AddHandler` appelle l'accesseur `AddHandler` de l'événement.  Pour plus d'informations sur les événements personnalisés, consultez [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## Exemple  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## Voir aussi  
 [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)