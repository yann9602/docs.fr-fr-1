---
title: "Présentation de Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7aecddc617afcaf197aa212e8eea7e1342c029fa
ms.sourcegitcommit: 08684dd61444c2f072b89b926370f750e456fca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="what-is-windows-communication-foundation"></a>Présentation de Windows Communication Foundation
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] est une infrastructure pour la création d’applications orientées service. Avec [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], vous pouvez envoyer des données sous forme de messages asynchrones d'un point de terminaison de service à un autre. Un point de terminaison de service peut faire partie d'un service disponible en continu et hébergé par IIS, ou il peut s'agir d'un service hébergé dans une application. Un point de terminaison peut être un client d'un service qui demande des données auprès d'un point de terminaison de service. Les messages peuvent être simplement constitués d'un caractère ou d'un mot unique envoyé au format XML, ou se présenter sous la forme d'un flux de données binaires plus complexe. Voici quelques exemples de scénarios :  
  
-   Service sécurisé pour traiter des transactions commerciales.  
  
-   Service qui fournit des données actuelles à d'autres services, comme un rapport sur le trafic ou tout autre service de surveillance.  
  
-   Service de conversation qui permet à deux personnes de communiquer ou d'échanger des données en temps réel.  
  
-   Application de tableau de bord qui interroge les données d'un ou de plusieurs services et les présente de manière logique.  
  
-   Exposition d'un workflow implémenté à l'aide de Windows Workflow Foundation en tant que service WCF.  
  
-   Application Silverlight pour interroger un service afin d'obtenir les flux de données les plus récents.  
  
 Si la création de telles applications était possible avant [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] simplifie le développement de points de terminaison comme jamais auparavant. En résumé, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est conçu de manière à offrir une approche gérable à la création de services Web et de clients de services Web.  
  
## <a name="features-of-wcf"></a>Fonctions de WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] inclut l’ensemble de fonctionnalités suivant. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [WCF Feature Details](../../../docs/framework/wcf/feature-details/index.md).  
  
-   **Orientation services**  
  
     L'une des conséquences de l'utilisation de normes WS est que [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] vous permet de créer des applications *orientées services* . L'architecture orientée services (SOA, Service-Oriented Architecture) dépend de services Web pour envoyer et recevoir des données. Les services présentent l'avantage d'être faiblement couplés, au lieu d'être encodés de manière irréversible d'une application à une autre. Une relation faiblement couplée implique que tout client créé sur une plate-forme peut se connecter à n'importe quel service, dans la mesure où les contrats essentiels sont respectés.  
  
-   **Interopérabilité**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] implémente les normes industrielles modernes pour l’interopérabilité des services Web. [!INCLUDE[crabout](../../../includes/crabout-md.md)] les standards pris en charge, consultez [Interoperability and Integration](../../../docs/framework/wcf/feature-details/interoperability-and-integration.md).  
  
-   **Modèles de messages variés**  
  
     Les messages sont échangés selon l'un des différents modèles disponibles. Le modèle le plus courant est de type demande/réponse, dans lequel un point de terminaison demande des données auprès d'un second point de terminaison. Le second point de terminaison répond. Il existe d'autres modèles, comme un message unidirectionnel dans lequel un seul point de terminaison envoie un message sans attendre de réponse. Le modèle d'échange en duplex constitue un modèle plus complexe dans la mesure où deux points de terminaison établissent une connexion et envoient des données de part et d'autre, à la manière d'un programme de messagerie instantanée. [!INCLUDE[crabout](../../../includes/crabout-md.md)] l’implémentation de différents modèles d’échange de messages à l’aide de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] , consultez [Contracts](../../../docs/framework/wcf/feature-details/contracts.md).  
  
-   **Métadonnées de service**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] prend en charge la publication des métadonnées de service à l’aide de formats spécifiés dans les normes industrielles telles que WSDL, schéma XML et WS-Policy. Ces métadonnées peuvent être utilisées pour générer et configurer automatiquement des clients en vue de l'accès à des services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] . Les métadonnées peuvent être publiées via HTTP et HTTPS ou à l'aide de la norme d'échange de métadonnées de service Web. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Metadata](../../../docs/framework/wcf/feature-details/metadata.md).  
  
-   **Contrats de données**  
  
     Étant donné que [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] repose sur [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], il offre également des méthodes faciles à coder pour fournir les contrats que vous souhaitez appliquer. Le contrat de données représente l'un des types universels de contrats. Par nature, lorsque vous codez votre service à l'aide de Visual C# ou de Visual Basic, la méthode la plus simple de gérer les données consiste à créer des classes qui représentent une entité de données dotée de propriétés. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] inclut un système complet permettant d'utiliser les données aisément grâce à cette méthode. Une fois que vous avez créé les classes qui représentent les données, votre service génère automatiquement les métadonnées qui permettent aux clients de se conformer aux types de données que vous avez conçus. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Using Data Contracts](../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
  
-   **Sécurité**  
  
     Les messages peuvent être chiffrés afin de protéger la confidentialité. Par ailleurs, vous pouvez demander aux utilisateurs de s'authentifier avant de pouvoir recevoir des messages. La sécurité peut être implémentée à l'aide de normes célèbres, telles que SSL ou WS-SecureConversation. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Sécurité](../../../docs/framework/wcf/feature-details/security.md).  
  
