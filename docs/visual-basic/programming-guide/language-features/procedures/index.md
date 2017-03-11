---
title: "Procedures in Visual Basic | Microsoft Docs"
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
  - "procedures, structured code"
  - "Visual Basic code, procedures"
  - "procedures, types of"
  - "structured code, procedures"
  - "procedures"
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Procedures in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Une *procédure* est un bloc d'instructions [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] délimité par une instruction de déclaration \(`Function`, `Sub` , `Operator` , `Get`,  `Set`\) et une déclaration `End` correspondante.  Toutes les instructions exécutables en [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] doivent être incluses dans une procédure.  
  
## Appel d'une procédure  
 Vous appelez une procédure à partir de n'importe quel emplacement dans le code.  C'est ce qu'on appelle un *appel de procédure*.  Lorsque la procédure a fini de s'exécuter, elle retourne le contrôle au code qui l'a appelé, en d'autres termes, le *code appelant*.  Le code appelant est une instruction, ou une expression comprise dans une instruction, qui spécifie la procédure par son nom et lui transfère le contrôle.  
  
## Retour d'une procédure  
 Une procédure retourne le contrôle au code appelant à la fin de son exécution.  Pour ce faire, elle peut utiliser une instruction [Return Statement](../../../../visual-basic/language-reference/statements/return-statement.md), l'instruction [Exit Statement](../../../../visual-basic/language-reference/statements/exit-statement.md) appropriée pour la procédure, ou l'instruction [End \<keyword\> Statement](../../../../visual-basic/language-reference/statements/end-keyword-statement.md) de la procédure.  Le contrôle passe ensuite au code appelant qui suit le point de l'appel de procédure.  
  
-   Avec une instruction `Return`, le contrôle retourne immédiatement au code appelant.  Les instructions qui suivent l'instruction `Return` ne s'exécutent pas.  Une même procédure peut contenir plusieurs instructions `Return`.  
  
-   Avec une instruction `Exit Sub` ou `Exit Function`, le contrôle retourne immédiatement au code appelant.  Les instructions qui suivent l'instruction `Exit` ne s'exécutent pas.  Une même procédure peut contenir plusieurs instructions `Exit` et vous pouvez mixer les instructions `Return` et `Exit` dans la même procédure.  
  
-   Si une procédure ne contient pas d'instructions `Return` ou `Exit`, elle conclut par une instruction `End Sub` ou `End Function`, `End Get` ou `End Set` qui suit la dernière instruction du corps de la procédure.  L'instruction `End` retourne immédiatement le contrôle au code appelant.  Une procédure peut contenir uniquement une instruction `End`.  
  
## Paramètres et arguments  
 Dans la plupart des cas, une procédure doit utiliser des données différentes à chaque appel.  Vous pouvez passer ces informations à la procédure dans le cadre de l'appel de procédure.  La procédure définit zéro ou plus de *paramètres*, chacun représentant une valeur que vous devez lui passer.  À chaque paramètre dans la définition de procédure correspond un *argument* dans l'appel de procédure.  Un argument représente la valeur que vous passez au paramètre correspondant dans un appel de procédure donné.  
  
## Types de procédures  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] utilise plusieurs types de procédures :  
  
-   Les procédures [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) exécutent des actions mais ne retournent aucune valeur au code d'appel.  
  
-   Les procédures de gestion des événements sont des procédures `Sub` qui s'exécutent en réponse à un événement déclenché par l'action d'un utilisateur ou une occurrence dans un programme.  
  
-   Les procédures [Function, procédures](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) retournent une valeur au code d'appel.  Elles peuvent exécuter d'autres actions avant de retourner.  
  
-   Les procédures [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md) retournent et assignent des valeurs de propriétés aux objets ou aux modules.  
  
-   Les procédures [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md) définissent le comportement d'un opérateur standard lorsque l'un ou les deux opérandes désignent une classe ou une structure définie récemment.  
  
-   Les procédures [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) définissent un ou plusieurs *paramètres de type*, en plus de leurs paramètres normaux. Par conséquent, le code appelant peut passer des types de données spécifiques à chaque appel.  
  
## Procédures et code structuré  
 Chaque ligne de code exécutable dans votre application doit faire partie d'une procédure, par exemple `Main`, `calculate` ou `Button1_Click`.  Si vous subdivisez les procédures de grande taille en procédures plus petites, vous facilitez la lecture de votre application.  
  
 Les procédures permettent d'exécuter des tâches répétées ou partagées, par exemple des calculs fréquents, des manipulations de textes et de contrôles ou des opérations de base de données.  Vous pouvez appeler une procédure à partir de divers emplacements dans votre code, ce qui vous permet d'utiliser les procédures comme des blocs de construction pour votre application.  
  
 Le fait de structurer votre code à l'aide de procédures vous apporte les avantages suivants :  
  
-   Les procédures vous permettent de décomposer vos programmes en unités logiques discrètes.  Vous pouvez déboguer plus facilement des unités séparées qu'un programme entier sans procédures.  
  
-   Vous pouvez utiliser des procédures développées pour un programme dans d'autres programmes, avec peu ou pas de modifications.  Cela permet d'éviter la duplication du code.  
  
## Voir aussi  
 [How to: Create a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Function, procédures](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Recursive Procedures](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)