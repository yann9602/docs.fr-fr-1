---
title: "Comment : créer un contrôle dépendant et mettre en forme les données affichées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6088048ed27b2021e297494275f4e80f7c0cb681
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a><span data-ttu-id="f93a2-102">Comment : créer un contrôle dépendant et mettre en forme les données affichées</span><span class="sxs-lookup"><span data-stu-id="f93a2-102">How to: Create a Bound Control and Format the Displayed Data</span></span>
<span data-ttu-id="f93a2-103">Liaison de données Windows Forms, vous pouvez mettre en forme les données affichées dans un contrôle lié aux données à l’aide de la **mise en forme et liaison avancée** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="f93a2-103">With Windows Forms data binding, you can format the data displayed in a data-bound control by using the **Formatting and Advanced Binding** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f93a2-104">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="f93a2-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f93a2-105">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="f93a2-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f93a2-106">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="f93a2-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-bind-a-control-and-format-the-displayed-data"></a><span data-ttu-id="f93a2-107">Pour lier un contrôle et mettre en forme les données affichées</span><span class="sxs-lookup"><span data-stu-id="f93a2-107">To bind a control and format the displayed data</span></span>  
  
1.  <span data-ttu-id="f93a2-108">Connectez-vous à une source de données.</span><span class="sxs-lookup"><span data-stu-id="f93a2-108">Connect to a data source.</span></span>  
  
     <span data-ttu-id="f93a2-109">Pour plus d’informations, consultez [la connexion à une Source de données](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="f93a2-109">For more information, see [Connecting to a Data Source](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2.  <span data-ttu-id="f93a2-110">Dans le formulaire, sélectionnez le contrôle, puis ouvrez la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="f93a2-110">In the form, select the control, and then open the Properties window.</span></span>  
  
3.  <span data-ttu-id="f93a2-111">Développez le **(DataBindings)** propriété, puis, dans le **(Avancé)** , cliquez sur le bouton de sélection (![capture d’écran de VisualStudioEllipsesButton] (../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) pour afficher la **mise en forme et liaison avancée** boîte de dialogue, qui présente une liste complète des propriétés de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="f93a2-111">Expand the **(DataBindings)** property, and then in the **(Advanced)** box, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) to display the **Formatting and Advanced Binding** dialog box, which has a complete list of properties for that control.</span></span>  
  
4.  <span data-ttu-id="f93a2-112">Sélectionnez la propriété que vous souhaitez lier, puis cliquez sur le **liaison** flèche.</span><span class="sxs-lookup"><span data-stu-id="f93a2-112">Select the property you want to bind, and then click the **Binding** arrow.</span></span>  
  
     <span data-ttu-id="f93a2-113">Une liste des sources de données disponibles s'affiche.</span><span class="sxs-lookup"><span data-stu-id="f93a2-113">A list of available data sources is displayed.</span></span>  
  
5.  <span data-ttu-id="f93a2-114">Développez la source de données avec laquelle vous voulez établir une liaison jusqu'à trouver l'élément de données souhaité.</span><span class="sxs-lookup"><span data-stu-id="f93a2-114">Expand the data source you want to bind to until you find the single data element you want.</span></span>  
  
     <span data-ttu-id="f93a2-115">Par exemple, si vous établissez une liaison à une valeur de colonne dans une table de dataset, développez le nom du dataset, puis développez le nom de la table pour afficher les noms des colonnes.</span><span class="sxs-lookup"><span data-stu-id="f93a2-115">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
6.  <span data-ttu-id="f93a2-116">Cliquez sur le nom d'un élément avec lequel établir une liaison.</span><span class="sxs-lookup"><span data-stu-id="f93a2-116">Click the name of an element to bind to.</span></span>  
  
7.  <span data-ttu-id="f93a2-117">Dans le **Format de type** , cliquez sur le format à appliquer aux données affichées dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="f93a2-117">In the **Format type** box, click the format you want to apply to the data displayed in the control.</span></span>  
  
     <span data-ttu-id="f93a2-118">Dans tous les cas, vous pouvez spécifier la valeur affichée dans le contrôle si la source de données contient <xref:System.DBNull>.</span><span class="sxs-lookup"><span data-stu-id="f93a2-118">In every case, you can specify the value displayed in the control if the data source contains <xref:System.DBNull>.</span></span> <span data-ttu-id="f93a2-119">Sinon, les options varient légèrement en fonction du type de format que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="f93a2-119">Otherwise, the options vary slightly, depending on the format type you choose.</span></span> <span data-ttu-id="f93a2-120">Le tableau suivant présente les options et les types de format.</span><span class="sxs-lookup"><span data-stu-id="f93a2-120">The following table shows the format types and options.</span></span>  
  
    |<span data-ttu-id="f93a2-121">Type de format</span><span class="sxs-lookup"><span data-stu-id="f93a2-121">Format type</span></span>|<span data-ttu-id="f93a2-122">Option de mise en forme</span><span class="sxs-lookup"><span data-stu-id="f93a2-122">Formatting option</span></span>|  
    |-----------------|-----------------------|  
    |<span data-ttu-id="f93a2-123">Aucune mise en forme</span><span class="sxs-lookup"><span data-stu-id="f93a2-123">No Formatting</span></span>|<span data-ttu-id="f93a2-124">Aucune option.</span><span class="sxs-lookup"><span data-stu-id="f93a2-124">No options.</span></span>|  
    |<span data-ttu-id="f93a2-125">Numérique</span><span class="sxs-lookup"><span data-stu-id="f93a2-125">Numeric</span></span>|<span data-ttu-id="f93a2-126">Spécifiez le nombre de décimales à l’aide de **décimales** contrôle up-down.</span><span class="sxs-lookup"><span data-stu-id="f93a2-126">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="f93a2-127">Devise</span><span class="sxs-lookup"><span data-stu-id="f93a2-127">Currency</span></span>|<span data-ttu-id="f93a2-128">Spécifiez le nombre de décimales à l’aide de **décimales** contrôle up-down.</span><span class="sxs-lookup"><span data-stu-id="f93a2-128">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="f93a2-129">Date et heure</span><span class="sxs-lookup"><span data-stu-id="f93a2-129">Date Time</span></span>|<span data-ttu-id="f93a2-130">Sélectionnez comment la date et l’heure doivent être affichées en sélectionnant un des éléments dans le **Type** zone de sélection.</span><span class="sxs-lookup"><span data-stu-id="f93a2-130">Select how the date and time should be displayed by selecting one of the items in the **Type** selection box.</span></span>|  
    |<span data-ttu-id="f93a2-131">Scientifique</span><span class="sxs-lookup"><span data-stu-id="f93a2-131">Scientific</span></span>|<span data-ttu-id="f93a2-132">Spécifiez le nombre de décimales à l’aide de **décimales** contrôle up-down.</span><span class="sxs-lookup"><span data-stu-id="f93a2-132">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="f93a2-133">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="f93a2-133">Custom</span></span>|<span data-ttu-id="f93a2-134">Spécifiez une chaîne de format personnalisée.</span><span class="sxs-lookup"><span data-stu-id="f93a2-134">Specify a custom format string using.</span></span><br /><br /> <span data-ttu-id="f93a2-135">Pour plus d’informations, consultez [mise en forme des Types](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="f93a2-135">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="f93a2-136">**Remarque :** chaînes de format personnalisé ne sont pas garanti que pour effectuer un aller-retour entre la source de données et le contrôle dépendant.</span><span class="sxs-lookup"><span data-stu-id="f93a2-136">**Note:**  Custom format strings are not guaranteed to successfully round trip between the data source and bound control.</span></span> <span data-ttu-id="f93a2-137">Gérez plutôt l'événement <xref:System.Windows.Forms.Binding.Parse> ou <xref:System.Windows.Forms.Binding.Format> pour la liaison et appliquez la mise en forme personnalisée dans le code de gestion d'événements.</span><span class="sxs-lookup"><span data-stu-id="f93a2-137">Instead handle the <xref:System.Windows.Forms.Binding.Parse> or <xref:System.Windows.Forms.Binding.Format> event for the binding and apply custom formatting in the event-handling code.</span></span>|  
  
8.  <span data-ttu-id="f93a2-138">Cliquez sur **OK** pour fermer la **mise en forme et liaison avancée** boîte de dialogue et revenir à la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="f93a2-138">Click **OK** to close the **Formatting and Advanced Binding** dialog box and return to the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f93a2-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f93a2-139">See Also</span></span>  
 [<span data-ttu-id="f93a2-140">Guide pratique pour créer un contrôle à liaison simple dans un Windows Form</span><span class="sxs-lookup"><span data-stu-id="f93a2-140">How to: Create a Simple-Bound Control on a Windows Form</span></span>](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)  
 [<span data-ttu-id="f93a2-141">Validation des entrées d’utilisateur dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f93a2-141">User Input Validation in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 [<span data-ttu-id="f93a2-142">Liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f93a2-142">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
