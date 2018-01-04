---
title: "Attributs dans les contrôles Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [Windows Forms]
- attributes [Windows Forms], data binding properties
- attributes [Windows Forms], control properties
- attributes [Windows Forms], classes
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13aad22dca249147e3037bcef6da755c264021db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="attributes-in-windows-forms-controls"></a><span data-ttu-id="d3348-102">Attributs dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3348-102">Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="d3348-103">.NET Framework fournit divers attributs que vous pouvez appliquer aux membres de vos composants et contrôles personnalisés.</span><span class="sxs-lookup"><span data-stu-id="d3348-103">The .NET Framework provides a variety of attributes you can apply to the members of your custom controls and components.</span></span> <span data-ttu-id="d3348-104">Certains de ces attributs affectent le comportement d’exécution d’une classe, et d’autres affectent le comportement au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="d3348-104">Some of these attributes affect the run-time behavior of a class, and others affect the design-time behavior.</span></span>  
  
## <a name="attributes-for-control-and-component-properties"></a><span data-ttu-id="d3348-105">Attributs pour les propriétés de composant et de contrôle</span><span class="sxs-lookup"><span data-stu-id="d3348-105">Attributes for Control and Component Properties</span></span>  
 <span data-ttu-id="d3348-106">Le tableau suivant décrit les attributs que vous pouvez appliquer aux propriétés ou aux autres membres de vos composants et contrôles personnalisés.</span><span class="sxs-lookup"><span data-stu-id="d3348-106">The following table shows the attributes you can apply to properties or other members of your custom controls and components.</span></span> <span data-ttu-id="d3348-107">Pour obtenir un exemple d’utilisation de ces attributs, consultez [Comment : appliquer des attributs dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d3348-107">For an example that uses many of these attributes, see [How to: Apply Attributes in Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
|<span data-ttu-id="d3348-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="d3348-108">Attribute</span></span>|<span data-ttu-id="d3348-109">Description</span><span class="sxs-lookup"><span data-stu-id="d3348-109">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|<span data-ttu-id="d3348-110">Spécifie la valeur à passer à une propriété pour que celle-ci obtienne sa valeur à partir d’une autre source.</span><span class="sxs-lookup"><span data-stu-id="d3348-110">Specifies the value to pass to a property to cause the property to get its value from another source.</span></span> <span data-ttu-id="d3348-111">On appelle cela *l’ambiance*.</span><span class="sxs-lookup"><span data-stu-id="d3348-111">This is known as *ambience*.</span></span>|  
|<xref:System.ComponentModel.BrowsableAttribute>|<span data-ttu-id="d3348-112">Spécifie si une propriété ou un événement doit être affiché dans une fenêtre **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d3348-112">Specifies whether a property or event should be displayed in a **Properties** window.</span></span>|  
|<xref:System.ComponentModel.CategoryAttribute>|<span data-ttu-id="d3348-113">Spécifie le nom de la catégorie dans laquelle grouper la propriété ou l’événement lorsque affichés dans un <xref:System.Windows.Forms.PropertyGrid> contrôle <xref:System.Windows.Forms.PropertySort.Categorized> mode.</span><span class="sxs-lookup"><span data-stu-id="d3348-113">Specifies the name of the category in which to group the property or event when displayed in a <xref:System.Windows.Forms.PropertyGrid> control set to <xref:System.Windows.Forms.PropertySort.Categorized> mode.</span></span>|  
|<xref:System.ComponentModel.DefaultValueAttribute>|<span data-ttu-id="d3348-114">Spécifie la valeur par défaut d'une propriété.</span><span class="sxs-lookup"><span data-stu-id="d3348-114">Specifies the default value for a property.</span></span>|  
|<xref:System.ComponentModel.DescriptionAttribute>|<span data-ttu-id="d3348-115">Spécifie une description pour une propriété ou un événement.</span><span class="sxs-lookup"><span data-stu-id="d3348-115">Specifies a description for a property or event.</span></span>|  
|<xref:System.ComponentModel.DisplayNameAttribute>|<span data-ttu-id="d3348-116">Spécifie le nom d’affichage complet pour une propriété, un événement, ou une méthode `public``void` qui n’accepte aucun argument.</span><span class="sxs-lookup"><span data-stu-id="d3348-116">Specifies the display name for a property, event, or `public``void` method that takes no arguments.</span></span>|  
|<xref:System.ComponentModel.EditorAttribute>|<span data-ttu-id="d3348-117">Spécifie l’éditeur à utiliser pour modifier une propriété.</span><span class="sxs-lookup"><span data-stu-id="d3348-117">Specifies the editor to use to change a property.</span></span>|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|<span data-ttu-id="d3348-118">Spécifie qu'une propriété ou une méthode peut s'afficher dans un éditeur.</span><span class="sxs-lookup"><span data-stu-id="d3348-118">Specifies that a property or method is viewable in an editor.</span></span>|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|<span data-ttu-id="d3348-119">Spécifie le mot-clé de contexte pour une classe ou un membre.</span><span class="sxs-lookup"><span data-stu-id="d3348-119">Specifies the context keyword for a class or member.</span></span>|  
|<xref:System.ComponentModel.LocalizableAttribute>|<span data-ttu-id="d3348-120">Spécifie si une propriété doit être localisée.</span><span class="sxs-lookup"><span data-stu-id="d3348-120">Specifies whether a property should be localized.</span></span>|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|<span data-ttu-id="d3348-121">Indique que la représentation sous forme de texte d’un objet est masquée par des caractères tels que des astérisques.</span><span class="sxs-lookup"><span data-stu-id="d3348-121">Indicates that an object's text representation is obscured by characters such as asterisks.</span></span>|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|<span data-ttu-id="d3348-122">Spécifie si la propriété de cet attribut est liée est en lecture seule ou lecture/écriture au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="d3348-122">Specifies whether the property this attribute is bound to is read-only or read/write at design time.</span></span>|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|<span data-ttu-id="d3348-123">Indique que la grille de propriétés doit s’actualiser lorsque la valeur de propriété associée change.</span><span class="sxs-lookup"><span data-stu-id="d3348-123">Indicates that the property grid should refresh when the associated property value changes.</span></span>|  
|<xref:System.ComponentModel.TypeConverterAttribute>|<span data-ttu-id="d3348-124">Spécifie le type à utiliser comme convertisseur de l'objet auquel cet attribut est lié.</span><span class="sxs-lookup"><span data-stu-id="d3348-124">Specifies what type to use as a converter for the object this attribute is bound to.</span></span>|  
  
## <a name="attributes-for-data-binding-properties"></a><span data-ttu-id="d3348-125">Attributs pour les propriétés de liaison de données</span><span class="sxs-lookup"><span data-stu-id="d3348-125">Attributes for Data Binding Properties</span></span>  
 <span data-ttu-id="d3348-126">Le tableau suivant montre les attributs que vous pouvez appliquer pour spécifier la façon dont vos composants et contrôles personnalisés interagissent avec la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="d3348-126">The following table shows the attributes you can apply to specify how your custom controls and components interact with data binding.</span></span>  
  
|<span data-ttu-id="d3348-127">Attribut</span><span class="sxs-lookup"><span data-stu-id="d3348-127">Attribute</span></span>|<span data-ttu-id="d3348-128">Description</span><span class="sxs-lookup"><span data-stu-id="d3348-128">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|<span data-ttu-id="d3348-129">Spécifie si une propriété est généralement utilisée pour la liaison.</span><span class="sxs-lookup"><span data-stu-id="d3348-129">Specifies whether a property is typically used for binding.</span></span>|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|<span data-ttu-id="d3348-130">Spécifie la source de données et les propriétés de membre de données pour un composant.</span><span class="sxs-lookup"><span data-stu-id="d3348-130">Specifies the data source and data member properties for a component.</span></span>|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|<span data-ttu-id="d3348-131">Spécifie la propriété de liaison par défaut pour un composant.</span><span class="sxs-lookup"><span data-stu-id="d3348-131">Specifies the default binding property for a component.</span></span>|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|<span data-ttu-id="d3348-132">Spécifie la source de données et les propriétés de membre de données pour un composant.</span><span class="sxs-lookup"><span data-stu-id="d3348-132">Specifies the data source and data member properties for a component.</span></span>|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|<span data-ttu-id="d3348-133">Active la redirection d’attribut.</span><span class="sxs-lookup"><span data-stu-id="d3348-133">Enables attribute redirection.</span></span>|  
  
## <a name="attributes-for-classes"></a><span data-ttu-id="d3348-134">Attributs pour les classes</span><span class="sxs-lookup"><span data-stu-id="d3348-134">Attributes for Classes</span></span>  
 <span data-ttu-id="d3348-135">Le tableau suivant montre les attributs que vous pouvez appliquer pour spécifier le comportement de vos composants et contrôles personnalisés au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="d3348-135">The following table shows the attributes you can apply to specify the behavior of your custom controls and components at design time.</span></span>  
  
|<span data-ttu-id="d3348-136">Attribut</span><span class="sxs-lookup"><span data-stu-id="d3348-136">Attribute</span></span>|<span data-ttu-id="d3348-137">Description</span><span class="sxs-lookup"><span data-stu-id="d3348-137">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|<span data-ttu-id="d3348-138">Spécifie l’événement par défaut d’un composant.</span><span class="sxs-lookup"><span data-stu-id="d3348-138">Specifies the default event for a component.</span></span>|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|<span data-ttu-id="d3348-139">Spécifie la propriété par défaut d’un composant.</span><span class="sxs-lookup"><span data-stu-id="d3348-139">Specifies the default property for a component.</span></span>|  
|<xref:System.ComponentModel.DesignerAttribute>|<span data-ttu-id="d3348-140">Spécifie la classe utilisée pour implémenter des services au moment de la conception pour un composant.</span><span class="sxs-lookup"><span data-stu-id="d3348-140">Specifies the class used to implement design-time services for a component.</span></span>|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|<span data-ttu-id="d3348-141">Spécifie que le concepteur pour une classe appartient à une certaine catégorie.</span><span class="sxs-lookup"><span data-stu-id="d3348-141">Specifies that the designer for a class belongs to a certain category.</span></span>|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|<span data-ttu-id="d3348-142">Représente un attribut d’un élément de boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="d3348-142">Represents an attribute of a toolbox item.</span></span>|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|<span data-ttu-id="d3348-143">Spécifie la chaîne de filtrage et le type de filtre à utiliser pour un élément de boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="d3348-143">Specifies the filter string and filter type to use for a Toolbox item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3348-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3348-144">See Also</span></span>  
 <xref:System.Attribute>  
 [<span data-ttu-id="d3348-145">Guide pratique pour appliquer des attributs dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3348-145">How to: Apply Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)  
 [<span data-ttu-id="d3348-146">Extension de la prise en charge au moment du design</span><span class="sxs-lookup"><span data-stu-id="d3348-146">Extending Design-Time Support</span></span>](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [<span data-ttu-id="d3348-147">Développement de contrôles Windows Forms personnalisés avec le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d3348-147">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
