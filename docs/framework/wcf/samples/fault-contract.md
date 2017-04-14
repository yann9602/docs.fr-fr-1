---
title: "Contrat d&#39;erreur | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# Contrat d&#39;erreur
Cet exemple illustre comment transmettre les informations relatives à une erreur d'un service à un client.  Il est basé sur [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md). Quelques lignes de code sont ajoutées au service pour permettre la conversion d'une exception interne en erreur.  Le client tente d'effectuer une opération de division par zéro pour imposer la génération d'une erreur sur le service.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Le contrat de calculatrice a été modifié afin d'y inclure un <xref:System.ServiceModel.FaultContractAttribute>, tel qu'illustré dans l'exemple de code suivant.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 L'attribut <xref:System.ServiceModel.FaultContractAttribute> indique que l'opération `Divide` est susceptible de retourner une erreur de type `MathFault`.  Il peut s'agir de tout type pouvant être sérialisé.  Ici, le type `MathFault` correspond à un contrat de données, tel qu'illustré ci\-dessous :  
  
```  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class MathFault  
{      
    private string operation;  
    private string problemType;  
  
    [DataMember]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]          
    public string ProblemType  
    {  
        get { return problemType; }  
        set { problemType = value; }  
    }  
}  
  
```  
  
 La méthode `Divide` lève une exception <xref:System.ServiceModel.FaultException%601> lorsqu'une opération de division par zéro se produit, tel qu'illustré dans l'exemple de code suivant.  Cette exception provoque l'envoi d'une erreur au client.  
  
```  
public int Divide(int n1, int n2)  
{  
    try  
    {  
        return n1 / n2;  
    }  
    catch (DivideByZeroException)  
    {  
        MathFault mf = new MathFault();  
        mf.operation = "division";  
        mf.problemType = "divide by zero";  
        throw new FaultException<MathFault>(mf);  
    }  
}  
```  
  
 Le code client impose la génération d'une erreur en demandant une division par zéro.  Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.  Vous pouvez voir que la division par zéro est signalée comme étant une erreur.  Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 Pour ce faire, le client intercepte l'exception `FaultException<MathFault>` appropriée :  
  
```  
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 Par défaut, les informations relatives aux exceptions non escomptées ne sont pas envoyées au client afin d'éviter que les informations relatives à l'implémentation du service ne franchissent les frontières de la zone sécurisée de ce dernier.  `FaultContract` permet de décrire des erreurs dans un contrat et de baliser certains types d'exceptions comme requis pour permettre leur transmission au client.  `FaultException<T>` fournit le mécanisme d'exécution nécessaire à l'envoi des erreurs aux consommateurs.  
  
 Toutefois, en cas de débogage, il est utile de consulter les détails internes relatifs aux éventuelles défaillances d'un service.  Pour désactiver le comportement sécurisé précédemment décrit, vous pouvez définir la spécification suivante : inclusion des détails relatifs à toutes les exceptions non prises en charge sur le serveur dans les erreurs envoyées au client.  Pour ce faire, il vous suffit d'affecter à <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> la valeur `true`.  Ce paramétrage peut être effectué dans le code ou la configuration, tel qu'illustré dans l'exemple suivant.  
  
```  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="True" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 En outre, le comportement doit être associé au service en affectant à l'attribut `behaviorConfiguration` du service dans le fichier de configuration la valeur CalculatorServiceBehavior.  
  
 Pour intercepter de telles erreurs sur le client, il est nécessaire d'intercepter l'exception non générique <xref:System.ServiceModel.FaultException>.  
  
 Ce comportement doit être utilisé à des fins de débogage uniquement et ne doit jamais être activé dans la production.  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, conformez\-vous aux instructions figurant dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## Voir aussi