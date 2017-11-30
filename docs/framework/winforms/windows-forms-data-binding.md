---
title: "Liaison de données Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 60a9f66fec64ceda71dd5b70211b897c84113429
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="windows-forms-data-binding"></a><span data-ttu-id="8137c-102">Liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8137c-102">Windows Forms Data Binding</span></span>
<span data-ttu-id="8137c-103">La liaison de données dans les Windows Forms vous permet d’afficher et de modifier les informations d’une source de données dans les contrôles du formulaire.</span><span class="sxs-lookup"><span data-stu-id="8137c-103">Data binding in Windows Forms gives you the means to display and make changes to information from a data source in controls on the form.</span></span> <span data-ttu-id="8137c-104">Vous pouvez établir une liaison à une source de données traditionnelle et à presque toute structure qui contient des données.</span><span class="sxs-lookup"><span data-stu-id="8137c-104">You can bind to both traditional data sources as well as almost any structure that contains data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8137c-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8137c-105">In This Section</span></span>  
 [<span data-ttu-id="8137c-106">Liaison de données et Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8137c-106">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 <span data-ttu-id="8137c-107">Fournit une vue d’ensemble de la liaison de données dans les Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8137c-107">Provides an overview of data binding in Windows Forms.</span></span>  
  
 [<span data-ttu-id="8137c-108">Sources de données prises en charge par les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8137c-108">Data Sources Supported by Windows Forms</span></span>](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 <span data-ttu-id="8137c-109">Décrit les sources de données qui peuvent être utilisées avec Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8137c-109">Describes the data sources that can be used with Windows Forms.</span></span>  
  
 [<span data-ttu-id="8137c-110">Interfaces participant à la liaison de données</span><span class="sxs-lookup"><span data-stu-id="8137c-110">Interfaces Related to Data Binding</span></span>](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 <span data-ttu-id="8137c-111">Décrit plusieurs interfaces utilisées avec la liaison de données Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8137c-111">Describes several of the interfaces used with Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="8137c-112">Guide pratique pour naviguer au sein des données dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8137c-112">How to: Navigate Data in Windows Forms</span></span>](../../../docs/framework/winforms/how-to-navigate-data-in-windows-forms.md)  
 <span data-ttu-id="8137c-113">Montre comment parcourir les éléments dans une source de données.</span><span class="sxs-lookup"><span data-stu-id="8137c-113">Shows how to navigate through items in a data source.</span></span>  
  
 [<span data-ttu-id="8137c-114">Notification de modifications dans la liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8137c-114">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 <span data-ttu-id="8137c-115">Décrit les différents types de notifications de modifications pour la liaison de données Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8137c-115">Describes different types of change notification for Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="8137c-116">Guide pratique pour implémenter l'interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="8137c-116">How to: Implement the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 <span data-ttu-id="8137c-117">Montre comment implémenter l'interface <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="8137c-117">Shows how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="8137c-118">L'interface communique à un contrôle dépendant les modifications apportées aux propriétés d'un objet métier.</span><span class="sxs-lookup"><span data-stu-id="8137c-118">The interface  communicates to a bound control the property changes on a business object</span></span>  
  
 [<span data-ttu-id="8137c-119">Guide pratique pour appliquer le modèle PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="8137c-119">How to: Apply the PropertyNameChanged Pattern</span></span>](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 <span data-ttu-id="8137c-120">Montre comment appliquer le *PropertyName*modèle aux propriétés d’un contrôle utilisateur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8137c-120">Shows how to apply the *PropertyName*Changed pattern to properties of a Windows Forms user control.</span></span>  
  
 [<span data-ttu-id="8137c-121">Guide pratique pour implémenter l’interface ITypedList</span><span class="sxs-lookup"><span data-stu-id="8137c-121">How to: Implement the ITypedList Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-itypedlist-interface.md)  
 <span data-ttu-id="8137c-122">Montre comment activer la découverte du schéma pour une liste pouvant être liée en implémentant l'interface <xref:System.ComponentModel.ITypedList>.</span><span class="sxs-lookup"><span data-stu-id="8137c-122">Shows how to enable discovery of the schema for a bindable list by implementing the <xref:System.ComponentModel.ITypedList> interface.</span></span>  
  
 [<span data-ttu-id="8137c-123">Guide pratique pour implémenter l'interface IListSource</span><span class="sxs-lookup"><span data-stu-id="8137c-123">How to: Implement the IListSource Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-ilistsource-interface.md)  
 <span data-ttu-id="8137c-124">Montre comment implémenter l'interface <xref:System.ComponentModel.IListSource> pour créer une classe pouvant être liée qui n'implémente pas <xref:System.Collections.IList> mais fournit une liste à partir d'un autre emplacement.</span><span class="sxs-lookup"><span data-stu-id="8137c-124">Shows how to implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class does not implement <xref:System.Collections.IList>, but provides a list from another location.</span></span>  
  
 [<span data-ttu-id="8137c-125">Guide pratique pour s’assurer que plusieurs contrôles liés à la même source de données restent synchronisés</span><span class="sxs-lookup"><span data-stu-id="8137c-125">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 <span data-ttu-id="8137c-126">Montre comment gérer l'événement <xref:System.Windows.Forms.BindingSource.BindingComplete> pour garantir que tous les contrôles liés à une source de données restent synchronisés.</span><span class="sxs-lookup"><span data-stu-id="8137c-126">Shows how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event to ensure all controls bound to a data source remain synchronized.</span></span>  
  
 [<span data-ttu-id="8137c-127">Guide pratique pour s'assurer que la ligne sélectionnée dans une table enfant reste au bon emplacement</span><span class="sxs-lookup"><span data-stu-id="8137c-127">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>](../../../docs/framework/winforms/ensure-the-selected-row-in-a-child-table-correct.md)  
 <span data-ttu-id="8137c-128">Montre comment s'assurer que la ligne sélectionnée dans une table enfant ne change pas quand une modification est apportée à un champ de la table parente.</span><span class="sxs-lookup"><span data-stu-id="8137c-128">Shows how to ensure the selected row of a child table does not change, when a change is made to a field of the parent table.</span></span>  
  
 <span data-ttu-id="8137c-129">Consultez également [Interfaces associées à la liaison de données](http://msdn.microsoft.com/library/41e17s4b\(v=vs.110\)), [Comment : parcourir les données dans les Windows Forms](http://msdn.microsoft.com/library/b63ha24w\(v=vs.110\)), [Comment : créer un contrôle à liaison Simple dans un Windows Form](http://msdn.microsoft.com/library/sw223a62\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="8137c-129">Also see [Interfaces Related to Data Binding](http://msdn.microsoft.com/library/41e17s4b\(v=vs.110\)), [How to: Navigate Data in Windows Forms](http://msdn.microsoft.com/library/b63ha24w\(v=vs.110\)), [How to: Create a Simple-Bound Control on a Windows Form](http://msdn.microsoft.com/library/sw223a62\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8137c-130">Référence</span><span class="sxs-lookup"><span data-stu-id="8137c-130">Reference</span></span>  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 <span data-ttu-id="8137c-131">Décrit la classe qui représente la liaison entre un composant pouvant être lié et une source de données.</span><span class="sxs-lookup"><span data-stu-id="8137c-131">Describes the class that represents the binding between a bindable component and a data source.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 <span data-ttu-id="8137c-132">Décrit la classe qui encapsule une source de données pour la liaison à des contrôles.</span><span class="sxs-lookup"><span data-stu-id="8137c-132">Describes the class that encapsulates a data source for binding to controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8137c-133">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="8137c-133">Related Sections</span></span>  
 [<span data-ttu-id="8137c-134">BindingSource, composant</span><span class="sxs-lookup"><span data-stu-id="8137c-134">BindingSource Component</span></span>](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 <span data-ttu-id="8137c-135">Contient une liste de rubriques qui expliquent comment utiliser le composant <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="8137c-135">Contains a list of topics that demonstrate how to use the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="8137c-136">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="8137c-136">DataGridView Control</span></span>](../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 <span data-ttu-id="8137c-137">Fournit une liste de rubriques qui expliquent comment utiliser un contrôle datagrid pouvant être lié.</span><span class="sxs-lookup"><span data-stu-id="8137c-137">Provides a list of topics that demonstrate how to use a bindable datagrid control.</span></span>  
  
 <span data-ttu-id="8137c-138">Consultez également [l’accès à des données dans Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="8137c-138">Also see [Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span></span>
