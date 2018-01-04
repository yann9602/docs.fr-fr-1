---
title: "Comment : créer une décoration de texte"
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
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0beb22ba78c6fc99951bc2d780c1c5defa32e637
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-text-decoration"></a>Comment : créer une décoration de texte
A <xref:System.Windows.TextDecoration> objet est un ornement visuel que vous pouvez ajouter au texte. Il existe quatre types de décorations de texte : soulignement, ligne de base, barré et surligné. L’exemple suivant montre les emplacements des ornements de texte par rapport au texte.  
  
 ![Diagramme des emplacements d’ornements de texte](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")  
Exemple de types de décoration de texte  
  
 Pour ajouter une décoration de texte à texte, créez un <xref:System.Windows.TextDecoration> de l’objet, puis modifiez ses propriétés. Utilisez le <xref:System.Windows.TextDecoration.Location%2A> propriété pour spécifier où l’ornement de texte s’affiche, comme le trait de soulignement. Utilisez le <xref:System.Windows.TextDecoration.Pen%2A> propriété pour spécifier l’apparence de la décoration de texte, tel qu’un remplissage uni ou la couleur de dégradé. Si vous ne spécifiez pas une valeur pour le <xref:System.Windows.TextDecoration.Pen%2A> propriété, les valeurs par défaut de décorations de la même couleur que le texte. Une fois que vous avez défini un <xref:System.Windows.TextDecoration> de l’objet, ajoutez-la à la <xref:System.Windows.TextDecorations> collection de l’objet de texte de votre choix.  
  
 L’exemple suivant montre une décoration de texte qui a été mise en forme avec un pinceau de dégradé linéaire et un stylet en pointillés.  
  
 ![Décoration de texte avec souligné dégradé linéaire](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")  
Exemple d’un soulignement mis en forme avec un dégradé linéaire pinceau et stylet en pointillés  
  
 Le <xref:System.Windows.Documents.Hyperlink> objet est un élément de contenu de flux inline qui vous permet d’héberger des liens hypertexte dans le contenu de flux. Par défaut, <xref:System.Windows.Documents.Hyperlink> utilise un <xref:System.Windows.TextDecoration> objet pour afficher un trait de soulignement. <xref:System.Windows.TextDecoration>objets peuvent être des performances intensif à instancier, en particulier si vous avez plusieurs <xref:System.Windows.Documents.Hyperlink> objets. Si vous utilisez beaucoup <xref:System.Windows.Documents.Hyperlink> éléments, vous souhaiterez afficher un soulignement uniquement lors du déclenchement d’un événement, tel que le <xref:System.Windows.ContentElement.MouseEnter> événement.  
  
 Dans l’exemple suivant, le soulignement pour le lien « Mon MSN » est dynamique, il n’apparaît que lorsque le <xref:System.Windows.ContentElement.MouseEnter> est déclenché.  
  
 ![Liens hypertexte affichant TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
Liens hypertexte définis avec TextDecorations  
  
 Pour plus d’informations, consultez [Spécifier si un lien hypertexte est souligné ou non](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
## <a name="example"></a>Exemple  
 Dans l’exemple de code suivant, une décoration de texte souligné utilise la valeur de la police par défaut.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 Dans l’exemple de code suivant, une décoration de texte souligné est créée avec un pinceau de couleur unie pour le stylet.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 Dans l’exemple de code suivant, une décoration de texte souligné est créée avec un pinceau de dégradé linéaire pour le stylet en pointillés.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [Spécifier si un lien hypertexte est souligné ou non](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)
