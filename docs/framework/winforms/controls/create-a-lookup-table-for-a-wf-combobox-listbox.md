---
title: "Comment : créer une table de correspondance pour un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms"
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
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cb7ffb8a7f20c1e53b24a1db8bda326d73743a93
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="e17b3-102">Comment : créer une table de correspondance pour un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e17b3-102">How to: Create a Lookup Table for a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="e17b3-103">Il est parfois utile d'afficher les données dans un format convivial dans un Windows Form, mais de les stocker dans un format plus pertinent pour votre programme.</span><span class="sxs-lookup"><span data-stu-id="e17b3-103">Sometimes it is useful to display data in a user-friendly format on a Windows Form, but store the data in a format that is more meaningful to your program.</span></span> <span data-ttu-id="e17b3-104">Par exemple, un formulaire de commande de produits alimentaires peut présenter les éléments de menu par leur nom dans une zone de liste.</span><span class="sxs-lookup"><span data-stu-id="e17b3-104">For example, an order form for food might display the menu items by name in a list box.</span></span> <span data-ttu-id="e17b3-105">Toutefois, la table de données dans laquelle la commande est enregistrée contient alors les numéros d'ID uniques représentant les produits alimentaires.</span><span class="sxs-lookup"><span data-stu-id="e17b3-105">However, the data table recording the order would contain the unique ID numbers representing the food.</span></span> <span data-ttu-id="e17b3-106">Les tableaux ci-dessous montrent un exemple de stockage et d’affichage des données du formulaire de commande des produits alimentaires.</span><span class="sxs-lookup"><span data-stu-id="e17b3-106">The following tables show an example of how to store and display order-form data for food.</span></span>  
  
### <a name="orderdetailstable"></a><span data-ttu-id="e17b3-107">OrderDetailsTable</span><span class="sxs-lookup"><span data-stu-id="e17b3-107">OrderDetailsTable</span></span>  
  
|<span data-ttu-id="e17b3-108">OrderID</span><span class="sxs-lookup"><span data-stu-id="e17b3-108">OrderID</span></span>|<span data-ttu-id="e17b3-109">ItemID</span><span class="sxs-lookup"><span data-stu-id="e17b3-109">ItemID</span></span>|<span data-ttu-id="e17b3-110">Quantité</span><span class="sxs-lookup"><span data-stu-id="e17b3-110">Quantity</span></span>|  
|-------------|------------|--------------|  
|<span data-ttu-id="e17b3-111">4085</span><span class="sxs-lookup"><span data-stu-id="e17b3-111">4085</span></span>|<span data-ttu-id="e17b3-112">12</span><span class="sxs-lookup"><span data-stu-id="e17b3-112">12</span></span>|<span data-ttu-id="e17b3-113">1</span><span class="sxs-lookup"><span data-stu-id="e17b3-113">1</span></span>|  
|<span data-ttu-id="e17b3-114">4086</span><span class="sxs-lookup"><span data-stu-id="e17b3-114">4086</span></span>|<span data-ttu-id="e17b3-115">13</span><span class="sxs-lookup"><span data-stu-id="e17b3-115">13</span></span>|<span data-ttu-id="e17b3-116">3</span><span class="sxs-lookup"><span data-stu-id="e17b3-116">3</span></span>|  
  
### <a name="itemtable"></a><span data-ttu-id="e17b3-117">ItemTable</span><span class="sxs-lookup"><span data-stu-id="e17b3-117">ItemTable</span></span>  
  
