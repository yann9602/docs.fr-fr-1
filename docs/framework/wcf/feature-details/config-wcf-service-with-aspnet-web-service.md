---
title: "Comment&#160;: configurer le service WCF pour interagir avec des clients du service Web ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# Comment&#160;: configurer le service WCF pour interagir avec des clients du service Web ASP.NET
Pour configurer un [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] le point de terminaison de service pour fonctionner avec [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] les clients du service Web, utilisez le <xref:System.ServiceModel.BasicHttpBinding?displayProperty=fullName> type que le type de liaison pour le point de terminaison de votre service.  
  
 Vous pouvez éventuellement activer la prise en charge du protocole HTTPS et de l’authentification du client au niveau du transport sur la liaison. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Clients de service Web ne gèrent pas le codage des messages MTOM, donc la <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=fullName> propriété doit conserver sa valeur par défaut, qui est <xref:System.ServiceModel.WSMessageEncoding?displayProperty=fullName>. Les clients de Service Web ASP.Net ne prennent pas en charge WS-Security, donc la <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=fullName> doit être définie sur <xref:System.ServiceModel.BasicHttpSecurityMode>.  
  
 Pour rendre les métadonnées pour un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service disponible pour [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] outils de génération de proxy de service Web (autrement dit, [Web Services Description Language Tool (Wsdl.exe)](http://go.microsoft.com/fwlink/?LinkId=73833), [outil Web Services Discovery Tool (Disco.exe)](http://go.microsoft.com/fwlink/?LinkId=73834)et la fonctionnalité Ajouter une référence Web dans Visual Studio), vous devez exposer un point de terminaison de métadonnées HTTP/GET.  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a>Pour ajouter un point de terminaison WCF compatible avec les clients du service Web ASP.NET dans du code  
  
1.  Créer un nouveau <xref:System.ServiceModel.BasicHttpBinding> instance  
  
2.  Éventuellement activer la sécurité de transport pour cette liaison de point de terminaison de service en définissant le mode de sécurité de la liaison <xref:System.ServiceModel.BasicHttpSecurityMode>. Pour plus d’informations, consultez [la sécurité de Transport](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3.  Ajoutez un nouveau point de terminaison d’application à votre hôte de service à l’aide de l’instance de liaison que vous venez de créer. Pour plus d’informations sur l’ajout d’un point de terminaison dans le code, consultez la [Comment : créer un point de terminaison dans le Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
4.  Activez un point de terminaison de métadonnées HTTP/GET pour votre service. Pour plus d’informations, consultez [Comment : publier des métadonnées pour un Code à l’aide du Service](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a>Pour ajouter un point de terminaison WCF compatible avec les clients du service Web ASP.NET dans un fichier de configuration  
  
1.  Créer un nouveau <xref:System.ServiceModel.BasicHttpBinding> configuration de liaison. Pour plus d’informations, consultez la [Comment : spécifier une liaison de Service dans la Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
2.  Éventuellement activer la sécurité de transport pour cette configuration de liaison de point de terminaison de service en définissant le mode de sécurité de la liaison <xref:System.ServiceModel.BasicHttpSecurityMode>. Pour plus d’informations, consultez [la sécurité de Transport](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3.  Configurez un nouveau point de terminaison d’application pour votre service à l’aide de la configuration de liaison que vous venez de créer. Pour plus d’informations sur l’ajout d’un point de terminaison dans un fichier de configuration, consultez le [Comment : créer un point de terminaison de Service dans la Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
4.  Activez un point de terminaison de métadonnées HTTP/GET pour votre service. Pour plus d’informations, consultez la [Comment : publier des métadonnées pour un Service à l’aide d’un fichier de Configuration](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
## <a name="example"></a>Exemple  
 L'exemple de code ci-dessous montre comment ajouter un point de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui est compatible avec les clients du service Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dans du code, ainsi que dans des fichiers de configuration.  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
  
 <!-- TODO: review snippet reference [!code[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/common/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  -->  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer un point de terminaison dans le Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)   
 [Comment : publier les métadonnées d’un Service à l’aide de Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)   
 [Comment : spécifier une liaison de Service dans la Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)   
 [Comment : créer un point de terminaison de Service dans la Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)   
 [Comment : publier les métadonnées d’un Service à l’aide d’un fichier de Configuration](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)   
 [Sécurité de transport](../../../../docs/framework/wcf/feature-details/transport-security.md)   
 [À l’aide de métadonnées](../../../../docs/framework/wcf/feature-details/using-metadata.md)