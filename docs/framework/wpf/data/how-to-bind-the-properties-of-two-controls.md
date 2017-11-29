---
title: "Comment : lier les propriétés de deux contrôles"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff3da19d33e747ec514de9cd24fa08ccd6ab13bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>Comment : lier les propriétés de deux contrôles
Cet exemple montre comment lier la propriété d’un contrôle instancié à celle d’un autre à l’aide de la <xref:System.Windows.Data.Binding.ElementName%2A> propriété.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment lier le <xref:System.Windows.Controls.Panel.Background%2A> propriété d’un <xref:System.Windows.Controls.Canvas> à la <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> propriété d’un <xref:System.Windows.Controls.ComboBox>:  
  
 [!code-xaml[BindDptoDp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 Lors de l’affichage, on obtient un résultat similaire à ce qui suit :  
  
 ![Canevas avec arrière-plan vert](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")  
  
 **Remarque** la propriété de cible de liaison (dans cet exemple, le <xref:System.Windows.Controls.Panel.Background%2A> propriété) doit être une propriété de dépendance. Pour plus d’informations, consultez [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier la source de liaison](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
