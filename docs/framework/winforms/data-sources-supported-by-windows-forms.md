---
title: "Sources de données prises en charge par les Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- collections [Windows Forms], binding to
- OLE DB providers [Windows Forms], Windows Forms
- DataTable class [Windows Forms], binding and Windows Forms
- Windows Forms, data binding
- DataView class [Windows Forms], binding and Windows Forms
- DataViewManager class [Windows Forms], binding and Windows Forms
- Windows Forms, source data
- arrays [Windows Forms]
- data sources [Windows Forms]
- data providers [Windows Forms]
- DataSet class [Windows Forms], binding and Windows Forms
- data [Windows Forms], data providers
ms.assetid: 3d2c43f6-462b-4d35-9c86-13e9afe012e1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d2c1c021759c7032257e95eb2cad202a461dc05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="data-sources-supported-by-windows-forms"></a>Sources de données prises en charge par les Windows Forms
En règle générale, la liaison de données a été utilisée dans des applications pour tirer parti des données stockées dans les bases de données. Avec la liaison de données Windows Forms, vous pourrez accéder aux données à partir de bases de données, ainsi que les données d’autres structures, tels que les tableaux et collections, tant que certaines exigences minimales ont été remplies.  
  
## <a name="structures-to-bind-to"></a>Pour lier à des structures  
 Dans les Windows Forms, vous pouvez lier à un large éventail de structures, simple objets (liaison simple) à des listes complexes telles que les tables de données ADO.NET (liaison complexe). Pour la liaison simple, Windows Forms prend en charge la liaison aux propriétés publiques sur l’objet simple. Liaison de liste en fonction de Windows Forms requiert en général que l’objet prend en charge la <xref:System.Collections.IList> interface ou le <xref:System.ComponentModel.IListSource> interface. En outre, si vous établissez une liaison avec via un <xref:System.Windows.Forms.BindingSource> composant, vous pouvez lier à un objet qui prend en charge la <xref:System.Collections.IEnumerable> interface. Pour plus d’informations sur les interfaces participant à la liaison de données, consultez [Interfaces associées à la liaison de données](../../../docs/framework/winforms/interfaces-related-to-data-binding.md).  
  
 La liste suivante affiche les structures que vous pouvez lier à dans les Windows Forms.  
  
 <xref:System.Windows.Forms.BindingSource>  
 A <xref:System.Windows.Forms.BindingSource> est la source de données Windows Forms courante qui fait Office de proxy entre une source de données et des contrôles Windows Forms. Général <xref:System.Windows.Forms.BindingSource> modèle d’utilisation consiste à lier vos contrôles à la <xref:System.Windows.Forms.BindingSource> et lier le <xref:System.Windows.Forms.BindingSource> à la source de données (par exemple, une table de données ADO.NET ou un objet métier). Le <xref:System.Windows.Forms.BindingSource> fournit des services qui activent et améliorent le niveau de prise en charge de la liaison de données. Par exemple, Windows Forms contrôles basés sur liste tel que le <xref:System.Windows.Forms.DataGridView> et <xref:System.Windows.Forms.ComboBox> ne prennent pas directement en charge la liaison à <xref:System.Collections.IEnumerable> des sources de données, toutefois, vous pouvez activer ce scénario par liaison via un <xref:System.Windows.Forms.BindingSource>. Dans ce cas, le <xref:System.Windows.Forms.BindingSource> convertira la source de données à un <xref:System.Collections.IList>.  
  
 Objets simples  
 Windows Forms prend en charge les propriétés de contrôle de liaison de données aux propriétés publiques sur l’instance d’un objet en utilisant la <xref:System.Windows.Forms.Binding> type. Windows Forms prend également en charge des contrôles de liste en fonction de liaison comme un <xref:System.Windows.Forms.ListControl> à un objet d’instance quand un <xref:System.Windows.Forms.BindingSource> est utilisé.  
  
 tableau ou collection  
 Pour agir comme source de données, une liste doit implémenter la <xref:System.Collections.IList> interface ; un exemple serait un tableau qui est une instance de la <xref:System.Array> classe. Pour plus d’informations sur les tableaux, consultez [Comment : créer un tableau d’objets (Visual Basic)](http://msdn.microsoft.com/en-us/6b64e069-0387-400c-9081-3bdc581020c3).  
  
 En général, vous devez utiliser <xref:System.ComponentModel.BindingList%601> lorsque vous créez des listes d’objets pour la liaison de données. <xref:System.ComponentModel.BindingList%601>est une version générique de le <xref:System.ComponentModel.IBindingList> interface. Le <xref:System.ComponentModel.IBindingList> interface étend la <xref:System.Collections.IList> interface en ajoutant des propriétés, méthodes et événements nécessaires pour la liaison de données bidirectionnelle.  
  
 <xref:System.Collections.IEnumerable>  
 Contrôles Windows Forms peuvent être liés à des sources de données qui prennent en charge uniquement la <xref:System.Collections.IEnumerable> si elles sont liées par le biais de l’interface un <xref:System.Windows.Forms.BindingSource> composant.  
  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]objets de données  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]fournit un nombre pouvant être lié à des structures de données. Chaque varie en fonction de sa complexité et la complexité.  
  
