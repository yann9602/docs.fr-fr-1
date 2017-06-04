---
title: "WS Dual Http | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9997eba5-29ec-48db-86f3-fa77b241fb1a
caps.latest.revision: 21
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 21
---
# WS Dual Http
Cet exemple montre comment configurer la liaison `WSDualHttpBinding`.Cet exemple se compose d'un programme de console client \(.exe\) et d'une bibliothèque de service \(.dll\) hébergés par les services IIS \(Internet Information Services\).Le service implémente un contrat duplex.Le contrat est défini par l'interface `ICalculatorDuplex`, laquelle expose les opérations mathématiques suivantes : addition, soustraction, multiplication et division.Dans cet exemple, l'interface `ICalculatorDuplex` permet au client d'effectuer des opérations mathématiques, et notamment de calculer le résultat sur la session.Le service retourne indépendamment les résultats sur l'interface `ICalculatorDuplexCallback`.Un contrat duplex requiert une session, car un contexte doit être établi pour mettre en correspondance l'ensemble des messages échangés entre le client et le service.La liaison `WSDualHttpBinding` prend en charge la communication duplex.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Binding\WS\DualHttp`  
  
 Pour configurer un point de terminaison de service avec `WSDualHttpBinding`, spécifiez la liaison dans la configuration de point de terminaison tel qu'indiqué.  
  
```  
<endpoint address=""  
         binding="wsDualHttpBinding"  
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
```  
  
 Sur le client, vous devez configurer une adresse que le serveur peut utiliser afin de s'y connecter, tel qu'indiqué dans l'exemple de configuration suivant.  
  
```  
<system.serviceModel>  
  <client>  
    <endpoint address=  
         "http://localhost/servicemodelsamples/service.svc"   
         binding="wsDualHttpBinding"   
         bindingConfiguration="Binding1"   
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
  </client>  
  
  <bindings>  
    <!-- Configure a WSDualHttpBinding that supports duplex -->  
    <!-- communication. -->  
    <wsDualHttpBinding>  
      <binding name="Binding1"  
               clientBaseAddress="http://localhost:8000/myClient/"  
               useDefaultWebProxy="true"  
               bypassProxyOnLocal="false">  
      </binding>  
    </wsDualHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console cliente.Appuyez sur ENTER dans la fenêtre du client pour l'arrêter.  
  
```  
Press <ENTER> to terminate client once the output is displayed.  
  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
  
```  
  
 Lorsque vous exécutez l'exemple, vous pouvez consulter les messages retournés au client sur l'interface de rappel envoyée depuis le service.Tous les résultats intermédiaires s'affichent, suivis de l'équation complète une fois toutes les opérations terminées.Appuyez sur ENTRÉE pour arrêter le client.  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Installez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 à l'aide de la commande suivante.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
  
    ```  
  
2.  Assurez\-vous d'avoir effectué la [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, suivez les instructions indiquées dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans la rubrique [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!IMPORTANT]
    >  Lorsque vous exécutez le client dans une configuration à plusieurs ordinateurs, assurez\-vous de remplacer localhost à la fois dans l'attribut `address` de l'élément [endpoint](http://msdn.microsoft.com/fr-fr/13aa23b7-2f08-4add-8dbf-a99f8127c017) et dans l'attribut `clientBaseAddress` de l'élément [\<liaison\>](../../../../docs/framework/misc/binding.md) de l'élément [\<wsDualHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) par le nom de l'ordinateur approprié, tel qu'indiqué dans le code suivant :  
  
    ```  
    <client>  
        <endpoint name = ""  
          address=  
         "http://service_machine_name/servicemodelsamples/service.svc"  
        />  
    </client>  
    ...  
    <wsDualHttpBinding>  
        <binding name="DuplexBinding" clientBaseAddress=  
            "http://client_machine_name:8000/myClient/">  
        </binding>  
    </wsDualHttpBinding>  
    ```  
  
## Voir aussi