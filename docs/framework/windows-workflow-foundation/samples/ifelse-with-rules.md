---
title: IfElse With Rules
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bec818ca5492e9a49a602a4f7baef4b45cb073c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ifelse-with-rules"></a>IfElse With Rules
Cet exemple illustre l'utilisation d'une condition de règle avec une activité <xref:System.Workflow.Activities.IfElseActivity>.  
  
 L'exemple transmet un paramètre `OrderValue` depuis l'hôte. La valeur du paramètre est utilisée dans une condition de règle sur la première branche de l'activité <xref:System.Workflow.Activities.IfElseActivity>. Si la valeur est inférieure à 10 000, la première branche s’exécute et le <xref:System.Workflow.Activities.CodeActivity> activité de la première branche imprime **obtenir de l’approbation du Gestionnaire de** à la console. Si la valeur est supérieure à 10 000, le <xref:System.Workflow.Activities.CodeActivity> activité dans la deuxième branche s’exécute et imprime **obtenir de l’approbation du vice-président**.  
  
### <a name="to-build-the-sample"></a>Pour générer l'exemple  
  
1.  Ouvrez la solution dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Générez la solution en appuyant sur Ctrl+Maj+B.  
  
3.  Exécutez la solution sans débogage en appuyant sur Ctrl+F5.  
  
### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
-   Dans la fenêtre Invite de commandes du Kit de développement logiciel (SDK), exécutez le fichier .exe dans le dossier IfElseWithRules\bin\debug (ou le dossier IfElseWithRules\bin pour la version Visual Basic de l'exemple), situé sous le dossier principal de l'exemple.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer :  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant :  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
