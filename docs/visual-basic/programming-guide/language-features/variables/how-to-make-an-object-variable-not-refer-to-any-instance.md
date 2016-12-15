---
title: "How to: Make an Object Variable Not Refer to Any Instance (Visual Basic) | Microsoft Docs"
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
  - "Nothing keyword, variable assignment"
  - "object variables, null reference"
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Vous pouvez dissocier une variable objet de toute instance d'objet en lui affectant la valeur [Nothing](../../../../visual-basic/language-reference/nothing.md).  
  
### Pour dissocier une variable objet de toute instance d'objet  
  
-   Affectez à la variable la valeur `Nothing` dans une instruction d'assignation.  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## Programmation fiable  
 Si votre code essaie d'accéder à un membre d'une variable objet qui a la valeur `Nothing`, une exception <xref:System.NullReferenceException> se produit.  Si vous affectez fréquemment à une variable objet la valeur `Nothing` ou s'il est possible que la variable ne soit pas initialisée, il peut être souhaitable de placer les accès aux membres dans un bloc `Try...Catch...Finally`.  
  
## Sécurité .NET Framework  
 Si vous utilisez une variable objet pour des objets qui contiennent des données confidentielles ou sensibles, vous pouvez affecter à la variable la valeur `Nothing` lorsque vous n'utilisez pas activement l'un de ces objets.  Cela réduit le risque que du code malveillant accède aux données.  
  
## Voir aussi  
 <xref:System.NullReferenceException>   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Nothing](../../../../visual-basic/language-reference/nothing.md)   
 [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Dépannage des exceptions : System.NullReferenceException](../Topic/Troubleshooting%20Exceptions:%20System.NullReferenceException.md)