---
title: Collecte d'encre
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
- ink [WPF], collecting
- InkCanvas element [WPF]
- properties [WPF], DrawingAttributes
- collecting digital ink [WPF]
- digital ink [WPF], collecting
- properties [WPF], DefaultDrawingAttributes
- DefaultDrawingAttributes property [WPF]
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cbf55b5d84420a6aa7af06e94497a85a2b54a0c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="collecting-ink"></a>Collecte d'encre
La collecte d’encre numérique fait partie des principales fonctionnalités de la plateforme [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md). Cette rubrique présente des méthodes de collecte d’encre dans [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].  
  
## <a name="prerequisites"></a>Prérequis  
 Pour utiliser les exemples suivants, vous devez d’abord installer [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] et [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Vous devez également comprendre comment écrire des applications pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Pour plus d’informations sur la prise en main de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [procédure pas à pas : Ma première application de bureau WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="using-the-inkcanvas-element"></a>Utilisation de l’élément InkCanvas  
 Le <xref:System.Windows.Controls.InkCanvas> élément fournit le moyen le plus simple pour collecter de l’encre dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Le <xref:System.Windows.Controls.InkCanvas> élément est similaire à la [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/microsoft.ink.inkoverlay\(v=vs.90\).aspx) de l’objet à partir de la [!INCLUDE[TLA2#tla_tpclssdk](../../../../includes/tla2sharptla-tpclssdk-md.md)] et les versions antérieures.  
  
 Utilisez un <xref:System.Windows.Controls.InkCanvas> élément pour recevoir et afficher l’entrée d’encre. Généralement, vous entrez de l’encre à l’aide d’un stylet qui interagit avec un digitaliseur pour produire des traits d’encre. En outre, vous pouvez utiliser une souris à la place du stylet. Les traits créés sont représentés en tant que <xref:System.Windows.Ink.Stroke> objets et elles peuvent être manipulées par programme et par l’utilisateur d’entrée. Le <xref:System.Windows.Controls.InkCanvas> permet aux utilisateurs de sélectionner, modifier ou supprimer une existante <xref:System.Windows.Ink.Stroke>.  
  
 En utilisant XAML, il est aussi facile d’installer la collecte d’encre que d’ajouter un élément `InkCanvas` à votre arborescence. L’exemple suivant ajoute une <xref:System.Windows.Controls.InkCanvas> à une valeur par défaut [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projet créé dans [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)].  
  
 [!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]  
  
 L’élément `InkCanvas` peut également contenir des éléments enfants, ce qui permet d’ajouter des fonctions d’annotation manuscrite à quasiment tout type d’élément XAML. Par exemple, pour ajouter des fonctionnalités pour l’écriture manuscrite à un élément de texte, fait simplement en un enfant d’un <xref:System.Windows.Controls.InkCanvas>.  
  
 [!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]  
  
 Il est tout aussi simple d’ajouter une prise en charge pour baliser une image avec de l’encre.  
  
 [!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]  
  
### <a name="inkcollection-modes"></a>Modes InkCollection  
 Le <xref:System.Windows.Controls.InkCanvas> prend en charge différents modes d’entrée via sa <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> propriété.  
  
### <a name="manipulating-ink"></a>Manipulation d’encre  
 Le <xref:System.Windows.Controls.InkCanvas> prend en charge de nombreuses opérations de modification de l’encre. Par exemple, <xref:System.Windows.Controls.InkCanvas> prend en charge l’arrière du stylet effacer sans code supplémentaire est nécessaire pour ajouter les fonctionnalités à l’élément.  
  
#### <a name="selection"></a>Sélection  
 Paramètre de mode de sélection est aussi simple que le paramètre de la <xref:System.Windows.Controls.InkCanvasEditingMode> propriété **sélectionnez**. Le code suivant définit le mode de modification en fonction de la valeur d’un <xref:System.Windows.Forms.CheckBox>:  
  
 [!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
 [!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]  
  
#### <a name="drawingattributes"></a>DrawingAttributes  
 Utilisez le <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> propriété à modifier l’apparence des traits d’encre. Par exemple, le <xref:System.Windows.Ink.DrawingAttributes.Color%2A> membre <xref:System.Windows.Ink.DrawingAttributes> définit la couleur de rendu <xref:System.Windows.Ink.Stroke>. L’exemple suivant fait passer la couleur des traits sélectionnés en rouge.  
  
 [!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
 [!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]  
  
### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes  
 Le <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> propriété fournit l’accès aux propriétés telles que la hauteur, largeur et la couleur des traits à créer dans un <xref:System.Windows.Controls.InkCanvas>. Une fois que vous modifiez le <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, tous les futurs traits entrés dans le <xref:System.Windows.Controls.InkCanvas> sont rendus avec les nouvelles valeurs de propriété.  
  
 Outre la modification la <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> dans le fichier code-behind, vous pouvez utiliser la syntaxe XAML pour la spécification <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> propriétés. Le code XAML suivant montre comment définir le <xref:System.Windows.Ink.DrawingAttributes.Color%2A> propriété. Pour utiliser ce code, créez un projet [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] intitulé « HelloInkCanvas » dans Visual Studio 2005. Remplacez le code du fichier Window1.xaml par le code suivant.  
  
 [!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]  
  
 Ensuite, ajoutez les gestionnaires d’événements de bouton suivants au fichier code-behind, dans la classe Window1.  
  
 [!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]  
  
 Après avoir copié ce code, appuyez sur **F5** dans Microsoft Visual Studio 2005 pour exécuter le programme dans le débogueur.  
  
 Notez comment la <xref:System.Windows.Controls.StackPanel> place les boutons sur le <xref:System.Windows.Controls.InkCanvas>. Si vous tentez d’encre en haut des boutons, le <xref:System.Windows.Controls.InkCanvas> collecte et restitue l’encre derrière les boutons. Il s’agit, car les boutons sont des frères de la <xref:System.Windows.Controls.InkCanvas> par opposition aux enfants. De même, les boutons sont plus haut dans l’ordre de plan ; l’encre est donc restituée derrière eux.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Ink.DrawingAttributes>  
 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>  
 <xref:System.Windows.Ink>
