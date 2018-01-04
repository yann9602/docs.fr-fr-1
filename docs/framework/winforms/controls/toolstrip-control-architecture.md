---
title: "Architecture du contrôle ToolStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b112cb1e383b092c1bcc4403e04938b3b83c5ecc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="toolstrip-control-architecture"></a>Architecture du contrôle ToolStrip
Le <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.ToolStripItem> classes fournissent un système flexible et extensible pour afficher des éléments de menu, l’état et la barre d’outils. Ces classes sont toutes contenues dans le <xref:System.Windows.Forms> espace de noms et ils sont généralement nommés avec le préfixe « ToolStrip » (tel que <xref:System.Windows.Forms.ToolStripOverflow>) ou le suffixe « Bande » (tel que <xref:System.Windows.Forms.MenuStrip>).  
  
## <a name="toolstrip"></a>ToolStrip  
 Les rubriques suivantes décrivent <xref:System.Windows.Forms.ToolStrip> et les contrôles qui en dérivent.  
  
 <xref:System.Windows.Forms.ToolStrip>est la classe de base abstraite pour <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, et <xref:System.Windows.Forms.ContextMenuStrip>. Modèle objet la suivant illustre la <xref:System.Windows.Forms.ToolStrip> hiérarchie d’héritage.  
  
 ![Modèle objet ToolStrip](../../../../docs/framework/winforms/controls/media/toolstripobjectmodel.gif "ToolStripObjectModel")  
Modèle objet ToolStrip  
  
 Vous pouvez accéder à tous les éléments dans un <xref:System.Windows.Forms.ToolStrip> via la <xref:System.Windows.Forms.ToolStrip.Items%2A> collection. Vous pouvez accéder à tous les éléments dans un <xref:System.Windows.Forms.ToolStripDropDownItem> via la <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> collection. Dans une classe dérivée de <xref:System.Windows.Forms.ToolStrip>, vous pouvez également utiliser le <xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A> propriété à accéder uniquement aux éléments qui sont actuellement affichés. Voici les éléments qui ne sont pas actuellement dans un menu de dépassement de capacité.  
  
 Les éléments suivants sont spécifiquement conçus pour fonctionner de manière transparente avec les deux <xref:System.Windows.Forms.ToolStripSystemRenderer> et <xref:System.Windows.Forms.ToolStripProfessionalRenderer> dans toutes les orientations. Ils sont disponibles par défaut au moment du design pour le <xref:System.Windows.Forms.ToolStrip> contrôle :  
  
-   <xref:System.Windows.Forms.ToolStripButton>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="menustrip"></a>MenuStrip  
 <xref:System.Windows.Forms.MenuStrip>est le conteneur de niveau supérieur qui remplace <xref:System.Windows.Forms.MainMenu>. Il fournit également la gestion des clés et document plusieurs fonctionnalités de l’interface (multidocument MDI). Point de vue fonctionnel, <xref:System.Windows.Forms.ToolStripDropDownItem> et <xref:System.Windows.Forms.ToolStripMenuItem> fonctionnent avec <xref:System.Windows.Forms.MenuStrip>, bien qu’ils sont dérivés de <xref:System.Windows.Forms.ToolStripItem>.  
  
 Les éléments suivants sont spécifiquement conçus pour fonctionner de manière transparente avec les deux <xref:System.Windows.Forms.ToolStripSystemRenderer> et <xref:System.Windows.Forms.ToolStripProfessionalRenderer> dans toutes les orientations. Ils sont disponibles par défaut au moment du design pour le <xref:System.Windows.Forms.MenuStrip> contrôle :  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="statusstrip"></a>StatusStrip  
 <xref:System.Windows.Forms.StatusStrip>remplace le <xref:System.Windows.Forms.StatusBar> contrôle. Les fonctionnalités spéciales du <xref:System.Windows.Forms.StatusStrip> incluent une disposition de table personnalisée, la prise en charge de l’écran de dimensionnement et de déplacement des poignées et le `Spring` propriété, ce qui permet une <xref:System.Windows.Forms.ToolStripStatusLabel> de remplir automatiquement l’espace disponible.  
  
 Les éléments suivants sont spécifiquement conçus pour fonctionner de manière transparente avec les deux <xref:System.Windows.Forms.ToolStripSystemRenderer> et <xref:System.Windows.Forms.ToolStripProfessionalRenderer> dans toutes les orientations. Ils sont disponibles par défaut au moment du design pour le <xref:System.Windows.Forms.StatusStrip> contrôle :  
  
-   <xref:System.Windows.Forms.ToolStripStatusLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripProgressBar>  
  
