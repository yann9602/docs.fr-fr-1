---
title: "Set Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Set"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "property procedures, Set statements"
  - "Set statement"
  - "Set statement, syntax"
  - "write-only properties"
  - "properties [Visual Basic], write-only"
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Set Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Déclare une procédure de propriété `Set` utilisée pour assigner une valeur à une propriété.  
  
## Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## Composants  
 `attributelist`  
 Facultatif.  Consultez [Liste d'attributs](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Facultatif pour, au plus, l'une des instructions `Get` et `Set` de cette propriété.  Il peut s'agir de l'une des valeurs suivantes :  
  
-   [Protégé](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [Privé](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 Consultez [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `value`  
 Obligatoire.  Paramètre contenant la nouvelle valeur de la propriété.  
  
 `datatype`  
 Requis si `Option Strict` a la valeur `On`.  Type de données du paramètre `value`.  Le type de données spécifié doit être identique à celui de la propriété si cette instruction `Set` est déclarée.  
  
 `statements`  
 Facultatif.  Une ou plusieurs instructions qui s'exécutent lors de l'appel de la procédure de propriété `Set`.  
  
 `End Set`  
 Obligatoire.  Met fin à la définition de la procédure de propriété `Set`.  
  
## Notes  
 Chaque propriété doit contenir une procédure de propriété `Set` à moins que la propriété soit marquée `ReadOnly`.  La procédure `Set` est utilisée pour définir la valeur de la propriété.  
  
 Visual Basic appelle automatiquement la procédure `Set` d'une propriété lorsqu'une instruction d'assignation fournit une valeur à stocker dans la propriété.  
  
 Visual Basic passe un paramètre à la procédure `Set` pendant les assignations de propriétés.  Si vous ne précisez pas de paramètre pour `Set`, l'environnement de développement intégré \(IDE\) utilise un paramètre implicite appelé `value`.  Ce paramètre contient la valeur à assigner à la propriété.  Vous enregistrez généralement cette valeur dans une variable locale privée et la retournez à chaque appel de la procédure `Get`.  
  
 Le corps de la déclaration de propriété peut contenir uniquement les procédures `Get` et `Set` de la propriété entre l'instruction [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) et `End Property`.  Il ne peut stocker rien d'autre que ces procédures.  En particulier, il ne peut pas stocker la valeur actuelle de la propriété.  Vous devez stocker cette valeur à l'extérieur de la propriété, car si vous la stockez à l'intérieur de l'une ou l'autre des procédures de propriété, l'autre procédure de propriété ne peut pas y accéder.  L'approche habituelle consiste à stocker la valeur dans une variable [Private](../../../visual-basic/language-reference/modifiers/private.md) déclarée au même niveau que la propriété.  Vous devez définir une procédure `Set` dans la propriété à laquelle elle s'applique.  
  
 La procédure `Set` prend par défaut le niveau d'accès de sa propriété conteneur à moins que vous utilisiez `accessmodifier` dans l'instruction `Set`.  
  
## Règles  
  
-   **Niveaux d'accès mixtes.** Si vous définissez une propriété en lecture\-écriture, vous pouvez éventuellement spécifier un niveau d'accès différent pour la procédure  `Get` ou la procédure `Set`, mais pas pour les deux.  Dans ce cas, le niveau d'accès de la procédure doit être plus restrictif que celui de la propriété.  Par exemple, si la propriété est déclarée `Friend`, vous pouvez déclarer la procédure `Set` `Private`, mais pas `Public`.  
  
     Si vous définissez une propriété `WriteOnly`, la procédure `Set` représente l'ensemble de la propriété.  Vous ne pouvez pas déclarer un niveau d'accès différent pour `Set`, parce que deux niveaux d'accès seront définis pour la propriété.  
  
## Comportement  
  
-   **Retour d'une procédure de propriété.** Lorsque la procédure `Set` retourne au code appelant, l'exécution continue à suivre l'instruction qui a fourni la valeur à stocker.  
  
     Les procédures de propriété `Set` peuvent être retournées à l'aide de [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) ou de [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).  
  
     Les instructions `Exit Property` et `Return` provoquent la sortie immédiate d'une procédure de propriété.  Plusieurs instructions `Exit Property` et `Return` peuvent apparaître n'importe où dans la procédure, et vous pouvez associer des instructions `Exit Property` et `Return`.  
  
## Exemple  
 L'exemple suivant utilise l'instruction `Set` pour définir la valeur d'une propriété.  
  
 [!code-vb[VbVbalrStatements#55](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/set-statement_1.vb)]  
  
## Voir aussi  
 [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Procédures de propriété](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)