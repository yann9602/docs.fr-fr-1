---
title: "S&#233;curit&#233; de message avec un client Windows sans n&#233;gociation d&#39;informations d&#39;identification | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
caps.latest.revision: 18
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 18
---
# S&#233;curit&#233; de message avec un client Windows sans n&#233;gociation d&#39;informations d&#39;identification
Le scénario suivant montre un client et un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sécurisés par le protocole Kerberos.  
  
 Le service et le client appartiennent au même domaine ou domaines approuvés.  
  
> [!NOTE]
>  La différence entre ce scénario et [Sécurité de message avec un client Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) est qu'il ne négocie pas les informations d'identification du service avec le service avant d'envoyer le message d'application.  En outre, comme cette opération requiert le protocole Kerberos, ce scénario requiert un environnement de domaine Windows.  
  
 ![Sécurité des messages sans négociation des informations d'identification](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa\-2439\-4ef9\-92f4\-43c242d85d0d")  
  
|Caractéristique|Description|  
|---------------------|-----------------|  
|Mode de sécurité|Message|  
|Interopérabilité|Oui, WS\-Security avec des clients compatibles avec le profil de jeton Kerberos|  
|Authentification \(serveur\)|Authentification mutuelle du serveur et du client|  
|Authentification \(client\)|Authentification mutuelle du serveur et du client|  
|Intégrité|Oui|  
|Confidentialité|Oui|  
|Transport|HTTP|  
|Binding|<xref:System.ServiceModel.WSHttpBinding>|  
  
## Service  
 La configuration et le code ci\-dessous sont conçus pour s'exécuter indépendamment.  Effectuez l’une des opérations suivantes :  
  
-   Créez un service autonome à l'aide du code sans configuration.  
  
-   Créez un service à l'aide de la configuration fournie, mais ne définissez pas de point de terminaison.  
  
### Code  
 Le code ci\-dessous crée un point de terminaison de service qui utilise la sécurité de message.  Le code désactive la négociation des informations d'identification du service, et l'établissement d'un jeton de contexte de sécurité \(SCT\).  
  
> [!NOTE]
>  Pour utiliser le type d'informations d'identification Windows sans négociation, le compte d'utilisateur du service doit avoir accès au nom de principal du service \(SPN\) enregistré avec le domaine Active Directory.  Pour cela, deux solutions s'offrent à vous :  
  
1.  Utilisez le compte `NetworkService` ou `LocalSystem` pour exécuter votre service.  Comme ces comptes ont accès à l'ordinateur SPN établi lorsque l'ordinateur joint le domaine Active Directory, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère automatiquement l'élément SPN correct à l'intérieur du point de terminaison du service dans les métadonnées du service \(Web Services Description Language ou WSDL\).  
  
2.  Utilisez un compte de domaine Active Directory arbitraire pour exécuter votre service.  Dans ce cas, vous devez établir un nom de principal du service pour ce compte de domaine.  Une façon de procéder consiste à faire appel à l'utilitaire Setspn.exe.  Une fois que le nom de principal du service du compte du service a été créé, configurez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour publier ce nom de principal du service sur les clients du service par le biais de ses métadonnées \(WSDL\).  Cette opération s'effectue en définissant l'identité de point de terminaison pour le point de terminaison exposé, par le biais d'un fichier de configuration de l'application ou du code.  L'exemple suivant publie l'identité par programme.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] les SPN, le protocole Kerberos et Active Directory, consultez [Supplément technique Kerberos pour Windows](http://go.microsoft.com/fwlink/?LinkId=88330).  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] les identités de points de terminaison, consultez [Modes d'authentification SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 [!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
 [!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]  
  
### Configuration  
 La configuration ci\-dessous peut être utilisée à la place du code.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="KerberosBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator"   
                  listenUri="net.tcp://localhost/metadata" >  
         <identity>  
            <servicePrincipalName value="service_spn_name" />  
         </identity>  
        </endpoint>  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="KerberosBinding">  
          <security>  
            <message negotiateServiceCredential="false"   
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## Client  
 La configuration et le code ci\-dessous sont conçus pour s'exécuter indépendamment.  Effectuez l’une des opérations suivantes :  
  
-   Créez un client autonome à l'aide du code \(et du code client\).  
  
-   Créez un client qui ne définit pas d'adresse de point de terminaison.  Au lieu de cela, utilisez le constructeur client qui accepte le nom de configuration comme argument.  Par exemple :  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### Code  
 Le code ci\-dessous configure le client.  Le mode de sécurité a la valeur Message, et le type d'informations d'identification du client a la valeur Windows.  Notez que les propriétés <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> et <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> ont la valeur `false`.  
  
> [!NOTE]
>  Pour utiliser le type d'informations d'identification Windows sans négociation, le client doit être configuré avec le compte SPN du service avant de commencer la communication avec le service.  Le client utilise le nom de principal du service pour obtenir le jeton Kerberos afin d'authentifier et de sécuriser la communication avec le service.  L'exemple suivant montre comment configurer le client avec le nom principal du service.  Si vous utilisez l'[Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer le client, le nom principal du service sera propagé automatiquement au client des métadonnées du service \(WSDL\), si les métadonnées du service contiennent cette information.  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la configuration du service pour inclure son SPN dans ses métadonnées, consultez la section « Service » plus loin dans cette rubrique.  
>   
>  Pour plus d'informations sur les SPN, Kerberos et Active Directory, consultez [Supplément technique Kerberos pour Windows](http://go.microsoft.com/fwlink/?LinkId=88330).  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] les identités de point de terminaison, consultez la rubrique [Modes d'authentification SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 [!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
 [!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]  
  
### Configuration  
 Le code ci\-dessous configure le client.  Notez que l'élément [\<servicePrincipalName\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) doit être défini pour correspondre au nom principal du service enregistré pour le compte du service dans le domaine Active Directory.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Windows"   
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <servicePrincipalName value="service_spn_name" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## Voir aussi  
 [Vue d'ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [Identité du service et authentification](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [Modèle de sécurité pour Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)