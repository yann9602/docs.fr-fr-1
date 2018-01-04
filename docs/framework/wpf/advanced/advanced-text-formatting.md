---
title: "Mise en forme de texte avancée"
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
- formatting [WPF]
- text [WPF]
- typography [WPF], text formatting
ms.assetid: f0a7986e-f5b2-485c-a27d-f8e922022212
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bb2664b267301fdf1e3a67e385595a5d28212bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-text-formatting"></a>Mise en forme de texte avancée
Le [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] fournit un ensemble robuste de [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] pour inclure du texte dans votre application. Mise en page et [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], tel que <xref:System.Windows.Controls.TextBlock>, fournir les plus courants et général utiliser des éléments de présentation de texte. Dessin [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], tel que <xref:System.Windows.Media.GlyphRunDrawing> et <xref:System.Windows.Media.FormattedText>, fournir un moyen pour inclure le texte mis en forme dans des dessins. Au niveau le plus avancé, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit un moteur de contrôler tous les aspects de la présentation de texte, tels que la gestion du magasin de texte, la gestion de mise en forme de texte et gestion de l’objet incorporé de mise en forme du texte extensible.  
  
 Cette rubrique fournit une introduction au [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] mise en forme du texte. Il se concentre sur l’implémentation cliente et l’utilisation de la [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] du moteur de mise en forme de texte.  
  
> [!NOTE]
>  Vous trouverez tous les exemples de code dans ce document dans le [mise en forme de texte avancée, exemple](http://go.microsoft.com/fwlink/?LinkID=159965).  
  

  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique suppose que vous êtes familiarisé avec le niveau supérieur [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] utilisé pour la présentation du texte. La plupart des scénarios utilisateur ne nécessitent pas de la mise en forme de texte avancée [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] décrites dans cette rubrique. Pour une introduction à l’autre texte [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], consultez [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>Mise en forme de texte avancée  
 La mise en page de texte et [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] contrôles [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournissent des propriétés de mise en forme qui vous permettent d’inclure facilement le texte mis en forme dans votre application. Ces contrôles exposent un certain nombre de propriétés permettant de gérer la présentation du texte, ce qui inclut sa police, sa taille et sa couleur. Normalement, ces contrôles peuvent gérer la majorité de la présentation du texte dans votre application. Toutefois, certains scénarios avancés nécessitent le contrôle du stockage de texte, ainsi que sa présentation. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit un moteur de mise en forme du texte extensible dans ce but.  
  
 Le fonctionnalités de mise en forme de texte avancée trouvé dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] se composent d’un texte mise en forme du moteur, un magasin de texte, les exécutions de texte et de mise en forme de propriétés. Le moteur, la mise en forme de texte <xref:System.Windows.Media.TextFormatting.TextFormatter>, crée des lignes de texte à utiliser pour la présentation. Pour cela, l’initialisation du processus de mise en forme de ligne et en appelant le formateur de texte <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>. Le formateur de texte récupère les séquences de texte à partir de votre magasin de texte en appelant la banque de <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> (méthode). Le <xref:System.Windows.Media.TextFormatting.TextRun> objets sont transformés en <xref:System.Windows.Media.TextFormatting.TextLine> les objets par le formateur de texte et transmis à votre application pour l’inspection ou l’affichage.  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>Utilisation du formateur de texte  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>est le [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] mise en forme du moteur et fournit des services de mise en forme et couper des lignes de texte. Le formateur de texte peut gérer différents formats de caractères alphabétiques et prend en charge la présentation du texte international.  
  
 Contrairement à un texte traditionnelle [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)], le <xref:System.Windows.Media.TextFormatting.TextFormatter> interagit avec un client de mise en page de texte via un ensemble de méthodes de rappel. Il nécessite le client fournisse ces méthodes dans une implémentation de la <xref:System.Windows.Media.TextFormatting.TextSource> classe. Le diagramme suivant illustre l’interaction de mise en page de texte entre l’application cliente et <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagramme du client de disposition du texte et TextFormatter](../../../../docs/framework/wpf/advanced/media/textformatter01.png "TextFormatter01")  
