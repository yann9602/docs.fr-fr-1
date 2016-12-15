---
title: "How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic) | Microsoft Docs"
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
  - "variables [Visual Basic], accessing"
  - "variables [Visual Basic], object"
  - "With statement"
  - "With block"
  - "object variables, accessing"
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Si vous accédez fréquemment à un objet qui requiert un chemin d'accès de qualification de plusieurs méthodes et propriétés, vous pouvez accélérer votre code en évitant de répéter le chemin d'accès de qualification.  
  
 Vous pouvez éviter de répéter le chemin d'accès de qualification de deux manières.  Vous pouvez assigner l'objet à une variable ou vous pouvez l'utiliser dans un bloc `With`...`End With`.  
  
### Pour accélérer l'accès à un objet très qualifié en l'assignant à une variable  
  
1.  Déclarez une variable du type de l'objet auquel vous accédez fréquemment.  Spécifiez le chemin d'accès de qualification dans la partie d'initialisation de la déclaration.  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  Utilisez la variable pour accéder aux membres de l'objet.  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### Pour accélérer l'accès à un objet très qualifié à l'aide d'un bloc With...End With  
  
1.  Placez le chemin d'accès de qualification dans une instruction `With`.  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  Accédez aux membres de l'objet à l'intérieur du bloc `With` avant l'instruction `End With`  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## Voir aussi  
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)