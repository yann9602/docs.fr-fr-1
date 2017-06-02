---
title: "Comment&#160;: t&#233;l&#233;charger un fichier en arri&#232;re-plan | Microsoft Docs"
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
  - "modèle asynchrone"
  - "opérations d'arrière-plan"
  - "tâches en arrière-plan"
  - "BackgroundWorker (composant)"
  - "composants (Windows Forms), asynchrones"
  - "formulaires, opérations d'arrière-plan"
  - "formulaires, multithreading"
  - "threads (Windows Forms), opérations d'arrière-plan"
ms.assetid: 9b7bc5ae-051c-4904-9720-18f6667388bd
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: t&#233;l&#233;charger un fichier en arri&#232;re-plan
Le téléchargement de fichier est une tâche courante et il est souvent utile d'exécuter cette opération potentiellement longue sur un thread séparé.  Utilisez le composant <xref:System.ComponentModel.BackgroundWorker> pour accomplir cette tâche avec très peu de code.  
  
## Exemple  
 L'exemple de code suivant montre comment utiliser un composant <xref:System.ComponentModel.BackgroundWorker> pour charger un fichier XML à partir d'une URL.  Quand l'utilisateur clique sur le bouton **Download**, le gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> appelle la méthode <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> d'un composant <xref:System.ComponentModel.BackgroundWorker> pour démarrer l'opération de téléchargement.  Le bouton est désactivé pendant toute la durée du téléchargement, puis il est réactivé une fois le téléchargement terminé.  Un <xref:System.Windows.Forms.MessageBox> affiche le contenu du fichier.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 **Téléchargement du fichier**  
  
 Le fichier est téléchargé sur le thread de travail du composant <xref:System.ComponentModel.BackgroundWorker>, qui exécute le gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.DoWork>.  Ce thread démarre quand votre code appelle la méthode <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 **Attente de la fin d'un BackgroundWorker**  
  
 Le gestionnaire d'événements `downloadButton_Click` illustre comment attendre qu'un composant <xref:System.ComponentModel.BackgroundWorker> ait terminé sa tâche asynchrone.  
  
 Si vous souhaitez seulement que l'application réponde aux événements et que vous ne souhaitez pas effectuer de travail dans le thread principal en attendant que le thread d'arrière\-plan se termine, quittez simplement le gestionnaire.  
  
 Si vous souhaitez continuer à travailler dans le thread principal, utilisez la propriété <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> pour déterminer si le thread <xref:System.ComponentModel.BackgroundWorker> est toujours en cours d'exécution.  Dans l'exemple, une barre de progression est mise à jour pendant le téléchargement.  Veillez à appeler la méthode <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=fullName> pour que l'interface utilisateur reste réactive.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 **Affichage du résultat**  
  
 La méthode `backgroundWorker1_RunWorkerCompleted` gère l'événement <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> et est appelée quand l'opération d'arrière\-plan est terminée.  Cette méthode vérifie d'abord la propriété <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=fullName>.  Si <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=fullName> est `null`, cette méthode affiche le contenu du fichier.  Elle active ensuite le bouton de téléchargement, qui a été désactivé quand le téléchargement a commencé, et elle réinitialise la barre de progression.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System.Drawing, System.Windows.Forms et System.Xml.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Programmation fiable  
 Vérifiez toujours la propriété <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=fullName> dans votre gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> avant d'accéder à la propriété <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=fullName> ou à tout autre objet qui peut avoir été affecté par le gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.DoWork>.  
  
## Voir aussi  
 <xref:System.ComponentModel.BackgroundWorker>   
 [Comment : exécuter une opération en arrière\-plan](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)   
 [Comment : implémenter un formulaire qui utilise une opération d'arrière\-plan](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)