---
title: WCF et API Web ASP.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08ceded3-fd9a-4467-9715-c4cbd9c7228e
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e3d4d3677654934bc083ec14c97c65573a327146
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-and-aspnet-web-api"></a>WCF et API Web ASP.NET
WCF est le modèle de programmation unifié de Microsoft permettant de générer des applications orientées service. Il permet aux développeurs de générer des solutions transactionnelles sécurisées et fiables qui s'intègrent à plusieurs plateformes et interagissent avec les investissements existants. [ASP.NET Web API](http://www.asp.net/web-api) est une infrastructure qui permet de facilement créer des services HTTP qui atteignent un large éventail de clients, y compris les navigateurs et périphériques mobiles. L'API Web ASP.NET est une plate-forme idéale pour générer des applications RESTful sur le .NET Framework. Cette rubrique vous aider à déterminer quelle technologie est la plus adaptée vos besoins.  
  
## <a name="choosing-which-technology-to-use"></a>Choix de la technologie à utiliser  
 Le tableau suivant décrit les principales fonctionnalités de chaque technologie.  
  
|WCF|API Web ASP.NET|  
|---------|---------------------|  
|Active les services de génération qui prennent en charge plusieurs fournisseurs de transport (HTTP, TCP, UDP et transports personnalisés) et permet le basculement entre eux.|HTTP uniquement. Modèle de programmation de première classe pour le protocole HTTP. Plus adapté pour l’accès à partir de différents navigateurs, activation etc. large atteindre les appareils mobiles.|  
|Active les services de génération qui prennent en charge plusieurs encodages (texte, MTOM et binaire) du même type de message et permet la commutation entre eux.|Active les API Web de génération qui prennent en charge une large gamme de types de média y compris XML, JSON, etc.|  
|Prend en charge les services de génération avec les normes WS-*, tels que messagerie fiable, transactions et sécurité des messages.|Utilise le protocole et les formats de base, tels que HTTP, WebSockets, SSL, JQuery, JSON et XML. Il n'existe aucune prise en charge des protocoles de niveau supérieur, tels que Messagerie fiable ou Transactions.|  
|Prend en charge les modèles d’échange de messages duplex, demande-réponse et unidirectionnels.|HTTP est demande/réponse, mais des modèles supplémentaires peuvent être pris en charge via [SignalR](https://github.com/SignalR/SignalR) et l’intégration de WebSocket.|  
|Les services SOAP WCF peuvent être décrits en WSDL, ce qui permet aux outils automatisés de générer des proxys clients même pour les services ayant des schémas complexes.|Il existe plusieurs façons de décrire une API Web, allant d'une page HTML générée automatiquement décrivant les extraits de code aux métadonnées structurées pour les API intégrées OData.|  
|Fourni avec le .NET Framework.|Fourni avec le .NET framework, mais est open source et est également disponible hors band en tant que téléchargement indépendant.|  
  
 Utilisez WCF pour créer des services Web dignes de confiance et sécurisés accessibles via un large éventail de transports. Utilisez l'API Web ASP.NET pour créer des services HTTP qui sont accessibles à partir d'une large gamme de clients. Utilisez l'API Web ASP.NET si vous créez et concevez de nouveaux services REST. Bien que WCF prenne en charge l'écriture de services REST, la prise en charge de REST dans l'API Web ASP.NET est plus complète et toutes les futures améliorations des fonctionnalités REST seront apportées dans l'API Web ASP.NET. Si vous disposez d'un service WCF et souhaitez exposer des points de terminaison REST supplémentaires, utilisez WCF et <xref:System.ServiceModel.WebHttpBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [Concepts fondamentaux de Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)  
