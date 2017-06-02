---
title: "Vue d&#39;ensemble de RichTextBox | Microsoft Docs"
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
  - "contrôles, RichTextBox"
  - "RichTextBox (contrôle) (WPF), à propos du contrôle RichTextBox"
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Vue d&#39;ensemble de RichTextBox
Le contrôle <xref:System.Windows.Controls.RichTextBox> vous permet d'afficher ou de modifier le contenu d'un flux, y compris les paragraphes, images, tableaux, etc.  Cette rubrique présente la classe <xref:System.Windows.Controls.TextBox> et fournit des exemples de la manière de l'utiliser en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et [!INCLUDE[TLA#tla_lhcshrp](../../../../includes/tlasharptla-lhcshrp-md.md)].  
  
   
  
<a name="textbox_or_richtextbox"></a>   
## TextBox ou RichTextBox ?  
 <xref:System.Windows.Controls.RichTextBox> et <xref:System.Windows.Controls.TextBox> permettent tous deux aux utilisateurs de modifier du texte mais les deux contrôles s'utilisent dans des scénarios différents.  <xref:System.Windows.Controls.RichTextBox> est un meilleur choix lorsque l'utilisateur doit modifier du texte mis en forme, des images, des tableaux ou un autre contenu riche.  Par exemple, la modification d'un document, d'un article ou d'un blog qui nécessite une mise en forme, des images, etc. est mieux réalisée à l'aide de <xref:System.Windows.Controls.RichTextBox>.  Un <xref:System.Windows.Controls.TextBox> nécessite moins de ressources système qu'un <xref:System.Windows.Controls.RichTextBox> et est idéal lorsque seul du texte brut doit être modifié \(par exemple,  utilisation dans les formulaires\).  Consultez [Vue d'ensemble de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md) pour plus d'informations <xref:System.Windows.Controls.TextBox>.  Le tableau suivante résume les fonctionnalités principales de <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.RichTextBox>.  
  
|Contrôle|Vérification de l'orthographe en temps réel|Menu contextuel|Commandes de mise en forme telles que <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> \(Ctr\+B\)|Contenu <xref:System.Windows.Documents.FlowDocument> comme des images, des paragraphes, des tableaux, etc.|  
|--------------|-------------------------------------------------|---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Oui|Oui|Non|Non.|  
|<xref:System.Windows.Controls.RichTextBox>|Oui|Oui|Oui|Oui|  
  
 **Remarque :** Bien que <xref:System.Windows.Controls.TextBox> ne prenne pas en charge les commandes de mise en forme apparentées telles que <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> \(Ctr\+B\), les deux contrôles prennent en charge de nombreuses commandes de base comme <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>.  
  
 Les fonctionnalités énumérées dans le tableau ci\-dessus sont abordées plus en détail par la suite.  
  
