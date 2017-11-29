---
title: "Comment : exporter des métadonnées à partir de points de terminaison de service"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d076878f31d162713feaecc0a92c2f6f534897b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-export-metadata-from-service-endpoints"></a>Comment : exporter des métadonnées à partir de points de terminaison de service
Cette rubrique explique comment exporter des métadonnées à partir de points de terminaison de service.  
  
### <a name="to-export-metadata-from-service-endpoints"></a>Pour exporter des métadonnées à partir de points de terminaison de service  
  
1.  Créez un nouveau projet d'application console Visual Studio. Ajoutez le code affiché aux étapes suivantes dans le fichier Program.cs généré dans la méthode main().  
  
2.  Créer un <xref:System.ServiceModel.Description.WsdlExporter>.  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3.  Affectez l'une des valeurs de l'énumération <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> à la propriété <xref:System.ServiceModel.Description.PolicyVersion>. Cet exemple affecte <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> à la valeur ce qui correspond à WS-Policy 1.5.  
  
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
  
## <a name="example"></a>Exemple  
 Les éléments suivants représentent l'intégralité du code pour cet exemple.  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Lors de la compilation de Program.cs, faites référence à System.ServiceModel.dll.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’Architecture de métadonnées](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [À l’aide de métadonnées](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Points de terminaison : Adresses, liaisons et contrats](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
