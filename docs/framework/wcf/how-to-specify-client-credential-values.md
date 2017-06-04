---
title: "Comment&#160;: sp&#233;cifier des valeurs d&#39;informations d&#39;identification du client | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
caps.latest.revision: 28
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 28
---
# Comment&#160;: sp&#233;cifier des valeurs d&#39;informations d&#39;identification du client
Grâce à [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], le service peut spécifier comment un client est authentifié auprès du service.  Par exemple, un service peut stipuler que le client soit authentifié avec un certificat.  
  
### Pour déterminer le type d'informations d'identification du client  
  
1.  Récupérez les métadonnées à partir du point de terminaison des métadonnées du service.  Les métadonnées se composent généralement de deux fichiers : le code client dans le langage de programmation de votre choix \(la valeur par défaut est Visual C\#\) et un fichier de configuration XML.  L'une des manières permettant de récupérer des métadonnées consiste à utiliser l'outil Svcutil.exe pour retourner le code client et la configuration cliente.  Pour plus d'informations, consultez [Récupération de métadonnées](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) et [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
2.  Ouvrez le fichier de configuration XML.  Si vous utilisez l'outil Svcutil.exe, le nom par défaut du fichier est Output.config.  
  
3.  Recherchez l'élément **\<security\>** avec l'attribut **mode** \(**\<security mode \=** `MessageOrTransport`**\>** où `MessageOrTransport` est défini avec l'un des modes de sécurité.  
  
4.  Recherchez l'élément enfant qui correspond à la valeur de mode.  Par exemple, si le mode est défini sur **Message**, recherchez l'élément **\<message\>** contenu dans l'élément **\<sécurité\>**.  
  
5.  Notez la valeur affectée à l'attribut **clientCredentialType**.  La valeur réelle dépend du mode utilisé, du transport ou du message.  
  
 Le code XML suivant montre la configuration pour un client utilisant la sécurité du message et nécessitant un certificat pour authentifier le client.  
  
```  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## Exemple : mode de transport TCP avec certificat comme informations d'identification du client  
 Cet exemple définit le mode de sécurité sur le mode Transport et définit la valeur d'informations d'identification du client sur un certificat X.509.  Les procédures suivantes montrent comment définir la valeur d'information d'identification du client sur le client dans le code et dans la configuration.  Elles supposent que vous avez utilisé l'[Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour retourner les métadonnées \(code et configuration\) du service.  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Comment : créer un client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
#### Pour spécifier la valeur d'information d'identification du client sur le client dans le code  
  
1.  Utilisez l'[Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer le code et la configuration du service.  
  
2.  Créez une instance du client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] à l'aide du code généré.  
  
3.  Sur la classe de client, affectez à la propriété <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> de la classe <xref:System.ServiceModel.ClientBase%601> une valeur appropriée.  Cet exemple affecte à la propriété un certificat X.509 à l'aide de la méthode <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> de la classe <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>.  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     Vous pouvez utiliser n'importe lesquelles des énumérations de la classe <xref:System.Security.Cryptography.X509Certificates.X509FindType>.  Le nom du sujet est utilisé ici au cas où le certificat serait modifié \(en raison d'une date d'expiration\).  L'utilisation du nom du sujet permet à l'infrastructure de retrouver le certificat.  
  
#### Pour spécifier la valeur d'information d'identification du client sur le client dans la configuration  
  
1.  Ajoutez un élément [\<comportement\>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) à l'élément [\<comportements\>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).  
  
2.  Ajoutez un élément [\<clientCredentials\>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) à l'élément [\<comportements\>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).  Assurez\-vous d'affecter à l'attribut `name` requis une valeur appropriée.  
  
3.  Ajoutez un élément [\<clientCertificate\>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) à l'élément [\<clientCredentials\>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).  
  
4.  Affectez aux attributs suivants des valeurs appropriées : `storeLocation`, `storeName`, `x509FindType` et `findValue`, comme illustré dans le code suivant.  [!INCLUDE[crabout](../../../includes/crabout-md.md)] les certificats, consultez [Utilisation des certificats](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
    ```  
    <behaviors>  
       <endpointBehaviors>  
          <behavior name="endpointCredentialBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="Contoso.com"   
                                 storeLocation="LocalMachine"  
                                 storeName="TrustedPeople"  
                                 x509FindType="FindBySubjectName" />  
            </clientCredentials>  
          </behavior>  
       </endpointBehaviors>  
    </behaviors>  
    ```  
  
5.  Lorsque vous configurez le client, spécifiez le comportement en définissant l'attribut `behaviorConfiguration` de l'élément `<endpoint>`, comme illustré dans le code suivant.  L'élément de point de terminaison est un enfant de l'élément [\<client\>](../../../docs/framework/configure-apps/file-schema/wcf/client.md).  Spécifiez également le nom de la configuration de liaison en affectant à l'attribut `bindingConfiguration` la liaison pour le client.  Si vous utilisez un fichier de configuration généré, le nom de la liaison est généré automatiquement.  Dans cet exemple, le nom est `"tcpBindingWithCredential"`.  
  
    ```  
    <client>  
      <endpoint name =""  
                address="net.tcp://contoso.com:8036/aloha"  
                binding="netTcpBinding"  
                bindingConfiguration="tcpBindingWithCredential"  
                behaviorConfiguration="endpointCredentialBehavior" />  
    </client>  
    ```  
  
## Voir aussi  
 <xref:System.ServiceModel.NetTcpBinding>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>   
 <xref:System.ServiceModel.ClientBase%601>   
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>   
 [Programmation de la sécurité dans WCF](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)   
 [Sélection d'un type d'informations d'identification](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)   
 [Utilisation des certificats](../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [Comment : créer un client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)   
 [\<netTcpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)   
 [\<sécurité\>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)   
 [\<message\>](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)   
 [\<comportement\>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)   
 [\<comportements\>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)   
 [\<clientCertificate\>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)   
 [\<clientCredentials\>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)