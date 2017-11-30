---
title: NamedPipe Activation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 55594e1505e60ede8d7c6abcbd8a9cf9a1f739bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="namedpipe-activation"></a>NamedPipe Activation
Cet exemple illustre l'hébergement d'un service qui utilise le service d'activation des processus Windows (WAS) pour activer un service qui communique sur des canaux nommés. Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md) et nécessite [!INCLUDE[wv](../../../../includes/wv-md.md)] à exécuter.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`  
  
## <a name="sample-details"></a>Détails de l'exemple  
 L'exemple se compose d'un programme de console client (.exe) et d'une bibliothèque de service (.dll) hébergés dans un processus de travail activé par le service d'activation des processus Windows (WAS). L'activité du client est affichée dans la fenêtre de console.  
  
 Le service implémente un contrat qui définit un modèle de communication demande-réponse. Le contrat est défini par l'interface `ICalculator`, qui expose des opérations mathématiques (addition, soustraction, multiplication, division) comme illustré dans l'exemple de code suivant.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 Le client fait des demandes synchrones à une opération mathématique donnée et l'implémentation du service calcule et retourne le résultat approprié.  
  
```  
// Service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public double Add(double n1, double n2)  
    {  
        return n1 + n2;  
    }  
    public double Subtract(double n1, double n2)  
    {  
        return n1 - n2;  
    }  
    public double Multiply(double n1, double n2)  
    {  
        return n1 * n2;  
    }  
    public double Divide(double n1, double n2)  
    {  
        return n1 / n2;  
    }  
}  
```  
  
 L'exemple utilise une liaison `netNamedPipeBinding` modifiée sans sécurité. La liaison est spécifiée dans les fichiers de configuration pour le client et le service. Le type de liaison du service est spécifié dans l'attribut `binding` de l'élément du point de terminaison comme illustré dans l'exemple de configuration suivant.  
  
 Si vous souhaitez utiliser une liaison de canal nommé sécurisée, remplacez le mode de sécurité du serveur par le paramètre de sécurité souhaité et exécutez à nouveau svcutil.exe sur le client pour obtenir un fichier de configuration client mis à jour.  
  
```xml  
<system.serviceModel>  
        <services>  
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
  
        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->  
        <endpoint address=""   
                  binding="netNamedPipeBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is explosed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexNamedPipeBinding"  
                  contract="IMetadataExchange" />  
      </service>  
        </services>      
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="Binding1" >  
                    <security mode = "None">  
                    </security>  
                </binding >  
            </netNamedPipeBinding>  
        </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 Les informations sur le point de terminaison du client sont configurées comme illustré dans l'exemple de code suivant.  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <endpoint name=""  
                          address="net.pipe://localhost/servicemodelsamples/service.svc"   
                          binding="netNamedPipeBinding"   
                          bindingConfiguration="Binding1"   
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
    <bindings>  
  
      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.  
            Each property is configured with the default value.   -->  
  
      <netNamedPipeBinding>  
        <binding name="Binding1"   
                         maxBufferSize="65536"  
                         maxConnections="10">  
          <security mode = "None">  
          </security>  
        </binding >  
  
      </netNamedPipeBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Vérifiez que [!INCLUDE[iisver](../../../../includes/iisver-md.md)] est installé. [!INCLUDE[iisver](../../../../includes/iisver-md.md)] est requis pour l'activation du service WAS.  
  
2.  Vérifiez que vous avez exécuté le [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
     En outre, vous devez installer les composants d'activation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] non HTTP :  
  
    1.  À partir de la **Démarrer** menu, choisissez **le panneau de configuration**.  
  
    2.  Sélectionnez **programmes et fonctionnalités**.  
  
    3.  Cliquez sur **activer ou désactiver les composants Windows**.  
  
    4.  Développez le **Microsoft .NET Framework 3.0** nœud et cocher la **Activation Non-HTTP de Windows Communication Foundation** fonctionnalité.  
  
3.  Configurez le service d'activation des processus Windows pour prendre en charge l'activation de canal nommé.  
  
     Par commodité, les deux étapes suivantes sont implémentées dans un fichier de commandes appelé AddNetPipeSiteBinding.cmd et qui se trouve dans le répertoire d'exemple.  
  
    1.  Pour prendre en charge l'activation net.pipe, le site Web par défaut doit d'abord être lié au protocole net.pipe. Cela peut être fait à l'aide d'appcmd.exe, installé avec l'ensemble d'outils de gestion d'IIS 7.0. À partir d'une invite de commandes avec élévation de privilèges (administrateur), exécutez la commande suivante.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  Cette commande est une ligne unique de texte.  
  
         Cette commande ajoute une liaison de site net.pipe au site Web par défaut.  
  
    2.  Bien que toutes les applications d'un site partagent une liaison commune net.pipe, chaque application peut activer individuellement la prise en charge net.pipe. Pour activer net.pipe pour l'application /servicemodelsamples, exécutez la commande suivante à partir d'une invite de commandes avec élévation de privilèges.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe  
        ```  
  
        > [!NOTE]
        >  Cette commande est une ligne unique de texte.  
  
         Cette commande permet d'accéder à l'application servicemodelsamples à la fois via http://localhost/servicemodelsamples et via net.tcp://localhost/servicemodelsamples.  
  
4.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Supprimez la liaison du site net.pipe que vous avez ajoutée pour cet exemple.  
  
     Par commodité, les deux étapes suivantes sont implémentées dans un fichier de commandes appelé RemoveNetPipeSiteBinding.cmd et qui se trouve dans le répertoire d'exemple :  
  
    1.  Supprimez net.tcp de la liste de protocoles actifs en exécutant la commande suivante à partir d'une invite de commandes avec élévation de privilèges.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Cette commande doit être entrée comme une ligne unique de texte.  
  
    2.  Supprimez la liaison du site net.tcp en exécutant la commande suivante à partir d'une invite de commandes avec élévation de privilèges.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  Cette commande doit être tapée comme une ligne unique de texte.  
  
## <a name="see-also"></a>Voir aussi  
 [Hébergement de AppFabric et exemples de persistance](http://go.microsoft.com/fwlink/?LinkId=193961)