### <a name="contextmenustrip"></a>ContextMenuStrip  
 <xref:System.Windows.Forms.ContextMenuStrip>remplace <xref:System.Windows.Forms.ContextMenu>. Vous pouvez associer un <xref:System.Windows.Forms.ContextMenuStrip> avec n’importe quel contrôle et un droit de la souris cliquez automatiquement s’affiche dans le menu contextuel (ou le menu contextuel). Vous pouvez afficher un <xref:System.Windows.Forms.ContextMenuStrip> par programme en utilisant la <xref:System.Windows.Forms.ToolStripDropDown.Show%2A> (méthode). <xref:System.Windows.Forms.ContextMenuStrip>prend en charge annulable <xref:System.Windows.Forms.ToolStripDropDown.Opening> et <xref:System.Windows.Forms.ToolStripDropDown.Closing> événements pour gérer l’alimentation dynamique et cliquez plusieurs scénarios. <xref:System.Windows.Forms.ContextMenuStrip>prend en charge les images, élément de menu vérifier l’état, texte, clés d’accès, raccourcis et les menus en cascade.  
  
 Les éléments suivants sont spécifiquement conçus pour fonctionner de manière transparente avec les deux <xref:System.Windows.Forms.ToolStripSystemRenderer> et <xref:System.Windows.Forms.ToolStripProfessionalRenderer> dans toutes les orientations. Ils sont disponibles par défaut au moment du design pour le <xref:System.Windows.Forms.ContextMenuStrip> contrôle :  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="toolstrip-generic-features"></a>Fonctionnalités génériques de ToolStrip  
 Les rubriques suivantes décrivent les fonctionnalités et le comportement qui s’appliquent à la <xref:System.Windows.Forms.ToolStrip> et contrôles dérivés.  
  
#### <a name="painting"></a>Peinture  
 Vous pouvez effectuer une peinture personnalisée <xref:System.Windows.Forms.ToolStrip> contrôles de différentes manières. Comme avec d’autres contrôles Windows Forms, les <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.ToolStripItem> ont tous deux substituable `OnPaint` méthodes et `Paint` événements. Comme avec la peinture ordinaire, le système de coordonnées est relatif à la zone cliente du contrôle ; Autrement dit, l’angle supérieur gauche du contrôle est 0, 0. Le `Paint` événement et `OnPaint` méthode pour un <xref:System.Windows.Forms.ToolStripItem> se comportent comme les autres événements de peinture du contrôle.  
  
 Le <xref:System.Windows.Forms.ToolStrip> contrôles fournissent également un accès plus précis au rendu des éléments et du conteneur par le biais du <xref:System.Windows.Forms.ToolStripRenderer> (classe), qui a des méthodes substituables pour peindre l’arrière-plan arrière-plan de l’élément, élément image, flèche de l’élément, texte de l’élément et la bordure de la <xref:System.Windows.Forms.ToolStrip>. Les arguments d’événement pour ces méthodes exposent plusieurs propriétés telles que des rectangles, des couleurs et des formats de texte que vous pouvez ajuster selon vos besoins.  
  
 Pour ajuster uniquement quelques aspects de la peinture d’un élément, vous substituez en général la <xref:System.Windows.Forms.ToolStripRenderer>.  
  
 Si vous écrivez un nouvel élément et souhaitez contrôler tous les aspects de la peinture, substituez le `OnPaint` (méthode). Depuis `OnPaint`, vous pouvez utiliser les méthodes à partir de la <xref:System.Windows.Forms.ToolStripRenderer>.  
  
 Par défaut, le <xref:System.Windows.Forms.ToolStrip> double est mis en mémoire tampon, en tirant parti de le <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> paramètre.  
  
#### <a name="parenting"></a>Apparenter  
 Le concept de parentage et propriété de conteneur est plus complexe dans <xref:System.Windows.Forms.ToolStrip> contrôle que dans d’autres contrôles de conteneur Windows Forms. Qui est nécessaire pour prendre en charge des scénarios dynamiques de dépassement de capacité de partage des éléments déroulants entre plusieurs <xref:System.Windows.Forms.ToolStrip> éléments et pour prendre en charge la génération d’un <xref:System.Windows.Forms.ContextMenuStrip> à partir d’un contrôle.  
  
 La liste suivante décrit les membres associés au parentage et explique leur utilisation.  
  
-   <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A>accède à l’élément qui est la source de l’élément de liste déroulante. Cela revient à <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>, mais au lieu de retourner un contrôle, il retourne un <xref:System.Windows.Forms.ToolStripItem>.  
  
-   <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>Détermine le contrôle qui est la source de la <xref:System.Windows.Forms.ContextMenuStrip> lorsque plusieurs contrôles partagent le même <xref:System.Windows.Forms.ContextMenuStrip>.  
  
-   <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A>est un accesseur en lecture seule pour le <xref:System.Windows.Forms.ToolStripItem.Parent%2A> propriété. Un parent est différent d’un propriétaire dénote actuel retourné <xref:System.Windows.Forms.ToolStrip> dans lequel l’élément est affiché, qui peut être dans la zone de débordement.  
  
-   <xref:System.Windows.Forms.ToolStripItem.Owner%2A>Retourne le <xref:System.Windows.Forms.ToolStrip> dont la collection d’éléments contient actuel <xref:System.Windows.Forms.ToolStripItem>. C’est le meilleur moyen pour faire référence à <xref:System.Windows.Forms.ToolStrip.ImageList%2A> ou d’autres propriétés de niveau supérieur <xref:System.Windows.Forms.ToolStrip> sans écrire de code spécial pour gérer le dépassement de capacité.  
  
