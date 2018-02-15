---
title: "Dispose, modèle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e0c2e74afea8a0cb5a0e187f05511eabe0527b90
ms.sourcegitcommit: 08684dd61444c2f072b89b926370f750e456fca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="dispose-pattern"></a><span data-ttu-id="9e8c6-102">Dispose, modèle</span><span class="sxs-lookup"><span data-stu-id="9e8c6-102">Dispose Pattern</span></span>
<span data-ttu-id="9e8c6-103">Tous les programmes d’acquérir une ou plusieurs ressources système, telles que la mémoire, les handles du système ou les connexions de base de données, au cours de leur exécution.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-103">All programs acquire one or more system resources, such as memory, system handles, or database connections, during the course of their execution.</span></span> <span data-ttu-id="9e8c6-104">Les développeurs doivent être prudent lors de l’utilisation de ces ressources système, car ils doivent être libérées après que qu’ils ont été acquis et utilisés.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-104">Developers have to be careful when using such system resources, because they must be released after they have been acquired and used.</span></span>  
  
 <span data-ttu-id="9e8c6-105">Le CLR prend en charge pour la gestion automatique de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-105">The CLR provides support for automatic memory management.</span></span> <span data-ttu-id="9e8c6-106">La mémoire managée (mémoire allouée à l’aide de l’opérateur c# `new`) n'a pas besoin d’être libérées de manière explicite.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-106">Managed memory (memory allocated using the C# operator `new`) does not need to be explicitly released.</span></span> <span data-ttu-id="9e8c6-107">Il est publié automatiquement par le garbage collector (GC).</span><span class="sxs-lookup"><span data-stu-id="9e8c6-107">It is released automatically by the garbage collector (GC).</span></span> <span data-ttu-id="9e8c6-108">Cela évite aux développeurs de la tâche fastidieuse et difficile de libération de mémoire et a été une des principales raisons de la productivité sans précédent offertes par le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-108">This frees developers from the tedious and difficult task of releasing memory and has been one of the main reasons for the unprecedented productivity afforded by the .NET Framework.</span></span>  
  
 <span data-ttu-id="9e8c6-109">Malheureusement, la mémoire managée est simplement un des nombreux types de ressources système.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-109">Unfortunately, managed memory is just one of many types of system resources.</span></span> <span data-ttu-id="9e8c6-110">Ressources autres que la mémoire managée toujours doivent être libérées explicitement et sont appelés les ressources non managées.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-110">Resources other than managed memory still need to be released explicitly and are referred to as unmanaged resources.</span></span> <span data-ttu-id="9e8c6-111">Le catalogue global a été pas spécifiquement conçu pour gérer ces ressources non managées, ce qui signifie que la responsabilité de la gestion des ressources non managées se trouve entre les mains des développeurs.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-111">The GC was specifically not designed to manage such unmanaged resources, which means that the responsibility for managing unmanaged resources lies in the hands of the developers.</span></span>  
  
 <span data-ttu-id="9e8c6-112">Le CLR fournit une aide à la libération de ressources non managées.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-112">The CLR provides some help in releasing unmanaged resources.</span></span> <span data-ttu-id="9e8c6-113"><xref:System.Object?displayProperty=nameWithType> déclare une méthode virtuelle <xref:System.Object.Finalize%2A> (également appelé le finaliseur) qui est appelée par le garbage collector avant que la mémoire de l’objet ne soit récupérée par le garbage collector et peut être substituée pour libérer les ressources non managées.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-113"><xref:System.Object?displayProperty=nameWithType> declares a virtual method <xref:System.Object.Finalize%2A> (also called the finalizer) that is called by the GC before the object’s memory is reclaimed by the GC and can be overridden to release unmanaged resources.</span></span> <span data-ttu-id="9e8c6-114">Types de se substituer au finaliseur sont appelés types finalisables.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-114">Types that override the finalizer are referred to as finalizable types.</span></span>  
  
 <span data-ttu-id="9e8c6-115">Bien que les finaliseurs sont efficaces dans certains scénarios de nettoyage, ils ont deux inconvénients importants :</span><span class="sxs-lookup"><span data-stu-id="9e8c6-115">Although finalizers are effective in some cleanup scenarios, they have two significant drawbacks:</span></span>  
  
-   <span data-ttu-id="9e8c6-116">Le finaliseur est appelé lorsque le garbage collector détecte qu’un objet est éligible pour la collection.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-116">The finalizer is called when the GC detects that an object is eligible for collection.</span></span> <span data-ttu-id="9e8c6-117">Cela se produit sur une période indéterminée de temps une fois que la ressource n’est plus nécessaire.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-117">This happens at some undetermined period of time after the resource is not needed anymore.</span></span> <span data-ttu-id="9e8c6-118">Le délai entre lorsque le développeur peut ou souhaitez libérer la ressource et l’heure lorsque la ressource est libérée réellement par le finaliseur peut être inacceptable dans les programmes qui acquièrent de nombreuses ressources rares (les ressources qui peuvent être utilisées intégralement facilement) ou dans cas dans lequel les ressources sont coûteux à conserver en cours d’utilisation (par exemple, les tampons de grande taille de mémoire non managée).</span><span class="sxs-lookup"><span data-stu-id="9e8c6-118">The delay between when the developer could or would like to release the resource and the time when the resource is actually released by the finalizer might be unacceptable in programs that acquire many scarce resources (resources that can be easily exhausted) or in cases in which resources are costly to keep in use (e.g., large unmanaged memory buffers).</span></span>  
  
-   <span data-ttu-id="9e8c6-119">Lorsque le CLR a besoin d’appeler un finaliseur, il doit reporter la collecte de mémoire de l’objet jusqu'à ce que la prochaine arrondir du garbage collection (exécuter entre les collections les finaliseurs).</span><span class="sxs-lookup"><span data-stu-id="9e8c6-119">When the CLR needs to call a finalizer, it must postpone collection of the object’s memory until the next round of garbage collection (the finalizers run between collections).</span></span> <span data-ttu-id="9e8c6-120">Cela signifie que les mémoire de l’objet (et tous les objets qu’il fait référence au) ne seront pas libérées pour une période plus longue.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-120">This means that the object’s memory (and all objects it refers to) will not be released for a longer period of time.</span></span>  
  
 <span data-ttu-id="9e8c6-121">Par conséquent, exclusivement sur les finaliseurs de partie de confiance peut ne pas convenir dans de nombreux scénarios quand il est important de libérer les ressources non managées aussi rapidement que possible, lorsque vous traitez des ressources rares ou dans hautement performant scénarios dans lesquels la surcharge GC ajoutée de la finalisation n’est pas acceptable.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-121">Therefore, relying exclusively on finalizers might not be appropriate in many scenarios when it is important to reclaim unmanaged resources as quickly as possible, when dealing with scarce resources, or in highly performant scenarios in which the added GC overhead of finalization is unacceptable.</span></span>  
  
 <span data-ttu-id="9e8c6-122">Le Framework fournit la <xref:System.IDisposable?displayProperty=nameWithType> interface qui doit être implémentée pour fournir aux développeurs un moyen manuel de libérer les ressources non managées, dès qu’ils ne sont pas nécessaires.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-122">The Framework provides the <xref:System.IDisposable?displayProperty=nameWithType> interface that should be implemented to provide the developer a manual way to release unmanaged resources as soon as they are not needed.</span></span> <span data-ttu-id="9e8c6-123">Il fournit également la <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> méthode pouvant indiquer le garbage collector qui un objet a été supprimé manuellement et ne doive pas être finalisée, auquel cas la mémoire de l’objet peut être récupérée de plus haut.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-123">It also provides the <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> method that can tell the GC that an object was manually disposed of and does not need to be finalized anymore, in which case the object’s memory can be reclaimed earlier.</span></span> <span data-ttu-id="9e8c6-124">Les types qui implémentent la `IDisposable` interface sont considérés comme des types pouvant être supprimés.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-124">Types that implement the `IDisposable` interface are referred to as disposable types.</span></span>  
  
 <span data-ttu-id="9e8c6-125">Le modèle Dispose est destiné à normaliser l’utilisation et l’implémentation des finaliseurs et `IDisposable` interface.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-125">The Dispose Pattern is intended to standardize the usage and implementation of finalizers and the `IDisposable` interface.</span></span>  
  
 <span data-ttu-id="9e8c6-126">La motivation principale pour le modèle consiste à réduire la complexité de l’implémentation de la <xref:System.Object.Finalize%2A> et <xref:System.IDisposable.Dispose%2A> méthodes.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-126">The main motivation for the pattern is to reduce the complexity of the implementation of the <xref:System.Object.Finalize%2A> and the <xref:System.IDisposable.Dispose%2A> methods.</span></span> <span data-ttu-id="9e8c6-127">La complexité vient du fait que les méthodes partagent certains, mais pas tous les chemins de code (les différences sont décrites plus loin dans ce chapitre).</span><span class="sxs-lookup"><span data-stu-id="9e8c6-127">The complexity stems from the fact that the methods share some but not all code paths (the differences are described later in the chapter).</span></span> <span data-ttu-id="9e8c6-128">En outre, il existe des raisons historiques pour certains éléments du modèle liés à l’évolution de la prise en charge linguistique pour la gestion des ressources déterministe.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-128">In addition, there are historical reasons for some elements of the pattern related to the evolution of language support for deterministic resource management.</span></span>  
  
 <span data-ttu-id="9e8c6-129">**✓ FAIRE** implémenter le modèle de suppression de base sur les types contenant des instances de types pouvant être supprimés.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-129">**✓ DO** implement the Basic Dispose Pattern on types containing instances of disposable types.</span></span> <span data-ttu-id="9e8c6-130">Consultez le [base modèle Dispose](#basic_pattern) pour plus d’informations sur le modèle de base.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-130">See the [Basic Dispose Pattern](#basic_pattern) section for details on the basic pattern.</span></span>  
  
 <span data-ttu-id="9e8c6-131">Si un type est chargé pour la durée de vie d’autres objets pouvant être supprimés, les développeurs ont besoin d’un moyen de les supprimer, trop.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-131">If a type is responsible for the lifetime of other disposable objects, developers need a way to dispose of them, too.</span></span> <span data-ttu-id="9e8c6-132">À l’aide du conteneur `Dispose` méthode est un moyen pratique de rend cela possible.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-132">Using the container’s `Dispose` method is a convenient way to make this possible.</span></span>  
  
 <span data-ttu-id="9e8c6-133">**✓ FAIRE** implémenter le modèle de suppression de base et de fournir un finaliseur sur les types de ressources d’exploitation qui doivent être libérées explicitement et qui n’ont pas de finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-133">**✓ DO** implement the Basic Dispose Pattern and provide a finalizer on types holding resources that need to be freed explicitly and that do not have finalizers.</span></span>  
  
 <span data-ttu-id="9e8c6-134">Par exemple, le modèle doit être implémenté sur les types de stockage des mémoires tampons de mémoire non managée.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-134">For example, the pattern should be implemented on types storing unmanaged memory buffers.</span></span> <span data-ttu-id="9e8c6-135">Le [Types finalisables](#finalizable_types) section décrit les instructions relatives à l’implémentation des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-135">The [Finalizable Types](#finalizable_types) section discusses guidelines related to implementing finalizers.</span></span>  
  
 <span data-ttu-id="9e8c6-136">**✓ Envisagez** implémentant le modèle de suppression de base sur les classes qu’eux-mêmes ne contiennent pas les ressources non managées ou les objets à supprimer, mais sont susceptibles d’avoir les sous-types de font.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-136">**✓ CONSIDER** implementing the Basic Dispose Pattern on classes that themselves don’t hold unmanaged resources or disposable objects but are likely to have subtypes that do.</span></span>  
  
 <span data-ttu-id="9e8c6-137">Un bon exemple est la <xref:System.IO.Stream?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-137">A great example of this is the <xref:System.IO.Stream?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="9e8c6-138">Bien qu’il soit une classe de base abstraite qui ne contient pas toutes les ressources, la plupart de ses sous-classes et pour cette raison, il implémente ce modèle.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-138">Although it is an abstract base class that doesn’t hold any resources, most of its subclasses do and because of this, it implements this pattern.</span></span>  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a><span data-ttu-id="9e8c6-139">Modèle de suppression de base</span><span class="sxs-lookup"><span data-stu-id="9e8c6-139">Basic Dispose Pattern</span></span>  
 <span data-ttu-id="9e8c6-140">L’implémentation du modèle de base implique l’implémentation de la `System.IDisposable` interface et en déclarant le `Dispose(bool)` méthode qui implémente la logique de nettoyage toutes les ressources d’être partagées entre le `Dispose` (méthode) et le finaliseur facultatif.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-140">The basic implementation of the pattern involves implementing the `System.IDisposable` interface and declaring the `Dispose(bool)` method that implements all resource cleanup logic to be shared between the `Dispose` method and the optional finalizer.</span></span>  
  
 <span data-ttu-id="9e8c6-141">L’exemple suivant montre une implémentation simple du modèle de base :</span><span class="sxs-lookup"><span data-stu-id="9e8c6-141">The following example shows a simple implementation of the basic pattern:</span></span>  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder(){  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        if (disposing){  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="9e8c6-142">Le paramètre booléen `disposing` indique si la méthode a été appelée à partir de la `IDisposable.Dispose` implémentation ou à partir du finaliseur.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-142">The Boolean parameter `disposing` indicates whether the method was invoked from the `IDisposable.Dispose` implementation or from the finalizer.</span></span> <span data-ttu-id="9e8c6-143">Le `Dispose(bool)` implémentation doit vérifier le paramètre avant d’accéder à d’autres objets de référence (par exemple, le champ de ressource dans l’exemple précédent).</span><span class="sxs-lookup"><span data-stu-id="9e8c6-143">The `Dispose(bool)` implementation should check the parameter before accessing other reference objects (e.g., the resource field in the preceding sample).</span></span> <span data-ttu-id="9e8c6-144">Ces objets doivent uniquement être utilisés lorsque la méthode est appelée à partir de la `IDisposable.Dispose` implémentation (lorsque le `disposing` paramètre est égal à true).</span><span class="sxs-lookup"><span data-stu-id="9e8c6-144">Such objects should only be accessed when the method is called from the `IDisposable.Dispose` implementation (when the `disposing` parameter is equal to true).</span></span> <span data-ttu-id="9e8c6-145">Si la méthode est appelée depuis le finaliseur (`disposing` a la valeur false), autres objets ne doivent pas être accessibles.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-145">If the method is invoked from the finalizer (`disposing` is false), other objects should not be accessed.</span></span> <span data-ttu-id="9e8c6-146">La raison est que les objets sont finalisés dans un ordre imprévisible et par conséquent, ils, ou une de ses dépendances, peut déjà avoir été finalisée.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-146">The reason is that objects are finalized in an unpredictable order and so they, or any of their dependencies, might already have been finalized.</span></span>  
  
 <span data-ttu-id="9e8c6-147">En outre, cette section s’applique aux classes de base qui n’implémente pas déjà le modèle Dispose.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-147">Also, this section applies to classes with a base that does not already implement the Dispose Pattern.</span></span> <span data-ttu-id="9e8c6-148">Si vous héritez d’une classe qui implémente déjà le modèle, il vous suffit de remplacer le `Dispose(bool)` méthode pour fournir la logique de nettoyage des ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-148">If you are inheriting from a class that already implements the pattern, simply override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="9e8c6-149">**✓ FAIRE** déclarer un `protected virtual void Dispose(bool disposing)` méthode pour centraliser toute la logique associée à la libération des ressources non managées.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-149">**✓ DO** declare a `protected virtual void Dispose(bool disposing)` method to centralize all logic related to releasing unmanaged resources.</span></span>  
  
 <span data-ttu-id="9e8c6-150">Nettoyage des ressources doit avoir lieu dans cette méthode.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-150">All resource cleanup should occur in this method.</span></span> <span data-ttu-id="9e8c6-151">La méthode est appelée à partir de deux le finaliseur et `IDisposable.Dispose` (méthode).</span><span class="sxs-lookup"><span data-stu-id="9e8c6-151">The method is called from both the finalizer and the `IDisposable.Dispose` method.</span></span> <span data-ttu-id="9e8c6-152">Le paramètre est false si l’appelé à partir d’à l’intérieur d’un finaliseur.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-152">The parameter will be false if being invoked from inside a finalizer.</span></span> <span data-ttu-id="9e8c6-153">Elle doit être utilisée pour vous assurer de n’importe quel code qui s’exécute pendant la finalisation n’accède pas aux autres objets finalisables.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-153">It should be used to ensure any code running during finalization is not accessing other finalizable objects.</span></span> <span data-ttu-id="9e8c6-154">Détails de l’implémentation des finaliseurs sont décrits dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-154">Details of implementing finalizers are described in the next section.</span></span>  
  
```  
protected virtual void Dispose(bool disposing){  
    if (disposing){  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 <span data-ttu-id="9e8c6-155">**✓ FAIRE** implémenter la `IDisposable` interface en appelant simplement `Dispose(true)` suivie `GC.SuppressFinalize(this)`.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-155">**✓ DO** implement the `IDisposable` interface by simply calling `Dispose(true)` followed by `GC.SuppressFinalize(this)`.</span></span>  
  
 <span data-ttu-id="9e8c6-156">L’appel à `SuppressFinalize` doit se produire uniquement si `Dispose(true)` s’exécute avec succès.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-156">The call to `SuppressFinalize` should only occur if `Dispose(true)` executes successfully.</span></span>  
  
```  
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 <span data-ttu-id="9e8c6-157">**X ne sont pas** rendre sans paramètre `Dispose` méthode virtuelle.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-157">**X DO NOT** make the parameterless `Dispose` method virtual.</span></span>  
  
 <span data-ttu-id="9e8c6-158">Le `Dispose(bool)` méthode est celle qui doit être substituée par les sous-classes.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-158">The `Dispose(bool)` method is the one that should be overridden by subclasses.</span></span>  
  
```  
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
```  
  
 <span data-ttu-id="9e8c6-159">**X ne sont pas** déclarer toutes les surcharges de la `Dispose` autrement que `Dispose()` et `Dispose(bool)`.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-159">**X DO NOT** declare any overloads of the `Dispose` method other than `Dispose()` and `Dispose(bool)`.</span></span>  
  
 <span data-ttu-id="9e8c6-160">`Dispose` Prenez en compte un mot réservé pour codifier ce modèle et éviter toute confusion entre les implémenteurs, les utilisateurs et les compilateurs.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-160">`Dispose` should be considered a reserved word to help codify this pattern and prevent confusion among implementers, users, and compilers.</span></span> <span data-ttu-id="9e8c6-161">Certains langages peuvent choisir d’implémenter automatiquement ce modèle sur certains types.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-161">Some languages might choose to automatically implement this pattern on certain types.</span></span>  
  
 <span data-ttu-id="9e8c6-162">**✓ FAIRE** autoriser la `Dispose(bool)` méthode à être appelée plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-162">**✓ DO** allow the `Dispose(bool)` method to be called more than once.</span></span> <span data-ttu-id="9e8c6-163">La méthode peut choisir de ne rien faire après le premier appel.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-163">The method might choose to do nothing after the first call.</span></span>  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 <span data-ttu-id="9e8c6-164">**X Évitez** lever une exception depuis `Dispose(bool)` sauf dans les situations où le processus de conteneur a été endommagé critiques (fuites, un état partagé incohérent, etc.).</span><span class="sxs-lookup"><span data-stu-id="9e8c6-164">**X AVOID** throwing an exception from within `Dispose(bool)` except under critical situations where the containing process has been corrupted (leaks, inconsistent shared state, etc.).</span></span>  
  
 <span data-ttu-id="9e8c6-165">Les utilisateurs s’attendent à qui un appel à `Dispose` ne lève pas d’exception.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-165">Users expect that a call to `Dispose` will not raise an exception.</span></span>  
  
 <span data-ttu-id="9e8c6-166">Si `Dispose` peut lever une exception, la logique de nettoyage supplémentaire bloc finally n’exécutera pas.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-166">If `Dispose` could raise an exception, further finally-block cleanup logic will not execute.</span></span> <span data-ttu-id="9e8c6-167">Pour contourner ce problème, l’utilisateur aurait besoin d’encapsuler chaque appel à `Dispose` (dans le bloc finally !) dans un bloc try, ce qui aboutit à des gestionnaires de nettoyage très complexe.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-167">To work around this, the user would need to wrap every call to `Dispose` (within the finally block!) in a try block, which leads to very complex cleanup handlers.</span></span> <span data-ttu-id="9e8c6-168">Si l’exécution une `Dispose(bool disposing)` (méthode), jamais lève une exception si disposing a la valeur false.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-168">If executing a `Dispose(bool disposing)` method, never throw an exception if disposing is false.</span></span> <span data-ttu-id="9e8c6-169">Cela va se terminer le processus s’exécute à l’intérieur d’un contexte de finaliseur.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-169">Doing so will terminate the process if executing inside a finalizer context.</span></span>  
  
 <span data-ttu-id="9e8c6-170">**✓ FAIRE** lever un <xref:System.ObjectDisposedException> à partir de n’importe quel membre qui ne peut pas être utilisé une fois que l’objet a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-170">**✓ DO** throw an <xref:System.ObjectDisposedException> from any member that cannot be used after the object has been disposed of.</span></span>  
  
```  
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething(){  
           if(disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
            ...  
    }  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 <span data-ttu-id="9e8c6-171">**✓ Envisagez** en fournissant la méthode `Close()`, en plus de la `Dispose()`, si proche est une terminologie standard dans la zone.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-171">**✓ CONSIDER** providing method `Close()`, in addition to the `Dispose()`, if close is standard terminology in the area.</span></span>  
  
 <span data-ttu-id="9e8c6-172">Dans ce cas, il est important d’effectuer la `Close` implémentation identique à `Dispose` et implémentez la `IDisposable.Dispose` méthode explicitement.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-172">When doing so, it is important that you make the `Close` implementation identical to `Dispose` and consider implementing the `IDisposable.Dispose` method explicitly.</span></span>  
  
```  
public class Stream : IDisposable {  
    IDisposable.Dispose(){  
        Close();  
    }  
    public void Close(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## <a name="finalizable-types"></a><span data-ttu-id="9e8c6-173">Types finalisables</span><span class="sxs-lookup"><span data-stu-id="9e8c6-173">Finalizable Types</span></span>  
 <span data-ttu-id="9e8c6-174">Types finalisables sont des types qui étendent le modèle de suppression de base en substituant le finaliseur et en fournissant le chemin d’accès du code de finalisation dans le `Dispose(bool)` (méthode).</span><span class="sxs-lookup"><span data-stu-id="9e8c6-174">Finalizable types are types that extend the Basic Dispose Pattern by overriding the finalizer and providing finalization code path in the `Dispose(bool)` method.</span></span>  
  
 <span data-ttu-id="9e8c6-175">Les finaliseurs sont notoirement difficiles à implémenter correctement, principalement du fait que vous ne pouvez apporter certaines hypothèses (normalement valides) sur l’état du système lors de leur exécution.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-175">Finalizers are notoriously difficult to implement correctly, primarily because you cannot make certain (normally valid) assumptions about the state of the system during their execution.</span></span> <span data-ttu-id="9e8c6-176">Les instructions suivantes doivent être prises en considération prudence.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-176">The following guidelines should be taken into careful consideration.</span></span>  
  
 <span data-ttu-id="9e8c6-177">Notez que certaines instructions s’appliquent pas uniquement à la `Finalize` (méthode), mais à tout code appelé à partir d’un finaliseur.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-177">Note that some of the guidelines apply not just to the `Finalize` method, but to any code called from a finalizer.</span></span> <span data-ttu-id="9e8c6-178">Dans le cas le modèle Dispose base défini précédemment, cela signifie que la logique qui s’exécute à l’intérieur de `Dispose(bool disposing)` lorsque le `disposing` paramètre a la valeur false.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-178">In the case of the Basic Dispose Pattern previously defined, this means logic that executes inside `Dispose(bool disposing)` when the `disposing` parameter is false.</span></span>  
  
 <span data-ttu-id="9e8c6-179">Si la classe de base est finalisable déjà et implémente le modèle Dispose de base, vous ne devez pas substituer `Finalize` à nouveau.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-179">If the base class already is finalizable and implements the Basic Dispose Pattern, you should not override `Finalize` again.</span></span> <span data-ttu-id="9e8c6-180">Vous devez substituer à la place simplement la `Dispose(bool)` méthode pour fournir la logique de nettoyage des ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-180">You should instead just override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="9e8c6-181">Le code suivant montre un exemple d’un type finalisable :</span><span class="sxs-lookup"><span data-stu-id="9e8c6-181">The following code shows an example of a finalizable type:</span></span>  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder(){  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing){  
            ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing){ // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 <span data-ttu-id="9e8c6-182">**X Évitez** rendre types finalisables.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-182">**X AVOID** making types finalizable.</span></span>  
  
 <span data-ttu-id="9e8c6-183">Étudiez attentivement tout cas dans lequel vous pensez qu'un finaliseur est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-183">Carefully consider any case in which you think a finalizer is needed.</span></span> <span data-ttu-id="9e8c6-184">Il existe une véritable coût associé à des instances avec les finaliseurs, du point de vue à la fois une performance et la complexité.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-184">There is a real cost associated with instances with finalizers, from both a performance and code complexity standpoint.</span></span> <span data-ttu-id="9e8c6-185">Préférez travailler avec des wrappers de ressources tels que <xref:System.Runtime.InteropServices.SafeHandle> pour encapsuler les ressources non managées lorsque cela est possible, auquel cas un finaliseur devienne inutile, car le wrapper est responsable de son propre nettoyage des ressources.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-185">Prefer using resource wrappers such as <xref:System.Runtime.InteropServices.SafeHandle> to encapsulate unmanaged resources where possible, in which case a finalizer becomes unnecessary because the wrapper is responsible for its own resource cleanup.</span></span>  
  
 <span data-ttu-id="9e8c6-186">**X ne sont pas** rendre des types valeur finalisables.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-186">**X DO NOT** make value types finalizable.</span></span>  
  
 <span data-ttu-id="9e8c6-187">Seuls les types référence réellement obtient finalisés par le CLR, et par conséquent, toute tentative visant à placer un finaliseur sur un type valeur sera ignorée.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-187">Only reference types actually get finalized by the CLR, and thus any attempt to place a finalizer on a value type will be ignored.</span></span> <span data-ttu-id="9e8c6-188">Les compilateurs c# et C++ appliquent cette règle.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-188">The C# and C++ compilers enforce this rule.</span></span>  
  
 <span data-ttu-id="9e8c6-189">**✓ FAIRE** rendre un type finalisables si le type est responsable de la libération d’une ressource non managée qui n’a pas son propre finaliseur.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-189">**✓ DO** make a type finalizable if the type is responsible for releasing an unmanaged resource that does not have its own finalizer.</span></span>  
  
 <span data-ttu-id="9e8c6-190">Lorsque vous implémentez le finaliseur, appelez simplement `Dispose(false)` et placez la logique de nettoyage toutes les ressources à l’intérieur de la `Dispose(bool disposing)` (méthode).</span><span class="sxs-lookup"><span data-stu-id="9e8c6-190">When implementing the finalizer, simply call `Dispose(false)` and place all resource cleanup logic inside the `Dispose(bool disposing)` method.</span></span>  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        ...  
    }  
}  
```  
  
 <span data-ttu-id="9e8c6-191">**✓ FAIRE** implémenter le modèle de suppression de base sur chaque type finalisable.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-191">**✓ DO** implement the Basic Dispose Pattern on every finalizable type.</span></span>  
  
 <span data-ttu-id="9e8c6-192">Cela permet aux utilisateurs du type pour effectuer explicitement le nettoyage déterministe de ces mêmes ressources dont le finaliseur est responsable.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-192">This gives users of the type a means to explicitly perform deterministic cleanup of those same resources for which the finalizer is responsible.</span></span>  
  
 <span data-ttu-id="9e8c6-193">**X ne sont pas** accéder à tous les objets finalisables dans le chemin d’accès du code finaliseur, étant donné le risque qu’ils seront déjà avoir été finalisés.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-193">**X DO NOT** access any finalizable objects in the finalizer code path, because there is significant risk that they will have already been finalized.</span></span>  
  
 <span data-ttu-id="9e8c6-194">Par exemple, un objet finalisable A qui fait référence à un autre objet finalisable B ne peut pas utiliser fiable de B dans une suite de finaliseur, ou vice versa.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-194">For example, a finalizable object A that has a reference to another finalizable object B cannot reliably use B in A’s finalizer, or vice versa.</span></span> <span data-ttu-id="9e8c6-195">Les finaliseurs sont appelés dans un ordre aléatoire (au niveau de la garantie de classement faible pour la finalisation critique).</span><span class="sxs-lookup"><span data-stu-id="9e8c6-195">Finalizers are called in a random order (short of a weak ordering guarantee for critical finalization).</span></span>  
  
 <span data-ttu-id="9e8c6-196">En outre, sachez que les objets stockés dans des variables statiques seront collectés à certains points pendant un déchargement du domaine d’application ou lors de la sortie du processus.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-196">Also, be aware that objects stored in static variables will get collected at certain points during an application domain unload or while exiting the process.</span></span> <span data-ttu-id="9e8c6-197">Accéder à une variable statique qui fait référence à un objet finalisable (ou en appelant une méthode statique qui peut utiliser des valeurs stockées dans des variables statiques) ne peut pas être sécurisé if <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> retourne la valeur true.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-197">Accessing a static variable that refers to a finalizable object (or calling a static method that might use values stored in static variables) might not be safe if <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> returns true.</span></span>  
  
 <span data-ttu-id="9e8c6-198">**✓ FAIRE** rendre votre `Finalize` méthode protégée.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-198">**✓ DO** make your `Finalize` method protected.</span></span>  
  
 <span data-ttu-id="9e8c6-199">Les développeurs c#, C++ et VB.NET est inutile à vous soucier de cette opération, car les compilateurs pour appliquer cette règle.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-199">C#, C++, and VB.NET developers do not need to worry about this, because the compilers help to enforce this guideline.</span></span>  
  
 <span data-ttu-id="9e8c6-200">**X ne sont pas** échappement permettent d’exceptions à partir de la logique de finaliseur, à l’exception des défaillances système critiques.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-200">**X DO NOT** let exceptions escape from the finalizer logic, except for system-critical failures.</span></span>  
  
 <span data-ttu-id="9e8c6-201">Si une exception est levée à partir d’un finaliseur, le CLR s’arrête à l’ensemble du processus (à compter de .NET Framework version 2.0), empêchant d’autres finaliseurs d’exécuter et de ressources à partir de libéré de manière contrôlée.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-201">If an exception is thrown from a finalizer, the CLR will shut down the entire process (as of .NET Framework version 2.0), preventing other finalizers from executing and resources from being released in a controlled manner.</span></span>  
  
 <span data-ttu-id="9e8c6-202">**✓ Envisagez** création et utilisation d’un objet finalisable critiques (un type avec une hiérarchie de type qui contient <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) pour les situations dans lesquelles un finaliseur absolument doit s’exécuter même en cas de déchargement de domaine d’application forcé et de thread abandonne.</span><span class="sxs-lookup"><span data-stu-id="9e8c6-202">**✓ CONSIDER** creating and using a critical finalizable object (a type with a type hierarchy that contains <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) for situations in which a finalizer absolutely must execute even in the face of forced application domain unloads and thread aborts.</span></span>  
  
 <span data-ttu-id="9e8c6-203">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="9e8c6-203">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9e8c6-204">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="9e8c6-204">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e8c6-205">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e8c6-205">See Also</span></span>  
 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="9e8c6-206">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9e8c6-206">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="9e8c6-207">Modèles de design courants</span><span class="sxs-lookup"><span data-stu-id="9e8c6-207">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 [<span data-ttu-id="9e8c6-208">Nettoyage de la mémoire</span><span class="sxs-lookup"><span data-stu-id="9e8c6-208">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
