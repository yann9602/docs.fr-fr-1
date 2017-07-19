---
title: "How to: Cancel a Dataflow Block | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Task Parallel Library, dataflows"
  - "dataflow blocks, canceling in TPL"
  - "TPL dataflow library,canceling dataflow blocks"
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# How to: Cancel a Dataflow Block
Ce document explique comment activer l'annulation dans votre application.  Cet exemple utilise Windows Forms pour indiquer que les éléments de travail sont actifs dans un pipeline de flux de données ainsi que les effets de l'annulation.  
  
> [!TIP]
>  La bibliothèque de flux de données de TPL \(espace de noms<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> \) n'est pas distribuée avec [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choisissez **Gérer les packages NuGet** dans le menu Projet, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.  
  
### Pour Créer une Application Windows Forms  
  
1.  Créez un projet C\# ou une **Application Windows Forms** Visual Basic.  Dans les étapes suivantes, le projet est nommé `CancellationWinForms`.  
  
2.  Dans le concepteur de formulaires pour le formulaire principal, Form1.cs \(Form1.vb pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\), ajouter un contrôle <xref:System.Windows.Forms.ToolStrip>.  
  
3.  Ajoutez un contrôle <xref:System.Windows.Forms.ToolStripButton> au contrôle <xref:System.Windows.Forms.ToolStrip>.  Affectez la propriété <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> à <xref:System.Windows.Forms.ToolStripItemDisplayStyle> et définissez la propriété <xref:System.Windows.Forms.ToolStripItem.Text%2A> pour ajouter des éléments de travail.  
  
4.  Ajoutez un deuxième contrôle <xref:System.Windows.Forms.ToolStripButton> au contrôle <xref:System.Windows.Forms.ToolStrip> .  Affectez la propriété <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> à la valeur <xref:System.Windows.Forms.ToolStripItemDisplayStyle>, la propriété <xref:System.Windows.Forms.ToolStripItem.Text%2A> pour annuler, et la propriété <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> à `False`.  
  
5.  Ajoutez les objets <xref:> System.Windows.Forms.ToolStripProgressBar?qualifyHint=False&autoUpgrade=True au contrôle <xref:System.Windows.Forms.ToolStrip>.  
  
## Création d'un Pipeline de Flux de Données  
 Cette section explique comment créer le pipeline de flux de données qui traite des éléments de travail et met à jour les barres de progression.  
  
#### Pour Créer le Pipeline de Flux de Données  
  
1.  Dans votre projet, ajoutez une référence à System.Threading.Tasks.Dataflow.dll.  
  
2.  Vérifiez que Form1.cs \(Form1.vb pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\) contient les `using` déclarations \(`Imports` dans les instructions [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\).  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  Ajoutez la classe `WorkItem` en tant que type interne de la classe `Form1`.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  Ajoutez les membres de données suivants à la classe `Form1` :  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  Ajoutez la méthode suivante `CreatePipeline` , à la classe `Form1`.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 Étant donné que les blocs de flux de données `incrementProgress` et `decrementProgress` agissent sur l'interface utilisateur, il est important que ces actions se produisent sur le thread de l'interface utilisateur.  Pour ce faire, lors de la construction ces objets fournissent chacun un objet <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> qui contient le jeu de propriétés <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> à <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=fullName>.  La méthode <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=fullName> crée un objet <xref:System.Threading.Tasks.TaskScheduler> qui effectue le travail dans le contexte actuel de synchronisation.  Etant donné que le constructeur `Form1` est appelé du thread de l'interface utilisateur, les actions des blocs de flux de données `incrementProgress` et `decrementProgress` fonctionnent aussi sur le thread de l'interface utilisateur.  
  
 Cet exemple définit la propriété <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> lorsqu'il construit les membres du pipeline.  Comme la propriété <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> annule définitivement l'exécution du bloc de flux de données, le pipeline doit être entièrement recréé après l'utilisateur annule l'opération puis souhaite ajouter plus d'éléments de travail au pipeline.  Pour obtenir un exemple qui illustre un autre moyen d'annuler un bloc de flux de données afin qu'un autre travail puisse être effectuée après une opération soit annulée, consultez [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## Connexion du Pipeline de flux de données à l'interface utilisateur  
 Cette section décrit comment connecter le pipeline de flux de données à l'interface utilisateur.  La création du pipeline et l'ajout des éléments de travail au pipeline sont contrôlés par le gestionnaire d'événements du bouton Ajouter des éléments de travail.  L'annulation est initialisée par le bouton Annuler.  Lorsque l'utilisateur clique sur l'un ou l'autre de ces boutons, l'action appropriée est initialisée de manière asynchrone.  
  
#### Pour se connecter le Pipeline de flux de données à l'interface utilisateur  
  
1.  Dans le Concepteur de formulaires pour le formulaire principal, créez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.ToolStripItem.Click> pour le bouton Ajouter des éléments de travail.  
  
2.  Implémentez l'événement <xref:System.Windows.Forms.ToolStripItem.Click> du bouton Ajouter des éléments de travail.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  Dans le concepteur de formulaires pour le formulaire principal, créez un gestionnaire d'événements pour le gestionnaire d'événements <xref:System.Windows.Forms.ToolStripItem.Click> pour le bouton Annuler.  
  
4.  Implémentez le gestionnaire d'événements <xref:System.Windows.Forms.ToolStripItem.Click> pour le bouton Annuler.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## Exemple  
 L'exemple suivant montre le code complet pour Form1.cs \(Form1.vb pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\).  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 L'illustration suivante présente l'application en cours d'exécution.  
  
 ![Application Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow\_Cancellation")  
  
## Programmation fiable  
  
## Voir aussi  
 [Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)