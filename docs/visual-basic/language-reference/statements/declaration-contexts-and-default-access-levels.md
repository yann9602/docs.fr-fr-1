---
title: "Contextes de déclaration et niveaux d'accès par défaut (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b89b74a6c0393f6a52a0b5c1ddf6f66c505564ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Contextes de déclaration et niveaux d'accès par défaut (Visual Basic)
Cette rubrique décrit les types Visual Basic peuvent être déclarées dans les autres types, et ce que leurs niveaux d’accès par défaut n’est spécifié.  
  
## <a name="declaration-context-levels"></a>Niveaux de contexte de déclaration  
 Le *contexte de déclaration* d’un élément de programmation est la région de code dans laquelle elle est déclarée. Il s’agit souvent d’un autre élément de programmation, qui est alors appelé la *contenant l’élément*.  
  
 Les niveaux de contextes de déclaration sont les suivants :  
  
-   *Niveau de Namespace* — dans un fichier source ou un espace de noms mais pas dans une classe, une structure, un module ou une interface  
  
-   *Au niveau du module* — au sein d’une classe, une structure, un module ou une interface, mais pas dans une procédure ou un bloc  
  
-   *Niveau de la procédure* — au sein d’une procédure ou un bloc (tel que `If` ou `For`)  
  
 Le tableau suivant présente les niveaux d’accès par défaut pour les différents éléments de programmation déclarés, selon leurs contextes de déclaration.  
  
|Élément déclaré|Niveau de Namespace|Au niveau du module|Niveau de la procédure|  
|----------------------|---------------------|------------------|---------------------|  
|Variable ([Dim, instruction](../../../visual-basic/language-reference/statements/dim-statement.md))|Non autorisé|`Private`(`Public` dans `Structure`, non autorisé dans `Interface`)|`Public`|  
|Constante ([Const, instruction](../../../visual-basic/language-reference/statements/const-statement.md))|Non autorisé|`Private`(`Public` dans `Structure`, non autorisé dans `Interface`)|`Public`|  
|Énumération ([Enum, instruction](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|Non autorisé|  
|Classe ([Class, instruction](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|Non autorisé|  
|Structure ([Structure instruction](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|Non autorisé|  
|Module ([Module, instruction](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|Non autorisé|Non autorisé|  
|Interface ([Interface, instruction](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|Non autorisé|  
|Procédure ([Function, instruction](../../../visual-basic/language-reference/statements/function-statement.md), [Sub, instruction](../../../visual-basic/language-reference/statements/sub-statement.md))|Non autorisé|`Public`|Non autorisé|  
|Référence externe ([instruction Declare](../../../visual-basic/language-reference/statements/declare-statement.md))|Non autorisé|`Public`(non autorisé dans `Interface`)|Non autorisé|  
|Opérateur ([Operator, instruction](../../../visual-basic/language-reference/statements/operator-statement.md))|Non autorisé|`Public`(non autorisé dans `Interface` ou `Module`)|Non autorisé|  
|Propriété ([Property, instruction](../../../visual-basic/language-reference/statements/property-statement.md))|Non autorisé|`Public`|Non autorisé|  
|Propriété par défaut ([par défaut](../../../visual-basic/language-reference/modifiers/default.md))|Non autorisé|`Public`(non autorisé dans `Module`)|Non autorisé|  
|Événements ([Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md))|Non autorisé|`Public`|Non autorisé|  
|Délégué ([Delegate, instruction](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|Non autorisé|  
  
 Pour plus d’informations, consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)
