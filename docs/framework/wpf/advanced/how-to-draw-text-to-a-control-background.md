---
title: "Guide pratique pour dessiner du texte sur l’arrière-plan d’un contrôle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 091be80e055279685c9dba33dd6b6635e64eaff0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-text-to-a-control39s-background"></a>Guide pratique pour dessiner du texte sur l’arrière-plan d’un contrôle
Vous pouvez dessiner du texte directement à l’arrière-plan d’un contrôle en convertissant une chaîne de texte à un <xref:System.Windows.Media.FormattedText> de l’objet et le dessin du contrôle <xref:System.Windows.Media.DrawingContext>. Vous pouvez également utiliser cette technique pour attirer à l’arrière-plan d’objets dérivés de <xref:System.Windows.Controls.Panel>, tel que <xref:System.Windows.Controls.Canvas> et <xref:System.Windows.Controls.StackPanel>.  
  
 ![Contrôles affichant le texte en arrière-plan](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")  
Exemple de contrôles avec des arrière-plans de texte personnalisés  
  
## <a name="example"></a>Exemple  
 Pour dessiner à l’arrière-plan d’un contrôle, créez un <xref:System.Windows.Media.DrawingBrush> de l’objet et de dessiner le texte converti à l’objet <xref:System.Windows.Media.DrawingContext>. Ensuite, assignez le nouveau <xref:System.Windows.Media.DrawingBrush> à la propriété du contrôle en arrière-plan.  
  
 L’exemple de code suivant montre comment créer un <xref:System.Windows.Media.FormattedText> de l’objet et dessiner à l’arrière-plan d’un <xref:System.Windows.Controls.Label> et <xref:System.Windows.Controls.Button> objet.  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.FormattedText>  
 [Dessin du texte mis en forme](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
