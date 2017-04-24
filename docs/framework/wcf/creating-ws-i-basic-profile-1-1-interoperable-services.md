---
title: "Cr&#233;ation de services pouvant interagir avec le profil Basic Profile 1.1 de WS-I | Microsoft Docs"
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
  - "configuration (WCF), services interopérables"
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Cr&#233;ation de services pouvant interagir avec le profil Basic Profile 1.1 de WS-I
Pour configurer un point de terminaison de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] afin qu'il puisse interagir avec les clients du service Web [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] :  
  
-   Utilisez le <xref:System.ServiceModel.BasicHttpBinding?displayProperty=fullName> type que le type de liaison pour le point de terminaison de votre service.  
  
-   N’utilisez pas les fonctionnalités de rappel et de contrat de session, ni les comportements de transaction sur votre point de terminaison de service  
  
 Vous pouvez éventuellement activer la prise en charge du protocole HTTPS et de l’authentification du client au niveau du transport sur la liaison.  
  
 Les fonctionnalités suivantes de la <xref:System.ServiceModel.BasicHttpBinding> classe requièrent des fonctionnalités au-delà de WS-I Basic Profile 1.1 :  
  
-   Encodage des messages Message Transmission Optimization Mechanism (MTOM) contrôlée par le <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=fullName> propriété. Laissez cette propriété à sa valeur par défaut, qui est <xref:System.ServiceModel.WSMessageEncoding?displayProperty=fullName> à ne pas utiliser MTOM.  
  
-   Sécurité du message contrôlée par le <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=fullName> valeur fournit la prise en charge de WS-Security conforme à WS-I Basic Security Profile 1.0. Laissez cette propriété à sa valeur par défaut, qui est <xref:System.ServiceModel.SecurityMode?displayProperty=fullName> à ne pas utiliser WS-Security.  
  
 Pour rendre les métadonnées pour un [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service disponible pour [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], utilisez les outils de génération de clients de service Web : [Web Services Description Language Tool (Wsdl.exe)](http://msdn.microsoft.com/fr-fr/b9210348-8bc2-4367-8c91-d1a04b403e88), [outil Web Services Discovery Tool (Disco.exe)](http://msdn.microsoft.com/fr-fr/acd88078-c581-42bc-94ca-6633e2851979)et `Add Web Reference` fonctionnalité dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]; vous devez activer la publication de métadonnées. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Points de terminaison](../../../docs/framework/wcf/publishing-metadata-endpoints.md).  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L'exemple de code ci-dessous montre comment ajouter un point de terminaison [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] qui est compatible avec les clients du service Web [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] dans du code, ainsi que dans des fichiers de configuration.  
  
### <a name="code"></a>Code  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
  
 <!-- TODO: review snippet reference [!code[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/common/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  -->  
  
## <a name="see-also"></a>Voir aussi  
 [Interopérabilité avec les Services Web ASP.NET](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)