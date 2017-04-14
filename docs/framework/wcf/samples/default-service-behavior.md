---
title: "Default Service Behavior | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Default Service Behavior (exemple) (Windows Communication Foundation)"
  - "comportements de service, par défaut"
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
caps.latest.revision: 28
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 28
---
# Default Service Behavior
Cet exemple montre comment les paramètres de comportement du service peuvent être configurés.Cet exemple est basé sur l'[Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente le contrat de service `ICalculator`.Cet exemple définit explicitement des comportements de service et des comportements d'opération à l'aide des attributs <xref:System.ServiceModel.ServiceBehaviorAttribute> et <xref:System.ServiceModel.OperationBehaviorAttribute>.Vous pouvez configurer les comportements dans les fichiers de configuration ou impérativement dans le code \(comme le montre cet exemple\).  
  
 Dans cet exemple, le client est une application console \(.exe\) et le service est hébergé par les services IIS \(Internet Information Services\).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent en fin de rubrique.  
  
 La classe de service spécifie des comportements avec l'<xref:System.ServiceModel.ServiceBehaviorAttribute> et l'<xref:System.ServiceModel.OperationBehaviorAttribute> comme le montre l'exemple de code suivant.Toutes les valeurs spécifiées sont les valeurs par défaut.  
  
```  
[ServiceBehavior(  
    AutomaticSessionShutdown=true,  
    ConcurrencyMode=ConcurrencyMode.Single,  
    InstanceContextMode=InstanceContextMode.PerSession,  
    IncludeExceptionDetailInFaults=false,  
    UseSynchronizationContext=true,  
    ValidateMustUnderstand=true)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(  
        TransactionAutoComplete=true,  
        TransactionScopeRequired=false,  
        Impersonation=ImpersonationOption.NotAllowed)]  
    public double Add(double n1, double n2)  
    {  
        System.Threading.Thread.Sleep(1600);  
        return n1 + n2;  
    }  
    ...  
}  
  
```  
  
 Les comportements de service sont spécifiés avec l'attribut <xref:System.ServiceModel.ServiceBehaviorAttribute>.Le tableau suivant décrit quelques\-uns de ces comportements.  
  
|Comportement de service|Description|  
|-----------------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|Ferme automatiquement une session à la demande du client.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|Spécifie le mode d'accès concurrentiel pour chaque instance de service.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|Spécifie le mode de contexte d'instance.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|Détermine s'il faut utiliser le contexte de synchronisation fourni, s'il est défini.Utilisez\-le pour contrôler s'il faut utiliser un `WindowsFormsSynchronizationContext` dans les applications Windows Forms.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|Détermine si les exceptions d'exécution non prise en charge générales doivent être converties en `Fault<string>` et envoyées comme un message d'erreur.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|Spécifie le niveau d'isolation des transactions.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|Détermine si les en\-têtes de message inattendus provoquent une condition d'erreur.|  
  
 Les comportements d'opération sont spécifiés à l'aide de l'attribut <xref:System.ServiceModel.OperationBehaviorAttribute>.Le tableau suivant décrit quelques\-uns de ces comportements.  
  
|Comportement d'opération|Description|  
|------------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|Détermine si l'achèvement de l'opération de service valide la transaction en cours.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|Détermine si l'opération de service s'inscrit dans une transaction transmise par le client.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|Détermine si l'opération de service emprunte l'identité de l'appelant.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|Détermine si les instances de service sont recyclées au début ou à la fin de l'appel de l'opération de service.|  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console cliente.Le délai entre les appels est le résultat des appels passés à `System.Threading.Thread.Sleep()` dans les opérations de service.Le reste des exemples de comportements explique ces comportements de manière plus détaillée.Appuyez sur ENTER dans la fenêtre du client pour fermer celui\-ci.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, suivez les instructions indiquées dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans la rubrique [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
  
## Voir aussi