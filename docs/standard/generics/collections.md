---
title: "Collections génériques dans le .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], collections
- generic collections [.NET Framework]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 94da20072f793e137b0b7545c1a658ed20537a7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-collections-in-the-net-framework"></a><span data-ttu-id="9c964-102">Collections génériques dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9c964-102">Generic Collections in the .NET Framework</span></span>
<span data-ttu-id="9c964-103">Cette rubrique donne une vue d'ensemble des classes de collections génériques et d'autres types génériques dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9c964-103">This topic provides an overview of the generic collection classes and other generic types in the .NET Framework.</span></span>  
  
## <a name="generic-collections-in-the-net-framework"></a><span data-ttu-id="9c964-104">Collections génériques dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9c964-104">Generic Collections in the .NET Framework</span></span>  
 <span data-ttu-id="9c964-105">Le .NET Framework fournit plusieurs classes de collection génériques dans les espaces de noms <xref:System.Collections.Generic> et <xref:System.Collections.ObjectModel>.</span><span class="sxs-lookup"><span data-stu-id="9c964-105">The .NET Framework class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="9c964-106">Pour plus d’informations sur ces classes, consultez [utilisé Types de collections couramment](../../../docs/standard/collections/commonly-used-collection-types.md).</span><span class="sxs-lookup"><span data-stu-id="9c964-106">For more information about these classes, see [Commonly Used Collection Types](../../../docs/standard/collections/commonly-used-collection-types.md).</span></span>  
  
### <a name="systemcollectionsgeneric"></a><span data-ttu-id="9c964-107">System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="9c964-107">System.Collections.Generic</span></span>  
 <span data-ttu-id="9c964-108">La plupart des types de collections génériques sont des équivalents directs de types non génériques.</span><span class="sxs-lookup"><span data-stu-id="9c964-108">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="9c964-109"><xref:System.Collections.Generic.Dictionary%602> est une version générique de <xref:System.Collections.Hashtable> ; elle utilise la structure générique <xref:System.Collections.Generic.KeyValuePair%602> pour l'énumération, au lieu de <xref:System.Collections.DictionaryEntry>.</span><span class="sxs-lookup"><span data-stu-id="9c964-109"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="9c964-110"><xref:System.Collections.Generic.List%601> est une version générique de <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="9c964-110"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="9c964-111">Il existe des classes génériques <xref:System.Collections.Generic.Queue%601> et <xref:System.Collections.Generic.Stack%601> qui correspondent aux versions non génériques.</span><span class="sxs-lookup"><span data-stu-id="9c964-111">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="9c964-112">Il existe des versions génériques et non génériques de <xref:System.Collections.Generic.SortedList%602>.</span><span class="sxs-lookup"><span data-stu-id="9c964-112">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="9c964-113">Les deux versions sont des hybrides d'un dictionnaire et une liste.</span><span class="sxs-lookup"><span data-stu-id="9c964-113">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="9c964-114">La classe générique <xref:System.Collections.Generic.SortedDictionary%602> est un dictionnaire pur et n'a pas de contrepartie non générique.</span><span class="sxs-lookup"><span data-stu-id="9c964-114">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="9c964-115">La classe générique <xref:System.Collections.Generic.LinkedList%601> est une véritable liste liée.</span><span class="sxs-lookup"><span data-stu-id="9c964-115">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="9c964-116">Il n'a pas de contrepartie non générique.</span><span class="sxs-lookup"><span data-stu-id="9c964-116">It has no nongeneric counterpart.</span></span>  
  
### <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="9c964-117">System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="9c964-117">System.Collections.ObjectModel</span></span>  
 <span data-ttu-id="9c964-118">La classe générique <xref:System.Collections.ObjectModel.Collection%601> fournit une classe de base pour dériver vos propres types de collections génériques.</span><span class="sxs-lookup"><span data-stu-id="9c964-118">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="9c964-119">La classe <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> offre un moyen facile de produire une collection en lecture seule à partir de n'importe quel type implémentant l'interface générique <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="9c964-119">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="9c964-120">La classe générique <xref:System.Collections.ObjectModel.KeyedCollection%602> fournit un moyen de stocker des objets qui contiennent leurs propres clés.</span><span class="sxs-lookup"><span data-stu-id="9c964-120">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="9c964-121">Autres types génériques</span><span class="sxs-lookup"><span data-stu-id="9c964-121">Other Generic Types</span></span>  
 <span data-ttu-id="9c964-122">La structure générique <xref:System.Nullable%601> vous permet d'utiliser des types valeur comme si la valeur `null` pouvait leur être affectée.</span><span class="sxs-lookup"><span data-stu-id="9c964-122">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="9c964-123">Ceci peut être utile quand vous travaillez avec des requêtes de base de données, où des champs contenant des types valeur peuvent être manquants.</span><span class="sxs-lookup"><span data-stu-id="9c964-123">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="9c964-124">Le paramètre de type générique peut être n'importe quel type valeur.</span><span class="sxs-lookup"><span data-stu-id="9c964-124">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c964-125">En C#, il n'est pas nécessaire d'utiliser <xref:System.Nullable%601> explicitement, car le langage a une syntaxe pour les types Nullable.</span><span class="sxs-lookup"><span data-stu-id="9c964-125">In C# it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span>  
  
 <span data-ttu-id="9c964-126">La structure générique <xref:System.ArraySegment%601> offre un moyen de délimiter une plage d'éléments dans un tableau unidimensionnel de base zéro, de n'importe quel type.</span><span class="sxs-lookup"><span data-stu-id="9c964-126">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="9c964-127">Le paramètre de type générique est le type des éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="9c964-127">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="9c964-128">Le délégué générique <xref:System.EventHandler%601> élimine le besoin de déclarer un type de délégué pour gérer les événements, si votre événement respecte le modèle de gestion des événements utilisé par le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9c964-128">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="9c964-129">Par exemple, supposons que vous avez créé une classe `MyEventArgs` dérivée de <xref:System.EventArgs>, pour stocker les données de votre événement.</span><span class="sxs-lookup"><span data-stu-id="9c964-129">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="9c964-130">Vous pouvez ensuite déclarer l'événement comme suit :</span><span class="sxs-lookup"><span data-stu-id="9c964-130">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="9c964-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c964-131">See Also</span></span>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [<span data-ttu-id="9c964-132">Génériques</span><span class="sxs-lookup"><span data-stu-id="9c964-132">Generics</span></span>](../../../docs/standard/generics/index.md)  
 [<span data-ttu-id="9c964-133">Délégués génériques pour la manipulation de tableaux et de listes</span><span class="sxs-lookup"><span data-stu-id="9c964-133">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [<span data-ttu-id="9c964-134">Interfaces génériques</span><span class="sxs-lookup"><span data-stu-id="9c964-134">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)
