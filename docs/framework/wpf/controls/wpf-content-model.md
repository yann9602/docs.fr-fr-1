---
title: "Modèle de contenu WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UIElement class [WPF], displaying content
- content model [WPF], controls
- controls [WPF], displaying text
- content display [WPF], controls
- controls [WPF], formatting text
- displaying content [WPF]
- arbitrary content classes [WPF], content model
- ContentControl class [WPF], displaying content
ms.assetid: 214da5ef-547a-4cf8-9b07-4aa8a0e52cdd
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52cb3a5391d6e24643b03a880d3695a11baceca3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="wpf-content-model"></a><span data-ttu-id="cb559-102">Modèle de contenu WPF</span><span class="sxs-lookup"><span data-stu-id="cb559-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="cb559-103"> est une plateforme de présentation qui fournit de nombreux contrôles et des éléments de type contrôle dont le principal objectif est d’afficher différents types de contenu.</span><span class="sxs-lookup"><span data-stu-id="cb559-103"> is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="cb559-104">Pour déterminer le contrôle à utiliser ou le contrôle d’où dériver, vous devez comprendre les types d’objets qu’un contrôle donné peut afficher de manière optimale.</span><span class="sxs-lookup"><span data-stu-id="cb559-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="cb559-105">Cette rubrique présente de manière synthétique le modèle de contenu pour les contrôles et les éléments de type contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb559-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="cb559-106">Le modèle de contenu décrit le contenu qui peut être utilisé dans un contrôle.</span><span class="sxs-lookup"><span data-stu-id="cb559-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="cb559-107">Cette rubrique répertorie également les propriétés de contenu pour chaque modèle de contenu.</span><span class="sxs-lookup"><span data-stu-id="cb559-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="cb559-108">Une propriété de contenu est une propriété qui est utilisée pour stocker le contenu de l’objet.</span><span class="sxs-lookup"><span data-stu-id="cb559-108">A content property is a property that is used to store the content of the object.</span></span>  
  
 
  
<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="cb559-109">Classes qui contiennent du contenu arbitraire</span><span class="sxs-lookup"><span data-stu-id="cb559-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="cb559-110">Certains contrôles peuvent contenir un objet de tout type, tel qu’une chaîne, un <xref:System.DateTime> objet, ou un <xref:System.Windows.UIElement> qui est un conteneur pour d’autres éléments.</span><span class="sxs-lookup"><span data-stu-id="cb559-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="cb559-111">Par exemple, un <xref:System.Windows.Controls.Button> peut contenir une image et du texte ; ou une <xref:System.Windows.Controls.CheckBox> peut contenir la valeur de <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cb559-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="cb559-112"> proposent quatre classes qui contiennent du contenu arbitraire.</span><span class="sxs-lookup"><span data-stu-id="cb559-112"> has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="cb559-113">Le tableau suivant répertorie les classes qui héritent de <xref:System.Windows.Controls.Control>.</span><span class="sxs-lookup"><span data-stu-id="cb559-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="cb559-114">Classe qui contient du contenu arbitraire</span><span class="sxs-lookup"><span data-stu-id="cb559-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="cb559-115">Contenu</span><span class="sxs-lookup"><span data-stu-id="cb559-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="cb559-116">Objet arbitraire unique.</span><span class="sxs-lookup"><span data-stu-id="cb559-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="cb559-117">En-tête et élément unique, correspondant tous deux à des objets arbitraires.</span><span class="sxs-lookup"><span data-stu-id="cb559-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="cb559-118">Collection d’objets arbitraires.</span><span class="sxs-lookup"><span data-stu-id="cb559-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="cb559-119">En-tête et collection d’éléments, correspondant tous deux à des objets arbitraires.</span><span class="sxs-lookup"><span data-stu-id="cb559-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="cb559-120">Les contrôles qui héritent de ces classes peuvent contenir le même type de contenu et traiter le contenu de la même façon.</span><span class="sxs-lookup"><span data-stu-id="cb559-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="cb559-121">L’illustration suivante montre un contrôle dérivé de chaque modèle de contenu qui contient une image et du texte.</span><span class="sxs-lookup"><span data-stu-id="cb559-121">The following illustration shows one control from each content model that contains an image and some text.</span></span>  
  
 <span data-ttu-id="cb559-122">![Button, GroupBox, Listbax, TreeViewItem](../../../../docs/framework/wpf/controls/media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")</span><span class="sxs-lookup"><span data-stu-id="cb559-122">![Button, GroupBox, Listbax, TreeViewItem](../../../../docs/framework/wpf/controls/media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")</span></span>  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="cb559-123">Contrôles qui contiennent un objet arbitraire unique</span><span class="sxs-lookup"><span data-stu-id="cb559-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="cb559-124">La <xref:System.Windows.Controls.ContentControl> classe contient un morceau unique de contenu arbitraire.</span><span class="sxs-lookup"><span data-stu-id="cb559-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="cb559-125">Sa propriété de contenu est <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb559-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="cb559-126">Les contrôles suivants héritent de <xref:System.Windows.Controls.ContentControl> et utiliser son modèle de contenu :</span><span class="sxs-lookup"><span data-stu-id="cb559-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Button>  
  
