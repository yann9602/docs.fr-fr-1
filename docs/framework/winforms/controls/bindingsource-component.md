---
title: Composant BindingSource
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 006cafafdf8e3c3f4da77394d6155fa52e113b58
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="bindingsource-component"></a>Composant BindingSource
Encapsule une source de données pour la liaison à des contrôles.  
  
 Le composant <xref:System.Windows.Forms.BindingSource> remplit deux fonctions. Tout d'abord, il fournit une couche d'indirection lors de la liaison des contrôles sur un formulaire de données. Vous devez pour cela lier le composant <xref:System.Windows.Forms.BindingSource> à votre source de données, puis lier les contrôles sur votre formulaire au composant <xref:System.Windows.Forms.BindingSource>. Toute interaction supplémentaire avec les données, y compris la navigation, le tri, le filtrage et la mise à jour, est effectuée en appelant le composant <xref:System.Windows.Forms.BindingSource>.  
  
 Ensuite, le composant <xref:System.Windows.Forms.BindingSource> peut agir comme source de données fortement typée. L'ajout d'un type au composant <xref:System.Windows.Forms.BindingSource> avec la méthode <xref:System.Windows.Forms.BindingSource.Add%2A> crée une liste de ce type.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d'ensemble du composant BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 Présente les concepts généraux du composant <xref:System.Windows.Forms.BindingSource>, qui vous permet de lier une source de données à un contrôle.  
  
 [Comment : lier des contrôles Windows Forms à des valeurs de base de données DBNull](../../../../docs/framework/winforms/controls/how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 Montre comment gérer une valeur <xref:System.DBNull> de la source de données à l'aide du composant <xref:System.Windows.Forms.BindingSource>.  
  
 [Comment : trier et filtrer des données ADO.NET avec le composant BindingSource Windows Forms](../../../../docs/framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 Illustre comment utiliser le composant <xref:System.Windows.Forms.BindingSource> pour appliquer des tris et des filtres aux données affichées.  
  
 [Comment : établir une liaison à un service Web à l’aide du BindingSource Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 Montre comment utiliser le composant <xref:System.Windows.Forms.BindingSource> pour établir une liaison à un service web.  
  
 [Comment : gérer des erreurs et des exceptions qui se produisent avec Databinding](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 Illustre comment utiliser le composant <xref:System.Windows.Forms.BindingSource> pour gérer correctement les erreurs qui se produisent dans une opération de liaison de données.  
  
 [Comment : lier un contrôle Windows Forms à un type](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 Montre comment utiliser un composant <xref:System.Windows.Forms.BindingSource> pour établir une liaison à un type.  
  
 [Comment : lier un contrôle Windows Forms à un objet Factory](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 Montre comment utiliser un composant <xref:System.Windows.Forms.BindingSource> pour établir une liaison à une méthode ou un objet de fabrique.  
  
 [Comment : personnaliser l'ajout d'éléments avec le composant BindingSource Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 Montre comment utiliser un composant <xref:System.Windows.Forms.BindingSource> pour créer des éléments et les ajouter à une source de données.  
  
 [Comment : générer des notifications de modifications à l'aide de la méthode ResetItem de BindingSource](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 Montre comment utiliser un composant <xref:System.Windows.Forms.BindingSource> pour déclencher des événements de notifications de modifications pour les sources de données qui ne prennent pas en charge les notifications de modifications.  
  
 [Comment : générer des notifications de modifications à l'aide d'un BindingSource et de l'interface INotifyPropertyChanged](../../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 Montre comment utiliser un type qui hérite de <xref:System.ComponentModel.INotifyPropertyChanged> avec un contrôle <xref:System.Windows.Forms.BindingSource>.  
  
 [Comment : répercuter des mises à jour de source de données dans un contrôle Windows Forms avec le BindingSource](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 Montre comment répondre aux modifications qui se produisent dans la source de données à l'aide du composant <xref:System.Windows.Forms.BindingSource>.  
  
 [Comment : partager des données liées entre des formulaires à l'aide du composant BindingSource](../../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 Montre comment utiliser <xref:System.Windows.Forms.BindingSource> pour lier plusieurs formulaires à la même source de données.  
  
## <a name="reference"></a>Référence  
 <xref:System.Windows.Forms.BindingSource>  
 Fournit la documentation de référence pour le composant <xref:System.Windows.Forms.BindingSource>.  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 Fournit la documentation de référence pour le contrôle <xref:System.Windows.Forms.BindingNavigator>.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Liaison de données Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 Contient des liens vers des rubriques décrivant l’architecture de liaison de données Windows Forms.  
  
 Consultez également [Liaison de contrôles à des données dans Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).
