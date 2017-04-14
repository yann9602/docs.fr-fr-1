---
title: "Proc&#233;dure pas &#224; pas&#160;: ex&#233;cution d&#39;une op&#233;ration en arri&#232;re-plan | Microsoft Docs"
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
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Proc&#233;dure pas &#224; pas&#160;: ex&#233;cution d&#39;une op&#233;ration en arri&#232;re-plan
Si vous avez une opération dont l'exécution va prendre beaucoup de temps et que vous ne souhaitez pas causer de retards dans votre interface utilisateur, vous pouvez utiliser la classe <xref:System.ComponentModel.BackgroundWorker> pour exécuter l'opération sur un autre thread.  
  
 Pour une liste complète du code utilisé dans cet exemple, consultez [Comment : exécuter une opération en arrière\-plan](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour exécuter une opération en arrière\-plan  
  
1.  Avec votre formulaire actif dans le Concepteur Windows Forms, faites glisser deux contrôles <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le formulaire, puis définissez les propriétés `Name` et <xref:System.Windows.Forms.Control.Text%2A> des boutons en fonction du tableau suivant.  
  
    |Button|Nom|Texte|  
    |------------|---------|-----------|  
    |`button1`|`startBtn`|Démarrer|  
    |`button2`|`cancelBtn`|Cancel|  
  
2.  Ouvrez la **boîte à outils**, cliquez sur l'onglet **Composants**, puis faites glisser le composant <xref:System.ComponentModel.BackgroundWorker> sur votre formulaire.  
  
     Le composant `backgroundWorker1` apparaît dans la **barre d'état des composants**.  
  
3.  Dans la fenêtre **Propriétés**, affectez à la propriété <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> la valeur `true`.  
  
4.  Dans la fenêtre **Propriétés**, cliquez sur le bouton **Événements**, puis double\-cliquez sur les événements <xref:System.ComponentModel.BackgroundWorker.DoWork> et <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> pour créer des gestionnaires d'événements.  
  
5.  Insérez votre code dont l'exécution prend beaucoup de temps dans le gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.DoWork>.  
  
6.  Extrayez, de la propriété <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> du paramètre <xref:System.ComponentModel.DoWorkEventArgs>, tous les paramètres requis par l'opération.  
  
7.  Assignez le résultat du calcul à la propriété <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> de <xref:System.ComponentModel.DoWorkEventArgs>.  
  
     Celui\-ci sera accessible par le gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]  
  
8.  Insérez le code pour récupérer le résultat de votre opération dans le gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]  
  
9. Implémentez la méthode `TimeConsumingOperation`.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]  
  
10. Dans le Concepteur Windows Forms, doublez\-cliquez sur `startButton` pour créer le gestionnaire d'événements <xref:System.Windows.Forms.Control.Click>.  
  
11. Appelez la méthode <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> dans le gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> pour `startButton`.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]  
  
12. Dans le Concepteur Windows Forms, doublez\-cliquez sur `cancelButton` pour créer le gestionnaire d'événements <xref:System.Windows.Forms.Control.Click>.  
  
13. Appelez la méthode <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> dans le gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> pour `cancelButton`.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]  
  
14. En haut du fichier, importez les espaces de noms System.ComponentModel et System.Threading.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]  
  
15. Appuyez sur F6 pour générer la solution, puis sur CTRL\+F5 pour exécuter l'application en dehors du débogueur.  
  
> [!NOTE]
>  Si vous appuyez sur F5 pour exécuter l'application sous le débogueur, l'exception levée dans la méthode `TimeConsumingOperation` est interceptée et affichée par le débogueur.  Lorsque vous exécutez l'application en dehors du débogueur, <xref:System.ComponentModel.BackgroundWorker> gère l'exception et le met en cache dans la propriété <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> de <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.  
  
1.  Cliquez sur le bouton **Démarrer** pour exécuter une opération asynchrone, puis cliquez sur le bouton **Annuler** pour arrêter une opération asynchrone en cours d'exécution.  
  
     Le résultat de chaque opération est affiché dans un <xref:System.Windows.Forms.MessageBox>.  
  
## Étapes suivantes  
  
-   Implémentez un formulaire qui permet de suivre la progression d'une opération asynchrone.  Pour plus d'informations, consultez [Comment : implémenter un formulaire qui utilise une opération d'arrière\-plan](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
-   Implémentez une classe qui prend en charge le modèle asynchrone pour les composants.  Pour plus d'informations, consultez [Implementing the Event\-based Asynchronous Pattern](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## Voir aussi  
 <xref:System.ComponentModel.BackgroundWorker>   
 <xref:System.ComponentModel.DoWorkEventArgs>   
 [Comment : implémenter un formulaire qui utilise une opération d'arrière\-plan](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)   
 [Comment : exécuter une opération en arrière\-plan](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)   
 [BackgroundWorker, composant](../../../../docs/framework/winforms/controls/backgroundworker-component.md)