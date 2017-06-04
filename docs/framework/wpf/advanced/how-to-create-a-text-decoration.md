---
title: "Comment&#160;: cr&#233;er une d&#233;coration de texte | Microsoft Docs"
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
  - "type de ligne de base"
  - "polices, planification initiale"
  - "polices, surligné"
  - "polices, barré"
  - "polices, souligné"
  - "type de surlignement"
  - "type de ligne barrée"
  - "texte, ornements"
  - "typographie, ornements de texte"
  - "type de soulignement"
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: cr&#233;er une d&#233;coration de texte
Un objet <xref:System.Windows.TextDecoration> est un ornement visuel que vous pouvez ajouter au texte.  Il existe quatre types de décorations de texte : soulignement, ligne de base, ligne barrée et ligne au\-dessus.  L'exemple suivant montre les emplacements des décorations de texte relatives au texte.  
  
 ![Diagramme des emplacements d'ornements de texte](../../../../docs/framework/wpf/advanced/media/textdecoration01.png "TextDecoration01")  
Exemple de types de décorations de texte  
  
 Pour ajouter une décoration de texte à un texte, créez un objet <xref:System.Windows.TextDecoration> et modifiez ses propriétés.  Utilisez la propriété <xref:System.Windows.TextDecoration.Location%2A> pour spécifier l'endroit où apparaît la décoration, le soulignement par exemple.  Utilisez la propriété <xref:System.Windows.TextDecoration.Pen%2A> pour spécifier l'apparence de la décoration de texte, une couleur de remplissage ou un dégradé de couleurs par exemple.  Si vous ne spécifiez pas de valeur pour la propriété <xref:System.Windows.TextDecoration.Pen%2A>, les décorations sont par défaut de la même couleur que le texte.  Une fois que vous avez défini un objet <xref:System.Windows.TextDecoration>, ajoutez\-le à la collection <xref:System.Windows.TextDecorations> de l'objet de texte souhaité.  
  
 L'exemple suivant montre une décoration de texte qui a été mise en forme avec un pinceau à dégradé linéaire et un stylet en pointillés.  
  
 ![Ornement de texte avec souligné dégradé linéaire](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")  
Exemple d'un soulignement mis en forme avec un pinceau à dégradé linéaire et un stylet en pointillés  
  
 L'objet <xref:System.Windows.Documents.Hyperlink> est un élément inclus de contenu de flux qui vous permet d'héberger des liens hypertexte au sein du contenu du flux.  Par défaut, <xref:System.Windows.Documents.Hyperlink> utilise un objet <xref:System.Windows.TextDecoration> pour afficher un souligné.  Les objets <xref:System.Windows.TextDecoration> peuvent être exigeants en termes de performance à instancier, en particulier si vous avez de nombreux objets <xref:System.Windows.Documents.Hyperlink>.  Si vous utilisez beaucoup d'éléments <xref:System.Windows.Documents.Hyperlink>, envisagez d'afficher un soulignement uniquement lors du déclenchement d'un événement, tel que <xref:System.Windows.ContentElement.MouseEnter>.  
  
 Dans l'exemple suivant, le soulignement du lien "My MSN" est dynamique : il s'affiche uniquement lorsque l'événement <xref:System.Windows.ContentElement.MouseEnter> est déclenché.  
  
 ![Liens hypertexte affichant TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
Hyperliens définis à l'aide de décorations de texte  
  
 Pour plus d'informations, consultez [Spécifier si un lien hypertexte est souligné ou non](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
## Exemple  
 Dans l'exemple de code suivant, une décoration de texte souligné utilise la valeur de police par défaut.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 Dans l'exemple suivant, une décoration de texte souligné est créée à l'aide d'un pinceau de couleur unie pour le stylet.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 Dans l'exemple de code suivant, une décoration de texte souligné est créée à l'aide d'un pinceau à dégradé linéaire pour le stylet en pointillés.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## Voir aussi  
 <xref:System.Windows.TextDecoration>   
 <xref:System.Windows.Documents.Hyperlink>   
 [Spécifier si un lien hypertexte est souligné ou non](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)