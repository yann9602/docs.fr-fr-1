---
title: "Get Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Get"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Get statement, syntax"
  - "Get statement"
  - "properties [Visual Basic], read-only"
  - "read-only properties"
  - "Get keyword"
  - "property procedures, Get statements"
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Get Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Déclare une procédure de propriété `Get` utilisée pour récupérer la valeur d'une propriété.  
  
## Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`attributelist`|Facultatif.  Consultez [Liste d'attributs](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Facultatif pour, au plus, l'une des instructions `Get` et `Set` de cette propriété.  Il peut s'agir de l'une des valeurs suivantes :<br /><br /> -   [Protégé](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privé](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consultez [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`statements`|Facultatif.  Une ou plusieurs instructions qui s'exécutent lors de l'appel de la procédure de propriété `Get`.|  
|`End Get`|Obligatoire.  Met fin à la définition de la procédure de propriété `Get`.|  
  
## Notes  
 Chaque propriété doit contenir une procédure de propriété `Get` à moins que la propriété soit marquée `WriteOnly`.  La procédure `Get` est utilisée pour retourner la valeur actuelle de la propriété.  
  
 Visual Basic appelle automatiquement la procédure `Get` d'une propriété lorsqu'une expression demande la valeur de la propriété.  
  
 Le corps de la déclaration de propriété peut contenir uniquement les procédures `Get` et `Set` de la propriété entre l'instruction [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) et `End Property`.  Il ne peut stocker rien d'autre que ces procédures.  En particulier, il ne peut pas stocker la valeur actuelle de la propriété.  Vous devez stocker cette valeur à l'extérieur de la propriété, car si vous la stockez à l'intérieur de l'une ou l'autre des procédures de propriété, l'autre procédure de propriété ne peut pas y accéder.  L'approche habituelle consiste à stocker la valeur dans une variable [Private](../../../visual-basic/language-reference/modifiers/private.md) déclarée au même niveau que la propriété.  Vous devez définir une procédure `Get` dans la propriété à laquelle elle s'applique.  
  
 La procédure `Get` prend par défaut le niveau d'accès de sa propriété conteneur à moins que vous utilisiez `accessmodifier` dans l'instruction `Get`.  
  
## Règles  
  
-   **Niveaux d'accès mixtes.** Si vous définissez une propriété en lecture\-écriture, vous pouvez éventuellement spécifier un niveau d'accès différent pour la procédure  `Get` ou la procédure `Set`, mais pas pour les deux.  Dans ce cas, le niveau d'accès de la procédure doit être plus restrictif que celui de la propriété.  Par exemple, si la propriété est déclarée `Friend`, vous pouvez déclarer la procédure `Get` `Private`, mais pas `Public`.  
  
     Si vous définissez une propriété `ReadOnly`, la procédure `Get` représente l'ensemble de la propriété.  Vous ne pouvez pas déclarer un niveau d'accès différent pour `Get`, parce que deux niveaux d'accès seront définis pour la propriété.  
  
-   **Type de retour.** L'instruction du nom [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) peut déclarer le type de données de la valeur qu'elle retourne.  La procédure `Get` retourne automatiquement ce type de données.  Vous pouvez spécifier un type de données ou le nom d'une énumération, d'une structure, d'une classe ou d'une interface.  
  
     Si l'instruction `Property` ne spécifie pas `returntype`, la procédure retourne `Object`.  
  
## Comportement  
  
-   **Retour d'une procédure.** Lorsque la procédure `Get` retourne au code appelant, l'exécution continue dans l'instruction qui a demandé la valeur de la propriété.  
  
     Les procédures de propriété `Get` peuvent retourner une valeur en utilisant [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) ou en assignant la valeur de retour au nom de la propriété.  Pour plus d'informations, consultez « Valeur de retour » dans [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     Les instructions `Exit Property` et `Return` provoquent la sortie immédiate d'une procédure de propriété.  Plusieurs instructions `Exit Property` et `Return` peuvent apparaître n'importe où dans la procédure, et vous pouvez associer des instructions `Exit Property` et `Return`.  
  
-   **Valeur de retour.** Pour retourner une valeur à partir d'une procédure `Get`, vous pouvez soit assigner la valeur au nom de la propriété, soit l'inclure dans une instruction [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).  L'instruction `Return` assigne simultanément la valeur de retour de la procédure `Get` et ferme la procédure.  
  
     Si vous utilisez `Exit Property` sans assigner de valeur au nom de la propriété, la procédure `Get` retourne la valeur par défaut pour le type de données de la propriété.  Pour plus d'informations, consultez « Valeur de retour » dans [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     L'exemple suivant illustre deux méthodes utilisées par la propriété en lecture seule `quoteForTheDay` pour retourner la valeur contenue dans la variable privée `quoteValue`.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_2.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_3.vb)]  
  
## Exemple  
 L'exemple suivant utilise l'instruction `Get` pour retourner la valeur d'une propriété.  
  
 [!code-vb[VbVbalrStatements#30](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_4.vb)]  
  
## Voir aussi  
 [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Walkthrough: Defining Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)