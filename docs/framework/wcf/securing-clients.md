---
title: "S&#233;curisation des clients | Microsoft Docs"
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
  - "clients (WCF), considérations sur la sécurité"
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
caps.latest.revision: 22
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 22
---
# S&#233;curisation des clients
Dans [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], le service dicte les conditions de sécurité pour les clients.Autrement dit, le service spécifie quel mode de sécurité utiliser, et si le client doit fournir ou non une information d'identification.Le processus de la sécurisation d'un client, par conséquent, est simple : utilisez les métadonnées obtenues depuis le service \(s'il est publié\) et générez un client.Les métadonnées spécifient comment configurer le client.Si le service exige que le client fournisse une information d'identification, vous devez obtenir une information d'identification qui correspond à la spécification.Cette rubrique décrit en détail le processus.[!INCLUDE[crabout](../../../includes/crabout-md.md)] la création d'un service sécurisé, consultez [Sécurisation de services](../../../docs/framework/wcf/securing-services.md).  
  
## Le service spécifie la sécurité  
 Par défaut, les fonctionnalités de sécurité des liaisons [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sont activées.\(Exception : <xref:System.ServiceModel.BasicHttpBinding>.\) Par conséquent, si le service a été créé à l'aide de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], il est plus probable qu'il implémente la sécurité pour garantir l'identification, la confidentialité et l'intégrité.Dans ce cas, les métadonnées que le service fournit indiqueront ce qu'il faut pour établir un canal de communication sécurisé.Si les métadonnées du service n'incluent pas de conditions de sécurité, il n'y a aucun moyen d'imposer une méthode de sécurité, telle que SSL \(Secure Sockets Layer\) sur HTTP, sur un service.Toutefois, si le service exige que le client fournisse une information d'identification, le développeur, le responsable du déploiement ou l'administrateur client doit fournir l'information d'identification réelle que le client utilisera pour s'identifier auprès du service.  
  
## Obtention des métadonnées  
 Lors de la création d'un client, la première étape est d'obtenir les métadonnées pour le service avec lequel le client communiquera.Cette opération peut être effectuée de deux façons.En premier lieu, si le service publie un point de terminaison d'échange de métadonnées \(MEX\) ou rend ses métadonnées disponibles sur HTTP ou HTTPS, vous pouvez télécharger les métadonnées à l'aide de [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), qui génère à la fois des fichiers de code pour un client ainsi qu'un fichier de configuration.\([!INCLUDE[crabout](../../../includes/crabout-md.md)] l'utilisation de l'outil, consultez [Accès aux services à l'aide d'un client WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).\) Si le service ne publie pas de point de terminaison MEX et ne rend pas ses métadonnées disponibles sur HTTP ou HTTPS, vous devez contacter le créateur du service pour obtenir la documentation qui décrit les conditions de sécurité et les métadonnées.  
  
> [!IMPORTANT]
>  Il est recommandé de vérifier que les métadonnées proviennent d'une source fiable et qu'elles n'ont pas été falsifiées.Les métadonnées récupérées à l'aide du protocole HTTP sont envoyées en texte clair et peuvent être falsifiées.Si le service utilise les propriétés <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> et <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>, utilisez l'URL que le créateur du service vous a fournie pour télécharger les données à l'aide du protocole HTTPS.  
  
## Validation de la sécurité  
 Les sources de métadonnées peuvent être divisées en deux catégories principales : les sources fiables et les sources non fiables.Si vous faites confiance à une source et avez téléchargé le code client et d'autres métadonnées depuis le point de terminaison MEX sécurisé de cette source, vous pouvez générer le client, lui fournir les informations d'identification correctes et l'exécuter sans inquiétude.  
  
 Toutefois, si vous choisissez de télécharger un client et des métadonnées à partir d'une source dont vous savez peu de choses, veillez à valider les mesures de sécurité que le code utilise.Par exemple, vous ne devez pas créer un client qui envoie vos informations personnelles ou financières à un service à moins que le service n'exige confidentialité et intégrité \(au strict minimum\).Vous devez faire confiance au propriétaire du service au point d'être disposé à lui divulguer de telles informations car elles seront visibles par le propriétaire.  
  
 En règle générale, lorsque vous utilisez du code et des métadonnées provenant d'une source non fiable, vérifiez le code et métadonnées pour vous assurer qu'ils répondent au niveau de sécurité exigé.  
  
## Définition de l'information d'identification d'un client  
 La définition de l'information d'identification d'un client s'effectue en deux étapes :  
  
1.  Déterminez le *type d'information d'identification du client* que le service requiert.Pour cela, vous avez le choix entre deux méthodes.En premier lieu, si vous disposez de la documentation du créateur du service, celle\-ci doit spécifier le type d'information d'identification du client \(le cas échéant\) que le service requiert.En second lieu, si vous disposez uniquement d'un fichier de configuration généré par l'outil Svcutil.exe, vous pouvez examiner les liaisons individuelles pour déterminer quel type d'information d'identification est requis.  
  
2.  Spécifiez l'information d'identification effective du client.L'information d'identification effective du client est appelée *valeur d'information d'identification du client* pour la distinguer du type.Par exemple, si le type d'information d'identification du client spécifie un certificat, vous devez fournir un certificat X.509 publié par une autorité de certification que le service approuve.  
  
### Détermination du type d'information d'identification du client  
 Si vous disposez du fichier de configuration que l'outil Svcutil.exe a généré, examinez la section [\<liaisons\>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) pour déterminer quel type d'information d'identification du client est requis.Dans la section, des éléments de liaison spécifient les conditions de sécurité.Examinez en particulier l'élément \<sécurité\> de chaque de liaison.Cet élément inclut l'attribut `mode`, auquel vous pouvez affecter l'une de trois valeurs possibles \(`Message`, `Transport` ou `TransportWithMessageCredential`\).La valeur de l'attribut détermine le mode, et le mode détermine quel élément enfant est significatif.  
  
 L'élément  `<security>` peut ou contenir un élément `<transport>` ou `<message>` , ou les deux.L'élément significatif est celui qui correspond au mode de sécurité.Par exemple, le code suivant spécifie que le mode de sécurité est `"Message"`, et le type d'information d'identification du client pour l'élément `<message>` est `"Certificate"`.Dans ce cas, l'élément `<transport>` peut être ignoré.Toutefois, l'élément `<message>` spécifie qu'un certificat X.509 doit être fourni.  
  
```  
<wsHttpBinding>  
    <binding name="WSHttpBinding_ICalculator">  
       <security mode="Message">  
           <transport clientCredentialType="Windows"   
                      realm="" />  
           <message clientCredentialType="Certificate"   
                    negotiateServiceCredential="true"  
                    algorithmSuite="Default"   
                    establishSecurityContext="true" />  
       </security>  
    </binding>  
</wsHttpBinding>  
```  
  
 Notez que si l'attribut `clientCredentialType` a la valeur `"Windows"`, comme dans l'exemple suivant, vous n'avez pas besoin de fournir une valeur d'information d'identification effective.Cela est dû au fait que la sécurité intégrée de Windows fournit l'information d'identification effective \(un jeton Kerberos\) de la personne qui exécute le client.  
  
```  
<security mode="Message">  
    <transport clientCredentialType="Windows "   
        realm="" />  
</security>  
```  
  
### Définition de la valeur d'information d'identification du client  
 S'il est déterminé que le client doit fournir une information d'identification, utilisez la méthode appropriée pour configurer le client.Par exemple, pour définir un certificat client, utilisez la méthode <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>.  
  
 Le certificat X.509 est une forme courante d'information d'identification.Vous pouvez fournir l'information d'identification de deux manières :  
  
-   En la programmant dans votre code client \(à l'aide de la méthode `SetCertificate`\).  
  
 En ajoutant une section [\<comportements\>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) du fichier de configuration pour le client et en utilisant l'élément `clientCredentials` \(illustré ci\-dessous\).  
  
#### Définition d'une valeur \<clientCredentials\> dans du code  
 Pour définir une valeur [\<clientCredentials\>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) dans du code, vous devez accéder à la propriété <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> de la classe <xref:System.ServiceModel.ClientBase%601>.La propriété retourne un objet <xref:System.ServiceModel.Description.ClientCredentials> qui autorise l'accès à différents types d'informations d'identification, comme le montre le tableau suivant.  
  
|Propriété ClientCredential|Description|Remarques|  
|--------------------------------|-----------------|---------------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|Retourne un <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>.|Représente un certificat X.509 fourni par le client pour s'identifier auprès du service.|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|Retourne un <xref:System.ServiceModel.Security.HttpDigestClientCredential>.|Représente une information d'identification HTTP Digest.L'information d'identification est un hachage du nom d'utilisateur et du mot de passe.|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|Retourne un <xref:System.ServiceModel.Security.IssuedTokenClientCredential>.|Représente un jeton de sécurité personnalisé publié par un service de jeton de sécurité, utilisé communément dans les scénarios de fédération.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|Retourne un <xref:System.ServiceModel.Security.PeerCredential>.|Représente une information d'identification homologue pour la participation à une maille homologue sur un domaine Windows.|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|Retourne un <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>.|Représente un certificat X.509 fourni par le service dans une négociation hors bande.|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|Retourne un <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>.|Représente une paire nom d'utilisateur\/mot de passe.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|Retourne un <xref:System.ServiceModel.Security.WindowsClientCredential>.|Représente une information d'identification du client Windows \(une information d'identification Kerberos\).Les propriétés de la classe sont en lecture seule.|  
  
#### Définition d'une valeur \<clientCredentials\> dans la configuration  
 Les valeurs d'information d'identification sont spécifiées en utilisant un comportement de point de terminaison en tant qu'élément enfant de l'élément [\<clientCredentials\>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).L'élément utilisé dépend du type d'information d'identification du client.L'exemple suivant illustre la configuration pour définir un certificat X.509 à l'aide de \<[\<clientCertificate\>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).  
  
```  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myEndpointBehavior">  
          <clientCredentials>  
            <clientCertificate findvalue="myMachineName"   
            storeLocation="Current" X509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>              
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Pour définir l'information d'identification du client dans la configuration, ajoutez un élément [\<endpointBehaviors\>](../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) au fichier de configuration.En outre, l'élément de comportement ajouté doit être lié au point de terminaison du service à l'aide de l'attribut `behaviorConfiguration` de l'élément [\<endpoint\>](http://msdn.microsoft.com/fr-fr/13aa23b7-2f08-4add-8dbf-a99f8127c017) comme le montre l'exemple suivant.La valeur de l'attribut `behaviorConfiguration` doit correspondre à la valeur de l'attribut de comportement `name`.  
  
 `<configuration>`  
  
 `<system.serviceModel>`  
  
 `<client>`  
  
 `<endpoint address="http://localhost/servicemodelsamples/service.svc"`  
  
 `binding="wsHttpBinding"`  
  
 `bindingConfiguration="Binding1"`  
  
 `behaviorConfiguration="myEndpointBehavior"`  
  
 `contract="Microsoft.ServiceModel.Samples.ICalculator" />`  
  
 `</client>`  
  
 `</system.serviceModel>`  
  
 `</configuration>`  
  
> [!NOTE]
>  Certaines des valeurs d'information d'identification du client ne peuvent pas être définies à l'aide des fichiers de configuration de l'application, par exemple le nom d'utilisateur et le mot de passe, ou les valeurs d'utilisateur et de mot de passe Windows.Ces valeurs d'information d'identification peuvent être spécifiées dans du code uniquement.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] la définition de l'information d'identification du client, consultez [Comment : spécifier des valeurs d'informations d'identification du client](../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
> [!NOTE]
>  `ClientCredentialType` est ignoré lorsque `SecurityMode` a la valeur `"TransportWithMessageCredential",` comme le montre l'exemple de configuration suivant.  
  
```  
<wsHttpBinding>  
    <binding name="PingBinding">  
        <security mode="TransportWithMessageCredential"  >  
           <message  clientCredentialType="UserName"   
               establishSecurityContext="false"    
               negotiateServiceCredential="false" />  
           <transport clientCredentialType="Certificate"  />  
         </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>   
 <xref:System.ServiceModel.ClientBase%601>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>   
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>   
 [\<liaisons\>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)   
 [Outil Éditeur de configuration \(SvcConfigEditor.exe\)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)   
 [Sécurisation de services](../../../docs/framework/wcf/securing-services.md)   
 [Accès aux services à l'aide d'un client WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)   
 [Comment : spécifier des valeurs d'informations d'identification du client](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)   
 [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)   
 [Comment : spécifier le type d'informations d'identification du client](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)