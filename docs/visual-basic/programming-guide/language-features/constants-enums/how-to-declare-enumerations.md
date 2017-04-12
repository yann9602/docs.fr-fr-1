---
title: "Comment : déclarer des énumérations (Visual Basic) | Documents Microsoft"
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
- declarations, enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 8ff8bf2df39bed0597740bcda968283ec854f447
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-enumerations-visual-basic"></a>Comment : déclarer des énumérations (Visual Basic)
Vous créez une énumération avec la `Enum` instruction dans la section des déclarations d’une classe ou un module. Vous ne pouvez pas déclarer d’énumération dans une méthode. Pour spécifier le niveau d’accès approprié, utilisez `Private`, `Protected`, `Friend`, ou `Public`.  
  
 Un `Enum` type possède un nom, un type sous-jacent et un ensemble de champs, chacun représentant une constante. Le nom doit être valide [!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] qualificateur. Le type sous-jacent doit être un des types d’entiers :`Byte`, `Short`, `Long` ou `Integer`. `Integer` est la valeur par défaut. Les énumérations sont toujours fortement typées et ne sont pas interchangeables avec les types de nombre entier.  
  
 Les énumérations ne peut pas avoir de valeurs à virgule flottante. Si une énumération est assignée une valeur à virgule flottante `Option Strict On`, résulte d’une erreur du compilateur. Si `Option Strict` est `Off`, la valeur est automatiquement convertie en la `Enum` type.  
  
 Pour plus d’informations sur les noms et comment utiliser le `Imports` instruction pour rendre la qualification de noms inutiles, consultez [énumérations et Qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>Pour déclarer une énumération  
  
1.  Écrivez une déclaration qui inclut un niveau d’accès de code, le `Enum` (mot clé) et un nom valide, comme dans les exemples suivants, qui déclarent chacun un autre `Enum`.  
  
     [!code-vb[VbEnumsTask n °&3;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]  
  
2.  Définissez les constantes dans l’énumération. Par défaut, la première constante d’une énumération est initialisée à `0`, et les constantes suivantes sont initialisées à une valeur de plus que la constante précédente. Par exemple, l’énumération suivante, `Days`, contient une constante nommée `Sunday` avec la valeur `0`, une constante nommée `Monday` avec la valeur `1`, une constante nommée `Tuesday` avec la valeur de `2`, et ainsi de suite.  
  
     [!code-vb[VbEnumsTask n °&4;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]  
  
3.  Vous pouvez affecter explicitement des valeurs à des constantes dans une énumération à l’aide d’une instruction d’assignation. Vous pouvez affecter une valeur entière, y compris les nombres négatifs. Par exemple, vous souhaiterez peut-être constantes avec des valeurs inférieures à zéro pour représenter des conditions d’erreur. Dans l’énumération suivante, la constante `Invalid` est affectée de la valeur `–1`et la constante `Sunday` reçoit la valeur `0`. Car il s’agit de la première constante de l’énumération, `Saturday` est également initialisée à la valeur `0`. La valeur de `Monday` est `1` (plus que la valeur de `Sunday`), la valeur de `Tuesday` est `2`, et ainsi de suite.  
  
     [!code-vb[VbEnumsTask n °&5;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>Pour déclarer une énumération en tant que type explicite  
  
-   Spécifiez le type de l’énumération à l’aide de la `As` clause, comme illustré dans l’exemple suivant.  
  
     [!code-vb[VbEnumsTask n °&6;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et Qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Comment : faire référence à un membre d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Comment : parcourir une énumération dans Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [Comment : déterminer la chaîne associée à une valeur d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [Quand utiliser une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [Vue d’ensemble des constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Types de données littéraux et constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)
