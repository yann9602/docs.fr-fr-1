---
title: "Quand utiliser une énumération (Visual Basic) | Documents Microsoft"
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
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 12
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
ms.openlocfilehash: f22102a2e1e7eafd7fcf4db1f46af2cc622eba70
ms.lasthandoff: 03/13/2017

---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Quand utiliser une énumération (Visual Basic)
Les énumérations offrent un moyen simple de travailler avec des ensembles de constantes associées. Une énumération, ou `Enum`, est un nom symbolique pour un ensemble de valeurs. Les énumérations sont traitées comme des types de données, et vous pouvez les utiliser pour créer des jeux de constantes utilisables avec des variables et des propriétés.  
  
## <a name="when-to-use-an-enumeration"></a>Quand utiliser une énumération  
 Chaque fois qu’une procédure accepte un jeu limité de variables, envisagez d’utiliser une énumération. Énumérations rendent le code plus clair et plus lisible, en particulier lorsque des noms explicites sont utilisés.  
  
 Les avantages de l’utilisation des énumérations :  
  
-   Réduit les erreurs dues à la transposition ou entrée incorrecte de nombres.  
  
-   Rend plus facile à modifier les valeurs dans le futur.  
  
-   Rend le code plus facile à lire, ce qui signifie qu’il est peu probable que les erreurs lisibilité il.  
  
-   Garantit la compatibilité ascendante. Avec des énumérations, votre code est moins susceptible d’échouer si l’avenir quelqu'un modifie les valeurs correspondant aux noms de membres.  
  
## <a name="naming-enumerations"></a>Énumérations d’affectation de noms  
 Utilisez une convention d’affectation de noms pour les membres de l’énumération. Lorsque [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] rencontre un nom de membre d’énumération, une exception peut être levée si d’autres bibliothèques de types référencées contiennent le même nom. Utilisez un préfixe unique qui identifie les valeurs à partir de votre application ou composant.  
  
 Lorsque vous faites référence à un membre d’une énumération, vous devez qualifier le nom du membre avec le nom d’énumération ou bien utiliser la `Imports` instruction. Pour plus d’informations, consultez [énumérations et Qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Énumérations prédéfinies  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fournit plusieurs énumérations prédéfinies, telles que `FirstDayOfWeek` et `MsgBoxResul`t, pour faciliter votre code. Pour obtenir la liste, consultez [constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : déclarer une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Comment : faire référence à un membre d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Énumérations et Qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Comment : parcourir une énumération dans Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [Comment : déterminer la chaîne associée à une valeur d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [Enum, instruction](../../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)
