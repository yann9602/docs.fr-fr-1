---
title: "Comment : utiliser MetadataResolver pour obtenir des métadonnées de liaison dynamiquement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8f3d8245b9d5bf05297b4d1edfba1926d2104ce
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a>Comment : utiliser MetadataResolver pour obtenir des métadonnées de liaison dynamiquement
Cette rubrique indique comment utiliser la classe <xref:System.ServiceModel.Description.MetadataResolver> pour obtenir des métadonnées de liaison dynamiquement.  
  
### <a name="to-dynamically-obtain-binding-metadata"></a>Pour obtenir des métadonnées de liaison dynamiquement  
  
1.  Créez un objet <xref:System.ServiceModel.EndpointAddress> avec l'adresse du point de terminaison de métadonnées.  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2.  Appelez <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, qui passe le type de service et l'adresse du point de terminaison de métadonnées. Une collection de points de terminaison qui implémentent le contrat spécifié est alors retournée. Seules les informations de liaison sont importées à partir des métadonnées, les informations de contrat ne le sont pas. Le contrat fourni est utilisé à la place.  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3.  Vous pouvez ensuite itérer au sein de la collection de points de terminaison de service afin d'extraire les informations de liaison dont vous avez besoin. Le code suivant itère au sein des points de terminaison, crée un objet client de service qui passe la liaison et l’adresse associée au point de terminaison actuel, puis appelle une méthode sur le service.  
  
    ```  
    foreach (ServiceEndpoint point in endpoints)  
    {  
       if (point != null)  
       {  
          // Create a new wcfClient using retrieved endpoints.  
          using (wcfClient = new SampleServiceClient(point.Binding, point.Address))  
          {  
             Console.WriteLine(  
               wcfClient.SampleMethod("Client used the "  
               + point.Address.ToString() + " address."));  
          }  
      }  
    }  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Métadonnées](../../../../docs/framework/wcf/feature-details/metadata.md)
