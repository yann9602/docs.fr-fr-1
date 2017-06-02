---
title: "Comment&#160;: configurer la notification de mises &#224; jour de liaisons | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "liaison, mises à jour, notifications de"
  - "liaison de données, notification de mises à jour de liaisons"
  - "notifications, mises à jour de liaisons"
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: configurer la notification de mises &#224; jour de liaisons
Cet exemple montre comment effectuer le paramétrage pour être notifié lorsque la [cible de liaison](GTMT) \(cible\) ou la propriété [de source de liaison](GTMT) \(source\) d'une liaison a été mise à jour.  
  
## Exemple  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] déclenche un événement de mise à jour des données chaque fois que la source de liaison ou la cible est mise à jour.  En interne, cet événement est utilisé pour informer le [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] qu'il doit se mettre à jour, car les données dépendantes ont changé.  Notez que pour que ces événements fonctionnent, et également pour que la liaison uni ou bidirectionnelle fonctionne correctement, vous devez implémenter votre classe de données à l'aide de l'interface <xref:System.ComponentModel.INotifyPropertyChanged>.  Pour plus d'informations, consultez [Implémenter la notification des modifications de propriétés](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
 Définissez la propriété <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> ou <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> \(ou les deux\) avec la valeur `true` dans la liaison.  Le gestionnaire que vous fournissez pour écouter cet événement doit être joint directement à l'élément où vous souhaitez être informés des modifications, ou au contexte de données global si vous souhaitez être informé que n'importe quoi dans le contexte a changé.  
  
 Voici un exemple qui indique comment configurer la notification lorsqu'une propriété cible a été mise à jour.  
  
 [!code-xml[DirectionalBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 Vous pouvez attribuer ensuite un gestionnaire basé sur le délégué EventHandler\<T\>, *OnTargetUpdated* dans cet exemple, pour gérer l'événement :  
  
 [!code-csharp[DirectionalBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 Les paramètres de l'événement peuvent être utilisés pour déterminer des détails à propos de la propriété qui a changé \(tel que le type ou l'élément spécifique si le même gestionnaire est joint à plusieurs éléments\), ce qui peut s'avérer utile s'il existe plusieurs propriétés liées sur un élément unique.  
  
## Voir aussi  
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)