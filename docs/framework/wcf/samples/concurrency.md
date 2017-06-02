---
title: "Concurrency | Microsoft Docs"
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
  - "Concurrency (exemple) (Windows Communication Foundation)"
  - "comportements de service, accès concurrentiel (exemple)"
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
caps.latest.revision: 32
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 32
---
# Concurrency
Cet exemple montre l'utilisation du <xref:System.ServiceModel.ServiceBehaviorAttribute> avec l'énumération <xref:System.ServiceModel.ConcurrencyMode> qui contrôle si une instance de service traite des messages l'un après l'autre ou simultanément.  Cet exemple est basé sur l'[Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente le contrat de service `ICalculator`.  Cet exemple définit un nouveau contrat, `ICalculatorConcurrency`, qui hérite d' `ICalculator`, fournissant deux opérations supplémentaires pour l'inspection de l'état d'accès concurrentiel du service.  En modifiant le paramètre d'accès concurrentiel, vous pouvez observer le changement de comportement en exécutant le client.  
  
 Dans cet exemple, le client est une application console \(.exe\) et le service est hébergé par les services IIS \(Internet Information Services\).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Trois modes d'accès concurrentiel sont disponibles :  
  
-   `Single` : chaque instance de service traite un message à la fois.  Il s'agit du mode d'accès concurrentiel par défaut.  
  
-   `Multiple` : chaque instance de service traite plusieurs messages simultanément.  Pour utiliser ce mode, l'implémentation de service doit être « thread\-safe ».  
  
-   `Reentrant` : chaque instance de service traite un message à la fois, mais accepte des appels réentrants.  Le service accepte seulement ces appels lorsqu'il appelle.  Ce mode est illustré dans l'exemple [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md).  
  
 L'utilisation de l'accès concurrentiel est associée au mode d'instanciation.  Dans l'instanciation <xref:System.ServiceModel.InstanceContextMode>, l'accès concurrentiel n'est pas pertinent, parce que chaque message est traité par une nouvelle instance de service.  Dans l'instanciation <xref:System.ServiceModel.InstanceContextMode>, l'accès concurrentiel <xref:System.ServiceModel.ConcurrencyMode> ou <xref:System.ServiceModel.ConcurrencyMode> est pertinent, selon que la même instance traite des messages l'un après l'autre ou simultanément.  Dans l'instanciation <xref:System.ServiceModel.InstanceContextMode>, chacun des modes d'accès concurrentiel peut être pertinent.  
  
 La classe de service spécifie le comportement d'accès concurrentiel avec l'attribut `[ServiceBehavior(ConcurrencyMode=<setting>)]` comme illustré dans l'exemple de code suivant.  En modifiant les lignes commentées, vous pouvez tester les modes d'accès concurrentiel `Single` et `Multiple`.  Veillez à régénérer le service après avoir modifié le mode d'accès concurrentiel.  
  
```  
// Single allows a single message to be processed sequentially by each service instance.  
//[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, InstanceContextMode = InstanceContextMode.Single)]  
  
// Multiple allows concurrent processing of multiple messages by a service instance.  
// The service implementation should be thread-safe. This can be used to increase throughput.  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]  
  
// Uses Thread.Sleep to vary the execution time of each operation.  
public class CalculatorService : ICalculatorConcurrency  
{  
    int operationCount;  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(180);  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(100);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(150);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(120);  
        return n1 / n2;  
    }  
  
    public string GetConcurrencyMode()  
    {     
        // Return the ConcurrencyMode of the service.  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.ConcurrencyMode.ToString();  
    }  
  
    public int GetOperationCount()  
    {     
        // Return the number of operations.  
        return operationCount;  
    }  
}  
```  
  
 L'exemple utilise par défaut l'accès concurrentiel <xref:System.ServiceModel.ConcurrencyMode> avec l'instanciation <xref:System.ServiceModel.InstanceContextMode>.  Le code client a été modifié pour utiliser un proxy asynchrone.  Le client peut ainsi effectuer plusieurs appels au service sans attendre de réponse entre chaque appel.  Vous pouvez observer la différence dans le comportement du mode d'accès concurrentiel de service.  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.  Le mode d'accès concurrentiel sous lequel le service s'exécute s'affiche, chaque opération est appelée, puis, le nombre d'opérations est affiché.  Notez que lorsque le mode d'accès concurrentiel est `Multiple`, les résultats sont retournés dans un ordre différent de l'ordre d'appel parce que le service traite plusieurs messages simultanément.  En modifiant le mode d'accès concurrentiel en `Single`, les résultats sont retournés dans l'ordre d'appel parce que le service traite chaque message individuellement.  Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Si vous utilisez Svcutil.exe pour générer le client proxy, veillez à inclure l'option `/async`.  
  
3.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, conformez\-vous aux instructions figurant dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
  
## Voir aussi