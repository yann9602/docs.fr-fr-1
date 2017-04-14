---
title: "&lt;wsdlImporters&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 270c7f93-eab7-47b6-8b94-ac3f5b7f17e4
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;wsdlImporters&gt;
Cet élément de configuration indique tous les importateurs WSDL qui importent des métadonnées Web Services Description Language \(WSDL\) 1.1 avec des pièces jointes WS\-Policy.  Chaque élément enfant est un \<`wsdlImporter`\> qui spécifie une manière d'importer des métadonnées et de convertir ces informations en différentes classes représentant les informations de contrat et de point de terminaison.  Il peut importer sélectivement des informations de contrat et de point de terminaison ainsi que des propriétés qui exposent toute erreur d'importation et accepte des informations de types liées au processus d'importation et de conversion.  Il prend également en charge les informations et les propriétés de liaison qui donnent accès aux documents de stratégie, documents WSDL, extensions WSDL et documents de schéma XML.  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.MetadataElement>   
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>   
 <xref:System.ServiceModel.Description.MetadataImporter>   
 <xref:System.ServiceModel.Description.WsdlImporter>   
 [Configuration client WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)   
 [Clients](../../../../../docs/framework/wcf/feature-details/clients.md)