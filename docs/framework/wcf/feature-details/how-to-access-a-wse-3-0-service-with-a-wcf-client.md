---
title: "Comment : accéder à un service WSE 3.0 avec un client WCF"
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
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c70b7df47cb3f367318fb388ceda2163f538cb32
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a>Comment : accéder à un service WSE 3.0 avec un client WCF
Les clients [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sont compatibles au niveau câble avec les services WSE (Web Services Enhancements) 3.0 for Microsoft .NET lorsque les clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont configurés pour utiliser la version d'août 2004 de la spécification WS-Addressing. Toutefois, les services WSE 3.0 ne pas prennent en charge le protocole d’échange (MEX) métadonnées, par conséquent, lorsque vous utilisez la [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour créer un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] classe de client, les paramètres de sécurité ne sont pas appliquées à le texte généré [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client. Par conséquent, vous devez spécifier les paramètres de sécurité que le service WSE 3.0 requiert une fois le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] généré.  
  
 Vous pouvez appliquer ces paramètres de sécurité en utilisant une liaison personnalisée pour prendre en compte les spécifications du service WSE 3.0 et les spécifications interopérables entre un service WSE 3.0 et un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Ces spécifications d'interopérabilité incluent l'utilisation précédemment mentionnée de la version d'août 2004 de la spécification WS-Addressing et la protection des messages par défaut WSE 3.0 de <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>. La protection des messages par défaut pour [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Cette rubrique explique comment créer une liaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui interagit avec un service WSE 3.0. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit également un exemple qui incorpore cette liaison. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Cet exemple, consultez [interopérabilité avec les Services Web ASMX](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md).  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a>Pour accéder à un service Web WSE 3.0 avec un client WCF  
  
1.  Exécutez le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour créer un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client pour le service Web WSE 3.0.  
  
     Pour un service Web WSE 3.0, un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est créé. WSE 3.0 ne prenant pas en charge le protocole MEX, vous ne pouvez pas utiliser l'outil pour récupérer les conditions de sécurité pour le service Web. Le développeur d'applications doit ajouter les paramètres de sécurité pour le client.  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Création d’un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, consultez le [Comment : créer un Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Créez une classe qui représente une liaison pouvant communiquer avec les services Web WSE 3.0.  
  
     La classe suivante fait partie de la [il interagit avec WSE](http://msdn.microsoft.com/en-us/f6816861-96a0-45f9-8736-8e4e82cd3a41) exemple :  
  
    1.  Créez une classe qui dérive de la classe <xref:System.ServiceModel.Channels.Binding>.  
  
         L'exemple de code suivant crée une classe nommée `WseHttpBinding` qui dérive de la classe <xref:System.ServiceModel.Channels.Binding>.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Ajoutez à la classe des propriétés spécifiant l'assertion clé en main WSE utilisée par le service WSE, si des clés dérivées sont requises, si des sessions sécurisées sont utilisées, si des confirmations de signature sont requises, ainsi que les paramètres de protection des messages. Dans WSE 3.0, une assertion clé en main spécifie les conditions de sécurité pour un client ou un service Web (similaire au mode d'authentification d'une liaison dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]).  
  
         L'exemple de code suivant définit les propriétés `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext` et `MessageProtectionOrder` qui spécifient l'assertion clé en main WSE, si des clés dérivées sont requises, si des sessions sécurisées sont utilisées, si des confirmations de signature sont requises, ainsi que les paramètres de protection des messages, respectivement.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  Substituez la méthode <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> pour définir les propriétés de la liaison.  
  
         L'exemple de code suivant spécifie le transport, l'encodage de message et les paramètres de protection des messages en obtenant les valeurs des propriétés `SecurityAssertion` et `MessageProtectionOrder`.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  Dans le code d’application cliente, ajoutez le code pour définir les propriétés de la liaison.  
  
     L'exemple de code suivant spécifie que le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] doit utiliser l'authentification et la protection des messages telles que définies par l'assertion de sécurité clé en main `AnonymousForCertificate` WSE 3.0. En outre, des sessions sécurisées et des clés dérivées sont requises.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant définit une liaison personnalisée qui expose des propriétés correspondant à celles d’une assertion de sécurité clé en main WSE 3.0. Cette liaison personnalisée, qui est appelée `WseHttpBinding`, est utilisée pour spécifier les propriétés de liaison d'un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui communique avec l'exemple de Démarrage rapide WSE 3.0 WSSecurityAnonymous.  
  
  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.Binding>  
 [Il interagit avec WSE](http://msdn.microsoft.com/en-us/f6816861-96a0-45f9-8736-8e4e82cd3a41)
