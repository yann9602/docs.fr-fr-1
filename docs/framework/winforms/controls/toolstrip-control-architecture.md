---
title: "Architecture du contr&#244;le ToolStrip | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ToolStrip (contrôle Windows Forms), architecture"
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
caps.latest.revision: 32
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 32
---
# Architecture du contr&#244;le ToolStrip
Les classes <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.ToolStripItem> fournissent un système flexible et extensible pour afficher des éléments de barre d'outils, d'état et de menu.  Ces classes figurent toutes dans l'espace de noms <xref:System.Windows.Forms> et portent généralement le préfixe « ToolStrip » \(<xref:System.Windows.Forms.ToolStripOverflow>, par exemple\) ou le suffixe « Strip » \(<xref:System.Windows.Forms.MenuStrip>, par exemple\).  
  
## ToolStrip  
 Les rubriques suivantes décrivent le <xref:System.Windows.Forms.ToolStrip> et les contrôles qui en dérivent.  
  
 <xref:System.Windows.Forms.ToolStrip> est la classe de base abstraite de <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip> et <xref:System.Windows.Forms.ContextMenuStrip>.  Le modèle objet suivant illustre la hiérarchie d'héritage de <xref:System.Windows.Forms.ToolStrip>.  
  
 ![Modèle objet ToolStrip](../../../../docs/framework/winforms/controls/media/toolstripobjectmodel.png "ToolStripObjectModel")  
Modèle objet ToolStrip  
  
 Vous pouvez accéder à tous les éléments d'un contrôle <xref:System.Windows.Forms.ToolStrip> via la collection <xref:System.Windows.Forms.ToolStrip.Items%2A>.  Vous pouvez accéder à tous les éléments d'un contrôle <xref:System.Windows.Forms.ToolStripDropDownItem> via la collection <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A>.  Dans une classe dérivée de <xref:System.Windows.Forms.ToolStrip>, vous pouvez aussi utiliser la propriété <xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A> pour accéder uniquement aux éléments actuellement affichés.  Il s'agit des éléments qui ne figurent pas actuellement dans un menu de dépassement de capacité.  
  
 Les éléments suivants sont spécifiquement conçus pour fonctionner de façon transparente avec <xref:System.Windows.Forms.ToolStripSystemRenderer> et <xref:System.Windows.Forms.ToolStripProfessionalRenderer> dans toutes les orientations.  Ils sont disponibles par défaut au moment du design pour le contrôle <xref:System.Windows.Forms.ToolStrip> :  
  
-   <xref:System.Windows.Forms.ToolStripButton>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### MenuStrip  
 <xref:System.Windows.Forms.MenuStrip> est le conteneur de niveau supérieur qui remplace <xref:System.Windows.Forms.MainMenu>.  Il fournit également des fonctionnalités de gestion de clé et d'interface multidocument \(MDI, Multiple Document Interface\).  <xref:System.Windows.Forms.ToolStripDropDownItem> et <xref:System.Windows.Forms.ToolStripMenuItem> fonctionnent avec <xref:System.Windows.Forms.MenuStrip>, bien qu'ils soient dérivés de <xref:System.Windows.Forms.ToolStripItem>.  
  
 Les éléments suivants sont spécifiquement conçus pour fonctionner de façon transparente avec <xref:System.Windows.Forms.ToolStripSystemRenderer> et <xref:System.Windows.Forms.ToolStripProfessionalRenderer> dans toutes les orientations.  Ils sont disponibles par défaut au moment du design pour le contrôle <xref:System.Windows.Forms.MenuStrip> :  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### StatusStrip  
 <xref:System.Windows.Forms.StatusStrip> remplace le contrôle <xref:System.Windows.Forms.StatusBar>.  Les fonctionnalités spéciales de <xref:System.Windows.Forms.StatusStrip> incluent une disposition du tableau personnalisée, la prise en charge des poignées de dimensionnement et de déplacement du formulaire, et la propriété `Spring` qui permet à un <xref:System.Windows.Forms.ToolStripStatusLabel> de remplir automatiquement l'espace disponible.  
  
 Les éléments suivants sont spécifiquement conçus pour fonctionner de façon transparente avec <xref:System.Windows.Forms.ToolStripSystemRenderer> et <xref:System.Windows.Forms.ToolStripProfessionalRenderer> dans toutes les orientations.  Ils sont disponibles par défaut au moment du design pour le contrôle <xref:System.Windows.Forms.StatusStrip> :  
  
-   <xref:System.Windows.Forms.ToolStripStatusLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripProgressBar>  
  
