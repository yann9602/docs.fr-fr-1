---
title: "Références faibles"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 906c23caa7065486bb094ad2475ed9e7e24b3d9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="weak-references"></a><span data-ttu-id="8a035-102">Références faibles</span><span class="sxs-lookup"><span data-stu-id="8a035-102">Weak References</span></span>
<span data-ttu-id="8a035-103">Le Garbage collector ne peut pas collecter un objet actuellement utilisé par une application, tandis que le code de l’application peut accéder à cet objet.</span><span class="sxs-lookup"><span data-stu-id="8a035-103">The garbage collector cannot collect an object in use by an application while the application's code can reach that object.</span></span> <span data-ttu-id="8a035-104">On dit de l’application qu’elle a une référence forte à l’objet.</span><span class="sxs-lookup"><span data-stu-id="8a035-104">The application is said to have a strong reference to the object.</span></span>  
  
 <span data-ttu-id="8a035-105">Une référence faible permet au Garbage collector de collecter l’objet tout en permettant à l’application d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="8a035-105">A weak reference permits the garbage collector to collect the object while still allowing the application to access the object.</span></span> <span data-ttu-id="8a035-106">Une référence faible est valide uniquement pour une période indéterminée jusqu’à ce que l’objet soit collecté quand il n’existe aucune référence forte.</span><span class="sxs-lookup"><span data-stu-id="8a035-106">A weak reference is valid only during the indeterminate amount of time until the object is collected when no strong references exist.</span></span> <span data-ttu-id="8a035-107">Quand vous utilisez une référence faible, l’application peut toujours obtenir une référence forte à l’objet, ce qui l’empêche d’être collecté.</span><span class="sxs-lookup"><span data-stu-id="8a035-107">When you use a weak reference, the application can still obtain a strong reference to the object, which prevents it from being collected.</span></span> <span data-ttu-id="8a035-108">Toutefois, il existe toujours un risque que le Garbage collector accède à l’objet avant qu’une référence forte soit rétablie.</span><span class="sxs-lookup"><span data-stu-id="8a035-108">However, there is always the risk that the garbage collector will get to the object first before a strong reference is reestablished.</span></span>  
  
 <span data-ttu-id="8a035-109">Les références faibles sont utiles pour les objets qui utilisent beaucoup de mémoire, mais peuvent être recréées facilement si elles sont récupérées par le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="8a035-109">Weak references are useful for objects that use a lot of memory, but can be recreated easily if they are reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="8a035-110">Supposez qu’une arborescence dans une application Windows Forms affiche un choix hiérarchique complex d’options à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8a035-110">Suppose a tree view in a Windows Forms application displays a complex hierarchical choice of options to the user.</span></span> <span data-ttu-id="8a035-111">Si les données sous-jacentes sont volumineuses, la conservation de l’arborescence en mémoire est inefficace quand l’utilisateur est impliqué dans un autre élément de l’application.</span><span class="sxs-lookup"><span data-stu-id="8a035-111">If the underlying data is large, keeping the tree in memory is inefficient when the user is involved with something else in the application.</span></span>  
  
 <span data-ttu-id="8a035-112">Lorsque l’utilisateur passe à une autre partie de l’application, vous pouvez utiliser la <xref:System.WeakReference> classe pour créer une référence faible à l’arborescence et la destruction de toutes les références fortes.</span><span class="sxs-lookup"><span data-stu-id="8a035-112">When the user switches away to another part of the application, you can use the <xref:System.WeakReference> class to create a weak reference to the tree and destroy all strong references.</span></span> <span data-ttu-id="8a035-113">Quand l’utilisateur revient à l’arborescence, l’application tente d’obtenir une référence forte à l’arborescence et, en cas de réussite, évite de reconstruire l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="8a035-113">When the user switches back to the tree, the application attempts to obtain a strong reference to the tree and, if successful, avoids reconstructing the tree.</span></span>  
  
 <span data-ttu-id="8a035-114">Pour établir une référence faible à un objet, vous créez un <xref:System.WeakReference> à l’aide de l’instance de l’objet à suivre.</span><span class="sxs-lookup"><span data-stu-id="8a035-114">To establish a weak reference with an object, you create a <xref:System.WeakReference> using the instance of the object to be tracked.</span></span> <span data-ttu-id="8a035-115">Vous définissez ensuite la <xref:System.WeakReference.Target%2A> à cet objet et le jeu d’origine font référence à l’objet de propriété `null`.</span><span class="sxs-lookup"><span data-stu-id="8a035-115">You then set the <xref:System.WeakReference.Target%2A> property to that object and set the original reference to the object to `null`.</span></span> <span data-ttu-id="8a035-116">Pour obtenir un exemple de code, consultez <xref:System.WeakReference> dans la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="8a035-116">For a code example, see <xref:System.WeakReference> in the class library.</span></span>  
  
## <a name="short-and-long-weak-references"></a><span data-ttu-id="8a035-117">Références faibles courtes et longues</span><span class="sxs-lookup"><span data-stu-id="8a035-117">Short and Long Weak References</span></span>  
 <span data-ttu-id="8a035-118">Vous pouvez créer une référence faible courte ou une référence faible longue :</span><span class="sxs-lookup"><span data-stu-id="8a035-118">You can create a short weak reference or a long weak reference:</span></span>  
  
