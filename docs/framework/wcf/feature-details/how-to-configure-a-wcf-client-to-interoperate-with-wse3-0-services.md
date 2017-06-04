---
title: "Comment&#160;: configurer un client WCF pour interagir avec les services WSE&#160;3.0 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Comment&#160;: configurer un client WCF pour interagir avec les services WSE&#160;3.0
Les clients [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sont compatible au niveau câble avec les services Web Services Enhancements 3.0 for Microsoft .NET (WSE) lorsque les clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont configurés pour utiliser la version d'août 2004 de la spécification WS-Addressing.  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a>Configurer un client WCF pour interagir avec un service Web WSE 3.0  
  
1.  Exécutez le [Service Model Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour créer un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client pour le service Web WSE 3.0.  
  
     Pour un service Web WSE 3.0, une classe de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est créée.  
  
     Pour plus d’informations sur la création d’un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, consultez le [Comment : créer un Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Créez une classe qui représente une liaison pouvant communiquer avec les services Web WSE 3.0.  
  
     La classe suivante fait partie de la [interopérabilité avec WSE](http://msdn.microsoft.com/fr-fr/f6816861-96a0-45f9-8736-8e4e82cd3a41) exemple.  
  
    1.  Créez une classe qui dérive de la <xref:System.ServiceModel.Channels.Binding> classe.  
  
         L’exemple de code suivant crée une classe nommée `WseHttpBinding` qui dérive de la <xref:System.ServiceModel.Channels.Binding> classe.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Ajoutez à la classe des propriétés spécifiant l'assertion clé en main WSE, si des clés dérivées sont requises, si des sessions sécurisées sont utilisées, si des confirmations de signature sont requises, et les paramètres de protection des messages.  
  
         L’exemple de code suivant définit `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` propriétés qui spécifient l’assertion clé en main WSE, si des clés dérivées sont requises, si des sessions sécurisées sont utilisées, si des confirmations de signature sont requises et les paramètres de protection des messages, respectivement.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  Remplacer la <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> pour définir les propriétés de liaison.  
  
         L'exemple de code suivant spécifie le transport, l'encodage de message et les paramètres de protection des messages en obtenant les valeurs des propriétés `SecurityAssertion` et `MessageProtectionOrder`.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  Dans le code d’application cliente, ajoutez le code pour définir les propriétés de la liaison.  
  
     L'exemple de code suivant spécifie que le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] doit utiliser l'authentification et la protection des messages telles que définies par l'assertion de sécurité clé en main `AnonymousForCertificate` WSE 3.0. En outre, des sessions sécurisées et des clés dérivées sont requises.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant définit une liaison personnalisée qui expose des propriétés correspondant à celles d’une assertion de sécurité clé en main WSE 3.0. Puis la liaison personnalisée, nommée `WseHttpBinding`, est utilisée pour spécifier les propriétés de liaison pour un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.Binding>   
 [Interopérabilité avec WSE](http://msdn.microsoft.com/fr-fr/f6816861-96a0-45f9-8736-8e4e82cd3a41)