---
title: "Activité de stratégie dans .NET Framework 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e375e0c-d7c1-4d69-88ab-36d52db0aa7e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 68c81b81ac8070cff539b52c75e1cd7ffb3e54b5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="policy-activity-in-net-framework-45"></a>Activité de stratégie dans .NET Framework 4.5
L'activité Policy4 permet que des objets [!INCLUDE[wf2](../../../../includes/wf2-md.md)] de [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] dans <xref:System.Workflow.Activities.Rules.RuleSet> (WF 3.5) soient utilisés dans [!INCLUDE[wf2](../../../../includes/wf2-md.md)] dans [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directement à l'aide du moteur de règles fourni dans WF 3.5. À l'aide de cette activité, vous pouvez créer et exécuter un <xref:System.Workflow.Activities.Rules.RuleSet> WF 3.5. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] le moteur de règles WF 3.5 inclus dans Windows Workflow Foundation, consultez la Présentation du moteur de règles Windows Workflow Foundation. Pour plus d’informations sur la migration de règles WF dans [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], veuillez lire [conseils de Migration](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-Policy4`  
  
## <a name="projects-in-this-sample"></a>Projets dans cet exemple  
  
|Nom du projet|Description|Fichiers principaux|  
|------------------|-----------------|----------------|  
|Policy4|Contient l'activité Policy4 et son concepteur [!INCLUDE[wf1](../../../../includes/wf1-md.md)].|**Policy4.cs**: définition de l’activité Policy4.<br /><br /> **PolicyDesigner.xaml**: concepteur personnalisé pour l’activité Policy4. Elle utilise l’éditeur de règles ([classe RuleSetDialog](http://go.microsoft.com/fwlink/?LinkId=150378)) à partir de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] moteur de règles.|  
|ImperativeCodeClientSample|Exemple d'application cliente qui configure et exécute un workflow à l'aide d'une application Policy4 utilisant du code C# impératif (aucun concepteur [!INCLUDE[wf1](../../../../includes/wf1-md.md)] utilisé).|**ApplyDiscount.rules**: fichier avec [!INCLUDE[wf1](../../../../includes/wf1-md.md)] définitions de règles.<br /><br /> **Order.cs**: Type qui représente une commande client. Les règles sont appliquées aux objets de ce type.<br /><br /> **Program.cs**: Configure et exécute un workflow qui a une activité Policy4 pour appliquer les règles définies dans ApplyDiscount.rules aux instances d’objets Order.<br /><br /> **App.config**: fichier de Configuration avec le chemin d’accès du fichier de règles.|  
|DesignerClientSample|Exemple d'application cliente qui configure et exécute un workflow à l'aide d'une application Policy4 dans le concepteur [!INCLUDE[wf1](../../../../includes/wf1-md.md)].|**Sequence1.XAML**: workflow séquentiel qui utilise une activité Policy4 pour effectuer des évaluations de règle.<br /><br /> `Program.cs` : exécute une instance du workflow définie dans Sequence1.xaml.|  
  
## <a name="the-policy4-activity"></a>Activité Policy4  
 L'activité Policy4 est une classe qui dérive de <xref:System.Activities.NativeActivity%601> et qui permet aux workflows d'exécuter des ensembles de règles (RuleSets) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. L'exemple de code suivant est une définition simplifiée du modèle d'objet public de l'activité.  
  
```csharp  
public class Policy4Activity<TResult>: NativeActivity<TResult>  
{  
    public RuleSet RuleSet  
  
    [IsRequired]  
    public InArgument Input  
  
    public OutArgument<ValidationErrorCollection> ValidationErrors  
}  
```  
  
|Propriété|Description|  
|--------------|-----------------|  
|RuleSet|WF [classe RuleSet](http://go.microsoft.com/fwlink/?LinkId=150379) pour .NET Framework 3.5 à évaluer lorsque l’activité est exécutée.|  
|TargetObject|L’objet sur lequel les règles dans le [classe RuleSet](http://go.microsoft.com/fwlink/?LinkId=150379) sont évaluées.|  
|ValidationError|La liste des erreurs de validation retournées par la [!INCLUDE[wf1](../../../../includes/wf1-md.md)] du moteur de règles pour .NET Framework 3.5 lors de la validation du [classe RuleSet](http://go.microsoft.com/fwlink/?LinkId=150379) sur l’objet cible avant l’exécution.|  
  
## <a name="policy4-activity-designer"></a>Concepteur de l'activité Policy4  
 Le concepteur de Policy4 ajoute la fonctionnalité permettant de configurer une activité Policy4 sans qu'il soit nécessaire d'écrire du code. Après la génération de la solution, il peut être trouvé dans la boîte à outils dans la section **Microsoft.Samples.Activities.Rules**.  
  
 Le concepteur WF vous permet de configurer un objet cible et un ensemble de règles (RuleSet). Lorsque le **modifier le RuleSet** bouton est activé, le WF [classe RuleSetDialog](http://go.microsoft.com/fwlink/?LinkId=150378) pour [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] s’affiche. Cette boîte de dialogue est l'éditeur de règles de [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] réhébergé. Utilisez l'éditeur pour créer et modifier les règles que l'activité Policy4 exécute.  
  
## <a name="using-this-sample"></a>Utilisation de cet exemple  
 Aucune configuration particulière n'est requise pour exécuter cet exemple. Ouvrez simplement la solution dans Visual Studio, puis appuyez sur F5 pour exécuter l'application.  
  
 Cet exemple contient deux applications clientes : ImperativeCodeClientSample et DesignerClientSample. Le client ImperativeCodeClientSample montre comment configurer et exécuter l'activité Policy40 à l'aide de code C# impératif. DesignerClientSample montre comment configurer et exécuter l'activité Policy4 à l'aide du concepteur.  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>Pour exécuter l'application cliente ImperativeCodeClientSample  
  
1.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier solution Policy4Sample.sln.  
  
2.  Dans **l’Explorateur de solutions**, avec le bouton droit le **ImperativeCodeClientSample** de projet, puis sélectionnez **définir comme projet de démarrage**.  
  
3.  Pour exécuter le projet, appuyez sur CTRL+F5.  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>Pour exécuter l'application cliente ImperativeCodeClientSample  
  
1.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier solution Policy4Sample.sln.  
  
2.  Dans **l’Explorateur de solutions**, cliquez sur le **DesignerClientSample** projet.  
  
    -   Sélectionnez **définir comme projet de démarrage**.  
  
3.  Pour compiler le projet, appuyez sur Ctrl+Maj+B.  
  
4.  Pour exécuter le projet, appuyez sur CTRL+F5.