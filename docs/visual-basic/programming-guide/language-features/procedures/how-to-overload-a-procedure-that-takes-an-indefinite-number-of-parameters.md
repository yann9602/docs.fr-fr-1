---
title: "How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic) | Microsoft Docs"
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
  - "procedure overloading, indefinite number of parameters"
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "procedure parameters"
  - "procedures, overloading"
  - "procedures, multiple versions"
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Si une procédure dispose d'un paramètre [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md), vous ne pouvez pas définir une version surchargée acceptant un tableau unidimensionnel comme tableau de paramètres.  Pour plus d'informations, consultez des "Implicit Overloads for a ParamArray Parameter" dans [Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md).  
  
### Pour surcharger une procédure qui accepte un nombre variable de paramètres  
  
1.  Assurez\-vous que la procédure et la logique du code appelant bénéficient davantage de versions surchargées que d'un paramètre `ParamArray`.  Consultez des "Overloads and ParamArrays" dans [Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md).  
  
2.  Déterminez le nombre de valeurs fournies que la procédure doit accepter dans la partie variable de la liste de paramètres.  Elle peut n'accepter aucune valeur, ou accepter un tableau unidimensionnel unique.  
  
3.  Pour chaque nombre acceptable de valeurs fournies, écrivez une instruction de déclaration `Sub` ou `Function` qui définit la liste de paramètres correspondante.  N'utilisez ni le mot clé `Optional` ni `ParamArray` dans la version surchargée.  
  
4.  Dans chaque déclaration, précédez le mot clé `Sub` ou `Function` par le mot clé [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md).  
  
5.  Après chaque déclaration, écrivez le code de procédure à exécuter lorsque le code appelant fournit des valeurs correspondant à la liste de paramètres de cette déclaration.  
  
6.  Terminez chaque procédure par l'instruction `End Sub` ou `End Function`, selon le cas.  
  
## Exemple  
 L'exemple suivant affiche une procédure définie avec un paramètre [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md), puis un jeu équivalent de procédures surchargées.  
  
 [!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 Vous ne pouvez pas surcharger une procédure avec une liste de paramètres qui accepte un tableau unidimensionnel comme tableau de paramètres.  Toutefois, vous pouvez utiliser les signatures des autres surcharges implicites.  Les déclarations suivantes illustrent ce principe.  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 Le code dans les versions surchargées n'a pas à tester si le code appelant a fourni une ou plusieurs valeurs pour le paramètre `ParamArray`, ou si tel est le cas, le nombre de valeurs.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] passe le contrôle à la version qui correspond à la liste d'arguments appelants.  
  
## Compilation du code  
 Comme une procédure avec un paramètre `ParamArray` est équivalente à un jeu de versions surchargées, vous ne pouvez pas la surcharger avec une liste de paramètres correspondant à chacune de ces surcharges implicites.  Pour plus d'informations, consultez [Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md).  
  
## Sécurité .NET Framework  
 Si vous travaillez dans un tableau dont la taille peut être indéfinie, vous risquez de saturer la capacité interne de votre application.  Si vous acceptez un tableau de paramètres, vous devez tester la longueur du tableau passée par le code appelant et effectuer les étapes appropriées s'il est trop long pour votre application.  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [How to: Define Multiple Versions of a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [How to: Call an Overloaded Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-overloaded-procedure.md)   
 [How to: Overload a Procedure that Takes Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)