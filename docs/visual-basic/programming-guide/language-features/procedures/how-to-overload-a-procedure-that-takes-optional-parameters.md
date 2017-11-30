---
title: "Comment : surcharger une procédure qui accepte des paramètres optionnels (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b4a863944d4f9ab265aab52578fbb704ca376de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>Comment : surcharger une procédure qui accepte des paramètres optionnels (Visual Basic)
Si une procédure avec un ou plusieurs [facultatif](../../../../visual-basic/language-reference/modifiers/optional.md) paramètres, vous ne pouvez pas définir une version surchargée correspondant à un de ses surcharges implicites. Pour plus d’informations, consultez « Implicite surcharges pour les paramètres facultatifs » dans [considérations relatives à la surcharge de procédures](./considerations-in-overloading-procedures.md).  
  
## <a name="one-optional-parameter"></a>Un paramètre facultatif  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>Pour surcharger une procédure qui accepte un paramètre facultatif  
  
1.  Écrire un `Sub` ou `Function` instruction de déclaration qui inclut le paramètre facultatif dans la liste de paramètres. N’utilisez pas le `Optional` mot clé dans la version surchargée.  
  
2.  Faites précéder le `Sub` ou `Function` mot clé with le [surcharges](../../../../visual-basic/language-reference/modifiers/overloads.md) (mot clé).  
  
3.  Écrivez le code de procédure à exécuter lorsque le code appelant fournit l’argument facultatif.  
  
4.  Terminez la procédure par le `End Sub` ou `End Function` instruction comme il convient.  
  
5.  Écrivez une deuxième instruction de déclaration qui est identique à la première déclaration, sauf qu’elle n’inclut pas le paramètre facultatif dans la liste de paramètres.  
  
6.  Écrivez le code de procédure qui doit s’exécuter lorsque le code appelant ne fournit pas l’argument facultatif. Terminez la procédure par le `End Sub` ou `End Function` instruction comme il convient.  
  
     L’exemple suivant montre une procédure définie avec un paramètre facultatif, un ensemble équivalent de deux procédures surchargées et enfin des exemples de valides et non des versions surchargées.  
  
     [!code-vb[VbVbcnProcedures#59](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_2.vb)]  
  
     [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_3.vb)]  
  
## <a name="multiple-optional-parameters"></a>Plusieurs paramètres facultatifs  
 Pour une procédure avec plus d’un paramètre facultatif, vous devez normalement plus de deux versions surchargées. Par exemple, s’il existe deux paramètres facultatifs, et le code appelant peut fournir ou omettre de chacun d’eux indépendamment de l’autre, vous avez besoin de quatre versions surchargées, une pour chaque combinaison possible d’arguments fournis.  
  
 Le nombre de paramètres facultatifs augmente, la complexité de la surcharge augmente. À moins que certaines combinaisons d’arguments fournis ne sont pas acceptables, pour les paramètres optionnels de N, vous devez 2 ^ N des versions surchargées. Selon la nature de la procédure, vous constaterez peut-être que la clarté de logique justifie l’effort supplémentaire de définition de toutes les versions surchargées.  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>Pour surcharger une procédure qui accepte plusieurs paramètres facultatifs  
  
1.  Déterminer quelles combinaisons d’arguments facultatifs fournis sont acceptables pour la logique de la procédure. Une combinaison inacceptable peut survenir si un paramètre facultatif dépend d’un autre. Par exemple, si un paramètre accepte un conjoint et qu’un autre accepte âge le son, une combinaison d’arguments fournissant l’âge mais en omettant le nom est inacceptable.  
  
2.  Pour chaque combinaison acceptable d’arguments facultatifs fournis, écrivez une `Sub` ou `Function` instruction de déclaration qui définit la liste de paramètres correspondants. N’utilisez pas le `Optional` (mot clé).  
  
3.  Dans chaque déclaration, faites précéder le `Sub` ou `Function` mot clé avec la [surcharges](../../../../visual-basic/language-reference/modifiers/overloads.md) (mot clé).  
  
4.  Après chaque déclaration, écrivez le code de procédure qui doit être exécuté lorsque le code appelant fournit une liste d’arguments correspondant à la liste de paramètres de cette déclaration.  
  
5.  Terminez chaque procédure par le `End Sub` ou `End Function` instruction comme il convient.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)  
 [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)  
 [Paramètres facultatifs](./optional-parameters.md)  
 [tableaux de paramètres](./parameter-arrays.md)  
 [Surcharge de procédure](./procedure-overloading.md)  
 [Procédures de dépannage](./troubleshooting-procedures.md)  
 [Guide pratique : définir plusieurs versions d’une procédure](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Guide pratique : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md)  
 [Guide pratique : surcharger une procédure qui accepte un nombre indéfini de paramètres](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Résolution de surcharge](./overload-resolution.md)