|<span data-ttu-id="e17b3-118">ID</span><span class="sxs-lookup"><span data-stu-id="e17b3-118">ID</span></span>|<span data-ttu-id="e17b3-119">Nom</span><span class="sxs-lookup"><span data-stu-id="e17b3-119">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="e17b3-120">12</span><span class="sxs-lookup"><span data-stu-id="e17b3-120">12</span></span>|<span data-ttu-id="e17b3-121">Pomme de terre</span><span class="sxs-lookup"><span data-stu-id="e17b3-121">Potato</span></span>|  
|<span data-ttu-id="e17b3-122">13</span><span class="sxs-lookup"><span data-stu-id="e17b3-122">13</span></span>|<span data-ttu-id="e17b3-123">Poulet</span><span class="sxs-lookup"><span data-stu-id="e17b3-123">Chicken</span></span>|  
  
 <span data-ttu-id="e17b3-124">Dans ce scénario, une table, **OrderDetailsTable**, stocke les informations d’affichage et l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="e17b3-124">In this scenario, one table, **OrderDetailsTable**, stores the actual information you are concerned with displaying and saving.</span></span> <span data-ttu-id="e17b3-125">Cependant, pour économiser de l'espace, elle procède d’une façon plutôt insolite.</span><span class="sxs-lookup"><span data-stu-id="e17b3-125">But to save space, it does so in a fairly cryptic fashion.</span></span> <span data-ttu-id="e17b3-126">L’autre table, **ItemTable**, contient uniquement des informations relatives à l’apparence sur le ID de nombre équivaut au nom de produit alimentaire et rien sur les commandes de produits alimentaires réel.</span><span class="sxs-lookup"><span data-stu-id="e17b3-126">The other table, **ItemTable**, contains only appearance-related information about which ID number is equivalent to which food name, and nothing about the actual food orders.</span></span>  
  
 <span data-ttu-id="e17b3-127">Le **ItemTable** est connecté à la <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, ou <xref:System.Windows.Forms.CheckedListBox> via trois propriétés.</span><span class="sxs-lookup"><span data-stu-id="e17b3-127">The **ItemTable** is connected to the <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control through three properties.</span></span> <span data-ttu-id="e17b3-128">Le `DataSource` propriété contient le nom de la table.</span><span class="sxs-lookup"><span data-stu-id="e17b3-128">The `DataSource` property contains the name of this table.</span></span> <span data-ttu-id="e17b3-129">Le `DisplayMember` propriété contient la colonne de données de la table que vous souhaitez afficher dans le contrôle (nom de produit alimentaire).</span><span class="sxs-lookup"><span data-stu-id="e17b3-129">The `DisplayMember` property contains the data column of that table that you want to display in the control (the food name).</span></span> <span data-ttu-id="e17b3-130">Le `ValueMember` propriété contient la colonne de données de la table contenant les informations stockées (le numéro d’ID).</span><span class="sxs-lookup"><span data-stu-id="e17b3-130">The `ValueMember` property contains the data column of that table with the stored information (the ID number).</span></span>  
  
 <span data-ttu-id="e17b3-131">Le **OrderDetailsTable** est connecté au contrôle par sa collection de liaisons, accédée via la <xref:System.Windows.Forms.Control.DataBindings%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="e17b3-131">The **OrderDetailsTable** is connected to the control by its bindings collection, accessed through the <xref:System.Windows.Forms.Control.DataBindings%2A> property.</span></span> <span data-ttu-id="e17b3-132">Lorsque vous ajoutez un objet de liaison à la collection, vous connectez une propriété du contrôle à une donnée membre spécifique (la colonne des numéros d’ID) dans une source de données (la **OrderDetailsTable**).</span><span class="sxs-lookup"><span data-stu-id="e17b3-132">When you add a binding object to the collection, you connect a control property to a specific data member (the column of ID numbers) in a data source (the **OrderDetailsTable**).</span></span> <span data-ttu-id="e17b3-133">Quand une sélection est effectuée dans le contrôle, c’est dans cette table que l'entrée du formulaire est enregistrée.</span><span class="sxs-lookup"><span data-stu-id="e17b3-133">When a selection is made in the control, this table is where the form input is saved.</span></span>  
  
### <a name="to-create-a-lookup-table"></a><span data-ttu-id="e17b3-134">Pour créer une table de choix</span><span class="sxs-lookup"><span data-stu-id="e17b3-134">To create a lookup table</span></span>  
  
1.  <span data-ttu-id="e17b3-135">Ajoutez un contrôle <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox> ou <xref:System.Windows.Forms.CheckedListBox> au formulaire.</span><span class="sxs-lookup"><span data-stu-id="e17b3-135">Add a <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control to the form.</span></span>  
  
2.  <span data-ttu-id="e17b3-136">Connectez-vous à la source de données.</span><span class="sxs-lookup"><span data-stu-id="e17b3-136">Connect to your data source.</span></span>  
  
3.  <span data-ttu-id="e17b3-137">Établissez une relation de données entre les deux tables.</span><span class="sxs-lookup"><span data-stu-id="e17b3-137">Establish a data relation between the two tables.</span></span> <span data-ttu-id="e17b3-138">Consultez [Introduction aux objets DataRelation](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).</span><span class="sxs-lookup"><span data-stu-id="e17b3-138">See [Introduction to DataRelation Objects](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).</span></span>  
  
