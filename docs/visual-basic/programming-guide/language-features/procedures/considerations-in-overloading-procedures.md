---
title: "Considerations in Overloading Procedures (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "signatures, ParamArray arguments"
  - "ParamArray keyword, parameter arrays"
  - "ParamArray keyword, arguments and signatures"
  - "function overloading, implicit overloads for ParamArray"
  - "ParamArray keyword, signatures"
  - "Visual Basic code, procedures"
  - "arguments [Visual Basic], parameter arrays"
  - "procedures, overloading"
  - "parameters, lists"
  - "function overloading, typeless programming"
  - "typeless programming"
  - "function overloading, restrictions"
  - "arguments [Visual Basic], optional"
  - "optional arguments, overloading"
  - "signatures, procedure"
  - "parameter lists"
  - "parameter arrays, overloading arguments"
  - "Visual Basic code, parameter lists"
  - "procedure overloading, considerations"
  - "Option Explicit statement"
  - "restrictions, overloading procedures"
  - "procedures, parameter lists"
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
caps.latest.revision: 26
caps.handback.revision: 26
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Considerations in Overloading Procedures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Lorsque vous surchargez une procédure, vous devez utiliser une *signature* différente pour chaque version surchargée.  Cela signifie généralement que chaque version doit spécifier une liste de paramètres différente.  Pour plus d'informations, consultez « Signature différente » dans [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
 Vous pouvez surcharger une procédure `Function` avec une procédure `Sub`, et inversement, à condition que leurs signatures soient différentes.  Deux surcharges ne peuvent pas différer uniquement suivant que l'un a une valeur de retour et l'autre pas.  
  
 Vous pouvez surcharger une propriété de la même manière que vous surchargez une procédure et avec les mêmes restrictions.  Toutefois, vous ne pouvez pas surcharger une procédure avec une propriété, ou inversement.  
  
## Alternatives aux versions surchargées  
 Vous disposez parfois d'alternatives aux versions surchargées, en particulier lorsque la présence d'arguments est facultative ou que leur nombre est variable.  
  
 N'oubliez pas que les arguments facultatifs ne sont pas pris en charge nécessairement par tous les langages, et les tableaux de paramètres sont limités à [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  Si vous écrivez une procédure qui sera vraisemblablement appelée à partir du code écrit dans un des différents langages, les versions surchargées offrent la plus grande souplesse.  
  
### Surcharges et arguments facultatifs  
 Lorsque le code appelant peut éventuellement fournir ou omettre un ou plusieurs arguments, vous pouvez définir plusieurs versions surchargées ou utiliser des paramètres facultatifs.  
  
#### Quand utiliser des versions surchargées  
 Pensez à définir une série de versions surchargées dans les cas suivants :  
  
-   La logique dans le code de procédure est très différente suivant que le code appelant fournit un argument facultatif ou pas.  
  
-   Le code de procédure ne peut pas vérifier de manière fiable si le code appelant a fourni un argument facultatif.  Par exemple, c'est le cas s'il n'y a aucun candidat possible pour une valeur par défaut que le code appelant n'était pas supposé fournir.  
  
#### Quand utiliser les paramètres facultatifs  
 Il peut être préférable d'utiliser un ou plusieurs des paramètres facultatifs dans les cas suivants :  
  
-   La seule action requise lorsque le code appelant ne fournit pas un argument facultatif est de définir le paramètre à une valeur par défaut.  Dans ce cas, le code de procédure peut être moins compliqué si vous définissez une version unique avec un ou plusieurs paramètres `Optional`.  
  
 Pour plus d'informations, consultez [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).  
  
### Surcharges et ParamArray  
 Lorsque le code appelant peut passer un nombre variable d'arguments, vous pouvez définir plusieurs versions surchargées ou utiliser un tableau de paramètres.  
  
#### Quand utiliser des versions surchargées  
 Pensez à définir une série de versions surchargées dans les cas suivants :  
  
-   Vous savez que le code appelant ne passe jamais plus qu'un petit nombre de valeurs au tableau de paramètres.  
  
-   La logique dans le code de procédure est très différente selon le nombre de valeurs passées par le code appelant.  
  
-   Le code appelant peut passer des valeurs de types de données différents.  
  
#### Quand utiliser un tableau de paramètres  
 Un paramètre `ParamArray` est plus utile dans les cas suivants :  
  
-   Vous n'êtes pas en mesure de prévoir combien de valeurs le code appelant peut passer au tableau de paramètres et elles pourraient représenter un grand nombre.  
  
-   La logique de procédure implique d'itérer au sein de toutes les valeurs que le code appelant passe, en exécutant essentiellement les mêmes opérations sur chaque valeur.  
  
 Pour plus d'informations, consultez [Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
## Surcharges implicites des paramètres facultatifs  
 Une procédure avec un paramètre [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) équivaut à deux procédures surchargées, l'une avec l'argument facultatif et l'autre sans cet argument.  Vous ne pouvez pas surcharger une procédure avec une liste de paramètres correspondant à l'un ou l'autre de ceux\-ci.  Les déclarations suivantes illustrent ce principe.  
  
 [!code-vb[VbVbcnProcedures#58](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#60](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#61](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]  
  
 Dans le cas d'une procédure possédant plusieurs arguments facultatifs, il existe un ensemble de surcharges implicites, qui peuvent se produire de manière logique, comme dans l'exemple précédent.  
  
## Surcharges implicites pour un paramètre ParamArray  
 Le compilateur considère qu'une procédure comportant un paramètre [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) possède un nombre infini de surcharges, qui se différencient selon ce que le code appelant passe au tableau de paramètres, notamment :  
  
-   Une surcharge lorsque le code appelant ne fournit pas d'argument au `ParamArray`  
  
-   Une surcharge lorsque le code appelant fournit un tableau unidimensionnel du type d'élément `ParamArray`  
  
-   Pour chaque entier positif, une surcharge lorsque le code appelant fournit le nombre correspondant d'arguments dont le type d'élément est `ParamArray`  
  
 Les déclarations suivantes illustrent ces surcharges implicites.  
  
 [!code-vb[VbVbcnProcedures#68](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]  
  
 Vous ne pouvez pas surcharger une procédure avec une liste de paramètres qui accepte un tableau unidimensionnel comme tableau de paramètres.  Toutefois, vous pouvez utiliser les signatures des autres surcharges implicites.  Les déclarations suivantes illustrent ce principe.  
  
 [!code-vb[VbVbcnProcedures#71](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]  
  
## Programmation sans type en remplacement de la surcharge  
 Si vous souhaitez permettre au code appelant à de passer des types de données différents à un paramètre, est une approche alternative programmation sans type.  Vous pouvez affecter au commutateur de vérification de type la valeur `Off` avec l'[Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) ou l'option du compilateur [\/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md).  Vous ne devez donc pas déclarer le type de données du paramètre.  Cependant, cette approche présente les inconvénients suivants par rapport à la surcharge :  
  
-   La programmation sans type génère une exécution moins efficace du code.  
  
-   La procédure doit tester tous les types de données pouvant être passés.  
  
-   Le compilateur ne peut pas signaler d'erreur si le code appelant passe un type de données non pris en charge par la procédure.  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [How to: Define Multiple Versions of a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [How to: Call an Overloaded Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-overloaded-procedure.md)   
 [How to: Overload a Procedure that Takes Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)   
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)