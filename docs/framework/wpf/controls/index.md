---
title: "Contrôles | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: c50b3e328998b65ec47efe6d7457b36116813c77
ms.openlocfilehash: 3c9baa45741cbc21e1d22ad6a126d7c3d94370cb
ms.lasthandoff: 04/08/2017

---
# <a name="controls"></a>Contrôles
<a name="introduction"></a> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est fourni avec la plupart des composants d’interface utilisateur utilisés dans presque toutes les applications Windows, notamment <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.Menu> et <xref:System.Windows.Controls.ListBox>. Par le passé, ces objets étaient connus sous le nom de contrôles. Alors que le SDK [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] continue à utiliser le terme « contrôle » pour désigner vaguement toute classe représentant un objet visible dans une application, il est important de noter qu’une classe n’a pas besoin d’hériter de la classe <xref:System.Windows.Controls.Control> pour avoir une présence visible. Les classes qui héritent de la classe <xref:System.Windows.Controls.Control> contiennent un <xref:System.Windows.Controls.ControlTemplate> qui permet au consommateur d’un contrôle de changer radicalement l’apparence du contrôle sans devoir créer une sous-classe.  Cette rubrique traite de la façon dont les contrôles (qui héritent ou non de la classe <xref:System.Windows.Controls.Control>) sont couramment utilisés dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<<<<<<< HEAD
 
=======
   
>>>>>>> 4eb4097... fix build error
  
