---
title: Widening (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 034099397c1d296a42712b8c202e2ac99a0fb43b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="widening-visual-basic"></a>Widening (Visual Basic)
Indique qu’un opérateur de conversion (`CType`) convertit une classe ou structure en un type qui peut contenir toutes les valeurs possibles de la classe ou la structure d’origine.  
  
## <a name="converting-with-the-widening-keyword"></a>Conversion avec le mot clé étendue  
 La procédure de conversion doit spécifier `Public Shared` à `Widening`.  
  
 Les conversions étendues réussissent toujours en cours d’exécution et sans jamais aucune perte de données. Exemples `Single` à `Double`, `Char` à `String`et un type dérivé vers son type de base. Cette dernière conversion est étendue parce que le type dérivé contient tous les membres du type de base et est donc une instance du type de base.  
  
 Le code utilisateur ne doit pas utiliser `CType` pour les conversions étendues, même si `Option Strict` est `On`.  
  
 Le `Widening` mot clé peut être utilisé dans ce contexte :  
  
 [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 Par exemple des définitions d’étendues et restrictives des opérateurs de conversion, consultez [Comment : définir un opérateur de Conversion](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Guide pratique : définir un opérateur](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [CType (fonction)](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Guide pratique : définir un opérateur de conversion](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