-   <span data-ttu-id="8a035-119">Courte</span><span class="sxs-lookup"><span data-stu-id="8a035-119">Short</span></span>  
  
     <span data-ttu-id="8a035-120">La cible d’une référence faible courte devient `null` quand l’objet est récupéré par le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="8a035-120">The target of a short weak reference becomes `null` when the object is reclaimed by garbage collection.</span></span> <span data-ttu-id="8a035-121">La référence faible est elle-même un objet managé et fait l’objet d’un garbage collection comme tout autre objet managé.</span><span class="sxs-lookup"><span data-stu-id="8a035-121">The weak reference is itself a managed object, and is subject to garbage collection just like any other managed object.</span></span>  <span data-ttu-id="8a035-122">Une référence faible courte est le constructeur par défaut <xref:System.WeakReference>.</span><span class="sxs-lookup"><span data-stu-id="8a035-122">A short weak reference is the default constructor for <xref:System.WeakReference>.</span></span>  
  
-   <span data-ttu-id="8a035-123">Long</span><span class="sxs-lookup"><span data-stu-id="8a035-123">Long</span></span>  
  
     <span data-ttu-id="8a035-124">Une référence faible longue est conservée après l’objet <xref:System.Object.Finalize%2A> méthode a été appelée.</span><span class="sxs-lookup"><span data-stu-id="8a035-124">A long weak reference is retained after the object's <xref:System.Object.Finalize%2A> method has been called.</span></span> <span data-ttu-id="8a035-125">Cela permet à l’objet d’être recréé, mais l’état de l’objet reste imprévisible.</span><span class="sxs-lookup"><span data-stu-id="8a035-125">This allows the object to be recreated, but the state of the object remains unpredictable.</span></span> <span data-ttu-id="8a035-126">Pour utiliser une référence longue, spécifiez `true` dans le <xref:System.WeakReference> constructeur.</span><span class="sxs-lookup"><span data-stu-id="8a035-126">To use a long reference, specify `true` in the <xref:System.WeakReference> constructor.</span></span>  
  
     <span data-ttu-id="8a035-127">Si le type d’objet n’a pas un <xref:System.Object.Finalize%2A> (méthode), la référence faible courte fonctionnalité s’applique et la référence faible est valide uniquement jusqu'à ce que la cible est collectée, qui peut se produire à tout moment après le finaliseur n’est exécuté.</span><span class="sxs-lookup"><span data-stu-id="8a035-127">If the object's type does not have a <xref:System.Object.Finalize%2A> method, the short weak reference functionality applies and the weak reference is valid only until the target is collected, which can occur anytime after the finalizer is run.</span></span>  
  
 <span data-ttu-id="8a035-128">Pour établir une référence forte et utiliser à nouveau l’objet, effectuez un cast du <xref:System.WeakReference.Target%2A> propriété d’un <xref:System.WeakReference> pour le type de l’objet.</span><span class="sxs-lookup"><span data-stu-id="8a035-128">To establish a strong reference and use the object again, cast the <xref:System.WeakReference.Target%2A> property of a <xref:System.WeakReference> to the type of the object.</span></span> <span data-ttu-id="8a035-129">Si le <xref:System.WeakReference.Target%2A> propriété renvoie `null`, l’objet a été collecté ; sinon, vous pouvez continuer à utiliser l’objet, car l’application a récupéré une référence forte à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="8a035-129">If the <xref:System.WeakReference.Target%2A> property returns `null`, the object was collected; otherwise, you can continue to use the object because the application has regained a strong reference to it.</span></span>  
  
## <a name="guidelines-for-using-weak-references"></a><span data-ttu-id="8a035-130">Instructions d’utilisation de références faibles</span><span class="sxs-lookup"><span data-stu-id="8a035-130">Guidelines for Using Weak References</span></span>  
 <span data-ttu-id="8a035-131">Utilisez des références faibles longues uniquement quand cela est nécessaire, car l’état de l’objet est imprévisible après la finalisation.</span><span class="sxs-lookup"><span data-stu-id="8a035-131">Use long weak references only when necessary as the state of the object is unpredictable after finalization.</span></span>  
  
 <span data-ttu-id="8a035-132">Évitez d’utiliser des références faibles aux petits objets, car le pointeur lui-même peut être de la même taille ou d’une taille supérieure.</span><span class="sxs-lookup"><span data-stu-id="8a035-132">Avoid using weak references to small objects because the pointer itself may be as large or larger.</span></span>  
  
 <span data-ttu-id="8a035-133">Évitez d’utiliser les références faibles comme solution automatique aux problèmes de gestion de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="8a035-133">Avoid using weak references as an automatic solution to memory management problems.</span></span> <span data-ttu-id="8a035-134">Développez plutôt une stratégie de mise en cache efficace pour gérer les objets de votre application.</span><span class="sxs-lookup"><span data-stu-id="8a035-134">Instead, develop an effective caching policy for handling your application's objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a035-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a035-135">See Also</span></span>  
 [<span data-ttu-id="8a035-136">Nettoyage de la mémoire</span><span class="sxs-lookup"><span data-stu-id="8a035-136">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
