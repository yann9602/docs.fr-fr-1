---
title: "Comment : configurer des paramètres de service COM+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7cbe038b55358ec8607d54b67861ef1743c2e301
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-configure-com-service-settings"></a>Comment : configurer des paramètres de service COM+
Lorsqu'une interface d'application est ajoutée ou supprimée en utilisant l'outil de configuration de service COM+, la configuration de service Web est mise à jour dans le fichier de configuration de l'application. Dans le mode d’hébergement COM +, le fichier Application.config est placé dans le répertoire racine de l’Application (%PROGRAMFILES%\ComPlus Applications\\{appid} est la valeur par défaut). Dans l'un ou l'autre des modes hébergés sur le Web, le fichier Web.config est placé dans le répertoire vroot spécifié.  
  
> [!NOTE]
>  La signature du message doit être utilisée pour éviter la falsification des messages entre un client et un serveur. De plus, le chiffrement de la couche transport ou message doit être utilisé pour se protéger contre la divulgation d'informations de messages entre un client et un serveur. Comme avec les services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], vous devez utiliser la fonctionnalité de limitation pour limiter le nombre d'appels, de connexions, d'instances simultanés et d'opérations en attente. Elle permet d'empêcher la surconsommation de ressources. La fonctionnalité de limitation est spécifiée à l'aide des paramètres de fichier de configuration de service.  
  
## <a name="example"></a>Exemple  
 Prenons l'exemple d'un composant qui implémente l'interface suivante :  
  
```  
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 Si le composant est exposé en tant que service Web, le contrat de service correspondant qui est exposé, et auquel les clients doivent se conformer, est le suivant :  
  
```  
[ServiceContract(Session = true,  
Namespace = "http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7",  
Name = "IFinances")]  
public interface IFinancesContract : IDisposable  
{  
    [OperationContract]  
    string Debit(string accountNo, double amount);  
    [OperationContract]  
    string Credit(string accountNo, double amount);  
}  
```  
  
> [!NOTE]
>  IID fait partie intégrante de l'espace de noms initial pour le contrat.  
  
 Les applications clientes qui utilisent ce service doivent se conformer à ce contrat et utiliser une liaison compatible avec celui spécifié dans la configuration de l'application.  
  
 L'exemple de code suivant affiche un fichier de configuration par défaut. En tant que service Web [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], il se conforme au schéma de configuration du modèle de service standard et peut être modifié de la même façon que d'autres fichiers de configuration des services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Les changements standard incluent :  
  
-   Remplacer l'adresse de point de terminaison de la forme par défaut ApplicationName/ComponentName/InterfaceName par une forme plus utilisable.  
  
-   Remplacer l'espace de noms du service de la forme "http://tempuri.org/InterfaceID" par défaut par une forme plus pertinente.  
  
-   Modifier le point de terminaison pour utiliser une liaison de transport différente.  
  
     Dans le cas hébergé par COM+, le transport de canaux nommés est utilisé par défaut, mais un transport off-machine, tel que TCP, peut être utilisé à la place.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="comNonTransactionalBinding" />  
                <binding name="comTransactionalBinding" transactionFlow="true" />  
            </netNamedPipeBinding>  
        </bindings>  
        <comContracts>  
            <comContract contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"  
                name="IFinances" namespace="http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7"  
                requiresSession="true">  
                <exposedMethods>  
                    <add exposedMethod="Debit" />  
                    <add exposedMethod="Credit" />  
                </exposedMethods>  
            </comContract>  
        </comContracts>  
        <services>  
            <service name="{DCDB24CC-0B19-4534-95CD-FBBFF4D67DD9},{C942B840-AD54-4A44-B5F7-928130980AB9}">  
                <endpoint address="IFinances" binding="netNamedPipeBinding" bindingConfiguration="comNonTransactionalBinding"  
                    contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" />  
                <host>  
                    <baseAddresses>  
                        <add baseAddress="net.pipe://localhost/ServiceModelDocSampleApp/ServiceModelDocSample.esFinance" />  
                    </baseAddresses>  
                </host>  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Intégration à des Applications COM +](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
