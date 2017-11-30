---
title: "Comment : implémenter l'interface INotifyPropertyChanged"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 54dc436ec40f001ab1bf90acaedf22745d35d1b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="e8405-102">Comment : implémenter l'interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="e8405-102">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="e8405-103">L’exemple de code suivant montre comment implémenter la <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span><span class="sxs-lookup"><span data-stu-id="e8405-103">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="e8405-104">Implémentez cette interface sur les objets métier qui sont utilisés dans la liaison de données Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e8405-104">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="e8405-105">En cas d’implémentation, l’interface communique à un contrôle dépendant les modifications des propriétés d’un objet métier.</span><span class="sxs-lookup"><span data-stu-id="e8405-105">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8405-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="e8405-106">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e8405-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8405-107">See Also</span></span>  
 [<span data-ttu-id="e8405-108">Guide pratique pour appliquer le modèle PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="e8405-108">How to: Apply the PropertyNameChanged Pattern</span></span>](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 [<span data-ttu-id="e8405-109">Liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e8405-109">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="e8405-110">Comment : générer des notifications de modifications à l'aide d'un BindingSource et de l'interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="e8405-110">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 [<span data-ttu-id="e8405-111">Notification de modifications dans la liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e8405-111">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
