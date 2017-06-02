---
title: "Mise en forme de texte avanc&#233;e | Microsoft Docs"
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
  - "mettre en forme (WPF)"
  - "texte (WPF)"
  - "typographie, mise en forme du texte"
ms.assetid: f0a7986e-f5b2-485c-a27d-f8e922022212
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Mise en forme de texte avanc&#233;e
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] fournit un ensemble fiable d'[!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] pour inclure du texte dans votre application.  Layout et [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)][!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], tel que <xref:System.Windows.Controls.TextBlock>, fournissent les éléments d'utilisation les plus courants et généraux pour la présentation de texte.  L'[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] de dessin, telle que <xref:System.Windows.Media.GlyphRunDrawing> et <xref:System.Windows.Media.FormattedText> permet d'inclure du texte mis en forme dans des dessins.  Au niveau le plus avancé, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], fournit un moteur de mise en forme de texte extensible pour contrôler chaque aspect de la présentation de texte, tel que la gestion du magasin de texte, la gestion de séquence de texte et la gestion d'objet incorporé.  
  
 Cette rubrique présente la mise en forme du texte [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  Elle porte principalement sur l'implémentation cliente et l'utilisation du moteur de mise en forme du texte [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
> [!NOTE]
>  Tous les exemples de code dans ce document se trouvent dans [Mise en forme de texte avancée, exemple](http://go.microsoft.com/fwlink/?LinkID=159965).  
  
   
  
<a name="prereq"></a>   
## Composants requis  
 Cette rubrique suppose que vous connaissez le niveau supérieur [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] utilisé pour la présentation de texte.  La plupart des scénarios utilisateur ne nécessitent pas les [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] de mise en forme de texte avancée décrites dans cette rubrique.  Pour une présentation des différentes [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] texte, consultez [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
<a name="section1"></a>   
## Mise en forme de texte avancée  
 La mise en page de texte et les contrôles [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournissent des propriétés de mise en forme qui permettent d'inclure facilement le texte mis en forme dans votre application.  Ces contrôles exposent des propriétés pour gérer la présentation de texte, ce qui inclut sa police, sa taille et sa couleur.  Dans des conditions normales, ces contrôles peuvent gérer la majorité de la présentation de texte dans votre application.  Cependant, certains scénarios avancés requièrent le contrôle du stockage de texte ainsi que la présentation du texte.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit un moteur de mise en forme du texte extensible dans ce but.  
  
 Les fonctionnalités de mise en forme de texte avancée dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sont constituées d'un moteur de mise en forme de texte, d'un magasin de texte, de séquences de texte et de propriétés de mise en forme.  Le moteur de mise en forme du texte, <xref:System.Windows.Media.TextFormatting.TextFormatter>, crée des lignes de texte à utiliser pour la présentation.  Cela est accompli en initialisant le processus de la mise en forme de ligne et en appelant les <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> du formateur de texte.  Le formateur de texte récupère les séquences de texte de votre magasin de texte en appelant la méthode <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> du magasin.  Ensuite, les objets <xref:System.Windows.Media.TextFormatting.TextRun> sont transformés en objets <xref:System.Windows.Media.TextFormatting.TextLine> par le formateur de texte et transmis à votre application pour l'inspection ou l'affichage.  
  
<a name="section2"></a>   
## Utilisation du formateur de texte  
 <xref:System.Windows.Media.TextFormatting.TextFormatter> est le moteur de mise en forme du texte [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] et il fournit des services pour mettre en forme et couper des lignes de texte.  Le formateur de texte peut gérer différents formats de caractères alphabétiques et il prend en charge la présentation de texte internationale.  
  
 Contrairement à une [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] texte traditionnelle, le <xref:System.Windows.Media.TextFormatting.TextFormatter> interagit avec le client de disposition de texte par l'intermédiaire d'un ensemble de méthodes de rappel.  Cela suppose que le client fournisse ces méthodes dans une implémentation de la classe <xref:System.Windows.Media.TextFormatting.TextSource>.  Le diagramme suivant montre l'interaction de la disposition du texte entre l'application cliente et <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagramme du client de disposition du texte et TextFormatter](../../../../docs/framework/wpf/advanced/media/textformatter01.png "TextFormatter01")  
Interaction entre l'application et TextFormatter  
  
 Le formateur de texte est utilisé pour récupérer des lignes de texte mis en forme dans le magasin de texte qui est une implémentation de <xref:System.Windows.Media.TextFormatting.TextSource>.  Cette opération est effectuée en créant une instance du formateur de texte et en utilisant la méthode <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A>.  Cette méthode crée une instance du formateur de texte et définit la hauteur et la largeur de ligne maximales.  Dès qu'une instance du formateur de texte est créée, le processus de création de ligne est démarré en appelant la méthode <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>.  <xref:System.Windows.Media.TextFormatting.TextFormatter> rappelle la source de texte pour récupérer le texte et les paramètres de mise en forme pour les séries de texte qui forment une ligne.  
  
 L'exemple suivant montre le processus de mise en forme d'un magasin de texte.  L'objet <xref:System.Windows.Media.TextFormatting.TextFormatter> est utilisé pour récupérer des lignes de texte du magasin de texte et mettre en forme la ligne de texte pour la placer dans le <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[TextFormatterExample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## Implémentation du magasin de texte client  
 Lorsque vous étendez le moteur de mise en forme du texte, vous devez implémenter et gérer tous les aspects du magasin de texte.  Ce n'est pas une tâche simple.  Le magasin de texte est chargé de suivre les propriétés de séquence de texte, les propriétés de paragraphe, les objets incorporés et tout autre contenu semblable.  Il fournit également au formateur de texte des objets <xref:System.Windows.Media.TextFormatting.TextRun> individuels que le formateur de texte utilise pour créer des objets <xref:System.Windows.Media.TextFormatting.TextLine>.  
  
 Pour gérer la virtualisation du magasin de texte, le magasin de texte doit être dérivé de <xref:System.Windows.Media.TextFormatting.TextSource>.  <xref:System.Windows.Media.TextFormatting.TextSource> définit la méthode que le formateur de texte utilise pour récupérer les séquences de texte du magasin de texte.  <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> est la méthode utilisée par le formateur de texte pour récupérer les séquences de texte utilisées dans la mise en forme de ligne.  L'appel à <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> est exécuté de manière répétitive par le formateur de texte jusqu'à ce que l'une des conditions suivantes existe :  
  
-   Un <xref:System.Windows.Media.TextFormatting.TextEndOfLine> ou une sous\-classe sont retournés.  
  
-   La largeur cumulée des séquences de texte dépasse la largeur de ligne maximale spécifiée dans l'appel pour créer le formateur de texte ou l'appel à la méthode <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> du formateur de texte.  
  
-   Une séquence de saut de ligne [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)], telle que "CF", "LF" ou "CRLF", est retournée.  
  
<a name="section4"></a>   
## Fourniture des séquences de texte  
 Le cœur du processus de mise en forme du texte est l'interaction entre le formateur de texte et le magasin de texte.  Votre implémentation <xref:System.Windows.Media.TextFormatting.TextSource> fournit au formateur de texte les objets et les propriétés <xref:System.Windows.Media.TextFormatting.TextRun> nécessaires à la mis en forme des séquences de texte.  Cette interaction est contrôlée par la méthode <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> appelée par le formateur de texte.  
  
 Le tableau suivant répertorie certains des objets <xref:System.Windows.Media.TextFormatting.TextRun> prédéfinis.  
  
|Type TextRun|Utilisation|  
|------------------|-----------------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Séquence de texte spécialisée utilisée pour renvoyer une représentation des glyphes de caractères au formateur de texte.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|La séquence de texte spécialisée utilisée pour fournir le contenu de mesure, le test de positionnement et le dessin est effectuée globalement, tel qu'un bouton ou une image dans le texte.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Séquence de texte spécialisée utilisée pour marquer la fin d'une ligne.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Séquence de texte spécialisée utilisée pour marquer la fin d'un paragraphe.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|Séquence de texte spécialisée utilisée pour marquer la fin d'un segment, pour terminer, par exemple, la portée affectée par une séquence <xref:System.Windows.Media.TextFormatting.TextModifier> précédente.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Séquence de texte spécialisée utilisée pour marquer une plage de caractères cachés.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Séquence de texte spécialisée utilisée pour modifier les propriétés de séquences de texte dans sa portée.  La portée s'étend à la séquence de texte <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> correspondante suivante ou au <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph> suivant.|  
  
 Chacun des objets <xref:System.Windows.Media.TextFormatting.TextRun> prédéfinis peut être sous\-classé.  Cela permet à la source de texte de fournir au formateur de texte des séquences de texte qui incluent des données personnalisées.  
  
 L'exemple de code suivant montre une méthode <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>.  Ce magasin de texte retourne des objets <xref:System.Windows.Media.TextFormatting.TextRun> au formateur de texte pour les traiter.  
  
 [!code-csharp[TextFormatterExample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
>  Dans cet exemple, le magasin de texte fournit les mêmes propriétés de texte à l'ensemble du texte.  Les magasins de textes avancés doivent implémenter leur propre gestion de plage pour que les caractères individuels aient des propriétés différentes.  
  
<a name="section5"></a>   
## Spécification des propriétés de mise en forme  
 Les objets <xref:System.Windows.Media.TextFormatting.TextRun> sont mis en forme en utilisant les propriétés fournies par le magasin de texte.  Ces propriétés sont de deux types, <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> et <xref:System.Windows.Media.TextFormatting.TextRunProperties>.  <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> gère les propriétés de paragraphe telles que <xref:System.Windows.TextAlignment> et <xref:System.Windows.FlowDirection>.  <xref:System.Windows.Media.TextFormatting.TextRunProperties> sont des propriétés qui peuvent être différentes pour chaque séquence de texte au sein d'un paragraphe, tel que le pinceau de premier plan, <xref:System.Windows.Media.Typeface> et taille de police.  Pour implémenter des types de propriétés de paragraphe personnalisé et de séquence de texte personnalisé, votre application doit créer des classes dérivées de <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> et de <xref:System.Windows.Media.TextFormatting.TextRunProperties>, respectivement.  
  
## Voir aussi  
 [Typographie dans WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)   
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)