---
title: "Liaisons et s&#233;curit&#233; | Microsoft Docs"
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
  - "liaisons (WCF)"
  - "liaisons (WCF), sécurité"
  - "sécurité WCF"
  - "Windows Communication Foundation, sécurité"
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
caps.latest.revision: 42
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 42
---
# Liaisons et s&#233;curit&#233;
Les liaisons fournies par le système incluses avec [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] permettent de programmer rapidement des applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].À une exception près, la méthode de sécurité par défaut de toutes les liaisons est activée.Cette rubrique vous permet de sélectionner la liaison appropriée à vos besoins de sécurité.  
  
 Pour une vue d'ensemble de la sécurité [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [Vue d'ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] la programmation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide de liaisons, consultez [Programmation de la sécurité dans WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md).  
  
 Si vous avez déjà sélectionné une liaison, de plus amples informations sur les comportements au moment de l'exécution associés sont disponibles dans [Comportements de sécurité](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
 Certaines fonctions de sécurité ne sont pas programmables à l'aide des liaisons fournies par le système.Pour davantage de contrôle à l'aide d'une liaison personnalisée, consultez [Fonctionnalités de sécurité avec des liaisons personnalisées](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## Fonctions de sécurité des liaisons  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inclut un certain nombre de liaisons fournies par le système qui répondent à la plupart des besoins.Si une liaison spécifique ne suffit pas, vous pouvez également créer une liaison personnalisée.Pour obtenir une liste des liaisons fournies par le système, consultez [Liaisons fournies par le système](../../../../docs/framework/wcf/system-provided-bindings.md).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les liaisons personnalisées, consultez [Liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 Chaque liaison dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] comporte deux formulaires : l'un en tant qu'API et l'autre en tant qu'élément XML utilisé dans un fichier de configuration.Par exemple, `WSHttpBinding` \(API\) a un équivalent dans [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 La section suivante répertorie ces deux formulaires pour chaque de liaison et récapitule les fonctionnalités de sécurité.  
  
