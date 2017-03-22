---
title: "Considérations sur les surcharges de procédures (Visual Basic) | Documents Microsoft"
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
- signatures, ParamArray arguments
- ParamArray keyword, parameter arrays
- ParamArray keyword, arguments and signatures
- function overloading, implicit overloads for ParamArray
- ParamArray keyword, signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures, overloading
- parameters, lists
- function overloading, typeless programming
- typeless programming
- function overloading, restrictions
- arguments [Visual Basic], optional
- optional arguments, overloading
- signatures, procedure
- parameter lists
- parameter arrays, overloading arguments
- Visual Basic code, parameter lists
- procedure overloading, considerations
- Option Explicit statement
- restrictions, overloading procedures
- procedures, parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
caps.latest.revision: 26
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
ms.openlocfilehash: aa20cf367fba157f88afd861a4799540dcdecde1
ms.lasthandoff: 03/13/2017

---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>Considérations sur les surcharges de procédures (Visual Basic)
Lorsque vous surchargez une procédure, vous devez utiliser une autre *signature* pour chaque version surchargée. Cela signifie généralement que chaque version doit spécifier une liste de paramètres différente. Pour plus d’informations, consultez « Signature différente » dans [surcharge de procédure](./procedure-overloading.md).  
  
 Vous pouvez surcharger une `Function` procédure avec un `Sub` procédure et inversement, à condition qu’ils ont des signatures différentes. Deux surcharges ne peuvent pas différer uniquement car une a une valeur de retournée et l’autre non.  
  
 Vous pouvez surcharger une propriété de la même manière que vous surchargez une procédure et avec les mêmes restrictions. Toutefois, vous ne pouvez pas surcharger une procédure avec une propriété, ou vice versa.  
  
## <a name="alternatives-to-overloaded-versions"></a>Alternatives aux Versions surchargées  
 Vous devez parfois d’alternatives aux versions surchargées, en particulier lorsque la présence d’arguments est facultative ou que leur nombre est variable.  
  
 N’oubliez pas que les arguments facultatifs ne sont pas nécessairement pris en charge par tous les langages et les tableaux de paramètres sont limités à [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]. Si vous écrivez une procédure qui est susceptible d’être appelée à partir du code écrit dans un des différents langages, les versions surchargées offrent la plus grande flexibilité.  
  
### <a name="overloads-and-optional-arguments"></a>Surcharges et Arguments facultatifs  
 Lorsque le code appelant peut éventuellement fournir ou omettre un ou plusieurs arguments, vous pouvez définir plusieurs versions surchargées ou utiliser des paramètres facultatifs.  
  
#### <a name="when-to-use-overloaded-versions"></a>Quand utiliser des Versions surchargées  
 Vous pouvez envisager de définir une série de versions surchargées dans les cas suivants :  
  
-   La logique dans le code de procédure est très différente selon que le code appelant fournit un argument facultatif ou pas.  
  
-   Le code de procédure ne peut pas tester de manière fiable si le code appelant a fourni un argument facultatif. C’est le cas, par exemple, s’il n’existe aucun candidat possible pour une valeur par défaut que le code appelant ne peut pas censé fournir.  
  
#### <a name="when-to-use-optional-parameters"></a>Quand utiliser les paramètres facultatifs  
 Vous préférerez peut-être un ou plusieurs paramètres facultatifs dans les cas suivants :  
  
-   La seule action requise lorsque le code appelant ne fournit pas un argument facultatif consiste à définir le paramètre à une valeur par défaut. Dans ce cas, le code de procédure peut être moins compliqué si vous définissez une version unique avec un ou plusieurs `Optional` paramètres.  
  
 Pour plus d’informations, consultez [paramètres facultatifs](./optional-parameters.md).  
  
### <a name="overloads-and-paramarrays"></a>Overloads and ParamArrays  
 Lorsque le code appelant peut passer un nombre variable d’arguments, vous pouvez définir plusieurs versions surchargées ou utiliser un tableau de paramètres.  
  
#### <a name="when-to-use-overloaded-versions"></a>Quand utiliser des Versions surchargées  
 Vous pouvez envisager de définir une série de versions surchargées dans les cas suivants :  
  
