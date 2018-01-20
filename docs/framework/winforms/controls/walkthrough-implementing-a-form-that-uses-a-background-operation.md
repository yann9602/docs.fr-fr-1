---
title: "Procédure pas à pas : implémentation d'un formulaire qui utilise une opération d'arrière-plan"
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
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- threading [Windows Forms], walkthroughs
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 4691b796-9200-471a-89c3-ba4c7cc78c03
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aaee6f1d650e6af57ab05ad56b5578e094ee50ef
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-implementing-a-form-that-uses-a-background-operation"></a>Procédure pas à pas : implémentation d'un formulaire qui utilise une opération d'arrière-plan
Si vous avez une opération qui prendra un certain temps, et vous ne souhaitez pas votre interface utilisateur (IU) cesse de répondre ou « se bloque », vous pouvez utiliser la <xref:System.ComponentModel.BackgroundWorker> classe pour exécuter l’opération sur un autre thread.  
  
 Cette procédure pas à pas montre comment utiliser la <xref:System.ComponentModel.BackgroundWorker> classe pour effectuer des calculs de longue durées « en arrière-plan », tandis que l’interface utilisateur reste réactive.  Lorsque vous avez terminé, vous disposerez d’une application qui calcule les nombres de Fibonacci de manière asynchrone. Même si le calcul d’un nombre de Fibonacci élevé peut prendre beaucoup de temps, le thread d’interface utilisateur principal ne sera pas interrompu et le formulaire restera réactif tout au long de l’opération de calcul.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d’une application Windows  
  
-   Création d’un <xref:System.ComponentModel.BackgroundWorker> dans votre formulaire  
  
-   Ajout de gestionnaires d’événements asynchrones  
  
