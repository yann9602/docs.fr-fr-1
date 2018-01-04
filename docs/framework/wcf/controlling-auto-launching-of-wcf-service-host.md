---
title: "Contrôle de l'auto-lancement de l'hôte de service WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65daceac9b865f3e8224c709d672344606905d9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>Contrôle de l'auto-lancement de l'hôte de service WCF
Vous pouvez contrôler la fonction d'auto-lancement de l'hôte du service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] (WcfSvcHost.exe) pour un projet de bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] lorsque vous déboguez un autre projet dans la même solution [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] contenant plusieurs projets.  
  
 Pour ce faire, cliquez sur le [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projet de Service dans **l’Explorateur de solutions**, choisissez **propriétés**, puis cliquez sur **Options WCF** onglet. Le **démarrer WCF Service hôte lors du débogage d’un autre projet dans la même solution** case à cocher est activée par défaut. Vous pouvez la désactiver afin que l'hôte du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] de ce projet spécifique ne démarre pas lorsqu'un autre projet est débogué dans la même solution.  
  
 Ce comportement n'affecte pas le débogage F5 ni les fonctionnalités d'ajout d'une référence de service pour ce projet.  
  
 Cette option est disponible dans le cadre des projets suivants :  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Projet de la bibliothèque du service  
  
-   Projet de la bibliothèque du service du workflow séquentiel  
  
-   Projet de la bibliothèque du service de workflow d'ordinateur d'état  
  
-   Projet de la bibliothèque du service de syndication  
  
## <a name="see-also"></a>Voir aussi  
 [WCF Service Host (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
