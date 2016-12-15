---
title: "How to: Declare an Object Variable and Assign an Object to It in Visual Basic | Microsoft Docs"
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
  - "object variables, declaring"
  - "declaring object variables"
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Declare an Object Variable and Assign an Object to It in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Déclarez une variable du [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) en spécifiant `As Object` dans une [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).  Assignez un objet à cette variable en insérant celui\-ci après le signe égal \(`=`\) dans une instruction d'assignation ou une clause d'initialisation.  
  
## Exemple  
 L'exemple suivant déclare une variable `Object` et lui assigne l'instance de classe en cours.  
  
```  
  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 Vous pouvez associer la déclaration et l'assignation en initialisant la variable dans le cadre de sa déclaration.  L'exemple suivant équivaut au précédent.  
  
```  
Dim thisObject As Object = "This is an Object"  
```  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Référence à l'espace de noms <xref:System>.  
  
-   une classe, une structure ou un module où placer l'instruction `Dim` ;  
  
-   une procédure dans laquelle placer l'instruction d'assignation.  
  
## Voir aussi  
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)