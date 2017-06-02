---
title: "Comment&#160;: cr&#233;er un formulaire ma&#238;tre/d&#233;tail utilisant deux contr&#244;les DataGridView Windows Form | Microsoft Docs"
ms.custom: ""
ms.date: "02/15/2017"
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
  - "DataGridView (contrôle Windows Forms), formulaire maître/détail"
  - "listes maître/détails, créer"
  - "tables parent-enfant, afficher sur les Windows Forms"
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Comment&#160;: cr&#233;er un formulaire ma&#238;tre/d&#233;tail utilisant deux contr&#244;les DataGridView Windows Form
L'exemple de code suivant crée un formulaire maître\/détail avec deux contrôles <xref:System.Windows.Forms.DataGridView> liés à deux composants <xref:System.Windows.Forms.BindingSource>.  La source de données est un <xref:System.Data.DataSet> qui contient les tables `Customers` et `Orders` de l'exemple de base de données Northwind SQL Server, ainsi qu'un <xref:System.Data.DataRelation> qui associe les deux par l'intermédiaire de la colonne `CustomerID`.  
  
 Un <xref:System.Windows.Forms.BindingSource> est lié à la table `Customers` parente dans le jeu de données.  Ces données sont affichées dans le contrôle <xref:System.Windows.Forms.DataGridView> maître.  L'autre <xref:System.Windows.Forms.BindingSource> est lié au premier connecteur de données.  La propriété <xref:System.Windows.Forms.BindingSource.DataMember%2A> du deuxième <xref:System.Windows.Forms.BindingSource> a comme valeur le nom de <xref:System.Data.DataRelation>.  Cela a pour conséquence l'affichage, par le contrôle <xref:System.Windows.Forms.DataGridView> détail, des lignes de la table `Orders` enfant qui correspondent à la ligne actuelle dans le contrôle <xref:System.Windows.Forms.DataGridView> maître.  
  
 Pour obtenir une explication complète de cet exemple de code, consultez [Procédure pas à pas : création d'un formulaire maître\/détail qui utilise deux contrôles DataGridView Windows Forms](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagrids.md).  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   des références aux assemblys System, System.Data, System.Windows.Forms et System.XML.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Sécurité .NET Framework  
 Le stockage d'informations sensibles \(telles qu'un mot de passe\) dans la chaîne de connexion peut affecter la sécurité de votre application.  L'utilisation de l'authentification Windows \(également appelée sécurité intégrée\) offre un moyen plus sûr de contrôler l'accès à une base de données.  Pour plus d'informations, consultez [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [Procédure pas à pas : création d'un formulaire maître\/détail qui utilise deux contrôles DataGridView Windows Forms](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagrids.md)   
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md)