### ContextMenuStrip  
 <xref:System.Windows.Forms.ContextMenuStrip> remplace <xref:System.Windows.Forms.ContextMenu>.  Vous pouvez associer un <xref:System.Windows.Forms.ContextMenuStrip> à tout contrôle, et un clic droit affiche automatiquement le menu contextuel.  Vous pouvez également afficher un <xref:System.Windows.Forms.ContextMenuStrip> par programmation à l'aide de la méthode <xref:System.Windows.Forms.ToolStripDropDown.Show%2A>.  <xref:System.Windows.Forms.ContextMenuStrip> prend en charge les événements annulables <xref:System.Windows.Forms.ToolStripDropDown.Opening> et <xref:System.Windows.Forms.ToolStripDropDown.Closing> pour gérer les scénarios de remplissage dynamique et de clics multiples.  <xref:System.Windows.Forms.ContextMenuStrip> prend en charge les images, l'état d'activation des éléments de menu, le texte, les touches d'accès rapide, les raccourcis et les menus en cascade.  
  
 Les éléments suivants sont spécifiquement conçus pour fonctionner de façon transparente avec <xref:System.Windows.Forms.ToolStripSystemRenderer> et <xref:System.Windows.Forms.ToolStripProfessionalRenderer> dans toutes les orientations.  Ils sont disponibles par défaut au moment du design pour le contrôle <xref:System.Windows.Forms.ContextMenuStrip> :  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### Fonctionnalités génériques de ToolStrip  
 Les rubriques suivantes décrivent les fonctionnalités et le comportement qui sont génériques aux <xref:System.Windows.Forms.ToolStrip> et contrôles dérivés.  
  
#### Peinture  
 Vous pouvez appliquer une peinture personnalisée aux contrôles <xref:System.Windows.Forms.ToolStrip> de plusieurs façons.  Comme avec d'autres contrôles Windows Forms, les <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.ToolStripItem> ont tous deux des méthodes `OnPaint` et des événements `Paint` substituables.  Comme avec la peinture ordinaire, le système de coordonnées est relatif à la zone cliente du contrôle ; en d'autres termes, l'angle supérieur gauche du contrôle a pour coordonnées 0, 0.  L'événement `Paint` et la méthode `OnPaint` d'un <xref:System.Windows.Forms.ToolStripItem> se comportent comme d'autres événements de peinture de contrôle.  
  
 Les contrôles <xref:System.Windows.Forms.ToolStrip> fournissent également un accès plus précis au rendu des éléments et du conteneur par le biais de la classe <xref:System.Windows.Forms.ToolStripRenderer>, qui a des méthodes substituables pour peindre l'arrière\-plan, l'arrière\-plan de l'élément, l'image de l'élément, la flèche de l'élément, le texte de l'élément et la bordure du <xref:System.Windows.Forms.ToolStrip>.  Les arguments d'événement pour ces méthodes exposent plusieurs propriétés, telles que des rectangles, couleurs et formats de texte que vous pouvez ajuster en fonction de vos souhaits.  
  
 Pour ajuster uniquement quelques aspects de la façon dont un élément est peint, vous substituez en général la <xref:System.Windows.Forms.ToolStripRenderer>.  
  
 Si vous écrivez un nouvel élément et souhaitez contrôler tous les aspects de la peinture, substituez la méthode `OnPaint`.  À partir de `OnPaint`, vous pouvez utiliser des méthodes de la <xref:System.Windows.Forms.ToolStripRenderer>.  
  
 Par défaut, le <xref:System.Windows.Forms.ToolStrip> fait l'objet d'une double mise en mémoire tampon, en tirant parti du paramètre <xref:System.Windows.Forms.ControlStyles>.  
  
#### Parentage  
 Le concept de parentage et propriété de conteneur est plus complexe dans les contrôles <xref:System.Windows.Forms.ToolStrip> que dans d'autres contrôles conteneur Windows Forms.  Cela est nécessaire pour prendre en charge des scénarios dynamiques, tels que le dépassement de capacité, le partage des éléments déroulants entre plusieurs éléments <xref:System.Windows.Forms.ToolStrip>, et pour prendre en charge la génération d'un <xref:System.Windows.Forms.ContextMenuStrip> à partir d'un contrôle.  
  
 La liste suivante décrit des membres associés au parentage et leur utilisation.  
  
-   <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A> accède à l'élément qui est la source de l'élément déroulant.  Il est semblable à <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>, mais retourne un <xref:System.Windows.Forms.ToolStripItem> au lieu d'un contrôle.  
  
-   <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A> détermine le contrôle qui est la source du <xref:System.Windows.Forms.ContextMenuStrip> lorsque plusieurs contrôles partagent le même <xref:System.Windows.Forms.ContextMenuStrip>.  
  
-   <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A> est un accesseur en lecture seule à la propriété <xref:System.Windows.Forms.ToolStripItem.Parent%2A>.  Un parent est différent d'un propriétaire, car il dénote le <xref:System.Windows.Forms.ToolStrip> actuel retourné dans lequel l'élément est affiché, qui peut se trouver dans la zone de débordement.  
  
-   <xref:System.Windows.Forms.ToolStripItem.Owner%2A> retourne le <xref:System.Windows.Forms.ToolStrip> dont la collection Items contient le <xref:System.Windows.Forms.ToolStripItem> actuel.  Il s'agit de la meilleure façon de référencer <xref:System.Windows.Forms.ToolStrip.ImageList%2A> ou d'autres propriétés dans le <xref:System.Windows.Forms.ToolStrip> de niveau supérieur sans écrire de code spécial pour gérer le dépassement de capacité.  
  
