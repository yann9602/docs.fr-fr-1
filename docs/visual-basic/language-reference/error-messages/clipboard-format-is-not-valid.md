---
title: "Clipboard format is not valid | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID460"
dev_langs: 
  - "VB"
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Clipboard format is not valid
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Le format de Presse\-papiers spécifié est incompatible avec la méthode exécutée.  Cette erreur peut se produire pour de nombreuses raisons.  
  
-   utilisation de la méthode `GetText` ou `SetText` du Presse\-papiers avec un format de Presse\-papiers autre que `vbCFText` ou `vbCFLink` ;  
  
-   utilisation de la méthode `GetData` ou `SetData` du Presse\-papiers avec un format de Presse\-papiers autre que `vbCFBitmap`, `vbCFDIB` ou `vbCFMetafile` ;  
  
-   utilisation de la méthode `DataObject` `GetData` ou `SetData` avec un format de Presse\-papiers compris dans la plage réservée par Microsoft Windows pour les formats enregistrés \(&HC000\-&HFFFF\), mais ce format de Presse\-papiers n'a pas été enregistré par Microsoft Windows.  
  
### Pour corriger cette erreur  
  
-   Supprimez le format non valide et spécifiez un format valide.  
  
## Voir aussi  
 [Presse\-papiers : ajout d'autres formats](../Topic/Clipboard:%20Adding%20Other%20Formats.md)