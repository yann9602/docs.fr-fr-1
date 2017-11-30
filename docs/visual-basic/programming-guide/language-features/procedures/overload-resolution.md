---
title: "Résolution de surcharge (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- overload resolution
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedure overloading [Visual Basic], overload resolution
- signatures [Visual Basic], procedure
- overloads [Visual Basic], resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7eb71b69496e27b664fe297e9e5f105b360ce01d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="overload-resolution-visual-basic"></a>Résolution de surcharge (Visual Basic)
Lorsque le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur rencontre un appel à une procédure qui est défini dans plusieurs versions surchargées, le compilateur doit décider de la surcharge à appeler. Pour cela, procédez comme suit :  
  
1.  **Accessibilité.** Il élimine toute surcharge avec un niveau d’accès qui empêche le code appelant de l’appeler.  
  
2.  **Nombre de paramètres.** Il élimine les surcharges qui définissent un nombre différent de paramètres que ceux spécifiés dans l’appel.  
  
3.  **Types de données de paramètre.** Le compilateur émet la préférence de méthodes d’instance sur les méthodes d’extension. Si n’importe quelle méthode d’instance est trouvée qui nécessite uniquement des conversions pour faire correspondre l’appel de procédure étendues, toutes les méthodes d’extension sont supprimées et le compilateur continue avec uniquement les candidats de méthode d’instance. Si aucune méthode d’instance de ce type n’est trouvée, elle se poursuit avec l’instance et les méthodes d’extension.  
  
     Dans cette étape, il élimine toute surcharge pour lesquels les types de données des arguments d’appel ne peut pas être convertis pour les types de paramètres définis dans la surcharge.  
  
4.  **Conversions restrictives.** Il élimine les surcharges qui nécessitent une conversion restrictive à partir des types d’argument appelant pour les types de paramètres définis. Cela est vrai si la vérification du type de commutateur ([Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) est `On` ou `Off`.  
  
5.  **Moindre extension.** Le compilateur considère les surcharges restantes par paires. Pour chaque paire, il compare les types de données des paramètres définis. Si les types dans une des surcharges tous les s’étendent aux types correspondants dans l’autre, le compilateur élimine ce dernier. Autrement dit, il conserve la surcharge qui nécessite le moins importante.  
  
6.  **Candidat unique.** Il continue à rassembler les surcharges par paires jusqu'à ce que la seule surcharge et il résout l’appel à cette surcharge. Si le compilateur ne peut pas réduire la surcharge à un seul candidat, il génère une erreur.  
  
 L’illustration suivante montre le processus qui détermine un ensemble de versions surchargées d’appeler.  
  
 ![Diagramme de flux de processus de résolution de surcharge](./media/overloadres.gif "OverloadRes")  
Résolution parmi des versions surchargées  
  
 L’exemple suivant illustre ce processus de résolution de surcharge.  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/overload-resolution_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/overload-resolution_2.vb)]  
  
 Dans le premier appel, le compilateur élimine la première surcharge, car le type du premier argument (`Short`) restreint au type du paramètre correspondant (`Byte`). Il élimine ensuite la troisième surcharge, car chaque argument de type dans la deuxième surcharge (`Short` et `Single`) s’étend au type correspondant dans la troisième surcharge (`Integer` et `Single`). La deuxième surcharge requiert une extension moins importante, par conséquent, le compilateur l’utilise pour l’appel.  
  
 Dans le deuxième appel, le compilateur ne peut pas supprimer les surcharges en fonction des conversions restrictives lors. Il élimine la troisième surcharge pour la même raison que dans le premier appel, car elle peut appeler la deuxième surcharge avec une extension moins importante des types d’arguments. Toutefois, le compilateur ne peut pas résoudre entre les surcharges de la première et deuxième. Chacune a un type de paramètre défini qui s’étend au type correspondant dans l’autre (`Byte` à `Short`, mais `Single` à `Double`). Par conséquent, le compilateur génère une erreur de résolution de surcharge.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>Surchargé facultatif et Arguments ParamArray  
 Si deux surcharges d’une procédure ont des signatures identiques, mais que le dernier paramètre est déclaré [facultatif](../../../../visual-basic/language-reference/modifiers/optional.md) dans un et [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) dans l’autre, le compilateur résout un appel à cette procédure en tant que suit :  
  
|Si l’appel fournit le dernier argument comme|Le compilateur résout l’appel à la surcharge en déclarant le dernier argument comme|  
|---|---|  
|Aucune valeur (argument omis)|`Optional`|  
|une valeur unique|`Optional`|  
|Deux ou plusieurs valeurs dans une liste séparée par des virgules|`ParamArray`|  
|Un tableau d’une longueur quelconque (y compris un tableau vide)|`ParamArray`|  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres facultatifs](./optional-parameters.md)  
 [tableaux de paramètres](./parameter-arrays.md)  
 [Surcharge de procédure](./procedure-overloading.md)  
 [Procédures de dépannage](./troubleshooting-procedures.md)  
 [Guide pratique : définir plusieurs versions d’une procédure](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Guide pratique : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md)  
 [Guide pratique : surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Guide pratique : surcharger une procédure qui accepte un nombre indéfini de paramètres](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Considérations sur les surcharges de procédures](./considerations-in-overloading-procedures.md)  
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Méthodes d’extension](./extension-methods.md)