#### Comportement des contrôles hérités  
 Les contrôles suivants sont verrouillés chaque fois qu'ils sont utilisés en héritage :  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.ToolStripPanel> qui inclut les panneaux dans un <xref:System.Windows.Forms.ToolStripContainer> et également des contrôles <xref:System.Windows.Forms.ToolStripPanel> individuels.  
  
 Par exemple, créez une application Windows Forms en utilisant un ou plusieurs des contrôles de la liste précédente.  Affectez au modificateur d'accès d'un ou de plusieurs contrôles la valeur `public` ou `protected`, puis générez le projet.  Ajoutez un formulaire qui hérite du premier formulaire, puis sélectionnez un contrôle hérité.  Le contrôle apparaît verrouillé et se comporte comme si son modificateur d'accès avait la valeur `private`.  
  
#### Prise en charge de l'héritage par ToolStripContainer  
 Le contrôle <xref:System.Windows.Forms.ToolStripContainer> prend en charge des scénarios hérités limités, semblables à l'exemple suivant :  
  
1.  Créer une nouvelle application Windows Forms.  
  
2.  Ajoutez <xref:System.Windows.Forms.ToolStripContainer> au formulaire.  
  
3.  Affectez au modificateur d'accès du <xref:System.Windows.Forms.ToolStripContainer> la valeur `public` ou `protected`.  
  
4.  Ajoutez toute combinaison de contrôles <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.ContextMenuStrip> aux régions <xref:System.Windows.Forms.ToolStripPanel> du <xref:System.Windows.Forms.ToolStripContainer>.  
  
5.  Générez le projet.  
  
6.  Ajoutez un formulaire qui hérite du premier formulaire.  
  
7.  Sélectionnez le <xref:System.Windows.Forms.ToolStripContainer> hérité sur le formulaire.  
  
#### Comportement hérité des contrôles enfants  
 Après avoir effectué la procédure précédente, le comportement hérité suivant se produit :  
  
-   Dans le concepteur, le contrôle apparaît avec une icône héritée.  
  
-   Les contrôles <xref:System.Windows.Forms.ToolStripPanel> sont verrouillés ; vous ne pouvez pas sélectionner ni réordonner leur contenu.  
  
-   Vous pouvez ajouter des contrôles au <xref:System.Windows.Forms.ToolStripContentPanel>, déplacer les contrôles et en faire des contrôles enfants du <xref:System.Windows.Forms.ToolStripContentPanel>.  
  
-   Vos modifications sont conservées après avoir généré le formulaire.  
  
    > [!NOTE]
    >  Supprimez les modificateurs d'accès de tous les contrôles <xref:System.Windows.Forms.ToolStripPanel> qui font partie d'un <xref:System.Windows.Forms.ToolStripContainer>.  Le modificateur d'accès du <xref:System.Windows.Forms.ToolStripContainer> gouverne l'intégralité du contrôle.  
  
#### Confiance partielle  
 Les limitations des `ToolStrip` sous confiance partielle sont conçues pour empêcher toute entrée inopportune d'informations personnelles qui peuvent être utilisées par des personnes ou services non autorisés.  Les mesures de protection sont les suivantes :  
  
-   Les contrôles `ToolStripDropDown` requièrent <xref:System.Security.Permissions.UIPermissionWindow> pour afficher des éléments dans un <xref:System.Windows.Forms.ToolStripControlHost>.  Cela s'applique à la fois aux contrôles intrinsèques, tels que <xref:System.Windows.Forms.ToolStripTextBox>, <xref:System.Windows.Forms.ToolStripComboBox> et <xref:System.Windows.Forms.ToolStripProgressBar>, et aux contrôles créés par l'utilisateur.  Si cette spécification n'est pas satisfaite, ces éléments ne sont pas affichés.  Aucune exception n'est levée.  
  
-   L'affectation à la propriété <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> de la valeur `false` n'est pas autorisée, et le paramètre d'événement <xref:System.Windows.Forms.ToolStripDropDown.Closing> annulable est ignoré.  Il est donc impossible d'entrer plusieurs séquences de touches sans fermer l'élément déroulant.  Si cette spécification n'est pas satisfaite, ces éléments ne sont pas affichés.  Aucune exception n'est levée.  
  
-   De nombreux événements de gestion de séquences de touches ne seront pas déclenchés s'ils se produisent dans des contextes de confiance partielle autres que <xref:System.Security.Permissions.UIPermissionWindow>.  
  
-   Les touches d'accès rapide ne sont pas traitées lorsque <xref:System.Security.Permissions.UIPermissionWindow> n'est pas accordé.  
  
#### Utilisation  
 Les modèles d'utilisation suivants ont une incidence sur la disposition du <xref:System.Windows.Forms.ToolStrip>, l'interaction du clavier et le comportement d'utilisateur final :  
  
-   Joint dans un <xref:System.Windows.Forms.ToolStripPanel>  
  
     Le <xref:System.Windows.Forms.ToolStrip> peut être repositionné dans le <xref:System.Windows.Forms.ToolStripPanel> et dans les <xref:System.Windows.Forms.ToolStripPanel>.  La propriété `Dock` est ignorée, et si la propriété <xref:System.Windows.Forms.ToolStrip.Stretch%2A> a la valeur `false`, la taille du <xref:System.Windows.Forms.ToolStrip> augmente au fur et à mesure que des éléments sont ajoutés à <xref:System.Windows.Forms.ToolStripPanel>.  En général, le <xref:System.Windows.Forms.ToolStrip> ne participe pas à l'ordre de tabulation.  
  
