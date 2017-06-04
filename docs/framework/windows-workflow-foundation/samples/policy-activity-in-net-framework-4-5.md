---
title: "Activit&#233; de strat&#233;gie dans .NET Framework&#160;4.5 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8e375e0c-d7c1-4d69-88ab-36d52db0aa7e
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# Activit&#233; de strat&#233;gie dans .NET Framework&#160;4.5
L'activité Policy4 permet que des objets <xref:System.Workflow.Activities.Rules.RuleSet> de [!INCLUDE[wf2](../../../../includes/wf2-md.md)] dans [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] \(WF 3.5\) soient utilisés dans [!INCLUDE[wf2](../../../../includes/wf2-md.md)] dans [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] \(WF 4.5\) directement à l'aide du moteur de règles fourni dans WF 3.5.À l'aide de cette activité, vous pouvez créer et exécuter un <xref:System.Workflow.Activities.Rules.RuleSet> WF 3.5.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] le moteur de règles WF 3.5 inclus dans Windows Workflow Foundation, consultez la Présentation du moteur de règles Windows Workflow Foundation.Pour plus d'informations sur la migration de règles vers WF dans [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], consultez [Conseils de migration](../../../../docs/framework/windows-workflow-foundation//migration-guidance.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-Policy4`  
  
## Projets dans cet exemple  
  
|Nom du projet|Description|Fichiers principaux|  
|-------------------|-----------------|-------------------------|  
|Policy4|Contient l'activité Policy4 et son concepteur [!INCLUDE[wf1](../../../../includes/wf1-md.md)].|**Policy4.cs** : définition de l'activité Policy4.<br /><br /> **PolicyDesigner.xaml** : concepteur personnalisé pour l'activité Policy4.Il utilise l'éditeur de règles \([classe RuleSetDialog](http://go.microsoft.com/fwlink/?LinkId=150378)\) du moteur de règles [!INCLUDE[wf1](../../../../includes/wf1-md.md)].|  
|ImperativeCodeClientSample|Exemple d'application cliente qui configure et exécute un workflow à l'aide d'une application Policy4 utilisant du code C\# impératif \(aucun concepteur [!INCLUDE[wf1](../../../../includes/wf1-md.md)] utilisé\).|**ApplyDiscount.rules** : fichier avec les définitions de règles [!INCLUDE[wf1](../../../../includes/wf1-md.md)].<br /><br /> **Order.cs** : type qui représente une commande client.Les règles sont appliquées aux objets de ce type.<br /><br /> **Program.cs** : configure et exécute un workflow qui a une activité Policy4 pour appliquer les règles définies dans ApplyDiscount.rules aux instances d'objets Order.<br /><br /> **App.config** : fichier de configuration avec le chemin d'accès du fichier de règles.|  
|DesignerClientSample|Exemple d'application cliente qui configure et exécute un workflow à l'aide d'une application Policy4 dans le concepteur [!INCLUDE[wf1](../../../../includes/wf1-md.md)].|**Sequence1.xaml** : workflow séquentiel qui utilise une activité Policy4 pour effectuer des évaluations de règle.<br /><br /> `Program.cs` : exécute une instance du workflow définie dans Sequence1.xaml.|  
  
## Activité Policy4  
 L'activité Policy4 est une classe qui dérive de <xref:System.Activities.NativeActivity%601> et qui permet aux workflows d'exécuter des ensembles de règles \(RuleSets\) [!INCLUDE[wf1](../../../../includes/wf1-md.md)].L'exemple de code suivant est une définition simplifiée du modèle d'objet public de l'activité.  
  
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
|---------------|-----------------|  
|RuleSet|[Classe RuleSet](http://go.microsoft.com/fwlink/?LinkId=150379) WF pour .NET Framework 3.5 à évaluer lorsque l'activité est exécutée.|  
|TargetObject|Objet sur lequel les règles de la [classe RuleSet](http://go.microsoft.com/fwlink/?LinkId=150379) sont évaluées.|  
|ValidationError|Liste des erreurs de validation retournées par le moteur de règles [!INCLUDE[wf1](../../../../includes/wf1-md.md)] pour .NET Framework 3.5 lors de la validation de la [classe RuleSet](http://go.microsoft.com/fwlink/?LinkId=150379) sur l'objet cible avant l'exécution.|  
  
## Concepteur de l'activité Policy4  
 Le concepteur de Policy4 ajoute la fonctionnalité permettant de configurer une activité Policy4 sans qu'il soit nécessaire d'écrire du code.Après avoir généré la solution, il se trouve dans la boîte à outils, dans la section **Microsoft.Samples.Activities.Rules**.  
  
 Le concepteur WF vous permet de configurer un objet cible et un ensemble de règles \(RuleSet\).Lorsque l'utilisateur clique sur le bouton **Modifier le RuleSet**, la [classe RuleSetDialog](http://go.microsoft.com/fwlink/?LinkId=150378) WF pour [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] s'affiche.Cette boîte de dialogue est l'éditeur de règles de [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] réhébergé.Utilisez l'éditeur pour créer et modifier les règles que l'activité Policy4 exécute.  
  
## Utilisation de cet exemple  
 Aucune configuration particulière n'est requise pour exécuter cet exemple.Ouvrez simplement la solution dans Visual Studio, puis appuyez sur F5 pour exécuter l'application.  
  
 Cet exemple contient deux applications clientes : ImperativeCodeClientSample et DesignerClientSample.Le client ImperativeCodeClientSample montre comment configurer et exécuter l'activité Policy40 à l'aide de code C\# impératif.DesignerClientSample montre comment configurer et exécuter l'activité Policy4 à l'aide du concepteur.  
  
#### Pour exécuter l'application cliente ImperativeCodeClientSample  
  
1.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier solution Policy4Sample.sln.  
  
2.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **ImperativeCodeClientSample**, puis sélectionnez **Définir comme projet de démarrage**.  
  
3.  Pour exécuter le projet, appuyez sur CTRL\+F5.  
  
#### Pour exécuter l'application cliente ImperativeCodeClientSample  
  
1.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier solution Policy4Sample.sln.  
  
2.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **DesignerClientSample**.  
  
    -   Sélectionnez **Définir comme projet de démarrage**.  
  
3.  Appuyez sur Ctrl\+Maj\+B pour compiler le projet.  
  
4.  Pour exécuter le projet, appuyez sur CTRL\+F5.  
  
## Voir aussi