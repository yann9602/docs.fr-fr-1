---
title: "Génériques dans la bibliothèque de classes .NET Framework (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], in .NET Framework class library
ms.assetid: afdd5477-6770-4686-8297-f58a4d749daf
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
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
ms.openlocfilehash: f3d5f15c92031301b68c6a702cf8d6b135cca36d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="generics-in-the-net-framework-class-library-c-programming-guide"></a><span data-ttu-id="ac5eb-102">Génériques dans la bibliothèque de classes .NET Framework (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="ac5eb-102">Generics in the .NET Framework Class Library (C# Programming Guide)</span></span>
<span data-ttu-id="ac5eb-103">La version 2.0 de la bibliothèque de classes .NET Framework fournit un nouvel espace de noms, <xref:System.Collections.Generic>, qui inclut plusieurs classes de collections génériques prêtes à l’emploi, ainsi que les interfaces associées.</span><span class="sxs-lookup"><span data-stu-id="ac5eb-103">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which includes several ready-to-use generic collection classes and associated interfaces.</span></span> <span data-ttu-id="ac5eb-104">D’autres espaces de noms, tels que <xref:System>, fournissent également de nouvelles interfaces génériques comme <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="ac5eb-104">Other namespaces, such as <xref:System>, also provide new generic interfaces such as <xref:System.IComparable%601>.</span></span> <span data-ttu-id="ac5eb-105">Ces classes et ces interfaces sont de type sécurisé et sont plus efficaces que les classes de collection non générique fournies dans les versions antérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ac5eb-105">These classes and interfaces are more efficient and type-safe than the non-generic collection classes provided in earlier releases of the .NET Framework.</span></span> <span data-ttu-id="ac5eb-106">Avant de concevoir et d’implémenter vos propres classes de collection personnalisées, envisagez d’utiliser ou de dériver une classe d’une des classes fournies dans la bibliothèque de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ac5eb-106">Before designing and implementing your own custom collection classes, consider whether you can use or derive a class from one of the classes provided in the .NET Framework class library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac5eb-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac5eb-107">See Also</span></span>  
 <span data-ttu-id="ac5eb-108">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ac5eb-108">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ac5eb-109">[Quand utiliser les collections génériques](../../../standard/collections/when-to-use-generic-collections.md) </span><span class="sxs-lookup"><span data-stu-id="ac5eb-109">[When to Use Generic Collections](../../../standard/collections/when-to-use-generic-collections.md) </span></span>  
 <span data-ttu-id="ac5eb-110">[Collections et structures de données](../../../standard/collections/index.md) </span><span class="sxs-lookup"><span data-stu-id="ac5eb-110">[Collections and Data Structures](../../../standard/collections/index.md) </span></span>  
 [<span data-ttu-id="ac5eb-111">Introduction aux génériques</span><span class="sxs-lookup"><span data-stu-id="ac5eb-111">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)

