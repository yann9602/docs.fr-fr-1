---
title: "Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate"
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
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.assetid: 678dd116-43a2-4b8c-82b5-6b826f126e31
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0019b739c794cbffa62b49749371c2a19f752267
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate
<a name="introduction"></a>A <xref:System.Windows.Controls.ControlTemplate> spécifie la structure visuelle et le comportement d’un contrôle. Vous pouvez personnaliser l’apparence d’un contrôle en lui donnant un nouveau <xref:System.Windows.Controls.ControlTemplate>. Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate>, vous remplacez l’apparence d’un contrôle existant sans modifier ses fonctionnalités. Par exemple, vous pouvez arrondir les boutons dans votre application au lieu de la forme carrée par défaut, mais le bouton déclenchera toujours le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement.  
  
 Cette rubrique explique les différentes parties d’un <xref:System.Windows.Controls.ControlTemplate>, montre comment créer un simple <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.Button>et explique comment interpréter le contrat de contrôle d’un contrôle afin que vous puissiez personnaliser son apparence. Étant donné que vous créez un <xref:System.Windows.Controls.ControlTemplate> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez modifier l’apparence d’un contrôle sans écrire de code. Vous pouvez également utiliser un concepteur, tel que Microsoft Expression Blend, pour créer des modèles de contrôle personnalisé. Cette rubrique présente des exemples dans la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui personnaliser l’apparence d’un <xref:System.Windows.Controls.Button> et répertorie l’exemple complet à la fin de la rubrique. Pour plus d’informations sur l’utilisation d’Expression Blend, consultez [Définition d’un style pour un contrôle prenant en charge les modèles](http://go.microsoft.com/fwlink/?LinkId=161153).  
  
 Les illustrations suivantes montrent un <xref:System.Windows.Controls.Button> qui utilise le <xref:System.Windows.Controls.ControlTemplate> qui est créé dans cette rubrique.  
  
 ![Bouton avec un modèle de contrôle personnalisé. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Bouton qui utilise un modèle de contrôle personnalisé  
  
 ![Un bouton avec une bordure rouge. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Bouton qui utilise un modèle de contrôle personnalisé et sur lequel le pointeur de la souris se trouve  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique part du principe que vous savez comment créer et utiliser des contrôles et des styles, comme indiqué dans [Contrôles](../../../../docs/framework/wpf/controls/index.md). Les concepts abordés dans cette rubrique s’appliquent aux éléments qui héritent de la <xref:System.Windows.Controls.Control> (classe), à l’exception de la <xref:System.Windows.Controls.UserControl>. Vous ne pouvez pas appliquer un <xref:System.Windows.Controls.ControlTemplate> à un <xref:System.Windows.Controls.UserControl>.  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>Quand créer un ControlTemplate  
 Les contrôles ont de nombreuses propriétés, telles que <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, et <xref:System.Windows.Controls.Control.FontFamily%2A>, que vous pouvez définir pour spécifier différents aspects de l’apparence du contrôle, mais les modifications que vous pouvez apporter à la définition de ces propriétés sont limitées. Par exemple, vous pouvez définir le <xref:System.Windows.Controls.Control.Foreground%2A> propriété bleu et <xref:System.Windows.Controls.Control.FontStyle%2A> à italique sur un <xref:System.Windows.Controls.CheckBox>.  
  
 Sans la capacité de créer un nouveau <xref:System.Windows.Controls.ControlTemplate> pour les contrôles, tous les contrôles dans chaque [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-applications aurait la même apparence générale, ce qui limite la possibilité de créer une application avec une apparence personnalisée. Par défaut, chaque <xref:System.Windows.Controls.CheckBox> a des caractéristiques similaires. Par exemple, le contenu de la <xref:System.Windows.Controls.CheckBox> est toujours à droite de l’indicateur de sélection et la case à cocher est toujours utilisée pour indiquer que le <xref:System.Windows.Controls.CheckBox> est sélectionnée.  
  
 Vous créez un <xref:System.Windows.Controls.ControlTemplate> lorsque vous souhaitez personnaliser l’apparence du contrôle au-delà de ce qui est défini par les autres propriétés du contrôle. Dans l’exemple de la <xref:System.Windows.Controls.CheckBox>, supposons que vous voulez que le contenu de la case à cocher à se situer au-dessus de l’indicateur de sélection et que vous souhaitez un X pour indiquer que le <xref:System.Windows.Controls.CheckBox> est sélectionnée. Vous spécifiez ces modifications dans le <xref:System.Windows.Controls.ControlTemplate> de la <xref:System.Windows.Controls.CheckBox>.  
  
 L’illustration suivante montre un <xref:System.Windows.Controls.CheckBox> qui utilise une valeur par défaut <xref:System.Windows.Controls.ControlTemplate>.  
  
 ![Une case à cocher avec le modèle de contrôle par défaut. ] (../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Case à cocher qui utilise le modèle de contrôle par défaut  
  
 L’illustration suivante montre un <xref:System.Windows.Controls.CheckBox> qui utilise une personnalisée <xref:System.Windows.Controls.ControlTemplate> pour placer le contenu de la <xref:System.Windows.Controls.CheckBox> au-dessus de l’indicateur de sélection et affiche un X lorsque le <xref:System.Windows.Controls.CheckBox> est sélectionnée.  
  
 ![Une case à cocher avec un modèle de contrôle personnalisé. ] (../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Case à cocher qui utilise un modèle de contrôle personnalisé  
  
 Le <xref:System.Windows.Controls.ControlTemplate> pour le <xref:System.Windows.Controls.CheckBox> dans cet exemple est relativement complexe, par conséquent, cette rubrique utilise un exemple simple de création d’un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.Button>.  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>Changement de la structure visuelle d’un contrôle  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], un contrôle est souvent un composite <xref:System.Windows.FrameworkElement> objets. Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate>, vous combinez <xref:System.Windows.FrameworkElement> objets pour générer un seul contrôle. A <xref:System.Windows.Controls.ControlTemplate> doit avoir un seul <xref:System.Windows.FrameworkElement> comme élément racine. L’élément racine contient généralement d’autres <xref:System.Windows.FrameworkElement> objets. La combinaison d’objets constitue la structure visuelle du contrôle.  
  
 L’exemple suivant crée une personnalisée <xref:System.Windows.Controls.ControlTemplate> pour le <xref:System.Windows.Controls.Button>. Le <xref:System.Windows.Controls.ControlTemplate> crée la structure visuelle de le <xref:System.Windows.Controls.Button>. Cet exemple ne change pas l’apparence du bouton si vous placez le pointeur de la souris dessus ou cliquez dessus. La modification de l’apparence du bouton quand celui-ci est dans un autre état est décrite plus loin dans cette rubrique.  
  
 Dans cet exemple, la structure visuelle se compose des parties suivantes :  
  
-   A <xref:System.Windows.Controls.Border> nommé `RootElement` qui sert de racine du modèle <xref:System.Windows.FrameworkElement>.  
  
-   A <xref:System.Windows.Controls.Grid> qui est un enfant de `RootElement`.  
  
-   Un <xref:System.Windows.Controls.ContentPresenter> qui affiche le contenu du bouton. Le <xref:System.Windows.Controls.ContentPresenter> permet à n’importe quel type d’objet à afficher.  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>Conservation de la fonctionnalité des propriétés d’un contrôle en utilisant TemplateBinding  
 Lorsque vous créez un nouveau <xref:System.Windows.Controls.ControlTemplate>, vous souhaiterez toujours utiliser les propriétés publiques pour modifier l’apparence du contrôle. Le [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) extension de balisage est liée à une propriété d’un élément qui se trouve dans le <xref:System.Windows.Controls.ControlTemplate> à une propriété publique définie par le contrôle. Quand vous utilisez [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md), vous permettez aux propriétés sur le contrôle d’agir comme paramètres du modèle. Autrement dit, quand une propriété sur un contrôle est définie, cette valeur est passée à l’élément qui a le [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md).  
  
 L’exemple suivant répète la partie de l’exemple précédent qui utilise le [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) extension de balisage pour lier les propriétés d’éléments qui se trouvent dans le <xref:System.Windows.Controls.ControlTemplate> aux propriétés publiques définies par le bouton.  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 Dans cet exemple, le <xref:System.Windows.Controls.Grid> a son <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> propriété modèle lié à <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>. Étant donné que <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> est liée par modèle, vous pouvez créer plusieurs boutons qui utilisent la même <xref:System.Windows.Controls.ControlTemplate> et définir le <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> des valeurs différentes sur chaque bouton. Si <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> n’était pas de modèle lié à une propriété d’un élément dans le <xref:System.Windows.Controls.ControlTemplate>, en affectant la <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> d’un bouton n’aurait aucun impact sur l’apparence du bouton.  
  
 Notez que les noms des deux propriétés n’ont pas besoin d’être identiques. Dans l’exemple précédent, le <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> propriété de la <xref:System.Windows.Controls.Button> est modèle lié à la <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> propriété de la <xref:System.Windows.Controls.ContentPresenter>. Le contenu du bouton est ainsi positionné horizontalement. <xref:System.Windows.Controls.ContentPresenter>ne dispose pas d’une propriété nommée `HorizontalContentAlignment`, mais <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> peut être lié à <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>. Quand vous liez par modèle une propriété, vérifiez que les propriétés source et cible sont du même type.  
  
 La <xref:System.Windows.Controls.Control> classe définit plusieurs propriétés qui doivent être utilisées par le modèle de contrôle pour avoir un effet sur le contrôle lorsqu’elles sont définies. Comment la <xref:System.Windows.Controls.ControlTemplate> utilise la propriété dépend de la propriété. Le <xref:System.Windows.Controls.ControlTemplate> doit utiliser la propriété de l’une des manières suivantes :  
  
-   Un élément dans le <xref:System.Windows.Controls.ControlTemplate> modèle lie à la propriété.  
  
-   Un élément dans le <xref:System.Windows.Controls.ControlTemplate> hérite de la propriété parent d’un <xref:System.Windows.FrameworkElement>.  
  
 Le tableau suivant répertorie les propriétés visuelles héritées par un contrôle de la <xref:System.Windows.Controls.Control> classe. Il indique également si le modèle de contrôle par défaut d’un contrôle utilise la valeur de la propriété héritée ou s’il doit être lié par modèle.  
  
|Propriété|Méthode d’utilisation|  
|--------------|------------------|  
|<xref:System.Windows.Controls.Control.Background%2A>|Liaison de modèle|  
|<xref:System.Windows.Controls.Control.BorderThickness%2A>|Liaison de modèle|  
|<xref:System.Windows.Controls.Control.BorderBrush%2A>|Liaison de modèle|  
|<xref:System.Windows.Controls.Control.FontFamily%2A>|Héritage de propriété ou liaison de modèle|  
|<xref:System.Windows.Controls.Control.FontSize%2A>|Héritage de propriété ou liaison de modèle|  
|<xref:System.Windows.Controls.Control.FontStretch%2A>|Héritage de propriété ou liaison de modèle|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|Héritage de propriété ou liaison de modèle|  
|<xref:System.Windows.Controls.Control.Foreground%2A>|Héritage de propriété ou liaison de modèle|  
|<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>|Liaison de modèle|  
|<xref:System.Windows.Controls.Control.Padding%2A>|Liaison de modèle|  
|<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>|Liaison de modèle|  
  
 Le tableau répertorie uniquement les propriétés visuelles héritées de la <xref:System.Windows.Controls.Control> classe. Outre les propriétés répertoriées dans la table, un contrôle peut également hériter les <xref:System.Windows.FrameworkElement.DataContext%2A>, <xref:System.Windows.FrameworkElement.Language%2A>, et <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> propriétés à partir de l’élément parent de l’infrastructure.  
  
 En outre, si le <xref:System.Windows.Controls.ContentPresenter> est dans le <xref:System.Windows.Controls.ControlTemplate> d’un <xref:System.Windows.Controls.ContentControl>, le <xref:System.Windows.Controls.ContentPresenter> sera automatiquement lié au <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> et <xref:System.Windows.Controls.ContentControl.Content%2A> propriétés. De même, un <xref:System.Windows.Controls.ItemsPresenter> qui se trouve dans le <xref:System.Windows.Controls.ControlTemplate> d’un <xref:System.Windows.Controls.ItemsControl> crée automatiquement une liaison à la <xref:System.Windows.Controls.ItemsControl.Items%2A> et <xref:System.Windows.Controls.ItemsPresenter> propriétés.  
  
 L’exemple suivant crée deux boutons qui utilisent le <xref:System.Windows.Controls.ControlTemplate> défini dans l’exemple précédent. L’exemple définit le <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, et <xref:System.Windows.Controls.Control.FontSize%2A> propriétés sur chaque bouton. Définition de la <xref:System.Windows.Controls.Control.Background%2A> propriété a un effet, car elle est liée par modèle dans le <xref:System.Windows.Controls.ControlTemplate>. Bien que le <xref:System.Windows.Controls.Control.Foreground%2A> et <xref:System.Windows.Controls.Control.FontSize%2A> propriétés ne sont pas liées par modèle, leur définition a une incidence, car leurs valeurs sont héritées.  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 L’exemple précédent produit une sortie similaire à celle de l’illustration suivante.  
  
 ![Deux boutons, un bleu et un pourpre. ] (../../../../docs/framework/wpf/controls/media/ndp-buttontwo.png "NDP_ButtonTwo")  
Deux boutons avec des couleurs d’arrière-plan différentes  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>Modification de l’apparence d’un contrôle en fonction de son état  
 La différence entre un bouton avec son apparence par défaut et le bouton de l’exemple précédent est que le bouton par défaut change légèrement selon son état. Par exemple, l’apparence du bouton par défaut change quand l’utilisateur clique dessus ou pointe sur lui. Bien que le <xref:System.Windows.Controls.ControlTemplate> ne modifie pas les fonctionnalités d’un contrôle, il modifie le comportement du contrôle visual. Un comportement visuel décrit l’apparence du contrôle quand ce dernier est dans un état particulier. Pour comprendre la différence entre la fonctionnalité et le comportement visuel d’un contrôle, considérez l’exemple du bouton. La fonctionnalité du bouton consiste à déclencher le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement lorsque vous cliquez dessus, mais le comportement du bouton visual consiste à modifier son apparence lorsqu’il est désigné ou enfoncé.  
  
 Vous utilisez <xref:System.Windows.VisualState> objets pour spécifier l’apparence d’un contrôle lorsqu’il est dans un certain état. A <xref:System.Windows.VisualState> contient un <xref:System.Windows.Media.Animation.Storyboard> qui modifie l’apparence des éléments qui se trouvent dans le <xref:System.Windows.Controls.ControlTemplate>. Il est inutile d’écrire du code pour rendre cette opération, car la logique du contrôle modifie l’état à l’aide de la <xref:System.Windows.VisualStateManager>. Lorsque le contrôle passe à l’état spécifié par le <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType> propriété, le <xref:System.Windows.Media.Animation.Storyboard> commence. Lorsque le contrôle quitte l’état, le <xref:System.Windows.Media.Animation.Storyboard> s’arrête.  
  
 L’exemple suivant illustre la <xref:System.Windows.VisualState> qui modifie l’apparence d’un <xref:System.Windows.Controls.Button> lorsque le pointeur de la souris est sur lui. Le <xref:System.Windows.Media.Animation.Storyboard> modifie la couleur de bordure du bouton en modifiant la couleur de la `BorderBrush`. Si vous faites référence à la <xref:System.Windows.Controls.ControlTemplate> exemple au début de cette rubrique, souvenez-vous que `BorderBrush` est le nom de la <xref:System.Windows.Media.SolidColorBrush> qui est assignée à la <xref:System.Windows.Controls.Border.Background%2A> de la <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[VSMButtonTemplate#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 Le contrôle est chargé de définir les états dans le cadre de son contrat de contrôle, lequel est décrit en détail dans [Personnalisation des autres contrôles grâce à une bonne compréhension du contrat de contrôle](#customizing_other_controls_by_understanding_the_control_contract), plus loin dans cette rubrique. Le tableau suivant répertorie les États qui sont spécifiés pour le <xref:System.Windows.Controls.Button>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|----------------------|---------------------------|-----------------|  
|Normale|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de la souris est positionné sur le contrôle.|  
|Appuyé|CommonStates|Le contrôle est enfoncé.|  
|Désactivé|CommonStates|Le contrôle est désactivé.|  
|Avec focus|FocusStates|Le contrôle a le focus.|  
|Sans focus|FocusStates|Le contrôle n’a pas le focus.|  
  
 Le <xref:System.Windows.Controls.Button> définit deux groupes d’état : le `CommonStates` groupe contient les `Normal`, `MouseOver`, `Pressed`, et `Disabled` les États. le groupe `FocusStates` contient les états `Focused` et `Unfocused`. Les états d’un même groupe d’état s’excluent mutuellement. Le contrôle est toujours dans un état par groupe. Par exemple, un <xref:System.Windows.Controls.Button> peut avoir le focus même lorsque le pointeur de souris n’est pas ainsi, un <xref:System.Windows.Controls.Button> dans les `Focused` état peut être dans le `MouseOver`, `Pressed`, ou `Normal` état.  
  
 Vous ajoutez <xref:System.Windows.VisualState> objets <xref:System.Windows.VisualStateGroup> objets. Vous ajoutez <xref:System.Windows.VisualStateGroup> des objets sur le <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> propriété jointe. L’exemple suivant définit la <xref:System.Windows.VisualState> des objets pour le `Normal`, `MouseOver`, et `Pressed` États, qui se trouvent dans le `CommonStates` groupe. Le <xref:System.Windows.VisualState.Name%2A> de chaque <xref:System.Windows.VisualState> correspond au nom dans le tableau précédent. L’état `Disabled` et les états du groupe `FocusStates` sont omis pour que l’exemple reste concis, mais ils figurent dans l’exemple complet fourni à la fin de cette rubrique.  
  
> [!NOTE]
>  Veillez à définir le <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> propriété jointe sur la racine <xref:System.Windows.FrameworkElement> de la <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 L’exemple précédent produit une sortie similaire à celle des illustrations suivantes.  
  
 ![Bouton avec un modèle de contrôle personnalisé. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Bouton qui utilise un modèle de contrôle personnalisé dans l’état normal  
  
 ![Un bouton avec une bordure rouge. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Bouton qui utilise un modèle de contrôle personnalisé dans l’état de pointage avec la souris  
  
 ![La bordure est transparente sur un bouton enfoncé. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonpressed.png "NDP_ButtonPressed")  
Bouton qui utilise un modèle de contrôle personnalisé dans l’état enfoncé  
  
 Pour trouver les états visuels pour les contrôles inclus avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Styles et modèles Control](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>Spécification du comportement d’un contrôle durant les transitions entre états  
 Dans l’exemple précédent, l’apparence du bouton change également quand l’utilisateur clique dessus, mais à moins que le bouton ne soit enfoncé pendant une seconde complète, aucun effet n’est visible pour l’utilisateur. Par défaut, une seconde est nécessaire au déclenchement de l’animation. Étant donné que les utilisateurs sont susceptibles de cliquer sur et relâchez un bouton en beaucoup moins de temps, la rétroaction visuelle ne sera pas efficace si vous laissez le <xref:System.Windows.Controls.ControlTemplate> dans son état par défaut.  
  
 Vous pouvez spécifier la quantité de temps nécessaire à une animation pour se produire pour la transition douce entre un contrôle d’un état à un autre en ajoutant <xref:System.Windows.VisualTransition> des objets sur le <xref:System.Windows.Controls.ControlTemplate>. Lorsque vous créez un <xref:System.Windows.VisualTransition>, vous spécifiez un ou plusieurs des opérations suivantes :  
  
-   Temps nécessaire à une transition entre des états  
  
-   Changements supplémentaires dans l’apparence du contrôle durant la transition  
  
-   Les États du <xref:System.Windows.VisualTransition> est appliqué à.  
  
### <a name="specifying-the-duration-of-a-transition"></a>Spécification de la durée d’une transition  
 Vous pouvez spécifier la durée pendant laquelle une transition prend en définissant le <xref:System.Windows.VisualTransition.GeneratedDuration%2A> propriété. L’exemple précédent a un <xref:System.Windows.VisualState> qui spécifie que la bordure du bouton devient transparente quand le bouton est enfoncé, mais l’animation met trop de temps pour se déclencher lorsque le bouton est rapidement enfoncé et relâché. Vous pouvez utiliser un <xref:System.Windows.VisualTransition> pour spécifier la quantité de temps il prend le contrôle à la transition à l’état enfoncé. L’exemple suivant spécifie que le contrôle passe à l’état Pressed après un centième de seconde.  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>Spécification de changements de l’apparence du contrôle durant une transition  
 Le <xref:System.Windows.VisualTransition> contient un <xref:System.Windows.Media.Animation.Storyboard> qui commence lorsque le contrôle effectue des transitions entre États. Par exemple, vous pouvez spécifier qu’une animation particulière a lieu quand le contrôle passe de l’état `MouseOver` à l’état `Normal`. L’exemple suivant crée un <xref:System.Windows.VisualTransition> qui spécifie que lorsque l’utilisateur déplace le pointeur de la souris du bouton, la bordure du bouton change les bleu, puis en jaune, puis sur la couleur noire dans 1,5 seconde.  
  
 [!code-xaml[VSMButtonTemplate#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>Spécification du moment où VisualTransition est appliqué  
 Un <xref:System.Windows.VisualTransition> peut être limité à appliquer aux seuls certains États, ou elle peut être appliquée chaque fois que les contrôle effectue des transitions entre les États. Dans l’exemple précédent, le <xref:System.Windows.VisualTransition> est appliquée lorsque le contrôle passe à partir de la `MouseOver` l’état le `Normal` état ; dans l’exemple antérieur, la <xref:System.Windows.VisualTransition> est appliquée lorsque le contrôle passe à la `Pressed` état. Restreindre le moment où un <xref:System.Windows.VisualTransition> est appliqué en définissant le <xref:System.Windows.VisualTransition.To%2A> et <xref:System.Windows.VisualTransition.From%2A> propriétés. Le tableau suivant décrit les niveaux de restriction, du plus restrictif au moins restrictif.  
  
|Type de restriction|Valeur de From|Valeur de To|  
|-------------------------|-------------------|-----------------|  
|D’un état spécifié à un autre état spécifié|Le nom d’un<xref:System.Windows.VisualState>|Le nom d’un<xref:System.Windows.VisualState>|  
|De n’importe quel état à un état spécifié|Non défini|Le nom d’un<xref:System.Windows.VisualState>|  
|D’un état spécifié à n’importe quel état|Le nom d’un<xref:System.Windows.VisualState>|Non défini|  
|De n’importe quel état à n’importe quel autre état|Non défini|Non défini|  
  
 Vous pouvez avoir plusieurs <xref:System.Windows.VisualTransition> des objets dans un <xref:System.Windows.VisualStateGroup> qui font référence au même état, mais elles seront utilisées dans l’ordre de la table précédente. Dans l’exemple suivant, il existe deux <xref:System.Windows.VisualTransition> objets. Lorsque le contrôle effectue une transition à partir de la `Pressed` l’état le `MouseOver` état, le <xref:System.Windows.VisualTransition> qui possède à la fois <xref:System.Windows.VisualTransition.From%2A> et <xref:System.Windows.VisualTransition.To%2A> jeu est utilisé. Quand le contrôle passe d’un état autre que `Pressed` à l’état `MouseOver`, l’autre état est utilisé.  
  
 [!code-xaml[VSMButtonTemplate#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 Le <xref:System.Windows.VisualStateGroup> a un <xref:System.Windows.VisualStateGroup.Transitions%2A> propriété qui contient le <xref:System.Windows.VisualTransition> les objets qui s’appliquent à la <xref:System.Windows.VisualState> des objets dans le <xref:System.Windows.VisualStateGroup>. Comme le <xref:System.Windows.Controls.ControlTemplate> auteur, vous êtes libre d’inclure toute <xref:System.Windows.VisualTransition> souhaité. Toutefois, si le <xref:System.Windows.VisualTransition.To%2A> et <xref:System.Windows.VisualTransition.From%2A> propriétés sont définies sur les noms d’état qui ne figurent pas dans le <xref:System.Windows.VisualStateGroup>, le <xref:System.Windows.VisualTransition> est ignoré.  
  
 L’exemple suivant illustre la <xref:System.Windows.VisualStateGroup> pour le `CommonStates`. L’exemple définit un <xref:System.Windows.VisualTransition> pour chacune des suivantes du bouton passe.  
  
-   À l’état `Pressed`  
  
-   À l’état `MouseOver`  
  
-   De l’état `Pressed` à l’état `MouseOver`  
  
-   De l’état `MouseOver` à l’état `Normal`  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>Personnalisation des autres contrôles grâce à une bonne compréhension du contrat de contrôle  
 Un contrôle qui utilise un <xref:System.Windows.Controls.ControlTemplate> pour spécifier sa structure visuelle (à l’aide de <xref:System.Windows.FrameworkElement> objets) et le comportement visuel (à l’aide de <xref:System.Windows.VisualState> objets) utilise le modèle de contrôle des composants. Bon nombre des contrôles inclus avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 utilisent ce modèle. Les parties qui un <xref:System.Windows.Controls.ControlTemplate> auteur doit connaître est communiqués via le contrat de contrôle. Quand vous connaissez les composants d’un contrat de contrôle, vous pouvez personnaliser l’apparence de tout contrôle qui utilise le modèle de contrôle des composants.  
  
 Un contrat de contrôle comporte trois éléments :  
  
-   les éléments visuels utilisés par la logique du contrôle ;  
  
-   les états du contrôle et le groupe auquel appartient chaque état ;  
  
-   les propriétés publiques qui affectent visuellement le contrôle.  
  
### <a name="visual-elements-in-the-control-contract"></a>Éléments visuels du contrat de contrôle  
 Parfois, la logique d’un contrôle interagit avec un <xref:System.Windows.FrameworkElement> qui se trouve dans le <xref:System.Windows.Controls.ControlTemplate>. Par exemple, le contrôle peut gérer un événement de l’un de ses éléments. Lorsqu’un contrôle s’attend à trouver des particuliers <xref:System.Windows.FrameworkElement> dans les <xref:System.Windows.Controls.ControlTemplate>, il doit communiquer cette information à le <xref:System.Windows.Controls.ControlTemplate> auteur. Le contrôle utilise le <xref:System.Windows.TemplatePartAttribute> pour transmettre le type d’élément attendu, et ce qui doit être le nom de l’élément. Le <xref:System.Windows.Controls.Button> n’a pas <xref:System.Windows.FrameworkElement> parties dans son contrat de contrôle, mais d’autres contrôles, tels que le <xref:System.Windows.Controls.ComboBox>, faire.  
  
 L’exemple suivant illustre la <xref:System.Windows.TemplatePartAttribute> les objets qui sont spécifiées sur la <xref:System.Windows.Controls.ComboBox> classe. La logique de <xref:System.Windows.Controls.ComboBox> s’attend à trouver un <xref:System.Windows.Controls.TextBox> nommé `PART_EditableTextBox` et un <xref:System.Windows.Controls.Primitives.Popup> nommé `PART_Popup` dans son <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 L’exemple suivant montre une manière simplifiée <xref:System.Windows.Controls.ControlTemplate> pour le <xref:System.Windows.Controls.ComboBox> qui inclut les éléments qui sont spécifiées par le <xref:System.Windows.TemplatePartAttribute> des objets sur le <xref:System.Windows.Controls.ComboBox> classe.  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>États du contrat de contrôle  
 Les états d’un contrôle font également partie du contrat de contrôle. L’exemple de création d’un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.Button> montre comment spécifier l’apparence d’un <xref:System.Windows.Controls.Button> en fonction de ses États. Vous créez un <xref:System.Windows.VisualState> pour chaque état spécifié et placez tous les <xref:System.Windows.VisualState> objets qui partagent un <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> dans un <xref:System.Windows.VisualStateGroup>, comme décrit dans [modification de l’apparence d’un contrôle en fonction de son état](#changing_the_appearance_of_a_control_depending_on_its_state) plus haut dans cette rubrique. Les contrôles tiers doivent spécifier des États à l’aide de la <xref:System.Windows.TemplateVisualStateAttribute>, ce qui permet des outils de conception, telles que Expression Blend, pour exposer les États du contrôle pour la création de modèles de contrôle.  
  
 Pour trouver le contrat de contrôle pour les contrôles inclus avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Styles et modèles Control](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
### <a name="properties-in-the-control-contract"></a>Propriétés du contrat de contrôle  
 Les propriétés publiques qui affectent visuellement le contrôle sont également incluses dans le contrat de contrôle. Vous pouvez définir ces propriétés pour modifier l’apparence du contrôle sans créer de nouveau <xref:System.Windows.Controls.ControlTemplate>. Vous pouvez également utiliser le [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) extension de balisage pour lier les propriétés d’éléments qui se trouvent dans le <xref:System.Windows.Controls.ControlTemplate> aux propriétés publiques définies par le <xref:System.Windows.Controls.Button>.  
  
 L’exemple suivant illustre le contrat de contrôle pour le bouton.  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate>, il est souvent plus facile de commencer avec un existant <xref:System.Windows.Controls.ControlTemplate> et apporter des modifications. Vous pouvez effectuer l’une des opérations suivantes pour modifier un existant <xref:System.Windows.Controls.ControlTemplate>:  
  
-   Utiliser un concepteur, tel qu’Expression Blend, qui fournit une interface graphique utilisateur pour créer des modèles de contrôle. Pour plus d’informations, consultez [Définition d’un style pour un contrôle prenant en charge les modèles](http://go.microsoft.com/fwlink/?LinkId=161153).  
  
-   Obtenir la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> et le modifier. Pour trouver les modèles de contrôle par défaut compris dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Thèmes WPF par défaut](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Exemple complet  
 L’exemple suivant montre l’intégralité <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate> qui est décrite dans cette rubrique.  
  
 [!code-xaml[VSMButtonTemplate#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>Voir aussi  
 [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)
