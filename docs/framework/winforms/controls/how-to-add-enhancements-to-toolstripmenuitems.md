---
title: "Comment : ajouter des améliorations aux ToolStripMenuItems"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- commands [Windows Forms], grouping on menus
- check marks [Windows Forms], adding to menus
- ToolStripMenuItems [Windows Forms], displaying access keys
- menus [Windows Forms], grouping commands
- menu items [Windows Forms], displaying shortcut keys
- ToolStripMenuItems
- separators [Windows Forms], displaying on menus
- menu items [Windows Forms], showing separators
- menu items [Windows Forms], adding check marks
- ToolStripMenuItems [Windows Forms], adding check marks
- menu items [Windows Forms], adding images
- ToolStripSeparators [Windows Forms], displaying on MenuStrips
- menu items [Windows Forms], displaying access keys
- ToolStripMenuItems [Windows Forms], displaying shortcut keys
- ToolStripMenuItems [Windows Forms], adding images
- keyboard shortcuts [Windows Forms], displaying on menus
- images [Windows Forms], adding to menus
- ToolStripMenuItems [Windows Forms], showing separator bars
ms.assetid: aa5f19bb-b545-4378-bfa6-36ba592f0d7c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2701094ffcbcf7eeb14444163b995816398876fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a><span data-ttu-id="fbbdb-102">Comment : ajouter des améliorations aux ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="fbbdb-102">How to: Add Enhancements to ToolStripMenuItems</span></span>
<span data-ttu-id="fbbdb-103">Vous pouvez améliorer la facilité d’utilisation de <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.ContextMenuStrip> contrôles comme suit :</span><span class="sxs-lookup"><span data-stu-id="fbbdb-103">You can enhance the usability of <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> controls in the following ways:</span></span>  
  
-   <span data-ttu-id="fbbdb-104">Ajouter des coches pour désigner si une fonctionnalité est activée ou désactivée, telles que si une règle est affichée le long de la marge d’une application de traitement de texte, ou pour indiquer le fichier d’une liste de fichiers est affichée, par exemple, en tant que sur un **fenêtre** menu.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-104">Add check marks to designate whether a feature is turned on or off, such as whether a ruler is displayed along the margin of a word-processing application, or to indicate which file in a list of files is being displayed, such as on a **Window** menu.</span></span>  
  
-   <span data-ttu-id="fbbdb-105">Ajouter des images qui visuellement représentent des commandes de menu.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-105">Add images that visually represent menu commands.</span></span>  
  
-   <span data-ttu-id="fbbdb-106">Afficher les touches de raccourci pour fournir un autre clavier à la souris pour exécuter des commandes.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-106">Display shortcut keys to provide a keyboard alternative to the mouse for performing commands.</span></span> <span data-ttu-id="fbbdb-107">Par exemple, l’en appuyant sur CTRL + C effectue la **copie** commande.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-107">For example, pressing CTRL+C performs the **Copy** command.</span></span>  
  
-   <span data-ttu-id="fbbdb-108">Afficher les clés d’accès pour fournir un autre clavier à la souris pour la navigation de menu.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-108">Display access keys to provide a keyboard alternative to the mouse for menu navigation.</span></span> <span data-ttu-id="fbbdb-109">Par exemple, en appuyant sur ALT + F pour choisir le **fichier** menu.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-109">For example, pressing ALT+F chooses the **File** menu.</span></span>  
  
-   <span data-ttu-id="fbbdb-110">Afficher les barres de séparation pour regrouper les commandes associées et d’améliorer la lisibilité des menus.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-110">Show separator bars to group related commands and make menus more readable.</span></span>  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a><span data-ttu-id="fbbdb-111">Pour afficher une coche sur une commande de menu</span><span class="sxs-lookup"><span data-stu-id="fbbdb-111">To display a check mark on a menu command</span></span>  
  
