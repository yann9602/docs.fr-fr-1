---
title: "Procédures Sub (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e20e0dd5ff9e2b931e5792bebb3144930826f89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sub-procedures-visual-basic"></a>Procédures Sub (Visual Basic)
A `Sub` procédure est une série de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] instructions délimitée par le `Sub` et `End Sub` instructions. Le `Sub` procédure effectue une tâche, puis retourne le contrôle au code appelant, mais elle ne retourne pas de valeur au code appelant.  
  
 Chaque fois que la procédure est appelée, ses instructions sont exécutées, en commençant par la première instruction exécutable après le `Sub` instruction et en terminant par la première `End Sub`, `Exit Sub`, ou `Return` instruction rencontrée.  
  
 Vous pouvez définir un `Sub` procédure dans les modules, les classes et structures. Par défaut, il est `Public`, ce qui signifie que vous pouvez l’appeler à partir de n’importe où dans votre application qui a accès pour le module, classe ou structure dans laquelle vous l’avez définie. Le terme, *méthode*, décrit une `Sub` ou `Function` procédure accessible en dehors de sa définition de module, classe ou structure. Pour plus d’informations, consultez [Procédures](./index.md).  
  
 A `Sub` procédure peut prendre des arguments, tels que des constantes, variables ou expressions qui lui sont passées par le code appelant.  
  
## <a name="declaration-syntax"></a>Syntaxe de déclaration  
 La syntaxe de déclaration d’un `Sub` comme suit :  
  
 `[`*modificateurs* `] Sub` *nomsub* `[(` *parameterlist*  `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 Le `modifiers` peut spécifier plus d’informations sur la surcharge, la substitution, le partage et l’occultation et de niveau d’accès. Pour plus d’informations, consultez [Sub, instruction](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="parameter-declaration"></a>Déclaration de paramètre  
 Vous déclarez chaque paramètre de procédure de la même façon à la façon dont vous déclarez une variable, en spécifiant le type de données et le nom du paramètre. Vous pouvez également spécifier le mécanisme de passage et indique si le paramètre est facultatif, ou un tableau de paramètres.  
  
 La syntaxe de chaque paramètre dans la liste de paramètres est la suivante :  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *nom_paramètre*`As`*type de données*   
  
 Si le paramètre est facultatif, vous devez également fournir une valeur par défaut dans le cadre de sa déclaration. La syntaxe pour spécifier une valeur par défaut est la suivante :  
  
 `Optional [ByVal | ByRef]`  *nom_paramètre*`As`*datatype*`=`*defaultvalue*   
  
### <a name="parameters-as-local-variables"></a>Paramètres en tant que Variables locales  
 Lorsque le contrôle passe à la procédure, chaque paramètre est traité comme une variable locale. Cela signifie que sa durée de vie est identique à celle de la procédure et son étendue est l’ensemble de la procédure.  
  
## <a name="calling-syntax"></a>Syntaxe d’appel  
 Vous appelez un `Sub` procédure explicitement avec une instruction d’appel autonome. Vous ne pouvez pas l’appeler à l’aide de son nom dans une expression. Vous devez fournir des valeurs pour tous les arguments qui ne sont pas facultatifs, et vous devez placer la liste d’arguments entre parenthèses. Si aucun argument n’est fourni, vous pouvez omettre les parenthèses. L’utilisation de la `Call` le mot clé est facultatif, mais non recommandée.  
  
 La syntaxe d’un appel à un `Sub` comme suit :  
  
 `[Call]`  *nomsub* `[(` *argumentlist*`)]`  
  
 Vous pouvez appeler une `Sub` méthode en dehors de la classe qui le définit. Tout d’abord, vous devez utiliser le `New` (mot clé) pour créer une instance de la classe ou appeler une méthode qui retourne une instance de la classe. Pour plus d’informations, consultez [nouvel opérateur](../../../../visual-basic/language-reference/operators/new-operator.md). Ensuite, vous pouvez utiliser la syntaxe suivante pour appeler le `Sub` méthode sur l’objet de l’instance :  
  
 *Objet*. *MethodName*`[(`*argumentlist*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>Illustration de déclaration et d’appel  
 Les éléments suivants `Sub` procédure indique à l’opérateur la tâche que l’application est sur le point d’effectuer et affiche également un horodatage. Au lieu de dupliquer ce code au début de chaque tâche, l’application appelle simplement `tellOperator` depuis différents emplacements. Chaque appel passe une chaîne dans le `task` qui identifie la tâche en cours de démarrage.  
  
 [!code-vb[VbVbcnProcedures#2](./codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 L’exemple suivant montre un appel typique à `tellOperator`.  
  
 [!code-vb[VbVbcnProcedures#3](./codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)  
 [Procédures Function](./function-procedures.md)  
 [Procédures de propriété](./property-procedures.md)  
 [Procédures d’opérateur](./operator-procedures.md)  
 [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)  
 [Sub (instruction)](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Guide pratique : appeler une procédure qui ne retourne pas de valeur](./how-to-call-a-procedure-that-does-not-return-a-value.md)  
 [Comment : appeler un gestionnaire d’événements en Visual Basic](./how-to-call-an-event-handler.md)
