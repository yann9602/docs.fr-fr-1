---
title: "&lt;message&gt; de &lt;netMsmqBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;message&gt; de &lt;netMsmqBinding&gt;
Définit les paramètres de sécurité des messages SOAP sur cette liaison `netMsmqBinding`.  
  
## Syntaxe  
  
```  
  
<netMsmqBinding>  
    <binding>  
      <security>  
         <message   
                      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
    </security>  
</netMsmqBinding>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|algorithmSuite|Définit le chiffrement des messages et algorithmes de clé de type WRAP utilisés pour obtenir la sécurité basée sur des messages pour les messages envoyés via le transport MSMQ.<br /><br /> La valeur par défaut est `Aes256`.  Cet attribut est de type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|clientCredentialType|Spécifie le type d'information d'identification à utiliser lors de l'exécution de l'authentification du client pour les messages envoyés via le transport MSMQ.  Les valeurs valides sont les suivantes :<br /><br /> -   None : Permet au service d'interagir avec les clients anonymes.  Ni le service ni le client n'exigent d'informations d'identification.<br />-   Windows : permet aux échanges SOAP d'être sous le contexte authentifié d'informations d'identification Windows.  Exécute toujours une authentification basée sur Kerberos.<br />-   UserName : permet au service d'exiger que le client soit authentifié à l'aide d'informations d'identification UserName.  L'information d'identification dans ce cas doit être spécifiée à l'aide du comportement `clientCredentials` **Caution:**  [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ne prend pas en charge l'envoi d'un mot de passe Digest ou la dérivation de clés à l'aide du mot de passe et l'utilisation de telles clés pour la sécurité de message.  [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] s'assure ainsi que l'échange est sécurisé lors de l'utilisation d'informations d'identification UserName.  Ce mode requiert que le certificat de service soit spécifié côté client à l'aide du comportement `clientCredential` et de `serviceCertificate`. <br /><br /> -   Certificate : permet au service d'exiger que le client soit authentifié à l'aide d'un certificat.  Les informations d'identification du client dans ce cas doivent être spécifiées à l'aide du comportement `clientCredentials`.  Les informations d'identification du service dans ce cas doivent être spécifiées à l'aide du comportement `clientCredentials` en spécifiant le `serviceCertificate`.<br />-   CardSpace : autorise le service à imposer que le client soit authentifié à l'aide d'un CardSpace.  Le `serviceCertiifcate` doit être configuré dans le comportement `clientCredential`.<br /><br /> La valeur par défaut est `Windows`.  Cet attribut est de type <xref:System.ServiceModel.MessageCredentialType>.|  
  
### Éléments enfants  
 None  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sécurité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Définit les paramètres de sécurité d'une liaison.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>   
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>   
 <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>   
 <xref:System.ServiceModel.MessageSecurityOverMsmq>   
 [Files d'attente dans WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/fr-fr/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)