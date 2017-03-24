---
title: "Sub de procédures (Visual Basic) | Documents Microsoft"
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
- Sub procedures, about Sub procedures
- statement blocks
- Sub procedures, calling
- procedures, calling
- Sub procedures, syntax
- Sub procedures
- procedures, Sub
- syntax, Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
caps.latest.revision: 21
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
ms.openlocfilehash: d224fa3338ca707070ee431380578a8fdde47e07
ms.lasthandoff: 03/13/2017

---
# <a name="sub-procedures-visual-basic"></a>Procédures Sub (Visual Basic)
A `Sub` procédure est une série de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] instructions placées par le `Sub` et `End Sub` instructions. Le `Sub` procédure effectue une tâche, puis retourne le contrôle au code appelant, mais elle ne retourne pas de valeur au code appelant.  
  
 Chaque fois que la procédure est appelée, ses instructions sont exécutées à partir de la première instruction exécutable après le `Sub` instruction et se terminant par la première `End Sub`, `Exit Sub`, ou `Return` instruction rencontrée.  
  
 Vous pouvez définir un `Sub` procédure dans les modules, les classes et structures. Par défaut, il est `Public`, ce qui signifie que vous pouvez l’appeler depuis n’importe où dans votre application qui a accès au module, classe ou une structure dans laquelle vous définie. Le terme *méthode*, décrit une `Sub` ou `Function` procédure qui est accessible en dehors de sa définition de module, classe ou structure. Pour plus d’informations, consultez [procédures](./index.md).  
  
 Un `Sub` procédure peut prendre des arguments, tels que les constantes, variables ou expressions qui sont passées par le code appelant.  
  
## <a name="declaration-syntax"></a>Syntaxe de déclaration  
 La syntaxe de déclaration d’un `Sub` comme suit :  
  
 `[`*modifiers* `] Sub`*subname* `[(` *parameterlist*  `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 Le `modifiers` peut spécifier de niveau d’accès et des informations sur la surcharge, la substitution, le partage et l’occultation. Pour plus d’informations, consultez [Sub, instruction](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="parameter-declaration"></a>Déclaration de paramètre  
 Vous déclarez chaque paramètre de procédure de la même façon à comment vous déclarez une variable, en spécifiant le type de données et le nom du paramètre. Vous pouvez également spécifier le mécanisme de passage et si le paramètre est facultatif ou un tableau de paramètres.  
  
 La syntaxe de chaque paramètre dans la liste des paramètres est la suivante :  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *ParameterName*`As`*type de données    *  
  
 Si le paramètre est facultatif, vous devez également fournir une valeur par défaut dans le cadre de sa déclaration. La syntaxe de spécification d’une valeur par défaut est la suivante :  
  
 `Optional [ByVal | ByRef]`  *ParameterName*`As`*type de données*`=`*defaultvalue        *  
  
### <a name="parameters-as-local-variables"></a>Paramètres en tant que Variables locales  
 Lorsque le contrôle passe à la procédure, chaque paramètre est traité comme une variable locale. Cela signifie que sa durée de vie est la même que celle de la procédure, et son étendue est l’ensemble de la procédure.  
  
## <a name="calling-syntax"></a>Syntaxe d’appel  
 Vous appelez un `Sub` procédure explicitement avec une instruction d’appel autonome. Vous ne pouvez pas l’appeler en utilisant son nom dans une expression. Vous devez fournir des valeurs pour tous les arguments qui ne sont pas facultatifs, et vous devez placer la liste d’arguments entre parenthèses. Si aucun argument n’est fourni, vous pouvez omettre les parenthèses. L’utilisation de la `Call` mot clé est facultatif, mais non recommandée.  
  
 La syntaxe d’un appel à une `Sub` comme suit :  
  
 `[Call]`  *nomsub* `[(` *argumentlist*`)]`  
  
 Vous pouvez appeler une `Sub` méthode en dehors de la classe qui le définit. Tout d’abord, vous devez utiliser le `New` (mot clé) pour créer une instance de la classe ou appeler une méthode qui retourne une instance de la classe. Pour plus d’informations, consultez [nouveau opérateur](../../../../visual-basic/language-reference/operators/new-operator.md). Ensuite, vous pouvez utiliser la syntaxe suivante pour appeler le `Sub` méthode sur l’objet d’instance :  
  
 *Object*.* MethodName*`[(`*argumentlist*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>Illustration de déclaration et d’appel  
 Les éléments suivants `Sub` procédure indique à l’opérateur la tâche que l’application est sur le point d’exécuter et affiche également un horodatage. Au lieu de dupliquer ce code au début de chaque tâche, l’application appelle simplement `tellOperator` à partir de différents emplacements. Chaque appel passe une chaîne dans le `task` qui identifie la tâche en cours de démarrage.  
  
 [!code-vb[VbVbcnProcedures n °&2;](./codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 L’exemple suivant montre un appel typique à `tellOperator`.  
  
 [!code-vb[VbVbcnProcedures n °&3;](./codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)   
 [Procédures Function](./function-procedures.md)   
 [Procédures de propriété](./property-procedures.md)   
 [Procédures d’opérateur](./operator-procedures.md)   
 [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md)   
 [Sub (instruction)](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Comment : appeler une procédure qui ne retourne pas de valeur](./how-to-call-a-procedure-that-does-not-return-a-value.md)   
 [Comment : appeler un gestionnaire d’événements en Visual Basic](./how-to-call-an-event-handler.md)
