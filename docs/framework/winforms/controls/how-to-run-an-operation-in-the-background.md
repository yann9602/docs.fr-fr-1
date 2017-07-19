---
title: "Comment&#160;: ex&#233;cuter une op&#233;ration en arri&#232;re-plan | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "opérations d'arrière-plan"
  - "tâches en arrière-plan"
  - "threads d'arrière-plan"
  - "BackgroundWorker (classe), exemples"
  - "formulaires, opérations d'arrière-plan"
  - "formulaires, multithreading"
  - "threads (Windows Forms), opérations d'arrière-plan"
ms.assetid: 5b56e2aa-dc05-444f-930c-2d7b23f9ad5b
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: ex&#233;cuter une op&#233;ration en arri&#232;re-plan
Si vous avez une opération qui prendra un certain temps et que vous ne souhaitez pas causer de retards dans votre interface utilisateur, vous pouvez utiliser la classe <xref:System.ComponentModel.BackgroundWorker> pour exécuter l'opération sur un autre thread.  
  
 L'exemple de code suivant montre comment exécuter une longue opération en arrière\-plan.  Le formulaire possède des boutons **Démarrer** et **Annuler**.  Cliquez sur le bouton **Démarrer** pour exécuter une opération asynchrone.  Cliquez sur le bouton **Annuler** pour arrêter une opération asynchrone en cours d'exécution.  Le résultat de chaque opération est affiché dans un <xref:System.Windows.Forms.MessageBox>.  
  
 Cette tâche est très bien prise en charge dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].  
  
 Consultez également [Procédure pas à pas : exécution d'une opération en arrière\-plan](http://msdn.microsoft.com/library/ms233672%20\(v=vs.110\)).  
  
## Exemple  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.ComponentModel.BackgroundWorker>   
 <xref:System.ComponentModel.DoWorkEventArgs>   
 [Comment : implémenter un formulaire qui utilise une opération d'arrière\-plan](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)   
 [BackgroundWorker, composant](../../../../docs/framework/winforms/controls/backgroundworker-component.md)