-   Ancré  
  
     Le <xref:System.Windows.Forms.ToolStrip> est placé d'un côté d'un conteneur dans une position fixe, et sa taille se développe sur l'intégralité du bord auquel il est ancré.  En général, le <xref:System.Windows.Forms.ToolStrip> ne participe pas à l'ordre de tabulation.  
  
-   Position absolue  
  
     Le <xref:System.Windows.Forms.ToolStrip> est semblable à d'autres contrôles, dans le sens où il est placé par la propriété <xref:System.Windows.Forms.Control.Location%2A>, a une taille fixe et participe en général à l'ordre de tabulation.  
  
#### Interaction du clavier  
  
##### Touches d'accès rapide  
 Combinées avec la touche ALT ou à sa suite, les touches d'accès rapide permettent d'activer un contrôle à l'aide du clavier.  <xref:System.Windows.Forms.ToolStrip> prend en charge les touches d'accès rapide explicites et implicites.  Une définition explicite utilise un caractère & \(et commercial\) avant la lettre.  Une définition implicite utilise un algorithme qui essaie de trouver un élément correspondant basé sur l'ordre des caractères dans une propriété `Text` donnée.  
  
##### Touches de raccourci  
 Les touches de raccourci utilisées par un <xref:System.Windows.Forms.MenuStrip> emploient une combinaison de l'énumération <xref:System.Windows.Forms.Keys> \(qui n'est pas spécifique à l'ordre\) pour définir la touche de raccourci.  Vous pouvez également utiliser la propriété <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> pour afficher une touche de raccourci avec uniquement du texte, tel que l'affichage de « Suppr » au lieu de « Supprimer ».  
  
##### Navigation  
 La touche ALT active le <xref:System.Windows.Forms.MenuStrip> sur lequel <xref:System.Windows.Forms.Form.MainMenuStrip%2A> pointe.  Ensuite, CTRL\+TAB permet de naviguer d'un contrôle <xref:System.Windows.Forms.ToolStrip> à l'autre dans les `ToolStripPanel`s.  La touche de tabulation et les touches de direction du pavé numérique permettent de naviguer d'un élément à l'autre dans un <xref:System.Windows.Forms.ToolStrip>.  Un algorithme spécial gère la navigation dans la région de dépassement de capacité.  ESPACE sélectionne un <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton> ou <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
##### Focus et validation  
 En cas d'activation par la touche ALT, le <xref:System.Windows.Forms.MenuStrip> ou <xref:System.Windows.Forms.ToolStrip> ne prend ni ne supprime en général le focus du contrôle qui a actuellement le focus.  Si un contrôle est hébergé dans <xref:System.Windows.Forms.MenuStrip> ou un élément déroulant de <xref:System.Windows.Forms.MenuStrip>, le contrôle obtient le focus lorsque l'utilisateur appuie sur la touche TAB.  En général, les événements <xref:System.Windows.Forms.Control.GotFocus>, <xref:System.Windows.Forms.Control.LostFocus>, <xref:System.Windows.Forms.Control.Enter> et <xref:System.Windows.Forms.Control.Leave> de <xref:System.Windows.Forms.MenuStrip> peuvent ne pas être déclenchés lorsqu'ils sont activés par le clavier.  Dans de tels cas, utilisez à la place les événements <xref:System.Windows.Forms.MenuStrip.MenuActivate> et <xref:System.Windows.Forms.MenuStrip.MenuDeactivate>.  
  
 Par défaut, <xref:System.Windows.Forms.ToolStrip.CausesValidation%2A> a la valeur `false`.  Appelez <xref:System.Windows.Forms.ContainerControl.Validate%2A> explicitement sur votre formulaire pour effectuer la validation.  
  
#### Disposition  
 Vous contrôlez la disposition <xref:System.Windows.Forms.ToolStrip> en choisissant l'un des membres de <xref:System.Windows.Forms.ToolStripLayoutStyle> avec la propriété <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>.  
  
##### Dispositions de pile  
 L'empilement est une action qui consiste à réorganiser les éléments entre eux aux deux extrémités de <xref:System.Windows.Forms.ToolStrip>.  La liste suivante décrit les dispositions de pile.  
  
-   La valeur par défaut est <xref:System.Windows.Forms.ToolStripLayoutStyle>.  Ce paramètre oblige <xref:System.Windows.Forms.ToolStrip> à altérer automatiquement sa disposition en conformité avec la propriété <xref:System.Windows.Forms.ToolStrip.Orientation%2A> afin de gérer les scénarios de déplacement et d'ancrage.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle> effectue un rendu des éléments <xref:System.Windows.Forms.ToolStrip> entre eux selon une disposition verticale.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle> effectue un rendu des éléments <xref:System.Windows.Forms.ToolStrip> entre eux selon une disposition horizontale.  
  
