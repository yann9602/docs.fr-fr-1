---
title: "Passing Arguments by Position and by Name (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "arguments [Visual Basic], passing by name"
  - "procedures, arguments"
  - ":= passing arguments"
  - "procedure arguments"
  - "Visual Basic code, procedures"
  - "named arguments, passing arguments"
  - "arguments [Visual Basic], passing by position"
  - "Function procedures, passing arguments"
  - "named parameters, passing arguments"
  - "named arguments"
  - "passing parameters, named parameter arguments"
  - "passing parameters, by position"
  - "procedures, calling"
  - "named parameters"
  - "Sub procedures, passing arguments"
  - "argument passing"
  - "passing parameters, by name"
  - "argument passing, by position"
  - "arguments [Visual Basic], listing by name"
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Passing Arguments by Position and by Name (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Lorsque vous appelez une procédure `Sub` ou `Function`, vous pouvez passer des arguments *par position* \(dans l'ordre où ils apparaissent dans la définition de la procédure\) ou *par nom*, sans tenir compte de la position.  
  
 Lorsque vous passez un argument par nom, vous devez spécifier le nom déclaré de l'argument suivi de deux\-points et d'un signe égal \(`:=`\), puis ajouter la valeur de l'argument.  L'ordre des arguments nommés n'a pas d'importance.  
  
 Par exemple, la procédure `Sub` suivante accepte trois arguments :  
  
 [!code-vb[VbVbcnProcedures#41](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]  
  
 Lorsque vous appelez cette procédure, vous pouvez fournir les arguments par position, par nom ou les deux.  
  
## Passage des arguments par position  
 Vous pouvez appeler la procédure  `studentInfo`  avec des arguments passés par position et séparés par des virgules, comme le montre l'exemple suivant :  
  
 [!code-vb[VbVbcnProcedures#42](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]  
  
 Si vous omettez un argument facultatif dans une liste d'arguments positionnels, vous devez marquer son emplacement à l'aide d'une virgule.  L'exemple suivant appelle  `studentInfo`  sans l'argument  `age`  :  
  
 [!code-vb[VbVbcnProcedures#43](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]  
  
## Passage des arguments par nom  
 Vous pouvez également appeler  `studentInfo`  avec des arguments passés par nom et séparés par des virgules, comme le montre l'exemple suivant :  
  
 [!code-vb[VbVbcnProcedures#44](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]  
  
## Mélange d'arguments par position et par nom  
 Vous pouvez fournir des arguments à la fois par position et par nom dans un seul appel de procédure, comme le montre l'exemple suivant :  
  
 [!code-vb[VbVbcnProcedures#45](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]  
  
 Dans l'exemple précédent, aucune virgule supplémentaire n'est nécessaire pour marquer l'emplacement de l'argument  `age`  ayant été omis, car  `birth`  est passé par nom.  
  
 Lorsque vous fournissez des arguments à la fois par position et par nom, les arguments positionnels doivent tous être placés en premier.  Une fois que vous avez fourni un argument par nom, les arguments restants doivent tous être fournis par nom.  
  
## Spécification d'arguments facultatifs par nom  
 Le fait de passer des arguments par nom est très utile lorsque vous appelez une procédure qui possède plusieurs arguments facultatifs.  Si vous fournissez des arguments par nom, vous n'êtes pas obligé d'utiliser des virgules successives pour signaler l'absence d'arguments positionnels.  Le fait de passer des arguments par nom facilite également le suivi des arguments qui sont passés ou de ceux qui sont omis.  
  
## Restrictions sur les spécifications d'arguments par nom  
 Vous ne pouvez pas passer d'arguments par nom pour éviter d'entrer des arguments requis.  Vous ne pouvez omettre que les arguments facultatifs.  
  
 Vous ne pouvez pas passer un tableau de paramètres par nom.  En effet, lorsque vous appelez la procédure, vous devez fournir un nombre indéfini d'arguments séparés par des virgules pour le tableau de paramètres, or, le compilateur ne peut pas associer plusieurs arguments à un seul nom.  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)   
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)