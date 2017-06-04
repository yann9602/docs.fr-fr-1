---
title: "Comment&#160;: d&#233;finir les modes de redimensionnement du contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "grilles de données, définir les modes de dimensionnement"
  - "DataGridView (contrôle Windows Forms), modes de dimensionnement"
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: d&#233;finir les modes de redimensionnement du contr&#244;le DataGridView Windows Forms
Les procédures suivantes montrent des scénarios courants de personnalisation et de combinaison des options de dimensionnement disponibles pour le contrôle <xref:System.Windows.Forms.DataGridView> et pour certaines colonnes des contrôles.  
  
### Pour créer une colonne de largeur fixe  
  
-   Définissez la propriété <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> sur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>, la propriété <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> sur <xref:System.Windows.Forms.DataGridViewTriState>, la propriété <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> sur `true`, et la propriété <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> sur une valeur appropriée.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### Pour créer une colonne dont la taille s'ajuste au contenu  
  
-   Définissez la propriété <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> sur un mode de dimensionnement basé sur le contenu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### Pour créer des colonnes avec mode de remplissage pour les valeurs de taille et d'importance variables  
  
-   Définissez la propriété <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=fullName> sur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode> pour définir le mode de dimensionnement de toutes les colonnes qui ne substituent pas cette valeur.  Définissez la propriété <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> des colonnes sur des valeurs qui soient proportionnelles à leur largeur moyenne de contenu.  Définissez la propriété <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> des colonnes importantes pour garantir un affichage partiel du contenu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## Exemple  
 L'exemple de code complet suivant est une démonstration d'application qui peut vous aider à comprendre les options de dimensionnement décrites dans cette rubrique.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 Pour utiliser cette démonstration d'application :  
  
-   Modifiez la taille du formulaire.  Observez comment les colonnes avec mode de remplissage changent tout en conservant les proportions indiquées par les valeurs de propriétés <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>.  Observez comment la <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> d'une colonne empêche celle\-ci de changer quand le formulaire est trop petit.  
  
-   Modifiez les tailles des colonnes en faisant glisser les séparateurs de colonnes avec la souris.  Observez comment certaines colonnes ne peuvent pas être redimensionnées et comment les colonnes redimensionnables ne peuvent pas devenir plus étroites que leur largeur minimale.  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Des références aux assemblys System et System.Windows.Forms.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], voir [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Voir également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>   
 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=fullName>