---
title: "IIS Hosting Using Inline Code | Microsoft Docs"
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
  - "IIS Hosting Using Inline Code (exemple) (Windows Communication Foundation)"
  - "service Web hébergé"
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
caps.latest.revision: 40
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 40
---
# IIS Hosting Using Inline Code
Cet exemple montre comment implémenter un service hébergé par les services IIS \(Internet Information Services\), où le code de service est contenu en ligne dans un fichier .svc et est compilé à la demande.Le code de service peut également être implémenté directement dans les fichiers de code source localisés dans le répertoire de \\App\_Code de l'application, ou être compilé dans l'assembly déployé dans \\bin.Cet exemple ne présente pas ces techniques.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`  
  
 L'exemple présente un service standard qui implémente un contrat définissant un modèle de communication demande\-réponse.Le service est hébergé dans IIS et le code de service est entièrement contenu dans le fichier Service.svc.Le service est activé par l'hôte et est compilé à la demande par le premier message envoyé au service.Aucune précompilation n'est nécessaire.Le service implémente un contrat `ICalculator` tel que défini dans le code suivant :  
  
```  
// Define a service contract.  
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
  
 L'implémentation de service calcule et retourne le résultat approprié.  
  
```  
<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>   
…  
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
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console cliente.Appuyez sur ENTER dans la fenêtre du client pour arrêter le client.  
  
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
  
3.  Une fois la solution générée, exécutez setup.bat pour installer l'application ServiceModelSamples dans [!INCLUDE[iisver](../../../../includes/iisver-md.md)].Le répertoire ServiceModelSamples doit maintenant apparaître en tant qu'application [!INCLUDE[iisver](../../../../includes/iisver-md.md)].  
  
4.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).Pour obtenir un exemple de la façon de créer une application cliente qui peut appeler ce service, consultez [Comment : créer un client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
## Voir aussi  
 [Hébergement AppFabric et exemples de persistance](http://go.microsoft.com/fwlink/?LinkId=193961)