-   <span data-ttu-id="fbbdb-112">Définir son <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-112">Set its <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="fbbdb-113">Il définit également la <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-113">This also sets the <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> property to `true`.</span></span> <span data-ttu-id="fbbdb-114">Utilisez cette procédure uniquement si vous souhaitez que la commande de menu apparaisse comme cochée par défaut, indépendamment de si elle est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-114">Use this procedure only if you want the menu command to appear as checked by default, regardless of whether it is selected.</span></span>  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a><span data-ttu-id="fbbdb-115">Pour afficher une coche qui modifie l’état à chaque clic</span><span class="sxs-lookup"><span data-stu-id="fbbdb-115">To display a check mark that changes state with each click</span></span>  
  
-   <span data-ttu-id="fbbdb-116">Définir la commande de menu <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-116">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true`.</span></span>  
  
### <a name="to-add-an-image-to-a-menu-command"></a><span data-ttu-id="fbbdb-117">Pour ajouter une image à une commande de menu</span><span class="sxs-lookup"><span data-stu-id="fbbdb-117">To add an image to a menu command</span></span>  
  
-   <span data-ttu-id="fbbdb-118">Définir la commande de menu <xref:System.Windows.Forms.ToolStripItem.Image%2A> nom à la propriété de l’image.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-118">Set the menu command's <xref:System.Windows.Forms.ToolStripItem.Image%2A> property to the name of the image.</span></span> <span data-ttu-id="fbbdb-119">Si le <xref:System.Windows.Forms.ToolStripItemDisplayStyle> de cette commande de menu est définie sur <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> ou <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, l’image ne peut pas être affichée.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-119">If the <xref:System.Windows.Forms.ToolStripItemDisplayStyle> property of this menu command is set to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, the image cannot be displayed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbbdb-120">La marge d’image peut également afficher une case à cocher si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-120">The image margin can also show a check mark if you so choose.</span></span> <span data-ttu-id="fbbdb-121">En outre, vous pouvez définir le <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> propriété de l’image à `true`, et l’image s’affiche avec une bordure hachurée au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-121">Also, you can set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property of the image to `true`, and the image will appear with a hatched border around it at run time.</span></span>  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a><span data-ttu-id="fbbdb-122">Pour afficher une touche de raccourci pour une commande de menu</span><span class="sxs-lookup"><span data-stu-id="fbbdb-122">To display a shortcut key for a menu command</span></span>  
  
-   <span data-ttu-id="fbbdb-123">Définir la commande de menu <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> propriété à la combinaison de touches souhaitée, tels que CTRL + O pour la **ouvrir** commande de menu et définissez la <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-123">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> property to the desired keyboard combination, such as CTRL+O for the **Open** menu command, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a><span data-ttu-id="fbbdb-124">Pour afficher les touches de raccourci personnalisées pour une commande de menu</span><span class="sxs-lookup"><span data-stu-id="fbbdb-124">To display custom shortcut keys for a menu command</span></span>  
  
-   <span data-ttu-id="fbbdb-125">Définir la commande de menu <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> propriété à la combinaison de touches souhaitée, tels que CTRL + MAJ + O plutôt que MAJ + CTRL + O et ensemble la <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-125">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> property to the desired keyboard combination, such as CTRL+SHIFT+O rather than SHIFT+CTRL+O, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a><span data-ttu-id="fbbdb-126">Pour afficher une clé d’accès pour une commande de menu</span><span class="sxs-lookup"><span data-stu-id="fbbdb-126">To display an access key for a menu command</span></span>  
  