4.  <span data-ttu-id="e17b3-139">Définissez les propriétés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="e17b3-139">Set the following properties.</span></span> <span data-ttu-id="e17b3-140">Elles peuvent être définies dans le code ou dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="e17b3-140">They can be set in code or in the designer.</span></span>  
  
    |<span data-ttu-id="e17b3-141">Propriété</span><span class="sxs-lookup"><span data-stu-id="e17b3-141">Property</span></span>|<span data-ttu-id="e17b3-142">Paramètre</span><span class="sxs-lookup"><span data-stu-id="e17b3-142">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|<span data-ttu-id="e17b3-143">Table qui contient des informations sur les équivalences entre les numéros d’ID et les articles.</span><span class="sxs-lookup"><span data-stu-id="e17b3-143">The table that contains information about which ID number is equivalent to which item.</span></span> <span data-ttu-id="e17b3-144">Dans le scénario précédent, il s’agit de `ItemTable`.</span><span class="sxs-lookup"><span data-stu-id="e17b3-144">In the previous scenario, this is `ItemTable`.</span></span>|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|<span data-ttu-id="e17b3-145">Colonne de la table de source de données que vous souhaitez afficher dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="e17b3-145">The column of the data source table that you want to display in the control.</span></span> <span data-ttu-id="e17b3-146">Dans le scénario précédent, il s’agit `"Name"` (pour la définir dans le code, utilisez des guillemets doubles).</span><span class="sxs-lookup"><span data-stu-id="e17b3-146">In the previous scenario, this is `"Name"` (to set in code, use quotation marks).</span></span>|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|<span data-ttu-id="e17b3-147">Colonne de la table de source de données qui contient les informations stockées.</span><span class="sxs-lookup"><span data-stu-id="e17b3-147">The column of the data source table that contains the stored information.</span></span> <span data-ttu-id="e17b3-148">Dans le scénario précédent, il s’agit `"ID"` (pour la définir dans le code, utilisez des guillemets doubles).</span><span class="sxs-lookup"><span data-stu-id="e17b3-148">In the previous scenario, this is `"ID"` (to set in code, use quotation marks).</span></span>|  
  
5.  <span data-ttu-id="e17b3-149">Dans une procédure, appelez la méthode <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> de la classe <xref:System.Windows.Forms.ControlBindingsCollection> pour lier la ppropriété <xref:System.Windows.Forms.ListControl.SelectedValue%2A> du contrôle à la table d'enregistrement de l'entrée du formulaire.</span><span class="sxs-lookup"><span data-stu-id="e17b3-149">In a procedure, call the <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> method of the <xref:System.Windows.Forms.ControlBindingsCollection> class to bind the control's <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property to the table recording the form input.</span></span> <span data-ttu-id="e17b3-150">Vous pouvez également le faire dans le concepteur plutôt que dans le code, en accédant à du contrôle <xref:System.Windows.Forms.Control.DataBindings%2A> propriété dans le **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="e17b3-150">You can also do this in the Designer instead of in code, by accessing the control's <xref:System.Windows.Forms.Control.DataBindings%2A> property in the **Properties** window.</span></span> <span data-ttu-id="e17b3-151">Dans le scénario précédent, il s’agit de `OrderDetailsTable`, et la colonne est `"ItemID"`.</span><span class="sxs-lookup"><span data-stu-id="e17b3-151">In the previous scenario, this is `OrderDetailsTable`, and the column is `"ItemID"`.</span></span>  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e17b3-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e17b3-152">See Also</span></span>  
 [<span data-ttu-id="e17b3-153">Liaison de données et Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e17b3-153">Data Binding and Windows Forms</span></span>](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [<span data-ttu-id="e17b3-154">Vue d'ensemble du contrôle ListBox</span><span class="sxs-lookup"><span data-stu-id="e17b3-154">ListBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="e17b3-155">Vue d'ensemble du contrôle ComboBox</span><span class="sxs-lookup"><span data-stu-id="e17b3-155">ComboBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [<span data-ttu-id="e17b3-156">Vue d'ensemble du contrôle CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="e17b3-156">CheckedListBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="e17b3-157">Contrôles Windows Forms utilisés pour l’affichage de listes d’options</span><span class="sxs-lookup"><span data-stu-id="e17b3-157">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
