---
title: ASP.NET Compatibility
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 751fe96caa2be63e925b3107fa2c198b523bef72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="aspnet-compatibility"></a>ASP.NET Compatibility
Cet exemple illustre comment activer le mode de compatibilité [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Les services qui s'exécutent dans le mode de compatibilité [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] participent pleinement au pipeline de l'application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et peuvent utiliser des fonctionnalités [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] telles que l'autorisation de fichier/d'URL, l'état de session et la classe <xref:System.Web.HttpContext>. La classe <xref:System.Web.HttpContext> permet l'accès aux cookies, aux sessions ainsi qu'à d'autres fonctionnalités [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Dans ce mode, les liaisons doivent utiliser le transport HTTP et le service lui-même doit être hébergé dans les services IIS.  
  
 Dans cet exemple, le client est une application console (fichier exécutable) et le service est hébergé dans les services IIS   
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
> [!NOTE]
>  Cet exemple requiert pour fonctionner un pool d'applications [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]. Pour créer un pool d'applications ou modifier le pool d'applications par défaut, procédez comme suit.  
>   
>  1.  Ouvrez le **Panneau de configuration**.  Ouvrez le **outils d’administration** applet sous le **système et sécurité** titre. Ouvrez le **Gestionnaire des Services Internet (IIS)** applet.  
> 2.  Développez l’arborescence dans le **connexions** volet. Sélectionnez le **Pools d’applications** nœud.  
> 3.  Pour définir le pool d’applications par défaut à utiliser [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (ce qui peut entraîner des problèmes d’incompatibilité avec les sites existants), avec le bouton droit le **DefaultAppPool** élément de liste et sélectionnez **les paramètres de base...** . Définir le **.Net Framework Version** déroulant **.Net Framework v4.0.30128** (ou version ultérieure).  
> 4.  Pour créer un nouveau pool d’applications qui utilise [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (pour préserver la compatibilité avec d’autres applications), avec le bouton droit le **Pools d’applications** nœud et sélectionnez **ajouter un Pool d’applications...** . Nommez le nouveau pool d’applications et le **.Net Framework Version** déroulant **.Net Framework v4.0.30128** (ou version ultérieure). Une fois que le programme d’installation en cours d’exécution d’étapes ci-dessous, cliquez sur le **ServiceModelSamples** application et sélectionnez **gérer l’Application**, **paramètres avancés...** . Définir le **Pool d’applications** pour le pool d’applications.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md), qui implémente un service de calculatrice. Les contrats `ICalculator` et `ICalculatorSession` ont été modifiés pour permettre à un ensemble d'opérations d'être effectuées tout en conservant un résultat d'exécution.  
  
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
  
 Le service conserve l'état de chaque client (à l'aide de la fonctionnalité correspondante) tandis que plusieurs opérations de service sont appelées pour effectuer un calcul. Le client peut récupérer le résultat actuel en appelant `Result` et remettre le résultat à zéro en appelant `Clear`.  
  
 Le service utilise la session [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pour stocker le résultat de chaque session de client. Cela lui permet de conserver le résultat d'exécution de chaque client tandis qu'il reçoit plusieurs appels.  
  
> [!NOTE]
>  L'état de session [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et les sessions [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont deux fonctionnalités très différentes l'une de l'autre.  Consultez le [Session](../../../../docs/framework/wcf/samples/session.md) pour plus d’informations sur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessions.  
  
 Le service dépend étroitement de l'état de session [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et nécessite que le mode de compatibilité [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] fonctionne correctement. Ces spécifications sont définies de manière déclarative en appliquant l'attribut `AspNetCompatibilityRequirements`.  
  
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
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```  
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Vérifiez que vous avez effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Une fois la solution générée, exécutez Setup.bat pour installer l'application ServiceModelSamples dans [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. Le répertoire ServiceModelSamples doit maintenant apparaître en tant qu'application [!INCLUDE[iisver](../../../../includes/iisver-md.md)].  
  
4.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Hébergement de AppFabric et exemples de persistance](http://go.microsoft.com/fwlink/?LinkId=193961)