##### Autres fonctionnalités des dispositions de pile  
 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> détermine la fin du <xref:System.Windows.Forms.ToolStrip> en fonction duquel l'élément est aligné.  
  
 Lorsque des éléments ne peuvent pas être contenus dans <xref:System.Windows.Forms.ToolStrip>, un bouton de dépassement de capacité apparaît automatiquement.  Le paramètre de propriété <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> détermine si un élément apparaît systématiquement, autant que nécessaire ou jamais dans la zone de dépassement de capacité.  
  
 Dans l'événement <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>, vous pouvez inspecter la propriété <xref:System.Windows.Forms.ToolStripItem.Placement%2A> pour déterminer si un élément est placé dans le <xref:System.Windows.Forms.ToolStrip> principal, le <xref:System.Windows.Forms.ToolStrip> de dépassement de capacité, ou s'il ne s'affiche pas du tout.  Les raisons classiques pour lesquelles un élément n'est pas affiché sont que l'élément ne tenait pas dans le <xref:System.Windows.Forms.ToolStrip> principal et que sa propriété <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> avait la valeur <xref:System.Windows.Forms.ToolStripItemOverflow>.  
  
 Rendez un <xref:System.Windows.Forms.ToolStrip> mobile en le plaçant dans <xref:System.Windows.Forms.ToolStripPanel> et en affectant la valeur <xref:System.Windows.Forms.ToolStripGripStyle> à <xref:System.Windows.Forms.ToolStrip.GripStyle%2A>.  
  
##### Autres options de disposition  
 Les autres options de disposition sont <xref:System.Windows.Forms.ToolStripLayoutStyle> et <xref:System.Windows.Forms.ToolStripLayoutStyle>.  
  
##### Mise en page fluide  
 La disposition <xref:System.Windows.Forms.ToolStripLayoutStyle> est la valeur par défaut pour <xref:System.Windows.Forms.ContextMenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu> et <xref:System.Windows.Forms.ToolStripOverflow>.  Elle est semblable à <xref:System.Windows.Forms.FlowLayoutPanel>.  Les fonctionnalités de la disposition <xref:System.Windows.Forms.ToolStripLayoutStyle> sont les suivantes :  
  
-   Toutes les fonctionnalités de <xref:System.Windows.Forms.FlowLayoutPanel> sont exposées par la propriété <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>.  Vous devez effectuer un cast de la classe <xref:System.Windows.Forms.LayoutSettings> en une classe <xref:System.Windows.Forms.FlowLayoutSettings>.  
  
-   Vous pouvez utiliser les propriétés <xref:System.Windows.Forms.ToolStripItem.Dock%2A> et <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> dans du code pour aligner les éléments dans la ligne.  
  
-   La propriété <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> est ignorée.  
  
-   Dans l'événement <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>, vous pouvez inspecter la propriété <xref:System.Windows.Forms.ToolStripItem.Placement%2A> pour déterminer si un élément est placé dans le <xref:System.Windows.Forms.ToolStrip> principal, ou s'il ne peut pas être contenu.  
  
-   La poignée n'est pas rendue ; par conséquent, un <xref:System.Windows.Forms.ToolStrip> en style de disposition <xref:System.Windows.Forms.ToolStripLayoutStyle> dans <xref:System.Windows.Forms.ToolStripPanel> ne peut pas être déplacé.  
  
-   Le bouton de dépassement de capacité <xref:System.Windows.Forms.ToolStrip> n'est pas restitué et <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> est ignoré.  
  
##### Présentation tabulaire  
 La disposition <xref:System.Windows.Forms.ToolStripLayoutStyle> est la valeur par défaut pour <xref:System.Windows.Forms.StatusStrip>.  Elle est semblable à <xref:System.Windows.Forms.TableLayoutPanel>.  Les fonctionnalités de la disposition <xref:System.Windows.Forms.ToolStripLayoutStyle> sont les suivantes :  
  
-   Toutes les fonctionnalités de <xref:System.Windows.Forms.TableLayoutPanel> sont exposées par la propriété <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>.  Vous devez effectuer un cast de la classe <xref:System.Windows.Forms.LayoutSettings> en une classe <xref:System.Windows.Forms.TableLayoutSettings>.  
  
-   Vous pouvez utiliser les propriétés <xref:System.Windows.Forms.ToolStripItem.Dock%2A> et <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> dans du code pour aligner les éléments dans la cellule de tableau.  
  
-   La propriété <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> est ignorée.  
  
-   Dans l'événement <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>, vous pouvez inspecter la propriété <xref:System.Windows.Forms.ToolStripItem.Placement%2A> pour déterminer si un élément est placé dans le <xref:System.Windows.Forms.ToolStrip> principal, ou s'il ne peut pas être contenu.  
  
-   La poignée n'est pas restituée et, par conséquent, un <xref:System.Windows.Forms.ToolStrip> dans le style de disposition <xref:System.Windows.Forms.ToolStripLayoutStyle> d'un <xref:System.Windows.Forms.ToolStripPanel> ne peut pas être déplacé.  
  
-   Le bouton de dépassement de capacité <xref:System.Windows.Forms.ToolStrip> n'est pas restitué et <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> est ignoré.  
  
