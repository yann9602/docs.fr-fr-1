---
title: "Sources de donn&#233;es prises en charge par les Windows Forms | Microsoft Docs"
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
  - "tableaux (Windows Forms)"
  - "collections (Windows Forms), lier à"
  - "données (Windows Forms), fournisseurs de données"
  - "fournisseurs de données (Windows Forms)"
  - "sources de données (Windows Forms)"
  - "DataColumn (classe)"
  - "DataSet (classe), liaison et Windows Forms"
  - "DataTable (classe), liaison et Windows Forms"
  - "DataView (classe), liaison et Windows Forms"
  - "DataViewManager (classe), liaison et Windows Forms"
  - "fournisseurs OLE DB, Windows Forms"
  - "Windows Forms, liaison de données"
  - "Windows Forms, données sources"
ms.assetid: 3d2c43f6-462b-4d35-9c86-13e9afe012e1
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Sources de donn&#233;es prises en charge par les Windows Forms
Traditionnellement, les applications utilisaient la liaison de données pour exploiter les données stockées dans des bases de données.  Avec la liaison de données Windows Forms, vous pouvez accéder aux données des bases de données mais aussi aux données d'autres structures, telles que les tableaux et les collections, sous certaines conditions.  
  
## Structures auxquelles se lier  
 Dans Windows Forms, vous pouvez créer une liaison avec une large gamme de structures allant de simples objets \(liaison simple\) à des listes complexes telles que les tables de données ADO.NET \(liaison complexe\).  Pour la liaison simple, Windows Forms prend en charge la liaison aux propriétés publiques sur l'objet simple.  La liaison basée sur liste de Windows Forms requiert en général que l'objet prenne en charge l'interface <xref:System.Collections.IList> ou l'interface <xref:System.ComponentModel.IListSource>.  En outre, si vous créez une liaison via un composant <xref:System.Windows.Forms.BindingSource>, vous pouvez créer une liaison avec un objet qui prend en charge l'interface <xref:System.Collections.IEnumerable>.  Pour plus d'informations sur les interfaces en rapport avec la liaison de données, consultez [Interfaces participant à la liaison de données](../../../docs/framework/winforms/interfaces-related-to-data-binding.md).  
  
 La liste suivante affiche les structures avec lesquelles vous pouvez créer une liaison dans Windows Forms.  
  
 <xref:System.Windows.Forms.BindingSource>  
 Une <xref:System.Windows.Forms.BindingSource> est la source de données Windows Forms la plus commune. Elle agit comme un proxy entre une source de données et les contrôles Windows Forms.  Le modèle d'utilisation <xref:System.Windows.Forms.BindingSource> général consiste à lier vos contrôles à la <xref:System.Windows.Forms.BindingSource> et à lier la <xref:System.Windows.Forms.BindingSource> à la source de données \(par exemple, une table de données ADO.NET ou un objet métier\).  La <xref:System.Windows.Forms.BindingSource> fournit des services qui activent et améliorent le niveau de prise en charge de la liaison de données.  Par exemple, les contrôles basés sur liste de Windows Forms tels que <xref:System.Windows.Forms.DataGridView> et <xref:System.Windows.Forms.ComboBox> ne prennent pas directement en charge la création de liaison avec les sources de données <xref:System.Collections.IEnumerable>, mais vous pouvez toutefois activer ce scénario en créant une liaison via une <xref:System.Windows.Forms.BindingSource>.  Dans ce cas, la <xref:System.Windows.Forms.BindingSource> convertira la source de données en une <xref:System.Collections.IList>.  
  
 Objets simples  
 Windows Forms prend en charge la liaison de données entre des propriétés de contrôles et des propriétés publiques sur l'instance d'un objet à l'aide du type <xref:System.Windows.Forms.Binding>.  Windows Forms prend également en charge la liaison de contrôles basés sur liste, tels qu'un <xref:System.Windows.Forms.ListControl> à une instance d'objet lorsqu'une <xref:System.Windows.Forms.BindingSource> est utilisée.  
  
 Tableau ou collection  
 Pour agir comme une source de données, une liste doit implémenter l'interface <xref:System.Collections.IList>. Un tableau étant une instance de la classe <xref:System.Array> en serait un exemple.  Pour plus d'informations sur les tableaux, consultez [How to: Create an Array of Objects \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/6b64e069-0387-400c-9081-3bdc581020c3).  
  
 En règle générale, vous devez utiliser <xref:System.ComponentModel.BindingList%601> lorsque vous créez des listes d'objets pour la liaison de données.  <xref:System.ComponentModel.BindingList%601> est une version générique de l'interface <xref:System.ComponentModel.IBindingList>.  L'interface <xref:System.ComponentModel.IBindingList> étend l'interface <xref:System.Collections.IList> par l'ajout de propriétés, de méthodes et d'événements nécessaires à la liaison de données bidirectionnelle.  
  
 <xref:System.Collections.IEnumerable>  
 Les contrôles Windows Forms peuvent être liés aux sources de données qui prennent uniquement en charge l'interface <xref:System.Collections.IEnumerable> s'ils sont liés via un composant <xref:System.Windows.Forms.BindingSource>.  
  
 Objets de données [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] propose une série de structures de données auxquelles il est possible de se lier.  Chaque objet possède son propre niveau de sophistication et de complexité.  
  
