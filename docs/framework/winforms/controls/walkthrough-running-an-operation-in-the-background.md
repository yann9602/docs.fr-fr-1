---
title: "Procédure pas à pas : exécution d'une opération en arrière-plan"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: de485eb0b9c67ee9c3c897b6521971f50aaf751c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-running-an-operation-in-the-background"></a>Procédure pas à pas : exécution d'une opération en arrière-plan
Si vous avez une opération qui prendra un certain temps et que vous ne souhaitez pas causer de retards dans votre interface utilisateur, vous pouvez utiliser la classe <xref:System.ComponentModel.BackgroundWorker> pour exécuter l'opération sur un autre thread.  
  
 Pour obtenir une liste complète du code utilisé dans cet exemple, consultez [Comment : exécuter une opération en arrière-plan](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-run-an-operation-in-the-background"></a>Pour exécuter une opération en arrière-plan  
  
1.  Avec votre formulaire actif dans le Concepteur Windows Forms, faites glisser deux <xref:System.Windows.Forms.Button> des contrôles de la **boîte à outils** pour le formulaire et définissez la `Name` et <xref:System.Windows.Forms.Control.Text%2A> propriétés des boutons conformément au tableau suivant.  
  
    |Bouton|Nom|Texte|  
    |------------|----------|----------|  
    |`button1`|`startBtn`|**Start**|  
    |`button2`|`cancelBtn`|**Annuler**|  
  
2.  Ouvrez le **boîte à outils**, cliquez sur le **composants** onglet, puis faites glisser le <xref:System.ComponentModel.BackgroundWorker> composant vers votre formulaire.  
  
     Le `backgroundWorker1` composant apparaît dans le **barre d’état du composant**.  
  
3.  Dans le **propriétés** , configurez la <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> propriété `true`.  
  
4.  Dans le **propriétés** fenêtre, cliquez sur le **événements** bouton, puis double-cliquez sur le <xref:System.ComponentModel.BackgroundWorker.DoWork> et <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> événements pour créer des gestionnaires d’événements.  
  
5.  Insérez votre code qui prennent du temps dans le <xref:System.ComponentModel.BackgroundWorker.DoWork> Gestionnaire d’événements.  
  
6.  Extraire les paramètres requis par l’opération à partir de la <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> propriété de le <xref:System.ComponentModel.DoWorkEventArgs> paramètre.  
  
7.  Assignez le résultat du calcul à la <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> propriété de la <xref:System.ComponentModel.DoWorkEventArgs>.  
  
     Il est disponible pour être le <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> Gestionnaire d’événements.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]  
  
8.  Insérer du code pour récupérer le résultat de votre opération dans le <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> Gestionnaire d’événements.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]  
  
9. Implémentez la méthode `TimeConsumingOperation`.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]  
  
10. Dans le Concepteur Windows Forms, double-cliquez sur `startButton` pour créer le <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements.  
  
11. Appelez le <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> méthode dans le <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements pour `startButton`.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]  
  
12. Dans le Concepteur Windows Forms, double-cliquez sur `cancelButton` pour créer le <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements.  
  
13. Appelez le <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> méthode dans le <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements pour `cancelButton`.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]  
  
14. En haut du fichier, importez les espaces de noms System.ComponentModel et System.Threading.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]  
  
15. Appuyez sur F6 pour générer la solution, puis appuyez sur CTRL + F5 pour exécuter l’application en dehors du débogueur.  
  
> [!NOTE]
>  Si vous appuyez sur F5 pour exécuter l’application sous le débogueur, l’exception est levée dans le `TimeConsumingOperation` méthode est interceptée et affichée par le débogueur. Lorsque vous exécutez l’application en dehors du débogueur, la <xref:System.ComponentModel.BackgroundWorker> gère l’exception et met en cache dans le <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> propriété de la <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.  
  
1.  Cliquez sur le **Démarrer** bouton pour exécuter une opération asynchrone, puis cliquez sur le **Annuler** bouton pour arrêter une opération asynchrone en cours d’exécution.  
  
     Le résultat de chaque opération est affiché dans un <xref:System.Windows.Forms.MessageBox>.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   Implémenter un formulaire qui signale la progression au fur et une opération asynchrone. Pour plus d’informations, consultez [Comment : implémenter un formulaire qui utilise une opération d’arrière-plan](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
-   Implémentez une classe qui prend en charge le modèle asynchrone pour les composants. Pour plus d’informations, consultez [implémentation du modèle asynchrone basé sur événement](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [Comment : implémenter un formulaire qui utilise une opération d’arrière-plan](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Guide pratique pour exécuter une opération en arrière-plan](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Composant BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
