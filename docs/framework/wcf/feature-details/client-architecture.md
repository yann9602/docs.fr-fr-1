---
title: "Architecture du client | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 02624403-0d77-41cb-9a86-ab55e98c7966
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Architecture du client
Les applications utilisent des objets de client [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour appeler des opérations de service.Cette rubrique contient des informations sur les objets de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], les canaux de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et leurs relations par rapport à l'architecture de canal sous\-jacente.Pour une vue d'ensemble de base des objets clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [Vue d'ensemble d'un client WCF](../../../../docs/framework/wcf/wcf-client-overview.md).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] la couche du canal, consultez [Extension de la couche du canal](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## Vue d'ensemble  
 L'exécution de modèle de service crée des clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui se composent des éléments suivants :  
  
-   Implémentation de client générée automatiquement d'un contrat de service qui transforme les appels de votre code d'application en messages sortants, les messages de réponse en paramètres de sortie et retourne des valeurs pouvant être récupérées par votre application.  
  
-   Implémentation d'une interface de contrôle \(<xref:System.ServiceModel.IClientChannel?displayProperty=fullName>\) qui regroupe différentes interfaces et fournit l'accès au contrôle des fonctionnalités, plus précisément aux fonctionnalités permettant de fermer la session client et de déployer le canal.  
  
-   Canal de client construit en fonction des paramètres de configuration spécifiés par la liaison utilisée.  
  
 Les applications peuvent créer de tels clients à la demande, via une fabrication <xref:System.ServiceModel.ChannelFactory?displayProperty=fullName> ou en créant une instance d'une classe dérivée <xref:System.ServiceModel.ClientBase%601> celle\-ci étant générée par l'outil [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).Ces classes de client déjà construites encapsulent une implémentation de canal de client construite dynamiquement par un <xref:System.ServiceModel.ChannelFactory> et délèguent vers cette implémentation.Par conséquent, cette rubrique traite principalement des canaux de client et de la fabrication de canal à leur origine.  
  
## Objets et canaux de client  
 L'interface de base des clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] correspond à l'interface <xref:System.ServiceModel.IClientChannel?displayProperty=fullName> qui expose la fonctionnalité principale de client, la fonctionnalité d'objet de communication de base de <xref:System.ServiceModel.ICommunicationObject?displayProperty=fullName>, la fonctionnalité de contexte de <xref:System.ServiceModel.IContextChannel?displayProperty=fullName> et le comportement extensible de <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=fullName>.  
  
 Toutefois, l'interface <xref:System.ServiceModel.IClientChannel> ne définit pas de contrat de service.Ces contrats sont déclarés par l'interface de contrat de service \(générée en principe à partir des métadonnées de service à l'aide d'un outil tel que [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)\).Les types de clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] étendent <xref:System.ServiceModel.IClientChannel> et l'interface cible du contrat de service pour permettre aux applications d'appeler des opérations directement et d'avoir également accès à la fonctionnalité runtime côté client.La création d'un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit des objets [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.ServiceModel.ChannelFactory?displayProperty=fullName> et les informations nécessaires pour créer un processus d'exécution pouvant se connecter au point de terminaison de service configuré et interagir avec ce dernier.  
  
 Comme mentionné précédemment, les deux types de clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] doivent être configurés pour pouvoir être utilisés.Le type de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] le plus simple correspond à un ensemble d'objets qui dérivent de <xref:System.ServiceModel.ClientBase%601> \(ou de <xref:System.ServiceModel.DuplexClientBase%601> si le contrat de service est un contrat duplex\).Vous pouvez créer ces types en utilisant un constructeur \(ou un fichier de configuration\) configuré par un programme, puis appelé directement pour appeler les opérations de service.Pour une vue d'ensemble de base des objets <xref:System.ServiceModel.ClientBase%601>, consultez [Vue d'ensemble d'un client WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
 Le second type est généré pendant l'exécution depuis un appel de la méthode <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>.Les applications pour lesquelles le contrôle stricte des spécifications de communication est important utilisent en général ce type de client et appellent un *objet de canal de client*, ce dernier leur permettant d'interagir plus directement que le système de canal et d'exécution de client sous\-jacent.  
  
## Fabrication de canal  
 La classe qui est chargée de créer le processus d'exécution sous\-jacent prenant en charge les appels de client correspond à <xref:System.ServiceModel.ChannelFactory%601?displayProperty=fullName>.Les objets de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et les objets de canal de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilisent un objet <xref:System.ServiceModel.ChannelFactory%601> pour créer des instances. L'objet de client dérivé <xref:System.ServiceModel.ClientBase%601> encapsule la gestion de la fabrication de canal. Dans certaines situations, il est tout à fait possible cependant d'utiliser directement la fabrication de canal.Vous souhaiterez le plus souvent créer à plusieurs reprises de nouveaux canaux de client à partir de la fabrication de canal existante.Si vous utilisez un objet de client, vous pouvez obtenir la fabrication de canal sous\-jacente à partir d'un objet de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en appelant la propriété <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A?displayProperty=fullName>.  
  
 Concernant les fabrications de canaux, il est important de garder à l'esprit qu'elles créent des nouvelles instances de canaux de client pour la configuration fournie avant l'appel de la méthode <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=fullName>.Après avoir appelé <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> \(ou <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=fullName>, <xref:System.ServiceModel.ClientBase%601.CreateChannel%2A?displayProperty=fullName>ou toute opération d'un objet de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]\), vous ne pouvez plus modifier la fabrication de canal et espérer obtenir des canaux vers des instances de service différentes, même si vous modifiez l'adresse de point de terminaison cible.Si vous souhaitez créer un objet de client ou un canal de client avec une configuration différente, vous devez d'abord créer une nouvelle fabrication de canal.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] les différents problèmes pouvant survenir lors de l'utilisation des objets de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et des canaux de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [Accès aux services à l'aide d'un client WCF](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
 Les deux sections suivantes contiennent des instructions permettant de créer et d'utiliser les objets de canal de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
