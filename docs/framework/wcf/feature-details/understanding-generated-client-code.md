---
title: "Fonctionnement du code client généré"
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
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4d185371c1648241db7b01f26a49e2e1e8710b0e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="understanding-generated-client-code"></a>Fonctionnement du code client généré
L' [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) génère du code client et un fichier de configuration d'application cliente à des fins de création d’applications clientes. Cette rubrique présente des exemples de code généré pour des scénarios de contrat de service standard. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la génération d'une application cliente à l'aide du code généré, consultez [WCF Client Overview](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Vue d'ensemble  
 Si vous utilisez [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] afin de générer des types de clients [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour votre projet, il n'est en général pas nécessaire d'examiner le code client généré. Si vous n'utilisez pas un environnement de développement qui exécute les mêmes services pour vous, vous pouvez utiliser un outil tel que Svcutil.exe pour générer le code client, puis utiliser ce code pour développer votre application cliente.  
  
 Svcutil.exe disposant de plusieurs options qui modifient les informations de type générées, cette rubrique ne traite pas de tous les scénarios. Toutefois, les tâches standard suivantes impliquent la localisation de code généré :  
  
-   Identification d'interfaces de contrat de service.  
  
-   Identification de la classe de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .  
  
-   Identification des types de données.  
  
-   Identification des contrats de rappel pour les services duplex.  
  
-   Identification de l'interface de canal de contrat de service d'assistance.  
  
### <a name="finding-service-contract-interfaces"></a>Recherche d'interfaces de contrat de service  
 Pour trouver les interfaces qui modèlent des contrats de service, recherchez les interfaces marquées avec l'attribut <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>. Cet attribut est souvent difficile à trouver avec une lecture rapide en raison de la présence d'autres attributs et des propriétés explicites définies sur l'attribut lui-même. N'oubliez pas que l'interface de contrat de service et l'interface de contrat client sont deux types différents. L'exemple de code suivant illustre le contrat de service d'origine.  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 L'exemple de code suivant illustre le même contrat de service, tel que généré par Svcutil.exe.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Vous pouvez utiliser l'interface de contrat de service générée avec la classe <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> pour créer un objet de canal [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec lequel appeler des opérations de service. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : utiliser la classe ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).  
  
### <a name="finding-wcf-client-classes"></a>Recherche de classes de client WCF  
 Pour trouver la classe de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui implémente le contrat de service que vous souhaitez utiliser, recherchez une extension de <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, où le paramètre de type est l'interface de contrat de service que vous avez trouvée précédemment et qui étend cette interface. L'exemple de code suivant illustre la classe <xref:System.ServiceModel.ClientBase%601> de type `ISampleService`.  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Vous pouvez utiliser cette classe de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en créant une nouvelle instance et en appelant les méthodes qu'elle implémente. Ces méthodes appellent l'opération de service avec laquelle elle est conçue et configurée pour interagir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Vue d’ensemble du Client WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
> [!NOTE]
>  Lorsque SvcUtil.exe génère une classe de client WCF, il ajoute un <xref:System.Diagnostics.DebuggerStepThroughAttribute> à la classe de client qui empêche les débogueurs de parcourir pas à pas la classe de client WCF.  
  
### <a name="finding-data-types"></a>Recherche de types de données  
 Pour trouver des types de données dans le code généré, le mécanisme le plus simple consiste à identifier le nom de type spécifié dans un contrat et à rechercher le code pour cette déclaration de type. Par exemple, le contrat suivant spécifie que le `SampleMethod` peut retourner une erreur SOAP de type `microsoft.wcf.documentation.SampleFault`.  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 La recherche de `SampleFault` localise la déclaration de type suivante.  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 Dans ce cas, le type de données est le type de détail levé par une exception spécifique sur le client, un <xref:System.ServiceModel.FaultException%601> où le paramètre de type de détail est `microsoft.wcf.documentation.SampleFault`. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] les types de données, consultez [Specifying Data Transfer in Service Contracts](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la gestion des exceptions dans les clients, consultez [Sending and Receiving Faults](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>Recherche de contrats de rappel pour les services duplex  
 Si vous trouvez un contrat de service pour lequel l'interface de contrat spécifie une valeur pour la propriété <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType>, ce contrat spécifie un contrat duplex. Les contrats duplex requièrent que l'application cliente crée une classe de rappel qui implémente le contrat de rappel et passe une instance de cette classe au <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> ou <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> utilisé pour communiquer avec le service. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]les clients duplex, consultez [Comment : accéder aux Services avec un contrat Duplex](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).  
  
 Le contrat suivant spécifie un contrat de rappel de type `SampleDuplexHelloCallback`.  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 La recherche de ce contrat de rappel localise l'interface suivante que l'application cliente doit implémenter.  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a>Recherche d'interfaces de canal de contrat de service  
 Lorsque vous utilisez la classe <xref:System.ServiceModel.ChannelFactory> avec une interface de contrat de service, vous devez effectuer une conversion de type dans l'interface <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> pour ouvrir, fermer ou abandonner le canal de manière explicite. Pour faciliter son utilisation, l'outil Svcutil.exe génère également une interface d'assistance qui implémente à la fois l'interface de contrat de service et <xref:System.ServiceModel.IClientChannel> afin de vous permettre d'interagir avec l'infrastructure de canal client sans devoir convertir de type. Le code suivant illustre la définition d'un canal client d'assistance qui implémente le contrat de service précédent.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble d’un client WCF](../../../../docs/framework/wcf/wcf-client-overview.md)
