---
title: "Comment : étiqueter des instructions (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 190ec9fc2392e6e4adae9b2b612edd69d73cedfd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-label-statements-visual-basic"></a>Comment : étiqueter des instructions (Visual Basic)
Blocs d’instructions sont composés de lignes de code délimitées par le signe deux-points. Lignes de code, précédé d’une chaîne ou entier identifiant sont dites *intitulé*. Les étiquettes d’instruction sont utilisées pour marquer une ligne de code pour identifier pour une utilisation avec des instructions telles que `On Error Goto`.  
  
 Les étiquettes peuvent être soit des identificateurs Visual Basic valides, telles que celles qui identifient les éléments de programmation, soit des littéraux entiers. Une étiquette doit apparaître au début d’une ligne de code source et doit être suivie par un signe deux-points, indépendamment de si elle est suivie par une instruction sur la même ligne.  
  
 Le compilateur identifie les étiquettes en vérifiant si le début de la ligne correspond à n’importe quel identificateur déjà défini. Si elle n’est pas le cas, le compilateur suppose qu’il existe une étiquette.  
  
 Les étiquettes ont leur propre espace de déclaration et n’interfèrent pas avec d’autres identificateurs. Portée d’une étiquette est le corps de la méthode. Déclaration d’étiquette est prioritaire en cas d’ambiguïté.  
  
> [!NOTE]
>  Étiquettes peuvent être utilisées uniquement sur des instructions exécutables à l’intérieur de méthodes.  
  
### <a name="to-label-a-line-of-code"></a>Pour étiqueter une ligne de code  
  
-   Placez un identificateur, suivi d’un signe deux-points, au début de la ligne de code source.  
  
     Par exemple, les lignes de code suivantes sont étiquetés avec `Jump` et `120`, respectivement :  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Structure de programme et conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
