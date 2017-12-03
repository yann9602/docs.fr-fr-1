---
title: "Modèle de configuration hiérarchique"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cbcef9ebe1b4876e429da97b3e217dd32286e4d6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="hierarchical-configuration-model"></a>Modèle de configuration hiérarchique
Cet exemple montre comment implémenter une hiérarchie de fichiers de configuration pour les services. Il montre également comment les liaisons, comportements de service et comportements de point de terminaison sont hérités des niveaux supérieurs de la hiérarchie.  
  
## <a name="sample-details"></a>Détails de l'exemple  
 L'une des fonctionnalités développées pour [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] est l'amélioration du modèle de configuration hiérarchique. Un exemple de modèle de configuration hiérarchique pourrait être celui que définit Machine.config -> Rootweb.config -> Web.config. Dans [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], les liaisons et comportements définis dans les niveaux supérieurs de la hiérarchie de configuration sont ajoutés à vos services sans configuration explicite. Cet exemple montre comment il est possible de simplifier votre configuration de services en vous appuyant sur les éléments de configuration définis au niveau de l'ordinateur ou de l'application.  
  
 Cet exemple se compose de neuf services, définis dans trois niveaux de la hiérarchie. `Service1` se trouve à la racine. `Service2` et `Service3` héritent des éléments par défaut de `Service1`. `Service4`, `Service5`, `Service6` et `Service7` sont définis à un troisième niveau de la hiérarchie et héritent des éléments par défaut de `Service3`. Enfin, `Service10` et `Service11` se situent à un quatrième niveau de la hiérarchie.  
  
 Tous les services implémentent le contrat `IDesc`. La définition de l'interface `IDesc` qui montre les méthodes exposées dans cette interface est présentée ci-dessous. L'interface `IDesc` est définie dans Service1.cs.  
  
```  
// Define a service contract  
[ServiceContract(Namespace="http://Microsoft.Samples.ConfigHierarchicalModel")]  
public interface IDesc  
{  
    [OperationContract]  
    List<string> ListEndpoints();  
    [OperationContract]  
    List<string> ListServiceBehaviors();  
    [OperationContract]  
    List<string> ListEndpointBehaviors();  
}  
```  
  
 L'implémentation de ces méthodes par les services est simple. `ListEndpoints` itère au sein de tous les points de terminaison de service et retourne une liste de tous les points de terminaison dont le service dispose. `ListServiceBehaviors` itère au sein de tous les comportements ajoutés au service et retourne la liste de tous les comportements de service associés au service. `ListEndpointBehaviors` se comporte de manière similaire à `ListServiceBehaviors`, mais il retourne la liste des comportements de point de terminaison à la place.  
  
 Cette implémentation permet au client de connaître le nombre de points de terminaison qu'expose le service et les comportements de service et comportements de point de terminaison qui ont été ajoutés au service. Le client implémenté dans le cadre de l'exemple ajoute une référence de service à tous les services de la solution et affiche ces éléments pour chacun des services.  
  
## <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
#### <a name="to-run-the-client"></a>Pour exécuter le client  
  
1.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier ConfigHierarchicalModel.sln.  
  
2.  Le projet client n'est pas encore configuré en tant que projet de démarrage. Procédez comme suit.  
  
    1.  Dans **l’Explorateur de solutions**, avec le bouton droit de la solution, puis sélectionnez **propriétés**.  
  
    2.  Dans **propriétés communes**, sélectionnez **projet de démarrage**, puis cliquez sur **projet de démarrage unique**.  
  
    3.  À partir de la **projet de démarrage unique** liste déroulante, sélectionnez **Client**.  
  
    4.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
3.  Pour créer l'exemple, appuyez sur Ctrl+Maj+B.  
  
4.  Pour exécuter le client, appuyez sur Ctrl+F5.  
  
> [!NOTE]
>  Si ces étapes ne fonctionnent pas, vérifiez que votre environnement a été correctement configuré, en procédant comme suit.  
>   
>  1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
> 2.  Pour générer la solution, suivez les instructions de [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
> 3.  Pour exécuter l’exemple dans un seul ou plusieurs configurations d’ordinateur, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de gestion de AppFabric](http://go.microsoft.com/fwlink/?LinkId=193960)
