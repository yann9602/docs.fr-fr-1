---
title: "Comment&#160;: lier des objets aux contr&#244;les DataGridView Windows Forms | Microsoft Docs"
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
  - "grilles de données, liaison d'objet"
  - "DataGridView (contrôle Windows Forms), liaison d'objet"
  - "liaison d'objet, DataGridView (contrôle)"
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: lier des objets aux contr&#244;les DataGridView Windows Forms
L'exemple de code suivant montre comment lier une collection d'objets à un contrôle <xref:System.Windows.Forms.DataGridView> pour que chaque objet soit affichée sur une ligne distincte.  Cet exemple illustre également comment afficher une propriété avec un type énumération dans un <xref:System.Windows.Forms.DataGridViewComboBoxColumn> pour que la zone de liste déroulante modifiable contienne les valeurs d'énumération.  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   des références aux assemblys System et System.Windows.Forms.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [Comment : accéder à des objets liés à des lignes DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)