-   <xref:System.Data.DataColumn>.  Une classe <xref:System.Data.DataColumn> est le bloc de construction fondamental d'une classe <xref:System.Data.DataTable>, dans la mesure où une table est constituée d'un certain nombre de colonnes.  Chaque <xref:System.Data.DataColumn> possède une propriété <xref:System.Data.DataColumn.DataType%2A> qui détermine le type de données figurant dans la colonne \(par exemple, la marque d'une automobile dans une table décrivant des voitures\).  Vous pouvez créer une liaison simple entre un contrôle \(la propriété <xref:System.Windows.Forms.Control.Text%2A> d'un contrôle <xref:System.Windows.Forms.TextBox>, par exemple\) à une colonne d'une table de données.  
  
-   <xref:System.Data.DataTable>.  Une classe <xref:System.Data.DataTable> est la représentation d'une table, avec des lignes et des colonnes, dans [!INCLUDE[vstecado](../../../includes/vstecado-md.md)].  Une table de données contient deux collections : <xref:System.Data.DataColumn> qui représente les colonnes de données d'une table \(et détermine le type des données pouvant être entrées dans cette table\) et <xref:System.Data.DataRow> qui représente les lignes de données d'une table.  Il est possible de créer une liaison complexe entre un contrôle et les informations contenues dans une table de données \(comme la liaison d'un contrôle <xref:System.Windows.Forms.DataGridView> à une table de données\).  Toutefois, lorsque vous créez une liaison à un objet <xref:System.Data.DataTable>, vous créez en fait une liaison avec la vue par défaut de la table.  
  
-   <xref:System.Data.DataView>.  Une classe <xref:System.Data.DataView> est une vue personnalisée d'une table de données unique pouvant être filtrée ou triée.  Une vue de données est « l'instantané » des données utilisé par les contrôles dépendants complexes.  Dans une vue de données, vous pouvez créer une liaison simple ou complexe aux données. Il faut toutefois savoir que vous créez, dans ce cas, une liaison à une « image » fixe des données plutôt qu'à une source de données qui effectue des mises à jour.  
  
-   <xref:System.Data.DataSet>.  Une classe <xref:System.Data.DataSet> est une collection de tables, de relations et de contraintes des données d'une base de données.  Dans un groupe de données \(dataset\), vous pouvez créer une liaison simple ou complexe aux données. Il faut toutefois savoir que vous créez en réalité une liaison à l'objet <xref:System.Data.DataViewManager> par défaut du <xref:System.Data.DataSet> \(voir ci\-dessous\).  
  
-   <xref:System.Data.DataViewManager>.  Une classe <xref:System.Data.DataViewManager> est une vue personnalisée de la classe <xref:System.Data.DataSet> entière, analogue à une classe <xref:System.Data.DataView>, mais avec les relations incluses.  Avec une collection <xref:System.Data.DataViewManager.DataViewSettings%2A>, vous pouvez définir des filtres et des options de tri par défaut pour toutes les vues dont dispose le <xref:System.Data.DataViewManager> pour une table donnée.  
  
## Voir aussi  
 [Notification de modifications dans la liaison de données Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)   
 [Liaison de données et Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)   
 [Liaison de données Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)