#### Création d'un nouvel objet de canal de client WCF  
 Dans notre exemple illustrant l'utilisation d'un canal de client, nous supposons que le contrat de service suivant a été généré.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Pour vous connecter à un service `ISampleService`, utilisez l'interface de contrat générée directement avec une fabrication de canal \(<xref:System.ServiceModel.ChannelFactory%601>\).Après avoir créé et configuré une fabrication de canal pour un contrat particulier, vous pouvez appeler la méthode <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> pour retourner des objets de canal de client qui vous permettront de communiquer avec un service `ISampleService`.  
  
 Lorsque vous utilisez la classe <xref:System.ServiceModel.ChannelFactory%601> avec une interface de contrat de service, vous devez transtyper vers l'interface <xref:System.ServiceModel.IClientChannel> pour ouvrir, fermer ou abandonner le canal de manière explicite.Pour faciliter son utilisation, l'outil Svcutil.exe génère également une interface d'assistance qui implémente à la fois l'interface de contrat de service et <xref:System.ServiceModel.IClientChannel> afin de vous permettre d'interagir avec l'infrastructure de canal client sans devoir convertir de type.L'exemple de code suivant définit un canal de client d'assistance qui implémente le contrat de service précédent.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
#### Création d'un nouvel objet de canal de client WCF  
 Pour utiliser un canal client et se connecter à un service `ISampleService`, utilisez directement l'interface de contrat générée \(ou la version d'assistance\) avec une fabrication de canal, en passant le type de l'interface de contrat comme paramètre de type.Après avoir créé et configuré une fabrication de canal pour un contrat particulier, vous pouvez appeler la méthode <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=fullName> pour retourner des objets de canal client qui vous permettront de communiquer avec un service `ISampleService`.  
  
 Une fois créés, les objets de canal de client implémentent <xref:System.ServiceModel.IClientChannel> ainsi que l'interface de contrat.Par conséquent, vous pouvez les utiliser directement pour appeler les opérations qui interagissent avec un service prenant en charge le contrat.  
  
 La différence entre les objets de client et les objets de canal de client réside dans leurs modalités de contrôle et leur simplicité d'utilisation.De nombreux développeurs, qui se sentent à l'aise avec les classes et les objets, préféreront utiliser les objets de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] plutôt que les canaux de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Pour obtenir un exemple, consultez [Comment : utiliser la classe ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).