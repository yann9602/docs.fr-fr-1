---
title: "Impossible d’&#233;crire dans le fichier journal, car la quantit&#233; d’espace disque libre deviendrait alors inf&#233;rieure &#224; la valeur ReservedSpace | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrApplicationLog_ReservedSpaceEncroached"
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Impossible d’&#233;crire dans le fichier journal, car la quantit&#233; d’espace disque libre deviendrait alors inf&#233;rieure &#224; la valeur ReservedSpace
La classe <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> n’a pas pu écrire dans le fichier journal pour les raisons suivantes :  
  
-   La quantité d’espace disque libre \(en octets\) est inférieure à la valeur de la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>.  
  
     —et—  
  
-   La valeur de la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> est <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>.  
  
### Pour corriger cette erreur  
  
1.  Archivez les journaux existants et supprimez\-les de l’ordinateur pour permettre à l’objet <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> de créer des journaux.  
  
2.  Affectez à la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> une valeur inférieure pour réserver moins d’espace disque.  
  
3.  Affectez à la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> la valeur <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption> pour ignorer les messages indiquant une quantité d’espace disque libre insuffisante.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>   
 [My.Application.Log, objet](../../visual-basic/language-reference/objects/my-application-log-object.md)   
 [My.Log Object](../../visual-basic/language-reference/objects/my-log-object.md)