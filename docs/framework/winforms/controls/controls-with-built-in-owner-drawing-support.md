---
title: "Contr&#244;les avec prise en charge int&#233;gr&#233;e des dessins owner-drawn | Microsoft Docs"
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
  - "dessin, propriétaire"
  - "dessin personnalisé"
  - "modification de l’apparence des contrôles (Windows Forms),"
  - "dessin personnalisé"
  - "owner-drawn"
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Contr&#244;les avec prise en charge int&#233;gr&#233;e des dessins owner-drawn
Owner-drawn dans Windows Forms, qui est également appelé un dessin personnalisé, est une technique permettant de modifier l’apparence visuelle de certains contrôles.  
  
> [!NOTE]
>  Le mot « contrôle » dans cette rubrique est utilisé pour désigner les classes qui dérivent <xref:System.Windows.Forms.Control> ou <xref:System.ComponentModel.Component>.  
  
 En règle générale, Windows gère automatiquement la peinture à l’aide des paramètres de propriété tels que <xref:System.Windows.Forms.Control.BackColor%2A> pour déterminer l’apparence d’un contrôle. Avec owner-drawn, prendre le processus de peinture, modification de l’apparence des éléments qui ne sont pas disponibles à l’aide de propriétés. Par exemple, de nombreux contrôles vous permettent de définir la couleur du texte qui s’affiche, mais vous êtes limité à une seule couleur. Owner-drawn vous permet d’effectuer des opérations comme afficher une partie du texte en noir et une autre en rouge.  
  
 Dans la pratique, owner-drawn est similaire au dessin de graphiques dans un formulaire. Par exemple, vous pouvez utiliser des méthodes graphiques dans un gestionnaire pour le formulaire <xref:System.Windows.Forms.Control.Paint> événement pour émuler un `ListBox` contrôle, mais vous devriez écrire votre propre code pour gérer toutes les interactions utilisateur. Avec owner-drawn, le contrôle utilise votre code pour dessiner son contenu, mais conserve toutes ses capacités intrinsèques. Vous pouvez utiliser des méthodes graphiques pour dessiner chaque élément dans le contrôle ou pour personnaliser certains aspects de chaque élément lorsque vous utilisez l’apparence par défaut pour d’autres aspects de chaque élément.  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>Contrôles de dessin propriétaire dans Windows Forms  
 Pour exécuter owner-drawn dans les contrôles qui prennent en charge, vous allez généralement définir une propriété et gérer un ou plusieurs événements.  
  
 La plupart des contrôles que propriétaire de la prise en charge de dessin a une `OwnerDraw` ou `DrawMode` propriété qui indique si le contrôle déclenche ses événements de dessin ou des événements lorsqu’il peint.  
  
 Les contrôles qui n’ont pas une `OwnerDraw` ou `DrawMode` propriété incluent les `DataGridView` contrôle, qui fournit des événements de dessin qui se produisent automatiquement, et le `ToolStrip` contrôle, qui est dessiné à l’aide d’une classe de rendu externe qui possède ses propres événements de dessin.  
  
 Il existe de nombreux types d’événements de dessin, mais un événement de dessin typique a lieu pour dessiner un élément unique dans un contrôle. Le Gestionnaire d’événements reçoit un `EventArgs` objet qui contient des informations sur l’élément qui est dessiné et outils vous pouvez utiliser pour dessiner. Par exemple, cet objet contient en général numéro d’index de l’élément dans sa collection parente, un <xref:System.Drawing.Rectangle> qui indique l’élément affiche les limites et un <xref:System.Drawing.Graphics> pour appeler les méthodes de peinture. Pour certains événements, le `EventArgs` objet fournit plus d’informations sur les méthodes que vous pouvez appeler pour peindre certains aspects de l’élément par défaut, telles que l’arrière-plan ou un rectangle de focus.  
  
 Pour créer un contrôle réutilisable contenant vos personnalisations owner-drawn, créez une classe qui dérive d’une classe de contrôle qui prend en charge le dessin owner-drawn. Plutôt que de la gestion des événements de dessin, incluez votre code de dessins owner-drawn dans les substitutions pour approprié `On` *EventName* ou les méthodes de la nouvelle classe. Assurez-vous que vous appelez la classe de base `On` *EventName* ou des méthodes dans ce cas permettant aux utilisateurs de votre contrôle peuvent gérer les événements owner-drawing et fournir une personnalisation supplémentaire.  
  
 Le suivant Windows Forms contrôles prise en charge d’owner-drawn dans toutes les versions du .NET Framework :  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <xref:System.Windows.Forms.MenuItem> (utilisée par <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu>)  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 Les contrôles suivants prennent en charge owner-drawn uniquement dans [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 Les contrôles suivants prennent en charge le dessin owner-drawn et sont nouveaux dans [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 Les sections suivantes fournissent des détails supplémentaires pour chacun de ces contrôles.  
  
### <a name="listbox-and-combobox-controls"></a>Contrôles ListBox et ComboBox  
 Le <xref:System.Windows.Forms.ListBox> et <xref:System.Windows.Forms.ComboBox> vous permettent de dessiner des éléments individuels dans le contrôle tous dans la même taille, ou dans des tailles différentes.  
  
> [!NOTE]
>  Bien que le <xref:System.Windows.Forms.CheckedListBox> contrôle est dérivé le <xref:System.Windows.Forms.ListBox> contrôle, il ne prend pas en charge owner-drawn.  
  
 Pour dessiner chaque élément dans la même taille, définissez la `DrawMode` propriété <xref:System.Windows.Forms.DrawMode> et gérer les `DrawItem` événement.  
  
 Pour dessiner chaque élément à l’aide d’une taille différente, définissez la `DrawMode` propriété <xref:System.Windows.Forms.DrawMode> et gérer à la fois le `MeasureItem` et `DrawItem` les événements. Le `MeasureItem` événement vous permet d’indiquer la taille d’un élément avant du `DrawItem` événement se produit pour cet élément.  
  
 Pour plus d’informations, y compris des exemples de code, consultez les rubriques suivantes :  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=fullName>  
  
-   [Comment : créer du texte de taille Variable dans un contrôle ComboBox](../../../../docs/framework/winforms/controls/how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>Composant de MenuItem  
 Le <xref:System.Windows.Forms.MenuItem> composant représente un élément de menu dans un <xref:System.Windows.Forms.MainMenu> ou <xref:System.Windows.Forms.ContextMenu> composant.  
  
 Pour dessiner un <xref:System.Windows.Forms.MenuItem>, définissez son `OwnerDraw` propriété `true` et gérer son `DrawItem` événement. Pour personnaliser la taille de l’élément de menu avant du `DrawItem` événement se produit, traiter l’élément `MeasureItem` événement.  
  
 Pour plus d’informations, y compris des exemples de code, consultez les rubriques de référence suivantes :  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=fullName>  
  
### <a name="tabcontrol-control"></a>TabControl, contrôle  
 Le <xref:System.Windows.Forms.TabControl> contrôle vous permet de dessiner des onglets individuels dans le contrôle. Owner-drawn affecte uniquement les onglets ; le <xref:System.Windows.Forms.TabPage> contenu n’est pas affecté.  
  
 Pour dessiner chaque onglet un <xref:System.Windows.Forms.TabControl>, définissez le `DrawMode` propriété <xref:System.Windows.Forms.TabDrawMode> et gérer les `DrawItem` événement. Cet événement se produit une fois pour chaque onglet uniquement lorsque l’onglet est visible dans le contrôle.  
  
 Pour plus d’informations, y compris des exemples de code, consultez les rubriques de référence suivantes :  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=fullName>  
  
### <a name="tooltip-component"></a>ToolTip, composant  
 Le <xref:System.Windows.Forms.ToolTip> composant vous permet de dessiner l’info-bulle entièrement lorsqu’elle est affichée.  
  
 Pour dessiner un <xref:System.Windows.Forms.ToolTip>, définissez son `OwnerDraw` propriété `true` et gérer son `Draw` événement. Pour personnaliser la taille de la <xref:System.Windows.Forms.ToolTip> avant la `Draw` événement se produit, gérer la `Popup` événements et définissez la <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> propriété dans le Gestionnaire d’événements.  
  
 Pour plus d’informations, y compris des exemples de code, consultez les rubriques de référence suivantes :  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=fullName>  
  
### <a name="listview-control"></a>Contrôle ListView  
 Le <xref:System.Windows.Forms.ListView> contrôle vous permet de dessiner des éléments, sous-éléments et en-têtes de colonne dans le contrôle.  
  
 Pour activer owner-drawn dans le contrôle, définissez la `OwnerDraw` propriété `true`.  
  
 Pour dessiner chaque élément dans le contrôle, gérez le `DrawItem` événement.  
  
 Pour dessiner chaque sous-élément ou en-tête de colonne dans le contrôle lorsque la <xref:System.Windows.Forms.ListView.View%2A> est définie sur <xref:System.Windows.Forms.View>, gérer les `DrawSubItem` et `DrawColumnHeader` événements.  
  
 Pour plus d’informations, y compris des exemples de code, consultez les rubriques de référence suivantes :  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=fullName>  
  
### <a name="treeview-control"></a>TreeView, contrôle  
 Le <xref:System.Windows.Forms.TreeView> contrôle vous permet de dessiner des nœuds individuels dans le contrôle.  
  
 Pour dessiner uniquement le texte affiché dans chaque nœud, définissez la `DrawMode` propriété <xref:System.Windows.Forms.TreeViewDrawMode> et gérer les `DrawNode` événement pour dessiner le texte.  
  
 Pour dessiner tous les éléments de chaque nœud, définissez la `DrawMode` propriété <xref:System.Windows.Forms.TreeViewDrawMode> et gérer les `DrawNode` événement dessiner n’importe quel élément que vous avez besoin, telles que le texte et les icônes, cases à cocher, signes, plus et moins et lignes connectant les nœuds.  
  
 Pour plus d’informations, y compris des exemples de code, consultez les rubriques de référence suivantes :  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=fullName>  
  
### <a name="datagridview-control"></a>DataGridView, contrôle  
 Le <xref:System.Windows.Forms.DataGridView> contrôle vous permet de dessiner des cellules et des lignes dans le contrôle.  
  
 Pour dessiner des cellules, gérez les `CellPainting` événement.  
  
 Pour dessiner des lignes ou des éléments de ligne, gérez un ou deux le `RowPrePaint` et `RowPostPaint` les événements. Le `RowPrePaint` événement se produit avant que les cellules d’une ligne sont peints et le `RowPostPaint` les cellules sont peintes. Vous pouvez gérer les deux événements et les `CellPainting` événement pour peindre l’arrière-plan de la ligne, des cellules individuelles et au premier plan de la ligne séparément, ou vous pouvez fournir personnalisations spécifiques où vous en avez besoin et utilisez l’affichage par défaut pour les autres éléments de la ligne.  
  
 Pour plus d’informations, y compris des exemples de code, consultez les rubriques suivantes :  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [Comment : personnaliser l’apparence des cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [Comment : personnaliser l’apparence des lignes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>ToolStrip, contrôle  
 <xref:System.Windows.Forms.ToolStrip> et contrôles dérivés vous permettent de personnaliser n’importe quel aspect de leur apparence.  
  
 Pour fournir un rendu personnalisé pour <xref:System.Windows.Forms.ToolStrip> contrôles, définir le `Renderer` propriété d’un <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, ou <xref:System.Windows.Forms.ToolStripContentPanel> à un `ToolStripRenderer` de l’objet et de gérer une ou plusieurs des nombreux événements de dessin fournis par la `ToolStripRenderer` classe. Vous pouvez également définir un `Renderer` propriété à une instance de votre propre classe dérivée de `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, ou <xref:System.Windows.Forms.ToolStripSystemRenderer> qui implémente ou substitue spécifique `On` *EventName* méthodes.  
  
 Pour plus d’informations, y compris des exemples de code, consultez les rubriques suivantes :  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [Comment : créer et définir un convertisseur personnalisé pour le contrôle ToolStrip dans les Windows Forms](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [Comment : personnaliser le dessin d’un contrôle ToolStrip](../../../../docs/framework/winforms/controls/how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)