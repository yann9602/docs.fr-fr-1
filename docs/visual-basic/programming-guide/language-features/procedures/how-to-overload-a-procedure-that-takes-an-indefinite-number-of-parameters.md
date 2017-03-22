---
title: "Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres (Visual Basic) | Documents Microsoft"
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
- procedures, parameters
- procedure overloading, indefinite number of parameters
- procedures, defining
- Visual Basic code, procedures
- procedure parameters
- procedures, overloading
- procedures, multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
caps.latest.revision: 18
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
ms.openlocfilehash: c7e09bd482e35c7ce7f28a6cc7de0379b7cc89f6
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres (Visual Basic)
Si une procédure possède un [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) paramètre, vous ne pouvez pas définir une version surchargée acceptant un tableau unidimensionnel pour le tableau de paramètres. Pour plus d’informations, consultez « Implicite surcharges pour un paramètre ParamArray » dans [considérations dans les procédures](./considerations-in-overloading-procedures.md).  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>Pour surcharger une procédure qui accepte un nombre variable de paramètres  
  
1.  Vérifier que la procédure et les avantages liés au code logique à partir de l’appel surchargées versions plus que d’un `ParamArray` paramètre. Consultez « Surcharges et ParamArrays » dans [considérations sur les surcharges de procédures](./considerations-in-overloading-procedures.md).  
  
2.  Déterminer le nombre de valeurs fournies que la procédure doit accepter dans la partie variable de la liste de paramètres. Cela peut inclure le cas d’aucune valeur, et peut inclure le cas d’un tableau unidimensionnel unique.  
  
3.  Pour chaque nombre acceptable de valeurs fournies, écrivez une `Sub` ou `Function` instruction de déclaration qui définit la liste de paramètres correspondante. Ne pas utiliser le `Optional` ou `ParamArray` (mot clé) dans la version surchargée.  
  
4.  Dans chaque déclaration, faites précéder le `Sub` ou `Function` mot clé avec le [surcharges](../../../../visual-basic/language-reference/modifiers/overloads.md) (mot clé).  
  
5.  Après chaque déclaration, écrivez le code de procédure à exécuter lorsque le code appelant fournit des valeurs correspondant à la liste de paramètres de cette déclaration.  
  
6.  Terminez chaque procédure par le `End Sub` ou `End Function` instruction comme il convient.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une procédure définie avec un [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) paramètre, puis un jeu équivalent de procédures surchargées.  
  
 [!code-vb[VbVbcnProcedures&#69;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures&#70;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 Vous ne pouvez pas surcharger une procédure avec une liste de paramètres qui prend un tableau unidimensionnel pour le tableau de paramètres. Toutefois, vous pouvez utiliser les signatures des autres surcharges implicites. Les déclarations suivantes illustrent ce principe.  
  
 [!code-vb[VbVbcnProcedures&#71;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 Le code dans les versions surchargées n’a pas à tester si le code appelant a fourni une ou plusieurs valeurs pour le `ParamArray` paramètre, ou si c’est le cas, combien. [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]transmet le contrôle à la version correspondant à la liste d’arguments appelante.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Comme une procédure avec un `ParamArray` paramètre équivaut à un ensemble de versions surchargées, vous ne pouvez pas surcharger une procédure avec une liste de paramètres correspondant à chacune de ces surcharges implicites. Pour plus d’informations, consultez [considérations dans les procédures](./considerations-in-overloading-procedures.md).  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Si vous travaillez dans un tableau dont la taille peut être indéfinie, il existe un risque de saturer la capacité interne de votre application. Si vous acceptez un tableau de paramètres, vous devez tester la longueur du tableau passé au code appelant et prendre les mesures appropriées si elle est trop grande pour votre application.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)   
 [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md)   
 [Paramètres facultatifs](./optional-parameters.md)   
 [Tableaux de paramètres](./parameter-arrays.md)   
 [Surcharge de procédure](./procedure-overloading.md)   
 [Procédures de dépannage](./troubleshooting-procedures.md)   
 [Comment : définir plusieurs Versions d’une procédure](./how-to-define-multiple-versions-of-a-procedure.md)   
 [Comment : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md)   
 [Comment : surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [Résolution de surcharge](./overload-resolution.md)