#### <a name="behavior-of-inherited-controls"></a>Comportement des contrôles hérités  
 Les contrôles suivants sont verrouillés chaque fois qu’ils sont utilisés dans l’héritage :  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.ToolStripPanel>qui inclut les panneaux dans un <xref:System.Windows.Forms.ToolStripContainer> et également individuelles <xref:System.Windows.Forms.ToolStripPanel> contrôles.  
  
 Par exemple, créer une application Windows Forms à l’aide d’un ou plusieurs des contrôles dans la liste précédente. Définir le modificateur d’accès d’un ou plusieurs contrôles à `public` ou `protected`, puis générez le projet. Ajoutez un formulaire qui hérite de la première forme, puis sélectionnez un contrôle hérité. Le contrôle apparaît verrouillé et se comporte comme si son modificateur d’accès a été `private`.  
  
#### <a name="toolstripcontainer-support-of-inheritance"></a>Prise en charge du ToolStripContainer d’héritage  
 Le <xref:System.Windows.Forms.ToolStripContainer> contrôle prend en charge des scénarios hérités limités, semblables à l’exemple suivant :  
  
1.  Créez une application Windows Forms.  
  
2.  Ajoutez un <xref:System.Windows.Forms.ToolStripContainer> au formulaire.  
  
3.  Définir le modificateur d’accès de la <xref:System.Windows.Forms.ToolStripContainer> à `public` ou `protected`.  
  
4.  Ajouter n’importe quelle combinaison de <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, et <xref:System.Windows.Forms.ContextMenuStrip> des contrôles à la <xref:System.Windows.Forms.ToolStripPanel> des régions de la <xref:System.Windows.Forms.ToolStripContainer>.  
  
5.  Générez le projet.  
  
6.  Ajoutez un formulaire qui hérite du premier formulaire.  
  
7.  Sélectionnez hérité <xref:System.Windows.Forms.ToolStripContainer> sur le formulaire.  
  
#### <a name="inherited-behavior-of-child-controls"></a>Comportement hérité des contrôles enfants  
 Après avoir effectué les étapes précédentes, le comportement hérité suivant se produit :  
  
-   Dans le concepteur, le contrôle s’affiche avec une icône héritée.  
  
-   Le <xref:System.Windows.Forms.ToolStripPanel> contrôles sont verrouillées ; vous ne pouvez pas sélectionner ou réorganiser leur contenu.  
  
-   Vous pouvez ajouter des contrôles à la <xref:System.Windows.Forms.ToolStripContentPanel>, déplacer les contrôles et faire des contrôles enfants de la <xref:System.Windows.Forms.ToolStripContentPanel>.  
  
-   Vos modifications sont conservées après la génération de l’écran.  
  
    > [!NOTE]
    >  Supprimez les modificateurs d’accès de tous les <xref:System.Windows.Forms.ToolStripPanel> contrôles qui font partie d’un <xref:System.Windows.Forms.ToolStripContainer>. Le modificateur d’accès de la <xref:System.Windows.Forms.ToolStripContainer> régit l’ensemble du contrôle.  
  
#### <a name="partial-trust"></a>Confiance partielle  
 Les limitations de `ToolStrip`sous confiance partielle sont conçues pour empêcher toute entrée inopportune d’informations personnelles qui pourraient être utilisées par des personnes non autorisées ou des services. Les mesures de protection sont les suivantes :  
  
-   `ToolStripDropDown`les contrôles requièrent <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> pour afficher les éléments dans un <xref:System.Windows.Forms.ToolStripControlHost>. Cela s’applique aux deux contrôles intrinsèques, tels que <xref:System.Windows.Forms.ToolStripTextBox>, <xref:System.Windows.Forms.ToolStripComboBox>, et <xref:System.Windows.Forms.ToolStripProgressBar> comme des contrôles et aux créés par l’utilisateur. Si cette condition n’est pas remplie, ces éléments ne sont pas affichés. Aucune exception n'est levée.  
  
-   Définition de la <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> propriété `false` n’est pas autorisée et l’annulable <xref:System.Windows.Forms.ToolStripDropDown.Closing> événement paramètre est ignoré. Cela rend impossible d’entrer plus d’une séquence de touches sans fermer l’élément de liste déroulante. Si cette condition n’est pas remplie, les éléments de ce type ne sont pas affichés. Aucune exception n'est levée.  
  
-   Séquence de touches de la gestion des événements n’est pas déclenchés s’ils se produisent dans des contextes de confiance partielle, autre que <xref:System.Security.Permissions.UIPermissionWindow.AllWindows>.  
  
-   Les clés d’accès ne sont pas traités lorsque <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> n’est pas accordée.  
  
#### <a name="usage"></a>Utilisation  
 Les modèles d’utilisation suivants ont une incidence sur <xref:System.Windows.Forms.ToolStrip> disposition, interaction du clavier et le comportement de l’utilisateur final :  
  
-   Joint à un<xref:System.Windows.Forms.ToolStripPanel>  
  
     Le <xref:System.Windows.Forms.ToolStrip> peut être repositionné dans le <xref:System.Windows.Forms.ToolStripPanel> et à travers <xref:System.Windows.Forms.ToolStripPanel>s. Le `Dock` propriété est ignorée et si le <xref:System.Windows.Forms.ToolStrip.Stretch%2A> propriété est `false`, la taille de la <xref:System.Windows.Forms.ToolStrip> augmente à mesure que les éléments sont ajoutés à la <xref:System.Windows.Forms.ToolStripPanel>. En règle générale, le <xref:System.Windows.Forms.ToolStrip> ne participe pas à l’ordre de tabulation.  
  