<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>Création d’une instance d’un contrôle  
 Vous pouvez ajouter un contrôle à une application en utilisant le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ou du code.  L’exemple suivant montre comment créer une application simple qui demande à un utilisateur d’entrer son nom et son prénom.  Cet exemple crée six contrôles : deux étiquettes, deux zones de texte et deux boutons en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Tous les contrôles peuvent être créés de la même façon.  
  
 [!code-xml[ControlsOverview#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 L’exemple suivant crée la même application dans le code. Par souci de concision, la création du <xref:System.Windows.Controls.Grid>, `grid1`, a été exclue de l’exemple.                   `grid1` a les mêmes définitions de colonne et de ligne que celles présentées dans l’exemple précédent en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-csharp[ControlsOverview#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>Changement de l’apparence d’un contrôle  
 Vous pouvez couramment être amené à changer l’apparence d’un contrôle pour ajuster l’aspect de votre application. Vous pouvez changer l’apparence d’un contrôle en effectuant l’une des opérations suivantes, selon ce que vous souhaitez accomplir :  
  
-   Modifier la valeur d’une propriété du contrôle  
  
-   Créer un <xref:System.Windows.Style> pour le contrôle  
  
-   Créer un <xref:System.Windows.Controls.ControlTemplate> pour le contrôle  
  
### <a name="changing-a-controls-property-value"></a>Changement de la valeur de propriété d’un contrôle  
 De nombreux contrôles ont des propriétés vous permettant de changer la manière dont le contrôle apparaît, comme la propriété <xref:System.Windows.Controls.Control.Background%2A> d’un <xref:System.Windows.Controls.Button>. Vous pouvez définir les propriétés de valeur en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et dans le code. L’exemple suivant définit les propriétés <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.FontSize%2A> et <xref:System.Windows.Controls.Control.FontWeight%2A> sur un <xref:System.Windows.Controls.Button> en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xml[ControlsOverview#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 L’exemple suivant définit les mêmes propriétés dans le code.  
  
 [!code-csharp[ControlsOverview#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Création d’un style pour un contrôle  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet de spécifier l’apparence de contrôles massifs, au lieu de définir des propriétés sur chaque instance dans l’application, en créant un <xref:System.Windows.Style>.                           L’exemple suivant crée un <xref:System.Windows.Style> appliqué à chaque <xref:System.Windows.Controls.Button> de l’application.                          Les définitions <xref:System.Windows.Style> sont généralement définies en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dans un <xref:System.Windows.ResourceDictionary>, comme la propriété <xref:System.Windows.FrameworkElement.Resources%2A> de <xref:System.Windows.FrameworkElement>.  
  
 [!code-xml[ControlsOverview#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Vous pouvez également appliquer un style à certains contrôles d’un type spécifique en assignant une clé au style et en spécifiant cette clé dans la propriété `Style` de votre contrôle.  Pour plus d’informations sur les styles, consultez [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
### <a name="creating-a-controltemplate"></a>Création d’un ControlTemplate  
 Un <xref:System.Windows.Style> vous permet de définir des propriétés sur plusieurs contrôles à la fois, mais il peut arriver que vous souhaitiez personnaliser l’apparence d’un <xref:System.Windows.Controls.Control> au delà de ce que vous pouvez faire en créant un <xref:System.Windows.Style>. Les classes qui héritent de la classe <xref:System.Windows.Controls.Control> ont un <xref:System.Windows.Controls.ControlTemplate> qui définit la structure et l’apparence d’un <xref:System.Windows.Controls.Control>. La propriété <xref:System.Windows.Controls.Control.Template%2A> d’un <xref:System.Windows.Controls.Control> étant publique, vous pouvez donner à un <xref:System.Windows.Controls.Control> un <xref:System.Windows.Controls.ControlTemplate> différent de sa valeur par défaut. Vous pouvez souvent spécifier un nouveau <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.Control> au lieu d’hériter d’un contrôle pour personnaliser l’apparence d’un <xref:System.Windows.Controls.Control>.  
  
 Considérez le même contrôle commun, <xref:System.Windows.Controls.Button>.  Le comportement principal d’un <xref:System.Windows.Controls.Button> est de permettre à une application de prendre des mesures quand l’utilisateur clique dessus.  Par défaut, <xref:System.Windows.Controls.Button> dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] apparaît comme un rectangle en relief.  Durant le développement d’une application, vous pouvez souhaiter tirer parti du comportement d’un <xref:System.Windows.Controls.Button>, à savoir en gérant l’événement clic du bouton. Mais vous pouvez changer l’apparence du bouton au delà de ce que vous pouvez faire en modifiant les propriétés du bouton.  Dans ce cas, vous pouvez créer un <xref:System.Windows.Controls.ControlTemplate>.  
  
 L’exemple suivant crée un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.Button>.  <xref:System.Windows.Controls.ControlTemplate> crée un <xref:System.Windows.Controls.Button> avec des angles arrondis et un arrière-plan dégradé.  <xref:System.Windows.Controls.ControlTemplate> contient un <xref:System.Windows.Controls.Border> dont le <xref:System.Windows.Controls.Border.Background%2A> est un <xref:System.Windows.Media.LinearGradientBrush> avec deux objets <xref:System.Windows.Media.GradientStop>.  Le premier <xref:System.Windows.Media.GradientStop> utilise la liaison de données pour lier la propriété <xref:System.Windows.Media.GradientStop.Color%2A> de <xref:System.Windows.Media.GradientStop> à la couleur d’arrière-plan du bouton.  Quand vous définissez la propriété <xref:System.Windows.Controls.Control.Background%2A> de <xref:System.Windows.Controls.Button>, la couleur de cette valeur est utilisée comme premier <xref:System.Windows.Media.GradientStop>. Pour plus d’informations sur la liaison de données, consultez [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md). L’exemple crée également un <xref:System.Windows.Trigger> qui change l’apparence de <xref:System.Windows.Controls.Button> quand <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> a la valeur `true`.  
  
 [!code-xml[ControlsOverview#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xml[ControlsOverview#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
>  Un <xref:System.Windows.Media.SolidColorBrush> doit être affecté à la propriété <xref:System.Windows.Controls.Control.Background%2A> de <xref:System.Windows.Controls.Button> pour que l’exemple fonctionne correctement.  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>Abonnement à des événements  
 Vous pouvez vous abonner à l’événement d’un contrôle en utilisant [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou du code, mais vous pouvez gérer uniquement un événement dans le code.  L’exemple suivant montre comment s’abonner à l’événement `Click` de <xref:System.Windows.Controls.Button>.  
  
 [!code-xml[ControlsOverview#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 L’exemple suivant gère l’événement `Click` de <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ControlsOverview#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>Contenu riche dans les contrôles  
 La plupart des classes qui héritent de la classe <xref:System.Windows.Controls.Control> peuvent contenir du contenu riche. Par exemple, un <xref:System.Windows.Controls.Label> peut contenir n’importe quel objet (chaîne, <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.Panel>, etc.).  Les classes suivantes assurent la prise en charge du contenu riche et agissent comme classes de base pour la plupart des contrôles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   <xref:System.Windows.Controls.ContentControl> : <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button> et <xref:System.Windows.Controls.ToolTip> sont quelques exemples de classes qui héritent de cette classe.  
  
-   <xref:System.Windows.Controls.ItemsControl> : <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.Menu> et <xref:System.Windows.Controls.Primitives.StatusBar> sont quelques exemples de classes qui héritent de cette classe.  
  
-   <xref:System.Windows.Controls.HeaderedContentControl> : <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.GroupBox> et <xref:System.Windows.Controls.Expander> sont quelques exemples de classes qui héritent de cette classe.  
  
-   <xref:System.Windows.Controls.HeaderedItemsControl> : <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TreeViewItem> et <xref:System.Windows.Controls.ToolBar> sont quelques exemples de classes qui héritent de cette classe.  
  
-  
  
 Pour plus d’informations sur ces classes de base, consultez [Modèle de contenu WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Contrôles par catégorie](../../../../docs/framework/wpf/controls/controls-by-category.md)   
 [Bibliothèque de contrôles](../../../../docs/framework/wpf/controls/control-library.md)   
 [Vue d’ensemble des modèles de données](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Entrée](../../../../docs/framework/wpf/advanced/input-wpf.md)   
 [Activer une commande](../../../../docs/framework/wpf/advanced/how-to-enable-a-command.md)   
 [Procédures pas à pas : création d’un bouton animé personnalisé](../../../../docs/framework/wpf/controls/walkthroughs-create-a-custom-animated-button.md)   
 [Personnalisation des contrôles](../../../../docs/framework/wpf/controls/control-customization.md)