## ToolStripItem  
 Les rubriques suivantes décrivent le <xref:System.Windows.Forms.ToolStripItem> et les contrôles qui en dérivent.  
  
 <xref:System.Windows.Forms.ToolStripItem> est la classe de base abstraite pour tous les éléments qui intègrent un <xref:System.Windows.Forms.ToolStrip>.  Le modèle objet suivant illustre la hiérarchie d'héritage de <xref:System.Windows.Forms.ToolStripItem>.  
  
 ![Modèle objet ToolStripItem](../../../../docs/framework/winforms/controls/media/toolstripitemobjectmodel.png "ToolStripItemObjectModel")  
Modèle objet ToolStripItem  
  
 Les classes <xref:System.Windows.Forms.ToolStripItem> héritent directement de <xref:System.Windows.Forms.ToolStripItem> ou indirectement de <xref:System.Windows.Forms.ToolStripItem> par le biais de <xref:System.Windows.Forms.ToolStripControlHost> ou <xref:System.Windows.Forms.ToolStripDropDownItem>.  
  
 Les contrôles <xref:System.Windows.Forms.ToolStripItem> doivent être contenus dans <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip> ou <xref:System.Windows.Forms.ContextMenuStrip> et ne peuvent pas être ajoutés directement à un formulaire.  Les différentes classes de conteneur sont conçues pour contenir un sous\-ensemble approprié de contrôles <xref:System.Windows.Forms.ToolStripItem>.  
  
 Le tableau suivant répertorie les contrôles <xref:System.Windows.Forms.ToolStripItem> stock et les conteneurs dans lesquels ils s'affichent de façon optimale.  Bien que les éléments <xref:System.Windows.Forms.ToolStrip> puissent être hébergés dans tout conteneur dérivé de <xref:System.Windows.Forms.ToolStrip>, ces éléments ont été conçus de façon à s'afficher de façon optimale dans les conteneurs suivants :  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripDropDown> n'apparaît pas dans la boîte à outils du concepteur.  
  
|Élément inclus|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|  
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
  
### ToolStripButton  
 <xref:System.Windows.Forms.ToolStripButton> est l'élément de bouton pour <xref:System.Windows.Forms.ToolStrip>.  Vous pouvez l'afficher avec différents styles de bordure et l'utiliser pour représenter et activer des états opérationnels.  Vous pouvez également le définir comme ayant le focus par défaut.  
  
### ToolStripLabel  
 Le <xref:System.Windows.Forms.ToolStripLabel> fournit des fonctionnalités d'étiquette dans les contrôles <xref:System.Windows.Forms.ToolStrip>.  Le <xref:System.Windows.Forms.ToolStripLabel> est comme un <xref:System.Windows.Forms.ToolStripButton> qui n'obtient pas le focus par défaut et qui n'est pas restitué comme faisant l'objet d'un push ou en surbrillance.  
  
 <xref:System.Windows.Forms.ToolStripLabel> en tant qu'élément hébergé prend en charge les touches d'accès rapide.  
  
 Utilisez les propriétés <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> et <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> sur un <xref:System.Windows.Forms.ToolStripLabel> pour prendre en charge le contrôle de liaison dans un <xref:System.Windows.Forms.ToolStrip>.  
  
### ToolStripStatusLabel  
 <xref:System.Windows.Forms.ToolStripStatusLabel> est une version de <xref:System.Windows.Forms.ToolStripLabel> conçue spécifiquement pour une utilisation dans <xref:System.Windows.Forms.StatusStrip>.  Les fonctionnalités spéciales comprennent <xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>, <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A> et <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>.  
  
### ToolStripSeparator  
 <xref:System.Windows.Forms.ToolStripSeparator> ajoute une ligne verticale ou horizontale à une barre d'outils ou à un menu, selon l'orientation.  Il fournit le regroupement des éléments ou la distinction entre ceux\-ci, par exemple les éléments d'un menu.  
  
 Vous pouvez ajouter un <xref:System.Windows.Forms.ToolStripSeparator> au moment du design en le choisissant dans une liste déroulante.  Toutefois, vous pouvez également créer automatiquement un <xref:System.Windows.Forms.ToolStripSeparator> en tapant un trait d'union \(\-\) dans le nœud de modèle du concepteur ou dans la méthode <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A>.  
  
### ToolStripControlHost  
 <xref:System.Windows.Forms.ToolStripControlHost> est la classe de base abstraite de <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox> et <xref:System.Windows.Forms.ToolStripProgressBar>.  <xref:System.Windows.Forms.ToolStripControlHost> peut héberger d'autres contrôles, notamment les contrôles personnalisés, de deux façons :  
  
-   Construisez <xref:System.Windows.Forms.ToolStripControlHost> avec une classe qui dérive de <xref:System.Windows.Forms.Control>.  Pour accéder pleinement au contrôle hébergé et aux propriétés, vous devez effectuer un cast de la propriété <xref:System.Windows.Forms.ToolStripControlHost.Control%2A> en une classe réelle qu'elle représente.  
  
