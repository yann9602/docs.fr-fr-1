---
title: "Comment&#160;: lier des donn&#233;es au contr&#244;le DataGridView Windows&#160;Forms | Microsoft Docs"
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
  - "liaison de données, DataGridView (contrôle)"
  - "liaison de données, grilles"
  - "DataGridView (contrôle Windows Forms), liaison de données"
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
caps.latest.revision: 30
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 30
---
# Comment&#160;: lier des donn&#233;es au contr&#244;le DataGridView Windows&#160;Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> prend en charge le modèle de liaison de données Windows Forms standard. Il peut donc créer une liaison avec diverses sources de données.  Dans la plupart des cas, toutefois, vous créerez une liaison avec un composant <xref:System.Windows.Forms.BindingSource> qui gérera les détails de l'interaction avec la source de données.  Le composant <xref:System.Windows.Forms.BindingSource> peut représenter n'importe quelle source de données Windows Forms et procure une grande souplesse lors du choix ou de la modification de l'emplacement de vos données.  Pour plus d'informations sur les sources de données prises en charge par le contrôle <xref:System.Windows.Forms.DataGridView>, consultez [Vue d'ensemble du contrôle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).  
  
 Cette tâche est très bien prise en charge dans Visual Studio.  Consultez également [Comment : lier des données au contrôle DataGridView Windows Forms à l'aide du concepteur](http://msdn.microsoft.com/library/33w255ac%20\(v=vs.110\)).  
  
## Procédure  
  
#### Pour connecter un contrôle DataGridView à des données  
  
1.  Implémentez une méthode pour gérer les détails de la récupération des données d'une base de données.  L'exemple de code suivant implémente une méthode `GetData` qui initialise un composant <xref:System.Data.SqlClient.SqlDataAdapter> et l'utilise pour renseigner un <xref:System.Data.DataTable>.  Le <xref:System.Data.DataTable> est ensuite lié au composant <xref:System.Windows.Forms.BindingSource>.  Veillez à définir la variable `connectionString` avec une valeur appropriée pour votre base de données.  Vous devrez accéder à un serveur sur lequel est installé l'exemple de base de données SQL Server Northwind.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#20)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#20)]  
  
2.  Dans le gestionnaire d'événements <xref:System.Windows.Forms.Form.Load> de votre formulaire, liez le contrôle <xref:System.Windows.Forms.DataGridView> au composant <xref:System.Windows.Forms.BindingSource> et appelez la méthode `GetData` pour récupérer les données de la base de données.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#10)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#10)]  
  
## Exemple  
 L'exemple de code complet suivant fournit des boutons pour recharger des données à partir de la base de données et soumettre des modifications à la base de données.  
  
 [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#00)]
 [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#00)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Windows.Forms, System.Data et System.XML.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Sécurité .NET Framework  
 Le stockage d'informations sensibles \(telles qu'un mot de passe\) dans la chaîne de connexion peut affecter la sécurité de votre application.  L'utilisation de l'authentification Windows \(également appelée sécurité intégrée\) offre un moyen plus sûr de contrôler l'accès à une base de données.  Pour plus d'informations, consultez [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.BindingSource>   
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md)