-   Ajout de rapports de progression et prise en charge de l’annulation  
  
 Pour obtenir une liste complète du code utilisé dans cet exemple, consultez l’article [Comment : implémenter un formulaire qui utilise une opération d’arrière-plan](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Création du projet  
 La première étape consiste à créer le projet et à configurer le formulaire.  
  
#### <a name="to-create-a-form-that-uses-a-background-operation"></a>Pour créer un formulaire qui utilise une opération d’arrière-plan  
  
1.  Créez un projet d’application Windows appelé `BackgroundWorkerExample`. Pour plus d’informations, consultez l’article [Comment : créer un projet d’application Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Form1** et sélectionnez **Renommer** dans le menu contextuel. Remplacez le nom de fichier par `FibonacciCalculator`. Cliquez sur le bouton **Oui** lorsque l’on vous demande si vous souhaitez renommer toutes les références à l’élément de code « `Form1` ».  
  
3.  Faites glisser un <xref:System.Windows.Forms.NumericUpDown> contrôle depuis la **boîte à outils** vers le formulaire. Définir le <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> propriété `1` et <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> propriété `91`.  
  
4.  Ajouter deux <xref:System.Windows.Forms.Button> contrôles au formulaire.  
  
5.  Renommez le premier <xref:System.Windows.Forms.Button> contrôle `startAsyncButton` et définir le <xref:System.Windows.Forms.Control.Text%2A> propriété `Start Async`. Renommez le second <xref:System.Windows.Forms.Button> contrôle `cancelAsyncButton`et définissez la <xref:System.Windows.Forms.Control.Text%2A> propriété `Cancel Async`. Définir son <xref:System.Windows.Forms.Control.Enabled%2A> propriété `false`.  
  
6.  Créer un gestionnaire d’événements pour les deux le <xref:System.Windows.Forms.Button> contrôles <xref:System.Windows.Forms.Control.Click> événements. Pour plus d’informations, consultez l’article [Comment : créer des gestionnaires d’événements à l’aide du concepteur](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
7.  Faites glisser un <xref:System.Windows.Forms.Label> contrôle depuis la **boîte à outils** vers le formulaire et renommez-le `resultLabel`.  
  
8.  Faites glisser un <xref:System.Windows.Forms.ProgressBar> contrôle depuis la **boîte à outils** vers le formulaire.  
  
## <a name="creating-a-backgroundworker-in-your-form"></a>Création d’un composant BackgroundWorker dans votre formulaire  
 Vous pouvez créer le <xref:System.ComponentModel.BackgroundWorker> pour votre opération asynchrone à l’aide de la **Windows** **Concepteur Forms**.  
  
#### <a name="to-create-a-backgroundworker-with-the-designer"></a>Pour créer un composant BackgroundWorker à l’aide du concepteur  
  
-   À partir de la **composants** onglet de la **boîte à outils**, faites glisser un <xref:System.ComponentModel.BackgroundWorker> vers le formulaire.  
  
## <a name="adding-asynchronous-event-handlers"></a>Ajout de gestionnaires d’événements asynchrones  
 Vous êtes maintenant prêt à ajouter des gestionnaires d’événements pour le <xref:System.ComponentModel.BackgroundWorker> événements asynchrones du composant. L’opération de longue durée qui s’exécutera en arrière-plan et calculera les nombres de Fibonacci est appelée par l’un de ces gestionnaires d’événements.  
  
#### <a name="to-implement-asynchronous-event-handlers"></a>Pour implémenter des gestionnaires d’événements asynchrones  
  
1.  Dans le **propriétés** fenêtre, avec les <xref:System.ComponentModel.BackgroundWorker> composant étant toujours sélectionnée, cliquez sur le **événements** bouton. Double-cliquez sur le <xref:System.ComponentModel.BackgroundWorker.DoWork> et <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> événements pour créer des gestionnaires d’événements. Pour plus d’informations sur l’utilisation des gestionnaires d’événements, consultez l’article [Comment : créer des gestionnaires d’événements à l’aide du concepteur](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
2.  Dans votre formulaire, créez une nouvelle méthode appelée `ComputeFibonacci`. Cette méthode exécute l’opération requise en arrière-plan. Ce code décrit l’implémentation récursive de l’algorithme de Fibonacci qui est particulièrement inefficace et nécessite beaucoup plus de temps pour traiter des nombres élevés. Il est utilisé ici à titre d’exemple, dans le but d’illustrer une opération qui peut occasionner des temps d’inactivité assez longs pour votre application.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#10)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#10)]
     [!code-vb[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#10)]  
  
3.  Dans le <xref:System.ComponentModel.BackgroundWorker.DoWork> Gestionnaire d’événements, ajoutez un appel à la `ComputeFibonacci` (méthode). Prenez le premier paramètre `ComputeFibonacci` à partir de la <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> propriété de la <xref:System.ComponentModel.DoWorkEventArgs>. Le <xref:System.ComponentModel.BackgroundWorker> et <xref:System.ComponentModel.DoWorkEventArgs> paramètres seront utilisées ultérieurement pour le rapport de progression et annulation prennent en charge. Affecter la valeur de retour à partir de `ComputeFibonacci` à la <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> propriété de la <xref:System.ComponentModel.DoWorkEventArgs>. Ce résultat sera disponible pour le <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> Gestionnaire d’événements.  
  
    > [!NOTE]
    >  Le <xref:System.ComponentModel.BackgroundWorker.DoWork> Gestionnaire d’événements ne fait pas référence à la `backgroundWorker1` variable d’instance directement, car cette opération associerait ce gestionnaire d’événements à une instance spécifique de <xref:System.ComponentModel.BackgroundWorker>. Au lieu de cela, une référence à la <xref:System.ComponentModel.BackgroundWorker> qui a déclenché cet événement est récupérée à partir de la `sender` paramètre. Ceci est important lorsque le formulaire héberge plusieurs <xref:System.ComponentModel.BackgroundWorker>. Il est également important de ne pas manipuler d’objets interface utilisateur dans votre <xref:System.ComponentModel.BackgroundWorker.DoWork> Gestionnaire d’événements. À la place, communiquez à l’interface utilisateur via la <xref:System.ComponentModel.BackgroundWorker> événements.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
4.  Dans le `startAsyncButton` du contrôle <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements, ajoutez le code qui commence l’opération asynchrone.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#13)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#13)]
     [!code-vb[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#13)]  
  
5.  Dans le <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> Gestionnaire d’événements, assignez le résultat du calcul à la `resultLabel` contrôle.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#6)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#6)]  
  
## <a name="adding-progress-reporting-and-support-for-cancellation"></a>Ajout de rapports de progression et prise en charge de l’annulation  
 Pour les opérations asynchrones chronophages, il est souvent utile d’informer l’utilisateur de la progression et de lui permettre d’annuler l’opération. La <xref:System.ComponentModel.BackgroundWorker> classe fournit un événement qui vous permet de publier la progression en tant que résultat de l’opération en arrière-plan. Il fournit également un indicateur qui permet à votre code de travail détecter un appel à <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> et l’interrompre.  
  
#### <a name="to-implement-progress-reporting"></a>Pour implémenter le rapport de progression  
  
1.  Dans la fenêtre **Propriétés**, sélectionnez `backgroundWorker1`. Définir le <xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A> et <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> propriétés `true`.  
  
2.  Déclarez deux variables dans le formulaire `FibonacciCalculator`. Elles seront utilisées pour suivre la progression.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#14)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#14)]
     [!code-vb[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#14)]  
  
3.  Ajoutez un gestionnaire d'événements pour l'événement <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>. Dans le <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Gestionnaire d’événements, la mise à jour la <xref:System.Windows.Forms.ProgressBar> avec la <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> propriété de le <xref:System.ComponentModel.ProgressChangedEventArgs> paramètre.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#7)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#7)]  
  
#### <a name="to-implement-support-for-cancellation"></a>Pour implémenter la prise en charge de l’annulation  
  
1.  Dans le `cancelAsyncButton` du contrôle <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements, ajoutez le code qui annule l’opération asynchrone.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#4)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#4)]  
  
2.  Les fragments de code suivants de la méthode `ComputeFibonacci` indiquent la progression et prennent en charge l’opération d’annulation.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#11)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#11)]
     [!code-vb[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#11)]  
    [!code-cpp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#12)]
    [!code-csharp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#12)]
    [!code-vb[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#12)]  
  
## <a name="checkpoint"></a>Point de contrôle  
 À ce stade, vous pouvez compiler et exécuter l’application Fibonacci Calculator.  
  
#### <a name="to-test-your-project"></a>Pour tester votre projet  
  
-   Appuyez sur F5 pour compiler et exécuter l'application.  
  
     Alors que le calcul s’exécute en arrière-plan, vous verrez la <xref:System.Windows.Forms.ProgressBar> affiche la progression du calcul en voie d’achèvement. Vous pouvez également annuler l’opération en attente.  
  
     Pour les nombres peu élevés, le calcul devrait être très rapide, mais pour les nombres plus élevés, le délai est bien plus long. Si vous entrez une valeur supérieure ou égale à 30, vous devriez constater un délai de quelques secondes, selon la vitesse de votre ordinateur. Pour des valeurs supérieures à 40, l’opération de calcul peut prendre quelques minutes ou heures. Tandis que la calculatrice traite un nombre de Fibonacci élevé, vous pouvez librement déplacer le formulaire, le réduire, l’agrandir et même le faire disparaître. Cela est possible car le thread d’interface utilisateur principal n’attend pas que le calcul soit terminé.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant que vous avez implémenté un formulaire qui utilise un <xref:System.ComponentModel.BackgroundWorker> composant d’effectuer un calcul en arrière-plan, vous pouvez Explorer d’autres possibilités pour les opérations asynchrones :  
  
-   Utilisez plusieurs <xref:System.ComponentModel.BackgroundWorker> objets pour plusieurs opérations simultanées.  
  
-   Pour déboguer votre application multithread, consultez l’article [Comment : utiliser la fenêtre Threads](/visualstudio/debugger/how-to-use-the-threads-window).  
  
-   Implémentez votre propre composant qui prend en charge le modèle de programmation asynchrone. Pour plus d’informations, consultez l’article [Vue d’ensemble du modèle asynchrone basé sur les événements](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
    > [!CAUTION]
    >  Quand vous utilisez le multithreading, vous vous exposez potentiellement à des bogues très sérieux et complexes. Consultez les [Meilleures pratiques pour le threading managé](../../../../docs/standard/threading/managed-threading-best-practices.md) avant d’implémenter une solution qui utilise le multithreading.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Bonnes pratiques de threading géré](../../../../docs/standard/threading/managed-threading-best-practices.md)  
 [Multithreading dans les composants](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [NOT IN BUILD : Multithreading en Visual Basic](http://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)  
 [Comment : implémenter un formulaire qui utilise une opération d’arrière-plan](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Procédure pas à pas : exécution d’une opération en arrière-plan](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 [Composant BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
