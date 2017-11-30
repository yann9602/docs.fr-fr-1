---
title: "Opérateur IsNot (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.isnot
helpviewer_keywords: IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 969fdebdf15a1f779075c58616ccd16c64976a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isnot-operator-visual-basic"></a>Opérateur IsNot (Visual Basic)
Compare deux variables de référence d’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Obligatoire. Valeur `Boolean`.  
  
 `object1`  
 Obligatoire. N’importe quel `Object` variable ou une expression.  
  
 `object2`  
 Obligatoire. N’importe quel `Object` variable ou une expression.  
  
## <a name="remarks"></a>Remarques  
 Le `IsNot` opérateur détermine si deux références d’objet font référence à des objets différents. Toutefois, il n’effectue pas de comparaisons de valeurs. Si `object1` et `object2` se rapportent à la même instance d’objet, `result` est `False`; le cas contraire, `result` est `True`.  
  
 `IsNot`est le contraire de la `Is` opérateur. L’avantage de `IsNot` est que vous pouvez éviter la syntaxe difficile avec `Not` et `Is`, qui peut être difficile à lire.  
  
 Vous pouvez utiliser la `Is` et `IsNot` opérateurs pour tester des objets à liaison anticipée et liaison tardive.  
  
> [!NOTE]
>  Le `IsNot` opérateur ne peut pas être utilisé pour comparer des expressions retournées par la `TypeOf` opérateur. Au lieu de cela, vous devez utiliser le `Not` et `Is` opérateurs.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant utilise à la fois le `Is` opérateur et la `IsNot` opérateur pour effectuer la même comparaison.  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Is (opérateur)](../../../visual-basic/language-reference/operators/is-operator.md)  
 [TypeOf (opérateur)](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Guide pratique : déterminer si deux objets sont identiques](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