<a name="creating_a_richtextbox"></a>   
## Création d'un RichTextBox  
 Le code suivant montre comment créer un <xref:System.Windows.Controls.RichTextBox> permettant à l'utilisateur de modifier du contenu enrichi.  
  
 [!code-xml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]  
  
 Précisons que le contenu modifié dans un <xref:System.Windows.Controls.RichTextBox> est un contenu de flux.  Un contenu de flux peut comprendre de nombres types d'éléments dont du texte mis en forme, des images, des listes et des tableaux.  Consultez [Vue d'ensemble des documents dynamiques](../../../../docs/framework/wpf/advanced/flow-document-overview.md) pour plus d'informations sur les documents dynamiques.  Pour pouvoir abriter du contenu de flux, un <xref:System.Windows.Controls.RichTextBox> contient un objet <xref:System.Windows.Documents.FlowDocument>, lequel contient en fait le contenu modifiable.  Pour illustrer un contenu de flux dans un <xref:System.Windows.Controls.RichTextBox>, le code suivant montre comment créer un <xref:System.Windows.Controls.RichTextBox> avec un paragraphe et du texte gras.  
  
 [!code-xml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]  
  
 [!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
 [!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]  
  
 L'illustration suivante montre le rendu de cet exemple.  
  
 ![RichTextBox avec contenu](../../../../docs/framework/wpf/controls/media/editing-richtextbox-with-content.png "Editing\_RichTextBox\_with\_Content")  
  
 Des éléments comme <xref:System.Windows.Documents.Paragraph> et <xref:System.Windows.Documents.Bold> déterminent l'apparence du contenu d'un <xref:System.Windows.Controls.RichTextBox>.  Lorsqu'un utilisateur apporte des changements au contenu du <xref:System.Windows.Controls.RichTextBox>, il modifie le contenu du flux.  Pour en savoir plus sur les fonctionnalités du contenu de flux et sur leur utilisation, consultez [Vue d'ensemble des documents dynamiques](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
 **Remarque :** un contenu dynamique placé dans un <xref:System.Windows.Controls.RichTextBox> ne se comporte pas tout à fait de la même façon qu'un contenu dynamique dans d'autres contrôles.  Par exemple, <xref:System.Windows.Controls.RichTextBox> ne comporte pas de colonnes et ne permet donc pas de redimensionnement automatique.  Par ailleurs, <xref:System.Windows.Controls.RichTextBox> ne dispose pas de fonctionnalités intégrées de recherche, de mode d'affichage, de navigation entre les pages et de zoom.  
  
<a name="realtime_spellechecking"></a>   
## Vérification de l'orthographe en temps réel  
 Vous pouvez activer la vérification de l'orthographe en temps réel dans un <xref:System.Windows.Controls.TextBox> ou un <xref:System.Windows.Controls.RichTextBox>.  Lorsque la vérification de l'orthographe est activée, une ligne rouge apparaît sous les mots mal orthographiés \(voir l'illustration ci\-dessous\).  
  
 ![Textbox avec vérification orthographique](../../../../docs/framework/wpf/controls/media/editing-textbox-with-spellchecking.png "Editing\_TextBox\_with\_Spellchecking")  
  
 Consultez [Activer la vérification de l'orthographe dans un contrôle d'édition de texte](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md) pour savoir comment activer la vérification de l'orthographe.  
  
<a name="context_menu"></a>   
## Menu contextuel  
 Par défaut, <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.RichTextBox> ont un menu contextuel qui apparaît lorsqu'un utilisateur clique avec le bouton droit à l'intérieur du contrôle.  Le menu contextuel autorise l'utilisateur à couper, copier ou coller \(voir l'illustration ci\-dessous\).  
  
 ![TextBox avec menu contextuel](../../../../docs/framework/wpf/controls/media/editing-textbox-with-context-menu.png "Editing\_TextBox\_with\_Context\_Menu")  
  
 Vous pouvez créer votre propre menu contextuel personnalisé pour remplacer celui par défaut.  Pour plus d'informations, consultez [Positionner un menu contextuel personnalisé dans un RichTextBox](../../../../docs/framework/wpf/controls/how-to-position-a-custom-context-menu-in-a-richtextbox.md).  
  
<a name="detect_when_content_changes"></a>   
## Commandes d'édition  
 Les commandes d'édition permettent aux utilisateurs de mettre en forme le contenu modifiable d'un <xref:System.Windows.Controls.RichTextBox>.  En dehors des commandes d'édition de base, <xref:System.Windows.Controls.RichTextBox> inclut des commandes de mise en forme que <xref:System.Windows.Controls.TextBox> ne prend pas en charge.  Par exemple, lorsqu'un utilisateur apporte des modifications dans un <xref:System.Windows.Controls.RichTextBox>, il peut appuyer sur Ctr\+B pour basculer la mise en forme en caractères gras.  Pour obtenir une liste exhaustive des commandes disponibles, consultez <xref:System.Windows.Documents.EditingCommands>.  Vous pouvez utiliser les raccourcis clavier et associer des commandes à d'autres contrôles comme des boutons.  L'exemple suivant montre comment créer une barre d'outils simple contenant des boutons avec lesquels l'utilisateur peut modifier la mise en forme du texte.  
  
 [!code-xml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]  
  
 L'illustration suivante montre le résultat de cet exemple.  
  
 ![RichTextBox avec barre d'outils](../../../../docs/framework/wpf/controls/media/editing-richtextbox-with-toobar.png "Editing\_RichTextBox\_with\_TooBar")  
  
<a name="editing_commands"></a>   
## Détecter quand le contenu est modifié  
 L'événement <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> doit être généralement utilisé pour détecter chaque fois que le texte d'un <xref:System.Windows.Controls.TextBox> ou d'un <xref:System.Windows.Controls.RichTextBox> est modifié, et non <xref:System.Windows.UIElement.KeyDown> comme vous pourriez vous y attendre.  Pour obtenir un exemple, consultez [Détecter la modification du texte figurant dans un TextBox](../../../../docs/framework/wpf/controls/how-to-detect-when-text-in-a-textbox-has-changed.md).  
  
<a name="save_load_and_print_richtextbox_content"></a>   
## Enregistrer, charger et imprimer le contenu d'un RichTextBox  
 L'exemple suivant montre comment enregistrer le contenu d'un <xref:System.Windows.Controls.RichTextBox> dans un fichier, le recharger de nouveau dans le <xref:System.Windows.Controls.RichTextBox>, et l'imprimer.  Vous trouverez ci\-dessous le code de l'exemple.  
  
 [!code-xml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
 Vous trouverez ci\-dessous le code\-behind de l'exemple.  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## Voir aussi  
 [Rubriques Comment](../../../../docs/framework/wpf/controls/richtextbox-how-to-topics.md)   
 [Vue d'ensemble de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)