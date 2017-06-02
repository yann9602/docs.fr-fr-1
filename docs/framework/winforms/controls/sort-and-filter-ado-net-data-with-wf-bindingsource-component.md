---
title: "Comment&#160;: trier et filtrer des donn&#233;es ADO.NET avec le composant BindingSource Windows Forms | Microsoft Docs"
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
  - "ADO.NET (Windows Forms)"
  - "BindingSource (composant Windows Forms), trier et filtrer les données"
  - "données (Windows Forms), filtrer"
  - "données (Windows Forms), trier"
  - "trier les données, ADO.NET"
  - "filtrer (Windows Forms), ADO.NET"
  - "trier les données"
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: trier et filtrer des donn&#233;es ADO.NET avec le composant BindingSource Windows Forms
Vous pouvez exposer les fonctions de tri et de filtrage du contrôle <xref:System.Windows.Forms.BindingSource> à l'aide des propriétés <xref:System.Windows.Forms.BindingSource.Sort%2A> et <xref:System.Windows.Forms.BindingSource.Filter%2A>.  Vous pouvez appliquer le tri simple lorsque la source de données sous\-jacente est un <xref:System.ComponentModel.IBindingList>, et vous pouvez appliquer le filtrage et le tri avancé lorsque la source de données est un <xref:System.ComponentModel.IBindingListView>.  La propriété <xref:System.Windows.Forms.BindingSource.Sort%2A> requiert la syntaxe [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] standard : une chaîne représentant le nom d'une colonne de données dans la source de données suivie de `ASC` ou `DESC` pour indiquer si la liste doit être triée dans l'ordre croissant ou décroissant.  Vous pouvez définir un tri avancé ou un tri sur plusieurs colonnes en séparant chaque colonne par une virgule.  La propriété <xref:System.Windows.Forms.BindingSource.Filter%2A> adopte une expression sous forme de chaîne.  
  
> [!NOTE]
>  Le stockage d'informations sensibles, par exemple, un mot de passe, dans la chaîne de connexion peut affecter la sécurité de votre application.  L'utilisation de l'authentification Windows \(également appelée sécurité intégrée\) offre un moyen plus sûr de contrôler l'accès à une base de données.  Pour plus d'informations, consultez [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
### Pour filtrer des données à l'aide de BindingSource  
  
-   Affectez à la propriété <xref:System.Windows.Forms.BindingSource.Filter%2A> l'expression souhaitée.  
  
     Dans l'exemple de code suivant, l'expression est un nom de colonne suivi de la valeur souhaitée pour cette colonne.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### Pour trier des données à l'aide de BindingSource  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.BindingSource.Sort%2A> le nom de colonne souhaité suivi de `ASC` ou `DESC` pour indiquer l'ordre croissant ou décroissant.  
  
2.  Séparez les différentes colonnes par une virgule.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## Exemple  
 L'exemple de code suivant charge des données à partir de la table Customers de l'exemple de base de données Northwind dans un contrôle <xref:System.Windows.Forms.DataGridView>, puis filtre et tri les données affichées.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## Compilation du code  
 Pour exécuter cet exemple, collez le code dans un formulaire contenant <xref:System.Windows.Forms.BindingSource> nommé `BindingSource1` et <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1`.  Gérez l'événement <xref:System.Windows.Forms.Form.Load> pour le formulaire et appelez `InitializeSortedFilteredBindingSource` dans la méthode du gestionnaire d'événements de chargement.  
  
## Voir aussi  
 <xref:System.Windows.Forms.BindingSource.Sort%2A>   
 <xref:System.Windows.Forms.BindingSource.Filter%2A>   
 [Comment : installer des exemples de bases de données](../Topic/How%20to:%20Install%20Sample%20Databases.md)   
 [Composant BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)