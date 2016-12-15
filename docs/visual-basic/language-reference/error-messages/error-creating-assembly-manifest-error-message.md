---
title: "Error creating assembly manifest: &lt;error message&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30140"
  - "vbc30140"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30140"
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Error creating assembly manifest: &lt;error message&gt;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] appelle Assembly Linker \(Al.exe, également appelé Alink\) pour générer un assembly avec un manifeste. L'éditeur de liens a signalé une erreur dans la phase de préémission de création de l'assembly.  
  
 Cela peut être dû à des problèmes avec le fichier de clé ou le conteneur de clé indiqué. Pour signer un assembly, vous devez fournir un fichier de clé valide contenant des informations relatives aux clés publiques et privées. Pour retarder la signature d'un assembly, vous devez cocher la case **Différer la signature uniquement** et fournir un fichier de clé valide contenant des informations de clé publique. La clé privée n'est pas nécessaire quand la signature d'un assembly est différée. Pour plus d'informations, consultez [How to: Sign an Assembly \(Visual Studio\)](http://msdn.microsoft.com/fr-fr/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
 **ID d'erreur :** BC30140  
  
### Pour corriger cette erreur  
  
1.  Examinez le message d'erreur cité et consultez la rubrique [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/fr-fr/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) pour obtenir plus d'explications et de conseils sur l'erreur AL1019  
  
2.  Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.  
  
## Voir aussi  
 [How to: Sign an Assembly \(Visual Studio\)](http://msdn.microsoft.com/fr-fr/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [Page Signature, Concepteur de projets](/visual-studio/ide/reference/signing-page-project-designer)   
 [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)   
 [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/fr-fr/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)   
 [Nous contacter](/visual-studio/ide/talk-to-us)