---
title: "Exportation de m&#233;tadonn&#233;es personnalis&#233;es pour une extension WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Exportation de m&#233;tadonn&#233;es personnalis&#233;es pour une extension WCF
Dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], le processus d'exportation de métadonnées consiste à décrire des points de terminaison de service et à les projeter dans une représentation parallèle standardisée qui permet aux clients de comprendre comment utiliser le service.Les métadonnées personnalisées sont composées d'éléments XML que les exportateurs de métadonnées fournis par le système ne peuvent pas exporter.En général, cela inclut les éléments WSDL personnalisés des comportements définis par l'utilisateur ainsi que les éléments de liaison et les assertions de stratégie relatives aux fonctions et spécifications des liaisons et contrats.  
  
 Cette section décrit l'exportation des éléments WSDL personnalisés ou des assertions de stratégie, mais ne traite pas du processus d'exportation lui\-même.Pour plus d'informations sur l'utilisation des types qui exportent et importent des métadonnées, que celles\-ci soient personnalisées ou générées par le système, consultez [Exportation et importation de métadonnées](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## Vue d'ensemble  
 Lorsque les métadonnées sont publiés à l'aide de <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName>, <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=fullName> est examiné, et XSD et WSDL, y compris les assertions de stratégie, sont générés pour l'ensemble des contrats et des liaisons que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut prendre en charge à l'aide des liaisons et des attributs fournis par le système.Toutefois, les éléments de liaison ou les attributs de comportement personnalisés requièrent une prise en charge pour pouvoir être exportés correctement.  
  
 Cette section décrit :  
  
1.  Comment implémenter et utiliser l'interface <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=fullName>, laquelle vous expose les données de génération WSDL avant de publier le WSDL.  
  
2.  Comment implémenter et utiliser l'interface <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=fullName>, laquelle vous expose les données de stratégie avant d'exporter les assertions de stratégie dans les données WSDL.  
  
 Pour plus d'informations sur l'importation d'assertions de stratégie et d'éléments WSDL personnalisés, consultez [Importation de métadonnées personnalisées pour une extension WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md).  
  
## Exportation d'éléments WSDL personnalisés  
 Implémentez <xref:System.ServiceModel.Description.IWsdlExportExtension> sur un comportement d'opération, comportement de contrat, comportement de point de terminaison ou élément de liaison \(<xref:System.ServiceModel.Description.IOperationBehavior>, <xref:System.ServiceModel.Description.IContractBehavior>, <xref:System.ServiceModel.Description.IEndpointBehavior> ou <xref:System.ServiceModel.Channels.BindingElement?displayProperty=fullName> respectivement\) et insérez les comportements ou éléments de liaison dans la description du service que vous tentez d'exporter.\(Pour plus d'informations sur l'insertion de comportements, consultez [Configuration et extension de l'exécution à l'aide de comportements](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)\).<xref:System.ServiceModel.Description.IWsdlExportExtension> est appelé pour chaque point de terminaison et chaque point de terminaison exporte en premier le contrat si cela n'a pas été déjà fait.Selon vos besoins, vous pouvez participer à l'un ou à l'autre processus d'exportation :  
  
-   <xref:System.ServiceModel.Description.WsdlContractConversionContext> permet de modifier les métadonnées exportées dans la méthode <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A>.  
  
-   <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> permet de modifier les métadonnées exportées pour le point de terminaison dans la méthode <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A>.  
  
 La méthode <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> est appelée sur toutes les implémentations <xref:System.ServiceModel.Description.IWsdlExportExtension> dans l'instance <xref:System.ServiceModel.Description.ContractDescription?displayProperty=fullName> exportée.La méthode <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> est appelée sur toutes les implémentations <xref:System.ServiceModel.Description.IWsdlExportExtension> avec l'instance <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=fullName> exportée.  
  
 Pour plus d'informations, consultez [Comment : exporter des informations WSDL personnalisées](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md) et l'exemple [Publication WSDL personnalisée](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md).  
  
## Exportation d'assertions de stratégie personnalisées  
 Implémentez <xref:System.ServiceModel.Description.IPolicyExportExtension> sur un <xref:System.ServiceModel.Channels.BindingElement> et ajoutez l'élément de liaison à la liaison pour écrire des assertions de stratégie personnalisées concernant la prise en charge de la liaison et les fonctions de contrat dans le WSDL.<xref:System.ServiceModel.Description.IPolicyExportExtension> est appelé une fois lors de l'exportation de l'élément de liaison implémenté dans une liaison, et passe <xref:System.ServiceModel.Description.PolicyConversionContext> à la méthode <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A>.Vous pouvez utiliser les méthodes sur l'instance <xref:System.ServiceModel.Description.PolicyConversionContext> à ajouter aux assertions de stratégie jointe à la liaison WSDL au niveau des objets de message, d'opération ou de point de terminaison.  
  
 Pour plus d'informations, consultez [Comment : exporter des assertions de stratégie personnalisées](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md).  
  
## Voir aussi  
 [Comment : exporter des informations WSDL personnalisées](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)   
 [Comment : exporter des assertions de stratégie personnalisées](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md)   
 [Importation de métadonnées personnalisées pour une extension WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)