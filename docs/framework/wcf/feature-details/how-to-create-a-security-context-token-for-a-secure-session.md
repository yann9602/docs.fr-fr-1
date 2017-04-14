---
title: "Proc&#233;dure&#160;: cr&#233;er un jeton de contexte de s&#233;curit&#233; pour une session s&#233;curis&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
caps.latest.revision: 14
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 14
---
# Proc&#233;dure&#160;: cr&#233;er un jeton de contexte de s&#233;curit&#233; pour une session s&#233;curis&#233;e
En utilisant un jeton de contexte de sécurité avec état \(SCT\) dans une session sécurisée, la session peut résister au service qui est recyclé.Par exemple, lorsqu'un SCT sans état est utilisé dans une session sécurisée et que les services IIS \(Internet Information Services\) sont réinitialisés, les données de session associées au service sont perdues.Ces données de session incluent un cache du jeton SCT.Ainsi, la prochaine fois qu'un client enverra au service un SCT sans état, une erreur sera retournée, parce que la clé associée au SCT ne peut pas être récupérée.Toutefois, si un SCT avec état est utilisé, la clé associée au SCT est contenue dans le SCT.Étant donné que la clé est contenue dans le SCT et donc contenue dans le message, la session sécurisée n'est pas affectée par le service qui est recyclé.Par défaut, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utilise des SCT sans état dans une session sécurisée.Cette rubrique détaille la manière d'utiliser des SCT avec état dans une session sécurisée.  
  
> [!NOTE]
>  Les SCT avec état ne peuvent pas être utilisés dans une session sécurisée qui implique un contrat dérivé de <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
> [!NOTE]
>  Pour les applications qui utilisent des SCT avec état dans une session sécurisée, l'identité de thread pour le service doit être un compte d'utilisateur ayant un profil utilisateur associé.Lorsque le service est exécuté sous un compte qui n'a pas de profil utilisateur, tel qu'un `Local Service`, une exception peut être levée.  
  
> [!NOTE]
>  Lorsque l'emprunt d'identité est requis sur Windows XP, utilisez une session sécurisée sans SCT avec état.Lorsque des SCT avec état sont utilisés avec l'emprunt d'identité, une <xref:System.InvalidOperationException> est levée.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Scénarios non pris en charge](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
### Pour utiliser des SCT avec état dans une session sécurisée  
  
-   Créez une liaison personnalisée qui spécifie que les messages SOAP sont protégés par une session sécurisée qui utilise un SCT avec état.  
  
    1.  Définissez une liaison personnalisée, en ajoutant un [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) au fichier de configuration pour le service.  
  
        ```  
        <customBinding>  
        ```  
  
    2.  Ajoutez un élément enfant [\<liaison\>](../../../../docs/framework/misc/binding.md) à [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Spécifiez un nom de liaison en affectant à l'attribut `name` un nom unique dans le fichier de configuration.  
  
        ```  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3.  Spécifiez le mode d'authentification pour les messages envoyés à et depuis ce service en ajoutant un élément enfant [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) à [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Spécifiez qu'une session sécurisée est utilisée en affectant à l'attribut `authenticationMode` la valeur `SecureConversation`.Spécifiez que des SCT avec état sont utilisés en affectant à l'attribut `requireSecurityContextCancellation` la valeur `false`.  
  
        ```  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4.  Spécifiez comment le client est authentifié pendant que la session sécurisée est établie en ajoutant un élément enfant [\<secureConversationBootstrap\>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) à [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Spécifiez comment le client est authentifié en définissant l'attribut `authenticationMode`.  
  
        ```  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5.  Spécifiez l'encodage des messages en ajoutant un élément d'encodage, tel que [\<textMessageEncoding\>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
        ```  
        <textMessageEncoding />  
        ```  
  
    6.  Spécifiez le transport en ajoutant un élément de transport, tel que [\<httpTransport\>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
        ```  
        <httpTransport />  
        ```  
  
     L'exemple de code suivant utilise la configuration pour spécifier une liaison personnalisée que les messages peuvent utiliser avec des SCT avec état dans une session sécurisée.  
  
    ```  
    <customBinding>  
      <binding name="StatefulSCTSecureSession">  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
          <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        </security>  
        <textMessageEncoding />  
        <httpTransport />  
      </binding>  
    </customBinding>  
    ```  
  
## Exemple  
 L'exemple de code suivant crée une liaison personnalisée qui utilise le mode d'authentification <xref:System.ServiceModel.Configuration.AuthenticationMode> pour démarrer une session sécurisée.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Lorsque l'authentification Windows est utilisée en association avec un SCT avec état, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne remplit pas la propriété <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> avec l'identité de l'appelant réel mais à la place il rend la propriété anonyme.Vu que la sécurité [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] doit recréer le contenu du contexte de sécurité du service pour chaque demande du SCT entrant, le serveur n'effectue pas le suivi de la session de sécurité en mémoire.Comme il est impossible de sérialiser l'instance <xref:System.Security.Principal.WindowsIdentity> dans le SCT, la propriété <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> retourne une identité anonyme.  
  
 La configuration suivante expose ce comportement.  
  
```  
<customBinding>  
  <binding name="Cancellation">  
       <textMessageEncoding />  
        <security   
            requireSecurityContextCancellation="false">  
              <secureConversationBootstrap />  
      </security>  
    <httpTransport />  
  </binding>  
</customBinding>  
  
```  
  
## Voir aussi  
 [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)