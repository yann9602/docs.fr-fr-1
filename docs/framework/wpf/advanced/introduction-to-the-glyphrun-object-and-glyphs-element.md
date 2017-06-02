---
title: "Introduction &#224; l&#39;objet GlyphRun et &#224; l&#39;&#233;l&#233;ment Glyphs | Microsoft Docs"
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
  - "typographie, élément Glyphs"
  - "éléments Glyphs"
  - "GlyphRun (objet)"
  - "texte, glyphes"
  - "glyphes (WPF)"
  - "typographie, GlyphRun (objet)"
ms.assetid: 746ca769-a331-4435-9b95-f72a883b67c1
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# Introduction &#224; l&#39;objet GlyphRun et &#224; l&#39;&#233;l&#233;ment Glyphs
Cette rubrique décrit la <xref:System.Windows.Media.GlyphRun> objet et la <xref:System.Windows.Documents.Glyphs> élément.  
  
   
  
<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a>Introduction à GlyphRun  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Fournit la prise en charge de texte avancée, y compris la balise de niveau glyphe avec accès direct au <xref:System.Windows.Documents.Glyphs> pour les clients qui souhaitent intercepter et rendre le texte persistant après la mise en forme. Ces fonctionnalités prennent en charge critique les exigences de rendu dans chacun des scénarios suivants le texte différent.  
  
1.  L’écran de documents à format fixe.  
  
2.  Scénarios d’impression.  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]comme un langage d’imprimante périphérique.  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].  
  
    -   Les pilotes d’imprimante précédents, sorties de [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications au format fixe.  
  
    -   Format de spouleur d’impression.  
  
3.  Représentation sous forme de documents à format fixe, y compris les clients des versions précédentes de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] et autres périphériques informatiques.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs> et <xref:System.Windows.Media.GlyphRun> sont conçus pour la présentation de documents à format fixe et les scénarios d’impression.                      [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]fournit plusieurs éléments pour la présentation générale et [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénarii, tels que <xref:System.Windows.Controls.Label> et <xref:System.Windows.Controls.TextBlock>. Pour plus d’informations sur la mise en page et [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de scénarios, consultez le [typographie dans WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md).  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a>L’objet GlyphRun  
 Le <xref:System.Windows.Media.GlyphRun> objet représente une séquence de glyphes à partir d’un type unique d’une police unique à une taille unique et avec un style de rendu unique.  
  
 <xref:System.Windows.Media.GlyphRun> inclut les détails tels que les glyphes <xref:System.Windows.Documents.Glyphs.Indices%2A> et les positions de chaque glyphe. Il inclut également l’original [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] l’exécution a été générée à partir des informations de mappage offset de mémoire tampon de caractères de glyphe et les indicateurs par caractère et par glyphe de points de code.  
  
 <xref:System.Windows.Media.GlyphRun> a un niveau supérieur correspondant <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.                  <xref:System.Windows.Documents.Glyphs> peut être utilisé dans l’arborescence d’éléments et dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] balisage pour représenter <xref:System.Windows.Media.GlyphRun> sortie.  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a>L’élément Glyphs  
 Le <xref:System.Windows.Documents.Glyphs> élément représente la sortie d’un <xref:System.Windows.Media.GlyphRun> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. La syntaxe de balisage suivante est utilisée pour décrire la <xref:System.Windows.Documents.Glyphs> élément.  
  
 [!code-xml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Les définitions de propriété suivantes correspondent aux quatre premiers attributs dans l’exemple de balisage.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Spécifie un identificateur de ressource : nom de fichier, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], ou référence à une ressource dans l’application .exe ou le conteneur.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Spécifie la taille de police dans les unités de surface (valeur par défaut est.96 pouces) de dessin.|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Spécifie des indicateurs pour les styles gras et italiques.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Spécifie le niveau de mise en page bidirectionnel. Paires et valeurs zéro impliquent la mise en page de gauche à droite. valeurs impaires impliquent la disposition de droite à gauche.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a>Propriété indices  
 Le <xref:System.Windows.Documents.Glyphs.Indices%2A> propriété est une chaîne de spécifications de glyphe. Lorsqu’une séquence de glyphes forme un cluster unique, la spécification du premier glyphe du cluster est précédée par la spécification du nombre de glyphes et de points de code sont combinés pour former le cluster. Le <xref:System.Windows.Documents.Glyphs.Indices%2A> propriété recueille dans une chaîne les propriétés suivantes.  
  
-   Index de glyphes  
  
-   Largeurs d’avance de glyphe  
  
-   Combinaison de vecteurs d’attachements de glyphe  
  
-   Mappage de cluster à partir de points de code aux glyphes  
  
-   Indicateurs de glyphes  
  
 Chaque spécification de glyphe présente comme suit.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a>Mesures de glyphe  
 Chaque glyphe définit des métriques qui spécifient comment il va s’aligner avec d’autres <xref:System.Windows.Documents.Glyphs>. Le graphique suivant définit les diverses qualités typographiques de deux caractères de glyphe différents.  
  
 ![Diagramme des mesures de glyphe de](../../../../docs/framework/wpf/advanced/media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a>Balise de glyphes  
 L’exemple de code suivant montre comment utiliser diverses propriétés de la <xref:System.Windows.Documents.Glyphs> élément [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Typographie dans WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)   
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [Texte](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)