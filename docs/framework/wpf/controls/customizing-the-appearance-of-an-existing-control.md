---
title: "Personnalisation de l&#39;apparence d&#39;un contr&#244;le existant en cr&#233;ant un ControlTemplate | Microsoft Docs"
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
  - "contrat de contrôle (WPF)"
  - "contrôles (WPF), apparence spécifiée par l'état"
  - "contrôles (WPF), modifications de la structure visuelle"
  - "ControlTemplate (WPF), personnaliser pour des contrôles existants"
  - "définir l'apparence de contrôles (WPF)"
  - "modèles (WPF), personnalisés pour des contrôles existants"
ms.assetid: 678dd116-43a2-4b8c-82b5-6b826f126e31
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Personnalisation de l&#39;apparence d&#39;un contr&#244;le existant en cr&#233;ant un ControlTemplate
<a name="introduction"></a> Un <xref:System.Windows.Controls.ControlTemplate> spécifie la structure visuelle et le comportement visuel d'un contrôle.  Vous pouvez personnaliser l'apparence d'un contrôle en lui donnant un nouveau <xref:System.Windows.Controls.ControlTemplate>.  Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate>, vous remplacez l'apparence d'un contrôle existant sans modifier sa fonctionnalité.  Par exemple, vous pouvez donner aux boutons de votre application une forme arrondie à la place de la forme carrée par défaut, mais le bouton déclenchera toujours l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
 Cette rubrique décrit les différents composants d'un <xref:System.Windows.Controls.ControlTemplate>, présente la création d'un <xref:System.Windows.Controls.ControlTemplate> simple pour un <xref:System.Windows.Controls.Button> et explique comment interpréter le contrat de contrôle d'un contrôle de sorte que vous puissiez personnaliser son apparence.  Étant donné que vous créez un <xref:System.Windows.Controls.ControlTemplate> en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez modifier l'apparence d'un contrôle sans écrire de code.  Vous pouvez également utiliser un concepteur, tel que Microsoft Expression Blend, pour créer des modèles de contrôle personnalisé.  Cette rubrique affiche des exemples dans le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui personnalise l'apparence d'un <xref:System.Windows.Controls.Button> et répertorie l'exemple complet à la fin de la rubrique.  Pour plus d'informations sur l'utilisation d'Expression Blend, consultez [Définition d'un style pour un contrôle prenant en charge les modèles](http://go.microsoft.com/fwlink/?LinkId=161153).  
  
 Les illustrations suivantes montrent un <xref:System.Windows.Controls.Button> qui utilise le <xref:System.Windows.Controls.ControlTemplate> créé dans cette rubrique.  
  
 ![Bouton avec un modèle de contrôle personnalisé.](../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP\_ButtonNormal")  
Bouton qui utilise un modèle de contrôle personnalisé  
  
 ![Bouton avec une bordure rouge.](../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP\_ButtonMouseOver")  
Bouton qui utilise un modèle de contrôle personnalisé et sur lequel le pointeur de la souris se trouve  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="prerequisites"></a>   
## Composants requis  
 Cette rubrique suppose que vous comprenez comment créer et utiliser des contrôles et des styles comme discuté dans [Contrôles](../../../../docs/framework/wpf/controls/index.md).  Les concepts présentés dans cette rubrique s'appliquent aux éléments qui héritent de la classe <xref:System.Windows.Controls.Control>, excepté pour <xref:System.Windows.Controls.UserControl>.  Vous ne pouvez pas appliquer un <xref:System.Windows.Controls.ControlTemplate> à un <xref:System.Windows.Controls.UserControl>.  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## Quand créer un ControlTemplate  
 Les contrôles ont de nombreuses propriétés, telles que <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A> et <xref:System.Windows.Controls.Control.FontFamily%2A>, que vous pouvez définir pour spécifier différents aspects de l'apparence du contrôle ; cependant, les modifications que vous pouvez apporter en définissant ces propriétés sont limitées.  Par exemple, vous pouvez affecter la valeur blue à la propriété <xref:System.Windows.Controls.Control.Foreground%2A> et la valeur italic à la propriété <xref:System.Windows.Controls.Control.FontStyle%2A> d'un <xref:System.Windows.Controls.CheckBox>.  
  
 S'il n'était pas possible de créer un <xref:System.Windows.Controls.ControlTemplate> pour les contrôles, tous les contrôles de toutes les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] auraient la même apparence générale, ce qui limiterait les possibilités de créer une application avec une apparence personnalisée.  Par défaut, chaque <xref:System.Windows.Controls.CheckBox> présente des caractéristiques similaires.  Par exemple, le contenu du <xref:System.Windows.Controls.CheckBox> se situe toujours à droite de l'indicateur de sélection et la coche est toujours utilisée pour indiquer que la <xref:System.Windows.Controls.CheckBox> est activé.  
  
 Vous créez un <xref:System.Windows.Controls.ControlTemplate> lorsque vous souhaitez personnaliser l'apparence du contrôle au\-delà de ce qui est défini par les autres propriétés du contrôle.  Dans l'exemple du <xref:System.Windows.Controls.CheckBox>, supposons que vous vouliez que le contenu de la case à cocher apparaisse au\-dessus de l'indicateur de sélection et qu'un X indique que le <xref:System.Windows.Controls.CheckBox> est activé.  Vous spécifiez ces modifications dans le <xref:System.Windows.Controls.ControlTemplate> du <xref:System.Windows.Controls.CheckBox>.  
  
 L'illustration suivante affiche une <xref:System.Windows.Controls.CheckBox> qui utilise un <xref:System.Windows.Controls.ControlTemplate> par défaut.  
  
 ![Case à cocher avec le modèle de contrôle par défaut.](../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP\_CheckBoxDefault")  
Case à cocher qui utilise le modèle de contrôle par défaut  
  
 L'illustration suivante montre une <xref:System.Windows.Controls.CheckBox> qui utilise un <xref:System.Windows.Controls.ControlTemplate> personnalisé pour placer le contenu de la <xref:System.Windows.Controls.CheckBox> au\-dessus de l'indicateur de sélection et affiche un X lorsque la <xref:System.Windows.Controls.CheckBox> est sélectionnée.  
  
 ![Case à cocher avec un modèle de contrôle personnalisé.](../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP\_CheckBoxCustom")  
Case à cocher qui utilise un modèle de contrôle personnalisé  
  
 Le <xref:System.Windows.Controls.ControlTemplate> de la <xref:System.Windows.Controls.CheckBox> de cet exemple est relativement complexe ; cette rubrique utilise donc un exemple plus simple pour la création d'un <xref:System.Windows.Controls.ControlTemplate> d'un <xref:System.Windows.Controls.Button>.  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## Modification de la structure visuelle d'un contrôle  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], un contrôle est souvent un composite d'objets <xref:System.Windows.FrameworkElement>.  Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate>, vous combinez des objets <xref:System.Windows.FrameworkElement> pour générer un seul contrôle.  Un <xref:System.Windows.Controls.ControlTemplate> doit avoir un seul <xref:System.Windows.FrameworkElement> en tant qu'élément racine.  Ce dernier contient généralement d'autres objets <xref:System.Windows.FrameworkElement>.  Cette combinaison d'objets constitue la structure visuelle du contrôle.  
  
 L'exemple suivant crée un <xref:System.Windows.Controls.ControlTemplate> personnalisé pour le <xref:System.Windows.Controls.Button>.  Le <xref:System.Windows.Controls.ControlTemplate> crée la structure visuelle du <xref:System.Windows.Controls.Button>.  Cet exemple ne modifie pas l'apparence du bouton lorsque vous pointez sur lui ou cliquez dessus.  La modification de l'apparence du bouton lorsque celui\-ci est dans un autre état est décrite plus loin dans cette rubrique.  
  
 Dans cet exemple, la structure visuelle se compose des parties suivantes :  
  
-   une <xref:System.Windows.Controls.Border> nommée `RootElement` qui sert de <xref:System.Windows.FrameworkElement> racine du modèle ;  
  
-   une <xref:System.Windows.Controls.Grid> qui est un enfant de `RootElement` ;  
  
-   un <xref:System.Windows.Controls.ContentPresenter> qui affiche le contenu du bouton.  Le <xref:System.Windows.Controls.ContentPresenter> permet l'affichage de tout type d'objet.  
  
 [!code-xml[VSMButtonTemplate#BasicTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### Conservation de la fonctionnalité des propriétés d'un contrôle en utilisant TemplateBinding  
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate>, vous trouverez peut\-être toujours pratique d'utiliser les propriétés publiques pour modifier l'apparence du contrôle.  L'extension de balisage [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) lie une propriété d'un élément figurant dans le <xref:System.Windows.Controls.ControlTemplate> à une propriété publique définie par le contrôle.  Lorsque vous utilisez [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md), vous permettez aux propriétés sur le contrôle d'agir en tant que paramètres au modèle.  Autrement dit, lorsqu'une propriété sur un contrôle est définie, cette valeur est passée à l'élément possédant le [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md).  
  
 L'exemple précédent reproduit la partie de l'exemple précédent qui utilise l'extension de balisage [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) pour lier les propriétés des éléments du <xref:System.Windows.Controls.ControlTemplate> aux propriétés publiques définies par le bouton.  
  
 [!code-xml[VSMButtonTemplate#TemplateBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 Dans cet exemple, la <xref:System.Windows.Controls.Grid> a son modèle de propriété <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=fullName> qui est lié à <xref:System.Windows.Controls.Control.Background%2A?displayProperty=fullName>.  Étant donné que la propriété <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=fullName> est liée par modèle, vous pouvez créer plusieurs boutons qui utilisent le même <xref:System.Windows.Controls.ControlTemplate> et affecter des valeurs différentes à <xref:System.Windows.Controls.Control.Background%2A?displayProperty=fullName> pour chaque bouton.  Si la propriété <xref:System.Windows.Controls.Control.Background%2A?displayProperty=fullName> n'était pas liée par modèle à la propriété d'un élément dans le <xref:System.Windows.Controls.ControlTemplate>, la définition de la propriété <xref:System.Windows.Controls.Control.Background%2A?displayProperty=fullName> d'un bouton n'aurait aucune incidence sur l'apparence du bouton.  
  
 Notez que les noms des deux propriétés n'ont pas besoin d'être identiques.  Dans l'exemple précédent, la propriété <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=fullName> du <xref:System.Windows.Controls.Button> est liée par modèle à la propriété <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=fullName> du <xref:System.Windows.Controls.ContentPresenter>.  Le contenu du bouton est ainsi positionné horizontalement.  <xref:System.Windows.Controls.ContentPresenter> n'a pas de propriété nommée `HorizontalContentAlignment`, mais <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=fullName> peut être lié à <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=fullName>.  Lorsque vous liez par modèle une propriété, assurez\-vous que les propriétés source et cible sont du même type.  
  
 La classe <xref:System.Windows.Controls.Control> définit plusieurs propriétés qui doivent être utilisées par le modèle de contrôle pour avoir un effet sur le contrôle lorsqu'elles sont définies.  La façon dont <xref:System.Windows.Controls.ControlTemplate> utilise la propriété dépend de la propriété.  Le <xref:System.Windows.Controls.ControlTemplate> doit utiliser la propriété de l'une des façons suivantes :  
  
-   un élément du modèle <xref:System.Windows.Controls.ControlTemplate> crée une liaison avec la propriété ;  
  
-   un élément du <xref:System.Windows.Controls.ControlTemplate> hérite de la propriété d'un <xref:System.Windows.FrameworkElement> parent.  
  
 Le tableau suivant répertorie les propriétés visuelles héritées par un contrôle de la classe <xref:System.Windows.Controls.Control>.  Il indique également si le modèle de contrôle par défaut d'un contrôle utilise la valeur de propriété héritée ou s'il doit être lié par modèle.  
  
|Property|Méthode d'utilisation|  
|--------------|---------------------------|  
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
  
 Le tableau ne répertorie que les propriétés visuelles héritées de la classe <xref:System.Windows.Controls.Control>.  En dehors des propriétés répertoriées dans le tableau, un contrôle peut également hériter des propriétés <xref:System.Windows.FrameworkElement.DataContext%2A>, <xref:System.Windows.FrameworkElement.Language%2A> et <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> de l'élément d'infrastructure parent.  
  
 En outre, si le <xref:System.Windows.Controls.ContentPresenter> est dans le <xref:System.Windows.Controls.ControlTemplate> d'un <xref:System.Windows.Controls.ContentControl>, le <xref:System.Windows.Controls.ContentPresenter> se liera automatiquement aux propriétés <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> et <xref:System.Windows.Controls.ContentControl.Content%2A>.  De même, un <xref:System.Windows.Controls.ItemsPresenter> qui est dans le <xref:System.Windows.Controls.ControlTemplate> d'un <xref:System.Windows.Controls.ItemsControl> se liera automatiquement aux propriétés <xref:System.Windows.Controls.ItemsControl.Items%2A> et <xref:System.Windows.Controls.ItemsPresenter>.  
  
 L'exemple suivant crée deux boutons qui utilisent le <xref:System.Windows.Controls.ControlTemplate> défini dans l'exemple précédent.  Cet exemple définit les propriétés <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A> et <xref:System.Windows.Controls.Control.FontSize%2A> de chaque bouton.  La définition de la propriété <xref:System.Windows.Controls.Control.Background%2A> a une incidence, car elle est liée par modèle dans le <xref:System.Windows.Controls.ControlTemplate>.  Même si les propriétés <xref:System.Windows.Controls.Control.Foreground%2A> et <xref:System.Windows.Controls.Control.FontSize%2A> ne sont pas liées par modèle, leur définition a une incidence, car leurs valeurs sont héritées.  
  
 [!code-xml[VSMButtonTemplate#ButtonDeclaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 L'exemple précédent produit une sortie similaire à celle de l'illustration suivante.  
  
 ![Deux boutons, un bleu et un pourpre.](../../../../docs/framework/wpf/controls/media/ndp-buttontwo.png "NDP\_ButtonTwo")  
Deux boutons avec des couleurs d'arrière\-plan différentes  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## Modification de l'apparence d'un contrôle en fonction de son état  
 La différence entre un bouton avec son apparence par défaut et le bouton de l'exemple précédent est que le bouton par défaut change légèrement selon son état.  Par exemple, l'apparence du bouton par défaut change lorsque l'utilisateur clique dessus ou pointe sur lui.  Bien que le <xref:System.Windows.Controls.ControlTemplate> ne modifie pas la fonctionnalité d'un contrôle, il en modifie le comportement visuel.  Un comportement visuel décrit l'apparence du contrôle lorsque ce dernier est dans un état particulier.  Pour comprendre la différence entre la fonctionnalité et le comportement visuel d'un contrôle, considérez l'exemple du bouton.  La fonctionnalité du bouton consiste à déclencher l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> lorsque l'utilisateur clique dessus, alors que son comportement visuel consiste à changer d'apparence lorsque l'utilisateur pointe sur lui ou clique dessus.  
  
 Vous utilisez des objets <xref:System.Windows.VisualState> pour spécifier l'apparence d'un contrôle lorsque ce dernier est dans un état particulier.  Un objet <xref:System.Windows.VisualState> contient un <xref:System.Windows.Media.Animation.Storyboard> qui modifie l'apparence des éléments qui sont dans le <xref:System.Windows.Controls.ControlTemplate>.  Vous n'avez aucun code à écrire pour cela, car la logique du contrôle modifie l'état à l'aide du <xref:System.Windows.VisualStateManager>.  Lorsque le contrôle passe à l'état qui est spécifié par la propriété <xref:System.Windows.VisualState.Name%2A?displayProperty=fullName>, le <xref:System.Windows.Media.Animation.Storyboard> commence.  Lorsque le contrôle sort de cet état, le <xref:System.Windows.Media.Animation.Storyboard> cesse.  
  
 L'exemple suivant présente le <xref:System.Windows.VisualState> qui modifie l'apparence d'un <xref:System.Windows.Controls.Button> lorsque l'utilisateur pointe sur lui.  Le <xref:System.Windows.Media.Animation.Storyboard> modifie la couleur de la bordure du bouton en modifiant la couleur du `BorderBrush`.  Si vous vous reportez à l'exemple <xref:System.Windows.Controls.ControlTemplate> du début de cette rubrique, vous vous souviendrez que `BorderBrush` est le nom du <xref:System.Windows.Media.SolidColorBrush> affecté au <xref:System.Windows.Controls.Border.Background%2A> du <xref:System.Windows.Controls.Border>.  
  
 [!code-xml[VSMButtonTemplate#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 Le contrôle est chargé de définir les états dans le cadre de son contrat de contrôle, lequel est décrit en détail dans [Personnalisation des autres contrôles grâce à une bonne compréhension du contrat de contrôle](#customizing_other_controls_by_understanding_the_control_contract), plus loin dans cette rubrique.  Le tableau suivant répertorie les états spécifiés pour le <xref:System.Windows.Controls.Button>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|---------------------|--------------------------|-----------------|  
|Normal|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de souris est positionné sur le contrôle.|  
|Pressed|CommonStates|Le contrôle est enfoncé.|  
|Disabled|CommonStates|Le contrôle est désactivé.|  
|Focused|FocusStates|Le contrôle a le focus.|  
|Unfocused|FocusStates|Le contrôle n'a pas le focus.|  
  
 Le <xref:System.Windows.Controls.Button> définit deux groupes d'état : le groupe `CommonStates` contient les états `Normal`, `MouseOver`, `Pressed` et `Disabled`.  Le groupe `FocusStates` contient les états `Focused` et `Unfocused`.  Les états d'un même groupe d'état s'excluent mutuellement.  Le contrôle est toujours exactement dans un état par groupe.  Par exemple, un <xref:System.Windows.Controls.Button> peut avoir le focus même lorsque le pointeur de la souris n'est pas placé dessus, de sorte qu'un <xref:System.Windows.Controls.Button> à l'état `Focused` peut être à l'état `MouseOver`, `Pressed` ou `Normal`.  
  
 Vous ajoutez des objets <xref:System.Windows.VisualState> à des objets <xref:System.Windows.VisualStateGroup>.  Vous ajoutez des objets <xref:System.Windows.VisualStateGroup> à la propriété jointe <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=fullName>.  L'exemple suivant définit les objets <xref:System.Windows.VisualState> pour les états `Normal`, `MouseOver` et `Pressed`, lesquels figurent tous dans le groupe `CommonStates`.  Le <xref:System.Windows.VisualState.Name%2A> de chaque <xref:System.Windows.VisualState> correspond au nom dans le tableau précédent.  L'état `Disabled` et les états du groupe dans les `FocusStates` sont omis pour que l'exemple reste concis, mais ils figurent dans l'exemple complet fourni à la fin de la rubrique.  
  
> [!NOTE]
>  Veillez à définir la propriété jointe <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=fullName> sur le <xref:System.Windows.FrameworkElement> racine de <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xml[VSMButtonTemplate#VisualStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 L'exemple précédent produit une sortie similaire à celle des illustrations suivantes.  
  
 ![Bouton avec un modèle de contrôle personnalisé.](../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP\_ButtonNormal")  
Bouton qui utilise un modèle de contrôle personnalisé dans l'état normal  
  
 ![Bouton avec une bordure rouge.](../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP\_ButtonMouseOver")  
Bouton qui utilise un modèle de contrôle personnalisé dans l'état de pointage avec la souris  
  
 ![La bordure est transparente sur un bouton enfoncé.](../../../../docs/framework/wpf/controls/media/ndp-buttonpressed.png "NDP\_ButtonPressed")  
Bouton qui utilise un modèle de contrôle personnalisé dans l'état enfoncé  
  
 Pour rechercher les états visuels pour les contrôles compris avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Styles et modèles Control](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## Spécification du comportement d'un contrôle lors des transitions entre états  
 Dans l'exemple précédent, l'apparence du bouton change également lorsque l'utilisateur clique dessus, mais à moins que le bouton ne soit enfoncé pendant une seconde complète, aucun effet n'est visible pour l'utilisateur.  Par défaut, une seconde est nécessaire au déclenchement de l'animation.  Comme les utilisateurs mettent généralement moins de temps pour enfoncer un bouton et le relâcher, la rétroaction visuelle ne sera pas efficace si vous laissez le <xref:System.Windows.Controls.ControlTemplate> dans son état par défaut.  
  
 Vous pouvez spécifier la durée nécessaire à une animation pour effectuer une transition douce entre les états d'un contrôle en ajoutant des objets <xref:System.Windows.VisualTransition> au <xref:System.Windows.Controls.ControlTemplate>.  Lorsque vous créez une <xref:System.Windows.VisualTransition>, vous spécifiez un ou plusieurs des éléments suivants :  
  
-   le temps nécessaire à une transition entre des états ;  
  
-   les modifications supplémentaires dans l'apparence du contrôle qui ont lieu lors de la transition ;  
  
-   les états auxquels la <xref:System.Windows.VisualTransition> est appliquée.  
  
### Spécification de la durée d'une transition  
 Vous pouvez spécifier la durée d'une transition en définissant la propriété <xref:System.Windows.VisualTransition.GeneratedDuration%2A>.  L'exemple précédent possède un <xref:System.Windows.VisualState> qui spécifie que la bordure du bouton devient transparente lorsque l'utilisateur appuie sur le bouton, mais l'animation met trop de temps pour se déclencher lorsque l'utilisateur appuie sur le bouton et le relâche immédiatement.  Vous pouvez utiliser une <xref:System.Windows.VisualTransition> pour spécifier la durée nécessaire au contrôle pour que son état passe à Pressed.  L'exemple suivant spécifie que le contrôle nécessite un centième de seconde pour passer à l'état Pressed.  
  
 [!code-xml[VSMButtonTemplate#PressedTransition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### Spécification de modifications de l'apparence du contrôle pendant une transition  
 La <xref:System.Windows.VisualTransition> contient un <xref:System.Windows.Media.Animation.Storyboard> qui commence lorsque le contrôle effectue des transitions entre états.  Par exemple, vous pouvez spécifier qu'une animation particulière a lieu lorsque le contrôle effectue des transitions de l'état `MouseOver` vers l'état `Normal`.  L'exemple suivant crée une <xref:System.Windows.VisualTransition> qui spécifie que lorsque l'utilisateur éloigne le pointeur de la souris du bouton, la bordure de ce dernier passe du bleu au jaune et enfin au noir en 1,5 secondes.  
  
 [!code-xml[VSMButtonTemplate#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### Spécification du moment où une VisualTransition est appliquée  
 Une <xref:System.Windows.VisualTransition> peut être restreinte de manière à ne s'appliquer qu'à certains états, ou elle peut être appliquée chaque fois que le contrôle effectue des transitions entre états.  Dans l'exemple précédent, la <xref:System.Windows.VisualTransition> est appliquée lorsque le contrôle passe de l'état `MouseOver` à l'état `Normal` ; dans l'exemple antérieur, la <xref:System.Windows.VisualTransition> est appliquée lorsque le contrôle passe à l'état `Pressed`.  Pour restreindre le moment où une <xref:System.Windows.VisualTransition> est appliquée, il convient de définir les propriétés <xref:System.Windows.VisualTransition.To%2A> et <xref:System.Windows.VisualTransition.From%2A>.  Le tableau suivant décrit les niveaux de restriction, du plus restrictif au moins restrictif.  
  
|Type de restriction|Valeur de From|Valeur de To|  
|-------------------------|--------------------|------------------|  
|D'un état spécifié vers un autre état spécifié|Nom d'un <xref:System.Windows.VisualState>.|Nom d'un <xref:System.Windows.VisualState>.|  
|De n'importe quel état vers un état spécifié|Non définie|Nom d'un <xref:System.Windows.VisualState>.|  
|D'un état spécifié à n'importe quel état|Nom d'un <xref:System.Windows.VisualState>.|Non définie|  
|De n'importe quel état vers tout autre état|Non définie|Non définie|  
  
 Vous pouvez avoir plusieurs objets <xref:System.Windows.VisualTransition> dans un <xref:System.Windows.VisualStateGroup> qui font référence au même état, mais ces objets seront utilisés dans l'ordre spécifié dans le tableau précédent.  L'exemple suivant contient deux objets <xref:System.Windows.VisualTransition>.  Lorsque le contrôle effectue une transition de l'état `Pressed` vers l'état `MouseOver`, c'est le <xref:System.Windows.VisualTransition> dans lequel les propriétés <xref:System.Windows.VisualTransition.From%2A> et <xref:System.Windows.VisualTransition.To%2A> sont définies qui est utilisé.  Lorsque le contrôle effectue une transition d'un état différent de `Pressed` vers l'état `MouseOver`, c'est l'autre état qui est utilisé.  
  
 [!code-xml[VSMButtonTemplate#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 Le <xref:System.Windows.VisualStateGroup> comporte une propriété <xref:System.Windows.VisualStateGroup.Transitions%2A> qui contient les objets <xref:System.Windows.VisualTransition> qui s'appliquent aux objets <xref:System.Windows.VisualState> du <xref:System.Windows.VisualStateGroup>.  En tant qu'auteur du <xref:System.Windows.Controls.ControlTemplate>, vous êtes libre d'inclure toute <xref:System.Windows.VisualTransition> de votre choix.  Toutefois, si les propriétés <xref:System.Windows.VisualTransition.To%2A> et <xref:System.Windows.VisualTransition.From%2A> sont définies par des noms d'états qui ne figurent pas dans le <xref:System.Windows.VisualStateGroup>, le <xref:System.Windows.VisualTransition> est ignoré.  
  
 L'exemple suivant présente le <xref:System.Windows.VisualStateGroup> de `CommonStates`.  Cet exemple définit un <xref:System.Windows.VisualTransition> pour chacune des transitions suivantes du bouton.  
  
-   Vers l'état `Pressed`.  
  
-   Vers l'état `MouseOver`.  
  
-   De l'état `Pressed` à l'état `MouseOver`.  
  
-   De l'état `MouseOver` à l'état `Normal`.  
  
 [!code-xml[VSMButtonTemplate#VisualTransitions](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## Personnalisation des autres contrôles grâce à une bonne compréhension du contrat de contrôle  
 Un contrôle qui utilise un <xref:System.Windows.Controls.ControlTemplate> pour spécifier sa structure visuelle \(en utilisant des objets <xref:System.Windows.FrameworkElement>\) et son comportement visuel \(en utilisant des objets <xref:System.Windows.VisualState>\) utilise le modèle de contrôle des composants.  Bon nombre des contrôles inclus avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 utilisent ce modèle.  Les composants que doit connaître l'auteur d'un <xref:System.Windows.Controls.ControlTemplate> sont communiqués via le contrat de contrôle.  Lorsque vous connaissez les composants d'un contrat de contrôle, vous pouvez personnaliser l'apparence de tout contrôle qui utilise le modèle de contrôle des composants.  
  
 Un contrat de contrôle comporte trois éléments :  
  
-   les éléments visuels utilisés par la logique du contrôle ;  
  
-   les états du contrôle et le groupe auquel appartient chaque état ;  
  
-   les propriétés publiques qui affectent visuellement le contrôle.  
  
### Éléments visuels du contrat de contrôle  
 La logique d'un contrôle interagit parfois avec un <xref:System.Windows.FrameworkElement> qui se trouve dans le <xref:System.Windows.Controls.ControlTemplate>.  Par exemple, le contrôle peut gérer un événement de l'un de ses éléments.  Lorsqu'un contrôle s'attend à trouver un <xref:System.Windows.FrameworkElement> particulier dans le <xref:System.Windows.Controls.ControlTemplate>, il doit communiquer cette information à l'auteur du <xref:System.Windows.Controls.ControlTemplate>.  Le contrôle utilise le <xref:System.Windows.TemplatePartAttribute> pour communiquer le type d'élément attendu et le nom que doit porter cet élément.  Le <xref:System.Windows.Controls.Button> n'a pas de composants <xref:System.Windows.FrameworkElement> dans son contrat de contrôle, à la différence d'autres contrôles tels que <xref:System.Windows.Controls.ComboBox>.  
  
 L'exemple suivant présente les objets <xref:System.Windows.TemplatePartAttribute> qui sont spécifiés dans la classe <xref:System.Windows.Controls.ComboBox>.  La logique de <xref:System.Windows.Controls.ComboBox> s'attend à trouver une <xref:System.Windows.Controls.TextBox> nommée `PART_EditableTextBox` et un <xref:System.Windows.Controls.Primitives.Popup> nommé `PART_Popup` dans son <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 L'exemple suivant présente un <xref:System.Windows.Controls.ControlTemplate> simplifié pour la <xref:System.Windows.Controls.ComboBox> qui inclut les éléments qui sont spécifiés par les objets <xref:System.Windows.TemplatePartAttribute> dans la classe <xref:System.Windows.Controls.ComboBox>.  
  
 [!code-xml[VSMButtonTemplate#ComboBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### États du contrat de contrôle  
 Les états d'un contrôle font également partie du contrat de contrôle.  L'exemple de création d'un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.Button> indique comment spécifier l'apparence d'un <xref:System.Windows.Controls.Button> en fonction de ses états.  Vous créez un <xref:System.Windows.VisualState> pour chaque état spécifié et placez tous les objets <xref:System.Windows.VisualState> qui partagent un <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> dans un <xref:System.Windows.VisualStateGroup>, comme décrit dans [Modification de l'apparence d'un contrôle en fonction de son état](#changing_the_appearance_of_a_control_depending_on_its_state) plus haut dans cette rubrique.  Les contrôles tiers doivent spécifier des rapports à l'aide de <xref:System.Windows.TemplateVisualStateAttribute>, qui permet aux outils concepteurs, tels qu'Expression Blend, pour exposer les états du contrôle pour créer des modèles de contrôle.  
  
 Pour rechercher le contrat de contrôle pour les contrôles compris avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Styles et modèles Control](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
### Propriétés du contrat de contrôle  
 Les propriétés publiques qui affectent visuellement le contrôle sont également incluses dans le contrat de contrôle.  Vous pouvez définir ces propriétés pour modifier l'apparence du contrôle sans créer de nouveau <xref:System.Windows.Controls.ControlTemplate>.  Vous pouvez également utiliser l'extension de balisage [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) pour lier les propriétés d'éléments qui figurent dans le <xref:System.Windows.Controls.ControlTemplate> à des propriétés publiques définies par le <xref:System.Windows.Controls.Button>.  
  
 L'exemple suivant montre le contrat de contrôle du bouton.  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 Lors de la création d'un <xref:System.Windows.Controls.ControlTemplate>, il est souvent plus facile de commencer avec un <xref:System.Windows.Controls.ControlTemplate> existant et de lui apporter des modifications.  Vous pouvez effectuer l'une des opérations suivantes pour modifier un <xref:System.Windows.Controls.ControlTemplate> existant :  
  
-   Utiliser un concepteur, tel que Microsoft Expression Blend, lequel fournit une interface graphique utilisateur pour créer des modèles de contrôle.  Pour plus d'informations, consultez [Définition d'un style pour un contrôle prenant en charge les modèles](http://go.microsoft.com/fwlink/?LinkId=161153).  
  
-   Obtenir le <xref:System.Windows.Controls.ControlTemplate> par défaut et le modifier.  Pour rechercher les modèles de contrôle par défaut compris avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Thèmes WPF par défaut \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
<a name="complete_example"></a>   
## Exemple complet  
 L'exemple suivant affiche le <xref:System.Windows.Controls.Button><xref:System.Windows.Controls.ControlTemplate> complet discuté dans cette rubrique.  
  
 [!code-xml[VSMButtonTemplate#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## Voir aussi  
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)