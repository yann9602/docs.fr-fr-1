---
title: "Comment&#160;: cr&#233;er une session s&#233;curis&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sécurité [WCF], création d'une session"
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
caps.latest.revision: 10
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 10
---
# Comment&#160;: cr&#233;er une session s&#233;curis&#233;e
À l'exception de la liaison [\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), les liaisons fournies par le système dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utilisent automatiquement des sessions sécurisées lorsque la sécurité du message est activée.  
  
 Par défaut, les sessions sécurisées ne survivent pas à un serveur Web recyclé.  Lorsqu'une session sécurisée est établie, le client et le service mettent en cache la clé associée à la session sécurisée.  Lorsque les messages sont échangés, seul un identificateur de la clé mise en cache est échangé.  Si le serveur Web est recyclé, le cache est également recyclé, de sorte que le serveur Web ne peut pas récupérer la clé mise en cache pour l'identificateur.  Si cela arrive, une exception est retournée au client.  Les sessions sécurisées qui utilisent un jeton de contexte de sécurité avec état peuvent survivre au recyclage d'un serveur Web.  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'utilisation de SCT avec état dans une session sécurisée, consultez [Procédure : créer un jeton de contexte de sécurité pour une session sécurisée](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### Pour spécifier qu'un service utilise des sessions sécurisées à l'aide de l'une des liaisons fournies par le système  
  
-   Configurez un service pour utiliser une liaison fournie par le système qui prend en charge la sécurité de message.  
  
     À l'exception de la liaison [\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), lorsque les liaisons fournies par le système sont configurées pour utiliser la sécurité de message, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise automatiquement des sessions sécurisées.  Le tableau suivant répertorie les liaisons fournies par le système qui prennent en charge la sécurité de message et indique si la sécurité de message est le mécanisme de sécurité par défaut.  
  
    |Liaison fournie par le système|Élément de configuration|Sécurité de message activée par défaut|  
    |------------------------------------|------------------------------|--------------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Non|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Oui|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Oui|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Oui|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Non|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Non|  
  
     L'exemple de code suivant utilise la configuration pour spécifier une liaison nommée `wsHttpBinding_Calculator` qui utilise [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), la sécurité de message et les sessions sécurisées.  
  
    ```  
    <bindings>  
      <WSHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </WSHttpBinding>  
    </bindings>  
    ```  
  
     L'exemple de code suivant spécifie que [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), la sécurité de message et les sessions sécurisées sont utilisés pour sécuriser le service `secureCalculator`.  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  Les sessions sécurisées peuvent être désactivées pour [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) en affectant à l'attribut `establishSecurityContext` la valeur `false`.  Pour les autres liaisons fournies par le système, les sessions sécurisées peuvent être désactivées uniquement en créant une liaison personnalisée.  
  
### Pour spécifier qu'un service utilise des sessions sécurisées à l'aide d'une liaison personnalisée  
  
-   Créez une liaison personnalisée qui spécifie que les messages SOAP sont protégés par une session sécurisée.  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la création d'une liaison personnalisée, consultez [Comment : personnaliser une liaison fournie par le système](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
     L'exemple de code suivant utilise la configuration pour spécifier une liaison personnalisée à laquelle les messages font appel dans une session sécurisée.  
  
    ```  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="customBinding_Calculator">  
          <security authenticationMode="SecureConversation" />  
          <secureConversationBootstrap authenticationMode="SspiNegotiated" />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
     L'exemple de code suivant crée une liaison personnalisée qui utilise le mode d'authentification <xref:System.ServiceModel.Configuration.AuthenticationMode> pour démarrer une session sécurisée.  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## Voir aussi  
 [Vue d'ensemble des liaisons WCF](../../../../docs/framework/wcf/bindings-overview.md)