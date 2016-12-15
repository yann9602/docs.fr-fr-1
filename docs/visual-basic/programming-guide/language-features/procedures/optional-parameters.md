---
title: "Optional Parameters (Visual Basic) | Microsoft Docs"
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
  - "parameters, optional"
  - "Visual Basic code, procedures"
  - "procedures, optional arguments"
  - "optional arguments"
  - "named arguments, and optional arguments"
  - "optional parameters"
  - "Optional keyword, optional arguments"
  - "arguments [Visual Basic], optional"
  - "optional arguments, and named arguments"
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Optional Parameters (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Vous pouvez spécifier qu'un paramètre de procédure est facultatif et qu'il n'est pas nécessaire de fournir un argument lorsque la procédure est appelée.  Les *arguments facultatifs* sont indiqués à l'aide du mot clé `Optional` dans la définition de la procédure.  Les règles suivantes s'appliquent :  
  
-   Chaque paramètre facultatif dans la définition de la procédure doit spécifier une valeur par défaut.  
  
-   La valeur par défaut d'un paramètre facultatif doit être une expression constante.  
  
-   Tous les paramètres qui suivent un paramètre facultatif dans la définition de la procédure doivent également être facultatifs.  
  
 La syntaxe suivante montre une déclaration de procédure comprenant un paramètre facultatif :  
  
```  
Sub sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## Appel de procédures à l'aide de paramètres facultatifs  
 Lorsque vous appelez une procédure à l'aide d'un paramètre facultatif, vous pouvez choisir de fournir l'argument ou non.  Dans le cas contraire, la procédure utilise la valeur par défaut déclarée pour ce paramètre.  
  
 Pour omettre un ou plusieurs arguments facultatifs dans la liste des arguments, utilisez des virgules successives afin de marquer leurs positions.  L'exemple d'appel suivant fournit le premier et le quatrième argument, mais pas le deuxième ni le troisième :  
  
```  
  
sub name(argument 1, , , argument 4)  
```  
  
 L'exemple suivant effectue plusieurs appels à la fonction `MsgBox`.  `MsgBox` comporte un paramètre obligatoire et deux paramètres facultatifs.  
  
 Le premier appel à `MsgBox` fournit les trois arguments dans l'ordre dans lequel `MsgBox` les définit.  Le deuxième appel fournit uniquement l'argument requis.  Le troisième et le quatrième appel fournissent le premier et le troisième argument.  Le troisième appel le fait par position et le quatrième appel le fait par nom.  
  
 [!code-vb[VbVbcnProcedures#47](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/optional-parameters_1.vb)]  
  
## Détermination de la présence d'un argument facultatif  
 Une procédure ne peut pas détecter au moment de l'exécution si un argument donné a été omis ou si le code appelant a explicitement fourni la valeur par défaut.  Pour établir cette distinction, vous pouvez définir une valeur improbable comme valeur par défaut.  La procédure suivante définit le paramètre facultatif  `office`, puis teste sa valeur par défaut,  `QJZ`, pour déterminer s'il a été omis dans l'appel :  
  
 [!code-vb[VbVbcnProcedures#46](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/optional-parameters_2.vb)]  
  
 Si le paramètre facultatif est un type référence tel que `String`, vous pouvez utiliser `Nothing` comme valeur par défaut, à condition qu'il ne s'agisse pas d'une valeur attendue pour l'argument.  
  
## Paramètres facultatifs et surcharge  
 La surcharge est une autre méthode permettant de définir une procédure à l'aide de paramètres facultatifs.  Si vous disposez d'un seul paramètre facultatif, vous pouvez définir deux versions surchargées de la procédure, l'une avec le paramètre et l'autre sans.  Cette approche se complique au fur et à mesure que le nombre de paramètres facultatifs augmente.  Cependant, vous avez l'avantage de savoir avec certitude si le programme appelant a fourni chaque argument facultatif.  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)   
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)