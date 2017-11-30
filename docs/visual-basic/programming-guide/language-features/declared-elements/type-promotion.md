---
title: Promotion de type (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f3a55c023afe7afe96f862f0b3cbbdb03a15b902
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="type-promotion-visual-basic"></a>Promotion de type (Visual Basic)
Lorsque vous déclarez un élément de programmation dans un module, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] élève sa portée vers l’espace de noms contenant le module. Il s’agit en tant que *promotion de type*.  
  
 L’exemple suivant montre une définition squelette d’un module et de deux membres de ce module.  
  
 [!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]  
  
 Dans `projModule`, programmation éléments déclarés au niveau du module sont promus à `projNamespace`. Dans l’exemple précédent, `basicEnum` et `innerClass` sont promues, mais `numberSub` n’est pas, car il n’est pas déclaré au niveau du module.  
  
## <a name="effect-of-type-promotion"></a>Promotion de Type  
 L’effet de la promotion de type est que la chaîne de qualification n’a pas besoin d’inclure le nom de module. L’exemple suivant effectue deux appels à la procédure dans l’exemple précédent.  
  
 [!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]  
  
 Dans l’exemple précédent, le premier appel utilise des chaînes de qualification complète. Toutefois, cela n’est pas nécessaire en raison de la promotion de type. Le deuxième appel accède également aux membres du module sans inclure `projModule` dans les chaînes de qualification.  
  
## <a name="defeat-of-type-promotion"></a>Invalidation de la Promotion de Type  
 Si l’espace de noms comporte déjà un membre portant le même nom qu’un membre de module, la promotion de type est invalidée pour ce membre de module. L’exemple suivant montre une définition squelette d’une énumération et d’un module au sein du même espace de noms.  
  
 [!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]  
  
 Dans l’exemple précédent, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ne peut pas promouvoir la classe `abc` à `thisNameSpace` , car il existe déjà une énumération du même nom au niveau de l’espace de noms. Pour accéder à `abcSub`, vous devez utiliser la chaîne de qualification complète `thisNamespace.thisModule.abc.abcSub`. Toutefois, la classe `xyz` est promue, vous pouvez accéder à `xyzSub` avec la chaîne de qualification plus courte `thisNamespace.xyz.xyzSub`.  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>Invalidation de la Promotion de Type pour les Types partiels  
 Si une classe ou structure à l’intérieur d’un module utilise la [partielle](../../../../visual-basic/language-reference/modifiers/partial.md) (mot clé), la promotion de type est automatiquement invalidée pour cette classe ou structure, ou non de l’espace de noms a un membre portant le même nom. Autres éléments dans le module sont toujours éligibles pour la promotion de type.  
  
 **Conséquences.** Invalidation de la promotion de type d’une définition partielle peut provoquer des résultats inattendus et même des erreurs du compilateur. L’exemple suivant montre des définitions partielles squelettes d’une classe, y compris à l’intérieur d’un module.  
  
 [!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]  
  
 Dans l’exemple précédent, le développeur peut s’attendre le compilateur fusionne les deux définitions partielles de `sampleClass`. Toutefois, le compilateur ne tient pas compte pour la définition partielle à l’intérieur de la promotion `sampleModule`. Par conséquent, il tente de compiler deux classes distinctes, toutes deux nommées `sampleClass` , mais avec des chemins d’accès de qualification différents.  
  
 Le compilateur fusionne des définitions partielles uniquement lorsque leurs chemins qualifiés complets sont identiques.  
  
## <a name="recommendations"></a>Recommandations  
 Les recommandations suivantes représentent les bonnes pratiques de programmation.  
  
-   **Noms uniques.** Lorsque vous avez un contrôle total sur la dénomination des éléments de programmation, il est toujours de judicieux d’utiliser des noms uniques partout. Des noms identiques requièrent une qualification supplémentaire et peuvent rendre votre code plus difficile à lire. Elles peuvent entraîner des erreurs subtiles et des résultats inattendus.  
  
-   **Qualification complète.** Lorsque vous travaillez avec des modules et autres éléments dans le même espace de noms, l’approche la plus sûre consiste à toujours utiliser la qualification complète pour tous les éléments de programmation. Si la promotion de type est invalidée pour un membre de module et que vous ne qualifiez pas complètement ce membre, vous pouvez accéder par inadvertance un élément de programmation différent.  
  
## <a name="see-also"></a>Voir aussi  
 [Module (instruction)](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [Namespace (instruction)](../../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [Portée dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Guide pratique : contrôler la portée d'une variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [Références aux éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