-   <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBoxItem>  
  
-   <xref:System.Windows.Controls.ContentControl>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GroupItem>  
  
-   <xref:System.Windows.Controls.Label>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Navigation.NavigationWindow>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
-   <xref:System.Windows.Controls.ScrollViewer>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
-   <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
-   <xref:System.Windows.Controls.ToolTip>  
  
-   <xref:System.Windows.Controls.UserControl>  
  
-   <xref:System.Windows.Window>  
  
 <span data-ttu-id="cb559-127">L’illustration suivante montre quatre boutons dont <xref:System.Windows.Controls.ContentControl.Content%2A> est définie sur une chaîne, un <xref:System.DateTime> objet, un <xref:System.Windows.Shapes.Rectangle>et un <xref:System.Windows.Controls.Panel> qui contient un <xref:System.Windows.Shapes.Ellipse> et un <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="cb559-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 <span data-ttu-id="cb559-128">![Quatre boutons](../../../../docs/framework/wpf/controls/media/controlcontentmodelbuttons.PNG "ControlContentModelButtons")</span><span class="sxs-lookup"><span data-stu-id="cb559-128">![Four buttons](../../../../docs/framework/wpf/controls/media/controlcontentmodelbuttons.PNG "ControlContentModelButtons")</span></span>  
<span data-ttu-id="cb559-129">Quatre boutons ayant différents types de contenu</span><span class="sxs-lookup"><span data-stu-id="cb559-129">Four buttons that have different types of content</span></span>  
  
 <span data-ttu-id="cb559-130">Pour obtenir un exemple montrant comment définir le <xref:System.Windows.Controls.ContentControl.Content%2A> propriété, consultez <xref:System.Windows.Controls.ContentControl>.</span><span class="sxs-lookup"><span data-stu-id="cb559-130">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="cb559-131">Contrôles qui contiennent un en-tête et un objet arbitraire unique</span><span class="sxs-lookup"><span data-stu-id="cb559-131">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="cb559-132">Le <xref:System.Windows.Controls.HeaderedContentControl> hérite de la classe <xref:System.Windows.Controls.ContentControl> et affiche le contenu avec un en-tête.</span><span class="sxs-lookup"><span data-stu-id="cb559-132">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="cb559-133">Il hérite de la propriété de contenu, <xref:System.Windows.Controls.ContentControl.Content%2A>, à partir de <xref:System.Windows.Controls.ContentControl> et définit les <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> propriété qui est de type <xref:System.Object>; par conséquent, les deux peuvent être un objet arbitraire.</span><span class="sxs-lookup"><span data-stu-id="cb559-133">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="cb559-134">Les contrôles suivants héritent de <xref:System.Windows.Controls.HeaderedContentControl> et utiliser son modèle de contenu :</span><span class="sxs-lookup"><span data-stu-id="cb559-134">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="cb559-135">L’illustration suivante montre deux <xref:System.Windows.Controls.TabItem> objets.</span><span class="sxs-lookup"><span data-stu-id="cb559-135">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="cb559-136">La première <xref:System.Windows.Controls.TabItem> a <xref:System.Windows.UIElement> des objets en tant que le <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> et <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb559-136">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="cb559-137">Le <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> est définie sur une <xref:System.Windows.Controls.StackPanel> qui contient un <xref:System.Windows.Shapes.Ellipse> et un <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="cb559-137">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="cb559-138">Le <xref:System.Windows.Controls.ContentControl.Content%2A> est définie sur une <xref:System.Windows.Controls.StackPanel> qui contient un <xref:System.Windows.Controls.TextBlock> et un <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="cb559-138">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="cb559-139">La seconde <xref:System.Windows.Controls.TabItem> a une chaîne le <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> et un <xref:System.Windows.Controls.TextBlock> dans le <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb559-139">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 <span data-ttu-id="cb559-140">![TabControl](../../../../docs/framework/wpf/controls/media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")</span><span class="sxs-lookup"><span data-stu-id="cb559-140">![TabControl](../../../../docs/framework/wpf/controls/media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")</span></span>  
