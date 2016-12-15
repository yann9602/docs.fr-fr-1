---
title: "Statement is not valid in a namespace | Microsoft Docs"
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
  - "vbc30001"
  - "bc30001"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30001"
ms.assetid: 43c1b509-15f9-4e91-bcad-90bcb5f6f191
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Statement is not valid in a namespace
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'instruction ne peut pas apparaître au niveau d'un espace de noms.  Les seules déclarations autorisées au niveau de l'espace de noms sont les déclarations de module, d'interface, de classe, de délégué, d'énumération et de structure.  
  
 **ID d'erreur :** BC30001  
  
### Pour corriger cette erreur  
  
-   Déplacez l'instruction vers un emplacement situé à l'intérieur d'une définition de module, de classe, d'interface, de structure, d'énumération ou de délégué.  
  
## Voir aussi  
 [Scope in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)