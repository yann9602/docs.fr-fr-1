---
title: "Création d'un contrôle avec une apparence personnalisable"
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
- controls [WPF], customizing
- VisualStateManager [WPF], managing the state of a control
- ControlTemplate [WPF], customizing appearance
- controls [WPF], defining the visual structure and behavior of
- customizing appearance [WPF], ControlTemplate
- managing control states [WPF], VisualStateManager
- VisualStateManager [WPF], best practice
ms.assetid: 9e356d3d-a3d0-4b01-a25f-2d43e4d53fe5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e76e1d814df5946d0e0f946cbc8d55507a07c96
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>Création d'un contrôle avec une apparence personnalisable
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]vous donne la possibilité de créer un contrôle dont l’apparence peut être personnalisée. Par exemple, vous pouvez modifier l’apparence d’un <xref:System.Windows.Controls.CheckBox> dépasse le paramètre de propriétés fera en créant un nouveau <xref:System.Windows.Controls.ControlTemplate>. L’illustration suivante montre un <xref:System.Windows.Controls.CheckBox> qui utilise une valeur par défaut <xref:System.Windows.Controls.ControlTemplate> et un <xref:System.Windows.Controls.CheckBox> qui utilise une personnalisée <xref:System.Windows.Controls.ControlTemplate>.  
  
 ![Une case à cocher avec le modèle de contrôle par défaut. ] (../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Case à cocher qui utilise le modèle de contrôle par défaut  
  
 ![Une case à cocher avec un modèle de contrôle personnalisé. ] (../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Case à cocher qui utilise un modèle de contrôle personnalisé  
  
 Si vous suivez le modèle de composants et états lorsque vous créez un contrôle, l’apparence de votre contrôle est personnalisable. Outils de conception tels que Microsoft Expression Blend prend en charge le modèle de composants et états, lorsque vous suivez ce modèle votre contrôle est personnalisable dans ces types d’applications.  Cette rubrique explique le modèle de composants et états et suivre lorsque vous créez votre propre contrôle. Cette rubrique présente un exemple d’un contrôle personnalisé, `NumericUpDown`, pour illustrer la philosophie de ce modèle.  Le `NumericUpDown` contrôle affiche une valeur numérique, qu’un utilisateur peut augmenter ou diminuer en cliquant sur les boutons du contrôle.  L’illustration suivante montre la `NumericUpDown` contrôle qui est décrite dans cette rubrique.  
  
 ![Contrôle personnalisé NumericUpDown. ] (../../../../docs/framework/wpf/controls/media/ndp-numericupdown.png "NDP_NumericUPDown")  
Un contrôle NumericUpDown personnalisé  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Composants requis](#prerequisites)  
  
-   [Modèle de composants et États](#parts_and_states_model)  
  
-   [Définition de la Structure visuelle et le comportement d’un contrôle dans un modèle de contrôle](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)  
  
-   [À l’aide de parties de ControlTemplate dans le Code](#using_parts_of_the_controltemplate_in_code)  
  
-   [En fournissant le contrat de contrôle](#providing_the_control_contract)  
  
-   [Exemple complet](#complete_example)  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Conditions préalables  
 Cette rubrique suppose que vous connaissez la procédure créer un nouveau <xref:System.Windows.Controls.ControlTemplate> pour un contrôle existant, connaissez quels sont les éléments d’un contrat de contrôle et de comprendre les concepts abordés dans [personnalisation de l’apparence d’un contrôle existant par Création d’un modèle de contrôle](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
> [!NOTE]
>  Pour créer un contrôle qui peut avoir son apparence personnalisée, vous devez créer un contrôle qui hérite de la <xref:System.Windows.Controls.Control> classe ou une de ses sous-classes autres que <xref:System.Windows.Controls.UserControl>.  Un contrôle qui hérite de <xref:System.Windows.Controls.UserControl> est un contrôle qui peut être créé rapidement, mais elle n’utilise pas un <xref:System.Windows.Controls.ControlTemplate> et vous ne pouvez pas personnaliser son apparence.  
  
<a name="parts_and_states_model"></a>   
## <a name="parts-and-states-model"></a>Modèle de composants et États  
 Le modèle de composants et états spécifie comment définir la structure visuelle et le comportement d’un contrôle. Pour suivre le modèle de composants et états, vous devez procédez comme suit :  
  
-   Définir la structure visuelle et le comportement visuel dans le <xref:System.Windows.Controls.ControlTemplate> d’un contrôle.  
  
-   Suivez certaines meilleures pratiques lorsque la logique de votre contrôle interagit avec les parties du modèle de contrôle.  
  
-   Fournissez un contrat de contrôle pour spécifier ce qui doit être inclus dans le <xref:System.Windows.Controls.ControlTemplate>.  
  
 Lorsque vous définissez la structure visuelle et le comportement visuel dans le <xref:System.Windows.Controls.ControlTemplate> d’un contrôle, les auteurs d’application peuvent modifier la structure visuelle et le comportement visuel de votre contrôle en créant un <xref:System.Windows.Controls.ControlTemplate> au lieu d’écrire du code.   Vous devez fournir un contrat de contrôle qui indique l’application, la méthode qui <xref:System.Windows.FrameworkElement> les États et les objets doivent être définis dans le <xref:System.Windows.Controls.ControlTemplate>. Vous devez suivre certaines meilleures pratiques lorsque vous interagissez avec les parties dans le <xref:System.Windows.Controls.ControlTemplate> afin que votre contrôle gère correctement incomplet <xref:System.Windows.Controls.ControlTemplate>.  Si vous appliquez ces trois principes, aux auteurs d’applications sera en mesure de créer un <xref:System.Windows.Controls.ControlTemplate> pour votre contrôle tout aussi facilement que si elles peuvent pour les contrôles qui sont fournis avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  La section suivante décrit chacune de ces recommandations en détail.  
  
<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>   
## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>Définition de la Structure visuelle et le comportement d’un contrôle dans un modèle de contrôle  
 Lorsque vous créez votre contrôle personnalisé en utilisant le modèle de composants et états, vous définissez la structure visuelle du contrôle et le comportement visuel dans son <xref:System.Windows.Controls.ControlTemplate> au lieu de dans sa logique.  La structure visuelle d’un contrôle est le composite de <xref:System.Windows.FrameworkElement> objets qui composent le contrôle.  Le comportement visuel est l’apparence du contrôle lorsqu’il est dans un certain état.   Pour plus d’informations sur la création d’un <xref:System.Windows.Controls.ControlTemplate> qui spécifie la structure visuelle et le comportement d’un contrôle, consultez [personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
 Dans l’exemple de la `NumericUpDown` (contrôle), la structure visuelle inclut deux <xref:System.Windows.Controls.Primitives.RepeatButton> contrôles et un <xref:System.Windows.Controls.TextBlock>.  Si vous ajoutez ces contrôles dans le code de le `NumericUpDown` contrôle--dans son constructeur, par exemple--les positions de ces contrôles est irréversible.  Au lieu de définir la structure visuelle et le comportement visuel du contrôle dans son code, vous devez la définir dans le <xref:System.Windows.Controls.ControlTemplate>.  Un développeur d’applications pour personnaliser la position des boutons et <xref:System.Windows.Controls.TextBlock> et spécifier le comportement qui se produit lorsque `Value` est un nombre négatif, car la <xref:System.Windows.Controls.ControlTemplate> peut être remplacé.  
  
 L’exemple suivant montre la structure visuelle de la `NumericUpDown` contrôle, qui inclut un <xref:System.Windows.Controls.Primitives.RepeatButton> pour augmenter `Value`, un <xref:System.Windows.Controls.Primitives.RepeatButton> pour diminuer `Value`et un <xref:System.Windows.Controls.TextBlock> pour afficher `Value`.  
  
 [!code-xaml[VSMCustomControl#VisualStructure](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]  
  
 Un comportement visuel de la `NumericUpDown` contrôle est que la valeur est dans une police rouge s’il est négatif.  Si vous modifiez le <xref:System.Windows.Controls.TextBlock.Foreground%2A> de la <xref:System.Windows.Controls.TextBlock> dans le code lorsque le `Value` est négatif, la `NumericUpDown` affichent toujours une valeur négative rouge. Vous spécifiez le comportement visuel du contrôle dans le <xref:System.Windows.Controls.ControlTemplate> en ajoutant <xref:System.Windows.VisualState> des objets sur le <xref:System.Windows.Controls.ControlTemplate>.  L’exemple suivant illustre la <xref:System.Windows.VisualState> des objets pour le `Positive` et `Negative` les États.  `Positive`et `Negative` sont mutuellement exclusif (le contrôle est toujours exactement dans l’un des deux), de sorte que l’exemple place la <xref:System.Windows.VisualState> des objets dans un seul <xref:System.Windows.VisualStateGroup>.  Lorsque le contrôle passe à la `Negative` état, le <xref:System.Windows.Controls.TextBlock.Foreground%2A> de la <xref:System.Windows.Controls.TextBlock> devient rouge.  Lorsque le contrôle est dans le `Positive` état, le <xref:System.Windows.Controls.TextBlock.Foreground%2A> retrouve sa valeur d’origine.  Définition <xref:System.Windows.VisualState> des objets dans une <xref:System.Windows.Controls.ControlTemplate> est expliquée en détail dans [personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
> [!NOTE]
>  Veillez à définir le <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> propriété jointe sur la racine <xref:System.Windows.FrameworkElement> de la <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xaml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
<a name="using_parts_of_the_controltemplate_in_code"></a>   
## <a name="using-parts-of-the-controltemplate-in-code"></a>À l’aide de parties de ControlTemplate dans le Code  
 A <xref:System.Windows.Controls.ControlTemplate> auteur peut omettre <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.VisualState> des objets, intentionnellement ou par erreur, mais la logique de votre contrôle peut-être besoin de ces composants pour fonctionner correctement. Le modèle de composants et états Spécifie que votre contrôle doit être résilient à un <xref:System.Windows.Controls.ControlTemplate> qui n’a pas <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.VisualState> objets.  Votre contrôle ne doit pas lever d’exception ou signaler une erreur si un <xref:System.Windows.FrameworkElement>, <xref:System.Windows.VisualState>, ou <xref:System.Windows.VisualStateGroup> est manquant dans le <xref:System.Windows.Controls.ControlTemplate>. Cette section décrit les pratiques recommandées pour l’interaction avec <xref:System.Windows.FrameworkElement> objets et la gestion des États.  
  
### <a name="anticipate-missing-frameworkelement-objects"></a>Anticiper des objets FrameworkElement manquants  
 Lorsque vous définissez <xref:System.Windows.FrameworkElement> des objets dans le <xref:System.Windows.Controls.ControlTemplate>, la logique de votre contrôle devra peut-être interagir avec certains d'entre eux.  Par exemple, le `NumericUpDown` contrôle s’abonne aux boutons <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement pour augmenter ou diminuer `Value` et définit le <xref:System.Windows.Controls.TextBlock.Text%2A> propriété de la <xref:System.Windows.Controls.TextBlock> à `Value`. Si une personnalisée <xref:System.Windows.Controls.ControlTemplate> omet le <xref:System.Windows.Controls.TextBlock> ou boutons, il est acceptable que le contrôle perd certaines de ses fonctionnalités, mais vous devez être sûr que votre contrôle ne provoque pas une erreur. Par exemple, si un <xref:System.Windows.Controls.ControlTemplate> ne contient pas les boutons Modifier `Value`, le `NumericUpDown` perd cette fonctionnalité, mais une application qui utilise le <xref:System.Windows.Controls.ControlTemplate> continuera à s’exécuter.  
  
 Les méthodes suivantes garantissent que votre contrôle répond correctement à manquant <xref:System.Windows.FrameworkElement> objets :  
  
1.  Définir le `x:Name` attribut pour chaque <xref:System.Windows.FrameworkElement> que vous devez le référencer dans le code.  
  
2.  Définissez des propriétés privées pour chaque <xref:System.Windows.FrameworkElement> dont vous avez besoin d’interagir avec.  
  
3.  S’abonner et annuler l’abonnement à tous les événements que votre contrôle gère dans la <xref:System.Windows.FrameworkElement> accesseur set de la propriété.  
  
4.  Définir le <xref:System.Windows.FrameworkElement> propriétés que vous avez définie dans l’étape 2 la <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> (méthode). Il s’agit de la plus ancienne que la <xref:System.Windows.FrameworkElement> dans le <xref:System.Windows.Controls.ControlTemplate> est disponible pour le contrôle. Utilisez le `x:Name` de la <xref:System.Windows.FrameworkElement> pour l’obtenir à partir de la <xref:System.Windows.Controls.ControlTemplate>.  
  
5.  Vérifiez que le <xref:System.Windows.FrameworkElement> n’est pas `null` avant d’accéder à ses membres.  S’il s’agit `null`, ne signalent pas d’erreur.  
  
 Les exemples suivants montrent comment les `NumericUpDown` contrôle interagit avec <xref:System.Windows.FrameworkElement> objets conformément aux recommandations dans la liste précédente.  
  
 Dans l’exemple qui définit la structure visuelle de la `NumericUpDown` contrôler dans le <xref:System.Windows.Controls.ControlTemplate>, le <xref:System.Windows.Controls.Primitives.RepeatButton> qui augmente `Value` a son `x:Name` attribut la valeur `UpButton`.  L’exemple suivant déclare une propriété appelée `UpButtonElement` qui représente le <xref:System.Windows.Controls.Primitives.RepeatButton> qui est déclaré dans le <xref:System.Windows.Controls.ControlTemplate>. Le `set` accesseur annule d’abord sur le bouton <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement si `UpDownElement` n’est pas `null`, puis il définit la propriété, puis elle s’abonne à la <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement. Il existe également une propriété définie, mais ne pas indiqué ici, pour les autres <xref:System.Windows.Controls.Primitives.RepeatButton>, appelé `DownButtonElement`.  
  
 [!code-csharp[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
 [!code-vb[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]  
  
 L’exemple suivant illustre la <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> pour la `NumericUpDown` contrôle.  L’exemple utilise le <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> méthode pour obtenir le <xref:System.Windows.FrameworkElement> des objets de la <xref:System.Windows.Controls.ControlTemplate>.  Notez que l’exemple évite les cas où <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> recherche un <xref:System.Windows.FrameworkElement> avec le nom spécifié n’est pas du type attendu. Il est également recommandé d’ignorer les éléments qui ont spécifié `x:Name` mais sont de type incorrect.  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 En suivant les méthodes qui sont affichées dans les exemples précédents, vous assurez que votre contrôle continuera à exécuter quand le <xref:System.Windows.Controls.ControlTemplate> manque un <xref:System.Windows.FrameworkElement>.  
  
### <a name="use-the-visualstatemanager-to-manage-states"></a>Utiliser le VisualStateManager pour gérer des États  
 Le <xref:System.Windows.VisualStateManager> assure le suivi des États d’un contrôle et exécute la logique nécessaire pour effectuer la transition entre les États. Lorsque vous ajoutez <xref:System.Windows.VisualState> des objets à la <xref:System.Windows.Controls.ControlTemplate>, vous les ajoutez à un <xref:System.Windows.VisualStateGroup> et ajouter le <xref:System.Windows.VisualStateGroup> à la <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> propriété jointe afin que le <xref:System.Windows.VisualStateManager> puisse y accéder.  
  
 L’exemple suivant répète l’exemple précédent montre la <xref:System.Windows.VisualState> les objets qui correspond à la `Positive` et `Negative` les États du contrôle. Le <xref:System.Windows.Media.Animation.Storyboard> dans les `Negative` <xref:System.Windows.VisualState> Active le <xref:System.Windows.Controls.TextBlock.Foreground%2A> de la <xref:System.Windows.Controls.TextBlock> rouge.   Lorsque le `NumericUpDown` contrôle se trouve dans le `Negative` d’état, le plan conceptuel dans le `Negative` état commence.  Le <xref:System.Windows.Media.Animation.Storyboard> dans les `Negative` d’état s’arrête lorsque le contrôle retourne à la `Positive` état.  Le `Positive` <xref:System.Windows.VisualState> ne nécessitent aucun un <xref:System.Windows.Media.Animation.Storyboard> , car lorsque le <xref:System.Windows.Media.Animation.Storyboard> pour le `Negative` s’arrête, le <xref:System.Windows.Controls.TextBlock.Foreground%2A> reprend sa couleur d’origine.  
  
 [!code-xaml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
 Notez que la <xref:System.Windows.Controls.TextBlock> porte un nom, mais la <xref:System.Windows.Controls.TextBlock> n’est pas dans le contrat de contrôle `NumericUpDown` parce que la logique du contrôle ne référence jamais le <xref:System.Windows.Controls.TextBlock>.  Les éléments qui sont référencés dans les <xref:System.Windows.Controls.ControlTemplate> ont des noms, mais n’avez pas besoin de faire partie du contrat de contrôle, car un nouveau <xref:System.Windows.Controls.ControlTemplate> pour le contrôle ne peut pas besoin de faire référence à cet élément.  Par exemple, une personne qui crée un <xref:System.Windows.Controls.ControlTemplate> pour `NumericUpDown` pouvez décider de ne pas indiquer que `Value` est un nombre négatif en modifiant le <xref:System.Windows.Controls.Control.Foreground%2A>.  Dans ce cas, ni le code ni le <xref:System.Windows.Controls.ControlTemplate> références le <xref:System.Windows.Controls.TextBlock> par nom.  
  
 La logique du contrôle est responsable de la modification de l’état du contrôle. L’exemple suivant montre que le `NumericUpDown` appels de contrôle le <xref:System.Windows.VisualStateManager.GoToState%2A> méthode pour passer à la `Positive` état lorsque `Value` est 0 ou supérieur et le `Negative` état lorsque `Value` est inférieur à 0.  
  
 [!code-csharp[VSMCustomControl#ValueStateChange](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
 [!code-vb[VSMCustomControl#ValueStateChange](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]  
  
 Le <xref:System.Windows.VisualStateManager.GoToState%2A> méthode exécute la logique nécessaire pour démarrer et arrêter les plans conceptuels de manière appropriée. Lorsqu’un contrôle appelle <xref:System.Windows.VisualStateManager.GoToState%2A> pour modifier son état, le <xref:System.Windows.VisualStateManager> effectue les opérations suivantes :  
  
-   Si le <xref:System.Windows.VisualState> que le contrôle va a un <xref:System.Windows.Media.Animation.Storyboard>, l’animation commence. Ensuite, si le <xref:System.Windows.VisualState> que le contrôle provient a un <xref:System.Windows.Media.Animation.Storyboard>, les extrémités de la table de montage séquentiel.  
  
-   Si le contrôle est déjà dans l’état qui est spécifié, <xref:System.Windows.VisualStateManager.GoToState%2A> n’effectue aucune action et retourne `true`.  
  
-   Si l’état spécifié n’existe pas dans le <xref:System.Windows.Controls.ControlTemplate> de `control`, <xref:System.Windows.VisualStateManager.GoToState%2A> n’effectue aucune action et retourne `false`.  
  
#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>Meilleures pratiques pour utiliser le VisualStateManager  
 Il est recommandé de procéder comme suit pour mettre à jour les États de votre contrôle :  
  
-   Utilisez les propriétés pour suivre son état.  
  
-   Créez une méthode d’assistance pour effectuer la transition entre les États.  
  
 Le `NumericUpDown` de contrôles utilise son `Value` propriété pour déterminer si elle est dans le `Positive` ou `Negative` état.  Le `NumericUpDown` contrôle définit également la `Focused` et `UnFocused` les États, les pistes le <xref:System.Windows.UIElement.IsFocused%2A> propriété. Si vous utilisez des États qui ne correspondent pas naturellement à une propriété du contrôle, vous pouvez définir une propriété privée pour effectuer le suivi de l’état.  
  
 Une méthode unique qui met à jour tous les états centralise les appels à la <xref:System.Windows.VisualStateManager> et conserve votre code facile à gérer. L’exemple suivant illustre la `NumericUpDown` méthode d’assistance du contrôle `UpdateStates`. Lorsque `Value` est supérieur ou égal à 0, le <xref:System.Windows.Controls.Control> est dans le `Positive` état.  Lorsque `Value` est inférieur à 0, le contrôle est dans le `Negative` état.  Lorsque <xref:System.Windows.UIElement.IsFocused%2A> est `true`, le contrôle est dans le `Focused` état ; sinon, il se trouve dans le `Unfocused` état.  Le contrôle peut appeler `UpdateStates` chaque fois qu’il doit modifier son état, quel que soit l’état change.  
  
 [!code-csharp[VSMCustomControl#UpdateStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
 [!code-vb[VSMCustomControl#UpdateStates](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]  
  
 Si vous passez un nom d’état à <xref:System.Windows.VisualStateManager.GoToState%2A> lorsque le contrôle est déjà dans cet état, <xref:System.Windows.VisualStateManager.GoToState%2A> ne fait rien, vous n’avez pas besoin de vérifier l’état du contrôle actuel.  Par exemple, si `Value` passe d’un nombre négatif à un autre nombre négatif, la table de montage séquentiel pour les `Negative` état n’est pas interrompu et l’utilisateur ne voit pas une modification dans le contrôle.  
  
 Le <xref:System.Windows.VisualStateManager> utilise <xref:System.Windows.VisualStateGroup> objets afin de déterminer l’état de fermeture lorsque vous appelez <xref:System.Windows.VisualStateManager.GoToState%2A>. Le contrôle est toujours dans un état pour chaque <xref:System.Windows.VisualStateGroup> qui est définie dans son <xref:System.Windows.Controls.ControlTemplate> et ne quitte un état lorsqu’il passe à un autre état de la même <xref:System.Windows.VisualStateGroup>. Par exemple, le <xref:System.Windows.Controls.ControlTemplate> de la `NumericUpDown` contrôle définit les `Positive` et `Negative` <xref:System.Windows.VisualState> objets dans une <xref:System.Windows.VisualStateGroup> et le `Focused` et `Unfocused` <xref:System.Windows.VisualState> objets dans un autre. (Vous pouvez voir le `Focused` et `Unfocused` <xref:System.Windows.VisualState> défini dans le [exemple complet](#complete_example) dans cette rubrique, lorsque le contrôle passe à partir de la `Positive` l’état le `Negative` état, ou vice versa, le conserve le contrôle, que ce soit le `Focused` ou `Unfocused` état.  
  
 Il existe trois emplacements par défaut où l’état d’un contrôle peut changer :  
  
-   Lorsque le <xref:System.Windows.Controls.ControlTemplate> est appliqué à la <xref:System.Windows.Controls.Control>.  
  
-   Lorsqu’une propriété est modifiée.  
  
-   Lorsqu’un événement se produit.  
  
 Les exemples suivants illustrent la mise à jour de l’état de la `NumericUpDown` contrôle dans ces cas.  
  
 Vous devez mettre à jour l’état du contrôle dans le <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> méthode afin que le contrôle apparaît dans le bon état lorsque le <xref:System.Windows.Controls.ControlTemplate> est appliqué. L’exemple suivant appelle `UpdateStates` dans <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> pour vous assurer que le contrôle est dans les états appropriés.  Par exemple, supposons que vous créez un `NumericUpDown` contrôler, puis définissez son <xref:System.Windows.Controls.Control.Foreground%2A> vert et `Value` à -5.  Si vous n’appelez pas `UpdateStates` lors de la <xref:System.Windows.Controls.ControlTemplate> est appliqué à la `NumericUpDown` contrôle, le contrôle n’est pas dans le `Negative` état et la valeur est verte au lieu de rouge.  Vous devez appeler `UpdateStates` pour placer le contrôle dans le `Negative` état.  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 Vous devez souvent mettre à jour les États d’un contrôle lorsqu’une propriété est modifiée. L’exemple suivant montre l’intégralité de `ValueChangedCallback` (méthode). Étant donné que `ValueChangedCallback` est appelée lorsque `Value` change, les appels de méthode `UpdateStates` en cas de `Value` a été remplacée par positive, négative ou vice versa. Il est acceptable d’appeler `UpdateStates` lorsque `Value` change mais reste positive ou négative, car dans ce cas, le contrôle ne change pas d’état.  
  
 [!code-csharp[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
 [!code-vb[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]  
  
 Vous devrez peut-être également mettre à jour les États lorsqu’un événement se produit. L’exemple suivant montre que le `NumericUpDown` appelle `UpdateStates` sur la <xref:System.Windows.Controls.Control> pour gérer les <xref:System.Windows.UIElement.GotFocus> événement.  
  
 [!code-csharp[VSMCustomControl#OnGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
 [!code-vb[VSMCustomControl#OnGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]  
  
 Le <xref:System.Windows.VisualStateManager> vous permet de gérer les États de votre contrôle. À l’aide de la <xref:System.Windows.VisualStateManager>, vous assurer que votre contrôle effectue correctement les transitions entre États.  Si vous suivez les recommandations décrites dans cette section pour utiliser le <xref:System.Windows.VisualStateManager>, le code de votre contrôle restera lisibles et gérables.  
  
<a name="providing_the_control_contract"></a>   
## <a name="providing-the-control-contract"></a>En fournissant le contrat de contrôle  
 Vous fournissez un contrat de contrôle afin que <xref:System.Windows.Controls.ControlTemplate> auteurs sachent à quoi à placer dans le modèle. Un contrat de contrôle comporte trois éléments :  
  
-   les éléments visuels utilisés par la logique du contrôle ;  
  
-   les états du contrôle et le groupe auquel appartient chaque état ;  
  
-   les propriétés publiques qui affectent visuellement le contrôle.  
  
 Une personne qui crée un <xref:System.Windows.Controls.ControlTemplate> doit savoir <xref:System.Windows.FrameworkElement> la logique du contrôle utilise des objets, le type de chaque objet est, et le son nom est. A <xref:System.Windows.Controls.ControlTemplate> auteur doit également connaître le nom de chaque état possible que le contrôle peut être inclus dans et qui <xref:System.Windows.VisualStateGroup> l’état est.  
  
 Retour à la `NumericUpDown` exemple, le contrôle s’attend le <xref:System.Windows.Controls.ControlTemplate> à respecter les conditions suivantes <xref:System.Windows.FrameworkElement> objets :  
  
-   A <xref:System.Windows.Controls.Primitives.RepeatButton> appelée `UpButton`.  
  
-   A <xref:System.Windows.Controls.Primitives.RepeatButton> appelé`DownButton.`  
  
 Le contrôle peut être dans les états suivants :  
  
-   Dans le`ValueStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Positive`  
  
    -   `Negative`  
  
-   Dans le`FocusStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Focused`  
  
    -   `Unfocused`  
  
 Pour spécifier les éléments <xref:System.Windows.FrameworkElement> attend des objets le contrôle, vous utilisez le <xref:System.Windows.TemplatePartAttribute>, qui spécifie le nom et le type des éléments attendus.  Pour spécifier les états possibles d’un contrôle, vous utilisez la <xref:System.Windows.TemplateVisualStateAttribute>, qui spécifie le nom de l’état et qui <xref:System.Windows.VisualStateGroup> auquel il appartient.  Placez le <xref:System.Windows.TemplatePartAttribute> et <xref:System.Windows.TemplateVisualStateAttribute> sur la définition de classe du contrôle.  
  
 Toute propriété publique qui affecte l’apparence de votre contrôle fait également partie du contrat de contrôle.  
  
 L’exemple suivant spécifie la <xref:System.Windows.FrameworkElement> objet et des États pour les `NumericUpDown` contrôle.  
  
 [!code-csharp[VSMCustomControl#ControlContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
 [!code-vb[VSMCustomControl#ControlContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Exemple complet  
 L’exemple suivant est l’ensemble de <xref:System.Windows.Controls.ControlTemplate> pour la `NumericUpDown` contrôle.  
  
 [!code-xaml[VSMCustomControl#NUDTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]  
  
 L’exemple suivant montre la logique pour le `NumericUpDown`.  
  
 [!code-csharp[VSMCustomControl#ControlLogic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
 [!code-vb[VSMCustomControl#ControlLogic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)  
 [Personnalisation des contrôles](../../../../docs/framework/wpf/controls/control-customization.md)
