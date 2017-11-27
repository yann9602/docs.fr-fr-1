---
title: Contrats
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], contracts
- contracts [WCF]
- Windows Communication Foundation [WCF], contracts
ms.assetid: c8364183-4ac1-480b-804a-c5e6c59a5d7d
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 60835e9d85412aa07958273daa5d9b7a24cfbfeb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="contracts"></a>Contrats
Cette section vous montre comment définir et implémenter des contrats [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Un contrat de service spécifie ce qu'un point de terminaison communique au monde extérieur. À un niveau plus concret, il s'agit d'une instruction à propos d'un ensemble de messages spécifiques organisé en modèles d'échange de messages de base, tels que les messages demande/réponse, unidirectionnels et duplex. Si un contrat de service est un ensemble d'échanges de messages liés de manière logique, une opération de service est un échange de messages unique. Par exemple, une opération `Hello` doit évidemment accepter un message (de sorte que l'appelant puisse annoncer la salutation) et peut ou non retourner un message (en fonction du niveau de courtoisie de l'opération).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]contrats et autres principaux [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] les concepts, consultez [Concepts fondamentaux Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md). Cette rubrique est consacrée au fonctionnement des contrats de service. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]les contrats de la génération de clients qui utilisent le service pour se connecter aux services, consultez [vue d’ensemble du Client WCF](../../../../docs/framework/wcf/wcf-client-overview.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]les canaux clients, l’architecture du client et autres problèmes de client, consultez [Clients](../../../../docs/framework/wcf/feature-details/clients.md).  
  
## <a name="overview"></a>Vue d'ensemble  
 Cette rubrique fournit une orientation conceptuelle de niveau supérieur de la conception et de l'implémentation de services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Les sous-rubriques fournissent des informations plus détaillées sur les aspects spécifiques à la conception et à l'implémentation. Avant de concevoir et d'implémenter votre application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vous devez :  
  
-   comprendre ce qu'est un contrat de service, comment il fonctionne et comment en créer un ;  
  
-   comprendre que les contrats définissent des impératifs minimaux que la configuration à l'exécution ou l'environnement d'hébergement peuvent ne pas prendre en charge.  
  
## <a name="service-contracts"></a>Contrats de service  
 Un contrat de service est une instruction qui fournit des informations sur :  
  
-   le groupement d'opérations dans un service ;  
  
-   la signature des opérations en termes de messages échangés ;  
  
-   les types de données de ces messages ;  
  
-   l'emplacement des opérations ;  
  
-   les protocoles et formats de sérialisation spécifiques utilisés pour prendre en charge la communication avec le service.  
  
 Par exemple, un contrat de commande fournisseur peut avoir une opération `CreateOrder` qui accepte une entrée de types d'informations de commande et retourne des information de succès ou d'échec, y compris un identificateur de commande. Il peut également avoir une opération `GetOrderStatus` qui accepte un identificateur de commande et retourne des informations d'état de commande. Un tel contrat de service spécifie alors :  
  
-   que le contrat de commande fournisseur serait composé d'opérations `CreateOrder` et `GetOrderStatus` ;  
  
-   que les opérations auraient des messages d'entrée et des messages de sortie spécifiés ;  
  
-   les données que ces messages pourraient transporter ;  
  
