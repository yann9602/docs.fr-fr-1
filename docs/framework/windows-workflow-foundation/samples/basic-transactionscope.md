---
title: "Bases de TransactionScope | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e22b76a-76de-43b4-9be7-7a86ed3d5a44
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# Bases de TransactionScope
Cet exemple est composé de quatre scénarios qui s'exécutent pour montrer comment imbriquer des instances <xref:System.Activities.Statements.TransactionScope>.Le premier scénario présente l'imbrication d'une activité tierce dont l'auteur ignore totalement la construction.Les deuxième et troisième scénarios montrent comment les délais d'expiration sont respectés, et le dernier scénario présente le paramètre <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A>.  
  
## Imbrication de TransactionScopeActivity  
 Le workflow du premier scénario se compose d'une séquence de deux activités <xref:System.Activities.Statements.WriteLine> et d'un <xref:System.Activities.Statements.TransactionScope>.Le corps de <xref:System.Activities.Statements.TransactionScope> est une séquence de deux autres activités <xref:System.Activities.Statements.WriteLine>, d'une activité personnalisée qui imprime l'identificateur local de la transaction et d'une activité tierce.L'activité `TransactionScopeTest` tierce contient un <xref:System.Activities.Statements.TransactionScope>, mais l'auteur du workflow n'a aucun moyen de le savoir.Ce scénario montre que les activités <xref:System.Activities.Statements.TransactionScope> peuvent être imbriquées.  
  
## Délais d'expiration  
 Le workflow du deuxième scénario est presque identique au premier.`TransactionScopeTest` a été remplacé par un <xref:System.Activities.Statements.TransactionScope>.Le corps de <xref:System.Activities.Statements.TransactionScope> est un délai de cinq secondes et le délai d'expiration de la transaction est défini à deux secondes.La valeur du délai d'expiration de <xref:System.Activities.Statements.TransactionScope> est de 10 secondes.Notez que le plus petit délai d'expiration de l'étendue est respecté et que la transaction expire.  
  
 Le workflow du troisième scénario est presque identique au deuxième scénario.L'activité de délai a été déplacée du corps du <xref:System.Activities.Statements.TransactionScope> interne vers l'emplacement immédiatement après lui dans la séquence qui est le corps du <xref:System.Activities.Statements.TransactionScope> externe.La transaction expire toujours, mais cela est dû au fait que le délai d'expiration de deux secondes du <xref:System.Activities.Statements.TransactionScope> interne ne s'applique plus.La transaction expire au bout de 10 secondes lorsque le délai d'expiration du <xref:System.Activities.Statements.TransactionScope> externe est dépassé.  
  
## Abandon en cas d'échec de la transaction  
 Ce workflow est semblable au troisième scénario, excepté que les délais d'expiration ont été remplacés par la propriété <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A>.Notez que les indicateurs de tous les enfants internes, s'ils sont définis, doivent correspondre au <xref:System.Activities.Statements.TransactionScope> externe.Dans ce scénario, ils ne le sont pas, et une exception est levée lorsque le workflow s'ouvre.  
  
#### Pour exécuter l'exemple  
  
1.  Ouvrez la solution BasicTransactionScopeSample.sl dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B ou sélectionnez **Générer la solution** dans le menu **Générer**.  
  
3.  Une fois que la génération a réussi, appuyez sur F5 ou sélectionnez **Démarrer le débogage** dans le menu **Déboguer**.Vous pouvez également appuyer sur CTRL\+F5 ou sélectionner **Exécuter sans débogage** dans le menu **Déboguer** pour effectuer une exécution sans débogage.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Transactions\BasicTransactionScope`  
  
## Voir aussi