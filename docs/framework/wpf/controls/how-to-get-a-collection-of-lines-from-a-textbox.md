---
title: "Comment : obtenir une collection de lignes à partir d'un TextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb771cdb4d12ebaa5160ec16ca57ba6acf011222
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>Comment : obtenir une collection de lignes à partir d'un TextBox
Cet exemple montre comment obtenir une collection de lignes de texte d’un <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une méthode simple qui prend un <xref:System.Windows.Controls.TextBox> comme argument et retourne un <xref:System.Collections.Specialized.StringCollection> contenant les lignes de texte dans le **zone de texte**.  Le <xref:System.Windows.Controls.TextBox.LineCount%2A> propriété est utilisée pour déterminer le nombre de lignes n’est actuellement dans le **zone de texte**et le <xref:System.Windows.Controls.TextBox.GetLineText%2A> méthode est ensuite utilisée pour extraire chaque ligne et l’ajouter à la collection de lignes.  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [Vue d’ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
