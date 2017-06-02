---
title: "Comment&#160;: acc&#233;der &#224; des objets li&#233;s &#224; des lignes DataGridView Windows&#160;Forms | Microsoft Docs"
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
  - "grilles de données, accéder aux objets dépendants"
  - "DataGridView (contrôle Windows Forms), accéder aux objets liés aux lignes"
  - "liaison d'objet, accéder aux objets dépendants"
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Comment&#160;: acc&#233;der &#224; des objets li&#233;s &#224; des lignes DataGridView Windows&#160;Forms
Il est parfois utile d'afficher une table d'informations stockée dans une collection d'objets métier.  Quand vous liez un contrôle <xref:System.Windows.Forms.DataGridView> à une telle collection, chaque propriété publique est affichée dans sa propre colonne, à moins que la propriété n'ait été marquée comme non consultable avec un <xref:System.ComponentModel.BrowsableAttribute>.  Par exemple, une collection d'objets `Customer` aurait des colonnes telles que **Nom** et **Adresse**.  
  
 Si ces objets contiennent des informations supplémentaires et du code auquel vous souhaitez accéder, vous pouvez l'atteindre via des objets de ligne.  Dans l'exemple de code suivant, les utilisateurs peuvent sélectionner plusieurs lignes et cliquer sur un bouton pour envoyer une facture à chacun des clients correspondants.  
  
### Pour accéder à des objets liés à une ligne  
  
-   Utilisez la propriété <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=fullName>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## Exemple  
 L'exemple de code complet comprend une implémentation `Customer` simple et lie le <xref:System.Windows.Forms.DataGridView> à un <xref:System.Collections.ArrayList> contenant quelques objets `Customer`.  Le gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> du <xref:System.Windows.Forms.Button?displayProperty=fullName> doit accéder aux objets `Customer` par l'intermédiaire des lignes, car la collection de clients n'est pas accessible en dehors du gestionnaire d'événements <xref:System.Windows.Forms.Form.Load?displayProperty=fullName>.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System et System.Windows.Forms.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewRow>   
 <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=fullName>   
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [Comment : lier des objets aux contrôles DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-objects-to-windows-forms-datagridview-controls.md)