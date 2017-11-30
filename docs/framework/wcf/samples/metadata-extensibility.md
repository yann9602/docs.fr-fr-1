---
title: "Extensibilité des métadonnées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f92fcc76-0806-4c84-9d63-7aae0d3899de
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 36eb5940fa1d869948a94fcbbb1945aea1c534ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="metadata-extensibility"></a>Extensibilité des métadonnées
Cette section contient des exemples qui illustrent des métadonnées personnalisées.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Point de terminaison de métadonnées de sécurisé personnalisée](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 Montre comment implémenter un service avec un point de terminaison de métadonnées sécurisé qui utilise l’une des liaisons non-metadata exchange et comment configurer [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ou aux clients d’extraire les métadonnées à partir de cette terminaison de métadonnées.  
  
 [Publication WSDL personnalisée](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
 Montre comment implémenter un <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> sur un attribut <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> personnalisé pour exporter les propriétés de l'attribut en tant qu'annotations WSDL, entre autres fonctionnalités.
