---
title: "Comment : configurer le service WCF pour interagir avec des clients du service Web ASP.NET"
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
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7ed4bf8e86e727505d48e85bb55a88452217c76b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>Comment : configurer le service WCF pour interagir avec des clients du service Web ASP.NET
Pour configurer un point de terminaison de service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] de manière à interagir avec les clients du service Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], utilisez le type <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> comme type de liaison pour votre point de terminaison de service.  
  
 Vous pouvez éventuellement activer la prise en charge du protocole HTTPS et de l'authentification du client au niveau du transport sur la liaison. Les clients du service Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ne prennent pas en charge l'encodage de messages MTOM, donc la propriété <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> doit conserver sa valeur par défaut, soit <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>. Les clients du service Web ASP.NET ne prennent pas en charge la spécification WS-Security, donc <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> doit avoir la valeur <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
 Pour rendre les métadonnées un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service disponible pour [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web des outils de génération de proxy de service (autrement dit, [Web Services Description Language Tool (Wsdl.exe)](http://go.microsoft.com/fwlink/?LinkId=73833), [Web Services Discovery Tool () Disco.exe)](http://go.microsoft.com/fwlink/?LinkId=73834)et la fonctionnalité Ajouter une référence Web dans Visual Studio), vous devez exposer un point de terminaison de métadonnées HTTP/GET.  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a>Pour ajouter un point de terminaison WCF compatible avec les clients du service Web ASP.NET dans du code  
  
1.  Créez une nouvelle instance <xref:System.ServiceModel.BasicHttpBinding>.  
  
2.  Vous pouvez éventuellement activer la sécurité de transport pour cette liaison de point de terminaison de service en affectant au mode de sécurité de la liaison la valeur <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Pour plus d’informations, consultez [sécurité du Transport](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3.  Ajoutez un nouveau point de terminaison d’application à votre hôte de service à l’aide de l’instance de liaison que vous venez de créer. Pour plus d’informations sur l’ajout d’un point de terminaison de service dans le code, consultez la [Comment : créer un point de terminaison de Service dans le Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
4.  Activez un point de terminaison de métadonnées HTTP/GET pour votre service. Pour plus d’informations, consultez [Comment : publier des métadonnées pour un Code à l’aide du Service](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a>Pour ajouter un point de terminaison WCF compatible avec les clients du service Web ASP.NET dans un fichier de configuration  
  
1.  Créez une configuration de liaison <xref:System.ServiceModel.BasicHttpBinding>. Pour plus d’informations, consultez la [Comment : spécifier une liaison de Service dans la Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
2.  Vous pouvez éventuellement activer la sécurité de transport pour la configuration de cette liaison de point de terminaison de service en affectant au mode de sécurité de la liaison la valeur <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Pour plus d’informations, consultez [sécurité du Transport](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3.  Configurez un nouveau point de terminaison d’application pour votre service à l’aide de la configuration de liaison que vous venez de créer. Pour plus d’informations sur l’ajout d’un point de terminaison de service dans un fichier de configuration, consultez le [Comment : créer un point de terminaison de Service dans la Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
4.  Activez un point de terminaison de métadonnées HTTP/GET pour votre service. Pour plus d’informations, consultez la [Comment : publier les métadonnées pour un Service à l’aide d’un fichier de Configuration](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
## <a name="example"></a>Exemple  
 L'exemple de code ci-dessous montre comment ajouter un point de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui est compatible avec les clients du service Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dans du code, ainsi que dans des fichiers de configuration.  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)] 
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)] 
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]     
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer un point de terminaison de Service dans le Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 [Comment : publier les métadonnées d’un Service à l’aide de Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 [Guide pratique pour spécifier une liaison de service dans la configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [Comment : créer un point de terminaison de Service dans la Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [Comment : publier des métadonnées pour un Service à l’aide d’un fichier de Configuration](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [Sécurité de transport](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [À l’aide de métadonnées](../../../../docs/framework/wcf/feature-details/using-metadata.md)
