---
title: "Vue d&#39;ensemble de TextBox | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôles, TextBox"
  - "TextBox (contrôle), à propos du contrôle TextBox"
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Vue d&#39;ensemble de TextBox
La classe <xref:System.Windows.Controls.TextBox> vous permet d'afficher ou de modifier le texte non mis en forme.  Une utilisation courante d'un <xref:System.Windows.Controls.TextBox> est la modification de texte non formaté dans un formulaire.  Par exemple, un formulaire qui demande le nom de l'utilisateur, le numéro de téléphone, etc. utiliserait des contrôles <xref:System.Windows.Controls.TextBox> pour la saisie de texte.  Cette rubrique présente la classe <xref:System.Windows.Controls.TextBox> et fournit des exemples de la manière de l'utiliser en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et [!INCLUDE[TLA#tla_lhcshrp](../../../../includes/tlasharptla-lhcshrp-md.md)].  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="textbox_or_richtextbox"></a>   
## TextBox ou RichTextBox ?  
 <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.RichTextBox> permettent tous deux aux utilisateurs d'entrer du texte mais les deux contrôles sont utilisés pour des scénarios différents.  Une <xref:System.Windows.Controls.TextBox> requiert moins de ressources système qu'une <xref:System.Windows.Controls.RichTextBox>, ce qui est idéal lorsque seul du texte brut doit être modifié \(c'est\-à\-dire utilisé dans un formulaire\).  Une <xref:System.Windows.Controls.RichTextBox> est un meilleur choix lorsqu'il est nécessaire pour l'utilisateur de modifier du texte mis en forme, des images, des tables ou un autre contenu pris en charge.  Par exemple, la modification d'un document, d'un article ou d'un blog qui nécessite une mise en forme, des images, etc. est mieux réalisée à l'aide de <xref:System.Windows.Controls.RichTextBox>.  La table suivante résume les fonctionnalités principales de <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.TextBox>.  
  
|Contrôle|Vérification de l'orthographe en temps réel|Menu contextuel|Commandes de mise en forme telles que <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> \(Ctr\+B\)|Contenu <xref:System.Windows.Documents.FlowDocument> comme des images, des paragraphes, des tableaux, etc.|  
|--------------|-------------------------------------------------|---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Oui|Oui|Non|Non.|  
|<xref:System.Windows.Controls.RichTextBox>|Oui|Oui|Oui \(consulter [Vue d'ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)\)|Oui \(consulter [Vue d'ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)\)|  
  
> [!NOTE]
>  Bien que <xref:System.Windows.Controls.TextBox> ne prenne pas en charge les commandes de modification relatives à la mise en forme telles que <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> \(Ctr\+G\), de nombreuses commandes de base sont prises en charge par les deux contrôles telles que <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>.  Pour plus d'informations, consultez <xref:System.Windows.Documents.EditingCommands>.  
  
 Les fonctionnalités prises en charge par <xref:System.Windows.Controls.TextBox> sont décrites dans les sections ci\-dessous.  Pour plus d'informations sur <xref:System.Windows.Controls.RichTextBox>, consultez [Vue d'ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md).  
  
### Vérification de l'orthographe en temps réel  
 Vous pouvez activer la vérification de l'orthographe en temps réel dans un <xref:System.Windows.Controls.TextBox> ou un <xref:System.Windows.Controls.RichTextBox>.  Lorsque la vérification de l'orthographe est activée, une ligne rouge apparaît sous les mots mal orthographiés \(voir l'illustration ci\-dessous\).  
  
 ![Textbox avec vérification orthographique](../../../../docs/framework/wpf/controls/media/editing-textbox-with-spellchecking.png "Editing\_TextBox\_with\_Spellchecking")  
  
 Consultez [Activer la vérification de l'orthographe dans un contrôle d'édition de texte](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md) pour savoir comment activer la vérification de l'orthographe.  
  
### Menu contextuel  
 Par défaut, <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.RichTextBox> ont un menu contextuel qui apparaît lorsqu'un utilisateur clique avec le bouton droit à l'intérieur du contrôle.  Le menu contextuel autorise l'utilisateur à couper, copier ou coller \(voir l'image ci\-dessous\).  
  
 ![TextBox avec menu contextuel](../../../../docs/framework/wpf/controls/media/editing-textbox-with-context-menu.png "Editing\_TextBox\_with\_Context\_Menu")  
  
 Vous pouvez créer votre propre menu contextuel personnalisé pour remplacer le comportement par défaut.  Pour plus d'informations, consultez [Utiliser un menu contextuel personnalisé avec un TextBox](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md).  
  
<a name="creating_textboxes"></a>   
## Création de zones de texte  
 Une <xref:System.Windows.Controls.TextBox> peut être une ligne unique en hauteur ou comprendre plusieurs lignes.  Une <xref:System.Windows.Controls.TextBox> sur une ligne est mieux adaptée pour la saisie de petites quantités de texte brut \(par exemple, «   Nom », « Numéro de téléphone », etc.  dans un formulaire\).  L'exemple suivant montre comment créer une ligne de <xref:System.Windows.Controls.TextBox> unique.  
  
 [!code-xml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Vous pouvez également créer une <xref:System.Windows.Controls.TextBox> qui permet à l'utilisateur d'entrer plusieurs lignes de texte.  Par exemple, si votre formulaire demande une ébauche biographique de l'utilisateur, vous devriez utiliser une <xref:System.Windows.Controls.TextBox> qui prend en charge plusieurs lignes de texte.  L'exemple suivant indique comment utiliser [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour définir un contrôle <xref:System.Windows.Controls.TextBox> qui se développe automatiquement pour s'adapter à plusieurs lignes de texte.  
  
 [!code-xml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 La définition de l'attribut <xref:System.Windows.Controls.TextBox.TextWrapping%2A> à `Wrap` provoque le renvoi du texte à la ligne lorsque le bord du contrôle <xref:System.Windows.Controls.TextBox> est atteint, et à étirer automatiquement la hauteur du contrôle <xref:System.Windows.Controls.TextBox> pour faire de la place pour une nouvelle ligne, si nécessaire.  
  
 La définition de l'attribut <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> à `true` provoque l'insertion d'une nouvelle ligne lors de l'appui sur la touche RETOUR, en étirant encore une fois automatiquement la hauteur du contrôle <xref:System.Windows.Controls.TextBox> pour faire de la place pour une nouvelle ligne, si nécessaire.  
  
 L'attribut <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> ajoute une barre de défilement à la <xref:System.Windows.Controls.TextBox>, afin que le contenu de la <xref:System.Windows.Controls.TextBox> puisse être défilé si la <xref:System.Windows.Controls.TextBox> se développe au delà de la taille de la trame ou fenêtre qui l'entoure.  
  
 Pour plus d'informations sur les différentes tâches associées à l'utilisation d'une <xref:System.Windows.Controls.TextBox>, consultez [Rubriques Comment](../../../../docs/framework/wpf/controls/textbox-how-to-topics.md).  
  
<a name="editing_commands"></a>   
## Détecter quand le contenu est modifié  
 L'événement <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> doit être généralement utilisé pour détecter chaque fois que le texte d'un <xref:System.Windows.Controls.TextBox> ou d'un <xref:System.Windows.Controls.RichTextBox> est modifié, et non <xref:System.Windows.UIElement.KeyDown> comme vous pourriez vous y attendre.  Pour obtenir un exemple, consultez [Détecter la modification du texte figurant dans un TextBox](../../../../docs/framework/wpf/controls/how-to-detect-when-text-in-a-textbox-has-changed.md).  
  
## Voir aussi  
 [Rubriques Comment](../../../../docs/framework/wpf/controls/textbox-how-to-topics.md)   
 [Vue d'ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)