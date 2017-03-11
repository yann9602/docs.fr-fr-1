---
title: "Overload Resolution (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, procedures"
  - "overload resolution"
  - "procedures, overloading"
  - "procedures, calling"
  - "procedure overloading, overload resolution"
  - "signatures, procedure"
  - "overloads, resolution"
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Overload Resolution (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Lorsque le compilateur [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] rencontre un appel à une procédure défini dans plusieurs versions surchargées, il doit décider de la surcharge à appeler.  Pour ce faire, il effectue les étapes suivantes :  
  
1.  **Accessibilité.** Il élimine toute surcharge avec un niveau d'accès qui empêche le code appelant de l'appeler.  
  
2.  **Nombre de paramètres.** Il élimine les surcharges qui définissent un nombre de paramètres différent de ceux spécifiés dans l'appel.  
  
3.  **Types de données des paramètres.** Le compilateur donne la préférence aux méthodes d'instance plutôt qu'aux méthodes d'extension.  Si une méthode d'instance est trouvée, qui requiert que seules les conversions étendues correspondent à l'appel de procédure, toutes les méthodes d'extension sont abandonnées et le compilateur continue uniquement avec les candidats de méthode d'instance.  Si aucune méthode d'instance de ce type n'est trouvée, il continue à la fois avec les méthodes d'extension et les méthodes d'instance.  
  
     Au cours de cette étape, il élimine les surcharges dont les types de données des arguments d'appel ne sont pas convertibles en types de paramètres définis dans la surcharge.  
  
4.  **Conversions restrictives.** Il élimine les surcharges qui nécessitent une conversion restrictive des types des arguments d'appel vers les types des paramètres définis.  Cette règle est valable que le commutateur de vérification de type \([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) ait pour valeur `On` ou `Off`.  
  
5.  **Moindre extension.** Le compilateur prend en compte les surcharges restantes par paires.  Pour chaque paire, il compare les types de données des paramètres définis.  Si les types de l'une des surcharges s'étendent tous aux types correspondants dans l'autre surcharge, le compilateur élimine la seconde surcharge.  En d'autres termes, il conserve la surcharge qui requiert l'extension la moins importante.  
  
6.  **Candidat unique.** Il continue à rassembler les surcharges par paires jusqu'à ce qu'il ne reste qu'une seule surcharge et il résout l'appel vers celle\-ci.  Si le compilateur ne peut pas réduire les surcharges vers un seul candidat, il génère une erreur.  
  
 L'illustration suivante montre le processus de définition de la version à appeler parmi un jeu de versions surchargées.  
  
 ![Diagramme de flux du processus de résolution de surcharge](../../../../visual-basic/programming-guide/language-features/procedures/media/overloadres.gif "OverloadRes")  
Résolution parmi des versions surchargées  
  
 L'exemple suivant illustre ce processus de résolution de surcharge :  
  
 [!code-vb[VbVbcnProcedures#62](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/overload-resolution_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/overload-resolution_2.vb)]  
  
 Dans le premier appel, le compilateur élimine la première surcharge parce que le type du premier argument \(`Short`\) est restreint au type du paramètre correspondant \(`Byte`\).  Il élimine ensuite la troisième surcharge parce que chaque type d'argument dans la deuxième surcharge \(`Short` et `Single`\) est étendu au type correspondant dans la troisième surcharge \(`Integer` et `Single`\).  La deuxième surcharge requérant une extension moins importante, le compilateur l'utilise pour l'appel.  
  
 Dans le deuxième appel, le compilateur ne peut éliminer aucune des surcharges sur la base de la restriction.  Il élimine la troisième surcharge pour la même raison que dans le premier appel, parce qu'il peut appeler la deuxième surcharge moyennant une extension moins importante des types des arguments.  Toutefois, le compilateur ne peut pas effectuer de résolution entre la première et la deuxième surcharges.  Chaque surcharge possède un type de paramètre défini qui s'étend au type correspondant de l'autre \(`Byte` vers `Short`, mais `Single` vers `Double`\).  Par conséquent, le compilateur génère une erreur de résolution de surcharge.  
  
## Arguments Optional et ParamArray de surcharge  
 Si deux surcharges d'une procédure ont des signatures identiques, mais que le dernier paramètre est déclaré [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) dans l'une et [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) dans l'autre, le compilateur résout un appel à cette procédure comme suit :  
  
|||  
|-|-|  
|Si l'appel fournit le dernier argument comme|Le compilateur résout l'appel vers la surcharge en déclarant le dernier argument comme|  
|Aucune valeur \(argument omis\)|`Optional`|  
|Une valeur unique|`Optional`|  
|Au moins deux valeurs dans une liste séparée par des virgules|`ParamArray`|  
|Tableau de toute longueur \(y compris un tableau vide\)|`ParamArray`|  
  
## Voir aussi  
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [How to: Define Multiple Versions of a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [How to: Call an Overloaded Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-overloaded-procedure.md)   
 [How to: Overload a Procedure that Takes Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)   
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)   
 [méthodes d'extension.](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)