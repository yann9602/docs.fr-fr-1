---
title: "Sous-syst&#232;me approuv&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Sous-syst&#232;me approuv&#233;
Un client accède à un ou plusieurs services Web distribués sur un réseau.Les services Web sont conçus afin que l'accès aux ressources supplémentaires \(telles que les bases de données ou autres services Web\) soit encapsulé dans la logique métier du service Web.Ces ressources doivent être protégées contre tout accès non autorisé.L'illustration suivante présente un processus de sous\-système approuvé.  
  
 ![Sous&#45;système approuvé](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc\_TrustedSubsystemc")  
  
 Les étapes suivantes décrivent le processus de sous\-système approuvé tel qu'il est présenté :  
  
1.  Le client envoie une demande au sous\-système approuvé, accompagnée des informations d'identification.  
  
2.  Le sous\-système approuvé authentifie et autorise l'utilisateur.  
  
3.  Le sous\-système approuvé envoie un message de demande à la ressource distante.Cette demande est accompagnée des informations d'identification du sous\-système approuvé \(ou le compte de service sous lequel le processus de sous\-système approuvé est exécuté\).  
  
4.  La ressource principale authentifie et autorise le sous\-système approuvé.Elle traite ensuite la demande et envoie une réponse au sous\-système approuvé.  
  
5.  Le sous\-système approuvé traite la réponse et envoie sa propre réponse au client.  
  
|Caractéristique|Description|  
|---------------------|-----------------|  
|Mode de sécurité|Message|  
|Interopérabilité|[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uniquement.|  
|Authentification \(service\)|Le service de jeton de sécurité authentifie et autorise des clients.|  
|Authentification \(client\)|Le sous\-système approuvé authentifie le client et la ressource authentifie le service du sous\-système approuvé.|  
|Intégrité|Oui|  
|Confidentialité|Oui|  
|Transport|HTTP entre client et le service du sous\-système approuvé.<br /><br /> NET.TCP entre le service du sous\-système approuvé et la ressource \(service principal\).|  
|Liaison|<xref:System.ServiceModel.WSHttpBinding> et <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|  
  
## Ressource \(service principal\)  
  
### Code  
 Le code suivant indique comment créer un point de terminaison de service pour la ressource, qui utilise la sécurité de transport sur le protocole de transport TCP.  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### Configuration  
 La configuration suivante configure le même point de terminaison en utilisant la configuration.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.BackendService"  
               behaviorConfiguration="BackendServiceBehavior">  
        <endpoint address="net.tcp://localhost.com:8001/BackendService"  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="BackendServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, BackendService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## Sous\-système approuvé  
  
### Code  
 Le code suivant indique comment créer un point de terminaison de service pour le sous\-système approuvé qui utilise la sécurité de message sur le protocole HTTP ainsi qu'un nom d'utilisateur et un mot de passe pour l'authentification.  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 Le code suivant affiche un service dans un sous\-système approuvé qui communique avec un service principal en utilisant la sécurité de transport sur le protocole de transport TCP.  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### Configuration  
 La configuration suivante configure le même point de terminaison en utilisant la configuration.Notez les deux liaisons : l'une sécurise le service hébergé dans le sous\-système approuvé et l'autre communique entre le sous\-système approuvé et le service principal.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.FacadeService"  
               behaviorConfiguration="FacadeServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/FacadeService"/>  
          </baseAddresses>  
        </host>  
        <endpoint address="http://localhost:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <client>  
      <endpoint name=""   
                address="net.tcp://contoso.com:8001/BackendService"  
                binding="customBinding"  
                bindingConfiguration="ClientBinding"  
                contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
      <customBinding>  
        <binding name="ClientBinding">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="FacadeServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                storeLocation="LocalMachine"  
                                storeName="My"  
                                x509FindType="FindBySubjectName" />  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, FacadeService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## Client  
  
### Code  
 Le code suivant indique comment créer le client qui communique avec le sous\-système approuvé en utilisant la sécurité de message sur le protocole HTTP ainsi qu'un nom d'utilisateur et un mot de passe pour l'authentification.  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### Configuration  
 Le code suivant configure le client pour qu'il utilise la sécurité de message sur le protocole HTTP ainsi qu'un nom d'utilisateur et un mot de passe pour l'authentification.Le nom d'utilisateur et le mot de passe peuvent uniquement être spécifiés à l'aide du code \(cela n'est pas configurable\).  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <client>  
        <endpoint name=""   
                  address="http://www.cohowinery.com:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientUserNameBehavior"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientUserNameBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## Voir aussi  
 [Vue d'ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [Modèle de sécurité pour Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)