---
title: "Optimisation des performances&#160;: texte | Microsoft Docs"
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
  - "rendu de texte"
  - "liens hypertexte"
  - "texte mis en forme (WPF)"
  - "texte, performances"
  - "glyphes"
ms.assetid: 66b1b9a7-8618-48db-b616-c57ea4327b98
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Optimisation des performances&#160;: texte
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]prend en charge la présentation de contenu de texte via l’utilisation de fonctionnalités enrichies [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] contrôles. En général, vous pouvez diviser le rendu de texte en trois couches :  
  
1.  À l’aide de la <xref:System.Windows.Documents.Glyphs> et <xref:System.Windows.Media.GlyphRun> directement des objets.  
  
2.  À l’aide de la <xref:System.Windows.Media.FormattedText> objet.  
  
3.  À l’aide des contrôles de niveau supérieur, tels que les <xref:System.Windows.Controls.TextBlock> et <xref:System.Windows.Documents.FlowDocument> objets.  
  
 Cette rubrique fournit des recommandations relatives aux performances de rendu de texte.  
  
   
  
<a name="Glyph_Level"></a>   
## <a name="rendering-text-at-the-glyph-level"></a>Rendu de texte au niveau du glyphe  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Fournit la prise en charge de texte avancée, y compris la balise de niveau glyphe avec accès direct au <xref:System.Windows.Documents.Glyphs> pour les clients qui souhaitent intercepter et rendre le texte persistant après la mise en forme. Ces fonctionnalités prennent en charge critique les exigences de rendu dans chacun des scénarios suivants le texte différent.  
  
-   L’écran de documents à format fixe.  
  