-   <xref:System.Data.DataColumn>. A <xref:System.Data.DataColumn> est le bloc de construction fondamental d’un <xref:System.Data.DataTable>, dans la mesure où un nombre de colonnes comprendre une table. Chaque <xref:System.Data.DataColumn> a un <xref:System.Data.DataColumn.DataType%2A> propriété qui détermine le type de données figurant dans la colonne (par exemple, la marque d’une automobile dans une table décrivant des voitures). Vous pouvez créer une liaison simple un contrôle (comme un <xref:System.Windows.Forms.TextBox> du contrôle <xref:System.Windows.Forms.Control.Text%2A> propriété) à une colonne dans une table de données.  
  
-   <xref:System.Data.DataTable>. A <xref:System.Data.DataTable> est la représentation sous forme d’une table, avec des lignes et colonnes, dans [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]. Une table de données contient deux collections : <xref:System.Data.DataColumn>, représentant les colonnes de données dans une table donnée (qui détermine les types de données qui peuvent être entrées dans cette table), et <xref:System.Data.DataRow>, qui représente les lignes de données dans une table donnée. Vous pouvez complexe lier un contrôle pour les informations contenues dans une table de données (notamment la liaison la <xref:System.Windows.Forms.DataGridView> contrôle à une table de données). Toutefois, lorsque vous liez à un <xref:System.Data.DataTable>, vous avez fait une liaison à la vue du tableau par défaut.  
  
-   <xref:System.Data.DataView>. A <xref:System.Data.DataView> est une vue personnalisée d’une table de données unique qui peut être filtrée ou triée. Une vue de données est « instantané » utilisée par les contrôles liés complexes de données. Vous pouvez créer une liaison simple ou complexe lier à des données dans une vue de données, mais sachez que vous établissez une liaison à une « image » fixe de données plutôt que d’une source de données.  
  
-   <xref:System.Data.DataSet>. A <xref:System.Data.DataSet> est une collection de tables, relations et contraintes des données dans une base de données. Vous pouvez créer une liaison simple ou complexe lier à des données dans un jeu de données, mais sachez que vous établissez une liaison à la valeur par défaut <xref:System.Data.DataViewManager> pour le <xref:System.Data.DataSet> (voir la puce suivante).  
  
-   <xref:System.Data.DataViewManager>. A <xref:System.Data.DataViewManager> est une vue personnalisée de l’ensemble du <xref:System.Data.DataSet>, analogue à un <xref:System.Data.DataView>, mais avec les relations incluses. Avec un <xref:System.Data.DataViewManager.DataViewSettings%2A> collection, vous pouvez définir des filtres par défaut et les options de tri pour toutes les vues qui la <xref:System.Data.DataViewManager> a pour une table donnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Notification de modifications dans la liaison de données Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Liaison de données et Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Liaison de données Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)
