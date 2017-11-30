---
title: "Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 37d5b47f06bad1c2a8871168c5642663aedcccf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres (Visual Basic)
Si une procédure a un [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) paramètre, vous ne pouvez pas définir une version surchargée acceptant un tableau unidimensionnel pour le tableau de paramètres. Pour plus d’informations, consultez « Implicite surcharges pour un paramètre ParamArray » dans [considérations relatives à la surcharge de procédures](./considerations-in-overloading-procedures.md).  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>Pour surcharger une procédure qui accepte un nombre variable de paramètres  
  
1.  Vérifier que la procédure et les avantages de la logique de code à partir de l’appel surchargé versions plus que d’un `ParamArray` paramètre. Consultez « Surcharges et ParamArrays » dans [considérations sur les surcharges de procédures](./considerations-in-overloading-procedures.md).  
  
2.  Déterminer le nombre de valeurs fournies que la procédure doit accepter dans la partie variable de la liste de paramètres. Cela peut inclure le cas d’aucune valeur, et il peut inclure le cas d’un tableau unidimensionnel.  
  
3.  Pour chaque nombre acceptable de valeurs fournies, écrivez une `Sub` ou `Function` instruction de déclaration qui définit la liste de paramètres correspondants. N’utilisez pas le `Optional` ou `ParamArray` mot clé dans la version surchargée.  
  
4.  Dans chaque déclaration, faites précéder le `Sub` ou `Function` mot clé avec la [surcharges](../../../../visual-basic/language-reference/modifiers/overloads.md) (mot clé).  
  
5.  Après chaque déclaration, écrivez le code de procédure qui doit s’exécuter lorsque le code appelant fournit des valeurs correspondant à la liste de paramètres de cette déclaration.  
  
6.  Terminez chaque procédure par le `End Sub` ou `End Function` instruction comme il convient.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une procédure définie avec un [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) paramètre, puis un jeu équivalent de procédures surchargées.  
  
 [!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 Vous ne pouvez pas surcharger une procédure avec une liste de paramètres qui prend un tableau unidimensionnel pour le tableau de paramètres. Toutefois, vous pouvez utiliser les signatures des autres surcharges implicites. Les déclarations suivantes illustrent ce principe.  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 Le code dans les versions surchargées n’a pas vérifier si le code appelant a fourni une ou plusieurs valeurs pour le `ParamArray` paramètre, ou si c’est le cas, combien. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]transmet le contrôle à la version correspondant à la liste d’arguments appelante.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Car une procédure avec un `ParamArray` paramètre équivaut à un ensemble de versions surchargées, vous ne pouvez pas surcharger une procédure avec une liste de paramètres correspondant à chacune de ces surcharges implicites. Pour plus d’informations, consultez [considérations relatives à la surcharge de procédures](./considerations-in-overloading-procedures.md).  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Si vous travaillez dans un tableau qui peut être indéfiniment volumineux, il existe un risque de saturer la capacité interne de votre application. Si vous acceptez un tableau de paramètres, vous devez tester la longueur du tableau passé le code appelant et prenez les mesures appropriées si elle est trop grande pour votre application.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)  
 [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)  
 [Paramètres facultatifs](./optional-parameters.md)  
 [tableaux de paramètres](./parameter-arrays.md)  
 [Surcharge de procédure](./procedure-overloading.md)  
 [Procédures de dépannage](./troubleshooting-procedures.md)  
 [Guide pratique : définir plusieurs versions d’une procédure](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Guide pratique : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md)  
 [Guide pratique : surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Résolution de surcharge](./overload-resolution.md)
