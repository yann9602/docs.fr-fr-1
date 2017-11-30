---
title: "Caractéristiques d'éléments déclarés (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declared elements [Visual Basic], lifetime
- access levels, declared elements
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- elements [Visual Basic], programming
- scope [Visual Basic], declared elements
- lifetime [Visual Basic], declared elements
- declared elements [Visual Basic], access level
- data types [Visual Basic], declared elements
- declared elements [Visual Basic], visibility
ms.assetid: 1bc40fb8-b67c-4428-90a4-76b630ae2583
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 26ee27d3a1d085c6ab45ae850dbdac700aa208a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="declared-element-characteristics-visual-basic"></a>Caractéristiques d'éléments déclarés (Visual Basic)
A *caractéristique* d’un élément déclaré est un aspect de cet élément qui détermine comment le code peut interagir avec lui. Chaque élément déclaré a un ou plusieurs des caractéristiques suivantes associées :  
  
-   *Type de données* — les valeurs de l’élément peut contenir, et comment il stocke ces valeurs. Pour plus d’informations, consultez [des Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
-   *Durée de vie* : la période de temps d’exécution au cours de laquelle l’élément est disponible pour utilisation. Pour plus d’informations, consultez [durée de vie dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   *Étendue* : l’ensemble du code qui peut faire référence à l’élément sans qualifier son nom. Pour plus d’informations, consultez [Comment : contrôler la portée d’une Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md).  
  
-   *Niveau d’accès* , l’autorisation pour le code d’utiliser l’élément. Pour plus d’informations, consultez [Comment : contrôler la disponibilité d’une Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md).  
  
## <a name="characteristics-of-the-elements"></a>Caractéristiques des éléments  
 Le tableau suivant présente les éléments déclarés et les caractéristiques qui s’appliquent à chacun d’eux.  
  
|Élément|Type de données|Durée de vie|Étendue <sup>1</sup>|Niveau d’accès|  
|-------------|---------------|--------------|------------------------|------------------|  
|Variable|Oui|Oui|Oui|Oui|  
|Constante|Oui|Non|Oui|Oui|  
|Énumération|Oui|Non|Oui|Oui|  
|Structure|Non|Non|Oui|Oui|  
|Propriété|Oui|Oui|Oui|Oui|  
|Méthode|Non|Oui|Oui|Oui|  
|Procédure (`Sub` ou `Function`)|Non|Oui|Oui|Oui|  
|Paramètre de procédure|Oui|Oui|Oui|Non|  
|Retour de fonction|Oui|Oui|Oui|Non|  
|Opérateur|Oui|Non|Oui|Oui|  
|Interface|Non|Non|Oui|Oui|  
|Classe|Non|Non|Oui|Oui|  
|Événement|Non|Non|Oui|Oui|  
|Délégué|Non|Non|Oui|Oui|  
  
 <sup>1</sup> étendue est parfois appelée *visibilité*.  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [Noms d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Références aux éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Durée de vie dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Portée dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Niveaux d’accès dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
