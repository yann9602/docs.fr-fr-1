---
title: "Comment : lier un ListBox à des données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4701fe99231e115eb8cb14f7c1e5e003928bc5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-a-listbox-to-data"></a>Comment : lier un ListBox à des données
Un développeur peut créer <xref:System.Windows.Controls.ListBox> contrôles sans spécifier le contenu de chaque <xref:System.Windows.Controls.ListBoxItem> séparément. Vous pouvez utiliser la liaison de données pour lier des données aux éléments individuels.  
  
 L’exemple suivant montre comment créer un <xref:System.Windows.Controls.ListBox> qui remplit la <xref:System.Windows.Controls.ListBoxItem> éléments de liaison de données à une source de données appelée *couleurs*. Dans ce cas il n’est pas nécessaire d’utiliser <xref:System.Windows.Controls.ListBoxItem> balises pour spécifier le contenu de chaque élément.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.Controls.ListBoxItem>  
 [Contrôles](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
