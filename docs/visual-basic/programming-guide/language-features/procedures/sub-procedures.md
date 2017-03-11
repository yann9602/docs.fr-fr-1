---
title: "Sub Procedures (Visual Basic) | Microsoft Docs"
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
  - "Sub procedures, about Sub procedures"
  - "statement blocks"
  - "Sub procedures, calling"
  - "procedures, calling"
  - "Sub procedures, syntax"
  - "Sub procedures"
  - "procedures, Sub"
  - "syntax, Sub procedures"
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Sub Procedures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Une procédure `Sub` est une série d'instructions [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] délimitées par les instructions `Sub` et `End Sub`.  La procédure `Sub` effectue une tâche, puis retourne le contrôle au code appelant, mais ne retourne pas de valeur au code appelant.  
  
 Chaque fois que la procédure est appelée, ses instructions sont exécutées à partir de la première instruction exécutable située après l'instruction `Sub` jusqu'à la première instruction `End Sub`, `Exit Sub` ou `Return` rencontrée.  
  
 Vous pouvez définir une procédure `Sub` dans les modules, les classes et les structures.  La valeur par défaut est `Public`, ce qui signifie que vous pouvez l'appeler de n'importe où dans votre application qui a accès au module, à la classe ou à la structure dans laquelle vous l'avez définie.  Le terme *méthode* décrit une procédure `Sub` ou `Function`, accessible en dehors de son module, de sa classe ou de sa structure de définition.  Pour plus d'informations, consultez [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md).  
  
 Une procédure `Sub` peut accepter des arguments tels que les constantes, les variables ou les expressions qui sont passées à la procédure par le code appelant.  
  
## Syntaxe de déclaration  
 La syntaxe de déclaration d'une procédure `Sub` est la suivante :  
  
 `[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 Les `modifiers` peuvent spécifier un niveau d'accès et des informations concernant la surcharge, la substitution, le partage et l'occultation.  Pour plus d'informations, consultez [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## Déclaration de paramètre  
 Déclarez chaque paramètre de procédure de la même manière que lorsque vous déclarez une variable, en spécifiant le nom de paramètre et le type de données.  Vous pouvez également spécifier le mécanisme de passage et indiquer si le paramètre est facultatif ou s'il s'agit d'un tableau de paramètres.  
  
 La syntaxe de chaque paramètre dans la liste des paramètres est la suivante :  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*  
  
 Si le paramètre est facultatif, vous devez également fournir une valeur par défaut dans le cadre de sa déclaration.  La syntaxe de spécification d'une valeur par défaut est la suivante :  
  
 `Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*  
  
### Paramètres en tant que variables locales  
 Lorsque contrôle passe à la procédure, chaque paramètre est traité comme une variable locale.  Cela signifie que sa durée de vie est la même que celle de la procédure et que sa portée correspond à l'ensemble de la procédure.  
  
## Syntaxe d'appel  
 Vous appelez une procédure `Sub` de manière explicite à l'aide d'une instruction d'appel autonome.  Vous ne pouvez pas l'appeler en utilisant son nom dans une expression.  Vous devez fournir les valeurs de tous les arguments qui ne sont pas facultatifs et mettre la liste des arguments entre parenthèses.  Si aucun argument n'est spécifié, vous pouvez ne pas mettre les parenthèses.  L'utilisation du mot clé `Call` est facultative, mais non recommandée.  
  
 La syntaxe d'appel à une procédure `Sub` est la suivante :  
  
 `[Call]`  *subname* `[(` *argumentlist* `)]`  
  
 Vous pouvez appeler une méthode `Sub` en dehors de la classe qui la définit.  En premier lieu, vous devez utiliser le mot clé `New` pour créer une instance de la classe ou appeler une méthode qui retourne une instance de la classe.  Pour plus d'informations, consultez [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).  Puis, vous pouvez utiliser la syntaxe suivante pour appeler la méthode `Sub` l'objet d'instance :  
  
 *Object*.*methodname*`[(`*argumentlist*`)]`  
  
### Illustration de déclaration et d'appel  
 La procédure `Sub` ci\-dessous indique à l'opérateur la tâche que l'application est sur le point d'exécuter, et affiche également des informations de date.  Au lieu de dupliquer ce code au début de chaque tâche, l'application appelle simplement  `tellOperator`  depuis différents emplacements.  Chaque appel passe une chaîne dans l'argument  `task`  qui identifie la tâche en cours de démarrage.  
  
 [!code-vb[VbVbcnProcedures#2](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/sub-procedures_1.vb)]  
  
 L'exemple suivant montre un appel typique à  `tellOperator`  
  
 [!code-vb[VbVbcnProcedures#3](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/sub-procedures_2.vb)]  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Function, procédures](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [How to: Call a Procedure that Does Not Return a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-does-not-return-a-value.md)   
 [How to: Call an Event Handler in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-event-handler.md)