-   **Transports et encodages variés**  
  
     Les messages peuvent être envoyés via l'un des différents encodages et protocoles de transport intégrés. Le protocole et encodage le plus courant consiste à envoyer des messages SOAP à encodage texte avec le protocole HTTP (HyperText Transfer Protocol) en vue d'une utilisation sur Internet. Sinon, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] vous permet d'envoyer des messages via TCP, des canaux nommés ou MSMQ. Ces messages peuvent être encodés en tant que texte ou à l'aide d'un format binaire optimisé.  Les données binaires peuvent être envoyées efficacement à l'aide de la norme MTOM. Si aucun des transports ou encodages fournis ne convient à vos besoins, vous avez la possibilité de créer votre propre encodage ou transport personnalisé. [!INCLUDE[crabout](../../../includes/crabout-md.md)] transports et encodages pris en charge par [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] consultez [Transports](../../../docs/framework/wcf/feature-details/transports.md).  
  
-   **Messages fiables et mis en file d'attente**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] prend en charge l’échange de messages fiables à l’aide de sessions fiables implémentées via WS-Reliable Messaging et MSMQ. [!INCLUDE[crabout](../../../includes/crabout-md.md)] la prise en charge de la messagerie mise en file d’attente et fiable dans [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] , consultez [Queues and Reliable Sessions](../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).  
  
-   **Messages durables**  
  
     Un message durable est un message qui n'est jamais perdu suite à une interruption de la communication. Les messages conformes au modèle de message durable sont toujours enregistrés dans une base de données. En cas d'interruption, la base de données vous permet de reprendre l'échange de messages une fois la connexion restaurée. Vous pouvez également créer un message durable à l'aide de [!INCLUDE[wf](../../../includes/wf-md.md)]. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Workflow Services](../../../docs/framework/wcf/feature-details/workflow-services.md).  
  
-   **Transactions**  
  
     WCF prend également en charge les transactions à l'aide de trois modèles de transaction : WS-AtomicTtransactions, les interfaces API dans l'espace de noms <xref:System.Transactions> et MSDTC (Microsoft Distributed Transaction Coordinator). [!INCLUDE[crabout](../../../includes/crabout-md.md)] la prise en charge des transactions dans [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] , consultez [Transactions](../../../docs/framework/wcf/feature-details/transactions-in-wcf.md).  
  
-   **Prise en charge d'AJAX et de REST**  
  
     REST est un exemple d'une technologie évoluant vers le Web 2.0. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] peut être configuré pour traiter des données XML « ordinaires » qui ne sont pas encapsulées dans une enveloppe SOAP. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] peut être étendu pour prendre en charge des formats XML spécifiques, tels qu'ATOM (une norme populaire RSS), et même des formats non XML, tels que JSON (JavaScript Object Notation).  
  
-   **Extensibilité**  
  
     L'architecture [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] comporte un certain nombre de points d'extensibilité. Si une capacité supplémentaire est requise, il existe un certain nombre de points d'entrée qui vous permettent de personnaliser le comportement d'un service. [!INCLUDE[crabout](../../../includes/crabout-md.md)] les points d’extensibilité disponibles, consultez [extension de WCF](../../../docs/framework/wcf/extending/index.md).  
  
## <a name="wcf-integration-with-other-microsoft-technologies"></a>Intégration WCF avec d'autres technologies Microsoft  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est une plate-forme flexible. Grâce à son extrême flexibilité, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est également utilisé dans plusieurs autres produits Microsoft. Si vous maîtrisez les bases de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], vous bénéficiez d'un avantage immédiat lorsque vous utilisez également l'un de ces produits.  
  
 La première technologie associée à [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] a été Windows Workflow Foundation (WF). Les workflows simplifient le développement d’applications en encapsulant les étapes dans le flux de travail en tant que « activités ». Dans la première version de [!INCLUDE[wf2](../../../includes/wf2-md.md)], un développeur devait créer un hôte pour le workflow. La version suivante de [!INCLUDE[wf2](../../../includes/wf2-md.md)] a été intégrée à [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Cela a permis d'héberger facilement tout workflow dans un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ; cette opération peut s'effectuer automatiquement en choisissant WF/WCF comme type de projet dans [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
 Microsoft BizTalk Server R2 utilise également [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] comme technologie de communication. BizTalk a été conçu pour recevoir et transformer des données d'un format standardisé en un autre. Les messages doivent être remis dans leur boîte de message centrale, où ils peuvent être transformés suivant un mappage strict ou à l'aide de l'une des fonctionnalités BizTalk, telles que le moteur de workflow. BizTalk peut désormais utiliser l'adaptateur LOB (Line of Business) de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pour remettre les messages à la boîte de message.  
  
 Microsoft Silverlight est une plate-forme de création d'applications Web enrichies interopérables qui permettent aux développeurs de créer des sites Web comportant de nombreux médias (tels que la vidéo en continu). Depuis la version 2, Silverlight a intégré [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] en tant que technologie de communication afin de connecter les applications Silverlight aux points de terminaison [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] .  
  
 Le serveur d'applications [!INCLUDE[dublin](../../../includes/dublin-md.md)] est conçu spécifiquement pour le déploiement et la gestion d'applications qui utilisent [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pour la communication. [!INCLUDE[dublin2](../../../includes/dublin2-md.md)] propose des options de configuration et d'outillage enrichies, conçues spécifiquement pour les applications compatibles avec [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel>  
 [Concepts fondamentaux de Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)  
 [Architecture Windows Communication Foundation](../../../docs/framework/wcf/architecture.md)  
 [Conseils et bonnes pratiques](../../../docs/framework/wcf/guidelines-and-best-practices.md)  
 [Didacticiel Bien démarrer](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Guide de la documentation](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [Programmation WCF de base](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Exemples Windows Communication Foundation](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)
