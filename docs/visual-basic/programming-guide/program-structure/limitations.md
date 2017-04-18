---
title: "Restrictions liées à Visual Basic | Documents Microsoft"
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
- limits
- limitations, Visual Basic
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: 14
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
ms.openlocfilehash: d556b045b4ebae6ba24c0571a6cb7e5337c6a8f2
ms.lasthandoff: 03/13/2017

---
# <a name="visual-basic-limitations"></a>Restrictions liées à Visual Basic
Les versions antérieures de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] appliquée limites dans le code, telles que la longueur des noms de variables, le nombre de variables autorisé dans les modules et la taille du module. Dans [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)], ces restrictions ont été allégées, ce qui vous donne une plus grande liberté d’écriture et d’organisation de votre code.  
  
 Les limites physiques dépendent les plus sur l’exécution de mémoire que sur les considérations relatives à la compilation. Si vous utilisez des pratiques de programmation prudentes et divisez de grandes applications en plusieurs classes et modules, il existe très peu de risque de rencontrer interne [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] limitation.  
  
 Voici quelques limitations que vous pouvez rencontrer dans les cas extrêmes :  
  
-   **Longueur du nom.** Il est un nombre maximal de caractères pour le nom de chaque élément de programmation déclaré. Cette limite s’applique à une chaîne de qualification entière si le nom de l’élément est qualifié. Consultez la page [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   **Longueur de ligne.** Il existe un maximum de 65 535 caractères dans une ligne physique de code source. La ligne de code source logique peut être plus longue si vous utilisez des caractères de continuation de ligne. Consultez la page [Comment : diviser et combiner des instructions dans le Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
-   **Dimensions du tableau.** Il existe un nombre maximal de dimensions, que vous pouvez déclarer un tableau. Cela limite le nombre d’index vous permet de spécifier un élément de tableau. Consultez la page [en Visual Basic, les Dimensions de tableau](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
-   **Longueur de chaîne.** Il existe un nombre maximal de caractères Unicode que vous pouvez stocker dans une chaîne unique. Consultez la page [Type de données chaîne](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
-   **Longueur de chaîne d’environnement.** Il existe un maximum de 32768 caractères de n’importe quel environnement la chaîne utilisée comme argument de ligne de commande. Il s’agit d’une limitation sur toutes les plateformes.  
  
## <a name="see-also"></a>Voir aussi  
 [Structure de programme et Conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Conventions d’affectation de noms de Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
