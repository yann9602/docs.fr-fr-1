---
title: "Comment&#160;: imprimer dans les Windows Forms en utilisant l&#39;aper&#231;u avant impression | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "impression (Windows Forms), à l’aide de l’aperçu avant impression"
  - "impression, avec l’aperçu avant impression"
  - "aperçu avant impression"
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: imprimer dans les Windows Forms en utilisant l&#39;aper&#231;u avant impression
Il est très courant, dans la programmation Windows Forms, d'offrir un aperçu avant impression en plus des services d'impression. L'un des moyens les plus simples pour ajouter des services d'aperçu avant impression à votre application consiste à utiliser un contrôle <xref:System.Windows.Forms.PrintPreviewDialog> avec la logique de gestion d'événements <xref:System.Drawing.Printing.PrintDocument.PrintPage> pour l'impression d'un fichier.  
  
### Pour afficher un aperçu d'un document texte avec un contrôle PrintPreviewDialog  
  
1.  Ajoutez un <xref:System.Windows.Forms.PrintPreviewDialog>, un <xref:System.Drawing.Printing.PrintDocument> et deux chaînes à votre formulaire.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2.  Affectez comme valeur de la propriété <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> le document que vous souhaitez imprimer, puis ouvrez et lisez le contenu du document dans la chaîne que vous avez ajoutée précédemment.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3.  Comme vous le feriez pour imprimer le document, dans le gestionnaire d'événements <xref:System.Drawing.Printing.PrintDocument.PrintPage>, utilisez la propriété <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> de la classe <xref:System.Drawing.Printing.PrintPageEventArgs> et le contenu du fichier pour calculer les lignes par page et restituer le contenu du document. Après chaque dessin de page, vérifiez s'il s'agit de la dernière page et définissez la propriété <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> de <xref:System.Drawing.Printing.PrintPageEventArgs> en conséquence. L'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> est déclenché jusqu'à ce que <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> soit `false`. Une fois le rendu du document terminé, réinitialisez la chaîne à restituer. Assurez\-vous aussi que l'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> est associé à sa méthode de gestion d'événements.  
  
    > [!NOTE]
    >  Vous avez peut\-être déjà effectué les étapes 2 et 3 si vous avez implémenté l'impression dans votre application.  
  
     Dans l'exemple de code suivant, le gestionnaire d'événements est utilisé pour imprimer le fichier « testPage.txt » avec la même police que celle utilisée sur le formulaire.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4.  Affectez comme valeur de la propriété <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> du contrôle <xref:System.Windows.Forms.PrintPreviewDialog> le composant <xref:System.Drawing.Printing.PrintDocument> sur le formulaire.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5.  Appelez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> sur le contrôle <xref:System.Windows.Forms.PrintPreviewDialog>. Vous appelez généralement <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> à partir de la méthode de gestion d'événements <xref:System.Windows.Forms.Control.Click> d'un bouton. L'appel de <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> déclenche l'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> et affiche la sortie du contrôle <xref:System.Windows.Forms.PrintPreviewDialog>. Quand l'utilisateur clique sur l'icône d'impression dans la boîte de dialogue, l'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> est redéclenché et envoie la sortie vers l'imprimante plutôt que vers la boîte de dialogue d'aperçu. C'est pourquoi la chaîne est réinitialisée à la fin du processus de rendu à l'étape 3.  
  
     L'exemple de code suivant montre la méthode de gestion d'événements <xref:System.Windows.Forms.Control.Click> pour un bouton sur le formulaire. Cette méthode de gestion d'événements appelle les méthodes pour lire le document et afficher la boîte de dialogue Aperçu avant impression.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## Exemple  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Windows.Forms, System.Drawing.  
  
-   Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande associée à [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou à [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez les pages [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également la page [Comment : compiler et exécuter un exemple complet de code Windows Forms à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## Voir aussi  
 [Comment : imprimer un fichier texte composé de plusieurs pages dans les Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)   
 [Prise en charge de l'impression dans les Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)   
 [Impression plus sécurisée dans les Windows Forms](../../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)