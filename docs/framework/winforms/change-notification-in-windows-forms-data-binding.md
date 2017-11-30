---
title: "Notification de modifications dans la liaison de données Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ffafaff2355e89e2127742f2fba5c005492b4580
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Notification de modifications dans la liaison de données Windows Forms
Un des concepts plus importants de la liaison de données Windows Forms est *notification de modification*. Pour vous assurer que votre source de données et les contrôles liés ont toujours des données les plus récentes, vous devez ajouter la notification de modification pour la liaison de données. Plus précisément, vous souhaitez vous assurer que les contrôles dépendants sont avertis des modifications qui ont été apportées à leur source de données, et la source de données est informée des modifications apportées aux propriétés d’un contrôle dépendantes.  
  
 Il existe différents types de notifications de modifications, en fonction du type de liaison de données :  
  
-   Liaison simple dans lequel une seule propriété de contrôle est liée à une seule instance d’un objet.  
  
-   La liaison basée sur une liste qui peut inclure une seule propriété de contrôle liée à la propriété d’un élément dans une liste ou une propriété du contrôle lié à une liste d’objets.  
  
 En outre, si vous créez des contrôles Windows Forms que vous souhaitez utiliser pour la liaison de données, vous devez appliquer le *PropertyName*modifié le modèle pour les contrôles, afin que les modifications apportées à la propriété liée d’un contrôle sont propagées à la source de données.  
  
## <a name="change-notification-for-simple-binding"></a>Notification de modification pour la liaison Simple  
 Pour la liaison simple, les objets métier doivent fournir des notifications de modification lorsque la valeur d’une propriété liée change. Ce faire, vous pouvez exposer un *PropertyName*événement Changed pour chaque propriété de votre objet métier et liez cet objet aux contrôles avec le <xref:System.Windows.Forms.BindingSource> ou la méthode par défaut dans lequel votre objet métier implémente le <xref:System.ComponentModel.INotifyPropertyChanged> interface et déclenche une <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> événement lorsque la valeur d’une propriété change. Pour plus d’informations, consultez [Comment : implémenter l’INotifyPropertyChanged Interface](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md). Lorsque vous utilisez des objets qui implémentent la <xref:System.ComponentModel.INotifyPropertyChanged> interface, il est inutile d’utiliser le <xref:System.Windows.Forms.BindingSource> pour lier l’objet à un contrôle, mais à l’aide du <xref:System.Windows.Forms.BindingSource> est recommandé.  
  
## <a name="change-notification-for-list-based-binding"></a>Notification de modification pour la liaison basée sur la liste  
 Windows Forms dépend d’une liste liée pour fournir la modification de la propriété (une valeur de propriété des éléments de liste change) et à une liste (un élément est supprimé ou ajouté à la liste) à des contrôles liés aux informations. Par conséquent, les listes utilisées pour la liaison de données doivent implémenter le <xref:System.ComponentModel.IBindingList>, qui fournit les deux types de notification de modification. Le <xref:System.ComponentModel.BindingList%601> est une implémentation générique de <xref:System.ComponentModel.IBindingList> et est conçu pour une utilisation avec la liaison de données Windows Forms. Vous pouvez créer un <xref:System.ComponentModel.BindingList%601> qui contient un type d’objet métier qui implémente <xref:System.ComponentModel.INotifyPropertyChanged> et convertit automatiquement la liste le <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> événements <xref:System.ComponentModel.IBindingList.ListChanged> événements. Si la liste liée n’est pas un <xref:System.ComponentModel.IBindingList>, vous devez lier la liste d’objets aux contrôles Windows Forms à l’aide de la <xref:System.Windows.Forms.BindingSource> composant. Le <xref:System.Windows.Forms.BindingSource> composant fournit une conversion de la propriété à la liste semblable à celui de la <xref:System.ComponentModel.BindingList%601>. Pour plus d’informations, consultez [Comment : déclencher des Notifications de modification à l’aide d’un BindingSource et l’INotifyPropertyChanged Interface](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md).  
  
## <a name="change-notification-for-custom-controls"></a>Notification de modification pour les contrôles personnalisés  
 Enfin, du côté du contrôle, vous devez exposer un *PropertyName*événement Changed pour chaque propriété conçue pour être lié aux données. Les modifications apportées à la propriété du contrôle sont ensuite propagées à la source de données. Pour plus d’informations, consultez [Comment : appliquer le modèle PropertyNameChanged](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 <xref:System.ComponentModel.BindingList%601>  
 [Liaison de données Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Sources de données prises en charge par les Windows Forms](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [Liaison de données et Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
