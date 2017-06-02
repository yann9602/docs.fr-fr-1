---
title: "Notification de modifications dans la liaison de donn&#233;es Windows Forms | Microsoft Docs"
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
  - "Windows Forms, ajouter la notification de modification pour la liaison des données"
  - "Windows Forms, liaison de données"
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Notification de modifications dans la liaison de donn&#233;es Windows Forms
L'un des concepts les plus importants de la liaison de données Windows Forms est la *notification de modifications*.  Pour garantir que votre source de données et vos contrôles dépendants disposent toujours des données les plus récentes, vous devez ajouter la notification de modifications pour la liaison de données.  Spécifiquement, vous souhaitez vous assurer que les contrôles dépendants sont notifiés des modifications apportées à leur source de données et que la source de données est notifiée des modifications faites aux propriétés liées d'un contrôle.  
  
 Il existe plusieurs types de notification de modifications, selon le type de liaison de données :  
  
-   la liaison simple dans laquelle une seule propriété de contrôle est liée à une seule instance d'un objet ;  
  
-   la liaison basée sur liste qui peut inclure une seule propriété de contrôle liée à la propriété d'un élément de liste ou une propriété de contrôle liée à une liste d'objets.  
  
 En outre, si vous créez des contrôles Windows Forms que vous souhaitez utiliser pour la liaison de données, vous devez appliquer le modèle *NomPropriété*Changed aux contrôles, afin que les modifications apportées à la propriété liée d'un contrôle soient propagées à la source de données.  
  
## Notification de modifications pour la liaison simple  
 Dans le cas d'une liaison simple, les objets métier doivent fournir la notification de modifications lorsque la valeur d'un propriété liée change.  Pour ce faire, exposez un événement *NomPropriété*Changed pour chaque propriété de l'objet métier et liez cet objet aux contrôles avec <xref:System.Windows.Forms.BindingSource> ou avec la méthode par défaut dans laquelle votre objet métier implémente l'interface <xref:System.ComponentModel.INotifyPropertyChanged> et déclenche un événement <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> lorsque la valeur d'une propriété change.  Pour plus d'informations, consultez [Comment : implémenter l'interface INotifyPropertyChanged](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md).  Lorsque vous utilisez des objets qui implémentent l'interface <xref:System.ComponentModel.INotifyPropertyChanged>, il n'est pas nécessaire d'avoir recours à <xref:System.Windows.Forms.BindingSource> pour lier l'objet à un contrôle, mais il est conseillé d'utiliser <xref:System.Windows.Forms.BindingSource>.  
  
## Notification de modifications pour la liaison basée sur liste  
 Windows Forms a recours à une liste liée pour fournir aux contrôles dépendants des informations sur les modifications apportées aux propriétés \(modification de la valeur de propriété d'un élément de liste\) et à une liste \(suppression ou ajout d'un élément à la liste\).  Par conséquent, les listes utilisées pour la liaison de données doivent implémenter <xref:System.ComponentModel.IBindingList>, qui fournit les deux types de notification de modifications.  <xref:System.ComponentModel.BindingList%601> est une implémentation générique de <xref:System.ComponentModel.IBindingList>, conçue pour être utilisée avec la liaison de données Windows Forms.  Vous pouvez créer un <xref:System.ComponentModel.BindingList%601> qui contient un type d'objet métier implémentant <xref:System.ComponentModel.INotifyPropertyChanged> et la liste convertira automatiquement les événements <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> en événements <xref:System.ComponentModel.IBindingList.ListChanged>.  Si la liste liée n'est pas un <xref:System.ComponentModel.IBindingList>, vous devez lier la liste d'objets aux contrôles Windows Forms en utilisant le composant <xref:System.Windows.Forms.BindingSource>.  Le composant <xref:System.Windows.Forms.BindingSource> fournit une conversion des propriétés en liste similaire à celle de <xref:System.ComponentModel.BindingList%601>.  Pour plus d'informations, consultez [Comment : générer des notifications de modifications à l'aide d'un BindingSource et de l'interface INotifyPropertyChanged](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md).  
  
## Notifications de modifications pour les contrôles personnalisés  
 Côté contrôle, vous devez exposer un événement *NomPropriété*Changed pour chaque propriété conçue pour être liée aux données.  Les modifications apportées à la propriété du contrôle sont ensuite propagées à la source de données liée.  Pour plus d'informations, consultez [Comment : appliquer le modèle PropertyNameChanged](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
  
## Voir aussi  
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.ComponentModel.INotifyPropertyChanged>   
 <xref:System.ComponentModel.BindingList%601>   
 [Liaison de données Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [Sources de données prises en charge par les Windows Forms](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)   
 [Liaison de données et Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)