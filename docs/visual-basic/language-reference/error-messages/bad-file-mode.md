---
title: "Bad file mode | Microsoft Docs"
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
  - "vbrID54"
dev_langs: 
  - "VB"
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Bad file mode
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les instructions utilisées dans la manipulation du contenu de fichier doivent être appropriées au mode dans lequel le fichier a été ouvert.  Plusieurs causes sont possibles :  
  
-   Une instruction `FilePutObject` ou `FileGetObject` spécifie un fichier séquentiel.  
  
-   Une instruction `Print` spécifie un fichier ouvert pour un mode d'accès autre que `Output` ou `Append`.  
  
-   Une instruction `Input` spécifie un fichier ouvert pour un mode d'accès autre que `Input`.  
  
-   Tentative d'écriture sur une propriété en lecture seule.  
  
### Pour corriger cette erreur  
  
-   Vérifiez que `FilePutObject` et `FileGetObject` font uniquement référence à des fichiers ouverts pour un accès `Random` ou `Binary`.  
  
-   Vérifiez que `Print` spécifie un fichier ouvert pour un mode d'accès `Output` ou `Append`.  Si ce n'est pas le cas, utilisez une instruction différente pour placer les données dans le fichier ou rouvrez le fichier dans un mode approprié.  
  
-   Vérifiez que `Input` spécifie un fichier ouvert pour un mode d'accès `Input`.  Si tel n'est pas le cas, utilisez une instruction différente pour placer les données dans le fichier ou rouvrez le fichier dans un mode approprié.  
  
-   Si vous écrivez dans un fichier en lecture seule, modifiez l'état de lecture\/écriture du fichier ou n'essayez pas d'écrire dans celui\-ci.  
  
-   Utilisez les fonctionnalités disponibles dans l'objet `My.Computer.FileSystem`.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileSystem>   
 [Troubleshooting: Reading from and Writing to Text Files](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)