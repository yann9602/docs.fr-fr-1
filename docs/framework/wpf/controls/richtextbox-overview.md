---
title: Vue d'ensemble de RichTextBox
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
- controls [WPF], RichTextBox
- RichTextBox control [WPF], about RichTextBox control
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 41b423235fc2ed9c0e0612c90017d41ab0e83d0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="richtextbox-overview"></a>Vue d'ensemble de RichTextBox
Le <xref:System.Windows.Controls.RichTextBox> contrôle permet d’afficher ou modifier le contenu de flux, y compris des paragraphes, des images, des tables et bien plus encore. Cette rubrique présente la <xref:System.Windows.Controls.TextBox> classe et fournit des exemples de son utilisation dans les deux [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et [!INCLUDE[TLA#tla_lhcshrp](../../../../includes/tlasharptla-lhcshrp-md.md)].  
  
  
<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox ou RichTextBox ?  
 Les deux <xref:System.Windows.Controls.RichTextBox> et <xref:System.Windows.Controls.TextBox> permettre aux utilisateurs de modifier le texte, toutefois, les deux contrôles sont utilisés dans des scénarios différents. A <xref:System.Windows.Controls.RichTextBox> est un meilleur choix lorsqu’il est nécessaire pour l’utilisateur de modifier le texte mis en forme, des images, des tables ou autre contenu riche. Par exemple, la modification d’un document, un article ou un blog qui nécessite une mise en forme, des images, etc. est mieux réalisée à l’aide un <xref:System.Windows.Controls.RichTextBox>. A <xref:System.Windows.Controls.TextBox> nécessite moins de ressources système un <xref:System.Windows.Controls.RichTextBox> et est idéal lorsque uniquement du texte brut doit être modifié (autrement dit, l’utilisation dans les formulaires). Consultez [vue d’ensemble de la zone de texte](../../../../docs/framework/wpf/controls/textbox-overview.md) pour plus d’informations sur <xref:System.Windows.Controls.TextBox>. Le tableau ci-dessous récapitule les principales fonctionnalités de <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.RichTextBox>.  
  
|Contrôle|Vérification de l’orthographe en temps réel|Menu contextuel|Mise en forme des commandes telles que <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (CTRL + B)|<xref:System.Windows.Documents.FlowDocument>contenu tels que des images, des paragraphes, des tables, etc.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Oui|Oui|Non|Non.|  
|<xref:System.Windows.Controls.RichTextBox>|Oui|Oui|Oui|Oui|  
  
 **Remarque :** bien que <xref:System.Windows.Controls.TextBox> ne prend pas en charge la mise en forme des commandes associées comme <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (CTRL + B), de nombreuses commandes de base sont pris en charge par les deux contrôles tels que <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>.  
  
 Les fonctionnalités du tableau ci-dessus sont présentées plus en détail dans la suite de ce document.  
  
<a name="creating_a_richtextbox"></a>   
## <a name="creating-a-richtextbox"></a>Création d’un contrôle RichTextBox  
 Le code ci-dessous montre comment créer un <xref:System.Windows.Controls.RichTextBox> qu’un utilisateur de modifier du contenu rich.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]  
  
 Plus précisément, le contenu est modifié dans un <xref:System.Windows.Controls.RichTextBox> est le contenu de flux. Le contenu dynamique peut contenir de nombreux types d’éléments, notamment du texte mis en forme, des images, des listes et des tableaux. Pour obtenir des informations complètes sur les documents dynamiques, consultez [Vue d’ensemble des documents dynamiques](../../../../docs/framework/wpf/advanced/flow-document-overview.md). Afin de contenir le contenu de flux, un <xref:System.Windows.Controls.RichTextBox> hôtes un <xref:System.Windows.Documents.FlowDocument> objet qui contient le contenu modifiable. Pour illustrer le contenu de flux dans un <xref:System.Windows.Controls.RichTextBox>, le code suivant montre comment créer un <xref:System.Windows.Controls.RichTextBox> avec un paragraphe et du texte en gras.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]  
  
 [!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
 [!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]  
  
 L’illustration suivante montre le rendu de cet exemple.  
  
 ![Contrôle RichTextBox avec du contenu](../../../../docs/framework/wpf/controls/media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")  
  
 Éléments tels que <xref:System.Windows.Documents.Paragraph> et <xref:System.Windows.Documents.Bold> déterminer comment le contenu à l’intérieur d’un <xref:System.Windows.Controls.RichTextBox> s’affiche. Comme un utilisateur modifie le <xref:System.Windows.Controls.RichTextBox> contenu, ils changent le contenu de ce flux. Pour en savoir plus sur les fonctionnalités et l’utilisation du contenu dynamique, consultez [Vue d’ensemble des documents dynamiques](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
 **Remarque :** du contenu à l’intérieur d’un <xref:System.Windows.Controls.RichTextBox> ne se comporte pas exactement comme le contenu de flux contenu dans d’autres contrôles. Par exemple, il n’existe aucune colonne dans un <xref:System.Windows.Controls.RichTextBox> et donc pas de redimensionnement automatique. De même, intégrées dans les fonctionnalités de recherche, de mode d’affichage, de navigation entre les pages et de zoom ne sont pas disponibles dans un <xref:System.Windows.Controls.RichTextBox>.  
  
<a name="realtime_spellechecking"></a>   
## <a name="real-time-spell-checking"></a>Vérification de l’orthographe en temps réel  
 Vous pouvez activer la correction orthographique en temps réel une <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.RichTextBox>. Lorsque la vérification de l’orthographe est activée, une ligne rouge apparaît sous les mots mal orthographiés (voir l’illustration ci-dessous).  
  
 ![Contrôle TextBox avec vérification de l’orthographe](../../../../docs/framework/wpf/controls/media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Pour savoir comment activer la vérification de l’orthographe, consultez [Activer la vérification de l’orthographe dans un contrôle d’édition de texte](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md).  
  
<a name="context_menu"></a>   
## <a name="context-menu"></a>Menu contextuel  
 Par défaut, les deux <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.RichTextBox> ont un menu contextuel qui s’affiche quand un utilisateur clique dans le contrôle. Ce menu contextuel permet à l’utilisateur de couper, de copier ou de coller du texte (voir l’illustration ci-dessous).  
  
 ![Contrôle TextBox avec un menu contextuel](../../../../docs/framework/wpf/controls/media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Vous pouvez créer votre propre menu contextuel personnalisé pour remplacer celui par défaut. Pour plus d’informations, consultez [Positionner un menu contextuel personnalisé dans un RichTextBox](../../../../docs/framework/wpf/controls/how-to-position-a-custom-context-menu-in-a-richtextbox.md).  
  
<a name="detect_when_content_changes"></a>   
## <a name="editing-commands"></a>Commandes d’édition  
 Modification de commandes de permettre aux utilisateurs de mettre en forme le contenu modifiable à l’intérieur d’un <xref:System.Windows.Controls.RichTextBox>. Outre la base des commandes, de modification <xref:System.Windows.Controls.RichTextBox> inclut la mise en forme de commandes <xref:System.Windows.Controls.TextBox> ne prend pas en charge. Par exemple, lors de la modification dans un <xref:System.Windows.Controls.RichTextBox>, un utilisateur peut appuyer sur CTRL + B pour basculer la mise en forme du texte en gras. Consultez <xref:System.Windows.Documents.EditingCommands> pour une liste complète des commandes disponibles. Outre l’utilisation des raccourcis clavier, vous pouvez associer des commandes à d’autres contrôles, notamment des boutons. L’exemple suivant montre comment créer une barre d’outils simple contenant des boutons que l’utilisateur peut utiliser pour modifier la mise en forme du texte.  
  
 [!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]  
  
 L’illustration suivante montre comment cet exemple s’affiche.  
  
 ![Contrôle RichTextBox avec une barre d’outils](../../../../docs/framework/wpf/controls/media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_Content")  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>Détecter la modification du contenu  
 Généralement les <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> événement doit être utilisé pour détecter chaque fois que le texte dans un <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.RichTextBox> modifié, et non <xref:System.Windows.UIElement.KeyDown> comme prévu. Pour obtenir un exemple, consultez [Détecter la modification du texte figurant dans un TextBox](../../../../docs/framework/wpf/controls/how-to-detect-when-text-in-a-textbox-has-changed.md).  
  
<a name="save_load_and_print_richtextbox_content"></a>   
## <a name="save-load-and-print-richtextbox-content"></a>Enregistrer, charger et imprimer le contenu d'un RichTextBox  
 L’exemple suivant montre comment enregistrer le contenu d’un <xref:System.Windows.Controls.RichTextBox> vers un fichier, charger à nouveau dans le <xref:System.Windows.Controls.RichTextBox>et imprimer le contenu. Voici le balisage de l’exemple.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
 Voici le code-behind de l’exemple.  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/controls/richtextbox-how-to-topics.md)  
 [Vue d’ensemble de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)