<span data-ttu-id="cb559-141">TabControl qui utilise différents types dans la propriété d’en-tête</span><span class="sxs-lookup"><span data-stu-id="cb559-141">TabControl that uses different types in the Header property</span></span>  
  
 <span data-ttu-id="cb559-142">Pour obtenir un exemple montrant comment créer <xref:System.Windows.Controls.TabItem> , consultez <xref:System.Windows.Controls.HeaderedContentControl>.</span><span class="sxs-lookup"><span data-stu-id="cb559-142">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="cb559-143">Contrôles qui contiennent une collection d’objets arbitraires</span><span class="sxs-lookup"><span data-stu-id="cb559-143">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="cb559-144">Le <xref:System.Windows.Controls.ItemsControl> hérite de la classe <xref:System.Windows.Controls.Control> et peut contenir plusieurs éléments, tels que des chaînes, des objets ou des autres éléments.</span><span class="sxs-lookup"><span data-stu-id="cb559-144">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="cb559-145">Ses propriétés de contenu sont <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> et <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb559-145">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="cb559-146"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>est généralement utilisé pour remplir le <xref:System.Windows.Controls.ItemsControl> avec une collection de données.</span><span class="sxs-lookup"><span data-stu-id="cb559-146"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="cb559-147">Si vous ne souhaitez pas utiliser une collection pour remplir le <xref:System.Windows.Controls.ItemsControl>, vous pouvez ajouter des éléments à l’aide de la <xref:System.Windows.Controls.ItemsControl.Items%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="cb559-147">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="cb559-148">Les contrôles suivants héritent de <xref:System.Windows.Controls.ItemsControl> et utiliser son modèle de contenu :</span><span class="sxs-lookup"><span data-stu-id="cb559-148">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Menu>  
  
-   <xref:System.Windows.Controls.Primitives.MenuBase>  
  
-   <xref:System.Windows.Controls.ContextMenu>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.ItemsControl>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListView>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TreeView>  
  
-   <xref:System.Windows.Controls.Primitives.Selector>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 <span data-ttu-id="cb559-149">L’illustration suivante montre un <xref:System.Windows.Controls.ListBox> qui contient ces types d’éléments :</span><span class="sxs-lookup"><span data-stu-id="cb559-149">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
-   <span data-ttu-id="cb559-150">Chaîne.</span><span class="sxs-lookup"><span data-stu-id="cb559-150">A string.</span></span>  
  
-   <span data-ttu-id="cb559-151">Objet <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="cb559-151">A <xref:System.DateTime> object.</span></span>  
  
-   <span data-ttu-id="cb559-152"><xref:System.Windows.UIElement></span><span class="sxs-lookup"><span data-stu-id="cb559-152">A <xref:System.Windows.UIElement>.</span></span>  
  
