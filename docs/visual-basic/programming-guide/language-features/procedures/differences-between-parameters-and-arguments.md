---
title: "Differences Between Parameters and Arguments (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "procedures, arguments"
  - "procedures, parameters"
  - "parameters, and arguments"
  - "procedure arguments"
  - "Visual Basic code, procedures"
  - "arguments [Visual Basic], and parameters"
  - "procedure parameters"
  - "parameters, definition"
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Differences Between Parameters and Arguments (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Dans la plupart des cas, une procédure a besoin d'informations sur les circonstances dans lesquelles elle est appelée.  Une procédure qui exécute des tâches répétitives ou partagées utilise des informations différentes pour chaque appel.  Ces informations se composent des variables, constantes et expressions passées à la procédure lorsque celle\-ci est appelée.  
  
 Pour communiquer ces informations à la procédure, celle\-ci définit un *paramètre*, et le code appelant passe un *argument* à ce paramètre.  Vous pouvez comparer le paramètre à une place de parking et l'argument à une automobile.  De même que plusieurs automobiles peuvent se garer sur la même place à différents instants, le code appelant peut passer un argument différent au même paramètre à chaque fois qu'il appelle la procédure.  
  
## Paramètres  
 Un *paramètre* représente une valeur que vous êtes censé passer lorsque vous appelez la procédure.  La déclaration de la procédure définit ses paramètres.  
  
 Lorsque vous définissez une procédure `Function` ou `Sub`, vous spécifiez une *liste de paramètres* dans les parenthèses situées directement après le nom de la procédure.  Pour chaque paramètre, spécifiez un nom, un type de données et un mécanisme de passage \([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)\).  Vous pouvez également indiquer qu'un paramètre est facultatif.  Cela signifie que le code appelant n'a pas à passer une valeur pour lui.  
  
 Le nom de chaque paramètre sert de *variable locale* dans la procédure.  Vous utilisez le nom de paramètre de la même façon que vous utilisez toute autre variable.  
  
## Arguments  
 Un *argument* représente la valeur que vous passez à un paramètre de procédure lorsque vous appelez la procédure.  Le code appelant fournit les arguments lorsqu'il appelle la procédure.  
  
 Lors d'un appel à une procédure `Function` ou `Sub`, incluez une *liste d'arguments* dans les parenthèses situées directement après le nom de la procédure.  Chaque argument correspond au paramètre situé à la même position dans la liste.  
  
 Contrairement à une définition de paramètre, les arguments ne portent pas de noms.  Chaque argument est une expression qui peut éventuellement contenir des variables, des constantes et des littéraux.  Le type de données de l'expression évaluée doit correspondre normalement au type de données défini pour le paramètre correspondant, et dans tous les cas doit être convertible en le type de ce paramètre.  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Function, procédures](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define a Parameter for a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-parameter-for-a-procedure.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Recursive Procedures](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)