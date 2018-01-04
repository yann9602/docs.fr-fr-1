---
title: Composant BindingSource
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08b55bc2bd5af78eb6c3d0f5adce3ec39d288a9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="bindingsource-component"></a><span data-ttu-id="108c6-102">Composant BindingSource</span><span class="sxs-lookup"><span data-stu-id="108c6-102">BindingSource Component</span></span>
<span data-ttu-id="108c6-103">Encapsule une source de données pour la liaison à des contrôles.</span><span class="sxs-lookup"><span data-stu-id="108c6-103">Encapsulates a data source for binding to controls.</span></span>  
  
 <span data-ttu-id="108c6-104">Le composant <xref:System.Windows.Forms.BindingSource> remplit deux fonctions.</span><span class="sxs-lookup"><span data-stu-id="108c6-104">The <xref:System.Windows.Forms.BindingSource> component serves two purposes.</span></span> <span data-ttu-id="108c6-105">Tout d'abord, il fournit une couche d'indirection lors de la liaison des contrôles sur un formulaire de données.</span><span class="sxs-lookup"><span data-stu-id="108c6-105">First, it provides a layer of indirection when binding the controls on a form to data.</span></span> <span data-ttu-id="108c6-106">Vous devez pour cela lier le composant <xref:System.Windows.Forms.BindingSource> à votre source de données, puis lier les contrôles sur votre formulaire au composant <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="108c6-106">This is accomplished by binding the <xref:System.Windows.Forms.BindingSource> component to your data source, and then binding the controls on your form to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="108c6-107">Toute interaction supplémentaire avec les données, y compris la navigation, le tri, le filtrage et la mise à jour, est effectuée en appelant le composant <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="108c6-107">All further interaction with the data, including navigating, sorting, filtering, and updating, is accomplished with calls to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <span data-ttu-id="108c6-108">Ensuite, le composant <xref:System.Windows.Forms.BindingSource> peut agir comme source de données fortement typée.</span><span class="sxs-lookup"><span data-stu-id="108c6-108">Second, the <xref:System.Windows.Forms.BindingSource> component can act as a strongly typed data source.</span></span> <span data-ttu-id="108c6-109">L'ajout d'un type au composant <xref:System.Windows.Forms.BindingSource> avec la méthode <xref:System.Windows.Forms.BindingSource.Add%2A> crée une liste de ce type.</span><span class="sxs-lookup"><span data-stu-id="108c6-109">Adding a type to the <xref:System.Windows.Forms.BindingSource> component with the <xref:System.Windows.Forms.BindingSource.Add%2A> method creates a list of that type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="108c6-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="108c6-110">In This Section</span></span>  
 [<span data-ttu-id="108c6-111">Vue d'ensemble du composant BindingSource</span><span class="sxs-lookup"><span data-stu-id="108c6-111">BindingSource Component Overview</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 <span data-ttu-id="108c6-112">Présente les concepts généraux du composant <xref:System.Windows.Forms.BindingSource>, qui vous permet de lier une source de données à un contrôle.</span><span class="sxs-lookup"><span data-stu-id="108c6-112">Introduces the general concepts of the <xref:System.Windows.Forms.BindingSource> component, which allows you to bind a data source to a control.</span></span>  
  
 [<span data-ttu-id="108c6-113">Comment : lier des contrôles Windows Forms à des valeurs de base de données DBNull</span><span class="sxs-lookup"><span data-stu-id="108c6-113">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 <span data-ttu-id="108c6-114">Montre comment gérer une valeur <xref:System.DBNull> de la source de données à l'aide du composant <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="108c6-114">Shows how to handle a <xref:System.DBNull> value from the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="108c6-115">Comment : trier et filtrer des données ADO.NET avec le composant BindingSource Windows Forms</span><span class="sxs-lookup"><span data-stu-id="108c6-115">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 <span data-ttu-id="108c6-116">Illustre comment utiliser le composant <xref:System.Windows.Forms.BindingSource> pour appliquer des tris et des filtres aux données affichées.</span><span class="sxs-lookup"><span data-stu-id="108c6-116">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to apply sorts and filters to displayed data.</span></span>  
  
 [<span data-ttu-id="108c6-117">Comment : établir une liaison à un service Web à l’aide du BindingSource Windows Forms</span><span class="sxs-lookup"><span data-stu-id="108c6-117">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="108c6-118">Montre comment utiliser le composant <xref:System.Windows.Forms.BindingSource> pour établir une liaison à un service web.</span><span class="sxs-lookup"><span data-stu-id="108c6-118">Shows how to use the <xref:System.Windows.Forms.BindingSource> component to bind to a Web service.</span></span>  
  
 [<span data-ttu-id="108c6-119">Comment : gérer des erreurs et des exceptions qui se produisent avec Databinding</span><span class="sxs-lookup"><span data-stu-id="108c6-119">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 <span data-ttu-id="108c6-120">Illustre comment utiliser le composant <xref:System.Windows.Forms.BindingSource> pour gérer correctement les erreurs qui se produisent dans une opération de liaison de données.</span><span class="sxs-lookup"><span data-stu-id="108c6-120">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to gracefully handle errors that occur in a data binding operation.</span></span>  
  
 [<span data-ttu-id="108c6-121">Comment : lier un contrôle Windows Forms à un type</span><span class="sxs-lookup"><span data-stu-id="108c6-121">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 <span data-ttu-id="108c6-122">Montre comment utiliser un composant <xref:System.Windows.Forms.BindingSource> pour établir une liaison à un type.</span><span class="sxs-lookup"><span data-stu-id="108c6-122">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a type.</span></span>  
  
 [<span data-ttu-id="108c6-123">Comment : lier un contrôle Windows Forms à un objet Factory</span><span class="sxs-lookup"><span data-stu-id="108c6-123">How to: Bind a Windows Forms Control to a Factory Object</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 <span data-ttu-id="108c6-124">Montre comment utiliser un composant <xref:System.Windows.Forms.BindingSource> pour établir une liaison à une méthode ou un objet de fabrique.</span><span class="sxs-lookup"><span data-stu-id="108c6-124">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a factory object or method.</span></span>  
  
 [<span data-ttu-id="108c6-125">Comment : personnaliser l'ajout d'éléments avec le composant BindingSource Windows Forms</span><span class="sxs-lookup"><span data-stu-id="108c6-125">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="108c6-126">Montre comment utiliser un composant <xref:System.Windows.Forms.BindingSource> pour créer des éléments et les ajouter à une source de données.</span><span class="sxs-lookup"><span data-stu-id="108c6-126">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to create new items and add them to a data source.</span></span>  
  
 [<span data-ttu-id="108c6-127">Comment : générer des notifications de modifications à l'aide de la méthode ResetItem de BindingSource</span><span class="sxs-lookup"><span data-stu-id="108c6-127">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 <span data-ttu-id="108c6-128">Montre comment utiliser un composant <xref:System.Windows.Forms.BindingSource> pour déclencher des événements de notifications de modifications pour les sources de données qui ne prennent pas en charge les notifications de modifications.</span><span class="sxs-lookup"><span data-stu-id="108c6-128">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to raise change-notification events for data sources that do not support change notification.</span></span>  
  
 [<span data-ttu-id="108c6-129">Comment : générer des notifications de modifications à l'aide d'un BindingSource et de l'interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="108c6-129">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](../../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 <span data-ttu-id="108c6-130">Montre comment utiliser un type qui hérite de <xref:System.ComponentModel.INotifyPropertyChanged> avec un contrôle <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="108c6-130">Demonstrates how to use a type that inherits from the <xref:System.ComponentModel.INotifyPropertyChanged> with a <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
 [<span data-ttu-id="108c6-131">Comment : répercuter des mises à jour de source de données dans un contrôle Windows Forms avec le BindingSource</span><span class="sxs-lookup"><span data-stu-id="108c6-131">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 <span data-ttu-id="108c6-132">Montre comment répondre aux modifications qui se produisent dans la source de données à l'aide du composant <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="108c6-132">Demonstrates how to respond to changes in the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="108c6-133">Comment : partager des données liées entre des formulaires à l'aide du composant BindingSource</span><span class="sxs-lookup"><span data-stu-id="108c6-133">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 <span data-ttu-id="108c6-134">Montre comment utiliser <xref:System.Windows.Forms.BindingSource> pour lier plusieurs formulaires à la même source de données.</span><span class="sxs-lookup"><span data-stu-id="108c6-134">Shows how to use the <xref:System.Windows.Forms.BindingSource> to bind multiple forms to the same data source.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="108c6-135">Référence</span><span class="sxs-lookup"><span data-stu-id="108c6-135">Reference</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="108c6-136">Fournit la documentation de référence pour le composant <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="108c6-136">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 <span data-ttu-id="108c6-137">Fournit la documentation de référence pour le contrôle <xref:System.Windows.Forms.BindingNavigator>.</span><span class="sxs-lookup"><span data-stu-id="108c6-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="108c6-138">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="108c6-138">Related Sections</span></span>  
 [<span data-ttu-id="108c6-139">Liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="108c6-139">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 <span data-ttu-id="108c6-140">Contient des liens vers des rubriques décrivant l’architecture de liaison de données Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="108c6-140">Contains links to topics describing the Windows Forms data binding architecture.</span></span>  
  
 <span data-ttu-id="108c6-141">Consultez également [Liaison de contrôles à des données dans Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="108c6-141">Also see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>
