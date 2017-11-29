---
title: "&gt;&gt;Opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4eb0ed817c95905a679de5026bf6494eb72df078
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-visual-basic"></a>&gt;&gt;Opérateur (Visual Basic)
Effectue un décalage arithmétique vers la droite sur un modèle binaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Obligatoire. Valeur numérique intégrale. Le résultat du décalage du modèle binaire. Le type de données est identique à celle de `pattern`.  
  
 `pattern`  
 Obligatoire. Expression numérique intégrale. Le modèle de bits à décaler. Le type de données doit être un type intégral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ou `ULong`).  
  
 `amount`  
 Obligatoire. Expression numérique. Le nombre de bits à décaler le modèle binaire. Le type de données doit être `Integer` ou s’étendre à `Integer`.  
  
## <a name="remarks"></a>Remarques  
 Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés à une extrémité du résultat ne sont pas réintroduits à l’autre extrémité. Dans un décalage arithmétique vers la droite, les bits décalés au-delà de la position de bit plus à droite sont ignorés, et le bit de plus à gauche (authentification) est propagé dans les positions de bit libérées à gauche. Cela signifie que si `pattern` a une valeur négative, les positions libérées sont définies sur une ; sinon, elles sont définies à zéro.  
  
 Notez que les types de données `Byte`, `UShort`, `UInteger`, et `ULong` sont non signé, il n’existe aucun bit de signe à propager. Si `pattern` est de type non signé, les positions libérées sont toujours définies sur zéro.  
  
 Pour éviter un décalage plus de bits que peut en contenir le résultat, Visual Basic masque la valeur de `amount` avec un masque de taille correspondant au type de données de `pattern`. L’opérateur binaire AND de ces valeurs est utilisé pour le décalage. Les masques de taille sont les suivantes :  
  
|Type de données`pattern`|Masque de taille (décimal)|Masque de taille (hexadécimal)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|& H00000007|  
|`Short`, `UShort`|15|& H0000000F|  
|`Integer`, `UInteger`|31|& H0000001F|  
|`Long`, `ULong`|63|& H0000003F|  
  
 Si `amount` est égal à zéro, la valeur de `result` est identique à la valeur de `pattern`. Si `amount` est négatif, il est considéré comme une valeur non signée et masquée avec le masque de la taille appropriée.  
  
 Les décalages arithmétiques ne génèrent jamais des exceptions de dépassement de capacité.  
  
## <a name="overloading"></a>Surcharge  
 Le `>>` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure. Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini. Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `>>` opérateur pour effectuer des décalages arithmétiques vers la droite sur des valeurs intégrales. Le résultat a toujours les mêmes données de type que celui de l’expression décalée.  
  
 [!code-vb[VbVbalrOperators#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_1.vb)]  
  
 Les résultats de l’exemple précédent sont les suivantes :  
  
-   `result1`est 2560 (0000 1010 0000 0000).  
  
-   `result2`est de 160 (0000 0000 1010 0000).  
  
-   `result3`est 2 (0000 0000 0000 0010).  
  
-   `result4`est 640 (0000 0010 1000 0000).  
  
-   `result5`est égal à 0 (décalé de 15 places à droite).  
  
 Le nombre de positions de décalage pour `result4` est calculé comme 18 AND 15, ce qui est égal à 2.  
  
 L’exemple suivant montre les décalages arithmétiques sur une valeur négative.  
  
 [!code-vb[VbVbalrOperators#55](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_2.vb)]  
  
 Les résultats de l’exemple précédent sont les suivantes :  
  
-   `negresult1`est -512 (1111 1110 0000 0000).  
  
-   `negresult2`est -1 (le bit de signe est propagé).  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs de décalage de bits](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Opérateurs d’assignation](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [>>= (opérateur)](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)  
 [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Opérateurs arithmétiques en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
