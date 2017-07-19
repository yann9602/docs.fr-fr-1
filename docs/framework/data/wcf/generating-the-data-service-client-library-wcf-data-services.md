---
title: "G&#233;n&#233;ration de la biblioth&#232;que cliente du service de donn&#233;es (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ajouter une référence de service, boîte de dialogue"
  - "applications clientes, Services de données WCF"
  - "Services de données WCF, bibliothèque cliente"
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# G&#233;n&#233;ration de la biblioth&#232;que cliente du service de donn&#233;es (WCF Data Services)
Un service de données qui implémente le protocole [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] peut retourner un document des métadonnées du service qui décrit le modèle de données exposé par le flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  Pour plus d'informations, consultez [OData : document de métadonnées du service](http://go.microsoft.com/fwlink/?LinkId=186070). Vous pouvez utiliser la boîte de dialogue **Ajouter une référence de service** dans Visual Studio pour ajouter une référence à un service [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  Lorsque vous utilisez cet outil pour ajouter une référence aux métadonnées retournées par un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] dans un projet client, il effectue les actions suivantes :  
  
-   Demande le document de métadonnées du service de données et interprète les métadonnées retournées.  
  
    > [!NOTE]
    >  Les métadonnées retournées sont stockées dans le projet client sous forme de fichier .edmx.  Ce fichier .edmx ne peut pas s'ouvrir à l'aide d'Entity Data Model Designer parce qu'il n'a pas le même format que les fichiers .edmx utilisés par Entity Framework.  Vous pouvez consulter ce fichier de métadonnées à l'aide de l'éditeur XML ou d'un éditeur de texte.  Pour plus d'informations, consultez la spécification [\[MC\-EDMX\] : modèle de données des entités pour le format du packaging des services de données](http://go.microsoft.com/fwlink/?LinkID=178833)  
  
-   Génère une représentation du service comme une classe de conteneur d'entités qui hérite de <xref:System.Data.Services.Client.DataServiceContext>.  Cette classe de conteneur d'entités générée ressemble au conteneur d'entités que génèrent les outils Entity Data Model.  Pour plus d'informations, consultez [Object Services Overview \(Entity Framework\)](http://msdn.microsoft.com/fr-fr/43014cf9-c9cb-4538-bfbb-197820b60038).  
  
-   Génère des classes de données pour les types de modèles de données découverts dans les métadonnées de service.  
  
-   Ajoute une référence à l'assembly `System.Data.Services.Client` au projet.  
  
 Pour plus d'informations, consultez [Procédure : ajouter une référence de service de données](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).  
  
 Les classes de service de données client peuvent également être générées en utilisant l'outil [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) à l'invite de commandes.  Pour plus d'informations, consultez [Procédure : générer manuellement des classes de service de données client](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## Mappage de type de données client  
 Lorsque vous utilisez la boîte de dialogue **Ajouter une référence de service** dans Visual Studio ou l'outil `DataSvcUtil.exe` pour générer des classes de données clientes basées sur un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], les types de données .NET Framework sont mappés aux types primitifs du modèle de données comme suit :  
  
|Type de modèle de données|Types de données .NET Framework|  
|-------------------------------|-------------------------------------|  
|`Edm.Binary`|<xref:System.Byte> `[]`|  
|`Edm.Boolean`|<xref:System.Boolean>|  
|`Edm.Byte`|<xref:System.Byte>|  
|`Edm.DateTime`|<xref:System.DateTime>|  
|`Edm.Decimal`|<xref:System.Decimal>|  
|`Edm.Double`|<xref:System.Double>|  
|`Edm.Guid`|<xref:System.Guid>|  
|`Edm.Int16`|<xref:System.Int16>|  
|`Edm.Int32`|<xref:System.Int32>|  
|`Edm.Int64`|<xref:System.Int64>|  
|`Edm.SByte`|<xref:System.SByte>|  
|`Edm.Single`|<xref:System.Single>|  
|`Edm.String`|<xref:System.String>|  
  
 Pour plus d'informations, consultez [OData : types de données primitives](http://go.microsoft.com/fwlink/?LinkId=186072).  
  
## Voir aussi  
 [Bibliothèque cliente de WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)   
 [Démarrage rapide](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)