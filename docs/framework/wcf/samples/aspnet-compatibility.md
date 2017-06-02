---
title: "ASP.NET Compatibility | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
caps.latest.revision: 25
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 25
---
# ASP.NET Compatibility
Cet exemple illustre comment activer le mode de compatibilité [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  Les services qui s'exécutent dans le mode de compatibilité [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] participent pleinement au pipeline de l'application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et peuvent utiliser des fonctionnalités [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] telles que l'autorisation de fichier\/d'URL, l'état de session et la classe <xref:System.Web.HttpContext>.  La classe <xref:System.Web.HttpContext> permet l'accès aux cookies, aux sessions ainsi qu'à d'autres fonctionnalités [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  Dans ce mode, les liaisons doivent utiliser le transport HTTP et le service lui\-même doit être hébergé dans les services IIS.  
  
 Dans cet exemple, le client est une application console \(fichier exécutable\) et le service est hébergé dans les services IIS  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
> [!NOTE]
>  Cet exemple requiert pour fonctionner un pool d'applications [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].  Pour créer un pool d'applications ou modifier le pool d'applications par défaut, procédez comme suit.  
>   
>  1.  Ouvrez le **Panneau de configuration**.  Ouvrez l'applet **Outils d'administration** sous le titre **Système et sécurité**.  Ouvrez l'applet **Gestionnaire des services Internet \(IIS\)**.  
> 2.  Développez l'arborescence du volet **Connexions**.  Sélectionnez le nœud **Pools d'applications**.  
> 3.  Pour configurer le pool d'applications par défaut de sorte qu'il utilise [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] \(ce qui peut provoquer des problèmes d'incompatibilité avec des sites existants\), cliquez avec le bouton droit sur l'élément de liste **DefaultAppPool** et sélectionnez **Paramètres de base**.  Dans le menu déroulant **Version du .Net Framework**, choisissez **.Net Framework v4.0.30128** \(ou version ultérieure\).  
> 4.  Pour créer un pool d'applications qui utilise [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] \(afin de préserver la compatibilité avec d'autres applications\), cliquez avec le bouton droit sur le nœud **Pools d'applications** et sélectionnez **Ajouter un pool d'applications**.  Nommez le nouveau pool d'applications et dans le menu déroulant **Version du .Net Framework**, choisissez **.Net Framework v4.0.30128** \(ou version ultérieure\).  Après avoir exécuté les étapes de configuration ci\-dessous, cliquez avec le bouton droit sur l'application **ServiceModelSamples** et sélectionnez **Gérer une application**, puis  **Paramètres avancés**.  Affectez à **Pool d'applications** le nouveau pool d'applications.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, accédez à la page des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 Cet exemple est basé sur [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice.  Les contrats `ICalculator` et `ICalculatorSession` ont été modifiés pour permettre à un ensemble d'opérations d'être effectuées tout en conservant un résultat d'exécution.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculatorSession  
{  
    [OperationContract]  
    void Clear();  
    [OperationContract]  
    void AddTo(double n);  
    [OperationContract]  
    void SubtractFrom(double n);  
    [OperationContract]  
    void MultiplyBy(double n);  
    [OperationContract]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
  
```  
  
 Le service conserve l'état de chaque client \(à l'aide de la fonctionnalité correspondante\) tandis que plusieurs opérations de service sont appelées pour effectuer un calcul.  Le client peut récupérer le résultat actuel en appelant `Result` et remettre le résultat à zéro en appelant `Clear`.  
  
 Le service utilise la session [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pour stocker le résultat de chaque session de client.  Cela lui permet de conserver le résultat d'exécution de chaque client tandis qu'il reçoit plusieurs appels.  
  
> [!NOTE]
>  L'état de session [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et les sessions [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont deux fonctionnalités très différentes l'une de l'autre.  Consultez [Session](../../../../docs/framework/wcf/samples/session.md) pour plus d'informations sur les sessions [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Le service dépend étroitement de l'état de session [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et nécessite que le mode de compatibilité [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] fonctionne correctement.  Ces spécifications sont définies de manière déclarative en appliquant l'attribut `AspNetCompatibilityRequirements`.  
  
```  
[AspNetCompatibilityRequirements(RequirementsMode =  
                       AspNetCompatibilityRequirementsMode.Required)]  
public class CalculatorService : ICalculatorSession  
{  
    double Result  
    {  // store result in AspNet Session  
       get {  
          if (HttpContext.Current.Session["Result"] != null)  
             return (double)HttpContext.Current.Session["Result"];  
          return 0.0D;  
       }  
       set  
       {  
          HttpContext.Current.Session["Result"] = value;  
       }  
    }  
    public void Clear()  
    {  
        Result = 0.0D;  
    }  
    public void AddTo(double n)  
    {  
        Result += n;  
    }  
    public void SubtractFrom(double n)  
    {  
        Result -= n;  
    }  
    public void MultiplyBy(double n)  
    {  
        Result *= n;  
    }  
    public void DivideBy(double n)  
    {  
        Result /= n;  
    }  
    public double Result()  
    {  
        return Result;  
    }  
}  
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.  Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```  
  
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
  
```  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée dans la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, conformez\-vous aux instructions figurant dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Une fois la solution générée, exécutez Setup.bat pour installer l'application ServiceModelSamples dans [!INCLUDE[iisver](../../../../includes/iisver-md.md)].  Le répertoire ServiceModelSamples doit maintenant apparaître en tant qu'application [!INCLUDE[iisver](../../../../includes/iisver-md.md)].  
  
4.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## Voir aussi  
 [Exemples d'hébergement et de persistance AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)