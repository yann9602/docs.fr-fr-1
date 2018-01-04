---
title: x:Members, directive
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e76f539e713f3d21751de18c86cc2dcebf99f570
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xmembers-directive"></a><span data-ttu-id="f0503-102">x:Members, directive</span><span class="sxs-lookup"><span data-stu-id="f0503-102">x:Members Directive</span></span>
<span data-ttu-id="f0503-103">Contient un jeu de membres qui sont définis dans le balisage, et qui s’appliquent à x : Class de l’élément parent.</span><span class="sxs-lookup"><span data-stu-id="f0503-103">Holds a set of members that are defined in markup, which apply to the x:Class of the parent element.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="f0503-104">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="f0503-104">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="f0503-105">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="f0503-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`className`|<span data-ttu-id="f0503-106">Nom de la classe de stockage ou de la classe partielle pour la production XAML.</span><span class="sxs-lookup"><span data-stu-id="f0503-106">Name of the backing class or partial class for the XAML production.</span></span> <span data-ttu-id="f0503-107">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="f0503-107">See Remarks.</span></span>|  
|`oneOrMoreMembers`|<span data-ttu-id="f0503-108">Un ou plusieurs éléments objet qui représentent des définitions de membre.</span><span class="sxs-lookup"><span data-stu-id="f0503-108">One or more object elements that represent member definitions.</span></span> <span data-ttu-id="f0503-109">En règle générale, il s’agit `x:Property` éléments objet.</span><span class="sxs-lookup"><span data-stu-id="f0503-109">Typically, these are `x:Property` object elements.</span></span> <span data-ttu-id="f0503-110">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="f0503-110">See Remarks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0503-111">Notes</span><span class="sxs-lookup"><span data-stu-id="f0503-111">Remarks</span></span>  
 <span data-ttu-id="f0503-112">Dans l’implémentation de Services XAML .NET Framework, il n’existe aucune classe de stockage ou d’une implémentation d’un membre sous-jacent pour `x:Members`.</span><span class="sxs-lookup"><span data-stu-id="f0503-112">In the .NET Framework XAML Services implementation, there is no backing class or underlying member implementation for `x:Members`.</span></span> <span data-ttu-id="f0503-113">`x:Members`est un membre XAML spécial qui peut exister en tant que membre sur n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="f0503-113">`x:Members` is a special XAML member that can exist as a member on any type.</span></span> <span data-ttu-id="f0503-114">Dans un flux de nœud XAML, `x:Members` est représenté sous la forme d’un membre nommé `Members`, à partir de l’espace de noms XAML du langage XAML.</span><span class="sxs-lookup"><span data-stu-id="f0503-114">In a XAML node stream, `x:Members` is represented as a member named `Members`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="f0503-115">Le membre `Members` contient une liste générique en lecture seule de `Member` objets.</span><span class="sxs-lookup"><span data-stu-id="f0503-115">The member `Members` contains a read-only generic list of `Member` objects.</span></span> <span data-ttu-id="f0503-116">Dans le balisage par défaut, les membres individuels sont spécifiés comme `x:Property` éléments de propriété.</span><span class="sxs-lookup"><span data-stu-id="f0503-116">In typical markup the individual members are specified as `x:Property` property elements.</span></span> <span data-ttu-id="f0503-117">`x:Property`est un type plus précis, en particulier pour les propriétés des types et ne peut être assigné à `x:Member`.</span><span class="sxs-lookup"><span data-stu-id="f0503-117">`x:Property` is a more precise type specifically for properties of types and is assignable to `x:Member`.</span></span> <span data-ttu-id="f0503-118">Pour plus d’informations, consultez [x : Property Directive](../../../docs/framework/xaml-services/x-property-directive.md).</span><span class="sxs-lookup"><span data-stu-id="f0503-118">For more information, see [x:Property Directive](../../../docs/framework/xaml-services/x-property-directive.md).</span></span>  
  
 <span data-ttu-id="f0503-119">Pour pouvoir utiliser `x:Members` afin de spécifier des définitions de membre dans le balisage, les membres doivent être associés à une classe modifiable.</span><span class="sxs-lookup"><span data-stu-id="f0503-119">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="f0503-120">Dans le modèle prévu, `x:Members` existe en tant que membre d'un type qui spécifie un objet `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="f0503-120">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="f0503-121">Toutefois, le mécanisme permettant d'associer des types et des membres ou de générer des définitions de membre dynamique n'est pas pris en charge au niveau des services XAML .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f0503-121">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at the .NET Framework XAML Services level.</span></span> <span data-ttu-id="f0503-122">En revanche, chaque infrastructure dispose de modèles d'application qui prennent en charge les définitions de membre XAML.</span><span class="sxs-lookup"><span data-stu-id="f0503-122">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="f0503-123">Généralement, les actions de génération MSBUILD qui balisent-compilent le XAML et, soit lui intègre du code-behind, soit produisent des assemblys purement XAML, sont nécessaires pour prendre en charge cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="f0503-123">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>  
  
## <a name="xmembers-for-windows-workflow-foundation"></a><span data-ttu-id="f0503-124">x : Members pour Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="f0503-124">x:Members for Windows Workflow Foundation</span></span>  
 <span data-ttu-id="f0503-125">Pour Windows Workflow Foundation, `x:Members` contient les membres d’une activité personnalisée entièrement composée en XAML ou XAML : défini par les membres dynamiques pour un concepteur d’activités avec code-behind.</span><span class="sxs-lookup"><span data-stu-id="f0503-125">For Windows Workflow Foundation, `x:Members` contains the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="f0503-126">L'objet `x:Class` doit également être spécifié sur l'élément racine de la production XAML.</span><span class="sxs-lookup"><span data-stu-id="f0503-126">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="f0503-127">Cela n’est pas obligatoire dans le cadre des services XAML .NET Framework, mais le devient quand la production XAML est chargée par les actions de génération MSBUILD qui prennent en charge les activités personnalisées et le XAML de Windows Workflow Foundation en général.</span><span class="sxs-lookup"><span data-stu-id="f0503-127">This is not a requirement at the .NET Framework XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="f0503-128">`x:Members`doit être le premier élément enfant dans le balisage de l’élément objet qui déclare le `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="f0503-128">`x:Members` must be the first child element in markup of the object element that declares the `x:Class`.</span></span>
