---
title: "Proc&#233;dure pas &#224; pas&#160;: impl&#233;mentation d&#39;un formulaire qui utilise une op&#233;ration d&#39;arri&#232;re-plan | Microsoft Docs"
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
  - "BackgroundWorker (composant)"
  - "formulaires, opérations d'arrière-plan"
  - "formulaires, multithreading"
  - "threads (Windows Forms), opérations d'arrière-plan"
  - "threads (Windows Forms), formulaires"
  - "threads (Windows Forms), procédures pas à pas"
ms.assetid: 4691b796-9200-471a-89c3-ba4c7cc78c03
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# Proc&#233;dure pas &#224; pas&#160;: impl&#233;mentation d&#39;un formulaire qui utilise une op&#233;ration d&#39;arri&#232;re-plan
Si vous avez une opération dont l'exécution va prendre beaucoup de temps et que vous ne souhaitez pas que votre interface utilisateur cesse de répondre ou « se bloque », vous pouvez utiliser la classe <xref:System.ComponentModel.BackgroundWorker> pour exécuter l'opération sur un autre thread.  
  
 Cette procédure pas à pas illustre comment utiliser la classe <xref:System.ComponentModel.BackgroundWorker> pour exécuter « en arrière\-plan » des calculs qui prennent du temps, pendant que l'interface utilisateur continue de répondre.  Lorsque vous avez terminé, vous disposez alors d'une application qui calcule les nombres de Fibonacci de façon asynchrone.  Si le calcul d'un nombre de Fibonacci élevé peut prendre un nombre important d'heures, le thread d'interface utilisateur principal n'est pas interrompu par ce délai, et le formulaire continu de répondre pendant le calcul.  
  
 Cette procédure pas à pas illustre les tâches suivantes :  
  
-   Création d'une application Windows  
  
-   Création d'un <xref:System.ComponentModel.BackgroundWorker> dans votre formulaire  
  
-   Ajout de gestionnaires d'événements asynchrones  
  
