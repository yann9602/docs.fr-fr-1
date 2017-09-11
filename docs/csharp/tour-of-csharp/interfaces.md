---
title: "Interfaces C# - Visite guidée du langage C#"
description: "Les interfaces définissent des contrats implémentés par les types en C#"
keywords: ".NET, csharp, interfaces, héritage multiple, polymorphisme"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 673ac56f3f5732fcda02d313b6f4273708ae365f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="interfaces"></a><span data-ttu-id="6d972-104">Interfaces</span><span class="sxs-lookup"><span data-stu-id="6d972-104">Interfaces</span></span>

<span data-ttu-id="6d972-105">Une ***interface*** définit un contrat qui peut être implémenté par des classes et structures.</span><span class="sxs-lookup"><span data-stu-id="6d972-105">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="6d972-106">Une interface peut contenir des méthodes, des propriétés, des événements et des indexeurs.</span><span class="sxs-lookup"><span data-stu-id="6d972-106">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="6d972-107">Une interface ne fournit pas les implémentations des membres qu’elle définit, elle indique simplement les membres qui doivent être fournis par les classes ou les structs qui implémentent l’interface.</span><span class="sxs-lookup"><span data-stu-id="6d972-107">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="6d972-108">Les interfaces peuvent utiliser ***l’héritage multiple***.</span><span class="sxs-lookup"><span data-stu-id="6d972-108">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="6d972-109">Dans l’exemple suivant, l’interface `IComboBox` hérite à la fois de `ITextBox` et `IListBox`.</span><span class="sxs-lookup"><span data-stu-id="6d972-109">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

<span data-ttu-id="6d972-110">[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]</span><span class="sxs-lookup"><span data-stu-id="6d972-110">[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]</span></span>

<span data-ttu-id="6d972-111">Les classes et les structs peuvent implémenter plusieurs interfaces.</span><span class="sxs-lookup"><span data-stu-id="6d972-111">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="6d972-112">Dans l’exemple suivant, la classe `EditBox` implémente à la fois `IControl` et `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="6d972-112">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

<span data-ttu-id="6d972-113">[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]</span><span class="sxs-lookup"><span data-stu-id="6d972-113">[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]</span></span>

<span data-ttu-id="6d972-114">Lorsqu’une classe ou un struct implémente une interface spécifique, les instances de cette classe ou struct peuvent être converties implicitement en ce type d’interface.</span><span class="sxs-lookup"><span data-stu-id="6d972-114">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="6d972-115">Exemple :</span><span class="sxs-lookup"><span data-stu-id="6d972-115">For example</span></span>

<span data-ttu-id="6d972-116">[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]</span><span class="sxs-lookup"><span data-stu-id="6d972-116">[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]</span></span>

<span data-ttu-id="6d972-117">Si une instance n’est pas connue pour implémenter une interface donnée de façon statique, des casts de type dynamiques peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="6d972-117">In cases where an instance is not statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="6d972-118">Par exemple, les instructions suivantes utilisent des casts de type dynamiques pour obtenir les implémentations des interfaces `IControl` et `IDataBound` d’un objet.</span><span class="sxs-lookup"><span data-stu-id="6d972-118">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="6d972-119">Étant donné que le type réel au moment de l’exécution de l’objet est `EditBox`, les casts réussissent.</span><span class="sxs-lookup"><span data-stu-id="6d972-119">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

<span data-ttu-id="6d972-120">[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]</span><span class="sxs-lookup"><span data-stu-id="6d972-120">[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]</span></span>

<span data-ttu-id="6d972-121">Dans la classe `EditBox` précédente, la méthode `Paint` de l’interface `IControl` et la méthode `Bind` de l’interface `IDataBound` sont implémentées à l’aide des membres publics.</span><span class="sxs-lookup"><span data-stu-id="6d972-121">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="6d972-122">C# prend également en charge les ***implémentations de membres d’interface*** explicites, permettant ainsi à la classe ou structure d’éviter d’avoir à créer des membres publics.</span><span class="sxs-lookup"><span data-stu-id="6d972-122">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="6d972-123">Une implémentation de membre d’interface explicite est écrite à l’aide du nom de membre d’interface qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="6d972-123">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="6d972-124">Par exemple, la classe `EditBox` peut implémenter les méthodes `IControl.Paint` et `IDataBound.Bind` à l’aide des implémentations de membres d’interface explicites, comme suit.</span><span class="sxs-lookup"><span data-stu-id="6d972-124">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

<span data-ttu-id="6d972-125">[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]</span><span class="sxs-lookup"><span data-stu-id="6d972-125">[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]</span></span>

<span data-ttu-id="6d972-126">Les membres d’interface explicites sont accessibles uniquement via le type interface.</span><span class="sxs-lookup"><span data-stu-id="6d972-126">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="6d972-127">Par exemple, l’implémentation de `IControl.Paint` fournie par la classe EditBox précédente ne peut être appelée en convertissant d’abord l’ `EditBox` en référence vers le type d’interface `IControl`.</span><span class="sxs-lookup"><span data-stu-id="6d972-127">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

<span data-ttu-id="6d972-128">[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]</span><span class="sxs-lookup"><span data-stu-id="6d972-128">[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="6d972-129">[Précédent](arrays.md)
[Suivant](enums.md)</span><span class="sxs-lookup"><span data-stu-id="6d972-129">[Previous](arrays.md)
[Next](enums.md)</span></span>

