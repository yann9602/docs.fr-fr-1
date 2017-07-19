---
title: "WS Reliable Session | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "session fiable"
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
caps.latest.revision: 30
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 30
---
# WS Reliable Session
Cet exemple montre l'utilisation des sessions fiables.Les sessions fiables fournissent la prise en charge de la messagerie et des sessions fiables.La messagerie fiable réessaie d'établir la communication en cas d'échec et permet de spécifier des assurances de remise telles que l'ordre d'arrivée des messages.Les sessions conservent l'état pour les clients entre les appels.Cet exemple implémente des sessions permettant de conserver l'état du client et spécifie des assurances de remise par ordre d'arrivée.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 Cet exemple est basé sur [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice.Les fonctionnalités de session fiables sont activées et configurées dans les fichiers de configuration d'application respectifs du client et du service.  
  
 Dans cet exemple, le service est hébergé dans les services IIS \(Internet Information Services\) et le client est une application console \(.exe\).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 L'exemple utilise le fichier `wsHttpBinding`.La liaison est spécifiée dans les fichiers de configuration pour le client et le service.Le type de liaison est spécifié dans l'attribut `binding` de l'élément de point de terminaison, tel qu'indiqué dans l'exemple de configuration suivant.  
  
```  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  
```  
  
 Le point de terminaison contient un attribut `bindingConfiguration` qui référence une configuration de liaison appelée « Binding1 ». La configuration de liaison active des sessions fiables en affectant `true` à l'attribut `enabled` de [\<reliableSession\>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md).Les assurances de remise pour les sessions ordonnées sont contrôlées en affectant `true` ou `false` à l'attribut ordonné.La valeur par défaut est `true`.  
  
```  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
  
```  
  
 La classe d'implémentation de service implémente l'instanciation <xref:System.ServiceModel.InstanceContextMode> afin de conserver une instance de classe distincte pour chaque client, tel qu'indiqué dans l'exemple de code suivant.  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console cliente.Appuyez sur ENTRÉE dans la fenêtre du client pour l'arrêter.  
  
```  
  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Installez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 à l'aide de la commande suivante.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
  
    ```  
  
2.  Assurez\-vous d'avoir effectué la [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, suivez les instructions indiquées dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans la rubrique [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## Voir aussi