-   Ancré  
  
     Le <xref:System.Windows.Forms.ToolStrip> est placé sur un côté d’un conteneur dans une position fixe, et sa taille se développe sur l’intégralité du bord auquel il est ancré. En règle générale, le <xref:System.Windows.Forms.ToolStrip> ne participe pas à l’ordre de tabulation.  
  
-   Positionnement absolu  
  
     Le <xref:System.Windows.Forms.ToolStrip> est comme les autres contrôles, car elle est placée par le <xref:System.Windows.Forms.Control.Location%2A> propriété, a une taille fixe et participe en général à l’ordre de tabulation.  
  
#### <a name="keyboard-interaction"></a>Interaction du clavier  
  
##### <a name="access-keys"></a>Touches d’accès rapide  
 Combiné avec ou la touche ALT, les clés d’accès sont permettent d’activer un contrôle à l’aide du clavier. <xref:System.Windows.Forms.ToolStrip>prend en charge les deux clés d’accès explicites et implicites. Définition explicite utilise une esperluette (&) caractère précédant la lettre. Une définition implicite utilise un algorithme qui tente de trouver un élément correspondant basé sur l’ordre des caractères dans une donnée `Text` propriété.  
  
##### <a name="shortcut-keys"></a>Touches de raccourci  
 Les touches de raccourci utilisées par un <xref:System.Windows.Forms.MenuStrip> utilisent une combinaison de la <xref:System.Windows.Forms.Keys> énumération (qui n’est pas spécifique à une commande) pour définir la touche de raccourci. Vous pouvez également utiliser le <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> propriété pour afficher une touche de raccourci avec du texte uniquement, comme l’affichage « Del » au lieu de « Supprimer ».  
  
##### <a name="navigation"></a>Navigation  
 La touche ALT active le <xref:System.Windows.Forms.MenuStrip> vers lequel pointe <xref:System.Windows.Forms.Form.MainMenuStrip%2A>. À partir de là, CTRL + TAB navigue entre <xref:System.Windows.Forms.ToolStrip> des contrôles dans `ToolStripPanel`s. La touche TAB et les touches de direction sur le pavé numérique naviguer entre des éléments dans un <xref:System.Windows.Forms.ToolStrip>. Un algorithme spécial gère la navigation dans la région de dépassement de capacité. ESPACE sélectionne un <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, ou <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
##### <a name="focus-and-validation"></a>Le focus et Validation  
 Lors de l’activation par la touche ALT, la <xref:System.Windows.Forms.MenuStrip> ou <xref:System.Windows.Forms.ToolStrip> généralement ni prendre ni supprimer le focus du contrôle qui a actuellement le focus. Si un contrôle est hébergé dans le <xref:System.Windows.Forms.MenuStrip> ou une liste déroulante de la <xref:System.Windows.Forms.MenuStrip>, le contrôle obtient le focus lorsque l’utilisateur appuie sur la touche TAB. En général, les <xref:System.Windows.Forms.Control.GotFocus>, <xref:System.Windows.Forms.Control.LostFocus>, <xref:System.Windows.Forms.Control.Enter>, et <xref:System.Windows.Forms.Control.Leave> événements de <xref:System.Windows.Forms.MenuStrip> ne peuvent pas être déclenchés lorsqu’ils sont activés par le clavier. Dans ce cas, utilisez le <xref:System.Windows.Forms.MenuStrip.MenuActivate> et <xref:System.Windows.Forms.MenuStrip.MenuDeactivate> événements à la place.  
  
 Par défaut, <xref:System.Windows.Forms.ToolStrip.CausesValidation%2A> est `false`. Appelez <xref:System.Windows.Forms.ContainerControl.Validate%2A> explicitement sur votre formulaire pour effectuer la validation.  
  
#### <a name="layout"></a>Disposition  
 Vous contrôlez <xref:System.Windows.Forms.ToolStrip> mise en page en choisissant une des membres de <xref:System.Windows.Forms.ToolStripLayoutStyle> avec la <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> propriété.  
  
##### <a name="stack-layouts"></a>Dispositions de pile  
 L’empilement est réorganiser les éléments entre eux aux deux extrémités de la <xref:System.Windows.Forms.ToolStrip>. La liste suivante décrit les dispositions de pile.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow> est la valeur par défaut. Ce paramètre entraîne la <xref:System.Windows.Forms.ToolStrip> de modifier sa disposition automatiquement conformément à la <xref:System.Windows.Forms.ToolStrip.Orientation%2A> propriété pour gérer le déplacement et d’ancrage de scénarios.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>restitue le <xref:System.Windows.Forms.ToolStrip> verticalement les éléments entre eux.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow>restitue le <xref:System.Windows.Forms.ToolStrip> horizontalement les éléments entre eux.  
  