-   Étendez <xref:System.Windows.Forms.ToolStripControlHost>, et dans le constructeur par défaut de la classe héritée, appelez le constructeur de classe de base en passant une classe qui dérive de <xref:System.Windows.Forms.Control>.  Cette option permet d'encapsuler des méthodes de contrôle et des propriétés communes facilitant l'accès à <xref:System.Windows.Forms.ToolStrip>.  
  
### ToolStripComboBox  
 <xref:System.Windows.Forms.ToolStripComboBox> est le <xref:System.Windows.Forms.ComboBox> optimisé pour l'hébergement dans un <xref:System.Windows.Forms.ToolStrip>.  Un sous\-ensemble des événements et des propriétés du contrôle hébergé est exposé au niveau <xref:System.Windows.Forms.ToolStripComboBox>, mais le contrôle <xref:System.Windows.Forms.ComboBox> sous\-jacent est accessible via la propriété <xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A>.  
  
### ToolStripTextBox  
 <xref:System.Windows.Forms.ToolStripTextBox> est le <xref:System.Windows.Forms.TextBox> optimisé pour l'hébergement dans un <xref:System.Windows.Forms.ToolStrip>.  Un sous\-ensemble des événements et des propriétés du contrôle hébergé est exposé au niveau <xref:System.Windows.Forms.ToolStripTextBox>, mais le contrôle <xref:System.Windows.Forms.TextBox> sous\-jacent est accessible via la propriété <xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A>.  
  
### ToolStripProgressBar  
 <xref:System.Windows.Forms.ToolStripProgressBar> est le <xref:System.Windows.Forms.ProgressBar> optimisé pour l'hébergement dans un <xref:System.Windows.Forms.ToolStrip>.  Un sous\-ensemble des événements et des propriétés du contrôle hébergé est exposé au niveau <xref:System.Windows.Forms.ToolStripProgressBar>, mais le contrôle <xref:System.Windows.Forms.ProgressBar> sous\-jacent est accessible via la propriété <xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A>.  
  
### ToolStripDropDownItem  
 <xref:System.Windows.Forms.ToolStripDropDownItem> est la classe de base abstraite pour <xref:System.Windows.Forms.ToolStripMenuItem>, <xref:System.Windows.Forms.ToolStripDropDownButton> et <xref:System.Windows.Forms.ToolStripSplitButton>, qui peuvent héberger des éléments directement ou héberger des éléments supplémentaires dans un conteneur déroulant.  Pour ce faire, affectez <xref:System.Windows.Forms.ToolStripDropDown> à la propriété <xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A> et définissez la propriété <xref:System.Windows.Forms.ToolStrip.Items%2A> de <xref:System.Windows.Forms.ToolStripDropDown>.  Accédez directement à ces éléments déroulants par le biais de la propriété <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A>.  
  
### ToolStripMenuItem  
 <xref:System.Windows.Forms.ToolStripMenuItem> est un <xref:System.Windows.Forms.ToolStripDropDownItem> qui fonctionne avec <xref:System.Windows.Forms.ToolStripDropDownMenu> et <xref:System.Windows.Forms.ContextMenuStrip> pour gérer la mise en surbrillance spéciale, la disposition et la disposition des colonnes pour les menus.  
  
### ToolStripDropDownButton  
 <xref:System.Windows.Forms.ToolStripDropDownButton> ressemble à <xref:System.Windows.Forms.ToolStripButton>, mais affiche une zone déroulante lorsque l'utilisateur clique dessus.  Masquez ou affichez la flèche de déroulement en définissant la propriété <xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A>.  <xref:System.Windows.Forms.ToolStripDropDownButton> héberge un <xref:System.Windows.Forms.ToolStripOverflowButton> qui affiche des éléments dépassant du <xref:System.Windows.Forms.ToolStrip>.  
  
### ToolStripSplitButton  
 <xref:System.Windows.Forms.ToolStripSplitButton> associe les fonctions de bouton et de bouton déroulant.  
  
 Utilisez la propriété <xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A> pour synchroniser l'événement <xref:System.Windows.Forms.Control.Click> de l'élément déroulant choisi avec l'élément indiqué sur le bouton.  
  
### Fonctionnalités génériques de ToolStripItem  
 <xref:System.Windows.Forms.ToolStripItem> fournit les options et fonctionnalités génériques suivantes aux contrôles qui héritent :  
  
-   Événements principaux  
  
-   Gestion des images  
  
-   Alignement  
  
-   Relation entre l'image et le texte  
  
-   Style d'affichage  
  
#### Événements principaux  
 Les contrôles <xref:System.Windows.Forms.ToolStripItem> reçoivent leurs propres événements Click, de souris et Paint ; ils peuvent en outre exécuter certains prétraitements clavier.  
  
#### Gestion des images  
 Les propriétés <xref:System.Windows.Forms.ToolStripItem.Image%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageKey%2A> et <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> se rapportent à certains aspects de la gestion des images.  Utilisez des images dans les contrôles <xref:System.Windows.Forms.ToolStrip> en définissant ces propriétés directement ou en définissant la propriété <xref:System.Windows.Forms.ToolStrip.ImageList%2A> au moment de l'exécution uniquement.  
  
 La mise à l'échelle des images est déterminée par l'interaction de propriétés à la fois dans <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.ToolStripItem>, comme suit :  
  
