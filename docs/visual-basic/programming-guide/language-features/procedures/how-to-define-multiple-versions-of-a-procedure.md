---
title: "How to: Define Multiple Versions of a Procedure (Visual Basic) | Microsoft Docs"
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
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "procedures, overloading"
  - "procedures, multiple versions"
  - "procedure overloading, multiple versions"
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Define Multiple Versions of a Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez définir une procédure dans plusieurs versions en la *surchargeant*, à l'aide du même nom, mais avec une liste de paramètres différente pour chaque version.  La finalité d'une surcharge est de définir plusieurs versions de procédures étroitement liées sans avoir à les différencier par nom.  
  
 Pour plus d'informations, consultez [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
### Pour définir plusieurs versions d'une procédure  
  
1.  Écrivez une instruction de déclaration `Sub` ou `Function` pour chaque version de la procédure que vous souhaitez définir.  Utilisez le même nom de procédure dans chaque déclaration.  
  
2.  Précédez le mot clé `Sub` ou `Function` dans chaque déclaration du mot clé [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md).  Vous pouvez omettre `Overloads` dans les déclarations, mais si vous l'incluez dans une des déclarations, vous devez l'inclure dans toutes les déclarations.  
  
3.  À la suite de chaque instruction de déclaration, écrivez le code de procédure pour gérer le cas spécifique où le code appelant fournit des arguments qui correspondent à la liste de paramètres de cette version.  Vous n'avez pas à tester les paramètres fournis par le code appelant.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] passe le contrôle à la version correspondante de votre procédure.  
  
4.  Terminez chaque version de la procédure avec l'instruction `End Sub` ou `End Function` selon le cas.  
  
## Exemple  
 L'exemple suivant définit une procédure `Sub` pour publier une transaction par rapport au compte d'un client.  Il utilise le mot clé `Overloads` pour définir deux versions de la procédure, un qui accepte le client par son nom et l'autre par son numéro de compte.  
  
 [!code-vb[VbVbcnProcedures#72](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-define-multiple-v_1.vb)]  
  
 Le code appelant peut obtenir l'identification de client en tant que `String` ou en tant que `Integer`, puis utiliser la même instruction appelante dans les deux cas.  
  
 Pour plus d'informations sur l'appel de ces versions de la procédure `post`, consultez [How to: Call an Overloaded Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-overloaded-procedure.md).  
  
## Compilation du code  
 Assurez\-vous que chacune de vos versions surchargées a le même nom de procédure, mais une liste de paramètres différente.  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [How to: Overload a Procedure that Takes Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)