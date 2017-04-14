---
title: "Comment&#160;: permettre aux utilisateurs de copier plusieurs cellules dans le Presse-papiers &#224; partir du contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "cellules, copier dans le Presse-papiers"
  - "Presse-papiers, copier plusieurs cellules"
  - "grilles de données, copier plusieurs cellules"
  - "DataGridView (contrôle Windows Forms), copier plusieurs cellules"
ms.assetid: fd0403b2-d0e3-4ae0-839c-0f737e1eb4a9
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: permettre aux utilisateurs de copier plusieurs cellules dans le Presse-papiers &#224; partir du contr&#244;le DataGridView Windows Forms
Quand vous activez la copie des cellules, vous rendez les données de votre contrôle <xref:System.Windows.Forms.DataGridView> facilement accessibles à d'autres applications via le <xref:System.Windows.Forms.Clipboard>.  Les valeurs des cellules sélectionnées sont converties en chaînes et ajoutées au Presse\-papiers sous forme de texte délimité par des tabulations en vue d'être collées dans des applications, telles que le Bloc\-notes et Excel, et sous forme d'un tableau au format HTML en vue d'être collées dans des applications telles que Word.  
  
 Vous pouvez configurer la copie de cellules pour copier uniquement les valeurs des cellules, pour inclure le texte des en\-têtes de ligne et de colonne dans les données du Presse\-papiers ou pour inclure le texte des en\-têtes uniquement quand les utilisateurs sélectionnent des lignes et des colonnes entières.  
  
 Selon le mode de sélection, les utilisateurs peuvent sélectionner plusieurs groupes de cellules non connectés.  Quand un utilisateur copie des cellules dans le Presse\-papiers, les lignes et les colonnes qui ne contiennent pas de cellules sélectionnées ne sont pas copiées.  Toutes les autres lignes ou colonnes deviennent des lignes et des colonnes de la table de données copiée dans le Presse\-papiers.  Les cellules non sélectionnées de ces lignes ou colonnes sont copiées comme des espaces réservés dans le Presse\-papiers.  
  
### Pour activer la copie de cellule  
  
-   Définissez la propriété <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=fullName>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## Exemple  
 L'exemple de code complet suivant montre comment les cellules sont copiées vers le Presse\-papiers.  Cet exemple inclut un bouton qui copie les cellules sélectionnées dans le Presse\-papiers à l'aide de la méthode <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=fullName> et affiche le contenu du Presse\-papiers dans une zone de texte.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## Compilation du code  
 Ce code nécessite :  
  
-   Des références aux assemblys N:System et N:System.Windows.Forms.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], voir [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Voir également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>   
 <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>   
 [Sélection et utilisation du Presse\-papiers avec le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)