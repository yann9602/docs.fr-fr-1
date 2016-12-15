---
title: "Optional parameters must specify a default value | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
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
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Optional parameters must specify a default value
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

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