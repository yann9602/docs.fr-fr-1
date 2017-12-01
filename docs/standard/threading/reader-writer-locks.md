---
title: Verrous de lecteur-writer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ReaderWriterLock class, about ReaderWriterLock class
- threading [.NET Framework], ReaderWriterLock class
ms.assetid: 8c71acf2-2c18-4f4d-8cdb-0728639265fd
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df06e83165906199774f99de4140ace9b7396cbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="reader-writer-locks"></a>Verrous de lecteur-writer
La <xref:System.Threading.ReaderWriterLockSlim> classe permet à plusieurs threads de lire une ressource simultanément, mais nécessite qu’un thread d’attendre un verrou exclusif afin d’écrire dans la ressource.  
  
 Vous pouvez utiliser un <xref:System.Threading.ReaderWriterLockSlim> dans votre application pour fournir une synchronisation coopérative parmi les threads qui accèdent à une ressource partagée. Les verrous sont effectuées sur le <xref:System.Threading.ReaderWriterLockSlim> lui-même.  
  
 Comme avec tout mécanisme de synchronisation de threads, vous devez vous assurer qu’aucun thread ignore le verrouillage fourni par <xref:System.Threading.ReaderWriterLockSlim>. Un pour s’en assurer consiste à concevoir une classe qui encapsule la ressource partagée. Cette classe fournirait des membres qui accèdent à la ressource partagée privée et qui utilisent une privée <xref:System.Threading.ReaderWriterLockSlim> pour la synchronisation. Pour obtenir un exemple, consultez l’exemple de code pour la <xref:System.Threading.ReaderWriterLockSlim> classe. <xref:System.Threading.ReaderWriterLockSlim>est suffisamment efficace pour être utilisé pour synchroniser des objets individuels.  
  
 Structurer votre application pour réduire la durée de lecture et d’opérations d’écriture. Longues opérations d’écriture affectent le débit directement car le verrou en écriture est exclusif. Long writers en attente de bloquer les opérations de lecture, et si au moins un thread est en attente pour un accès en écriture, les threads qui demandent l’accès en lecture seront également bloqués.  
  
> [!NOTE]
>  Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] a deux verrous de lecteur-writer, <xref:System.Threading.ReaderWriterLockSlim> et <xref:System.Threading.ReaderWriterLock>. <xref:System.Threading.ReaderWriterLockSlim>est recommandée pour tout nouveau développement. <xref:System.Threading.ReaderWriterLockSlim>est semblable à <xref:System.Threading.ReaderWriterLock>, mais les règles de récurrence et de mise à niveau et la rétrogradation de l’état de verrou sont simplifiées. <xref:System.Threading.ReaderWriterLockSlim>évite de nombreux cas d’interblocage potentiel. En outre, les performances de <xref:System.Threading.ReaderWriterLockSlim> est considérablement plus performants que <xref:System.Threading.ReaderWriterLock>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.ReaderWriterLockSlim>  
 <xref:System.Threading.ReaderWriterLock>  
 [Thread](../../../docs/standard/threading/index.md)  
 [Fonctionnalités et objets de threading](../../../docs/standard/threading/threading-objects-and-features.md)
