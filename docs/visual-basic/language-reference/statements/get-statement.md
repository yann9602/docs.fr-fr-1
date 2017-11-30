---
title: Get, instruction
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c1ff062a5e3bf41794bd5b4c90f1e188d6d97480
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="get-statement"></a>Get, instruction
Déclare un `Get` procédure de propriété utilisée pour récupérer la valeur d’une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`attributelist`|Facultatif. Consultez [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Facultatif sur l’une de le `Get` et `Set` instructions dans cette propriété. Il peut s'agir d'une des valeurs suivantes :<br /><br /> -   [Protégé](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privé](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`statements`|Facultatif. Une ou plusieurs instructions qui s’exécutent lorsque le `Get` procédure de propriété est appelée.|  
|`End Get`|Obligatoire. Termine la définition de la `Get` procédure de propriété.|  
  
## <a name="remarks"></a>Remarques  
 Chaque propriété doit avoir un `Get` procédure de propriété, sauf si la propriété est marquée `WriteOnly`. Le `Get` procédure est utilisée pour retourner la valeur actuelle de la propriété.  
  
 Visual Basic appelle automatiquement d’une propriété `Get` procédure lorsqu’une expression demande la valeur de propriété.  
  
 Le corps de la déclaration de propriété peut contenir uniquement la propriété `Get` et `Set` procédures entre le [Property, instruction](../../../visual-basic/language-reference/statements/property-statement.md) et `End Property` instruction. Il ne peut pas stocker de celles de ces procédures. En particulier, il ne peut pas stocker la valeur de propriété en cours. Vous devez stocker cette valeur en dehors de la propriété, car si vous le stockez dans les procédures de propriété, les autres procédures de propriété ne peut pas y accéder. L’approche habituelle consiste à stocker la valeur dans un [privé](../../../visual-basic/language-reference/modifiers/private.md) variable déclarée au même niveau que la propriété. Vous devez définir un `Get` procédure à l’intérieur de la propriété à laquelle elle s’applique.  
  
 Le `Get` procédure par défaut est le niveau d’accès de sa propriété conteneur sauf si vous utilisez `accessmodifier` dans la `Get` instruction.  
  
## <a name="rules"></a>Règles  
  
-   **Niveaux d’accès mixtes.** Si vous définissez une propriété en lecture-écriture, vous pouvez éventuellement spécifier un niveau d’accès différent pour un le `Get` ou `Set` procédure, mais pas les deux. Si vous faites cela, le niveau d’accès de la procédure doit être plus restrictif que le niveau d’accès de la propriété. Par exemple, si la propriété est déclarée `Friend`, vous pouvez déclarer le `Get` procédure `Private`, mais pas `Public`.  
  
     Si vous définissez un `ReadOnly` propriété, le `Get` procédure représente la propriété entière. Vous ne pouvez pas déclarer un accès différent au niveau de `Get`, parce que seront définis à deux niveaux d’accès pour la propriété.  
  
-   **Type de retour.** Le [Property, instruction](../../../visual-basic/language-reference/statements/property-statement.md) peut déclarer le type de données de la valeur de retour. Le `Get` procédure retourne automatiquement ce type de données. Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, structure, classe ou d’interface.  
  
     Si le `Property` instruction ne spécifie pas `returntype`, la procédure retourne `Object`.  
  
## <a name="behavior"></a>Comportement  
  
-   **Retour d’une procédure.** Lorsque le `Get` procédure retourne au code appelant, l’exécution se poursuit au sein de l’instruction qui a demandé la valeur de propriété.  
  
     `Get`procédures de propriété peuvent retourner une valeur en utilisant le [instruction Return](../../../visual-basic/language-reference/statements/return-statement.md) ou en affectant la valeur de retour au nom de propriété. Pour plus d’informations, consultez « Valeur de retour » dans [Function, instruction](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     Le `Exit Property` et `Return` instructions provoquent la sortie immédiate d’une procédure de propriété. Un nombre quelconque de `Exit Property` et `Return` instructions peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger `Exit Property` et `Return` instructions.  
  
-   **Valeur de retour.** Pour retourner une valeur d’un `Get` procédure, vous pouvez affecter la valeur au nom de propriété ou l’inclure dans un [instruction Return](../../../visual-basic/language-reference/statements/return-statement.md). Le `Return` instruction assigne simultanément la `Get` procédure retourner de valeur et termine la procédure.  
  
     Si vous utilisez `Exit Property` sans lui assigner une valeur au nom de propriété, le `Get` procédure retourne la valeur par défaut pour le type de données de la propriété. Pour plus d’informations, consultez « Valeur de retour » dans [Function, instruction](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     L’exemple suivant illustre deux façons de la propriété en lecture seule `quoteForTheDay` peut retourner la valeur contenue dans la variable privée `quoteValue`.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_2.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_3.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la `Get` instruction pour retourner la valeur d’une propriété.  
  
 [!code-vb[VbVbalrStatements#30](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_4.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Set (instruction)](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Procédure pas à pas : définition de classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
