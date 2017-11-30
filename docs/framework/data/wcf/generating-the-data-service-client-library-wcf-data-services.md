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
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="4ba42-102">Génération de la bibliothèque client service de données (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="4ba42-102">Generating the Data Service Client Library (WCF Data Services)</span></span>
<span data-ttu-id="4ba42-103">Un service de données qui implémente le [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] peut retourner un document de métadonnées de service qui décrit le modèle de données exposé par le [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de flux.</span><span class="sxs-lookup"><span data-stu-id="4ba42-103">A data service that implements the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] can return a service metadata document that describes the data model exposed by the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span> <span data-ttu-id="4ba42-104">Pour plus d’informations, consultez [OData : Document de métadonnées de Service](http://go.microsoft.com/fwlink/?LinkId=186070).</span><span class="sxs-lookup"><span data-stu-id="4ba42-104">For more information, see [OData: Service Metadata Document](http://go.microsoft.com/fwlink/?LinkId=186070).</span></span> <span data-ttu-id="4ba42-105">Vous pouvez utiliser la **ajouter une référence de Service** boîte de dialogue dans Visual Studio pour ajouter une référence à un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-en fonction du service.</span><span class="sxs-lookup"><span data-stu-id="4ba42-105">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service.</span></span> <span data-ttu-id="4ba42-106">Lorsque vous utilisez cet outil pour ajouter une référence aux métadonnées retournées par une [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de flux dans un projet client, il effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="4ba42-106">When you use this tool to add a reference to the metadata returned by an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed in a client project, it performs the following actions:</span></span>  
  
-   <span data-ttu-id="4ba42-107">Demande le document de métadonnées du service de données et interprète les métadonnées retournées.</span><span class="sxs-lookup"><span data-stu-id="4ba42-107">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ba42-108">Les métadonnées retournées sont stockées dans le projet client sous forme de fichier .edmx.</span><span class="sxs-lookup"><span data-stu-id="4ba42-108">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="4ba42-109">Ce fichier .edmx ne peut pas s'ouvrir à l'aide d'Entity Data Model Designer parce qu'il n'a pas le même format que les fichiers .edmx utilisés par Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="4ba42-109">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="4ba42-110">Vous pouvez consulter ce fichier de métadonnées à l'aide de l'éditeur XML ou d'un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="4ba42-110">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="4ba42-111">Pour plus d’informations, consultez la [ \[MC-EDMX\]: Entity Data Model pour le Format du Packaging des Services de données](http://go.microsoft.com/fwlink/?LinkID=178833) spécification</span><span class="sxs-lookup"><span data-stu-id="4ba42-111">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](http://go.microsoft.com/fwlink/?LinkID=178833) specification</span></span>  
  
-   <span data-ttu-id="4ba42-112">Génère une représentation du service comme une classe de conteneur d'entités qui hérite de <xref:System.Data.Services.Client.DataServiceContext>.</span><span class="sxs-lookup"><span data-stu-id="4ba42-112">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="4ba42-113">Cette classe de conteneur d'entités générée ressemble au conteneur d'entités que génèrent les outils Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="4ba42-113">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="4ba42-114">Pour plus d’informations, consultez [Object Services Overview (Entity Framework)](http://msdn.microsoft.com/en-us/43014cf9-c9cb-4538-bfbb-197820b60038).</span><span class="sxs-lookup"><span data-stu-id="4ba42-114">For more information, see [Object Services Overview (Entity Framework)](http://msdn.microsoft.com/en-us/43014cf9-c9cb-4538-bfbb-197820b60038).</span></span>  
  
-   <span data-ttu-id="4ba42-115">Génère des classes de données pour les types de modèles de données découverts dans les métadonnées de service.</span><span class="sxs-lookup"><span data-stu-id="4ba42-115">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
-   <span data-ttu-id="4ba42-116">Ajoute une référence à l'assembly `System.Data.Services.Client` au projet.</span><span class="sxs-lookup"><span data-stu-id="4ba42-116">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="4ba42-117">Pour plus d’informations, consultez [Comment : ajouter une référence de Service de données](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="4ba42-117">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="4ba42-118">Les classes de service de données client peuvent également être générées à l’aide de la [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) outil à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="4ba42-118">The client data service classes can also be generated by using the [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="4ba42-119">Pour plus d’informations, consultez [Comment : manuellement générer Service Classes de données Client](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="4ba42-119">For more information, see [How to: Manually Generate Client Data Service Classes](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="4ba42-120">Mappage de type de données client</span><span class="sxs-lookup"><span data-stu-id="4ba42-120">Client Data Type Mapping</span></span>  
 <span data-ttu-id="4ba42-121">Lorsque vous utilisez la **ajouter une référence de Service** boîte de dialogue dans Visual Studio ou le `DataSvcUtil.exe` outil pour générer des classes de données client qui sont basés sur un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux, les types de données .NET Framework sont mappés aux types primitifs à partir de la le modèle de données comme suit :</span><span class="sxs-lookup"><span data-stu-id="4ba42-121">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="4ba42-122">Type de modèle de données</span><span class="sxs-lookup"><span data-stu-id="4ba42-122">Data model type</span></span>|<span data-ttu-id="4ba42-123">Types de données .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4ba42-123">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="4ba42-124"><xref:System.Byte> `[]`</span><span class="sxs-lookup"><span data-stu-id="4ba42-124"><xref:System.Byte> `[]`</span></span>|  
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
  
 <span data-ttu-id="4ba42-125">Pour plus d’informations, consultez [OData : Types de données primitifs](http://go.microsoft.com/fwlink/?LinkId=186072).</span><span class="sxs-lookup"><span data-stu-id="4ba42-125">For more information, see [OData: Primitive Data Types](http://go.microsoft.com/fwlink/?LinkId=186072).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ba42-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ba42-126">See Also</span></span>  
 [<span data-ttu-id="4ba42-127">Bibliothèque cliente WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="4ba42-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [<span data-ttu-id="4ba42-128">Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="4ba42-128">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
