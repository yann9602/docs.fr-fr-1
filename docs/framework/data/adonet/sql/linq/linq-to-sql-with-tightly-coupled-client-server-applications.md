---
title: "LINQ to SQL avec des applications client-serveur fortement couplés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e083d805-dcf6-459d-b9af-9ef0563f2dd7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a2fa902cfbea3c6eb15e1832231bb3ed83de5497
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="linq-to-sql-with-tightly-coupled-client-server-applications"></a>LINQ to SQL avec des applications client-serveur fortement couplés
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]peut être utilisé sur la couche intermédiaire avec des Clients intelligents fortement couplés sur la couche de présentation. Dans les scénarios qui impliquent l'accès aux données en lecture seule, aucun contrôle d'accès concurrentiel ni accès concurrentiel optimiste avec horodatages, la complexité n'est guère supérieure à celle des scénarios sans accès à distance. Toutefois, lorsqu'une base de données requiert des contrôles d'accès concurrentiel optimiste avec les valeurs d'origine, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne fournit pas le niveau de prise en charge pour l'aller-retour (round-trip) de données que vous trouvez dans DataSets. Toutefois, une couche intermédiaire [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] peut échanger des données avec les clients sur toutes les plateformes.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]dans [!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)] ne fournit aucune infrastructure de suivi de l’état de l’entité après qu’ils ont été sérialisés à un client. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Active des architectures orientées service où les interactions entre les couches données et présentation sont faibles et relativement atomiques, mais n’effectue aucun aller-retour des valeurs d’origine. Par conséquent, si vous souhaitez utiliser un client intelligent fortement couplé avec [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et qu'une base de données utilise l'accès concurrentiel optimiste avec les valeurs d'origine, vous devrez implémenter votre propre mécanisme pour communiquer les modifications entre la couche présentation et la couche intermédiaire. Il incombe au concepteur de systèmes de décider s'il convient de consentir ce petit effort supplémentaire en échange des avantages fournis par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sur la couche intermédiaire. En revanche, si la base de données comporte des horodatages, il n'est pas nécessaire de disposer d'une logique de suivi des modifications personnalisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications multicouches et distantes avec LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [Applications multicouches LINQ to SQL avec les services web](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
 [Utilisation de datasets dans des applications multiniveaux](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20)
