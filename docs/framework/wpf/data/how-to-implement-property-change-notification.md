---
title: "Comment : implémenter la notification des modifications de propriétés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6628ec27ab381f52a086cac3f8d0cd92aea2cd8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="9a6e5-102">Comment : implémenter la notification des modifications de propriétés</span><span class="sxs-lookup"><span data-stu-id="9a6e5-102">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="9a6e5-103">Pour prendre en charge <xref:System.Windows.Data.BindingMode.OneWay> ou <xref:System.Windows.Data.BindingMode.TwoWay> de liaison pour activer vos propriétés de cible de liaison à reflètent automatiquement les modifications dynamiques de la source de liaison (par exemple, pour que le volet Aperçu de mises à jour automatiquement lorsque l’utilisateur modifie un formulaire), votre classe. doit fournir les notifications de modification de propriété approprié.</span><span class="sxs-lookup"><span data-stu-id="9a6e5-103">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="9a6e5-104">Cet exemple montre comment créer une classe qui implémente <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="9a6e5-104">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a6e5-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="9a6e5-105">Example</span></span>  
 <span data-ttu-id="9a6e5-106">Pour implémenter <xref:System.ComponentModel.INotifyPropertyChanged> vous avez besoin de déclarer le <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> événement et créer le `OnPropertyChanged` (méthode).</span><span class="sxs-lookup"><span data-stu-id="9a6e5-106">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="9a6e5-107">Pour chaque propriété pour laquelle vous souhaitez modifier les notifications, vous devez ensuite appeler `OnPropertyChanged` chaque fois que la propriété est mise à jour.</span><span class="sxs-lookup"><span data-stu-id="9a6e5-107">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="9a6e5-108">Pour voir un exemple de la façon dont `Person` classe peut être utilisée pour prendre en charge <xref:System.Windows.Data.BindingMode.TwoWay> de liaison, consultez [lorsque le texte de la zone de texte met à jour la Source de contrôle](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).</span><span class="sxs-lookup"><span data-stu-id="9a6e5-108">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a6e5-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a6e5-109">See Also</span></span>  
 [<span data-ttu-id="9a6e5-110">Vue d'ensemble des sources de liaison</span><span class="sxs-lookup"><span data-stu-id="9a6e5-110">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [<span data-ttu-id="9a6e5-111">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="9a6e5-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="9a6e5-112">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="9a6e5-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
