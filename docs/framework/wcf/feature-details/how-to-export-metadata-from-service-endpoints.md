---
title: "Comment&#160;: exporter des m&#233;tadonn&#233;es &#224; partir de points de terminaison de service | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Comment&#160;: exporter des m&#233;tadonn&#233;es &#224; partir de points de terminaison de service
Cette rubrique explique comment exporter des métadonnées à partir de points de terminaison de service.  
  
### Pour exporter des métadonnées à partir de points de terminaison de service  
  
1.  Créez un nouveau projet d'application console Visual Studio.  Ajoutez le code affiché aux étapes suivantes dans le fichier Program.cs généré dans la méthode main\(\).  
  
2.  Créer un <xref:System.ServiceModel.Description.WsdlExporter>.  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3.  Affectez l'une des valeurs de l'énumération <xref:System.ServiceModel.Description.PolicyVersion> à la propriété <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A>.  Cet exemple affecte <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> à la valeur ce qui correspond à WS\-Policy 1.5.  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4.  Créez un tableau d'objets <xref:System.ServiceModel.Description.ServiceEndpoint>.  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5.  Exportez les métadonnées pour chaque point de terminaison de service.  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6.  Vérifiez qu'aucune erreur ne s'est produite pendant le processus d'exportation et récupérez les métadonnées.  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7.  Vous pouvez maintenant utiliser les métadonnées, par exemple les écrire dans un fichier en appelant la méthode <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29>.  
  
## Exemple  
 Les éléments suivants représentent l'intégralité du code pour cet exemple.  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## Compilation du code  
 Lors de la compilation de Program.cs, faites référence à System.ServiceModel.dll.  
  
## Voir aussi  
 [Vue d'ensemble de l'architecture de métadonnées](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)   
 [Utilisation des métadonnées](../../../../docs/framework/wcf/feature-details/using-metadata.md)   
 [Points de terminaison : adresses, liaisons et contrats](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)