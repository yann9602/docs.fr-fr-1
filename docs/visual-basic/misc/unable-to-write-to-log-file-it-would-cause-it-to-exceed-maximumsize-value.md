---
title: "Impossible d’&#233;crire dans le fichier journal, car cette op&#233;ration entra&#238;nerait un d&#233;passement de la valeur MaximumSize | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrApplicationLog_FileExceedsMaximumSize"
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’&#233;crire dans le fichier journal, car cette op&#233;ration entra&#238;nerait un d&#233;passement de la valeur MaximumSize
La classe <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> n’a pas pu écrire dans le fichier journal pour les raisons suivantes :  
  
-   La taille du fichier journal \(en octets\) est supérieure à la valeur de la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>  
  
     —et—  
  
-   La valeur de la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> est <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>.  
  
### Pour corriger cette erreur  
  
1.  Archivez les journaux existants et supprimez\-les de l’ordinateur pour permettre à l’objet <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> de créer des journaux.  
  
2.  Modifiez la valeur de la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> pour autoriser des tailles de journaux plus élevées.  
  
3.  Affectez la valeur <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption> à la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> pour ignorer les messages sans avertissement si le journal est trop volumineux.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>   
 [My.Application.Log, objet](../../visual-basic/language-reference/objects/my-application-log-object.md)   
 [My.Log Object](../../visual-basic/language-reference/objects/my-log-object.md)