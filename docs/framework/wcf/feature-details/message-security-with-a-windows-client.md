---
title: "S&#233;curit&#233; de message avec un client Windows | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 13
---
# S&#233;curit&#233; de message avec un client Windows
Dans le scénario suivant, le client [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et le serveur sont sécurisés à l'aide du mode de sécurité de niveau message.Le client et le service sont authentifiés à l'aide des informations d'identification Windows.  
  
 ![Sécurité des messages avec un client Windows](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4\-0005\-4022\-beb6\-32fd087a8c3c")  
  
|Caractéristique|Description|  
|---------------------|-----------------|  
|Mode de sécurité|Message|  
|Interopérabilité|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uniquement|  
|Authentification \(serveur\)|Authentification mutuelle du serveur et du client|  
|Authentification \(client\)|Authentification mutuelle du serveur et du client|  
|Intégrité|Oui, à l'aide du contexte de sécurité partagé|  
|Confidentialité|Oui, à l'aide du contexte de sécurité partagé|  
|Transport|NET.TCP|  
|Liaison|<xref:System.ServiceModel.NetTcpBinding>|  
  
## Service  
 La configuration et le code ci\-dessous sont conçus pour s'exécuter indépendamment.Effectuez l'une des opérations suivantes :  
  
-   Créez un service autonome à l'aide du code sans configuration.  
  
-   Créez un service à l'aide de la configuration fournie, mais ne définissez pas de point de terminaison.  
  
### Code  
 Le code suivant indique comment créer un point de terminaison de service qui utilise la sécurité de message pour établir un contexte sécurisé lorsqu'un ordinateur sous Windows est utilisé.  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### Configuration  
 La configuration suivante peut être utilisée à la place du code pour paramétrer le service :  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration=""  
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"  
                  binding="netTcpBinding"  
                  bindingConfiguration="Windows"  
                  name="WindowsOverMessage"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="Windows">  
          <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## Client  
 La configuration et le code ci\-dessous sont destinés à s'exécuter indépendamment.Effectuez l'une des opérations suivantes :  
  
-   Créez un client autonome à l'aide du code \(et du code client\).  
  
-   Créez un client qui ne définit pas d'adresse de point de terminaison.Au lieu de cela, utilisez le constructeur client qui accepte le nom de la configuration comme argument.Par exemple :  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### Code  
 Le code suivant crée un client.La liaison est définie au mode de sécurité de niveau message et le type d'informations d'identification du client a la valeur `Windows`.  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### Configuration  
 La configuration suivante est utilisée pour définir les propriétés du client.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
         <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator"   
                binding="netTcpBinding"  
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">          
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## Voir aussi  
 [Vue d'ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [Modèle de sécurité pour Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)