### BasicHttp  
 Dans le code, utilisez la classe <xref:System.ServiceModel.BasicHttpBinding> ; dans la configuration, utilisez [\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
 Cette liaison est conçue pour être utilisées avec une vaste gamme de technologies existantes, dont les suivantes :  
  
-   Services Web ASP.NET \(ASMX\), version 1.  
  
-   Applications WSE \(Web Service Enhancements\).  
  
-   Basic Profile tel que défini dans la spécification WS\-I \(Web Services Interoperability\), \([http:\/\/go.microsoft.com\/fwlink\/?LinkId\=38955](http://go.microsoft.com/fwlink/?LinkId=38955)\) \(page pouvant être en anglais\).  
  
-   Profil de sécurité de base tel que défini dans WS\-I.  
  
 Par défaut, cette liaison n'est pas sécurisée.Elle est conçue pour interagir avec les services ASMX.Lorsque la sécurité est activée, la liaison fournit une interopérabilité transparente avec les mécanismes de sécurité IIS \(Internet Information Services\), tels que l'authentification de base, Digest et la sécurité Windows intégrée.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Vue d'ensemble de la sécurité des transports](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).Cette liaison prend en charge les fonctionnalités suivantes :  
  
-   Sécurité du transport HTTPS.  
  
-   Authentification de base HTTP.  
  
-   WS\-Security.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType> et <xref:System.ServiceModel.BasicHttpSecurityMode>.  
  
### WSHttpBinding  
 Dans le code, utilisez la classe <xref:System.ServiceModel.WSHttpBinding> ; dans la configuration, utilisez [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 Par défaut, cette liaison implémente la spécification WS\-Security et fournit l'interopérabilité avec les services qui implémentent les spécifications WS\-\*.Elle prend en charge les fonctionnalités suivantes :  
  
-   Sécurité du transport HTTPS.  
  
-   WS\-Security.  
  
-   Protection du transport HTTPS avec sécurité des informations d'identification de message SOAP permettant d'authentifier l'appelant.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.WSHttpSecurity>, <xref:System.ServiceModel.MessageSecurityOverHttp>, <xref:System.ServiceModel.MessageCredentialType>, <xref:System.ServiceModel.SecurityMode>, <xref:System.ServiceModel.HttpTransportSecurity>, <xref:System.ServiceModel.HttpClientCredentialType> et <xref:System.ServiceModel.HttpProxyCredentialType>.  
  
### WSDualHttpBinding  
 Dans le code, utilisez la classe <xref:System.ServiceModel.WSDualHttpBinding> ; dans la configuration, utilisez [\<wsDualHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).  
  
 Cette liaison est conçue pour activer des applications de service duplex.Elle implémente la spécification WS\-Security pour la sécurité de transfert basée sur les messages.La sécurité de transport n'est pas disponible.Par défaut, elle fournit les fonctionnalités suivantes :  
  
-   Implémente WS\-Reliable Messaging pour la fiabilité.  
  
-   Implémente WS\-Security pour l'authentification et la sécurité de transfert.  
  
-   Utilise HTTP pour la remise de messages.  
  
-   Utilise l'encodage de message Text\/XML.  
  
 À l'aide de WS\-Security \(sécurité au niveau de la couche de message\), la liaison vous permet de configurer les paramètres suivants :  
  
-   La suite algorithmique de sécurité afin de déterminer l'algorithme de chiffrement.  
  
-   Options de liaison pour les éléments suivants :  
  
    -   Fourniture des informations d'identification de service disponibles hors bande au niveau du client.  
  
    -   Fourniture des informations d'identification de service négociées à partir du service dans le cadre de l'installation des canaux.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.WSDualHttpSecurity> et <xref:System.ServiceModel.WSDualHttpSecurityMode>.  
  
### NetTcpBinding  
 Dans le code, utilisez la classe <xref:System.ServiceModel.NetTcpBinding> ; dans la configuration, utilisez [\<netTcpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 Cette liaison est optimisée pour la communication d'un ordinateur à l'autre.Par défaut, elle présente les caractéristiques suivantes :  
  
-   Elle implémente la sécurité au niveau de la couche de transport.  
  
-   Elle tire parti de la sécurité Windows pour l'authentification et la sécurité de transfert.  
  
-   Elle utilise TCP pour le transport.  
  
-   Elle implémente l'encodage de message binaire.  
  
-   Elle implémente WS\-Reliable Messaging.  
  
 Les options disponibles sont les suivantes :  
  
-   Sécurité au niveau de la couche de message \(à l'aide de WS\-Security\).  
  
-   Sécurité de transport à l'aide des informations d'identification du message : confidentialité et intégrité fournies par TLS \(Transport Layer Security\), informations d'identification pour l'autorisation fournies par WS\-Security.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.NetTcpSecurity>, <xref:System.ServiceModel.TcpTransportSecurity>, <xref:System.ServiceModel.TcpClientCredentialType>, <xref:System.ServiceModel.MessageSecurityOverTcp> et <xref:System.ServiceModel.MessageCredentialType>.  
  
### NetNamedPipeBinding  
 Dans le code, utilisez la classe <xref:System.ServiceModel.NetNamedPipeBinding> ; dans la configuration, utilisez [\<netNamedPipeBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).  
  
 Cette liaison est optimisée pour la communication interprocessus \(généralement sur le même ordinateur\).Par défaut, elle présente les caractéristiques suivantes :  
  
-   Elle utilise la sécurité de transport pour l'authentification et le transfert de messages.  
  
-   Elle utilise des canaux nommés pour la remise de messages.  
  
-   Elle implémente l'encodage de message binaire.  
  
-   Chiffrement et signature des messages  
  
 Les options disponibles sont les suivantes :  
  
-   Authentification à l'aide de la sécurité Windows.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.NetNamedPipeSecurity>, <xref:System.ServiceModel.NetNamedPipeSecurityMode> et <xref:System.ServiceModel.NamedPipeTransportSecurity>.  
  
### MsmqIntegrationBinding  
 Dans le code, utilisez la classe <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ; dans la configuration, utilisez [\<msmqIntegrationBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).  
  
 Cette liaison est optimisée pour créer des services et des clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui interagissent avec les points de terminaison MSMQ \(Microsoft Message Queuing\) non\-[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Par défaut, elle utilise la sécurité de transport et fournit les caractéristiques de sécurité suivantes :  
  
-   La sécurité peut être désactivée \(None\).  
  
-   Sécurité de transport MSMQ \(Transport\).  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.NetMsmqSecurity> et <xref:System.ServiceModel.NetMsmqSecurityMode>.  
  
### NetMsmqBinding  
 Dans le code, utilisez la classe <xref:System.ServiceModel.NetMsmqBinding> ; dans la configuration, utilisez [\<netMsmqBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md).  
  
 Cette liaison est prévue pour être utilisée dans le cadre de la création de services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui requièrent la prise en charge des message en file d'attente MSMQ.  
  
 Par défaut, elle utilise la sécurité de transport et fournit les caractéristiques de sécurité suivantes :  
  
-   La sécurité peut être désactivée \(None\).  
  
-   Sécurité de transport MSMQ \(Transport\).  
  
-   Sécurité des messages SOAP \(Message\).  
  
-   Transport simultané et sécurité des messages \(Both\).  
  
-   Types d'informations d'identification du client pris en charge : None, Windows, UserName, Certificate, IssuedToken.  
  
 L'information d'identification <xref:System.ServiceModel.MessageCredentialType> est uniquement prise en charge lorsque le mode de sécurité a la valeur <xref:System.ServiceModel.NetMsmqSecurityMode> ou <xref:System.ServiceModel.NetMsmqSecurityMode>.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.MessageSecurityOverMsmq> et <xref:System.ServiceModel.MsmqTransportSecurity>.  
  
### WSFederationHttpBinding  
 Dans le code, utilisez la classe <xref:System.ServiceModel.WSFederationHttpBinding> ; dans la configuration, utilisez [\<wsFederationHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 Par défaut, cette liaison utilise WS\-Security \(sécurité au niveau de la couche de message\).  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Fédération](../../../../docs/framework/wcf/feature-details/federation.md), <xref:System.ServiceModel.WSFederationHttpSecurity> et <xref:System.ServiceModel.WSFederationHttpSecurityMode>.  
  
## Liaisons personnalisées  
 Si aucune des liaisons fournies par le système ne répondent à vos besoins, vous pouvez créer une liaison personnalisée à l'aide d'un élément de liaison de sécurité personnalisé.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Fonctionnalités de sécurité avec des liaisons personnalisées](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## Options de liaison  
 Le tableau suivant récapitule les fonctionnalités offertes par le paramètre de mode de sécurité défini ; autrement dit, il répertorie les fonctionnalités disponibles lorsque le mode de sécurité a la valeur `Transport`, `Message`ou `TransportWithMessageCredential`.Utilisez\-le pour rechercher les fonctionnalités de sécurité que votre application requiert.  
  
|Paramètre|Fonctionnalités|  
|---------------|---------------------|  
|Transport|Authentification du serveur<br /><br /> Authentification du client<br /><br /> Sécurité point à point<br /><br /> Interopérabilité<br /><br /> Accélération matérielle<br /><br /> Haut débit<br /><br /> Pare\-feu sécurisé<br /><br /> Applications à latence élevée<br /><br /> Rechiffrement sur des sauts multiples|  
|Message|Authentification du serveur<br /><br /> Authentification du client<br /><br /> Sécurité de bout en bout<br /><br /> Interopérabilité<br /><br /> Revendications enrichies<br /><br /> Fédération<br /><br /> Authentification multifacteur<br /><br /> Jetons personnalisés<br /><br /> Service de notaire\/horodatage<br /><br /> Applications à latence élevée<br /><br /> Persistance des signatures de message|  
|TransportWithMessageCredential|Authentification du serveur<br /><br /> Authentification du client<br /><br /> Sécurité point à point<br /><br /> Interopérabilité<br /><br /> Accélération matérielle<br /><br /> Haut débit<br /><br /> Revendications client enrichies<br /><br /> Fédération<br /><br /> Authentification multifacteur<br /><br /> Jetons personnalisés<br /><br /> Pare\-feu sécurisé<br /><br /> Applications à latence élevée<br /><br /> Rechiffrement sur des sauts multiples|  
  
 Le tableau suivant répertorie les liaisons qui prennent en charge les divers paramètres de mode.Sélectionnez dans le tableau la liaison à utiliser pour créer votre point de terminaison de service.  
  
|Liaison|Prise en charge du mode Transport|Prise en charge du mode Message|Prise en charge de TransportWithMessageCredential|  
|-------------|---------------------------------------|-------------------------------------|-------------------------------------------------------|  
|`BasicHttpBinding`|Oui|Oui|Oui|  
|`WSHttpBinding`|Oui|Oui|Oui|  
|`WSDualHttpBinding`|Non|Oui|Non|  
|`NetTcpBinding`|Oui|Oui|Oui|  
|`NetNamedPipeBinding`|Oui|Non|Non|  
|`NetMsmqBinding`|Oui|Oui|Non|  
|`MsmqIntegrationBinding`|Oui|Non|Non|  
|`wsFederationHttpBinding`|Non|Oui|Oui|  
  
## Informations d'identification de transport dans les liaisons  
 Le tableau suivant répertorie les types d'informations d'identification du client disponibles lors de l'utilisation de `BasicHttpBinding` ou `WSHttpBinding` en mode de sécurité Transport.  
  
|Type|Description|  
|----------|-----------------|  
|None|Spécifie que le client n'a pas besoin de présenter d'information d'identification.Cela se traduit en un client anonyme.|  
|Basic|Authentification de base.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] la RFC 2617 \- Authentification HTTP : authentification de base et Digest, disponible à l'adresse [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=84023](http://go.microsoft.com/fwlink/?LinkId=84023) \(page pouvant être en anglais\).|  
|Digest|Authentification Digest.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] la RFC 2617 \- Authentification HTTP : authentification de base et Digest, disponible à l'adresse [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=84023](http://go.microsoft.com/fwlink/?LinkId=84023) \(page pouvant être en anglais\).|  
|NTLM|Authentification NTLM \(NT LAN Manager\).|  
|Windows|Authentification Windows.|  
|Certificate|Authentification effectuée à l'aide d'un certificat.|  
|IssuedToken|Autorise le service à imposer que le client soit authentifié à l'aide d'un jeton émis par un service d'émission de jeton de sécurité ou par [!INCLUDE[infocard](../../../../includes/infocard-md.md)].[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Fédération et jetons émis](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### Informations d'identification du client de message dans les liaisons  
 Le tableau suivant répertorie les types d'informations d'identification du client disponibles lors de l'utilisation d'une liaison en mode de sécurité Message.  
  
|Type|Description|  
|----------|-----------------|  
|Aucune|Autorise le service à interagir avec des clients anonymes.|  
|Authentification Windows|Autorise les échanges de messages SOAP à se produire sous le contexte authentifié d'une information d'identification Windows.|  
|UserName|Autorise le service à imposer que le client soit authentifié à l'aide d'une information d'identification de nom d'utilisateur.Notez que lorsque le mode de sécurité a la valeur `TransportWithMessageCredential`, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne prend pas en charge l'envoi d'un condensé du mot de passe ou la dérivation de clés à l'aide du mot de passe, ainsi que l'utilisation de ces clés pour le mode de sécurité Message.De ce fait, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'assure que le transport est sécurisé lors de l'utilisation d'informations d'identification de nom d'utilisateur.|  
|Certificat|Autorise le service à imposer que le client soit authentifié à l'aide d'un certificat.|  
|IssuedToken|Autorise le service à utiliser un service d'émission de jeton de sécurité afin de fournir un jeton personnalisé.|  
  
## Voir aussi  
 [Vue d'ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [Sécurisation des services et des clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Sélection d'un type d'informations d'identification](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [Fonctionnalités de sécurité avec des liaisons personnalisées](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)   
 [Comportements de sécurité](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [Modèle de sécurité pour Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)