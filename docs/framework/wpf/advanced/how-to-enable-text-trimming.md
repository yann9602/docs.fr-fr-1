---
title: "Comment&#160;: activer la suppression de texte | Microsoft Docs"
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
  - "documents, supprimer du texte"
  - "texte, ajuster"
  - "supprimer du texte"
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: activer la suppression de texte
Cet exemple présente également l'utilisation et les effets des valeurs disponibles dans l'énumération <xref:System.Windows.TextTrimming>.  
  
## Exemple  
 L'exemple suivant définit un élément <xref:System.Windows.Controls.TextBlock> avec le jeu d'attributs <xref:System.Windows.Controls.TextBlock.TextTrimming%2A>.  
  
 [!code-xml[TextTrimmingSnippets#_TextTrimmingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## Exemple  
 La définition de la propriété <xref:System.Windows.TextTrimming> correspondante dans le code est présentée ci\-dessous.  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 Il existe actuellement trois options permettant de supprimer du texte : **CharacterEllipsis**, **WordEllipsis** et **None**.  
  
 Lorsque <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> a la valeur **CharacterEllipsis**, le texte est rogné et reprend avec des points de suspension au niveau du caractère le plus proche de la bordure de la suppression.  Ce paramètre tend à rogner le texte pour qu'il s'adapte mieux aux limites de la suppression, mais il peut provoquer la suppression partielle de certains mots.  L'illustration suivante présente l'effet de ce paramètre sur un <xref:System.Windows.Controls.TextBlock> similaire à celui défini ci\-dessus.  
  
 ![Exemple : TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming\_Character")  
  
 Lorsque <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> a la valeur **WordEllipsis**, le texte est rogné et reprend avec des points de suspension à la fin du premier mot entier le plus proche de la bordure de la suppression.  Ce paramètre n'affichera pas de mots partiellement rognés, mais ne tend pas à rogner le texte avec autant de précision que le paramètre **CharacterEllipsis**.  L'illustration suivante présente l'effet de ce paramètre sur le <xref:System.Windows.Controls.TextBlock> défini ci\-dessus.  
  
 ![Exemple : TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming\_Word")  
  
 Lorsque <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> a la valeur **None**, aucune suppression de texte n'est effectuée.  Dans ce cas, le texte est simplement rogné à la limite du conteneur de texte parent.  L'illustration suivante présente l'effet de ce paramètre sur un <xref:System.Windows.Controls.TextBlock> similaire à celui défini ci\-dessus.  
  
 ![Exemple : TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming\_None")