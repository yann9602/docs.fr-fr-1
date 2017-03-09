---
title: "Optional parameters must specify a default value | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30812"
  - "bc30812"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30812"
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Optional parameters must specify a default value
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Les paramètres optionnels doivent fournir des valeurs par défaut que vous pouvez utiliser si aucun paramètre n'est fourni par une procédure d'appel.  
  
 **ID d'erreur :** BC30812  
  
### Pour corriger cette erreur  
  
-   Spécifiez des valeurs par défaut pour les paramètres optionnels. Par exemple :  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## Voir aussi  
 [Optional](../../../visual-basic/language-reference/modifiers/optional.md)