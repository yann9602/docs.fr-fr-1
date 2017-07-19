---
title: "Comment&#160;: impl&#233;menter le mode virtuel avec le chargement de donn&#233;es juste-&#224;-temps dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "données (Windows Forms), gérer de grands groupes de données"
  - "DataGridView (contrôle Windows Forms), grands groupes de données"
  - "DataGridView (contrôle Windows Forms), mode virtuel"
  - "exemples (Windows Forms), chargement de données juste-à-temps"
  - "chargement de données juste-à-temps"
  - "mode virtuel, chargement de données juste-à-temps"
ms.assetid: 33825f92-7a22-40ee-86d9-9a2ed1ead7b7
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: impl&#233;menter le mode virtuel avec le chargement de donn&#233;es juste-&#224;-temps dans le contr&#244;le DataGridView Windows Forms
L'exemple de code suivant montre comment utiliser le mode virtuel dans le contrôle <xref:System.Windows.Forms.DataGridView> avec un cache de données qui charge des données à partir d'un serveur uniquement en cas de nécessité.  Cet exemple est décrit en détail dans [Implémentation du mode virtuel avec le chargement de données juste\-à\-temps dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#000)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   des références aux assemblys System.Data, System.Xml et System.Windows.Forms ;  
  
-   l'accès à un serveur sur lequel est installé l'exemple de base de données SQL Server Northwind.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Sécurité .NET Framework  
 Le stockage d'informations sensibles \(telles qu'un mot de passe\) dans la chaîne de connexion peut affecter la sécurité de votre application.  L'utilisation de l'authentification Windows \(également appelée sécurité intégrée\) offre un moyen plus sûr de contrôler l'accès à une base de données.  Pour plus d'informations, consultez [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>   
 <xref:System.Windows.Forms.DataGridView.CellValueNeeded>   
 [Implémentation du mode virtuel avec le chargement de données juste\-à\-temps dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)   
 [Réglage des performances dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)   
 [Mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)