-   Scénarios d’impression.  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]comme un langage d’imprimante périphérique.  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].  
  
    -   Les pilotes d’imprimante précédents, sorties de [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications au format fixe.  
  
    -   Format de spouleur d’impression.  
  
-   Représentation sous forme de documents à format fixe, y compris les clients des versions précédentes de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] et autres périphériques informatiques.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs> et <xref:System.Windows.Media.GlyphRun> sont conçus pour la présentation de documents à format fixe et les scénarios d’impression. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]fournit plusieurs éléments pour la présentation générale et [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénarii, tels que <xref:System.Windows.Controls.Label> et <xref:System.Windows.Controls.TextBlock>. Pour plus d’informations sur la mise en page et [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de scénarios, consultez le [typographie dans WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md).  
  
 Les exemples suivants montrent comment définir les propriétés d’un <xref:System.Windows.Documents.Glyphs> dans l’objet [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Le <xref:System.Windows.Documents.Glyphs> objet représente la sortie d’un <xref:System.Windows.Media.GlyphRun> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Les exemples supposent que les polices Arial, courrier New et Times New Roman sont installées dans le **C:\WINDOWS\Fonts** dossier sur l’ordinateur local.  
  
 [!code-xml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
### <a name="using-drawglyphrun"></a>Utilisation de DrawGlyphRun  
 Si vous avez le contrôle personnalisé et que vous souhaitez restituer des glyphes, utilisez la <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A> méthode.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit également des services de niveau inférieur pour le texte personnalisé de mise en forme à l’aide de la <xref:System.Windows.Media.FormattedText> objet. Le moyen le plus efficace de rendu du texte dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est de générer le contenu de texte au glyphe à l’aide <xref:System.Windows.Documents.Glyphs> et <xref:System.Windows.Media.GlyphRun>. Toutefois, le coût de ce rendement est la perte de facile à utiliser texte enrichi, qui sont des fonctionnalités intégrées de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] contrôles, tels que <xref:System.Windows.Controls.TextBlock> et <xref:System.Windows.Documents.FlowDocument>.  
  
<a name="FormattedText_Object"></a>   
## <a name="formattedtext-object"></a>Objet FormattedText  
 Le <xref:System.Windows.Media.FormattedText> objet vous permet de dessiner du texte multiligne, dans lequel chaque caractère du texte peut être mis en forme individuellement. Pour plus d’informations, consultez [dessin du texte au format](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md).  
  
 Pour créer le texte mis en forme, appelez le <xref:System.Windows.Media.FormattedText.%23ctor%2A> constructeur pour créer un <xref:System.Windows.Media.FormattedText> objet. Une fois que vous avez créé la chaîne initiale de texte mis en forme, vous pouvez appliquer différents styles de mise en forme. Si votre application souhaite implémenter sa propre présentation, puis la <xref:System.Windows.Media.FormattedText> objet est préférable à l’utilisation d’un contrôle, tel que <xref:System.Windows.Controls.TextBlock>. Pour plus d’informations sur la <xref:System.Windows.Media.FormattedText> , consultez [dessin du texte au format](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md) .  
  
 Le <xref:System.Windows.Media.FormattedText> objet fournit la fonctionnalité de mise en forme de texte de bas niveau. Vous pouvez appliquer plusieurs styles de mise en forme à un ou plusieurs caractères. Par exemple, vous pouvez appeler à la fois le <xref:System.Windows.Media.FormattedText.SetFontSize%2A> et <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> méthodes pour modifier la mise en forme des cinq premiers caractères dans le texte.  
  
 L’exemple de code suivant crée un <xref:System.Windows.Media.FormattedText> de l’objet et l’affiche.  
  
 [!code-csharp[formattedtextsnippets#FormattedTextSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[formattedtextsnippets#FormattedTextSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
<a name="FlowDocument_TextBlock_Label"></a>   
## <a name="flowdocument-textblock-and-label-controls"></a>FlowDocument, TextBlock et contrôles Label  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]inclut plusieurs contrôles pour dessiner le texte à l’écran. Chaque contrôle est ciblé pour un scénario différent et possède sa propre liste de fonctionnalités et limitations.  
  
### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument influe sur les performances plus de TextBlock ou Label  
 En général, les <xref:System.Windows.Controls.TextBlock> élément doit être utilisé lors de la prise en charge de texte limitée est requis, par exemple, une brève phrase dans un [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> peuvent être utilisés lors de la prise en charge de texte minimale est requise. Le <xref:System.Windows.Documents.FlowDocument> élément est un conteneur pour les documents de reflux qui prennent en charge la présentation enrichie de contenu et par conséquent, a un impact sur les performances supérieur à l’aide du <xref:System.Windows.Controls.TextBlock> ou <xref:System.Windows.Controls.Label> contrôles.  
  
 Pour plus d’informations sur <xref:System.Windows.Documents.FlowDocument>, consultez [présentation du flux de Document](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
### <a name="avoid-using-textblock-in-flowdocument"></a>Évitez d’utiliser TextBlock dans FlowDocument  
 Le <xref:System.Windows.Controls.TextBlock> élément dérivé <xref:System.Windows.UIElement>. Le <xref:System.Windows.Documents.Run> élément dérivé <xref:System.Windows.Documents.TextElement>, qui est moins cher à utiliser qu’un <xref:System.Windows.UIElement>-objet dérivé. Si possible, utilisez <xref:System.Windows.Documents.Run> plutôt que <xref:System.Windows.Controls.TextBlock> pour afficher le texte contenu dans un <xref:System.Windows.Documents.FlowDocument>.  
  
 Le balisage suivant illustre deux façons de définir le contenu de texte dans un <xref:System.Windows.Documents.FlowDocument>:  
  
 [!code-xml[Performance#PerformanceSnippet13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]  
  
### <a name="avoid-using-run-to-set-text-properties"></a>Évitez d’utiliser exécuter pour définir les propriétés de texte  
 En général, à l’aide un <xref:System.Windows.Documents.Run> dans un <xref:System.Windows.Controls.TextBlock> est performances plus performante que celle de ne pas utiliser de <xref:System.Windows.Documents.Run> tout l’objet. Si vous utilisez un <xref:System.Windows.Documents.Run> afin de définir les propriétés de texte, définissez ces propriétés directement sur le <xref:System.Windows.Controls.TextBlock> à la place.  
  
 Le balisage suivant illustre ces deux façons de définir une propriété de texte, dans ce cas, le <xref:System.Windows.Controls.TextBlock.FontWeight%2A> propriété :  
  
 [!code-xml[Performance#PerformanceSnippet12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]  
  
 Le tableau suivant présente le coût de l’affichage de 1000 <xref:System.Windows.Controls.TextBlock> objets avec et sans explicite <xref:System.Windows.Documents.Run>.  
  
|**Type de TextBlock**|**Heure de création (ms)**|**Afficher le temps (ms)**|  
|------------------------|------------------------------|----------------------------|  
|Exécuter la définition des propriétés de texte|146|540|  
|Définition des propriétés de texte TextBlock|43|453|  
  
### <a name="avoid-databinding-to-the-labelcontent-property"></a>Éviter la liaison de données à la propriété Label.Content  
 Imaginez un scénario où vous avez un <xref:System.Windows.Controls.Label> objet qui est fréquemment mis à jour depuis un <xref:System.String> source. Lors de la liaison de données la <xref:System.Windows.Controls.Label> l’élément <xref:System.Windows.Controls.ContentControl.Content%2A> propriété du <xref:System.String> source de l’objet, vous pouvez rencontrer des performances médiocres. Chaque fois que la source de <xref:System.String> est mis à jour, l’ancien <xref:System.String> objet est ignoré et un nouveau <xref:System.String> est recréé, car un <xref:System.String> objet est immuable, il ne peut pas être modifié. À son tour, provoque la <xref:System.Windows.Controls.ContentPresenter> de la <xref:System.Windows.Controls.Label> objet à ignorer son ancien contenu et à régénérer le nouveau contenu pour afficher le nouveau <xref:System.String>.  
  
 La solution à ce problème est simple. Si le <xref:System.Windows.Controls.Label> n’est pas défini sur un personnalisé <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> , remplacez le <xref:System.Windows.Controls.Label> avec un <xref:System.Windows.Controls.TextBlock> et lier les données son <xref:System.Windows.Controls.TextBlock.Text%2A> propriété à la chaîne source.  
  
|**Propriété liée aux données**|**Heure de mise à jour (ms)**|  
|-----------------------------|----------------------------|  
|Label.Content|835|  
|TextBlock.Text|242|  
  
<a name="Hyperlink"></a>   
## <a name="hyperlink"></a>Lien hypertexte  
 Le <xref:System.Windows.Documents.Hyperlink> objet est un élément de contenu de flux inline qui permet d’héberger des liens hypertexte dans le contenu de flux.  
  
### <a name="combine-hyperlinks-in-one-textblock-object"></a>Combiner des liens hypertexte dans un objet TextBlock  
 Vous pouvez optimiser l’utilisation de plusieurs <xref:System.Windows.Documents.Hyperlink> éléments en les regroupant dans le même <xref:System.Windows.Controls.TextBlock>. Cela permet de réduire le nombre d’objets que vous créez dans votre application. Par exemple, vous souhaiterez afficher plusieurs liens hypertexte, tels que les éléments suivants :  
  
 Page d’accueil MSN | Mon MSN  
  
 L’exemple de balisage suivant montre plusieurs <xref:System.Windows.Controls.TextBlock> éléments utilisés pour afficher les liens hypertexte :  
  
 [!code-xml[Performance#PerformanceSnippet9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]  
  
 Le balisage suivant illustre un moyen plus efficace d’afficher les liens hypertexte, cette fois, à l’aide d’un seul <xref:System.Windows.Controls.TextBlock>:  
  
 [!code-xml[Performance#PerformanceSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]  
  
### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Affichage des soulignements sur les liens hypertexte uniquement sur les événements MouseEnter  
 A <xref:System.Windows.TextDecoration> objet est un ornement visuel que que vous pouvez ajouter au texte ; Toutefois, il peut être performances intensif à instancier. Si vous utilisez beaucoup de <xref:System.Windows.Documents.Hyperlink> éléments, envisagez d’afficher un soulignement uniquement lors du déclenchement d’un événement, tel que le <xref:System.Windows.ContentElement.MouseEnter> événement. Pour plus d’informations, consultez [spécifiez si un lien hypertexte est souligné](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
 ![Liens hypertexte affichant TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
Lien hypertexte qui apparaît sur MouseEnter  
  
 L’exemple de balise suivant montre un <xref:System.Windows.Documents.Hyperlink> défini avec et sans soulignement :  
  
 [!code-xml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 Le tableau suivant présente le coût de performance de l’affichage de 1000 <xref:System.Windows.Documents.Hyperlink> éléments avec et sans soulignement.  
  
|**Lien hypertexte**|**Heure de création (ms)**|**Afficher le temps (ms)**|  
|-------------------|------------------------------|----------------------------|  
|Souligné|289|1130|  
|Sans soulignement|299|776|  
  
<a name="Text_Formatting_Features"></a>   
## <a name="text-formatting-features"></a>Fonctionnalités de mise en forme du texte  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Fournit des services, tels que les coupures de mots automatiques de mise en forme. Ces services peuvent affecter les performances de l’application et doivent être utilisés uniquement lorsque nécessaire.  
  
### <a name="avoid-unnecessary-use-of-hyphenation"></a>Évitez d’utiliser inutilement de la coupure de mots  
 Coupure de mots automatique recherche des points d’arrêt de trait d’union pour des lignes de texte et autorise des positions d’arrêt supplémentaires pour les lignes de <xref:System.Windows.Controls.TextBlock> et <xref:System.Windows.Documents.FlowDocument> objets. Par défaut, la fonctionnalité de coupure de mots automatique est désactivée dans ces objets. Vous pouvez activer cette fonctionnalité en affectant à la propriété l’objet IsHyphenationEnabled `true`. Toutefois, l’activation de cette fonctionnalité entraîne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour lancer [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)] l’interopérabilité, qui peut affecter les performances de l’application. Il est recommandé de ne pas utiliser la césure automatique, sauf si vous en avez besoin.  
  
### <a name="use-figures-carefully"></a>Utilisez les Figures avec précaution  
 A <xref:System.Windows.Documents.Figure> élément représente une partie du contenu de flux qui peut être positionné de manière absolue dans une page de contenu. Dans certains cas, un <xref:System.Windows.Documents.Figure> peut entraîner une page entière reformater automatiquement si sa position est en conflit avec un contenu qui a déjà été disposé. Vous pouvez réduire la probabilité de la remise en forme inutile en regroupant <xref:System.Windows.Documents.Figure> éléments en regard les uns des autres, ou en les déclarant vers le début du contenu dans un scénario de taille de page fixe.  
  
### <a name="optimal-paragraph"></a>Paragraphe optimal  
 La fonctionnalité de paragraphe optimal de la <xref:System.Windows.Documents.FlowDocument> objet dispose les paragraphes afin que les espaces soient distribués de manière aussi égale que possible. Par défaut, la fonctionnalité de paragraphe optimal est désactivée. Vous pouvez activer cette fonctionnalité en définissant l’objet <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> propriété `true`. Toutefois, l’activation de cette fonctionnalité affecte les performances de l’application. Il est recommandé de ne pas utiliser la fonctionnalité de paragraphe optimal, sauf si vous en avez besoin.  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances des applications WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [Planification des performances des applications](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [Tirer parti du matériel](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [Disposition et conception](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [Graphiques&2;D et acquisition d’images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [Comportement de l’objet](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [Ressources d’application](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [Autres recommandations relatives aux performances](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)