##### <a name="other-features-of-stack-layouts"></a>Autres fonctionnalités des dispositions de pile  
 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A>Détermine la fin de la <xref:System.Windows.Forms.ToolStrip> sur lequel l’élément est aligné.  
  
 Lorsque les éléments ne tiennent pas dans le <xref:System.Windows.Forms.ToolStrip>, un bouton de dépassement de capacité apparaît automatiquement. Le <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> propriété détermine si un élément apparaît dans la zone de dépassement de capacité, en fonction des besoins, jamais, ou toujours.  
  
 Dans le <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> événement, vous pouvez inspecter la <xref:System.Windows.Forms.ToolStripItem.Placement%2A> propriété pour déterminer si un élément a été placé sur le principal <xref:System.Windows.Forms.ToolStrip>, le dépassement de capacité <xref:System.Windows.Forms.ToolStrip>, ou si elle ne s’affiche pas du tout. Les raisons courantes pour lesquelles un élément n’est pas affiché sont que l’élément ne tiennent pas sur le principal <xref:System.Windows.Forms.ToolStrip> et son <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> a pris la valeur de propriété <xref:System.Windows.Forms.ToolStripItemOverflow.Never>.  
  
 Rendre un <xref:System.Windows.Forms.ToolStrip> mobile en le plaçant un <xref:System.Windows.Forms.ToolStripPanel> et en définissant son <xref:System.Windows.Forms.ToolStrip.GripStyle%2A> à <xref:System.Windows.Forms.ToolStripGripStyle.Visible>.  
  
##### <a name="other-layout-options"></a>Autres Options de disposition  
 Les autres options de mise en page sont <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> et <xref:System.Windows.Forms.ToolStripLayoutStyle.Table>.  
  
##### <a name="flow-layout"></a>Mise en page fluide  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>mise en forme est la valeur par défaut pour <xref:System.Windows.Forms.ContextMenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, et <xref:System.Windows.Forms.ToolStripOverflow>. Il est similaire à la <xref:System.Windows.Forms.FlowLayoutPanel>. Les fonctionnalités de <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> mise en page sont les suivantes :  
  
-   Toutes les fonctionnalités de <xref:System.Windows.Forms.FlowLayoutPanel> sont exposées par le <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> propriété. Vous devez caster le <xref:System.Windows.Forms.LayoutSettings> classe un <xref:System.Windows.Forms.FlowLayoutSettings> classe.  
  
-   Vous pouvez utiliser la <xref:System.Windows.Forms.ToolStripItem.Dock%2A> et <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> propriétés dans le code pour aligner les éléments dans la ligne.  
  
-   La propriété <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> est ignorée.  
  
-   Dans le <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> événement, vous pouvez inspecter la <xref:System.Windows.Forms.ToolStripItem.Placement%2A> propriété pour déterminer si un élément a été placé sur le principal <xref:System.Windows.Forms.ToolStrip> ou ne tiennent pas.  
  
-   La poignée n’est pas rendue et par conséquent un <xref:System.Windows.Forms.ToolStrip> dans <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> style de disposition dans un <xref:System.Windows.Forms.ToolStripPanel> ne peut pas être déplacé.  
  
-   Le <xref:System.Windows.Forms.ToolStrip> bouton de dépassement de capacité n’est pas rendu, et <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> est ignoré.  
  
##### <a name="table-layout"></a>Disposition de table  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Table>mise en forme est la valeur par défaut pour <xref:System.Windows.Forms.StatusStrip>. Il est similaire à <xref:System.Windows.Forms.TableLayoutPanel>. Les fonctionnalités de <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> mise en page sont les suivantes :  
  
-   Toutes les fonctionnalités de <xref:System.Windows.Forms.TableLayoutPanel> sont exposées par le <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> propriété. Vous devez caster le <xref:System.Windows.Forms.LayoutSettings> classe un <xref:System.Windows.Forms.TableLayoutSettings> classe.  
  
-   Vous pouvez utiliser la <xref:System.Windows.Forms.ToolStripItem.Dock%2A> et <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> propriétés dans le code pour aligner les éléments dans la cellule du tableau.  
  
-   La propriété <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> est ignorée.  
  
-   Dans le <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> événement, vous pouvez inspecter la <xref:System.Windows.Forms.ToolStripItem.Placement%2A> propriété pour déterminer si un élément a été placé sur le principal <xref:System.Windows.Forms.ToolStrip> ou ne tiennent pas.  
  
-   La poignée n’est pas rendue et par conséquent un <xref:System.Windows.Forms.ToolStrip> dans <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> style de disposition dans un <xref:System.Windows.Forms.ToolStripPanel> ne peut pas être déplacé.  
  
-   Le <xref:System.Windows.Forms.ToolStrip> bouton de dépassement de capacité n’est pas rendu, et <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> est ignoré.  
  
## <a name="toolstripitem"></a>ToolStripItem  
 Les rubriques suivantes décrivent <xref:System.Windows.Forms.ToolStripItem> et les contrôles qui en dérivent.  
  
 <xref:System.Windows.Forms.ToolStripItem>est la classe de base abstraite pour tous les éléments dans un <xref:System.Windows.Forms.ToolStrip>. Modèle objet la suivant illustre la <xref:System.Windows.Forms.ToolStripItem> hiérarchie d’héritage.  
  
 ![Modèle objet ToolStripItem](../../../../docs/framework/winforms/controls/media/toolstripitemobjectmodel.gif "ToolStripItemObjectModel")  
