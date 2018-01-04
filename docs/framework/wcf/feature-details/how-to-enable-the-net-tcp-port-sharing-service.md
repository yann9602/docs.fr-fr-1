---
title: "Comment : activer le service de partage de ports Net.TCP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9f1c57f067fa7c8bece3acaf0d51303b31d13bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>Comment : activer le service de partage de ports Net.TCP
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utilise un service Windows appelé Service de partage de ports Net.TCP pour faciliter le partage des ports TCP à travers des processus multiples. Ce service est installé dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], mais n'est pas activé par défaut par mesure de sécurité et doit être activé manuellement avant la première utilisation. Cette rubrique décrit comment configurer le service de partage de ports Net.TCP à l'aide du composant logiciel enfichable Microsoft Management Console (MMC).  
  
 Après avoir activé le Service de partage de ports Net.TCP et que vous démarrez manuellement, consultez [Comment : configurer un Service WCF à utiliser le partage de Port](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) pour plus d’informations sur la façon de configurer votre service pour utiliser ce service.  
  
 Pour voir un exemple qui utilise le partage de ports net.tcp://, le [Net.TCP Port Sharing, exemple](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>Pour activer le service de partage de ports Net.TCP à l'aide de MMC  
  
1.  Dans le menu Démarrer, ouvrez la Console de gestion de Services soit en ouvrant une fenêtre d’invite de commandes et en tapant `services.msc` ou en sélectionnant exécuter et en tapant `services.msc` dans la zone Ouvrir.  
  
2.  Dans le **nom** avec le bouton droit de la colonne de la liste des services, le **Service de partage de Port Net.Tcp**, puis sélectionnez **propriétés** à partir du menu.  
  
3.  Pour permettre le démarrage manuel du service, dans le **propriétés** fenêtre Sélectionner le **général** onglet et dans le **type de démarrage** zone Sélectionnez manuel, puis cliquez sur **Appliquer**.  
  
4.  Pour démarrer le service, dans la zone d’état de Service, cliquez sur le **Démarrer** bouton. L'état du service doit maintenant afficher "Démarré".  
  
5.  Pour revenir à la liste des services, cliquez sur le **OK**, quittez la Console MMC.  
  
## <a name="example"></a>Exemple  
  
## <a name="see-also"></a>Voir aussi  
 [Partage de ports Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [Configuration du service de partage de ports Net.TCP](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
