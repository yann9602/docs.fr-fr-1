---
title: "Création et utilisation de composants dans Visual Basic"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 03929dd0dbb81a9efee5b69ede78ff0b4ab4d380
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="creating-and-using-components-in-visual-basic"></a><span data-ttu-id="6dbdb-102">Création et utilisation de composants dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6dbdb-102">Creating and Using Components in Visual Basic</span></span>
<span data-ttu-id="6dbdb-103">Un *composant* est une classe qui implémente l’interface <xref:System.ComponentModel.IComponent?displayProperty=fullName> ou qui dérive directement ou indirectement d’une classe implémentant <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-103">A *component* is a class that implements the <xref:System.ComponentModel.IComponent?displayProperty=fullName> interface or that derives directly or indirectly from a class that implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="6dbdb-104">Un composant [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] est un objet réutilisable qui peut interagir avec d’autres objets, qui permet de contrôler les ressources externes et qui offre une prise en charge au moment du design.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-104">A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] component is an object that is reusable, can interact with other objects, and provides control over external resources and design-time support.</span></span>  
  
 <span data-ttu-id="6dbdb-105">Une caractéristique importante des composants est qu’ils peuvent servir au design, ce qui signifie qu’une classe qui est un composant peut être utilisée dans l’environnement de développement intégré (IDE) de [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6dbdb-105">An important feature of components is that they are designable, which means that a class that is a component can be used in the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Integrated Development Environment.</span></span> <span data-ttu-id="6dbdb-106">Un composant peut être ajouté à la boîte à outils, faire l’objet d’un glisser-déplacer sur un formulaire et être manipulé sur une aire de conception.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-106">A component can be added to the Toolbox, dragged and dropped onto a form, and manipulated on a design surface.</span></span> <span data-ttu-id="6dbdb-107">Notez que la prise en charge de base au moment du design pour les composants est intégrée au [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Un développeur de composant n’a pas besoin d’effectuer du travail supplémentaire pour tirer parti de la fonctionnalité de base au moment du design.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-107">Notice that base design-time support for components is built into the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]; a component developer does not have to do any additional work to take advantage of the base design-time functionality.</span></span>  
  
 <span data-ttu-id="6dbdb-108">Un *contrôle* est similaire à un composant dans la mesure où tous les deux peuvent servir au design.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-108">A *control* is similar to a component, as both are designable.</span></span> <span data-ttu-id="6dbdb-109">Toutefois, un contrôle fournit une interface utilisateur, ce qui n’est pas le cas d’un composant.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-109">However, a control provides a user interface, while a component does not.</span></span> <span data-ttu-id="6dbdb-110">Un contrôle doit dériver de l’une des classes de contrôle de base : <xref:System.Windows.Forms.Control> ou <xref:System.Web.UI.Control>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-110">A control must derive from one of the base control classes: <xref:System.Windows.Forms.Control> or <xref:System.Web.UI.Control>.</span></span>  
  
## <a name="when-to-create-a-component"></a><span data-ttu-id="6dbdb-111">Quand créer un composant</span><span class="sxs-lookup"><span data-stu-id="6dbdb-111">When to Create a Component</span></span>  
 <span data-ttu-id="6dbdb-112">Si votre classe doit être utilisée sur une aire de conception (telle que le concepteur Windows Forms ou Web Forms), mais qu’elle n’a pas d’interface utilisateur, elle doit être un composant et implémenter <xref:System.ComponentModel.IComponent>, ou dériver d’une classe qui implémente directement ou indirectement <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-112">If your class will be used on a design surface (such as the Windows Forms or Web Forms Designer) but has no user interface, it should be a component and implement <xref:System.ComponentModel.IComponent>, or derive from a class that directly or indirectly implements <xref:System.ComponentModel.IComponent>.</span></span>  
  
 <span data-ttu-id="6dbdb-113">Les classes <xref:System.ComponentModel.Component> et <xref:System.ComponentModel.MarshalByValueComponent> constituent des implémentations de base de l’interface <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-113">The <xref:System.ComponentModel.Component> and <xref:System.ComponentModel.MarshalByValueComponent> classes are base implementations of the <xref:System.ComponentModel.IComponent> interface.</span></span> <span data-ttu-id="6dbdb-114">La principale différence entre ces classes est que la classe <xref:System.ComponentModel.Component> est marshalée par référence, tandis que la classe <xref:System.ComponentModel.IComponent> est marshalée par valeur.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-114">The main difference between these classes is that the <xref:System.ComponentModel.Component> class is marshaled by reference, while <xref:System.ComponentModel.IComponent> is marshaled by value.</span></span> <span data-ttu-id="6dbdb-115">La liste suivante fournit des indications générales relatives aux implémenteurs.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-115">The following list provides broad guidelines for implementers.</span></span>  
  
-   <span data-ttu-id="6dbdb-116">Si votre composant doit être marshalé par référence, dérivez de <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-116">If your component needs to be marshaled by reference, derive from <xref:System.ComponentModel.Component>.</span></span>  
  
-   <span data-ttu-id="6dbdb-117">Si votre composant doit être marshalé par valeur, dérivez de <xref:System.ComponentModel.MarshalByValueComponent>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-117">If your component needs to be marshaled by value, derive from <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
-   <span data-ttu-id="6dbdb-118">Si votre composant ne peut pas dériver de l’une des implémentations de base en raison d’un héritage unique, implémentez <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-118">If your component cannot derive from one of the base implementations due to single inheritance, implement <xref:System.ComponentModel.IComponent>.</span></span>  
  
 <span data-ttu-id="6dbdb-119">Pour plus d’informations sur la prise en charge au moment du design, consultez [Attributs en mode design pour les composants](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3) et [Extension de la prise en charge au moment du design](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).</span><span class="sxs-lookup"><span data-stu-id="6dbdb-119">For more information about design-time support, see [Design-Time Attributes for Components](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3) and [Extending Design-Time Support](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).</span></span>  
  
## <a name="component-classes"></a><span data-ttu-id="6dbdb-120">Classes de composant</span><span class="sxs-lookup"><span data-stu-id="6dbdb-120">Component Classes</span></span>  
 <span data-ttu-id="6dbdb-121">L’espace de noms <xref:System.ComponentModel> fournit des classes utilisées pour implémenter le comportement des composants et des contrôles au moment de l’exécution et au moment du design.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-121">The <xref:System.ComponentModel> namespace provides classes that are used to implement the run-time and design-time behavior of components and controls.</span></span> <span data-ttu-id="6dbdb-122">Cet espace de noms inclut les classes et les interfaces de base servant à l’implémentation des attributs et des convertisseurs de type, à la liaison à des sources de données et à la gestion des licences des composants.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-122">This namespace includes the base classes and interfaces for implementing attributes and type converters, binding to data sources, and licensing components.</span></span>  
  
 <span data-ttu-id="6dbdb-123">Les classes de composant principales sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="6dbdb-123">The core component classes are:</span></span>  
  
-   <span data-ttu-id="6dbdb-124"><xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-124"><xref:System.ComponentModel.Component>.</span></span> <span data-ttu-id="6dbdb-125">Implémentation de base pour l’interface <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-125">A base implementation for the <xref:System.ComponentModel.IComponent> interface.</span></span> <span data-ttu-id="6dbdb-126">Cette classe permet le partage d’objets entre applications.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-126">This class enables object sharing between applications.</span></span>  
  
-   <span data-ttu-id="6dbdb-127"><xref:System.ComponentModel.MarshalByValueComponent>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-127"><xref:System.ComponentModel.MarshalByValueComponent>.</span></span> <span data-ttu-id="6dbdb-128">Implémentation de base pour l’interface <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-128">A base implementation for the <xref:System.ComponentModel.IComponent> interface.</span></span>  
  
-   <span data-ttu-id="6dbdb-129"><xref:System.ComponentModel.Container>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-129"><xref:System.ComponentModel.Container>.</span></span> <span data-ttu-id="6dbdb-130">Implémentation de base pour l’interface <xref:System.ComponentModel.IContainer>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-130">The base implementation for the <xref:System.ComponentModel.IContainer> interface.</span></span> <span data-ttu-id="6dbdb-131">Cette classe encapsule zéro, un ou plusieurs composants.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-131">This class encapsulates zero or more components.</span></span>  
  
 <span data-ttu-id="6dbdb-132">Les classes utilisées pour la gestion des licences des composants sont, entre autres, les suivantes :</span><span class="sxs-lookup"><span data-stu-id="6dbdb-132">Some of the classes used for component licensing are:</span></span>  
  
-   <span data-ttu-id="6dbdb-133"><xref:System.ComponentModel.License>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-133"><xref:System.ComponentModel.License>.</span></span> <span data-ttu-id="6dbdb-134">Classe de base abstraite pour toutes les licences.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-134">The abstract base class for all licenses.</span></span> <span data-ttu-id="6dbdb-135">Une licence est accordée à une instance spécifique d’un composant.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-135">A license is granted to a specific instance of a component.</span></span>  
  
-   <span data-ttu-id="6dbdb-136"><xref:System.ComponentModel.LicenseManager>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-136"><xref:System.ComponentModel.LicenseManager>.</span></span> <span data-ttu-id="6dbdb-137">Fournit des propriétés et des méthodes permettant d’ajouter une licence à un composant et de gérer un <xref:System.ComponentModel.LicenseProvider>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-137">Provides properties and methods to add a license to a component and to manage a <xref:System.ComponentModel.LicenseProvider>.</span></span>  
  
-   <span data-ttu-id="6dbdb-138"><xref:System.ComponentModel.LicenseProvider>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-138"><xref:System.ComponentModel.LicenseProvider>.</span></span> <span data-ttu-id="6dbdb-139">Classe de base abstraite pour l’implémentation d’un fournisseur de licences.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-139">The abstract base class for implementing a license provider.</span></span>  
  
-   <span data-ttu-id="6dbdb-140"><xref:System.ComponentModel.LicenseProviderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-140"><xref:System.ComponentModel.LicenseProviderAttribute>.</span></span> <span data-ttu-id="6dbdb-141">Spécifie la classe <xref:System.ComponentModel.LicenseProvider> à utiliser avec une classe.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-141">Specifies the <xref:System.ComponentModel.LicenseProvider> class to use with a class.</span></span>  
  
 <span data-ttu-id="6dbdb-142">Classes couramment utilisées pour la description et la persistance des composants.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-142">Classes commonly used for describing and persisting components.</span></span>  
  
-   <span data-ttu-id="6dbdb-143"><xref:System.ComponentModel.TypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-143"><xref:System.ComponentModel.TypeDescriptor>.</span></span> <span data-ttu-id="6dbdb-144">Fournit des informations relatives aux caractéristiques d’un composant, telles que ses attributs, ses propriétés et ses événements.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-144">Provides information about the characteristics for a component, such as its attributes, properties, and events.</span></span>  
  
-   <span data-ttu-id="6dbdb-145"><xref:System.ComponentModel.EventDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-145"><xref:System.ComponentModel.EventDescriptor>.</span></span> <span data-ttu-id="6dbdb-146">Fournit des informations sur un événement.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-146">Provides information about an event.</span></span>  
  
-   <span data-ttu-id="6dbdb-147"><xref:System.ComponentModel.PropertyDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-147"><xref:System.ComponentModel.PropertyDescriptor>.</span></span> <span data-ttu-id="6dbdb-148">Fournit des informations sur une propriété.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-148">Provides information about a property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6dbdb-149">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="6dbdb-149">Related Sections</span></span>  
 [<span data-ttu-id="6dbdb-150">Comparaison entre classe, composant et contrôle</span><span class="sxs-lookup"><span data-stu-id="6dbdb-150">Class vs. Component vs. Control</span></span>](http://msdn.microsoft.com/library/db8b842e-44d9-40cc-a0f8-70fd189632c3)  
 <span data-ttu-id="6dbdb-151">Définit les concepts de *composant* et de *contrôle*, et décrit les différences entre eux et les classes.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-151">Defines *component* and *control*, and discusses the differences between them and classes.</span></span>  
  
 [<span data-ttu-id="6dbdb-152">Création de composants</span><span class="sxs-lookup"><span data-stu-id="6dbdb-152">Component Authoring</span></span>](http://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 <span data-ttu-id="6dbdb-153">Documentation de présentation des composants.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-153">Roadmap for getting started with components.</span></span>  
  
 [<span data-ttu-id="6dbdb-154">Procédures pas à pas de la création de composants</span><span class="sxs-lookup"><span data-stu-id="6dbdb-154">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 <span data-ttu-id="6dbdb-155">Liens vers des rubriques fournissant des instructions étape par étape pour la programmation de composants.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-155">Links to topics that provide step-by-step instruction for component programming.</span></span>  
  
 [<span data-ttu-id="6dbdb-156">Classes de composant</span><span class="sxs-lookup"><span data-stu-id="6dbdb-156">Component Classes</span></span>](http://msdn.microsoft.com/library/ce2e5647-e673-4c2b-8125-ffebbd9d71bc)  
 <span data-ttu-id="6dbdb-157">Explique comment une classe devient un composant, comment exposer les fonctionnalités des composants, comment contrôler l’accès aux composants et comment contrôler la création des instances de composants.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-157">Describes what makes a class a component, ways to expose component functionality, controlling access to components, and controlling how component instances are created.</span></span>  
  
 [<span data-ttu-id="6dbdb-158">Dépannage de la création de contrôles et de composants</span><span class="sxs-lookup"><span data-stu-id="6dbdb-158">Troubleshooting Control and Component Authoring</span></span>](../../framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 <span data-ttu-id="6dbdb-159">Explique comment résoudre certains problèmes courants.</span><span class="sxs-lookup"><span data-stu-id="6dbdb-159">Explains how to fix common problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dbdb-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6dbdb-160">See Also</span></span>  
 <span data-ttu-id="6dbdb-161">[Comment : accéder à la prise en charge au moment du design dans les Windows Forms](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09) </span><span class="sxs-lookup"><span data-stu-id="6dbdb-161">[How to: Access Design-Time Support in Windows Forms](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09) </span></span>  
 <span data-ttu-id="6dbdb-162">[Comment : étendre l’apparence et le comportement des contrôles en mode design](http://msdn.microsoft.com/library/68f85054-2253-47f5-a4f2-3f1ac8c9f27b) </span><span class="sxs-lookup"><span data-stu-id="6dbdb-162">[How to: Extend the Appearance and Behavior of Controls in Design Mode](http://msdn.microsoft.com/library/68f85054-2253-47f5-a4f2-3f1ac8c9f27b) </span></span>  
 [<span data-ttu-id="6dbdb-163">Comment : effectuer une initialisation personnalisée pour les contrôles en mode design</span><span class="sxs-lookup"><span data-stu-id="6dbdb-163">How to: Perform Custom Initialization for Controls in Design Mode</span></span>](http://msdn.microsoft.com/library/914eaa03-092f-4556-9160-b8a2a40641d9)

