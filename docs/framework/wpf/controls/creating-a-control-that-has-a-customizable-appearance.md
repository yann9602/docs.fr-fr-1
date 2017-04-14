---
title: "Cr&#233;ation d&#39;un contr&#244;le avec une apparence personnalisable | Microsoft Docs"
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
  - "contrôles (WPF), personnaliser"
  - "contrôles (WPF), définir la structure visuelle et le comportement visuel de"
  - "ControlTemplate (WPF), personnaliser l'apparence"
  - "personnaliser l'apparence (WPF), ControlTemplate"
  - "gérer les états des contrôles (WPF), VisualStateManager"
  - "VisualStateManager (WPF), meilleure pratique"
  - "VisualStateManager (WPF), gérer l'état d'un contrôle"
ms.assetid: 9e356d3d-a3d0-4b01-a25f-2d43e4d53fe5
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Cr&#233;ation d&#39;un contr&#244;le avec une apparence personnalisable
<a name="introduction"></a> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vous permet de créer un contrôle dont l'apparence peut être personnalisée.  Par exemple, vous pouvez modifier l'apparence d'une <xref:System.Windows.Controls.CheckBox> au\-delà de ce que permet la définition des propriétés en créant un <xref:System.Windows.Controls.ControlTemplate>.  L'illustration suivante montre une <xref:System.Windows.Controls.CheckBox> qui utilise un <xref:System.Windows.Controls.ControlTemplate> par défaut et une <xref:System.Windows.Controls.CheckBox> qui utilise un <xref:System.Windows.Controls.ControlTemplate>personnalisé.  
  
 ![Case à cocher avec le modèle de contrôle par défaut.](../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP\_CheckBoxDefault")  
Case à cocher qui utilise le modèle de contrôle par défaut  
  
 ![Case à cocher avec un modèle de contrôle personnalisé.](../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP\_CheckBoxCustom")  
Case à cocher qui utilise un modèle de contrôle personnalisé  
  
 Si vous suivez le modèle de composants et d'états lorsque vous créez un contrôle, l'apparence de ce dernier est personnalisable.  Les outils du concepteur, tels que Microsoft Expression Blend, prennent en charge le modèle de composants et d'états, de sorte que lorsque vous suivez ce modèle votre contrôle est personnalisable dans ces types d'applications.  Cette rubrique décrit le modèle de composants et d'états et explique comment le suivre lorsque vous créez votre propre contrôle.  Elle utilise un exemple de contrôle personnalisé, `NumericUpDown`, pour illustrer la philosophie de ce modèle.  Le contrôle `NumericUpDown` affiche une valeur numérique qu'un utilisateur peut augmenter ou diminuer en cliquant sur les boutons du contrôle.  L'illustration suivante montre les contrôles `NumericUpDown` qui sont discutés dans cette rubrique.  
  
 ![Contrôle personnalisé NumericUpDown.](../../../../docs/framework/wpf/controls/media/ndp-numericupdown.png "NDP\_NumericUPDown")  
Contrôle NumericUpDown personnalisé  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Composants requis](#prerequisites)  
  
-   [Modèle de composants et d'états](#parts_and_states_model)  
  
-   [Définition de la structure visuelle et du comportement visuel d'un contrôle dans un ControlTemplate](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)  
  
-   [Utilisation de composants du ControlTemplate dans le code](#using_parts_of_the_controltemplate_in_code)  
  
-   [Fourniture du contrat de contrôle](#providing_the_control_contract)  
  
-   [Exemple complet](#complete_example)  
  
<a name="prerequisites"></a>   
## Composants requis  
 Cette rubrique suppose que vous savez comment créer un <xref:System.Windows.Controls.ControlTemplate> pour un contrôle existant, connaissez les éléments d'un contrat de contrôle et comprenez les concepts présentés dans [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
> [!NOTE]
>  Pour créer un contrôle dont l'apparence peut être personnalisée, vous devez créer un contrôle qui hérite de la classe <xref:System.Windows.Controls.Control> ou de l'une de ses sous\-classes autres que <xref:System.Windows.Controls.UserControl>.  Un contrôle qui hérite de <xref:System.Windows.Controls.UserControl> est un contrôle qui peut être créé rapidement. Cependant, il n'utilise pas de <xref:System.Windows.Controls.ControlTemplate> et vous ne pouvez pas personnaliser son apparence.  
  
<a name="parts_and_states_model"></a>   
## Modèle de composants et d'états  
 Le modèle de composants et d'états spécifie comment définir la structure visuelle et le comportement visuel d'un contrôle.  Pour suivre le modèle de composants et d'états, vous devez procéder comme suit :  
  
-   Définissez la structure visuelle et le comportement visuel dans le <xref:System.Windows.Controls.ControlTemplate> d'un contrôle.  
  
-   Suivez certaines meilleures pratiques lorsque la logique du contrôle interagit avec des composants du modèle de contrôle.  
  
-   Fournissez un contrat de contrôle pour spécifier les éléments à inclure dans le <xref:System.Windows.Controls.ControlTemplate>.  
  
 Lorsque vous définissez la structure visuelle et le comportement visuel dans le <xref:System.Windows.Controls.ControlTemplate> d'un contrôle, les auteurs d'application peuvent modifier la structure visuelle et le comportement visuel de votre contrôle en créant un <xref:System.Windows.Controls.ControlTemplate> au lieu d'écrire du code.  Vous devez fournir un contrat de contrôle qui indique aux auteurs d'application les objets et les états <xref:System.Windows.FrameworkElement> qui doivent être définis dans le <xref:System.Windows.Controls.ControlTemplate>.  Vous devez appliquer certaines meilleures pratiques lorsque vous interagissez avec les composants du <xref:System.Windows.Controls.ControlTemplate> afin que votre contrôle gère correctement un <xref:System.Windows.Controls.ControlTemplate> incomplet.  Si vous appliquez ces trois principes, les auteurs d'application seront en mesure de créer un <xref:System.Windows.Controls.ControlTemplate> pour votre contrôle tout aussi facilement qu'ils le font pour les contrôles fournis avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  La section suivante explique en détail chacune de ces recommandations.  
  
<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>   
## Définition de la structure visuelle et du comportement visuel d'un contrôle dans un ControlTemplate  
 Lorsque vous créez votre contrôle personnalisé à l'aide du modèle de composants et d'états, vous définissez la structure visuelle et le comportement visuel du contrôle dans son <xref:System.Windows.Controls.ControlTemplate> plutôt que dans sa logique.  La structure visuelle d'un contrôle est le composite d'objets <xref:System.Windows.FrameworkElement> qui constituent le contrôle.  Le comportement visuel désigne l'apparence du contrôle dans un état donné.  Pour plus d'informations sur la création d'un <xref:System.Windows.Controls.ControlTemplate> qui spécifie la structure visuelle et le comportement visuel d'un contrôle, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
 Dans l'exemple du contrôle `NumericUpDown`, la structure visuelle inclut deux contrôles <xref:System.Windows.Controls.Primitives.RepeatButton> et un <xref:System.Windows.Controls.TextBlock>.  Si vous ajoutez ces contrôles au code du contrôle `NumericUpDown`, dans son constructeur par exemple, les positions de ces contrôles ne peuvent pas être modifiées.  Au lieu de définir la structure visuelle et le comportement visuel du contrôle dans son code, vous devez les définir dans le <xref:System.Windows.Controls.ControlTemplate>.  Un développeur d'applications peut alors personnaliser la position des boutons et du <xref:System.Windows.Controls.TextBlock>, et spécifier le comportement qui se produit lorsque `Value` est négative parce que le <xref:System.Windows.Controls.ControlTemplate> peut être remplacé.  
  
 L'exemple suivant montre la structure visuelle du contrôle `NumericUpDown`, qui inclut un <xref:System.Windows.Controls.Primitives.RepeatButton> pour augmenter `Value`, un <xref:System.Windows.Controls.Primitives.RepeatButton> pour diminuer `Value` et un <xref:System.Windows.Controls.TextBlock> pour afficher `Value`.  
  
 [!code-xml[VSMCustomControl#VisualStructure](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]  
  
 Le fait que la valeur apparaisse en rouge lorsqu'elle est négative constitue un comportement visuel du contrôle `NumericUpDown`.  Si vous modifiez le <xref:System.Windows.Controls.TextBlock.Foreground%2A> du <xref:System.Windows.Controls.TextBlock> dans le code lorsque la `Value` est négative, le `NumericUpDown` affichera toujours une valeur négative rouge.  Vous spécifiez le comportement visuel du contrôle dans le <xref:System.Windows.Controls.ControlTemplate> en ajoutant des objets <xref:System.Windows.VisualState> au <xref:System.Windows.Controls.ControlTemplate>.  L'exemple suivant montre les objets <xref:System.Windows.VisualState> pour les états `Positive` et `Negative`.  `Positive` et `Negative` s'excluent mutuellement \(le contrôle est toujours exactement dans l'un des deux\), ainsi l'exemple place les objets <xref:System.Windows.VisualState> dans un seul <xref:System.Windows.VisualStateGroup>.  Lorsque le contrôle bascule dans l'état `Negative`, le <xref:System.Windows.Controls.TextBlock.Foreground%2A> du <xref:System.Windows.Controls.TextBlock> devient rouge.  Lorsque le contrôle est dans l'état `Positive`, le <xref:System.Windows.Controls.TextBlock.Foreground%2A> retrouve sa valeur d'origine.  La définition des objets <xref:System.Windows.VisualState> dans un <xref:System.Windows.Controls.ControlTemplate> est examinée plus en détail dans [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
> [!NOTE]
>  Veillez à définir la propriété jointe <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=fullName> sur le <xref:System.Windows.FrameworkElement> racine de <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
<a name="using_parts_of_the_controltemplate_in_code"></a>   
## Utilisation de composants du ControlTemplate dans le code  
 Un auteur <xref:System.Windows.Controls.ControlTemplate> peut omettre les objets <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.VisualState>, délibérément ou par erreur, mais la logique de votre contrôle a peut\-être besoin de ces composants pour fonctionner correctement.  Le modèle de composants et d'états spécifie que votre contrôle doit être résistant à un <xref:System.Windows.Controls.ControlTemplate> auquel il manque les objets <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.VisualState>.  Votre contrôle ne doit pas lever d'exception ou signaler une erreur s'il manque un <xref:System.Windows.FrameworkElement>, un <xref:System.Windows.VisualState> ou un <xref:System.Windows.VisualStateGroup> dans le <xref:System.Windows.Controls.ControlTemplate>.  Cette section décrit les méthodes recommandées pour interagir avec les objets <xref:System.Windows.FrameworkElement> et gérer des états.  
  
### Anticiper des objets FrameworkElement manquants  
 Lorsque vous définissez des objets <xref:System.Windows.FrameworkElement> dans le <xref:System.Windows.Controls.ControlTemplate>, la logique de votre contrôle devra peut\-être interagir avec certains d'entre eux.  Par exemple, le contrôle `NumericUpDown` s'abonne à l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> des boutons pour augmenter ou diminuer `Value` et affecte à la propriété <xref:System.Windows.Controls.TextBlock.Text%2A> du <xref:System.Windows.Controls.TextBlock> la valeur `Value`.  Si un <xref:System.Windows.Controls.ControlTemplate> personnalisé omet le <xref:System.Windows.Controls.TextBlock> ou des boutons, il est acceptable que le contrôle perde une partie de ses fonctionnalités, mais vous devez vous assurer que votre contrôle ne provoque pas d'erreur.  Par exemple, si un <xref:System.Windows.Controls.ControlTemplate> ne contient pas les boutons pour modifier `Value`, le `NumericUpDown` perd cette fonctionnalité, mais une application qui utilise le <xref:System.Windows.Controls.ControlTemplate> continuera à s'exécuter.  
  
 Les méthodes suivantes garantissent que votre contrôle répond de manière appropriée à des objets <xref:System.Windows.FrameworkElement> manquants :  
  
1.  Définissez l'attribut `x:Name` de chaque <xref:System.Windows.FrameworkElement> que vous devez référencer dans le code.  
  
2.  Définissez des propriétés privées pour chaque <xref:System.Windows.FrameworkElement> avec lequel vous devez interagir.  
  
3.  Abonnez\-vous et annulez votre abonnement à tous les événements que votre contrôle gère dans l'accesseur set de la propriété <xref:System.Windows.FrameworkElement>.  
  
4.  Définissez les propriétés <xref:System.Windows.FrameworkElement> que vous avez définies à l'étape 2 dans la méthode <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>.  C'est la première fois que le <xref:System.Windows.FrameworkElement> dans le <xref:System.Windows.Controls.ControlTemplate> est accessible au contrôle.  Utilisez le `x:Name` du <xref:System.Windows.FrameworkElement> pour l'obtenir à partir du <xref:System.Windows.Controls.ControlTemplate>.  
  
5.  Vérifiez que le <xref:System.Windows.FrameworkElement> n'est pas `null` avant d'accéder à ses membres.  S'il est `null`, ne signalez pas d'erreur.  
  
 Les exemples suivants montrent comment le contrôle `NumericUpDown` interagit avec les objets <xref:System.Windows.FrameworkElement> conformément aux recommandations dans la liste précédente.  
  
 Dans l'exemple qui définit la structure visuelle du contrôle `NumericUpDown` dans le <xref:System.Windows.Controls.ControlTemplate>, l'attribut `x:Name` du <xref:System.Windows.Controls.Primitives.RepeatButton> qui augmente `Value` a la valeur `UpButton`.  L'exemple suivant déclare une propriété appelée `UpButtonElement` qui représente le <xref:System.Windows.Controls.Primitives.RepeatButton> déclaré dans le <xref:System.Windows.Controls.ControlTemplate>.  L'accesseur `set` annule d'abord l'abonnement à l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> du bouton si `UpDownElement` n'est pas `null`. Il définit ensuite la propriété, puis s'abonne à l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  Il existe aussi une propriété, ne figurant pas ici, qui est également définie pour l'autre <xref:System.Windows.Controls.Primitives.RepeatButton>, nommée `DownButtonElement`.  
  
 [!code-csharp[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
 [!code-vb[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]  
  
 L'exemple suivant montre le <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> pour le contrôle `NumericUpDown`.  L'exemple utilise la méthode <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> pour obtenir les objets <xref:System.Windows.FrameworkElement> à partir du <xref:System.Windows.Controls.ControlTemplate>.  Remarquez que l'exemple évite les cas où <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> trouve un <xref:System.Windows.FrameworkElement> dont le nom spécifié n'est pas du type attendu.  Il est également recommandé d'ignorer les éléments qui ont le `x:Name` spécifié mais dont le type est incorrect.  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 En suivant les méthodes présentées dans les exemples précédents, vous êtes assuré que votre contrôle continuera de s'exécuter s'il manque un <xref:System.Windows.FrameworkElement> dans le <xref:System.Windows.Controls.ControlTemplate>.  
  
### Utiliser le VisualStateManager pour gérer des états  
 Le <xref:System.Windows.VisualStateManager> assure le suivi des états d'un contrôle et exécute la logique nécessaire à la transition entre les états.  Lorsque vous ajoutez des objets <xref:System.Windows.VisualState> au <xref:System.Windows.Controls.ControlTemplate>, vous les ajoutez à un <xref:System.Windows.VisualStateGroup> et vous ajoutez le <xref:System.Windows.VisualStateGroup> à la propriété jointe <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=fullName> afin que le <xref:System.Windows.VisualStateManager> puisse y accéder.  
  
 L'exemple suivant est similaire à l'exemple précédent qui montre les objets <xref:System.Windows.VisualState> qui correspondent aux états `Positive` et `Negative` du contrôle.  Le <xref:System.Windows.Media.Animation.Storyboard> dans le <xref:System.Windows.VisualState> `Negative` fait apparaître en rouge le <xref:System.Windows.Controls.TextBlock.Foreground%2A> du <xref:System.Windows.Controls.TextBlock>.  Lorsque le contrôle `NumericUpDown` est dans l'état `Negative`, le storyboard dans l'état `Negative` démarre.  Puis, le <xref:System.Windows.Media.Animation.Storyboard> dans l'état `Negative` s'arrête lorsque le contrôle retourne à l'état `Positive`.  Le <xref:System.Windows.VisualState> `Positive` n'a pas besoin de contenir de <xref:System.Windows.Media.Animation.Storyboard> car lorsque le <xref:System.Windows.Media.Animation.Storyboard> pour le `Negative` s'arrête, le <xref:System.Windows.Controls.TextBlock.Foreground%2A> reprend sa couleur d'origine.  
  
 [!code-xml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
 Notez qu'un nom est attribué au <xref:System.Windows.Controls.TextBlock>, mais que le <xref:System.Windows.Controls.TextBlock> n'est pas dans le contrat de contrôle pour `NumericUpDown` parce que la logique du contrôle ne référence jamais le <xref:System.Windows.Controls.TextBlock>.  Les éléments référencés dans le <xref:System.Windows.Controls.ControlTemplate> ont des noms, mais ne doivent pas faire partie du contrat de contrôle car un nouveau <xref:System.Windows.Controls.ControlTemplate> pour le contrôle ne doit pas nécessairement référencer cet élément.  Par exemple, quelqu'un qui crée un nouveau <xref:System.Windows.Controls.ControlTemplate> pour `NumericUpDown` peut décider de ne pas indiquer que `Value` est négative en modifiant le <xref:System.Windows.Controls.Control.Foreground%2A>.  Dans ce cas, ni le code ni le <xref:System.Windows.Controls.ControlTemplate> ne référence le <xref:System.Windows.Controls.TextBlock> par nom.  
  
 La logique du contrôle est chargée de modifier l'état du contrôle.  L'exemple suivant montre que le contrôle `NumericUpDown` appelle la méthode <xref:System.Windows.VisualStateManager.GoToState%2A> pour passer à l'état `Positive` lorsque `Value` est supérieure ou égale à 0, et à l'état `Negative` lorsque `Value` est inférieure à 0.  
  
 [!code-csharp[VSMCustomControl#ValueStateChange](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
 [!code-vb[VSMCustomControl#ValueStateChange](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]  
  
 La méthode <xref:System.Windows.VisualStateManager.GoToState%2A> exécute la logique nécessaire au démarrage et à l'arrêt appropriés des storyboards.  Lorsqu'un contrôle appelle <xref:System.Windows.VisualStateManager.GoToState%2A> pour modifier son état, le <xref:System.Windows.VisualStateManager> effectue les opérations suivantes :  
  
-   Si le <xref:System.Windows.VisualState> dans lequel bascule le contrôle possède un <xref:System.Windows.Media.Animation.Storyboard>, le storyboard démarre.  Puis, si le <xref:System.Windows.VisualState> d'où provient le contrôle possède un <xref:System.Windows.Media.Animation.Storyboard>, le storyboard s'arrête.  
  
-   Si le contrôle est déjà dans l'état spécifié, <xref:System.Windows.VisualStateManager.GoToState%2A> n'effectue aucune action et retourne `true`.  
  
-   Si l'état spécifié n'existe pas dans le <xref:System.Windows.Controls.ControlTemplate> de `control`, <xref:System.Windows.VisualStateManager.GoToState%2A> n'effectue aucune action et retourne `false`.  
  
#### Meilleures pratiques pour utiliser le VisualStateManager  
 Il est recommandé d'effectuer les opérations suivantes pour gérer les états de votre contrôle :  
  
-   utiliser des propriétés pour suivre son état ;  
  
-   créer une méthode d'assistance pour effectuer la transition entre les états.  
  
 Le contrôle `NumericUpDown` utilise sa propriété `Value` pour déterminer s'il se trouve dans l'état `Positive` ou `Negative`.  Le contrôle `NumericUpDown` définit aussi les états `Focused` et `UnFocused`, qui suivent la propriété <xref:System.Windows.UIElement.IsFocused%2A>.  Si vous utilisez des états qui ne correspondent pas naturellement à une propriété du contrôle, vous pouvez définir une propriété privée pour suivre l'état.  
  
 Une méthode unique qui met à jour tous les états centralise les appels au niveau du <xref:System.Windows.VisualStateManager> et permet de conserver le code gérable.  L'exemple suivant présente `UpdateStates`, la méthode d'assistance du contrôle `NumericUpDown`.  Lorsque `Value` est supérieure ou égale à 0, le <xref:System.Windows.Controls.Control> est dans l'état `Positive`.  Lorsque `Value` est inférieure à 0, le contrôle est dans l'état `Negative`.  Lorsque <xref:System.Windows.UIElement.IsFocused%2A> est `true`, le contrôle est dans l'état `Focused` ; sinon, il est dans l'état `Unfocused`.  Le contrôle peut appeler `UpdateStates` chaque fois qu'il doit modifier son état, indépendamment des modifications d'états.  
  
 [!code-csharp[VSMCustomControl#UpdateStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
 [!code-vb[VSMCustomControl#UpdateStates](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]  
  
 Si vous passez un nom d'état à <xref:System.Windows.VisualStateManager.GoToState%2A> lorsque le contrôle est déjà dans cet état, <xref:System.Windows.VisualStateManager.GoToState%2A> n'a aucun effet, vous n'avez donc pas besoin de vérifier l'état actuel du contrôle.  Par exemple, si `Value` passe d'un nombre négatif à un autre nombre négatif, le storyboard de l'état `Negative` n'est pas interrompu et l'utilisateur ne verra aucune modification au niveau du contrôle.  
  
 Le <xref:System.Windows.VisualStateManager> utilise des objets <xref:System.Windows.VisualStateGroup> pour déterminer l'état qu'il doit quitter lorsque vous appelez <xref:System.Windows.VisualStateManager.GoToState%2A>.  Le contrôle est toujours dans un état donné pour chaque <xref:System.Windows.VisualStateGroup> défini dans son <xref:System.Windows.Controls.ControlTemplate> et il ne le quitte que lorsqu'il passe à un autre état à partir du même <xref:System.Windows.VisualStateGroup>.  Par exemple, le <xref:System.Windows.Controls.ControlTemplate> du contrôle `NumericUpDown` définit les objets <xref:System.Windows.VisualState> `Positive` et `Negative` dans un <xref:System.Windows.VisualStateGroup> et les objets <xref:System.Windows.VisualState> `Focused` et `Unfocused` dans un autre.  \(Vous pouvez voir le <xref:System.Windows.VisualState> `Focused` et `Unfocused` défini dans la section [Exemple complet](#complete_example) de cette rubrique. Lorsque le contrôle passe de l'état `Positive` à l'état `Negative`, ou vice versa, l'état du contrôle demeure `Focused` ou `Unfocused`\).  
  
 L'état d'un contrôle peut changer dans trois cas typiques :  
  
-   lorsque le <xref:System.Windows.Controls.ControlTemplate> est appliqué au <xref:System.Windows.Controls.Control> ;  
  
-   lorsqu'une propriété est modifiée ;  
  
-   lorsqu'un événement se produit.  
  
 Les exemples suivants montrent la mise à jour de l'état du contrôle `NumericUpDown` dans ces cas\-là.  
  
 Vous devez mettre à jour l'état du contrôle dans la méthode <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> afin que le contrôle apparaisse dans l'état approprié quand le <xref:System.Windows.Controls.ControlTemplate> est appliqué.  L'exemple suivant appelle `UpdateStates` dans <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> pour garantir que le contrôle est dans les états appropriés.  Par exemple, supposez que vous créez un contrôle `NumericUpDown`, puis que vous affectez la couleur verte à <xref:System.Windows.Controls.Control.Foreground%2A> et la valeur \-5 à `Value`.  Si vous n'appelez pas `UpdateStates` lorsque le <xref:System.Windows.Controls.ControlTemplate> est appliqué au contrôle `NumericUpDown`, le contrôle n'est pas dans l'état `Negative` et la valeur est verte au lieu de rouge.  Vous devez appeler `UpdateStates` pour faire passer le contrôle dans l'état `Negative`.  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 Vous devez souvent mettre à jour les états d'un contrôle lorsqu'une propriété change.  L'exemple suivant présente la méthode `ValueChangedCallback` complète.  Comme `ValueChangedCallback` est appelé lorsque `Value` est modifiée, la méthode appelle `UpdateStates` si `Value` passe d'une valeur positive à une valeur négative, ou vice versa.  Il est acceptable d'appeler `UpdateStates` lorsque `Value` change mais reste positive ou négative, car, dans ce cas, le contrôle ne change pas d'état.  
  
 [!code-csharp[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
 [!code-vb[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]  
  
 Vous pourriez également devoir mettre à jour les états lorsqu'un événement se produit.  L'exemple suivant montre que le `NumericUpDown` appelle `UpdateStates` sur le <xref:System.Windows.Controls.Control> pour gérer l'événement <xref:System.Windows.UIElement.GotFocus>.  
  
 [!code-csharp[VSMCustomControl#OnGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
 [!code-vb[VSMCustomControl#OnGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]  
  
 Le <xref:System.Windows.VisualStateManager> vous aide à gérer les états de votre contrôle.  En utilisant le <xref:System.Windows.VisualStateManager>, vous garantissez que votre contrôle effectue les transitions entre états de manière correcte.  Si vous suivez les recommandations décrites dans cette section pour utiliser le <xref:System.Windows.VisualStateManager>, le code de votre contrôle restera lisible et gérable.  
  
<a name="providing_the_control_contract"></a>   
## Fourniture du contrat de contrôle  
 Vous fournissez un contrat de contrôle pour indiquer aux auteurs de <xref:System.Windows.Controls.ControlTemplate> les éléments à inclure dans le modèle.  Un contrat de contrôle comporte trois éléments :  
  
-   les éléments visuels utilisés par la logique du contrôle ;  
  
-   les états du contrôle et le groupe auquel appartient chaque état ;  
  
-   les propriétés publiques qui affectent visuellement le contrôle.  
  
 Quelqu'un qui crée un <xref:System.Windows.Controls.ControlTemplate> doit savoir quels objets <xref:System.Windows.FrameworkElement> sont utilisés par la logique du contrôle, ainsi que le type et le nom de chaque objet.  Un auteur de <xref:System.Windows.Controls.ControlTemplate> doit également savoir le nom de chaque état possible dans lequel le contrôle peut être et le <xref:System.Windows.VisualStateGroup> dans lequel l'état se trouve.  
  
 Si nous reprenons l'exemple de `NumericUpDown`, le contrôle s'attend à ce que le <xref:System.Windows.Controls.ControlTemplate> possède les objets <xref:System.Windows.FrameworkElement> suivants :  
  
-   <xref:System.Windows.Controls.Primitives.RepeatButton> appelé `UpButton` ;  
  
-   un <xref:System.Windows.Controls.Primitives.RepeatButton> appelé `DownButton.`,  
  
 Le contrôle peut être dans les états suivants :  
  
-   dans le `ValueStates` <xref:System.Windows.VisualStateGroup> ;  
  
    -   `Positive`  
  
    -   `Negative`  
  
-   dans le `FocusStates` <xref:System.Windows.VisualStateGroup>.  
  
    -   `Focused`  
  
    -   `Unfocused`  
  
 Pour spécifier les objets <xref:System.Windows.FrameworkElement> attendus par le contrôle, vous utilisez le <xref:System.Windows.TemplatePartAttribute>, qui spécifie le nom et type des éléments attendus.  Pour spécifier les états possibles d'un contrôle, vous utilisez le <xref:System.Windows.TemplateVisualStateAttribute>, qui spécifie le nom de l'état et le <xref:System.Windows.VisualStateGroup> auquel il appartient.  Placez le <xref:System.Windows.TemplatePartAttribute> et le <xref:System.Windows.TemplateVisualStateAttribute> dans la définition de classe du contrôle.  
  
 Toute propriété publique qui affecte l'apparence de votre contrôle fait également partie du contrat de contrôle.  
  
 L'exemple suivant spécifie l'objet <xref:System.Windows.FrameworkElement> et les états d'un contrôle `NumericUpDown`.  
  
 [!code-csharp[VSMCustomControl#ControlContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
 [!code-vb[VSMCustomControl#ControlContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]  
  
<a name="complete_example"></a>   
## Exemple complet  
 L'exemple suivant illustre le <xref:System.Windows.Controls.ControlTemplate> complet pour le `NumericUpDown`.  
  
 [!code-xml[VSMCustomControl#NUDTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]  
  
 L'exemple suivant illustre la logique pour le `NumericUpDown`.  
  
 [!code-csharp[VSMCustomControl#ControlLogic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
 [!code-vb[VSMCustomControl#ControlLogic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]  
  
## Voir aussi  
 [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)   
 [Personnalisation des contrôles](../../../../docs/framework/wpf/controls/control-customization.md)