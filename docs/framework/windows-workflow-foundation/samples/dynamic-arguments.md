---
title: "Arguments dynamiques | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 122ad479-d306-4602-a943-5aefe711329d
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Arguments dynamiques
Cet exemple montre comment implémenter une activité pour laquelle les arguments sont définis par le consommateur de l'activité plutôt que par l'auteur de l'activité.Pour ce faire, il substitue la façon dont le runtime construit les métadonnées de l'activité.  
  
## Détails de l'exemple  
 Avant l'exécution, le runtime génère une description d'une activité en examinant les membres publics du type d'activité et en déclarant automatiquement les arguments, les variables, les activités enfants et les délégués d'activité en tant qu'éléments des métadonnées d'une activité.Il s'assure ainsi que la construction d'un workflow est correcte, et gère les relations à l'exécution et les règles de durée de vie.En général, un auteur d'activité définit les arguments d'une activité en spécifiant des membres publics sur le type d'activité qui dérivent d'<xref:System.Activities.Argument>.Pour chaque membre public qui dérive d'<xref:System.Activities.Argument>, le runtime crée un <xref:System.Activities.RuntimeArgument> et le lie à l'ensemble d'arguments fourni par l'utilisateur sur ce membre.Dans certains cas, toutefois, le consommateur de l'activité fournit une configuration qui détermine l'ensemble d'arguments.Un auteur d'activité substitue <xref:System.Activities.Activity.CacheMetadata%2A> pour personnaliser la façon dont les métadonnées de l'activité sont générées, ce qui inclut l'ensemble d'arguments associé à l'activité.  
  
 Cet exemple montre comment générer dynamiquement une liste d'arguments pour une activité qui appelle une méthode.Le consommateur de l'activité spécifie le type et le nom de la méthode qu'ils veulent appeler avec une collection d'arguments à passer à cette méthode.  
  
> [!NOTE]
>  Le but de cet exemple est de montrer comment substituer <xref:System.Activities.CodeActivity.CacheMetadata%2A> et comment utiliser <xref:System.Activities.RuntimeArgument>.Il y a plusieurs points à noter concernant les types des méthodes que cette activité peut appeler.Par exemple, elle ne fonctionne pas avec des génériques ou des tableaux de paramètres.L'activité <xref:System.Activities.Statements.InvokeMethod> fournie dans le .NET Framework traite ces cas, et plus encore.  
  
 L'activité `MethodInvoke` substitue <xref:System.Activities.CodeActivity.CacheMetadata%2A> et commence par créer un <xref:System.Activities.RuntimeArgument> pour gérer le résultat de l'appel de méthode.Elle lie ce <xref:System.Activities.RuntimeArgument> à l'<xref:System.Activities.OutArgument> définissable publiquement nommé `Result`.Si `MethodInvoke.Result` est `null`, le runtime le remplit automatiquement avec un <xref:System.Activities.OutArgument> configuré avec l'expression par défaut pour son type.Ce comportement signifie qu'un auteur d'activité n'a jamais besoin de vérifier si une propriété d'argument est `null`.  
  
 Ensuite, la substitution <xref:System.Activities.CodeActivity.CacheMetadata%2A> détermine le `MethodInfo` qu'il utilise pour l'appel du `MethodName` et du `TargetType` fournis par l'utilisateur.La méthode `DetermineMethodInfo` prend le paramètre <xref:System.Activities.CodeActivityMetadata> passé à la substitution <xref:System.Activities.CodeActivity.CacheMetadata%2A> afin que toutes les erreurs de configuration puissent être signalées en tant qu'erreurs de validation.Pour ce faire, il suffit d'appeler `metadata.AddValidationError`.  
  
 Une fois `MethodInfo` défini, l'exemple itère au sein des paramètres `MethodInfo`.Pour chaque paramètre, il crée un <xref:System.Activities.RuntimeArgument> et le lie à l'argument correspondant dans la collection fournie par l'utilisateur de la propriété `Parameters`.Enfin, la collection de <xref:System.Activities.RuntimeArgument> est associée à l'activité en appelant `metadata.SetArgumentsCollection`.  
  
 Notez que la résolution des arguments peut s'effectuer à l'aide d'un <xref:System.Activities.RuntimeArgument>, comme dans le cas de `resultArgument`, ou de l'argument fourni par l'utilisateur, comme dans le cas de la collection `Parameters`.  
  
#### Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier DynamicArguments.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl\+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\DynamicArguments`  
  
## Voir aussi