---
title: "Comment : publier les métadonnées d'un service à l'aide de code"
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
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 455929144f771128ca070cd02e65c919ce4c741f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a>Comment : publier les métadonnées d'un service à l'aide de code
C'est l'une des deux rubriques de procédure qui traitent de la publication de métadonnées pour un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Il y a deux façons de spécifier comment un service doit publier des métadonnées : à l'aide d'un fichier de configuration et à l'aide du code. Cette rubrique montre comment publier les métadonnées d'un service à l'aide d'un code.  
  
> [!CAUTION]
>  Cette rubrique indique comment publier des métadonnées de manière non sécurisée. Tout client peut récupérer les métadonnées du service. Si votre service doit publier les métadonnées de manière sécurisée. consultez [personnalisé sécuriser les métadonnées de point de terminaison](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]publication de métadonnées dans un fichier de configuration, consultez [Comment : publier les métadonnées pour un Service à l’aide d’un fichier de Configuration](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md). La publication des métadonnées permet aux clients de récupérer les métadonnées via une requête WS-Transfer GET ou une requête HTTP/GET à l'aide de la chaîne de requête `?wsdl`. Pour être sûr que le code fonctionne, vous devez créer un service WCF de base. Un service auto-hébergé de base est fourni dans le code suivant.  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a>Pour publier les métadonnées dans le code  
  
1.  Dans la méthode principale d'une application console, instanciez un objet <xref:System.ServiceModel.ServiceHost> en passant le type de service et l'adresse de base.  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2.  Créez immédiatement un bloc try sous le code pour l'étape 1, celui-ci intercepte toutes les exceptions levées pendant l'exécution du service.  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3.  Vérifiez si l'hôte de service contient déjà un <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, si ce n'est pas le cas, créez une instance <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4.  Affectez à la propriété <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> la valeur `true.`  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5.  Le <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contient une <xref:System.ServiceModel.Description.MetadataExporter>. Le <xref:System.ServiceModel.Description.MetadataExporter> contient une <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A>. Affectez à la propriété <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> la valeur <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>. Vous pouvez affecter à la propriété <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> la valeur <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>. Lorsque la valeur <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> l’exportateur de métadonnées génère les informations de stratégie avec les métadonnées qui » est conforme à WS-Policy 1.5. Lorsqu'il a la valeur <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>, l'exportateur de métadonnées génère les informations de stratégie qui se conforment à WS-Policy 1.2.  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6.  Ajoutez l'instance <xref:System.ServiceModel.Description.ServiceMetadataBehavior> à la collection de comportements de l'hôte de service.  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7.  Ajoutez le point de terminaison d'échange des métadonnées à l'hôte de service.  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8.  Ajoutez un point de terminaison d'application à l'hôte de service.  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    >  Si vous n'ajoutez pas de points de terminaison au service, le runtime ajoute les points de terminaison par défaut. Dans cet exemple, étant donné que le service a un <xref:System.ServiceModel.Description.ServiceMetadataBehavior> défini sur la valeur `true`, la publication des métadonnées est activée pour le service. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]par défaut des points de terminaison, consultez [Configuration simplifiée](../../../../docs/framework/wcf/simplified-configuration.md) et [simplifié la Configuration des Services WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
9. Ouvrez l'hôte de service et attendez les appels entrants. Lorsque l'utilisateur appuie sur ENTRÉE, fermez l'hôte de service.  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. Créez et exécutez l'application console.  
  
11. Utilisez Internet Explorer pour naviguer jusqu'à l'adresse de base du service (http://localhost:8001/MetadataSample dans cet exemple) et vérifiez que la publication des métadonnées est activée. Vous devriez voir s'afficher une page Web qui indique "Service simple" en haut et plus bas "Vous a créé un service". Dans la négative, un message s'affiche en haut de la page résultante : "La publication des métadonnées pour ce service est actuellement désactivée".  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant affiche l'implémentation d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de base qui publie les métadonnées pour le service dans le code.  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour héberger un service WCF dans une application managée](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [Auto-hébergement](../../../../docs/framework/wcf/samples/self-host.md)  
 [Vue d’ensemble de l’architecture de métadonnées](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [Utilisation des métadonnées](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Guide pratique pour publier les métadonnées d’un service à l’aide d’un fichier de configuration](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
