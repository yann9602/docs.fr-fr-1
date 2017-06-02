---
title: "R&#233;cup&#233;ration de m&#233;tadonn&#233;es | Microsoft Docs"
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
  - "métadonnées (WCF), récupérer"
ms.assetid: 18d8ba4c-af0f-4827-a50b-4202d767bacc
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# R&#233;cup&#233;ration de m&#233;tadonn&#233;es
Le processus de récupération de métadonnées consiste à demander et à récupérer les métadonnées d'un point de terminaison de métadonnées, tel que WS\-MetadataExchange \(MEX\) ou HTTP\/GET.  
  
## Récupération de métadonnées à partir de la ligne de commande à l'aide de Svcutil.exe  
 Vous pouvez récupérer des métadonnées de service à l'aide d'un échange WS\-MetadataExchange ou de requêtes HTTP\/GET en utilisant l'outil [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) et en passant le commutateur `/target:metadata` et une adresse.Svcutil.exe télécharge les métadonnées à l'adresse spécifiée et enregistre le fichier sur disque.Svcutil.exe utilise une instance <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> en interne et charge, à partir de la configuration, la configuration de point de terminaison <xref:System.ServiceModel.Description.IMetadataExchange> dont le nom correspond au schéma de l'adresse passée à Svcutil.exe en tant qu'entrée.  
  
## Récupération de métadonnées par programme à l'aide de MetadataExchangeClient  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] récupère des métadonnées de service à l'aide des protocoles standardisés tels que WS\-MetadataExchange et les requêtes HTTP\/GET.Ces deux protocoles sont pris en charge par le type <xref:System.ServiceModel.Description.MetadataExchangeClient>.Vous récupérez les métadonnées de service à l'aide du type <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> en fournissant une adresse au point de terminaison de métadonnées et une liaison facultative.La liaison utilisée par une instance <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> peut être l'une des liaisons par défaut de la classe statique <xref:System.ServiceModel.Description.MetadataExchangeBindings>, une liaison fournie par l'utilisateur ou une liaison chargée à partir d'une configuration de point de terminaison pour le contrat `IMetadataExchange`.<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> peut également résoudre des références d'URL HTTP aux métadonnées à l'aide du type <xref:System.Net.HttpWebRequest>.  
  
 Par défaut, une instance <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> est attachée à une instance <xref:System.ServiceModel.ChannelFactory> unique.Vous pouvez modifier ou remplacer l'instance <xref:System.ServiceModel.ChannelFactory?displayProperty=fullName> utilisée par <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> en substituant la méthode virtuelle <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A>.De la même façon, vous pouvez modifier ou remplacer l'instance <xref:System.Net.HttpWebRequest> utilisée par <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> pour effectuer des requêtes HTTP\/GET en substituant la méthode virtuelle <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=fullName>.  
  
## Dans cette section  
 [Comment : utiliser Svcutil.exe pour télécharger des documents de métadonnées](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)  
 Indique comment utiliser Svcutil.exe pour télécharger des documents de métadonnées.  
  
 [Comment : utiliser MetadataResolver pour obtenir des métadonnées de liaison dynamiquement](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)  
 Indique comment utiliser <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=fullName> pour obtenir dynamiquement des métadonnées de liaison pendant l'exécution.  
  
 [Comment : utiliser MetadataExchangeClient pour récupérer des métadonnées](../../../../docs/framework/wcf/feature-details/how-to-use-metadataexchangeclient-to-retrieve-metadata.md)  
 Indique comment utiliser la classe <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> pour télécharger des fichiers de métadonnées dans un objet <xref:System.ServiceModel.Description.MetadataSet?displayProperty=fullName> qui contient des objets <xref:System.ServiceModel.Description.MetadataSection?displayProperty=fullName> à écrire dans des fichiers ou destinés à d'autres fins.  
  
## Voir aussi  
 <xref:System.ServiceModel.Description.MetadataExchangeClient>