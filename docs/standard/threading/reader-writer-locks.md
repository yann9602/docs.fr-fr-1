---
title: "Reader-Writer Locks | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ReaderWriterLock class, about ReaderWriterLock class"
  - "threading [.NET Framework], ReaderWriterLock class"
ms.assetid: 8c71acf2-2c18-4f4d-8cdb-0728639265fd
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Reader-Writer Locks
La classe <xref:System.Threading.ReaderWriterLockSlim> permet à plusieurs threads de lire une ressource simultanément, mais nécessite qu'un thread attende un verrou exclusif afin d'écrire dans la ressource.  
  
 Dans votre application, vous pouvez utiliser un <xref:System.Threading.ReaderWriterLockSlim> pour fournir une synchronisation coopérative parmi les threads qui accèdent à une ressource partagée.  Les verrous sont pris sur le <xref:System.Threading.ReaderWriterLockSlim> lui\-même.  
  
 Comme avec tout mécanisme de synchronisation de threads, vous devez veiller à ce qu'aucun thread n'ignore le verrouillage fourni par <xref:System.Threading.ReaderWriterLockSlim>.  Une façon de garantir cela est de créer une classe qui encapsule la ressource partagée.  Cette classe fournirait des membres qui accèdent à la ressource partagée privée et qui utilisent un <xref:System.Threading.ReaderWriterLockSlim> privé pour la synchronisation.  Consultez l'exemple de code indiqué pour la classe <xref:System.Threading.ReaderWriterLockSlim>.  <xref:System.Threading.ReaderWriterLockSlim> est assez efficace pour être utilisé pour synchroniser des objets individuels.  
  
 Structurez votre application pour minimiser la durée des opérations de lecture et d'écriture.  Les longues opérations d'écriture affectent le débit directement car le verrouillage en écriture est exclusif.  Les longues opérations de lecture bloquent les writers en attente et, si au moins un thread est en attente d'accès en écriture, les threads qui demandent l'accès en lecture seront également bloqués.  
  
> [!NOTE]
>  Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] a deux verrous de writer de lecteur, <xref:System.Threading.ReaderWriterLockSlim>et <xref:System.Threading.ReaderWriterLock>.  <xref:System.Threading.ReaderWriterLockSlim> est  recommandé pout tout nouveau développement.  <xref:System.Threading.ReaderWriterLockSlim> est semblable à <xref:System.Threading.ReaderWriterLock>, mais les règles de récurrence et de mise à niveau et rétrogradation de l'état de verrou sont simplifiées.  <xref:System.Threading.ReaderWriterLockSlim> évite de nombreux cas d'interblocage potentiel.  De plus, la performance de <xref:System.Threading.ReaderWriterLockSlim> est considérablement meilleure que <xref:System.Threading.ReaderWriterLock>.  
  
## Voir aussi  
 <xref:System.Threading.ReaderWriterLockSlim>   
 <xref:System.Threading.ReaderWriterLock>   
 [Threading](../../../docs/standard/threading/index.md)   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)