-   <span data-ttu-id="fbbdb-127">Lorsque vous définissez le <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriété pour la commande de menu, entrez une esperluette (&) devant la lettre que vous souhaitez être soulignée comme touche d’accès rapide.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-127">When you set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property for the menu command, enter an ampersand (&) before the letter you want to be underlined as the access key.</span></span> <span data-ttu-id="fbbdb-128">Par exemple, si vous tapez `&Open` comme le <xref:System.Windows.Forms.ToolStripItem.Text%2A> génère dans une commande de menu qui s’affiche en tant que propriété d’un élément de menu **O**stylet.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-128">For example, typing `&Open` as the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of a menu item will result in a menu command that appears as **O**pen.</span></span>  
  
     <span data-ttu-id="fbbdb-129">Pour accéder à cette commande de menu, appuyez sur ALT pour donner le focus à la <xref:System.Windows.Forms.MenuStrip>, appuyez sur la touche d’accès du nom de menu.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-129">To navigate to this menu command, press ALT to give focus to the <xref:System.Windows.Forms.MenuStrip>, and press the access key of the menu name.</span></span> <span data-ttu-id="fbbdb-130">Lorsque le menu s’ouvre et affiche les éléments avec des clés d’accès, il vous suffit d’appuyer sur la touche d’accès rapide pour sélectionner la commande de menu.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-130">When the menu opens and shows items with access keys, you only need to press the access key to select the menu command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbbdb-131">Évitez de définir des clés d’accès en double, tel que la définition ALT + F à deux reprises dans le même système de menus.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-131">Avoid defining duplicate access keys, such as defining ALT+F twice in the same menu system.</span></span> <span data-ttu-id="fbbdb-132">L’ordre de sélection des clés d’accès en double ne peut pas être garantie.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-132">The selection order of duplicate access keys cannot be guaranteed.</span></span>  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a><span data-ttu-id="fbbdb-133">Pour afficher une barre de séparation entre les commandes de menu</span><span class="sxs-lookup"><span data-stu-id="fbbdb-133">To display a separator bar between menu commands</span></span>  
  
-   <span data-ttu-id="fbbdb-134">Après avoir défini votre <xref:System.Windows.Forms.MenuStrip> et les éléments qu’il contient, utilisez la <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> ou <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> méthode pour ajouter les commandes de menu et <xref:System.Windows.Forms.ToolStripSeparator> des contrôles à le <xref:System.Windows.Forms.MenuStrip> dans l’ordre souhaité.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-134">After you define your <xref:System.Windows.Forms.MenuStrip> and the items it will contain, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> or <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add the menu commands and <xref:System.Windows.Forms.ToolStripSeparator> controls to the <xref:System.Windows.Forms.MenuStrip> in the order you want.</span></span>  
  
    ```vb  
    ' This code adds a top-level File menu to the MenuStrip.  
    Me.menuStrip1.Items.Add(New ToolStripMenuItem() _  
    {Me.fileToolStripMenuItem})  
  
    ' This code adds the New and Open menu commands, a separator bar,   
    ' and the Save and Exit menu commands to the top-level File menu,   
    ' in that order.  
    Me.fileToolStripMenuItem.DropDownItems.AddRange(New _  
    ToolStripMenuItem() {Me.newToolStripMenuItem, _  
    Me.openToolStripMenuItem, Me.toolStripSeparator1, _  
    Me.saveToolStripMenuItem, Me.exitToolStripMenuItem})  
    ```  
  
    ```csharp  
    // This code adds a top-level File menu to the MenuStrip.  
    this.menuStrip1.Items.Add(new ToolStripItem[]_  
    {this.fileToolStripMenuItem});  
  
    // This code adds the New and Open menu commands, a separator bar,   
    // and the Save and Exit menu commands to the top-level File menu,   
    // in that order.  
    this.fileToolStripMenuItem.DropDownItems.AddRange(new _  
    ToolStripItem[] {  
    this.newToolStripMenuItem,  
    this.openToolStripMenuItem,  
    this.toolStripSeparator1,  
    this.saveToolStripMenuItem,  
    this.exitToolStripMenuItem});  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fbbdb-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbbdb-135">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="fbbdb-136">Vue d'ensemble du contrôle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="fbbdb-136">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
