---
title: "Compteurs de performance de service | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Compteurs de performance de service
Les compteurs de performance de service mesurent le comportement du service dans son ensemble et peuvent être utilisés pour diagnostiquer la performance du service entier.Ils se trouvent sous l'objet de performance `ServiceModelService 4.0.0.0` dans l'affichage de l'analyseur de performances \(Perfmon.exe\).Les instances sont nommées à l'aide du modèle suivant :  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  La longueur du nom d'une instance de compteur de performance est limitée.Lorsqu'un nom d'instance de compteur [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] dépasse la longueur maximale, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] remplace une partie du nom par une valeur de hachage.  
  
## Voir aussi  
 [Compteurs de performance](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)