---
title: "Bad record length | Microsoft Docs"
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
  - "vbrID59"
dev_langs: 
  - "VB"
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Bad record length
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cette erreur peut se produire pour de nombreuses raisons.  
  
-   La longueur d'une variable d'enregistrement spécifiée dans une instruction `FileGet`, `FileGetObject`, `FilePut` ou `FilePutObject` diffère de la longueur spécifiée dans l'instruction `FileOpen` correspondante.  
  
-   La variable d'une instruction `FilePut` ou `FilePutObject` est ou inclut une chaîne à longueur variable.  
  
-   La variable d'une instruction `FilePut` ou `FilePutObject` est ou inclut un type `Variant`**.**  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que la somme des tailles des variables de longueur fixe dans le type défini par l'utilisateur qui définit le type de la variable d'enregistrement est identique à la valeur indiquée dans la clause `Len` de l'instruction `FileOpen`.  
  
2.  Si la variable d'une instruction `FilePut` ou `FilePutObject` est ou inclut une chaîne de longueur variable, vérifiez que cette dernière possède au moins 2 caractères de moins que la longueur d'enregistrement spécifiée dans la clause `Len` de l'instruction `FileOpen`.  
  
3.  Si la variable d'une instruction `FilePut` ou `FilePutObject` est ou inclut un type `Variant`, vérifiez que la chaîne de longueur variable possède au moins 4 octets de moins que la longueur d'enregistrement spécifiée dans la clause `Len` de l'instruction `FileOpen`.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>