Modèle objet ToolStripItem  
  
 <xref:System.Windows.Forms.ToolStripItem>les classes qui héritent directement de <xref:System.Windows.Forms.ToolStripItem>, ou ils héritent indirectement <xref:System.Windows.Forms.ToolStripItem> via <xref:System.Windows.Forms.ToolStripControlHost> ou <xref:System.Windows.Forms.ToolStripDropDownItem>.  
  
 <xref:System.Windows.Forms.ToolStripItem>les contrôles doivent être contenus dans un <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, ou <xref:System.Windows.Forms.ContextMenuStrip> et ne peut pas être ajoutés directement à un formulaire. Les différentes classes de conteneur sont conçues pour contenir un sous-ensemble approprié de <xref:System.Windows.Forms.ToolStripItem> contrôles.  
  
 Le tableau suivant répertorie les actions <xref:System.Windows.Forms.ToolStripItem> contrôles et les conteneurs dans lesquels ils affichent meilleures. Bien que les <xref:System.Windows.Forms.ToolStrip> élément peut être hébergé dans toute <xref:System.Windows.Forms.ToolStrip>-dérivée de conteneur, ces éléments ont été conçus pour mieux dans les conteneurs suivants :  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripDropDown>n’apparaît pas dans la boîte à outils Concepteur.  
  
|Élément de contenu|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|  
|--------------------|---------------|---------------|----------------------|-----------------|-----------------------|  
|<xref:System.Windows.Forms.ToolStripButton>|Oui|Non|Non|Non|Oui|  
|<xref:System.Windows.Forms.ToolStripComboBox>|Oui|Oui|Oui|Non|Oui|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|Oui|Non|Non|Oui|Oui|  
|<xref:System.Windows.Forms.ToolStripLabel>|Oui|Non|Non|Oui|Oui|  
|<xref:System.Windows.Forms.ToolStripSeparator>|Oui|Oui|Oui|Non|Oui|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|Oui|Non|Non|Oui|Oui|  
|<xref:System.Windows.Forms.ToolStripTextBox>|Oui|Oui|Oui|Non|Oui|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Non|Oui|Oui|Non|Non|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|Non|Non|Non|Oui|Non|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|Oui|Non|Non|Oui|Non|  
|<xref:System.Windows.Forms.ToolStripControlHost>|Oui|Oui|Non|Oui|Oui|  
  
### <a name="toolstripbutton"></a>ToolStripButton  
 <xref:System.Windows.Forms.ToolStripButton>est l’élément de bouton pour <xref:System.Windows.Forms.ToolStrip>. Vous pouvez l’afficher avec différents styles de bordure, et vous pouvez l’utiliser pour représenter et activer des états opérationnels. Vous pouvez également définir comme ayant le focus par défaut.  
  
### <a name="toolstriplabel"></a>ToolStripLabel  
 Le <xref:System.Windows.Forms.ToolStripLabel> fournit des fonctionnalités d’étiquette dans <xref:System.Windows.Forms.ToolStrip> contrôles. Le <xref:System.Windows.Forms.ToolStripLabel> est similaire à un <xref:System.Windows.Forms.ToolStripButton> qui n’obtient pas le focus par défaut et qui n’effectue pas le rendu comme envoyées ou mis en surbrillance.  
  
 <xref:System.Windows.Forms.ToolStripLabel>en tant qu’élément hébergé prend en charge les clés d’accès.  
  
 Utilisez le <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>, et <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> propriétés sur un <xref:System.Windows.Forms.ToolStripLabel> pour prendre en charge le contrôle de lien dans un <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel  
 <xref:System.Windows.Forms.ToolStripStatusLabel>est une version de <xref:System.Windows.Forms.ToolStripLabel> conçu spécifiquement pour une utilisation dans <xref:System.Windows.Forms.StatusStrip>. Les fonctionnalités spéciales incluent <xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>, <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>, et <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>.  
  
### <a name="toolstripseparator"></a>ToolStripSeparator  
 Le <xref:System.Windows.Forms.ToolStripSeparator> ajoute une ligne verticale ou horizontale à une barre d’outils ou un menu, selon l’orientation. Il fournit la distinction entre des éléments, tels que ceux d’un menu ou regroupement de.  
  
 Vous pouvez ajouter un <xref:System.Windows.Forms.ToolStripSeparator> au moment du design en la sélectionnant dans la liste déroulante. Toutefois, vous pouvez également créer automatiquement un <xref:System.Windows.Forms.ToolStripSeparator> en tapant un trait d’union (-) dans le nœud de modèle du concepteur ou dans le <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> (méthode).  
  
### <a name="toolstripcontrolhost"></a>ToolStripControlHost  
 <xref:System.Windows.Forms.ToolStripControlHost>est la classe de base abstraite pour <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, et <xref:System.Windows.Forms.ToolStripProgressBar>. <xref:System.Windows.Forms.ToolStripControlHost>peut héberger d’autres contrôles, notamment les contrôles personnalisés, de deux manières :  
  
