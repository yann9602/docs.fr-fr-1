---
title: "Collecte d&#39;encre | Microsoft Docs"
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
  - "collecter l'encre numérique"
  - "DefaultDrawingAttributes (propriété)"
  - "encre numérique, collecter"
  - "DrawingAttributes (propriété)"
  - "encre, collecter"
  - "InkCanvas (élément)"
  - "propriétés, DefaultDrawingAttributes"
  - "propriétés, DrawingAttributes"
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Collecte d&#39;encre
La collecte d'encre numérique fait partie des principales fonctionnalités de la plateforme [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md).  Cette rubrique présente des méthodes de collecte d'encre dans [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].  
  
## Composants requis  
 Pour utiliser les exemples suivants, vous devez d'abord installer [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] et [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].  Vous devez également comprendre comment écrire des applications pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Pour plus d'informations sur la mise en route de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Procédure pas à pas : mise en route de WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## Utilisation de l'élément InkCanvas  
 L'élément <xref:System.Windows.Controls.InkCanvas> offre la manière la plus simple de collecter de l'encre dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  L'élément <xref:System.Windows.Controls.InkCanvas> est semblable à l'objet <xref:Microsoft.Ink.InkOverlay> du [!INCLUDE[TLA2#tla_tpclssdk](../../../../includes/tla2sharptla-tpclssdk-md.md)] et des versions antérieures.  
  
 Utilisez un élément <xref:System.Windows.Controls.InkCanvas> pour recevoir et afficher l'entrée d'encre.  Généralement, vous entrez de l'encre à l'aide d'un stylet qui interagit avec un digitaliseur pour produire des traits d'encre.  En outre, une souris peut être utilisée à la place du stylet.  Les traits créés sont représentés comme objets <xref:System.Windows.Ink.Stroke> et ils peuvent être manipulés aussi bien par programme que par l'entrée d'utilisateur.  <xref:System.Windows.Controls.InkCanvas> permet aux utilisateurs de sélectionner, modifier ou supprimer un <xref:System.Windows.Ink.Stroke> existant.  
  
 En utilisant XAML, il est aussi facile d'installer la collecte d'encre que d'ajouter un élément `InkCanvas` à votre arborescence.  L'exemple suivant ajoute un <xref:System.Windows.Controls.InkCanvas> à un projet [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] par défaut créé dans [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)].  
  
 [!code-xml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]  
  
 L'élément `InkCanvas` peut également contenir des éléments enfants, ce qui permet d'ajouter des fonctions d'annotation manuscrite à quasiment tout type d'élément XAML.  Par exemple, pour ajouter des fonctions d'encrage à un élément de type texte, définissez\-le simplement en tant qu'enfant d'un <xref:System.Windows.Controls.InkCanvas>.  
  
 [!code-xml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]  
  
 Il est tout aussi simple d'ajouter une prise en charge pour baliser une image avec de l'encre.  
  
 [!code-xml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]  
  
### Modes InkCollection  
 Le <xref:System.Windows.Controls.InkCanvas> offre une prise en charge pour différents modes d'entrée via sa propriété <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>.  
  
### Manipulation d'encre  
 Le <xref:System.Windows.Controls.InkCanvas> offre une prise en charge pour de nombreuses opérations de modification de l'encre.  Par exemple, <xref:System.Windows.Controls.InkCanvas> prend en charge la gomme du stylet sans nécessiter de code supplémentaire pour ajouter les fonctionnalités à l'élément.  
  
#### Selection  
 La définition du mode de sélection est aussi simple que l'affectation de la valeur **Select** à la propriété <xref:System.Windows.Controls.InkCanvasEditingMode>.  Le code suivant définit le mode de modification d'après la valeur d'un <xref:System.Windows.Forms.CheckBox> :  
  
 [!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
 [!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]  
  
#### DrawingAttributes  
 Utilisez la propriété <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> pour modifier l'apparence des traits d'encre.  Par exemple, le membre <xref:System.Windows.Ink.DrawingAttributes.Color%2A> de <xref:System.Windows.Ink.DrawingAttributes> définit la couleur du <xref:System.Windows.Ink.Stroke> rendu.  L'exemple suivant fait passer la couleur des traits sélectionnés en rouge.  
  
 [!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
 [!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]  
  
### DefaultDrawingAttributes  
 La propriété <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> donne accès aux propriétés telles que la hauteur, la largeur et la couleur des traits à créer dans un <xref:System.Windows.Controls.InkCanvas>.  Une fois que vous modifiez <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, tous les futurs traits entrés dans le <xref:System.Windows.Controls.InkCanvas> sont restitués avec les nouvelles valeurs de propriété.  
  
 En plus de modifier <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> dans le fichier code\-behind, vous pouvez utiliser la syntaxe XAML pour spécifier des propriétés <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>.  Le code XAML suivant montre comment définir la propriété <xref:System.Windows.Ink.DrawingAttributes.Color%2A>.  Pour utiliser ce code, créez un nouveau projet [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] intitulé « HelloInkCanvas » dans Visual Studio 2005.  Remplacez le code du fichier Window1.xaml par le code suivant.  
  
 [!code-xml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]  
  
 Ensuite, ajoutez les gestionnaires d'événements de bouton suivants au fichier code\-behind, dans la classe Window1.  
  
 [!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]  
  
 Après avoir copié ce code, appuyez sur **F5** dans Microsoft Visual Studio 2005 pour exécuter le programme dans le débogueur.  
  
 Notez la façon dont le <xref:System.Windows.Controls.StackPanel> place les boutons sur le <xref:System.Windows.Controls.InkCanvas>.  Si vous essayez de mettre de l'encre en haut des boutons, le <xref:System.Windows.Controls.InkCanvas> collecte et restitue l'encre derrière les boutons.  En effet, les boutons sont des frères du <xref:System.Windows.Controls.InkCanvas>, par opposition aux enfants.  De même, les boutons sont plus haut dans l'ordre de plan ; l'encre est donc restituée derrière eux.  
  
## Voir aussi  
 <xref:System.Windows.Ink.DrawingAttributes>   
 <xref:System.Windows.InkCanvas.DefaultDrawingAttributes%2A>   
 <xref:System.Windows.Ink>