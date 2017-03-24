---
title: "How to: Overload a Procedure that Takes Optional Parameters (Visual Basic) | Microsoft Docs"
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
  - "procedures, parameters"
  - "procedure overloading, optional parameters"
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "procedure parameters"
  - "procedures, overloading"
  - "procedures, multiple versions"
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Si une procédure possède un ou plusieurs paramètres [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), vous ne pouvez pas définir de version surchargée correspondant une de ses surcharges implicites.  Pour plus d'informations, consultez des "Implicit Overloads for Optional Parameters" dans [Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md).  
  
## Paramètre facultatif unique  
  
#### Pour surcharger une procédure qui accepte un paramètre facultatif  
  
1.  Écrivez une instruction de déclaration `Sub` ou `Function` qui inclut le paramètre facultatif dans la liste de paramètres.  N'utilisez pas le mot clé `Optional` dans cette version surchargée.  
  
2.  Faites précéder le mot clé `Sub` ou `Function` du mot clé [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md).  
  
3.  Écrivez le code de procédure qui doit être exécuté lorsque le code appelant fournit l'argument facultatif.  
  
4.  Terminez la procédure par l'instruction `End Sub` ou `End Function`, selon le cas.  
  
5.  Écrivez une deuxième instruction de déclaration qui est identique à la première déclaration, excepté qu'elle n'inclut pas le paramètre facultatif dans la liste de paramètres.  
  
6.  Écrivez le code de procédure qui doit être exécuté lorsque le code appelant ne fournit pas l'argument facultatif.  Terminez la procédure par l'instruction `End Sub` ou `End Function`, selon le cas.  
  
     L'exemple suivant affiche une procédure définie par un paramètre facultatif, un jeu d'équivalents de deux procédures surchargées et enfin des exemples de versions surchargées non valides et valides.  
  
     [!code-vb[VbVbcnProcedures#59](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_2.vb)]  
  
     [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_3.vb)]  
  
## Paramètres facultatifs multiples  
 Pour créer une procédure disposant de plusieurs paramètres facultatifs, vous avez normalement besoin de plus de deux versions surchargées.  Par exemple, s'il y a deux paramètres optionnels, et le code appelant peut fournir ou omettre indépendamment chacun de l'autre, vous avez besoin de quatre versions surchargées, une pour chaque combinaison possible d'arguments fournis.  
  
 Comme le nombre de paramètres facultatifs augmente, la complexité de la surcharge augmente également.  À moins que certaines combinaisons d'arguments fournies ne soient pas acceptables, pour N paramètres facultatifs, vous devez disposer de 2 ^ N versions surchargées.  Selon la nature de la procédure, vous pouvez trouver que la clarté de logique justifie l'effort supplémentaire de définition de toutes les versions surchargées.  
  
#### Pour surcharger une procédure qui accepte plusieurs paramètres facultatifs  
  
1.  Déterminez quelles combinaisons d'arguments facultatifs fournis sont acceptables par rapport à la logique de la procédure.  Une combinaison inacceptable peut survenir si un paramètre facultatif dépend d'un autre.  Par exemple, si un paramètre accepte le nom du conjoint et qu'un autre accepte son âge, une combinaison d'arguments fournissant l'âge, mais omettant le nom est inacceptable.  
  
2.  Pour chaque combinaison acceptable d'arguments facultatifs fournis, écrivez une instruction de déclaration `Sub` ou `Function` qui définit la liste de paramètres correspondante.  N'utilisez pas le mot clé `Optional`.  
  
3.  Dans chaque déclaration, précédez le mot clé `Sub` ou `Function` par le mot clé [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md).  
  
4.  Après chaque déclaration, écrivez le code de procédure à exécuter lorsque le code appelant fournit une liste d'arguments correspondant à la liste de paramètres de cette déclaration.  
  
5.  Terminez chaque procédure par l'instruction `End Sub` ou `End Function`, selon le cas.  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [How to: Define Multiple Versions of a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [How to: Call an Overloaded Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-overloaded-procedure.md)   
 [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)