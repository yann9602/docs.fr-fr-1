---
title: Passage des arguments par position et par nom (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 164f69fcf23049441a0acbe05058c792d5363a03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Passage des arguments par position et par nom (Visual Basic)
Lorsque vous appelez un `Sub` ou `Function` procédure, vous pouvez passer des arguments *par position* , dans l’ordre dans lequel elles apparaissent dans la définition de la procédure, ou vous pouvez passer les *par nom*, sans vu les positionner.  
  
 Lorsque vous passez un argument par nom, vous spécifiez l’argument déclaré de le nom suivi d’un signe deux-points et un signe égal (`:=`), suivi par la valeur d’argument. Vous pouvez fournir des arguments nommés dans n’importe quel ordre.  
  
 Par exemple, les éléments suivants `Sub` procédure prend trois arguments :  
  
 [!code-vb[VbVbcnProcedures#41](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]  
  
 Lorsque vous appelez cette procédure, vous pouvez fournir les arguments par position, par nom ou à l’aide d’une combinaison des deux.  
  
## <a name="passing-arguments-by-position"></a>Passage des Arguments par Position  
 Vous pouvez appeler la procédure `studentInfo` avec des arguments passés par position et délimités par des virgules, comme indiqué dans l’exemple suivant :  
  
 [!code-vb[VbVbcnProcedures#42](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]  
  
 Si vous omettez un argument facultatif dans une liste d’arguments positionnels, vous devez marquer son emplacement avec une virgule. L’exemple suivant appelle `studentInfo` sans le `age` argument :  
  
 [!code-vb[VbVbcnProcedures#43](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]  
  
## <a name="passing-arguments-by-name"></a>Passage des Arguments par nom  
 Vous pouvez également appeler `studentInfo` avec les arguments passés par nom, également délimitées par des virgules, comme indiqué dans l’exemple suivant :  
  
 [!code-vb[VbVbcnProcedures#44](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>Mélange d’Arguments par Position et par nom  
 Vous pouvez fournir des arguments par position et par nom dans un seul appel de procédure, comme indiqué dans l’exemple suivant :  
  
 [!code-vb[VbVbcnProcedures#45](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]  
  
 Dans l’exemple précédent, aucune virgule supplémentaire n’est nécessaire pour marquer l’emplacement de l’indication `age` argument, étant donné que `birth` est passé par nom.  
  
 Lorsque vous fournissez des arguments par un mélange de position et le nom, les arguments positionnels doivent tous figurer en premier. Une fois que vous fournissez un argument par nom, les arguments restants doivent tous être par nom.  
  
## <a name="supplying-optional-arguments-by-name"></a>Spécification d’Arguments facultatifs par nom  
 Passer des arguments par nom est particulièrement utile lorsque vous appelez une procédure qui possède plusieurs arguments facultatifs. Si vous fournissez des arguments par nom, vous n’avez pas à utiliser des virgules successives pour signaler l’absence d’arguments de position. Passer des arguments par nom facilite également suivre les arguments que vous passez et ceux qui sont omis.  
  
## <a name="restrictions-on-supplying-arguments-by-name"></a>Restrictions sur la fourniture des Arguments par nom  
 Vous ne peut pas passer d’arguments par nom pour éviter d’entrer des arguments requis. Vous pouvez omettre que les arguments facultatifs.  
  
 Vous ne pouvez pas passer un tableau de paramètres par nom. Il s’agit, car lorsque vous appelez la procédure, vous indiquez un nombre indéfini d’arguments de séparées par des virgules pour le tableau de paramètres, et le compilateur ne peut pas associer plusieurs arguments avec un nom unique.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)  
 [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)  
 [Guide pratique : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)  
 [Passage d’un argument par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)  
 [Paramètres facultatifs](./optional-parameters.md)  
 [tableaux de paramètres](./parameter-arrays.md)  
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