Interaction entre l’application et TextFormatter  
  
 Le formateur de texte est utilisé pour récupérer les lignes de texte mis en forme à partir du magasin de texte, qui est une implémentation de <xref:System.Windows.Media.TextFormatting.TextSource>. Cela est effectué en créant une instance du module de formatage de texte à l’aide de la <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> (méthode). Cette méthode crée une instance du formateur de texte et définit la hauteur et la largeur de ligne maximales. Dès qu’une instance du module de formatage de texte est créée, le processus de création de ligne est lancé en appelant le <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> (méthode). <xref:System.Windows.Media.TextFormatting.TextFormatter>rappelle à la source de texte pour récupérer le texte et les paramètres de mise en forme pour les exécutions de texte qui forment une ligne.  
  
 L’exemple suivant illustre le processus de mise en forme d’un magasin de texte. Le <xref:System.Windows.Media.TextFormatting.TextFormatter> objet est utilisé pour récupérer des lignes de texte à partir du magasin de texte et puis mettre en forme la ligne de texte pour la placer dans le <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[TextFormatterExample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>Implémentation du magasin de texte client  
 Quand vous étendez le moteur de mise en forme du texte, vous devez implémenter et gérer tous les aspects du magasin de texte. Cela n’est pas une tâche facile. Le magasin de texte est chargé de suivre les propriétés de séquence de texte, les propriétés de paragraphe, les objets incorporés et tout autre contenu similaire. Il fournit également le formateur de texte avec une personne <xref:System.Windows.Media.TextFormatting.TextRun> que le formateur de texte utilise pour créer les objets <xref:System.Windows.Media.TextFormatting.TextLine> objets.  
  
 Pour gérer la virtualisation du magasin de texte, le magasin de texte doit être dérivé de <xref:System.Windows.Media.TextFormatting.TextSource>. <xref:System.Windows.Media.TextFormatting.TextSource>définit la méthode que le formateur de texte utilise pour récupérer les séquences de texte à partir du magasin de texte. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>est la méthode utilisée par le formateur de texte pour extraire le texte s’exécute utilisée dans la ligne mise en forme. L’appel à <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> est effectué à plusieurs reprises par le formateur de texte jusqu'à ce qu’une des conditions suivantes se produit :  
  
-   Un <xref:System.Windows.Media.TextFormatting.TextEndOfLine> ou une sous-classe sont retournés.  
  
-   La largeur cumulée des séquences de texte dépasse la largeur de ligne maximale spécifiée dans l’appel pour créer le formateur de texte ou de l’appel au formateur de texte <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> (méthode).  
  
-   A [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] séquence de saut de ligne, telles que « CF », « LF » ou « CRLF », est retournée.  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>Fourniture des séquences de texte  
 Le cœur du processus de mise en forme du texte est l’interaction entre le formateur de texte et le magasin de texte. Votre implémentation de <xref:System.Windows.Media.TextFormatting.TextSource> fournit le formateur de texte avec le <xref:System.Windows.Media.TextFormatting.TextRun> objets et les propriétés permettant de mettre en forme le texte s’exécute. Cette interaction est contrôlée par le <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> (méthode), qui est appelée par le formateur de texte.  
  
 Le tableau suivant répertorie certaines des prédéfinis <xref:System.Windows.Media.TextFormatting.TextRun> objets.  
  
|Type TextRun|Utilisation|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Séquence de texte spécialisée utilisée pour passer une représentation des glyphes de caractères au formateur de texte.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Séquence de texte spécialisée utilisée pour fournir du contenu dont la mesure, le test de positionnement et le dessin sont effectués globalement, par exemple un bouton ou une image dans le texte.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Séquence de texte spécialisée utilisée pour marquer la fin d’une ligne.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Séquence de texte spécialisée utilisée pour marquer la fin d’un paragraphe.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|La séquence de texte spécialisé utilisée pour marquer la fin d’un segment, par exemple à la fin de la portée affectée par une précédente <xref:System.Windows.Media.TextFormatting.TextModifier> exécuter.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Séquence de texte spécialisée utilisée pour marquer une plage de caractères masqués.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Séquence de texte spécialisée utilisée pour modifier les propriétés des séquences de texte dans sa portée. La portée s’étend à la correspondance suivante <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> séquence de texte, ou dans l’autre <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>.|  
  
 Un des prédéfinis <xref:System.Windows.Media.TextFormatting.TextRun> objets peuvent être sous-classés. Cela permet à votre source de texte de fournir au formateur de texte des séquences de texte qui incluent des données personnalisées.  
  
 L’exemple suivant montre un <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> (méthode). Ce magasin de texte retourne <xref:System.Windows.Media.TextFormatting.TextRun> objets pour le formateur de texte pour le traitement.  
  
 [!code-csharp[TextFormatterExample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
>  Dans cet exemple, le magasin de texte fournit les mêmes propriétés de texte à l’ensemble du texte. Les magasins de texte avancés doivent implémenter leur propre gestion de plage pour que les caractères individuels aient des propriétés distinctes.  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>Spécification des propriétés de mise en forme  
 <xref:System.Windows.Media.TextFormatting.TextRun>objets sont mis en forme à l’aide des propriétés fournies par le magasin de texte. Ces propriétés sont de deux types, <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> et <xref:System.Windows.Media.TextFormatting.TextRunProperties>. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>gérer les propriétés de paragraphe, par exemple <xref:System.Windows.TextAlignment> et <xref:System.Windows.FlowDirection>. <xref:System.Windows.Media.TextFormatting.TextRunProperties>sont des propriétés qui peuvent être différentes pour chaque exécution d’un paragraphe, tels que le pinceau de premier plan, de texte <xref:System.Windows.Media.Typeface>et la taille de police. Pour implémenter le paragraphe personnalisé et exécuter des types de propriété de texte personnalisé, votre application doit créer des classes qui dérivent <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> et <xref:System.Windows.Media.TextFormatting.TextRunProperties> respectivement.  
  
## <a name="see-also"></a>Voir aussi  
 [Typographie dans WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
