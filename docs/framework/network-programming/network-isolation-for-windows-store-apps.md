---
title: "Isolement réseau pour les applications du Windows Store"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b6c0665a379f02a74bd0f3631aa26b41dd6ece5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="network-isolation-for-windows-store-apps"></a>Isolement réseau pour les applications du Windows Store
Les classes des espaces de noms <xref:System.Net>, <xref:System.Net.Http> et <xref:System.Net.Http.Headers> peuvent être utilisées pour développer des applications Windows Store et des applications de bureau. Lorsqu’elles sont utilisées dans une application du Windows Store, les classes de ces espaces de noms sont affectées par l’isolement réseau, qui fait partie du modèle de sécurité des applications utilisé par [!INCLUDE[win8](../../../includes/win8-md.md)]. Les fonctionnalités réseau appropriées doivent être activées dans le manifeste d’une application du Windows Store pour que le système autorise l’accès réseau.  
  
## <a name="checklist-for-network-isolation"></a>Liste de vérification pour l’isolement réseau  
 Utilisez cette liste de vérification pour vérifier que l’isolement réseau est configuré pour votre application du Windows Store.  
  
1.  Déterminez la direction des requêtes d’accès réseau dont a besoin l’application. Il peut s’agir de requêtes sortantes lancées par le client, de requêtes entrantes non sollicitées, ou d’une combinaison de ces deux types de requêtes réseau.  
  
2.  Déterminez le type de ressources réseau avec lesquelles l’application va communiquer. Une application peut avoir besoin de communiquer avec des ressources approuvées appartenant à un réseau domestique ou d’entreprise. Une application peut avoir besoin de communiquer avec des ressources Internet. Une application peut avoir besoin d’accéder à ces deux types de ressources réseau.  
  
3.  Configurez les fonctionnalités d’isolement réseau minimales dans le manifeste d’application.  
  
4.  Déployez et exécutez votre application pour la tester à l’aide des outils d’isolement réseau fournis pour la résolution des problèmes.  
  
 Pour plus d’informations sur la configuration des fonctionnalités réseau et des outils utilisés pour le dépannage de l’isolement réseau, consultez [Comment définir les fonctionnalités réseau (HTML)](http://go.microsoft.com/fwlink/?LinkID=228265) dans la documentation du développeur de [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion à un service web](http://go.microsoft.com/fwlink/?LinkID=245696)  
 [Instructions et liste de vérification pour l’isolement réseau](http://go.microsoft.com/fwlink/?LinkID=228265)  
 [Démarrage rapide : Connexion à l’aide de HttpClient](http://go.microsoft.com/fwlink/?LinkId=245697)  
 [L’utilisation des gestionnaires de HttpClient](http://go.microsoft.com/fwlink/?LinkId=245699)  
 [Comment sécuriser les connexions client HTTP](http://go.microsoft.com/fwlink/?LinkId=245698)  
 [Exemple HttpClient](http://go.microsoft.com/fwlink/?LinkId=242550)