-   Ajout de rapport de progression et de prise en charge de l'annulation  
  
 Pour une liste complète du code utilisé dans cet exemple, consultez [Comment : implémenter un formulaire qui utilise une opération d'arrière\-plan](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Création du projet  
 La première étape consiste à créer le projet et à configurer le formulaire.  
  
#### Pour créer un formulaire qui utilise une opération d'arrière\-plan  
  
1.  Créez un projet d'application Windows appelé `BackgroundWorkerExample`.  Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **Form1** et sélectionnez **Renommer** dans le menu contextuel.  Remplacez le nom de fichier par  `FibonacciCalculator`.  Cliquez sur le bouton **Oui** à la question de savoir si vous souhaitez renommer toutes les références à l'élément de code "`Form1`".  
  
3.  Faites glisser un contrôle <xref:System.Windows.Forms.NumericUpDown> de la **Boîte à outils** vers le formulaire.  Attribuez à la propriété <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> la valeur `1` à et la propriété <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> la valeur `91`.  
  
4.  Ajoutez deux contrôles <xref:System.Windows.Forms.Button> au formulaire.  
  
5.  Renommez le premier contrôle <xref:System.Windows.Forms.Button> en `startAsyncButton` et attribuez à la propriété <xref:System.Windows.Forms.Control.Text%2A> la valeur `Start Async`.  Renommez le second contrôle <xref:System.Windows.Forms.Button> en `cancelAsyncButton` et attribuez à la propriété <xref:System.Windows.Forms.Control.Text%2A> la valeur `Cancel Async`.  affectez à sa propriété <xref:System.Windows.Forms.Control.Enabled%2A> la valeur `false`.  
  
6.  Créez un gestionnaire d'événements pour les deux événements <xref:System.Windows.Forms.Control.Click> du contrôle <xref:System.Windows.Forms.Button>.  Pour plus d'informations, consultez [How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/fr-fr/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
7.  Faites glisser un contrôle <xref:System.Windows.Forms.Label> de la **Boîte à outils** sur le formulaire et renommez\-le `resultLabel`.  
  
8.  Faites glisser un contrôle <xref:System.Windows.Forms.ProgressBar> de la **Boîte à outils** vers le formulaire.  
  
## Création d'un BackgroundWorker dans votre formulaire  
 Vous pouvez créer le <xref:System.ComponentModel.BackgroundWorker> pour votre opération asynchrone à l'aide du **Concepteur** **Windows Forms**.  
  
#### Pour créer un BackgroundWorker avec le concepteur  
  
-   À partir de l'onglet **Composants** de la **Boîte à outils**, faites glisser un <xref:System.ComponentModel.BackgroundWorker> jusqu'au formulaire.  
  
## Ajout de gestionnaires d'événements asynchrones  
 Vous êtes maintenant prêt à ajouter des gestionnaires d'événements pour les événements asynchrones du composant <xref:System.ComponentModel.BackgroundWorker>.  Cette longue opération qui s'exécute en arrière\-plan, pour calculer les nombres de Fibonacci, est appelée par l'un de ces gestionnaires d'événements.  
  
#### Pour implémenter des gestionnaires d'événements asynchrones  
  
1.  Dans la fenêtre **Propriétés**, laissez le composant <xref:System.ComponentModel.BackgroundWorker> sélectionné et cliquez sur le bouton **Événements**.  Double\-cliquez sur les événements <xref:System.ComponentModel.BackgroundWorker.DoWork> et <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> pour créer des gestionnaires d'événements.  Pour plus d'informations sur l'utilisation des gestionnaires d'événements, consultez [How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/fr-fr/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
2.  Créez une nouvelle méthode, appelée `ComputeFibonacci`, dans votre formulaire.  Cette méthode effectue le travail réel et s'exécute en arrière\-plan.  Ce code montre que l'implémentation récursive de l'algorithme de Fibonacci, qui est notamment inefficace, prend un temps exponentiellement plus long pour les grands nombres.  Il est utilisé ici à des fins d'illustration pour montrer une opération qui peut introduire de longs délais dans votre application.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#10)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#10)]
     [!code-vb[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#10)]  
  
3.  Dans le gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.DoWork>, ajoutez un appel à la méthode `ComputeFibonacci`.  Prenez le premier paramètre pour `ComputeFibonacci` à partir de la propriété <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> du <xref:System.ComponentModel.DoWorkEventArgs>.  Les paramètres <xref:System.ComponentModel.BackgroundWorker> et <xref:System.ComponentModel.DoWorkEventArgs> seront utilisés ultérieurement pour le rapport de progression et la prise en charge de l'annulation.  Assignez la valeur de retour de `ComputeFibonacci` à la propriété <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> du <xref:System.ComponentModel.DoWorkEventArgs>.  Ce résultat sera disponible au gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>.  
  
    > [!NOTE]
    >  Le gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.DoWork> ne fait pas directement référence à la variable d'instance `backgroundWorker1`, car cela associerait ce gestionnaire d'événements à une instance spécifique de <xref:System.ComponentModel.BackgroundWorker>.  À la place, une référence au <xref:System.ComponentModel.BackgroundWorker> qui a déclenché cet événement est récupérée à partir du paramètre `sender`.  Ceci est important lorsque le formulaire héberge plusieurs <xref:System.ComponentModel.BackgroundWorker>.  Il est également important de ne pas manipuler d'objets interface utilisateur dans votre gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.DoWork>.  À la place, communiquez à l'interface utilisateur via les événements <xref:System.ComponentModel.BackgroundWorker>.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
4.  Dans le gestionnaire d'événement <xref:System.Windows.Forms.Control.Click> du contrôle `startAsyncButton`, ajoutez du code pour lancer l'opération asynchrone.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#13)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#13)]
     [!code-vb[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#13)]  
  
5.  Dans le gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>, assignez le résultat du calcul au contrôle `resultLabel`.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#6)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#6)]  
  
## Ajout de rapport de progression et de prise en charge de l'annulation  
 Pour les opérations asynchrones qui prennent un certain temps, il est souvent souhaitable de signaler la progression à l'utilisateur et de permettre à celui\-ci d'annuler l'opération.  La classe <xref:System.ComponentModel.BackgroundWorker> fournit un événement qui vous permet de publier la progression comme résultat de l'opération d'arrière\-plan.  Il fournit également un indicateur qui permet à votre code de travail de détecter un appel à <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> et l'interrompre.  
  
#### Pour implémenter un rapport de progression  
  
1.  Dans la fenêtre **Propriétés**, sélectionnez la propriété `backgroundWorker1`.  Attribuez aux propriétés <xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A> et <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> la valeur `true`.  
  
2.  Déclarez deux variables dans le formulaire `FibonacciCalculator`.  Celles\-ci seront utilisées pour suivre la progression.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#14)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#14)]
     [!code-vb[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#14)]  
  
3.  Ajoute un gestionnaire d'événements pour l'événement <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>.  Dans le gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>, mettez à jour le <xref:System.Windows.Forms.ProgressBar> avec la propriété <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> du paramètre <xref:System.ComponentModel.ProgressChangedEventArgs>.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#7)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#7)]  
  
#### Pour implémenter la prise en charge de l'annulation  
  
1.  Dans le gestionnaire d'événements du contrôle  `cancelAsyncButton` <xref:System.Windows.Forms.Control.Click>, ajoutez le code qui annule l'opération asynchrone.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#4)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#4)]  
  
2.  Les fragments de code suivants dans le rapport de méthode `ComputeFibonacci` signalent la progression et prennent en charge l'annulation.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#11)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#11)]
     [!code-vb[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#11)]  
    [!code-cpp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#12)]
    [!code-csharp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#12)]
    [!code-vb[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#12)]  
  
## Point de contrôle  
 À ce stade, vous pouvez compiler et exécuter l'application Fibonacci Calculator.  
  
#### Pour tester le projet  
  
-   Appuyez sur F5 pour compiler et exécuter l'application.  
  
     Pendant que le calcul s'exécute en arrière\-plan, vous pouvez consulter <xref:System.Windows.Forms.ProgressBar> qui affiche la progression du calcul en voie d'achèvement.  Vous pouvez également annuler l'opération en suspens.  
  
     Pour les petits nombres, le calcul doit être très rapide, mais pour les grands nombres, vous devez constater un délai notable.  Si vous entrez une valeur égale ou supérieure à 30, vous devez constater un délai de plusieurs secondes, selon la vitesse de votre ordinateur.  Pour les valeurs supérieures à 40, le calcul peut durer plusieurs minutes, voire des heures.  Pendant que la calculatrice est occupée à calculer un grand nombre de Fibonacci, notez que vous pouvez déplacer librement le formulaire, le réduire, l'agrandir et même le faire disparaître.  L'explication en est simple : le thread d'interface utilisateur principal n'attend pas que le calcul se termine.  
  
## Étapes suivantes  
 Maintenant que vous avez implémenté un formulaire qui utilise un composant <xref:System.ComponentModel.BackgroundWorker> pour exécuter un calcul en arrière\-plan, vous pouvez explorer d'autres possibilités pour les opérations asynchrones :  
  
-   Utilisez plusieurs objets <xref:System.ComponentModel.BackgroundWorker> pour plusieurs opérations simultanées.  
  
-   Pour déboguer votre application multithread, consultez [Comment : utiliser la fenêtre Threads](../Topic/How%20to:%20Use%20the%20Threads%20Window.md).  
  
-   Implémentez votre propre composant qui prend en charge le modèle de programmation asynchrone.  Pour plus d'informations, consultez [Event\-based Asynchronous Pattern Overview](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
    > [!CAUTION]
    >  Lorsque vous utilisez le multithreading, vous vous exposez potentiellement à des bogues très sérieux et complexes.  Consultez [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) avant d'implémenter une solution utilisant le multithreading.  
  
## Voir aussi  
 <xref:System.ComponentModel.BackgroundWorker>   
 [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md)   
 [Multithreading in Components](../Topic/Multithreading%20in%20Components.md)   
 [NOT IN BUILD: Multithreading in Visual Basic](http://msdn.microsoft.com/fr-fr/c731a50c-09c1-4468-9646-54c86b75d269)   
 [Comment : implémenter un formulaire qui utilise une opération d'arrière\-plan](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)   
 [Procédure pas à pas : exécution d'une opération en arrière\-plan](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)   
 [BackgroundWorker, composant](../../../../docs/framework/winforms/controls/backgroundworker-component.md)