-   <span data-ttu-id="cb559-153">A <xref:System.Windows.Controls.Panel> qui contient un <xref:System.Windows.Shapes.Ellipse> et un <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="cb559-153">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 <span data-ttu-id="cb559-154">![ListBox avec quatre types de contenu](../../../../docs/framework/wpf/controls/media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")</span><span class="sxs-lookup"><span data-stu-id="cb559-154">![ListBox with four types of content](../../../../docs/framework/wpf/controls/media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")</span></span>  
<span data-ttu-id="cb559-155">ListBox contenant plusieurs types de contenu</span><span class="sxs-lookup"><span data-stu-id="cb559-155">ListBox that contains multiple types of objects</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="cb559-156">Contrôles qui contiennent un en-tête et une collection d’objets arbitraires</span><span class="sxs-lookup"><span data-stu-id="cb559-156">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="cb559-157">Le <xref:System.Windows.Controls.HeaderedItemsControl> hérite de la classe <xref:System.Windows.Controls.ItemsControl> et peut contenir plusieurs éléments, tels que des chaînes, objets, ou autres éléments et un en-tête.</span><span class="sxs-lookup"><span data-stu-id="cb559-157">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="cb559-158">Elle hérite la <xref:System.Windows.Controls.ItemsControl> propriétés, du contenu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, et <xref:System.Windows.Controls.ItemsControl.Items%2A>, et définit le <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> propriété qui peut être un objet arbitraire.</span><span class="sxs-lookup"><span data-stu-id="cb559-158">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="cb559-159">Les contrôles suivants héritent de <xref:System.Windows.Controls.HeaderedItemsControl> et utiliser son modèle de contenu :</span><span class="sxs-lookup"><span data-stu-id="cb559-159">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="cb559-160">Classes qui contiennent une collection d’objets UIElement</span><span class="sxs-lookup"><span data-stu-id="cb559-160">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="cb559-161">Le <xref:System.Windows.Controls.Panel> classe positionne et réorganise les enfants <xref:System.Windows.UIElement> objets.</span><span class="sxs-lookup"><span data-stu-id="cb559-161">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="cb559-162">Sa propriété de contenu est <xref:System.Windows.Controls.Panel.Children%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb559-162">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="cb559-163">Les classes suivantes héritent de la <xref:System.Windows.Controls.Panel> classe et utiliser son modèle de contenu :</span><span class="sxs-lookup"><span data-stu-id="cb559-163">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.Primitives.TabPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
-   <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 <span data-ttu-id="cb559-164">Pour plus d’informations, consultez la page [Vue d’ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cb559-164">For more information, see [Panels Overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="cb559-165">Classes qui affectent l’apparence d’un UIElement</span><span class="sxs-lookup"><span data-stu-id="cb559-165">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="cb559-166">Le <xref:System.Windows.Controls.Decorator> classe applique des effets visuels sur ou autour d’un seul enfant <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="cb559-166">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="cb559-167">Sa propriété de contenu est <xref:System.Windows.Controls.Decorator.Child%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb559-167">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="cb559-168">Les classes suivantes héritent de <xref:System.Windows.Controls.Decorator> et utiliser son modèle de contenu :</span><span class="sxs-lookup"><span data-stu-id="cb559-168">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
-   <xref:System.Windows.Documents.AdornerDecorator>  
  
-   <xref:System.Windows.Controls.Border>  
  
-   <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
-   <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
-   <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
-   <xref:System.Windows.Controls.InkPresenter>  
  
-   <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
-   <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
-   <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="cb559-169">L’illustration suivante montre un <xref:System.Windows.Controls.TextBox> qui a (est décoré avec) un <xref:System.Windows.Controls.Border> autour de lui.</span><span class="sxs-lookup"><span data-stu-id="cb559-169">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="cb559-170">![TextBox avec bordure noire](../../../../docs/framework/wpf/controls/media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="cb559-170">![TextBox with black border](../../../../docs/framework/wpf/controls/media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="cb559-171">TextBlock avec une bordure</span><span class="sxs-lookup"><span data-stu-id="cb559-171">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="cb559-172">Classes qui fournissent des commentaires visuels sur un UIElement</span><span class="sxs-lookup"><span data-stu-id="cb559-172">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="cb559-173">La <xref:System.Windows.Documents.Adorner> classe fournit des signaux visuels à un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cb559-173">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="cb559-174">Par exemple, utiliser un <xref:System.Windows.Documents.Adorner> pour ajouter des handles fonctionnels aux éléments ou fournir les informations d’état sur un contrôle.</span><span class="sxs-lookup"><span data-stu-id="cb559-174">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="cb559-175">La <xref:System.Windows.Documents.Adorner> classe fournit une infrastructure afin que vous pouvez créer vos propres ornements.</span><span class="sxs-lookup"><span data-stu-id="cb559-175">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="cb559-176"> ne fournit aucun ornement implémenté.</span><span class="sxs-lookup"><span data-stu-id="cb559-176"> does not provide any implemented adorners.</span></span> <span data-ttu-id="cb559-177">Pour plus d’informations, consultez [Vue d’ensemble des ornements](../../../../docs/framework/wpf/controls/adorners-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cb559-177">For more information, see [Adorners Overview](../../../../docs/framework/wpf/controls/adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="cb559-178">Classes qui permettent aux utilisateurs d’entrer du texte</span><span class="sxs-lookup"><span data-stu-id="cb559-178">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="cb559-179">WPF fournit trois principaux contrôles qui permettent aux utilisateurs d’entrer du texte.</span><span class="sxs-lookup"><span data-stu-id="cb559-179">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="cb559-180">Chaque contrôle affiche le texte de manière différente.</span><span class="sxs-lookup"><span data-stu-id="cb559-180">Each control displays the text differently.</span></span> <span data-ttu-id="cb559-181">Le tableau suivant répertorie ces trois contrôles liés au texte, leurs fonctions lors de l’affichage du texte et leurs propriétés qui contiennent le texte du contrôle.</span><span class="sxs-lookup"><span data-stu-id="cb559-181">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="cb559-182">Contrôle</span><span class="sxs-lookup"><span data-stu-id="cb559-182">Control</span></span>|<span data-ttu-id="cb559-183">Texte affiché en tant que</span><span class="sxs-lookup"><span data-stu-id="cb559-183">Text is displayed as</span></span>|<span data-ttu-id="cb559-184">Propriété de contenu</span><span class="sxs-lookup"><span data-stu-id="cb559-184">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="cb559-185">Texte brut</span><span class="sxs-lookup"><span data-stu-id="cb559-185">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="cb559-186">Texte mis en forme</span><span class="sxs-lookup"><span data-stu-id="cb559-186">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="cb559-187">Texte masqué (les caractères sont masqués)</span><span class="sxs-lookup"><span data-stu-id="cb559-187">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a><span data-ttu-id="cb559-188">Classes qui affichent votre texte</span><span class="sxs-lookup"><span data-stu-id="cb559-188">Classes That Display Your Text</span></span>  
 <span data-ttu-id="cb559-189">Plusieurs classes peuvent être utilisées pour afficher du texte brut ou mis en forme.</span><span class="sxs-lookup"><span data-stu-id="cb559-189">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="cb559-190">Vous pouvez utiliser <xref:System.Windows.Controls.TextBlock> pour afficher de petites quantités de texte.</span><span class="sxs-lookup"><span data-stu-id="cb559-190">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="cb559-191">Si vous souhaitez afficher de grandes quantités de texte, utilisez la <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, ou <xref:System.Windows.Controls.FlowDocumentScrollViewer> contrôles.</span><span class="sxs-lookup"><span data-stu-id="cb559-191">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="cb559-192">Le <xref:System.Windows.Controls.TextBlock> a deux propriétés de contenu : <xref:System.Windows.Controls.TextBlock.Text%2A> et <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb559-192">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="cb559-193">Lorsque vous souhaitez afficher du texte qui utilise la mise en forme cohérente, la <xref:System.Windows.Controls.TextBlock.Text%2A> propriété est souvent le meilleur choix.</span><span class="sxs-lookup"><span data-stu-id="cb559-193">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="cb559-194">Si vous envisagez d’utiliser la mise en forme différente dans tout le texte, utilisez le <xref:System.Windows.Controls.TextBlock.Inlines%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="cb559-194">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="cb559-195">Le <xref:System.Windows.Controls.TextBlock.Inlines%2A> propriété est une collection de <xref:System.Windows.Documents.Inline> objets, qui spécifient la mise en forme de texte.</span><span class="sxs-lookup"><span data-stu-id="cb559-195">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="cb559-196">Le tableau suivant répertorie la propriété de contenu pour <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, et <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span><span class="sxs-lookup"><span data-stu-id="cb559-196">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="cb559-197">Contrôle</span><span class="sxs-lookup"><span data-stu-id="cb559-197">Control</span></span>|<span data-ttu-id="cb559-198">Propriété de contenu</span><span class="sxs-lookup"><span data-stu-id="cb559-198">Content property</span></span>|<span data-ttu-id="cb559-199">Type de propriété de contenu</span><span class="sxs-lookup"><span data-stu-id="cb559-199">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="cb559-200">Document</span><span class="sxs-lookup"><span data-stu-id="cb559-200">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="cb559-201">Document</span><span class="sxs-lookup"><span data-stu-id="cb559-201">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="cb559-202">Document</span><span class="sxs-lookup"><span data-stu-id="cb559-202">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="cb559-203">Le <xref:System.Windows.Documents.FlowDocument> implémente la <xref:System.Windows.Documents.IDocumentPaginatorSource> interface ; par conséquent, les trois classes peuvent accepter un <xref:System.Windows.Documents.FlowDocument> en tant que contenu.</span><span class="sxs-lookup"><span data-stu-id="cb559-203">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a><span data-ttu-id="cb559-204">Classes de mise en forme du texte</span><span class="sxs-lookup"><span data-stu-id="cb559-204">Classes That Format Your Text</span></span>  
 <span data-ttu-id="cb559-205"><xref:System.Windows.Documents.TextElement>et ses classes connexes vous permettent de mettre en forme texte.</span><span class="sxs-lookup"><span data-stu-id="cb559-205"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="cb559-206"><xref:System.Windows.Documents.TextElement>les objets contiennent et mettre en forme le texte dans <xref:System.Windows.Controls.TextBlock> et <xref:System.Windows.Documents.FlowDocument> objets.</span><span class="sxs-lookup"><span data-stu-id="cb559-206"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="cb559-207">Les deux principaux types de <xref:System.Windows.Documents.TextElement> sont des objets <xref:System.Windows.Documents.Block> éléments et <xref:System.Windows.Documents.Inline> éléments.</span><span class="sxs-lookup"><span data-stu-id="cb559-207">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="cb559-208">A <xref:System.Windows.Documents.Block> élément représente un bloc de texte, tel qu’un paragraphe ou d’une liste.</span><span class="sxs-lookup"><span data-stu-id="cb559-208">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="cb559-209">Un <xref:System.Windows.Documents.Inline> élément représente une partie du texte dans un bloc.</span><span class="sxs-lookup"><span data-stu-id="cb559-209">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="cb559-210">Nombreux <xref:System.Windows.Documents.Inline> classes spécifient la mise en forme du texte dans lequel ils sont appliqués.</span><span class="sxs-lookup"><span data-stu-id="cb559-210">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="cb559-211">Chaque <xref:System.Windows.Documents.TextElement> possède son propre modèle de contenu.</span><span class="sxs-lookup"><span data-stu-id="cb559-211">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="cb559-212">Pour plus d’informations, consultez la page [Vue d’ensemble du modèle de contenu de TextElement](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cb559-212">For more information, see the [TextElement Content Model Overview](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb559-213">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb559-213">See Also</span></span>  
 [<span data-ttu-id="cb559-214">Avancé</span><span class="sxs-lookup"><span data-stu-id="cb559-214">Advanced</span></span>](../../../../docs/framework/wpf/advanced/index.md)