-   Vous savez que le code appelant passe jamais plus qu’un petit nombre de valeurs au tableau de paramètres.  
  
-   La logique dans le code de procédure est très différente selon le nombre de valeurs le code appelant passe.  
  
-   Le code appelant peut passer des valeurs de différents types de données.  
  
#### <a name="when-to-use-a-parameter-array"></a>Quand utiliser un tableau de paramètres  
 Il est préférable à une `ParamArray` paramètre dans les cas suivants :  
  
-   Vous n’êtes pas en mesure de prévoir combien de valeurs le code appelant peut passer au tableau de paramètres, et il peut être un grand nombre.  
  
-   La logique de la procédure se prête à l’itération sur toutes les valeurs que le code appelant passe, en exécutant essentiellement les mêmes opérations sur chaque valeur.  
  
 Pour plus d’informations, consultez [tableaux de paramètres](./parameter-arrays.md).  
  
## <a name="implicit-overloads-for-optional-parameters"></a>Surcharges implicites pour les paramètres optionnels  
 Une procédure avec un [facultatif](../../../../visual-basic/language-reference/modifiers/optional.md) paramètre équivaut à deux procédures surchargées, une avec le paramètre facultatif et l’autre sans. Vous ne pouvez pas surcharger une procédure avec une liste de paramètres correspondant à ces. Les déclarations suivantes illustrent ce principe.  
  
 [!code-vb[VbVbcnProcedures&#58;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]  
  
 [!code-vb[VbVbcnProcedures&#60;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures&#61;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]  
  
 Pour une procédure avec plus d’un paramètre facultatif, il existe un ensemble de surcharges implicites, déterminé par la logique, comme dans l’exemple précédent.  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>Surcharges implicites pour un paramètre ParamArray  
 Le compilateur considère qu’une procédure avec un [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) paramètre possède un nombre infini de surcharges, qui se différencient selon ce que le code appelant passe au tableau de paramètres, comme suit :  
  
-   Une surcharge lorsque le code appelant ne fournit pas un argument à la`ParamArray`  
  
-   Une surcharge lorsque le code appelant fournit un tableau unidimensionnel de le `ParamArray` le type d’élément  
  
-   Pour chaque entier positif, une surcharge lorsque le code appelant fournit ce nombre d’arguments de le `ParamArray` le type d’élément  
  
 Les déclarations suivantes illustrent ces surcharges implicites.  
  
 [!code-vb[VbVbcnProcedures&#68;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]  
  
 [!code-vb[VbVbcnProcedures&#70;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]  
  
 Vous ne pouvez pas surcharger une procédure avec une liste de paramètres qui prend un tableau unidimensionnel pour le tableau de paramètres. Toutefois, vous pouvez utiliser les signatures des autres surcharges implicites. Les déclarations suivantes illustrent ce principe.  
  
 [!code-vb[VbVbcnProcedures&#71;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>Programmation sans type comme une Alternative à la surcharge  
 Si vous souhaitez autoriser le code appelant à passer différents types de données à un paramètre, une autre approche consiste à la programmation sans type. Vous pouvez définir le type de commutateur à la vérification de la `Off` avec soit le [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md) ou [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) option du compilateur. Puis vous n’êtes pas obligé de déclarer le type de données du paramètre. Toutefois, cette approche présente les inconvénients suivants par rapport à la surcharge :  
  
-   Programmation sans type génère un code d’exécution moins efficace.  
  
-   La procédure doit tester chaque type de données que pouvant être passés.  
  
-   Le compilateur ne peut pas signaler d’erreur si le code appelant passe un type de données par la procédure ne prend pas en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)   
 [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md)   
 [Procédures de dépannage](./troubleshooting-procedures.md)   
 [Comment : définir plusieurs Versions d’une procédure](./how-to-define-multiple-versions-of-a-procedure.md)   
 [Comment : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md)   
 [Comment : surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Résolution de surcharge](./overload-resolution.md)   
 [Surcharges](../../../../visual-basic/language-reference/modifiers/overloads.md)