-   des instructions catégoriques à propos de l'infrastructure de communication nécessaire pour traiter les messages avec succès. Par exemple, ces détails incluent les éventuelles formes de sécurité requises pour établir la communication.  
  
 Pour transmettre ce type d’informations pour les applications sur d’autres plateformes (y compris des plateformes non-Microsoft), les contrats de service XML sont publiquement exprimés dans des formats XML standards, par exemple [Web Services Description Language (WSDL)](http://go.microsoft.com/fwlink/?LinkId=87004) et [XSD (XML Schema)](http://go.microsoft.com/fwlink/?LinkId=87005), entre autres. Les développeurs qui travaillent avec un grand nombre de plateformes différentes peuvent utiliser ces informations de contrat publiques pour créer des applications capables de communiquer avec le service, ces applications comprenant le langage des spécifications, d'une part, et ce langage assurant l'interopérabilité grâce à sa description de formes, formats et protocoles publics pris en charge par ce service, d'autre part. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Comment [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] descripteurs de ce type d’informations, consultez [métadonnées](../../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Les contrats peuvent toutefois être exprimés de nombreuses manières, et bien que WSDL et XSD constituent d'excellents langages pour décrire des services d'une manière accessible, ce sont des langages difficiles à utiliser directement ; en tous les cas, ils constituent simplement des descriptions d'un service, et non des implémentations de contrat de service. Par conséquent, les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilisent des attributs, des interfaces et des classes managés à la fois pour définir la structure et pour implémenter un service.  
  
 Le contrat résultant défini dans les types managés peut être converti (également appelé *exporté*) en tant que métadonnées, WSDL et XSD, si nécessaire par les clients ou d’autres implémenteurs de service, en particulier sur d’autres plateformes. Le résultat est un modèle de programmation simple qui peut être décrit à l'aide de métadonnées publiques à toute application cliente. Les détails des messages SOAP sous-jacents, tels que les informations de transport et relatives à la sécurité, peuvent être laissés à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], qui exécute automatiquement les conversions nécessaires entre le système de type de contrat de service et le système de type XML.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]contrats de conception, consultez [concevoir des contrats de Service](../../../../docs/framework/wcf/designing-service-contracts.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]l’implémentation de contrats, voir [implémentation de contrats de Service](../../../../docs/framework/wcf/implementing-service-contracts.md).  
  
 En outre, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] permet également de développer des contrats de service complètement au niveau du message. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]développement des contrats de service au niveau du message, consultez [à l’aide de contrats de Message](../../../../docs/framework/wcf/feature-details/using-message-contracts.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]services de développement dans non - SOAP XML, consultez [l’interopérabilité avec les Applications POX](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Présentation de la hiérarchie des exigences  
 Un contrat de service groupe les opérations, spécifie les modèles d'échange de messages, les types de messages et les types de données que ces messages transportent, et indique les catégories de comportement à l'exécution qu'une implémentation doit avoir pour prendre en charge le contrat (par exemple, il peut exiger que les messages soient chiffrés et signés). Toutefois, le contrat de service lui-même ne spécifie pas précisément comment ces spécifications sont satisfaites, mais uniquement qu'elles doivent l'être. Le type de chiffrement utilisé ou la façon dont un message est signé incombe à l'implémentation et à la configuration d'un service conforme.  
  
 Remarquez la façon dont le contrat requiert certaines choses de l'implémentation de contrat de service et de la configuration à l'exécution pour ajouter un comportement. L'ensemble de spécifications qui doivent être satisfaites pour exposer un service pour une utilisation repose sur l'ensemble de spécifications précédent. Si un contrat spécifie des exigences concernant l'implémentation, une implémentation peut requérir une plus grande partie de la configuration et des liaisons qui autorisent l'exécution du service. Pour finir, l'application hôte doit également prendre en charge les spécifications ajoutées par la configuration du service et les liaisons.  
  
 Il convient de prendre en compte ce processus de spécification additif lors de la conception, de l'implémentation, de la configuration et de l'hébergement de votre application de service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Par exemple, le contrat peut spécifier qu'il doit prendre en charge une session. Dans ce cas, vous devez configurer la liaison de façon à prendre en charge cette spécification contractuelle, sinon l'implémentation de service ne fonctionnera pas. Si votre service requiert l'authentification intégrée de Windows et qu'il est hébergé par les services IIS, l'option Authentification intégrée de Windows de l'application Web dans laquelle se trouve le service doit être activée et l'option de prise en charge anonyme doit être désactivée. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]les fonctionnalités et l’impact des types d’application hôte de service différent, consultez [hébergement](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Points de terminaison : Adresses, liaisons et contrats](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Conception de contrats de service](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [Implémentation de contrats de service](../../../../docs/framework/wcf/implementing-service-contracts.md)
