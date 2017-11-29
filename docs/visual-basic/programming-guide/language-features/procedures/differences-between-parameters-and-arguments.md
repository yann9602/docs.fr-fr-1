---
title: "Différences entre les paramètres et les arguments (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6613c64a24ef18239422b69f8b5320eadc95b92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>Différences entre les paramètres et les arguments (Visual Basic)
Dans la plupart des cas, une procédure doit avoir des informations sur les circonstances dans lesquelles elle a été appelée. Une procédure qui exécute des tâches répétitives ou partagées utilise des informations différentes pour chaque appel. Ces informations se composent des variables, des constantes et des expressions que vous passez à la procédure lorsque vous appelez.  
  
 Pour communiquer ces informations à la procédure, la procédure définit un *paramètre*, et le code appelant passe un *argument* à ce paramètre. Vous pouvez considérer le paramètre comme un espace de parking et l’argument comme une voiture. De même que plusieurs automobiles peuvent se dans un espace de parking à des moments différents, le code appelant peut passer un argument différent au même paramètre chaque fois qu’il appelle la procédure.  
  
## <a name="parameters"></a>Paramètres  
 A *paramètre* représente une valeur de la procédure que vous devez passer lorsque vous appelez. Déclaration de la procédure définit ses paramètres.  
  
 Lorsque vous définissez un `Function` ou `Sub` procédure, vous spécifiez un *liste de paramètres* entre parenthèses le nom de la procédure qui suit immédiatement. Pour chaque paramètre, vous spécifiez un nom, un type de données et un mécanisme de passage ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)). Vous pouvez également indiquer qu’un paramètre est facultatif. Cela signifie que le code appelant ne dispose pas de passer une valeur pour celle-ci.  
  
 Le nom de chaque paramètre sert un *variable locale* dans la procédure. Vous utilisez le nom du paramètre de la même façon que vous utilisez toute autre variable.  
  
## <a name="arguments"></a>Arguments  
 Un *argument* représente la valeur que vous passez à un paramètre de procédure lorsque vous appelez la procédure. Le code appelant fournit les arguments lorsqu’il appelle la procédure.  
  
 Lorsque vous appelez un `Function` ou `Sub` procédure, vous incluez un *liste d’arguments* entre parenthèses le nom de la procédure qui suit immédiatement. Chaque argument correspond au paramètre dans la même position dans la liste.  
  
 Contrairement à la définition des paramètres, arguments n’ont pas de noms. Chaque argument est une expression qui peut contenir zéro ou plusieurs variables, de constantes et des littéraux. Le type de données de l’expression évaluée doit correspondre en général, le type de données défini pour le paramètre correspondant, et dans tous les cas, il doit être convertible au type de paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)  
 [Procédures Sub](./sub-procedures.md)  
 [Procédures Function](./function-procedures.md)  
 [Procédures de propriété](./property-procedures.md)  
 [Procédures d’opérateur](./operator-procedures.md)  
 [Guide pratique : définir un paramètre pour une procédure](./how-to-define-a-parameter-for-a-procedure.md)  
 [Guide pratique : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)  
 [Passage d’un argument par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)  
 [Procédures récursives](./recursive-procedures.md)  
 [Surcharge de procédure](./procedure-overloading.md)
