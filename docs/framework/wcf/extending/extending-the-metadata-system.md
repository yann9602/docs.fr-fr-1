---
title: "Extension du syst&#232;me de m&#233;tadonn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "extension des métadonnées (WCF)"
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Extension du syst&#232;me de m&#233;tadonn&#233;es
Le système de métadonnées [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] est un groupe de classes et d'interfaces qui représentent les métadonnées requises pour implémenter des applications basées sur un service.Modifiez ou étendez les classes ou implémentez et configurez les interfaces pour exporter et importer des métadonnées personnalisées telles que les extensions WSDL \(Web Services Description Language\) ou des assertions WS\-PolicyAttachments personnalisées.  
  
## Dans cette section  
 [Exportation de métadonnées personnalisées pour une extension WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 Décrit comment implémenter et utiliser l'interface <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=fullName> pour incorporer des assertions de stratégie personnalisées dans des documents WSDL.  
  
 [Importation de métadonnées personnalisées pour une extension WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)  
 Décrit comment implémenter et utiliser l'interface <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=fullName> pour lire et répondre à des assertions de stratégie personnalisées dans des documents WSDL.  
  
 [Publication et récupération de métadonnées sur une liaison personnalisée](../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 Décrit comment échanger des métadonnées sur des liaisons personnalisées.