-   Construire un <xref:System.Windows.Forms.ToolStripControlHost> avec une classe qui dérive de <xref:System.Windows.Forms.Control>. Pour accéder pleinement au contrôle hébergé et les propriétés, vous devez caster le <xref:System.Windows.Forms.ToolStripControlHost.Control%2A> propriété à la classe qu’il représente.  
  
-   Étendre <xref:System.Windows.Forms.ToolStripControlHost>et dans le constructeur par défaut de la classe héritée, appelez le constructeur de classe de base en passant une classe qui dérive de <xref:System.Windows.Forms.Control>. Cette option permet d’encapsuler des méthodes de contrôle et des propriétés pour un accès facile dans un <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripcombobox"></a>ToolStripComboBox  
 <xref:System.Windows.Forms.ToolStripComboBox>est la <xref:System.Windows.Forms.ComboBox> optimisé pour l’hébergement dans un <xref:System.Windows.Forms.ToolStrip>. Un sous-ensemble de propriétés et les événements du contrôle hébergé est exposé à la <xref:System.Windows.Forms.ToolStripComboBox> niveau mais sous-jacent <xref:System.Windows.Forms.ComboBox> contrôle est accessible via la <xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A> propriété.  
  
### <a name="toolstriptextbox"></a>ToolStripTextBox  
 <xref:System.Windows.Forms.ToolStripTextBox>est la <xref:System.Windows.Forms.TextBox> optimisé pour l’hébergement dans un <xref:System.Windows.Forms.ToolStrip>. Un sous-ensemble de propriétés et les événements du contrôle hébergé est exposé à la <xref:System.Windows.Forms.ToolStripTextBox> niveau mais sous-jacent <xref:System.Windows.Forms.TextBox> contrôle est accessible via la <xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A> propriété.  
  
### <a name="toolstripprogressbar"></a>ToolStripProgressBar  
 <xref:System.Windows.Forms.ToolStripProgressBar>est la <xref:System.Windows.Forms.ProgressBar> optimisé pour l’hébergement dans un <xref:System.Windows.Forms.ToolStrip>. Un sous-ensemble de propriétés et les événements du contrôle hébergé est exposé à la <xref:System.Windows.Forms.ToolStripProgressBar> niveau mais sous-jacent <xref:System.Windows.Forms.ProgressBar> contrôle est accessible via la <xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A> propriété.  
  
### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem  
 <xref:System.Windows.Forms.ToolStripDropDownItem>est la classe de base abstraite pour <xref:System.Windows.Forms.ToolStripMenuItem>, <xref:System.Windows.Forms.ToolStripDropDownButton>, et <xref:System.Windows.Forms.ToolStripSplitButton>, qui peuvent héberger des éléments directement ou héberger des éléments supplémentaires dans un conteneur de liste déroulante. Ce faire, vous devez définir le <xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A> propriété un <xref:System.Windows.Forms.ToolStripDropDown> et en définissant le <xref:System.Windows.Forms.ToolStrip.Items%2A> propriété de la <xref:System.Windows.Forms.ToolStripDropDown>. Accéder à ces éléments de liste déroulante directement via le <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> propriété.  
  
### <a name="toolstripmenuitem"></a>ToolStripMenuItem  
 <xref:System.Windows.Forms.ToolStripMenuItem>est un <xref:System.Windows.Forms.ToolStripDropDownItem> qui fonctionne avec les <xref:System.Windows.Forms.ToolStripDropDownMenu> et <xref:System.Windows.Forms.ContextMenuStrip> pour gérer la disposition de la mise en surbrillance, la disposition et la colonne spéciale pour les menus.  
  
### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton  
 <xref:System.Windows.Forms.ToolStripDropDownButton>Il semble que <xref:System.Windows.Forms.ToolStripButton>, mais affiche une zone de liste déroulante lorsque l’utilisateur clique dessus. Masquer ou afficher la flèche de déroulement en définissant le <xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A> propriété. <xref:System.Windows.Forms.ToolStripDropDownButton>hôtes un <xref:System.Windows.Forms.ToolStripOverflowButton> qui affiche les éléments de dépassement de capacité du <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripsplitbutton"></a>ToolStripSplitButton  
 <xref:System.Windows.Forms.ToolStripSplitButton>combine un bouton et les fonctionnalités de bouton de liste déroulante.  
  
 Utilisez le <xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A> propriété pour synchroniser le <xref:System.Windows.Forms.Control.Click> événements de l’élément de liste déroulante choisi avec l’élément indiqué sur le bouton.  
  
### <a name="toolstripitem-generic-features"></a>Fonctionnalités génériques de ToolStripItem  
 <xref:System.Windows.Forms.ToolStripItem>fournit les options de l’héritage des contrôles et fonctionnalités génériques suivantes :  
  
-   Événements de base  
  
-   Gestion des images  
  
-   Alignement  
  
-   Relation entre le texte et image  
  
-   Style d’affichage  
  
#### <a name="core-events"></a>Événements de base  
 <xref:System.Windows.Forms.ToolStripItem>contrôles recevoir leurs propres cliquez, la souris et les événements de peinture et peuvent effectuer certains clavier prétraitement également.  
  
