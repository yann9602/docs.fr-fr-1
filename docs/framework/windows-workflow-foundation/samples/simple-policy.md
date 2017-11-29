---
title: Simple Policy
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0c704a9f3f27d63fb1a28db61f03cdc9b8de4370
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="simple-policy"></a>Simple Policy
Cet exemple indique comment utiliser une activité <xref:System.Workflow.Activities.PolicyActivity> dans un workflow.  
  
 Le workflow séquentiel de cet exemple est créé à l'aide d'une activité <xref:System.Workflow.Activities.PolicyActivity>. Le workflow définit les champs `orderValue`, `customerType` et `discount` utilisés pour configurer un workflow de remise de produit. Les règles configurées dans le fichier de règles définissent une valeur de remise basée sur `orderValue` et sur `customerType`. Les champs `orderValue` et `customerType` sont définis dans la définition de classe `SimplePolicyWorkflow` et peuvent être changés pour modifier le comportement. La remise obtenue est écrite dans la console dans le gestionnaire d'événements <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> défini dans la classe `SimplePolicyWorkflow`.  
  
### <a name="to-build-the-sample"></a>Pour générer l'exemple  
  
1.  Ouvrez la solution dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Générez la solution en appuyant sur Ctrl+Maj+B.  
  
3.  Exécutez la solution sans débogage en appuyant sur Ctrl+F5.  
  
### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
-   Dans la fenêtre d'invite de commandes du Kit de développement logiciel (SDK), exécutez le fichier .exe dans le dossier SimplePolicy\bin\debug (ou le dossier SimplePolicy\bin pour la version Visual Basic de l'exemple), situé sous le dossier principal de l'exemple.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer :  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant :  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [Stratégie avancée](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
