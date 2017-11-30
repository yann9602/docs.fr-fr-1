---
title: "Génération de la bibliothèque client service de données (services de données WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5fbf45a3447a1dc5fb449628bdd7f741fb3e8324
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Génération de la bibliothèque client service de données (services de données WCF)
Un service de données qui implémente le [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] peut retourner un document de métadonnées de service qui décrit le modèle de données exposé par le [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de flux. Pour plus d’informations, consultez [OData : Document de métadonnées de Service](http://go.microsoft.com/fwlink/?LinkId=186070). Vous pouvez utiliser la **ajouter une référence de Service** boîte de dialogue dans Visual Studio pour ajouter une référence à un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-en fonction du service. Lorsque vous utilisez cet outil pour ajouter une référence aux métadonnées retournées par une [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de flux dans un projet client, il effectue les actions suivantes :  
  
-   Demande le document de métadonnées du service de données et interprète les métadonnées retournées.  
  
    > [!NOTE]
    >  Les métadonnées retournées sont stockées dans le projet client sous forme de fichier .edmx. Ce fichier .edmx ne peut pas s'ouvrir à l'aide d'Entity Data Model Designer parce qu'il n'a pas le même format que les fichiers .edmx utilisés par Entity Framework. Vous pouvez consulter ce fichier de métadonnées à l'aide de l'éditeur XML ou d'un éditeur de texte. Pour plus d’informations, consultez la [ \[MC-EDMX\]: Entity Data Model pour le Format du Packaging des Services de données](http://go.microsoft.com/fwlink/?LinkID=178833) spécification  
  
-   Génère une représentation du service comme une classe de conteneur d'entités qui hérite de <xref:System.Data.Services.Client.DataServiceContext>. Cette classe de conteneur d'entités générée ressemble au conteneur d'entités que génèrent les outils Entity Data Model. Pour plus d’informations, consultez [Object Services Overview (Entity Framework)](http://msdn.microsoft.com/en-us/43014cf9-c9cb-4538-bfbb-197820b60038).  
  
-   Génère des classes de données pour les types de modèles de données découverts dans les métadonnées de service.  
  
-   Ajoute une référence à l'assembly `System.Data.Services.Client` au projet.  
  
 Pour plus d’informations, consultez [Comment : ajouter une référence de Service de données](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).  
  
 Les classes de service de données client peuvent également être générées à l’aide de la [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) outil à l’invite de commandes. Pour plus d’informations, consultez [Comment : manuellement générer Service Classes de données Client](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="client-data-type-mapping"></a>Mappage de type de données client  
 Lorsque vous utilisez la **ajouter une référence de Service** boîte de dialogue dans Visual Studio ou le `DataSvcUtil.exe` outil pour générer des classes de données client qui sont basés sur un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux, les types de données .NET Framework sont mappés aux types primitifs à partir de la le modèle de données comme suit :  
  
|Type de modèle de données|Types de données .NET Framework|  
|---------------------|------------------------------|  
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
  
 Pour plus d’informations, consultez [OData : Types de données primitifs](http://go.microsoft.com/fwlink/?LinkId=186072).  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque cliente WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Démarrage rapide](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