#### <a name="image-handling"></a>Gestion des images  
 Le <xref:System.Windows.Forms.ToolStripItem.Image%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageKey%2A>, et <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> propriétés relatives à divers aspects de la gestion des images. Utiliser des images dans <xref:System.Windows.Forms.ToolStrip> contrôles en définissant ces propriétés directement ou en définissant l’exécution-heure uniquement <xref:System.Windows.Forms.ToolStrip.ImageList%2A> propriété.  
  
 Mise à l’échelle de l’image est déterminé par l’interaction des propriétés dans les deux <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.ToolStripItem>, comme suit :  
  
-   <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A>échelle de l’image finale déterminée par la combinaison de l’image <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> paramètre et du conteneur <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> paramètre.  
  
    -   Si <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> est `true` (la valeur par défaut) et <xref:System.Windows.Forms.ToolStripItemImageScaling> est <xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>, aucune image mise à l’échelle se produit et le <xref:System.Windows.Forms.ToolStrip> taille est celle de l’élément de plus grande, ou une taille minimale recommandée.  
  
    -   Si <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> est `false` et <xref:System.Windows.Forms.ToolStripItemImageScaling> est <xref:System.Windows.Forms.ToolStripItemImageScaling.None>, aucune image ni <xref:System.Windows.Forms.ToolStrip> mise à l’échelle se produit.  
  
#### <a name="alignment"></a>Alignement  
 La valeur de la <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> propriété détermine la fin de la <xref:System.Windows.Forms.ToolStrip> à laquelle un élément apparaît. Le <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> propriété fonctionne uniquement lorsque le style de disposition du <xref:System.Windows.Forms.ToolStrip> est définie sur une des valeurs de dépassement de capacité de pile.  
  
 Les éléments sont placés sur le <xref:System.Windows.Forms.ToolStrip> dans l’ordre dans lequel les éléments apparaissent dans la collection d’éléments. Pour modifier par programmation dans lequel un élément est disposé, utilisez la <xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A> méthode pour déplacer l’élément dans la collection. Cette méthode déplace l’élément, mais n’existe pas déjà.  
  
#### <a name="text-and-image-relationship"></a>Texte et Image relation  
 Le <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> propriété définit le positionnement relatif de l’image en ce qui concerne le texte sur un <xref:System.Windows.Forms.ToolStripItem>. Les éléments qui ne disposent pas d’une image, text ou les deux sont traités comme des cas spéciaux afin que le <xref:System.Windows.Forms.ToolStripItem> n’affiche pas d’emplacement vide pour l’ou les éléments manquants.  
  
#### <a name="display-style"></a>Style d’affichage  
 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>vous permet de définir les valeurs des propriétés de texte et Image d’un élément lors de l’affichage que vous souhaitez. Cela est généralement utilisée pour modifier uniquement le style d’affichage lorsque montrant le même élément dans un contexte différent.  
  
## <a name="accessory-classes"></a>Classes d’accessoires  
 Les classes qui fournissent de nombreuses autres fonctionnalités incluent :  
  
-   <xref:System.Windows.Forms.ToolStripManager>prend en charge <xref:System.Windows.Forms.ToolStrip>-réalisation des tâches pour des applications entières, telles que les options de fusion, les paramètres et convertisseur.  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>vous permet d’appliquer un style ou thème particulier à un <xref:System.Windows.Forms.ToolStrip> facilement.  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer>crée des stylets et des pinceaux selon une table des couleurs remplaçable (<xref:System.Windows.Forms.ProfessionalColorTable>).  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer>applique des couleurs système et un style visuel en deux dimensions <xref:System.Windows.Forms.ToolStrip> applications.  
  
-   <xref:System.Windows.Forms.ToolStripContainer>est similaire à <xref:System.Windows.Forms.SplitContainer>. Il utilise quatre panneaux latéraux ancrés (instances de <xref:System.Windows.Forms.ToolStripPanel>) et un panneau central (une instance de <xref:System.Windows.Forms.ToolStripContentPanel>) pour créer une disposition classique. Vous ne pouvez pas supprimer les panneaux latéraux, mais vous pouvez les masquer. Vous ne pouvez ni supprimer ni masquer le panneau central. Vous pouvez réorganiser un ou plusieurs <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, ou <xref:System.Windows.Forms.StatusStrip> des contrôles dans les panneaux latéraux et vous pouvant utiliser le panneau central pour d’autres contrôles. Le <xref:System.Windows.Forms.ToolStripContentPanel> offre également un moyen pour obtenir un support technique de rendu dans le corps de votre formulaire pour une apparence cohérente. <xref:System.Windows.Forms.ToolStripContainer>ne prend pas en charge l’interface multidocument (MDI).  
  
-   <xref:System.Windows.Forms.ToolStripPanel>fournit un espace pour déplacer et réorganiser <xref:System.Windows.Forms.ToolStrip> contrôles. Vous pouvez utiliser qu’un seul panneau si vous le souhaitez, et <xref:System.Windows.Forms.ToolStripPanel> fonctionne bien dans les scénarios MDI.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Résumé de la technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)  
 [Contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [MenuStrip, contrôle](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [StatusStrip, contrôle](../../../../docs/framework/winforms/controls/statusstrip-control.md)  
 [ContextMenuStrip, contrôle](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)  
 [BindingNavigator, contrôle](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)