-   <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A> est l'échelle de la dernière image telle qu'elle est déterminée par la combinaison du paramètre <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> de l'image et du paramètre <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> du conteneur.  
  
    -   Si <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> a la valeur `true` \(valeur par défaut\) et que <xref:System.Windows.Forms.ToolStripItemImageScaling> a la valeur <xref:System.Windows.Forms.ToolStripItemImageScaling>, aucune mise à l'échelle des images ne se produit et la taille du <xref:System.Windows.Forms.ToolStrip> est celle de l'élément le plus grand, ou une taille minimale recommandée.  
  
    -   Si <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> a la valeur `false` et que <xref:System.Windows.Forms.ToolStripItemImageScaling> a la valeur <xref:System.Windows.Forms.ToolStripItemImageScaling>, aucune mise à l'échelle des images ni de <xref:System.Windows.Forms.ToolStrip> ne se produit.  
  
#### Alignement  
 La valeur de la propriété <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> détermine l'extrémité du <xref:System.Windows.Forms.ToolStrip> à laquelle un élément apparaît.  La propriété <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> fonctionne uniquement lorsque le style de disposition du <xref:System.Windows.Forms.ToolStrip> a pour valeur l'une des valeurs de dépassement de capacité de la pile.  
  
 Les éléments sont placés sur le <xref:System.Windows.Forms.ToolStrip> dans l'ordre dans lequel ils apparaissent dans la collection Items.  Pour changer par programme l'emplacement où un élément est disposé, utilisez la méthode <xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A> pour déplacer l'élément dans la collection.  Cette méthode déplace l'élément, mais ne le duplique pas.  
  
#### Relation entre l'image et le texte  
 La propriété <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> définit le positionnement relatif de l'image par rapport au texte sur un <xref:System.Windows.Forms.ToolStripItem>.  Les éléments auxquels il manque une image, du texte, ou les deux, sont traités comme des cas spéciaux afin que le <xref:System.Windows.Forms.ToolStripItem> n'affiche pas d'emplacement vide pour le ou les éléments manquants.  
  
#### Style d'affichage  
 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vous permet de définir les valeurs des propriétés de texte et d'image d'un élément tout en affichant uniquement ce que vous souhaitez.  Cette fonctionnalité est en général utilisée pour modifier uniquement le style d'affichage lors de l'affichage du même élément dans un contexte différent.  
  
## Classes d'accessoires  
 Les classes qui fournissent de nombreuses autres fonctionnalités incluent :  
  
-   <xref:System.Windows.Forms.ToolStripManager> prend en charge les tâches liées au <xref:System.Windows.Forms.ToolStrip> pour des applications entières, telles que la fusion, les paramètres et les options de convertisseur.  
  
-   <xref:System.Windows.Forms.ToolStripRenderer> vous permet d'appliquer facilement un style ou thème particulier à un <xref:System.Windows.Forms.ToolStrip>.  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer> crée des stylets et des pinceaux selon une table des couleurs remplaçable \(<xref:System.Windows.Forms.ProfessionalColorTable>\).  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer> applique des couleurs système et un style visuel à deux dimensions aux applications <xref:System.Windows.Forms.ToolStrip>.  
  
-   <xref:System.Windows.Forms.ToolStripContainer> est semblable à <xref:System.Windows.Forms.SplitContainer>.  Il utilise quatre panneaux latéraux ancrés \(instances de <xref:System.Windows.Forms.ToolStripPanel>\) et un panneau central \(instance de <xref:System.Windows.Forms.ToolStripContentPanel>\) pour créer une disposition classique.  Vous ne pouvez pas supprimer les panneaux latéraux, mais vous pouvez les masquer.  Vous ne pouvez ni supprimer ni masquer le panneau central.  Vous pouvez réorganiser un ou plusieurs contrôles <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip> ou <xref:System.Windows.Forms.StatusStrip> dans les panneaux latéraux, et vous pouvez utiliser le panneau central pour d'autres contrôles.  <xref:System.Windows.Forms.ToolStripContentPanel> offre également une prise en charge du rendu dans le corps de votre formulaire afin d'obtenir une apparence cohérente.  <xref:System.Windows.Forms.ToolStripContainer> ne prend pas en charge l'interface multidocument \(MDI\).  
  
-   <xref:System.Windows.Forms.ToolStripPanel> fournit l'espace pour déplacer et réorganiser des contrôles <xref:System.Windows.Forms.ToolStrip>.  Vous pouvez utiliser un seul panneau si vous préférez, et <xref:System.Windows.Forms.ToolStripPanel> fonctionne bien dans les scénarios MDI.  
  
## Voir aussi  
 [Vue d'ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [Résumé de la technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)   
 [ToolStrip, contrôle](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)   
 [MenuStrip, contrôle](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)   
 [StatusStrip, contrôle](../../../../docs/framework/winforms/controls/statusstrip-control.md)   
 [ContextMenuStrip, contrôle](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)   
 [BindingNavigator, contrôle](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)