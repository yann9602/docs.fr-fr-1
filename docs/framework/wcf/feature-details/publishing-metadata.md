---
title: "Publication de m&#233;tadonn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "métadonnées (WCF), publier"
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Publication de m&#233;tadonn&#233;es
Les services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] publient les métadonnées à l'aide d'un ou de plusieurs points de terminaison.La publication de métadonnées de service permet d'accéder à celles\-ci à l'aide de protocoles standardisés, tels que WS\-MetadataExchange \(MEX\) et les requêtes HTTP\/GET.Les points de terminaison de métadonnées sont semblables aux autres points de terminaison de service dans le sens où ils ont une adresse, une liaison et un contrat, et qu'ils peuvent être ajoutés à un hôte de service via la configuration ou du code impératif.  
  
## Publication de points de terminaison de métadonnées  
 Pour publier des points de terminaison de métadonnées pour un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vous devez dans un premier temps ajouter le comportement de service <xref:System.ServiceModel.Description.ServiceMetadataBehavior> au service.L'ajout d'une instance <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> permet à votre service d'exposer des points de terminaison de métadonnées.Après avoir ajouté le comportement de service <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName>, vous pouvez ensuite exposer les points de terminaison de métadonnées qui prennent en charge le protocole MEX ou qui répondent aux requêtes HTTP\/GET.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> utilise <xref:System.ServiceModel.Description.WsdlExporter> pour exporter les métadonnées de tous les points de terminaison de service de votre service.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'exportation des métadonnées d'un service, consultez [Exportation et importation de métadonnées](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> ajoute une instance <xref:System.ServiceModel.Description.ServiceMetadataExtension> comme extension à votre hôte de service.<xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=fullName> fournit l'implémentation pour les protocoles de publication de métadonnées.Vous pouvez également utiliser <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=fullName> pour obtenir les métadonnées de service au moment de l'exécution en accédant à la propriété <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=fullName>.  
  
### Points de terminaison de métadonnées MEX  
 Pour ajouter des points de terminaison de métadonnées qui utilisent le protocole MEX, ajoutez des points de terminaison de service à votre hôte de service qui utilisent le contrat de service nommé `IMetadataExchange`.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inclut une interface <xref:System.ServiceModel.Description.IMetadataExchange> avec ce nom de contrat de service que vous pouvez utiliser dans le cadre du modèle de programmation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Les points de terminaison WS\-MetadataExchange \(ou points de terminaison MEX\) peuvent utiliser l'une des quatre liaisons par défaut que les méthodes de fabrique statiques exposent sur la classe <xref:System.ServiceModel.Description.MetadataExchangeBindings> afin d'établir une correspondance avec les liaisons par défaut utilisées par les outils [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tels que Svcutil.exe.Vous pouvez également configurer des points de terminaison de métadonnées MEX à l'aide de votre propre liaison personnalisée.  
  
### Points de terminaison de métadonnées HTTP GET  
 Pour ajouter un point de terminaison de métadonnées à votre service qui répond aux requêtes HTTP\/GET, affectez `true` à la propriété <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> sur <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName>.Vous pouvez également configurer un point de terminaison de métadonnées qui utilise HTTPS en affectant `true` à la propriété <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> sur <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName>.  
  
## Dans cette section  
 [Comment : publier les métadonnées d'un service à l'aide d'un fichier de configuration](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Indique comment configurer un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] afin de publier les métadonnées et permettre ainsi aux clients de les récupérer à l'aide d'un échange WS\-MetadataExchange ou d'une requête HTTP\/GET en utilisant la chaîne de requête `?wsdl`.  
  
 [Comment : publier les métadonnées d'un service à l'aide de code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Indique comment activer la publication de métadonnées pour un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans le code afin que les clients puissent les récupérer à l'aide d'un échange WS\-MetadataExchange ou d'une requête HTTP\/GET en utilisant la chaîne de requête `?wsdl`.  
  
## Référence  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## Voir aussi  
 [Exportation et importation de métadonnées](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)