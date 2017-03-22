---
title: "Constantes (Visual Basic) définis par l’utilisateur | Documents Microsoft"
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
- constants, circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants
- scope, constants
- constants, user-defined
- circular references between constants
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
caps.latest.revision: 19
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
ms.openlocfilehash: e5942d8663a8866b2f9794a86756f2bf25660ba5
ms.lasthandoff: 03/13/2017

---
# <a name="user-defined-constants-visual-basic"></a>Constantes définies par l'utilisateur (Visual Basic)
Une constante est un nom significatif qui prend la place d’un nombre ou une chaîne qui ne change pas. Les constantes stockent des valeurs qui, comme son nom l’indique, demeurent constantes lors de l’exécution d’une application. Vous pouvez utiliser les constantes qui sont définies par les contrôles ou les composants que vous utilisez, ou vous pouvez créer vos propres. Constantes que vous créez vous-même sont décrits comme *définie par l’utilisateur*.  
  
 Vous déclarez une constante avec la `Const` instruction, en utilisant les mêmes instructions que vous le feriez pour la création d’un nom de variable. Si `Option Strict` est `On`, vous devez déclarer explicitement le type de constante.  
  
## <a name="const-statement-usage"></a>Utilisation de l’instruction const  
 Un `Const` instruction peut représenter une valeur mathématique ou de date/heure :  
  
 [!code-vb[VbEnumsTask&#10;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 Elle peut également définir `String` constantes :  
  
 [!code-vb[VbEnumsTask&#13;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 L’expression située à droite du signe égal ( `=` ) est souvent un nombre ou une chaîne littérale, mais il peut également être une expression qui donne un nombre ou une chaîne (bien que cette expression ne peut pas contenir les appels aux fonctions). Vous pouvez même définir des constantes en termes de constantes définies préalablement :  
  
 [!code-vb[VbEnumsTask&#15;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## <a name="scope-of-user-defined-constants"></a>Portée des constantes définies par l’utilisateur  
 Un `Const` étendue de l’instruction est identique à celle d’une variable déclarée au même emplacement. Vous pouvez spécifier l’étendue d’une des manières suivantes :  
  
-   Pour créer une constante qui existe uniquement dans une procédure, vous devez le déclarer dans celle-ci.  
  
-   Pour créer une constante disponible pour toutes les procédures dans une classe, mais pas pour le code en dehors du module, déclarez-le dans la section des déclarations de la classe.  
  
-   Pour créer une constante qui est disponible pour tous les membres d’un assembly, mais pas pour les clients en dehors de l’assembly, déclarez-le à l’aide de le `Friend` mot clé dans la section des déclarations de la classe.  
  
-   Pour créer une constante disponible tout au long de l’application, déclarez-le à l’aide de la `Public` (mot clé) dans les déclarations de section de la classe.  
  
 Pour plus d’informations, consultez [Comment : déclarer une constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).  
  
### <a name="avoiding-circular-references"></a>Éviter des références circulaires  
 Étant donné que les constantes peuvent être définies en termes d’autres constantes, il est possible de créer par inadvertance un *cycle*, ou une référence circulaire entre deux constantes ou plus. Un cycle se produit lorsque vous disposez de deux ou plusieurs constantes publiques, chacun d’eux est défini en termes de l’autre, comme dans l’exemple suivant :  
  
 [!code-vb[VbEnumsTask&#16;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask&#17;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 Lorsqu’un cycle se produit, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] génère une erreur du compilateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Const (instruction)](../../../../visual-basic/language-reference/statements/const-statement.md)   
 [Types de données littéraux et constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Constantes et énumérations](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)   
 [Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [Vue d’ensemble des énumérations](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [Vue d’ensemble des constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Comment : déclarer une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Énumérations et Qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
