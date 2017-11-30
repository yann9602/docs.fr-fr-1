---
title: "Les paramètres génériques utilisés comme types de paramètres optionnels doivent être contraints par classe"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords: BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a13ea66f12e54db4e585577e20e1f5396669f1a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a>Les paramètres génériques utilisés comme types de paramètres optionnels doivent être contraints par classe
Une procédure est déclarée avec un paramètre optionnel qui utilise un paramètre de type qui n’est pas contraint à être un type référence.  
  
 Vous devez toujours fournir une valeur par défaut pour chaque paramètre optionnel. Si le paramètre est d’un type référence, la valeur facultative doit être `Nothing`, qui est une valeur valide pour tout type référence. Toutefois, si le paramètre est d’un type valeur, ce type doit être un type de données élémentaire prédéfini par Visual Basic. Il s’agit, car un type de valeur composite, comme une structure définie par l’utilisateur, n’a aucune valeur par défaut valide.  
  
 Lorsque vous utilisez un paramètre de type pour un paramètre facultatif, vous devez vous assurer qu’il s’agit d’un type référence afin d’éviter le risque d’un type valeur sans valeur par défaut valide. Cela signifie que vous devez contraindre le paramètre de type avec le `Class` mot clé ou avec le nom d’une classe spécifique.  
  
 **ID d’erreur :** BC32124  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Contraindre le paramètre de type pour accepter uniquement un type référence, ou ne l’utilisez pas pour le paramètre facultatif.  
  
## <a name="see-also"></a>Voir aussi  
 [Types génériques en Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Liste de types](../../../visual-basic/language-reference/statements/type-list.md)  
 [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Paramètres facultatifs](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Nothing](../../../visual-basic/language-reference/nothing.md)
