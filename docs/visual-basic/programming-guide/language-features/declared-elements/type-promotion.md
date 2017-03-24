---
title: Type de Promotion (Visual Basic) | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declared elements, scope
- visibility, declared elements
- Partial keyword, unexpected results with type promotion
- scope, declared elements
- scope, Visual Basic
- type promotion
- declared elements, visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: 17
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d732e765fc28eaedc0deab477dbf9955a40e97c9
ms.lasthandoff: 03/13/2017

---
# <a name="type-promotion-visual-basic"></a>Promotion de type (Visual Basic)
Lorsque vous déclarez un élément de programmation dans un module, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] élève sa portée vers l’espace de noms contenant le module. Il s’agit en tant que *promotion de type*.  
  
 L’exemple suivant montre une définition squelette d’un module et deux membres de ce module.  
  
 [!code-vb[VbVbalrDeclaredElements n °&1;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]  
  
 Dans `projModule`, programmation éléments déclarés au niveau du module sont promus à `projNamespace`. Dans l’exemple précédent, `basicEnum` et `innerClass` sont promues, mais `numberSub` n’est pas, car il n’est pas déclaré au niveau du module.  
  
## <a name="effect-of-type-promotion"></a>Promotion de Type  
 L’effet de la promotion de type est que la chaîne de qualification n’a pas besoin d’inclure le nom du module. L’exemple suivant effectue deux appels à la procédure dans l’exemple précédent.  
  
 [!code-vb[VbVbalrDeclaredElements n °&2;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]  
  
 Dans l’exemple précédent, le premier appel utilise des chaînes de qualification complètes. Toutefois, cela n’est pas nécessaire en raison de la promotion de type. Le deuxième appel accède également aux membres du module sans inclure `projModule` dans les chaînes de qualification.  
  
## <a name="defeat-of-type-promotion"></a>Invalidation de la Promotion de Type  
 Si l’espace de noms possède déjà un membre portant le même nom qu’un membre de module, la promotion de type est invalidée pour ce membre de module. L’exemple suivant montre une définition squelette d’une énumération et d’un module dans le même espace de noms.  
  
 [!code-vb[VbVbalrDeclaredElements n °&3;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]  
  
 Dans l’exemple précédent, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne peut pas promouvoir la classe `abc` à `thisNameSpace` car il existe déjà une énumération du même nom au niveau de l’espace de noms. Pour accéder à `abcSub`, vous devez utiliser la chaîne de qualification complète `thisNamespace.thisModule.abc.abcSub`. Toutefois, la classe `xyz` est promue et vous pouvez accéder aux `xyzSub` avec la chaîne de qualification plus courte `thisNamespace.xyz.xyzSub`.  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>Invalidation de la Promotion de Type pour les Types partiels  
 Si une classe ou structure à l’intérieur d’un module utilise le [partielle](../../../../visual-basic/language-reference/modifiers/partial.md) (mot clé), la promotion de type est automatiquement invalidée pour cette classe ou structure, ou non de l’espace de noms possède un membre portant le même nom. D’autres éléments dans le module sont toujours éligibles pour la promotion de type.  
  
 **Conséquences.** Invalidation de la promotion de type d’une définition partielle peut provoquer des résultats inattendus et même des erreurs du compilateur. L’exemple suivant montre des définitions squelettes partielles d’une classe, y compris à l’intérieur d’un module.  
  
 [!code-vb[VbVbalrDeclaredElements n °&4;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]  
  
 Dans l’exemple précédent, le développeur peut s’attendre le compilateur fusionne les deux définitions partielles de `sampleClass`. Toutefois, le compilateur ne considère pas de promotion pour la définition partielle à l’intérieur de `sampleModule`. Par conséquent, il tente de compiler deux classes distinctes, toutes deux nommées `sampleClass` , mais avec des chemins d’accès de qualification différents.  
  
 Le compilateur fusionne des définitions partielles uniquement lorsque leurs chemins qualifiés complets sont identiques.  
  
## <a name="recommendations"></a>Recommandations  
 Les recommandations suivantes représentent les bonnes pratiques de programmation.  
  
-   **Noms uniques.** Lorsque vous avez un contrôle total sur l’appellation des éléments de programmation, il est toujours judicieux d’utiliser des noms uniques partout. Des noms identiques requièrent une qualification supplémentaire et peuvent rendre votre code plus difficile à lire. Elles peuvent entraîner des erreurs subtiles et des résultats inattendus.  
  
-   **Qualification complète.** Lorsque vous travaillez avec des modules et d’autres éléments dans le même espace de noms, l’approche la plus sûre consiste à toujours utiliser la qualification complète pour tous les éléments de programmation. Si la promotion de type est invalidée pour un membre de module et vous ne qualifiez pas complètement ce membre, vous pouvez accéder par inadvertance un élément de programmation différents.  
  
## <a name="see-also"></a>Voir aussi  
 [Module, instruction](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [Déclaration de Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Partielle](../../../../visual-basic/language-reference/modifiers/partial.md)   
 [Portée dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Comment : contrôler la portée d’une Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)   
 [Références aux éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
