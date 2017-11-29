---
title: Migration de votre application du Windows Store vers .NET Native
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
caps.latest.revision: "29"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c4257876abeeccf762a7caa87f667468a16bba70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="migrating-your-windows-store-app-to-net-native"></a><span data-ttu-id="3f2ae-102">Migration de votre application du Windows Store vers .NET Native</span><span class="sxs-lookup"><span data-stu-id="3f2ae-102">Migrating Your Windows Store App to .NET Native</span></span>
[!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="3f2ae-103"> fournit une compilation statique des applications dans le Windows Store ou sur l'ordinateur du développeur.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-103"> provides static compilation of apps in the Windows Store or on the developer’s computer.</span></span> <span data-ttu-id="3f2ae-104">Cela diffère de la compilation dynamique effectuée pour les applications du Windows Store par le compilateur juste-à-temps (JIT) ou le [générateur d'images natives (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) sur l'appareil.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-104">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="3f2ae-105">Malgré les différences, [!INCLUDE[net_native](../../../includes/net-native-md.md)] essaie d’assurer la compatibilité avec [.NET pour les applications du Windows Store](http://msdn.microsoft.com/library/windows/apps/br230302.aspx).</span><span class="sxs-lookup"><span data-stu-id="3f2ae-105">Despite the differences, [!INCLUDE[net_native](../../../includes/net-native-md.md)] tries to maintain compatibility with the [.NET for Windows Store apps](http://msdn.microsoft.com/library/windows/apps/br230302.aspx).</span></span> <span data-ttu-id="3f2ae-106">Pour l'essentiel, les éléments qui fonctionnent sur .NET pour les applications du Windows Store fonctionnent également avec [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f2ae-106">For the most part, things that work on the .NET for Windows Store apps also work with [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  <span data-ttu-id="3f2ae-107">Toutefois, dans certains cas, vous pouvez rencontrer des changements de comportement.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-107">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="3f2ae-108">Ce document traite de ces différences entre la version .NET standard pour les applications du Windows Store et [!INCLUDE[net_native](../../../includes/net-native-md.md)] dans les domaines suivants :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-108">This document discusses these differences between the standard .NET for Windows Store apps and [!INCLUDE[net_native](../../../includes/net-native-md.md)] in the following areas:</span></span>  
  
-   [<span data-ttu-id="3f2ae-109">Différences générales au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="3f2ae-109">General runtime differences</span></span>](#Runtime)  
  
-   [<span data-ttu-id="3f2ae-110">Différences de programmation dynamique</span><span class="sxs-lookup"><span data-stu-id="3f2ae-110">Dynamic programming differences</span></span>](#Dynamic)  
  
-   [<span data-ttu-id="3f2ae-111">Autres différences en matière de réflexion</span><span class="sxs-lookup"><span data-stu-id="3f2ae-111">Other reflection-related differences</span></span>](#Reflection)  
  
-   [<span data-ttu-id="3f2ae-112">API et scénarios non pris en charge</span><span class="sxs-lookup"><span data-stu-id="3f2ae-112">Unsupported scenarios and APIs</span></span>](#Unsupported)  
  
-   [<span data-ttu-id="3f2ae-113">Différences concernant Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3f2ae-113">Visual Studio differences</span></span>](#VS)  
  
<a name="Runtime"></a>   
## <a name="general-runtime-differences"></a><span data-ttu-id="3f2ae-114">Différences générales au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="3f2ae-114">General runtime differences</span></span>  
  
-   <span data-ttu-id="3f2ae-115">Les exceptions, telles que <xref:System.TypeLoadException>, qui sont levées par le compilateur JIT quand une application s'exécute sur le Common Language Runtime (CLR) entraînent généralement des erreurs de compilation pendant le traitement par [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f2ae-115">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
-   <span data-ttu-id="3f2ae-116">N'appelez pas la méthode <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> à partir du thread d'interface utilisateur d'une application.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-116">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="3f2ae-117">Cela peut entraîner un blocage sur [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f2ae-117">This can result in a deadlock on [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
-   <span data-ttu-id="3f2ae-118">Ne vous fiez pas à l'ordre d'appel des constructeurs de classe statique.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-118">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="3f2ae-119">Dans [!INCLUDE[net_native](../../../includes/net-native-md.md)], l'ordre d'appel est différent de l'ordre sur le runtime standard.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-119">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="3f2ae-120">(Même avec le runtime standard, évitez de vous fier à l'ordre d'exécution des constructeurs de classe statique.)</span><span class="sxs-lookup"><span data-stu-id="3f2ae-120">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>  
  
-   <span data-ttu-id="3f2ae-121">Des boucles infinies sans appel (par exemple, `while(true);`) sur n'importe quel thread peuvent entraîner l'arrêt de l'application.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-121">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="3f2ae-122">Il en va de même dans le cas des attentes de longues durées ou infinies.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-122">Similarly, large or infinite waits may bring the app to a halt.</span></span>  
  
-   <span data-ttu-id="3f2ae-123">Certains cycles d'initialisation générique ne lèvent pas d'exceptions dans [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f2ae-123">Certain generic initialization cycles don't throw exceptions in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="3f2ae-124">Par exemple, le code suivant lève une exception <xref:System.TypeLoadException> sur le CLR standard,</span><span class="sxs-lookup"><span data-stu-id="3f2ae-124">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="3f2ae-125">mais pas dans [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f2ae-125">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], it doesn't.</span></span>  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   <span data-ttu-id="3f2ae-126">Dans certains cas, [!INCLUDE[net_native](../../../includes/net-native-md.md)] fournit des implémentations différentes des bibliothèques de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-126">In some cases, [!INCLUDE[net_native](../../../includes/net-native-md.md)] provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="3f2ae-127">Un objet retourné par une méthode implémente toujours les membres du type retourné.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-127">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="3f2ae-128">Toutefois, l'implémentation de sa sauvegarde étant différente, vous ne pourrez peut-être pas effectuer un cast vers le même ensemble de types comme vous le pourriez sur d'autres plateformes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-128">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="3f2ae-129">Par exemple, dans certains cas, vous ne pourrez peut-être pas effectuer un cast de l'objet d'interface <xref:System.Collections.Generic.IEnumerable%601> retourné par des méthodes telles que <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> ou <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> vers `T[]`.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-129">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>  
  
-   <span data-ttu-id="3f2ae-130">Le cache WinInet n'est pas activé par défaut sur .NET pour les applications du Windows Store, mais il l'est sur [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f2ae-130">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="3f2ae-131">Cela améliore les performances, mais a des implications pour les jeux de travail.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-131">This improves performance but has working set implications.</span></span> <span data-ttu-id="3f2ae-132">Aucune action n'est nécessaire de la part du développeur.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-132">No developer action is necessary.</span></span>  
  
<a name="Dynamic"></a>   
## <a name="dynamic-programming-differences"></a><span data-ttu-id="3f2ae-133">Différences de programmation dynamique</span><span class="sxs-lookup"><span data-stu-id="3f2ae-133">Dynamic programming differences</span></span>  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="3f2ae-134"> effectue des liaisons statiques dans le code à partir du .NET Framework pour rendre le code app-local afin d'optimiser les performances.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-134"> statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="3f2ae-135">Cependant, la taille des binaires doit demeurer petite, pour que l'ensemble du .NET Framework ne soit pas sollicité.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-135">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="3f2ae-136">Le compilateur [!INCLUDE[net_native](../../../includes/net-native-md.md)] résout cette limitation en utilisant un réducteur de dépendances qui supprime les références au code non utilisé.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-136">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="3f2ae-137">Toutefois, [!INCLUDE[net_native](../../../includes/net-native-md.md)] ne peut pas tenir à jour ou générer certaines informations de type et du code quand ces informations ne peuvent pas être déduites statiquement au moment de la compilation, mais qu'elles sont au contraire récupérées de façon dynamique au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-137">However, [!INCLUDE[net_native](../../../includes/net-native-md.md)] might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="3f2ae-138"> n'active pas la réflexion et la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-138"> does enable reflection and dynamic programming.</span></span> <span data-ttu-id="3f2ae-139">Toutefois, tous les types ne peuvent pas être marqués pour réflexion, car la taille du code généré serait alors trop grande (notamment car la réflexion d'API publiques dans le .NET Framework est prise en charge).</span><span class="sxs-lookup"><span data-stu-id="3f2ae-139">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="3f2ae-140">Le compilateur [!INCLUDE[net_native](../../../includes/net-native-md.md)] choisit intelligemment les types devant prendre en charge la réflexion, et il ne conserve les métadonnées et ne génère le code que pour ces types.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-140">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>  
  
 <span data-ttu-id="3f2ae-141">Par exemple, pour la liaison de données, une application doit pouvoir mapper les noms de propriété sur les fonctions.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-141">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="3f2ae-142">Dans .NET pour les applications du Windows Store, le Common Language Runtime utilise automatiquement la réflexion pour fournir cette fonctionnalité pour les types managés et les types natifs disponibles publiquement.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-142">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="3f2ae-143">Dans [!INCLUDE[net_native](../../../includes/net-native-md.md)], le compilateur inclut automatiquement les métadonnées des types auxquels vous liez des données.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-143">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], the compiler automatically includes metadata for types to which you bind data.</span></span>  
  
 <span data-ttu-id="3f2ae-144">Le compilateur [!INCLUDE[net_native](../../../includes/net-native-md.md)] peut également gérer les types génériques couramment utilisés tels que <xref:System.Collections.Generic.List%601> et <xref:System.Collections.Generic.Dictionary%602>, qui fonctionnent sans indications ou directives.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-144">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="3f2ae-145">Le mot clé [dynamic](~/docs/csharp/language-reference/keywords/dynamic.md) est également pris en charge, dans certaines limites.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-145">The [dynamic](~/docs/csharp/language-reference/keywords/dynamic.md) keyword is also supported within certain limits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f2ae-146">Vous devez tester minutieusement tous les chemins de code dynamiques quand vous portez votre application vers [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f2ae-146">You should test all dynamic code paths thoroughly when porting your app to [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="3f2ae-147">La configuration par défaut pour [!INCLUDE[net_native](../../../includes/net-native-md.md)] est suffisante pour la plupart des développeurs, mais certains peuvent souhaiter affiner leurs configurations à l'aide d'un fichier de directives runtime (.rd.xml).</span><span class="sxs-lookup"><span data-stu-id="3f2ae-147">The default configuration for [!INCLUDE[net_native](../../../includes/net-native-md.md)] is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="3f2ae-148">En outre, dans certains cas, le compilateur [!INCLUDE[net_native](../../../includes/net-native-md.md)] est incapable de déterminer les métadonnées indispensables pour la réflexion et s'appuie sur les indicateurs, notamment dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-148">In addition, in some cases, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>  
  
-   <span data-ttu-id="3f2ae-149">Certaines constructions telles que <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> et <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> ne peuvent pas être déterminées de manière statique.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-149">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>  
  
-   <span data-ttu-id="3f2ae-150">Comme le compilateur ne peut pas déterminer les instanciations, un type générique à réfléchir doit être spécifié par les directives runtime.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-150">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="3f2ae-151">Cela est nécessaire à double titre : tout le code doit être inclus, et la réflexion de types génériques peut former un cycle infini (par exemple, quand une méthode générique est appelée sur un type générique).</span><span class="sxs-lookup"><span data-stu-id="3f2ae-151">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f2ae-152">Les directives runtime sont définies dans un fichier de directives runtime (.rd.xml).</span><span class="sxs-lookup"><span data-stu-id="3f2ae-152">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="3f2ae-153">Pour obtenir des informations générales sur l’utilisation de ce fichier, consultez la rubrique [Bien démarrer](../../../docs/framework/net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="3f2ae-153">For general information about using this file, see [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span> <span data-ttu-id="3f2ae-154">Pour plus d’informations sur les directives runtime, consultez [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="3f2ae-154">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="3f2ae-155"> inclut également des outils de profilage qui permettent au développeur de déterminer quels types en dehors du jeu par défaut doivent prendre en charge la réflexion.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-155"> also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>  
  
<a name="Reflection"></a>   
## <a name="other-reflection-related-differences"></a><span data-ttu-id="3f2ae-156">Autres différences en matière de réflexion</span><span class="sxs-lookup"><span data-stu-id="3f2ae-156">Other reflection-related differences</span></span>  
 <span data-ttu-id="3f2ae-157">Le comportement de .NET pour les applications du Windows Store et de [!INCLUDE[net_native](../../../includes/net-native-md.md)]présente un certain nombre d'autres différences liées à la réflexion.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-157">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="3f2ae-158">Dans [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="3f2ae-158">In [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
-   <span data-ttu-id="3f2ae-159">La réflexion privée de types et de membres de la bibliothèque de classes .NET Framework n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-159">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="3f2ae-160">Vous pouvez, toutefois, réfléchir vos propres types et membres privés, ainsi que les types et les membres dans des bibliothèques tierces.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-160">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>  
  
-   <span data-ttu-id="3f2ae-161">La propriété <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> retourne correctement `false` pour un objet <xref:System.Reflection.ParameterInfo> qui représente une valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-161">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="3f2ae-162">Dans .NET pour les applications du Windows Store, elle retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-162">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="3f2ae-163">Le langage intermédiaire ne prend pas cela en charge directement et l'interprétation est laissée au langage.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-163">Intermediate language (IL) doesn’t support this directly, and interpretation is left to the language.</span></span>  
  
-   <span data-ttu-id="3f2ae-164">Les membres publics sur les structures <xref:System.RuntimeFieldHandle> et <xref:System.RuntimeMethodHandle> ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-164">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="3f2ae-165">Ces types sont pris en charge uniquement pour LINQ, les arborescences d'expression et l'initialisation de tableau statique.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-165">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>  
  
-   <span data-ttu-id="3f2ae-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> et <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> comprennent des membres masqués dans des classes de base et peuvent donc être remplacés sans substitutions explicites.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="3f2ae-167">Cela vaut également pour les autres méthodes [RuntimeReflectionExtensions.GetRuntime*](http://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx) .</span><span class="sxs-lookup"><span data-stu-id="3f2ae-167">This is also true of other [RuntimeReflectionExtensions.GetRuntime*](http://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx) methods.</span></span>  
  
-   <span data-ttu-id="3f2ae-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> et <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> n'échouent pas quand vous essayez de créer certaines combinaisons (par exemple, un tableau de valeurs byref).</span><span class="sxs-lookup"><span data-stu-id="3f2ae-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of byrefs).</span></span>  
  
-   <span data-ttu-id="3f2ae-169">Vous ne pouvez pas utiliser la réflexion pour appeler des membres qui ont des paramètres de pointeur.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-169">You can't use reflection to invoke members that have pointer parameters.</span></span>  
  
-   <span data-ttu-id="3f2ae-170">Vous ne pouvez pas utiliser la réflexion pour obtenir ou définir un champ de pointeur.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-170">You can't use reflection to get or set a pointer field.</span></span>  
  
-   <span data-ttu-id="3f2ae-171">Quand le nombre d'arguments et le type de l'un des arguments sont incorrects, [!INCLUDE[net_native](../../../includes/net-native-md.md)] lève une <xref:System.ArgumentException> au lieu d'une <xref:System.Reflection.TargetParameterCountException>.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-171">When the argument count is wrong and the type of one of the arguments is incorrect, [!INCLUDE[net_native](../../../includes/net-native-md.md)] throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>  
  
-   <span data-ttu-id="3f2ae-172">La sérialisation binaire des exceptions n'est généralement pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-172">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="3f2ae-173">Ainsi, les objets non sérialisables peuvent être ajoutés au dictionnaire <xref:System.Exception.Data%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-173">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>  
  
<a name="Unsupported"></a>   
## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="3f2ae-174">API et scénarios non pris en charge</span><span class="sxs-lookup"><span data-stu-id="3f2ae-174">Unsupported scenarios and APIs</span></span>  
 <span data-ttu-id="3f2ae-175">Les sections suivantes répertorient les API et les scénarios non pris en charge pour le développement général, l'interopérabilité et les technologies telles que HTTPClient et Windows Communication Foundation (WCF) :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-175">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>  
  
-   [<span data-ttu-id="3f2ae-176">Développement général</span><span class="sxs-lookup"><span data-stu-id="3f2ae-176">General development</span></span>](#General)  
  
-   [<span data-ttu-id="3f2ae-177">HttpClient</span><span class="sxs-lookup"><span data-stu-id="3f2ae-177">HttpClient</span></span>](#HttpClient)  
  
-   [<span data-ttu-id="3f2ae-178">Interop</span><span class="sxs-lookup"><span data-stu-id="3f2ae-178">Interop</span></span>](#Interop)  
  
-   [<span data-ttu-id="3f2ae-179">API non prises en charge</span><span class="sxs-lookup"><span data-stu-id="3f2ae-179">Unsupported APIs</span></span>](#APIs)  
  
<a name="General"></a>   
### <a name="general-development-differences"></a><span data-ttu-id="3f2ae-180">Différences de développement général</span><span class="sxs-lookup"><span data-stu-id="3f2ae-180">General development differences</span></span>  
 <span data-ttu-id="3f2ae-181">**Types de valeur**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-181">**Value types**</span></span>  
  
-   <span data-ttu-id="3f2ae-182">Si vous substituez les méthodes <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> et <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> pour un type de valeur, n'appelez pas les implémentations de classe de base.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-182">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="3f2ae-183">Dans .NET pour les applications du Windows Store, ces méthodes reposent sur la réflexion.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-183">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="3f2ae-184">Au moment de la compilation, [!INCLUDE[net_native](../../../includes/net-native-md.md)] génère une implémentation qui ne repose pas sur la réflexion de runtime.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-184">At compile time, [!INCLUDE[net_native](../../../includes/net-native-md.md)] generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="3f2ae-185">Cela signifie que si vous ne substituez pas ces deux méthodes, elles fonctionnent comme prévu, car [!INCLUDE[net_native](../../../includes/net-native-md.md)] génère l'implémentation au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-185">This means that if you don't override these two methods, they will work as expected, because [!INCLUDE[net_native](../../../includes/net-native-md.md)] generates the implementation at compile time.</span></span> <span data-ttu-id="3f2ae-186">Toutefois, la substitution de ces méthodes tout en appelant l'implémentation de la classe de base entraîne une exception.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-186">However, overriding these methods but calling the base class implementation results in an exception.</span></span>  
  
-   <span data-ttu-id="3f2ae-187">Les types de valeur supérieurs à un mégaoctet ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-187">Value types larger than one megabyte aren't supported.</span></span>  
  
-   <span data-ttu-id="3f2ae-188">Les types de valeur ne peuvent pas avoir de constructeur par défaut dans [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f2ae-188">Value types can't have a default constructor in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="3f2ae-189">(C# et Visual Basic interdisent les constructeurs par défaut sur les types de valeur.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-189">(C# and Visual Basic prohibit default constructors on value types.</span></span> <span data-ttu-id="3f2ae-190">Toutefois, ceux-ci peuvent être créés dans un langage intermédiaire.)</span><span class="sxs-lookup"><span data-stu-id="3f2ae-190">However, these can be created in IL.)</span></span>  
  
 <span data-ttu-id="3f2ae-191">**Tableaux**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-191">**Arrays**</span></span>  
  
-   <span data-ttu-id="3f2ae-192">Les tableaux présentant une limite inférieure différente de zéro ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-192">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="3f2ae-193">En règle générale, ces tableaux sont créés en appelant la surcharge <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-193">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>  
  
-   <span data-ttu-id="3f2ae-194">La création dynamique de tableaux multidimensionnels n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-194">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="3f2ae-195">Ces tableaux sont généralement créés en appelant une surcharge de la méthode <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> qui inclut un paramètre `lengths`, ou en appelant la méthode <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-195">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="3f2ae-196">Les tableaux multidimensionnels qui ont quatre dimensions ou plus ne sont pas pris en charge ; il s'agit de tableaux dont la propriété <xref:System.Array.Rank%2A?displayProperty=nameWithType> à une valeur supérieure ou égale à quatre.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-196">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="3f2ae-197">Utilisez des [tableaux en escalier](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (tableaux de tableaux) à la place.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-197">Use [jagged arrays](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="3f2ae-198">Par exemple, `array[x,y,z]` n'est pas valide, contrairement à `array[x][y][z]` .</span><span class="sxs-lookup"><span data-stu-id="3f2ae-198">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>  
  
-   <span data-ttu-id="3f2ae-199">L'écart entre les tableaux multidimensionnels n'est pas pris en charge et provoque une exception <xref:System.InvalidCastException> au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-199">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>  
  
 <span data-ttu-id="3f2ae-200">**Génériques**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-200">**Generics**</span></span>  
  
-   <span data-ttu-id="3f2ae-201">Une extension de type générique infinie entraîne une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-201">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="3f2ae-202">Par exemple, la compilation de ce code échoue :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-202">For example, this code fails to compile:</span></span>  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 <span data-ttu-id="3f2ae-203">**Pointeurs**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-203">**Pointers**</span></span>  
  
-   <span data-ttu-id="3f2ae-204">Les tableaux de pointeurs ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-204">Arrays of pointers aren't supported.</span></span>  
  
-   <span data-ttu-id="3f2ae-205">Vous ne pouvez pas utiliser la réflexion pour obtenir ou définir un champ de pointeur.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-205">You can't use reflection to get or set a pointer field.</span></span>  
  
 <span data-ttu-id="3f2ae-206">**Sérialisation**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-206">**Serialization**</span></span>  
  
 <span data-ttu-id="3f2ae-207">L'attribut <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-207">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="3f2ae-208">Utilisez plutôt l'attribut <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> .</span><span class="sxs-lookup"><span data-stu-id="3f2ae-208">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>  
  
 <span data-ttu-id="3f2ae-209">**Ressources**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-209">**Resources**</span></span>  
  
 <span data-ttu-id="3f2ae-210">L'utilisation de ressources localisées avec la classe <xref:System.Diagnostics.Tracing.EventSource> n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-210">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="3f2ae-211">La propriété <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> ne définit pas de ressources localisées.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-211">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>  
  
 <span data-ttu-id="3f2ae-212">**Délégués**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-212">**Delegates**</span></span>  
  
 <span data-ttu-id="3f2ae-213">`Delegate.BeginInvoke` et `Delegate.EndInvoke` ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-213">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>  
  
 <span data-ttu-id="3f2ae-214">**Async**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-214">**Async**</span></span>  
  
 <span data-ttu-id="3f2ae-215">L'insertion de logique sous forme de thread dans les surcharges de Task IAsync n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-215">Threading logic in overloads of Task IAsync isn't supported.</span></span>  
  
 <span data-ttu-id="3f2ae-216">**API diverses**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-216">**Miscellaneous APIs**</span></span>  
  
-   <span data-ttu-id="3f2ae-217">La propriété <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> lève une exception <xref:System.PlatformNotSupportedException> si un attribut <xref:System.Runtime.InteropServices.GuidAttribute> n'est pas appliqué au type.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-217">The <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="3f2ae-218">Le GUID est utilisé principalement pour la prise en charge de COM.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-218">The GUID is used primarily for COM support.</span></span>  
  
-   <span data-ttu-id="3f2ae-219">La méthode <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> traite correctement les chaînes qui contiennent des dates courtes dans [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f2ae-219">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="3f2ae-220">Toutefois, elle n’assure pas la compatibilité avec les changements apportés à l’analyse des dates et heures, décrits dans les articles de la Base de connaissances Microsoft [KB2803771](http://support.microsoft.com/kb/2803771) et [KB2803755](http://support.microsoft.com/kb/2803755).</span><span class="sxs-lookup"><span data-stu-id="3f2ae-220">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](http://support.microsoft.com/kb/2803771) and [KB2803755](http://support.microsoft.com/kb/2803755).</span></span>  
  
-   <span data-ttu-id="3f2ae-221"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType>`("E")` est arrondi correctement dans [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f2ae-221"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="3f2ae-222">Dans certaines versions du CLR, la chaîne de résultat est tronquée et non arrondie.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-222">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>  
  
<a name="HttpClient"></a>   
### <a name="httpclient-differences"></a><span data-ttu-id="3f2ae-223">Différences pour HttpClient</span><span class="sxs-lookup"><span data-stu-id="3f2ae-223">HttpClient differences</span></span>  
 <span data-ttu-id="3f2ae-224">Dans [!INCLUDE[net_native](../../../includes/net-native-md.md)], la classe <xref:System.Net.Http.HttpClientHandler> utilise WinINet de façon interne (via la classe [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) ) au lieu des classes <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> utilisées dans la version .NET standard pour les applications du Windows Store.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-224">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="3f2ae-225">WinINet ne prend pas en charge toutes les options de configuration prises en charge par la classe <xref:System.Net.Http.HttpClientHandler> .</span><span class="sxs-lookup"><span data-stu-id="3f2ae-225">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="3f2ae-226">Par conséquent :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-226">As a result:</span></span>  
  
-   <span data-ttu-id="3f2ae-227">Certaines des propriétés de fonctionnalité de <xref:System.Net.Http.HttpClientHandler> retournent `false` sur [!INCLUDE[net_native](../../../includes/net-native-md.md)], tandis qu'elles retournent `true` dans la version .NET standard pour les applications du Windows Store.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-227">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on [!INCLUDE[net_native](../../../includes/net-native-md.md)], whereas they return `true` in the standard .NET for Windows Store apps.</span></span>  
  
-   <span data-ttu-id="3f2ae-228">Une partie des accesseurs `get` des propriétés de configuration retournent toujours une valeur fixe sur [!INCLUDE[net_native](../../../includes/net-native-md.md)] qui est différente de la valeur configurable par défaut dans .NET pour les applications du Windows Store.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-228">Some of the configuration property `get` accessors always return a fixed value on [!INCLUDE[net_native](../../../includes/net-native-md.md)] that is different than the default configurable value in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="3f2ae-229">Certaines différences de comportement supplémentaires sont décrites dans les sous-sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-229">Some additional behavior differences are covered in the following subsections.</span></span>  
  
 <span data-ttu-id="3f2ae-230">**Proxy**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-230">**Proxy**</span></span>  
  
 <span data-ttu-id="3f2ae-231">La classe [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) ne prend pas en charge la configuration ou le remplacement du proxy à chaque demande.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-231">The [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class doesn’t support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="3f2ae-232">Cela signifie que toutes les demandes présentées sur [!INCLUDE[net_native](../../../includes/net-native-md.md)] utilisent le serveur proxy configuré par le système ou aucun serveur proxy, en fonction de la valeur de la propriété <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-232">This means that all requests on [!INCLUDE[net_native](../../../includes/net-native-md.md)] use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="3f2ae-233">Dans .NET pour les applications du Windows Store, le serveur proxy est défini par la propriété <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-233">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="3f2ae-234">Sur [!INCLUDE[net_native](../../../includes/net-native-md.md)], définir <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> sur une valeur autre que `null` lève une exception <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-234">On [!INCLUDE[net_native](../../../includes/net-native-md.md)], setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="3f2ae-235">La propriété <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> retourne `false` sur [!INCLUDE[net_native](../../../includes/net-native-md.md)], tandis qu'elle retourne `true` dans le .NET Framework standard pour les applications du Windows Store.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-235">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on [!INCLUDE[net_native](../../../includes/net-native-md.md)], whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>  
  
 <span data-ttu-id="3f2ae-236">**Redirection automatique**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-236">**Automatic redirection**</span></span>  
  
 <span data-ttu-id="3f2ae-237">La classe [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) ne permet pas de configurer le nombre maximal de redirections automatiques.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-237">The [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="3f2ae-238">La valeur de la propriété <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> est 50 par défaut dans la version .NET standard pour les applications du Windows Store et peut être modifiée.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-238">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="3f2ae-239">Sur [!INCLUDE[net_native](../../../includes/net-native-md.md)], la valeur de cette propriété est 10 et toute modification de cette valeur lève une exception <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="3f2ae-239">On [!INCLUDE[net_native](../../../includes/net-native-md.md)], the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="3f2ae-240">La propriété <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> retourne `false` sur [!INCLUDE[net_native](../../../includes/net-native-md.md)], tandis qu'elle retourne `true` dans .NET pour les applications du Windows Store.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-240">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on [!INCLUDE[net_native](../../../includes/net-native-md.md)], whereas it returns `true` in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="3f2ae-241">**Décompression automatique**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-241">**Automatic decompression**</span></span>  
  
 <span data-ttu-id="3f2ae-242">.NET pour les applications du Windows Store vous permet de définir la propriété <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> sur <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, à la fois sur <xref:System.Net.DecompressionMethods.Deflate> et <xref:System.Net.DecompressionMethods.GZip>, ou sur <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-242">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="3f2ae-243"> ne prend en charge <xref:System.Net.DecompressionMethods.Deflate> qu'avec <xref:System.Net.DecompressionMethods.GZip>ou <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-243"> only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="3f2ae-244">Si vous essayez de définir la propriété <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> uniquement sur <xref:System.Net.DecompressionMethods.Deflate> ou <xref:System.Net.DecompressionMethods.GZip> , elle est automatiquement définie à la fois sur <xref:System.Net.DecompressionMethods.Deflate> et <xref:System.Net.DecompressionMethods.GZip>.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-244">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>  
  
 <span data-ttu-id="3f2ae-245">**Cookies**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-245">**Cookies**</span></span>  
  
 <span data-ttu-id="3f2ae-246">La gestion des cookies est effectuée simultanément par <xref:System.Net.Http.HttpClient> et WinINet.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-246">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="3f2ae-247">Les cookies de <xref:System.Net.CookieContainer> sont combinés aux cookies du cache de cookies WinINet.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-247">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="3f2ae-248">La suppression d'un cookie de <xref:System.Net.CookieContainer> empêche <xref:System.Net.Http.HttpClient> de l'envoyer, mais si le cookie a déjà été vu par WinINet et que les cookies n'ont pas été supprimés par l'utilisateur, WinInet l'envoie.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-248">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="3f2ae-249">Il est impossible de supprimer par programmation un cookie de WinINet à l'aide de l'API <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>ou <xref:System.Net.CookieContainer> .</span><span class="sxs-lookup"><span data-stu-id="3f2ae-249">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="3f2ae-250">Définir la propriété <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> sur `false` entraîne uniquement l'arrêt de l'envoi des cookies par <xref:System.Net.Http.HttpClient> ; WinINet peut toujours inclure ses cookies dans la demande.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-250">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>  
  
 <span data-ttu-id="3f2ae-251">**Informations d'identification**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-251">**Credentials**</span></span>  
  
 <span data-ttu-id="3f2ae-252">Dans .NET pour les applications du Windows Store, les propriétés <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> et <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> fonctionnent de manière indépendante.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-252">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="3f2ae-253">En outre, la propriété <xref:System.Net.Http.HttpClientHandler.Credentials%2A> accepte tout objet qui implémente l'interface <xref:System.Net.ICredentials> .</span><span class="sxs-lookup"><span data-stu-id="3f2ae-253">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="3f2ae-254">Dans [!INCLUDE[net_native](../../../includes/net-native-md.md)], quand la propriété <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> est définie sur `true` , la propriété <xref:System.Net.Http.HttpClientHandler.Credentials%2A> prend la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-254">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="3f2ae-255">En outre, la propriété <xref:System.Net.Http.HttpClientHandler.Credentials%2A> peut être définie uniquement sur `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>ou un objet de type <xref:System.Net.NetworkCredential>.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-255">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="3f2ae-256">L'affectation de tout autre objet <xref:System.Net.ICredentials> , le plus courant étant <xref:System.Net.CredentialCache>, à la propriété <xref:System.Net.Http.HttpClientHandler.Credentials%2A> lève une <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-256">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>  
  
 <span data-ttu-id="3f2ae-257">**Autres fonctionnalités non prises en charge ou non configurables**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-257">**Other unsupported or unconfigurable features**</span></span>  
  
 <span data-ttu-id="3f2ae-258">Dans [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="3f2ae-258">In [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
-   <span data-ttu-id="3f2ae-259">La valeur de la propriété <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> est toujours <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-259">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="3f2ae-260">Dans .NET pour les applications du Windows Store, la valeur par défaut est <xref:System.Net.Http.ClientCertificateOption.Manual>.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-260">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>  
  
-   <span data-ttu-id="3f2ae-261">La propriété <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> n'est pas configurable.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-261">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>  
  
-   <span data-ttu-id="3f2ae-262">La propriété <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> a toujours la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-262">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="3f2ae-263">Dans .NET pour les applications du Windows Store, la valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-263">In .NET for Windows Store apps, the default is `false`.</span></span>  
  
-   <span data-ttu-id="3f2ae-264">L'en-tête `SetCookie2` dans les réponses est ignoré, car considéré comme obsolète.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-264">The `SetCookie2` header in responses is ignored as obsolete.</span></span>  
  
<a name="Interop"></a>   
### <a name="interop-differences"></a><span data-ttu-id="3f2ae-265">Différences concernant l'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="3f2ae-265">Interop differences</span></span>  
 <span data-ttu-id="3f2ae-266">**API déconseillées**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-266">**Deprecated APIs**</span></span>  
  
 <span data-ttu-id="3f2ae-267">Un certain nombre d'API peu utilisées pour l'interopérabilité avec du code managé ont été déconseillées.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-267">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="3f2ae-268">Quand elles sont utilisées avec [!INCLUDE[net_native](../../../includes/net-native-md.md)], ces API peuvent lever une exception <xref:System.NotImplementedException> ou <xref:System.PlatformNotSupportedException> , ou entraîner une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-268">When used with [!INCLUDE[net_native](../../../includes/net-native-md.md)], these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="3f2ae-269">Dans .NET pour les applications du Windows Store, ces API sont marquées comme obsolètes, même si les appeler génère un avertissement, plutôt qu'une erreur, du compilateur.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-269">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>  
  
 <span data-ttu-id="3f2ae-270">API déconseillées pour le marshaling `VARIANT` :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-270">Deprecated APIs for `VARIANT` marshaling:</span></span>  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>|  
  
 <span data-ttu-id="3f2ae-271"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>est pris en charge, mais elle lève une exception dans certains scénarios, tels que lorsqu’il est utilisé avec [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) ou des variants byref.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-271"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) or byref variants.</span></span>  
  
 <span data-ttu-id="3f2ae-272">API déconseillées pour la prise en charge de [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-272">Deprecated APIs for [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) support:</span></span>  
  
|<span data-ttu-id="3f2ae-273">Type</span><span class="sxs-lookup"><span data-stu-id="3f2ae-273">Type</span></span>|<span data-ttu-id="3f2ae-274">Membre</span><span class="sxs-lookup"><span data-stu-id="3f2ae-274">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch>|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual>|  
|<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>|<span data-ttu-id="3f2ae-275">L'attribut n'est pas pris en charge</span><span class="sxs-lookup"><span data-stu-id="3f2ae-275">Attribute isn't supported</span></span>|  
  
 <span data-ttu-id="3f2ae-276">API déconseillées pour les événements COM classiques :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-276">Deprecated APIs for classic COM events:</span></span>  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|  
  
 <span data-ttu-id="3f2ae-277">API déconseillées dans l'interface <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>, non prises en charge dans [!INCLUDE[net_native](../../../includes/net-native-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-277">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
|<span data-ttu-id="3f2ae-278">Type</span><span class="sxs-lookup"><span data-stu-id="3f2ae-278">Type</span></span>|<span data-ttu-id="3f2ae-279">Membre</span><span class="sxs-lookup"><span data-stu-id="3f2ae-279">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>|<span data-ttu-id="3f2ae-280">Tous les membres.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-280">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>|<span data-ttu-id="3f2ae-281">Tous les membres.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-281">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>|<span data-ttu-id="3f2ae-282">Tous les membres.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-282">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=nameWithType>|  
  
 <span data-ttu-id="3f2ae-283">Autres fonctionnalités d'interopérabilité non prises en charge :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-283">Other unsupported interop features:</span></span>  
  
|<span data-ttu-id="3f2ae-284">Type</span><span class="sxs-lookup"><span data-stu-id="3f2ae-284">Type</span></span>|<span data-ttu-id="3f2ae-285">Membre</span><span class="sxs-lookup"><span data-stu-id="3f2ae-285">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>|<span data-ttu-id="3f2ae-286">Tous les membres.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-286">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>|<span data-ttu-id="3f2ae-287">Tous les membres.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-287">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.Currency>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AsAny>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler>|  
  
 <span data-ttu-id="3f2ae-288">API de marshaling rarement utilisées :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-288">Rarely used marshalling APIs:</span></span>  
  
|<span data-ttu-id="3f2ae-289">Type</span><span class="sxs-lookup"><span data-stu-id="3f2ae-289">Type</span></span>|<span data-ttu-id="3f2ae-290">Membre</span><span class="sxs-lookup"><span data-stu-id="3f2ae-290">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29>|  
  
 <span data-ttu-id="3f2ae-291">**Appel de plateforme et compatibilité avec l'interopérabilité COM**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-291">**Platform invoke and COM interop compatibility**</span></span>  
  
 <span data-ttu-id="3f2ae-292">La plupart des scénarios d'appel de plateforme et d'interopérabilité COM sont toujours pris en charge dans [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f2ae-292">Most platform invoke and COM interop scenarios are still supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="3f2ae-293">En particulier, toute l'interopérabilité avec les API Windows Runtime (WinRT) et tout le marshaling nécessaire pour le Windows Runtime sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-293">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="3f2ae-294">Cela inclut la prise en charge du marshaling pour les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-294">This includes marshaling support for:</span></span>  
  
-   <span data-ttu-id="3f2ae-295">Tableaux (y compris <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span><span class="sxs-lookup"><span data-stu-id="3f2ae-295">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>  
  
-   `BStr`  
  
-   <span data-ttu-id="3f2ae-296">Délégués</span><span class="sxs-lookup"><span data-stu-id="3f2ae-296">Delegates</span></span>  
  
-   <span data-ttu-id="3f2ae-297">Chaînes (Unicode, Ansi et HSTRING)</span><span class="sxs-lookup"><span data-stu-id="3f2ae-297">Strings (Unicode, Ansi, and HSTRING)</span></span>  
  
-   <span data-ttu-id="3f2ae-298">Structures (`byref` et `byval`)</span><span class="sxs-lookup"><span data-stu-id="3f2ae-298">Structs (`byref` and `byval`)</span></span>  
  
-   <span data-ttu-id="3f2ae-299">Unions</span><span class="sxs-lookup"><span data-stu-id="3f2ae-299">Unions</span></span>  
  
-   <span data-ttu-id="3f2ae-300">Handles Win32</span><span class="sxs-lookup"><span data-stu-id="3f2ae-300">Win32 handles</span></span>  
  
-   <span data-ttu-id="3f2ae-301">Toutes les constructions WinRT</span><span class="sxs-lookup"><span data-stu-id="3f2ae-301">All WinRT constructs</span></span>  
  
-   <span data-ttu-id="3f2ae-302">Prise en charge partielle du marshaling des types variant.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-302">Partial support for marshaling variant types.</span></span> <span data-ttu-id="3f2ae-303">Les fonctionnalités suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-303">The following are supported:</span></span>  
  
    -   <xref:System.Boolean>  
  
    -   <xref:System.Byte>  
  
    -   <xref:System.Decimal>  
  
    -   <xref:System.Double>  
  
    -   <xref:System.Int16>  
  
    -   <xref:System.Int32>  
  
    -   <xref:System.Int64>  
  
    -   <xref:System.SByte>  
  
    -   <xref:System.Single>  
  
    -   <xref:System.UInt16>  
  
    -   <xref:System.UInt32>  
  
    -   <xref:System.UInt64>  
  
    -   `BStr`  
  
    -   [<span data-ttu-id="3f2ae-304">IUnknown</span><span class="sxs-lookup"><span data-stu-id="3f2ae-304">IUnknown</span></span>](http://msdn.microsoft.com/library/windows/desktop/ms680509.aspx)  
  
 <span data-ttu-id="3f2ae-305">Toutefois, [!INCLUDE[net_native](../../../includes/net-native-md.md)] ne prend pas en charge les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-305">However, [!INCLUDE[net_native](../../../includes/net-native-md.md)] doesn't support the following:</span></span>  
  
-   <span data-ttu-id="3f2ae-306">L'utilisation d'événements COM classiques</span><span class="sxs-lookup"><span data-stu-id="3f2ae-306">Using classic COM events</span></span>  
  
-   <span data-ttu-id="3f2ae-307">La mise en œuvre de l'interface <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> sur un type managé</span><span class="sxs-lookup"><span data-stu-id="3f2ae-307">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>  
  
-   <span data-ttu-id="3f2ae-308">Implémentation de la [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) interface sur un type managé via la <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribut.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-308">Implementing the [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="3f2ae-309">Toutefois, vous ne pouvez pas appeler des objets COM via `IDispatch`, et votre objet managé ne peut pas implémenter `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-309">However, note that you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>  
  
 <span data-ttu-id="3f2ae-310">Utiliser la réflexion pour appeler une méthode d'appel de plateforme n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-310">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="3f2ae-311">Vous pouvez contourner cette limitation en encapsulant l'appel de méthode dans une autre méthode et en utilisant la réflexion pour appeler le wrapper.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-311">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>  
  
<a name="APIs"></a>   
### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="3f2ae-312">Autres différences par rapport aux API .NET pour les applications du Windows Store</span><span class="sxs-lookup"><span data-stu-id="3f2ae-312">Other differences from .NET APIs for Windows Store apps</span></span>  
 <span data-ttu-id="3f2ae-313">Cette section répertorie les API restantes qui ne sont pas prises en charge dans [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f2ae-313">This section lists the remaining APIs that aren't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="3f2ae-314">La plus grande partie des API non prises en charge sont des API Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3f2ae-314">The largest set of the unsupported APIs are Windows Communication Foundation (WCF) APIs.</span></span>  
  
 <span data-ttu-id="3f2ae-315">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-315">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>  
  
 <span data-ttu-id="3f2ae-316">Les types dans les espaces de noms <xref:System.ComponentModel.DataAnnotations> et <xref:System.ComponentModel.DataAnnotations.Schema> ne sont pas pris en charge dans [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f2ae-316">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="3f2ae-317">Ceux-ci comprennent les types suivants présents dans .NET pour les applications du Windows Store pour Windows 8 :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-317">These include the following types that are present in the .NET for Windows Store apps for Windows 8:</span></span>  
  
||  
|-|  
|<xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EditableAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>|  
  
 <span data-ttu-id="3f2ae-318">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-318">**Visual Basic**</span></span>  
  
 <span data-ttu-id="3f2ae-319">Visual Basic n'est pas actuellement pris en charge dans [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f2ae-319">Visual Basic isn't currently supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="3f2ae-320">Les types suivants dans les espaces de noms <xref:Microsoft.VisualBasic> et <xref:Microsoft.VisualBasic.CompilerServices> ne sont pas disponibles dans [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="3f2ae-320">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
||  
|-|  
|<xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>|  
  
 <span data-ttu-id="3f2ae-321">**Contexte de réflexion (espace de noms System.Reflection.Context)**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-321">**Reflection Context (System.Reflection.Context namespace)**</span></span>  
  
 <span data-ttu-id="3f2ae-322">La classe <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> n'est pas prise en charge dans [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f2ae-322">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="3f2ae-323">**RTC (System.Net.Http.Rtc)**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-323">**RTC (System.Net.Http.Rtc)**</span></span>  
  
 <span data-ttu-id="3f2ae-324">La classe <xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> n'est pas prise en charge dans [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f2ae-324">The <xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> class isn't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="3f2ae-325">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-325">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>  
  
 <span data-ttu-id="3f2ae-326">Les types dans les [espaces de noms System.ServiceModel.*](http://msdn.microsoft.com/library/gg145010.aspx) ne sont pas pris en charge dans [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f2ae-326">The types in the [System.ServiceModel.* namespaces](http://msdn.microsoft.com/library/gg145010.aspx) aren't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="3f2ae-327">Ce sont notamment les types suivants :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-327">These includes the following types:</span></span>  
  
||  
|-|  
|<xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>|  
  
### <a name="differences-in-serializers"></a><span data-ttu-id="3f2ae-328">Différences entre les sérialiseurs</span><span class="sxs-lookup"><span data-stu-id="3f2ae-328">Differences in serializers</span></span>  
 <span data-ttu-id="3f2ae-329">Les différences suivantes concernent la sérialisation et la désérialisation avec les classes <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>et <xref:System.Xml.Serialization.XmlSerializer> :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-329">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>  
  
-   <span data-ttu-id="3f2ae-330">Dans [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ne parviennent pas à sérialiser ou à désérialiser une classe dérivée qui a un membre de classe de base dont le type n'est pas un type de sérialisation racine.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-330">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="3f2ae-331">Par exemple, dans le code suivant, sérialiser ou désérialiser `Y` génère une erreur :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-331">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     <span data-ttu-id="3f2ae-332">Le type `InnerType` n'est pas connu du sérialiseur, car les membres de la classe de base ne sont pas parcourus pendant la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-332">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>  
  
-   <span data-ttu-id="3f2ae-333"><xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ne parviennent pas à sérialiser une classe ou une structure qui implémente l'interface <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="3f2ae-333"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="3f2ae-334">Par exemple, les types suivants ne parviennent pas à sérialiser ou à désérialiser :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-334">For example, the following types fail to serialize or deserialize:</span></span>  
  
  
  
-   <span data-ttu-id="3f2ae-335"><xref:System.Xml.Serialization.XmlSerializer> ne sérialise pas la valeur d'objet suivante, car il ne connaît pas le type exact de l'objet à sérialiser :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-335"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>  
  
  
  
-   <span data-ttu-id="3f2ae-336"><xref:System.Xml.Serialization.XmlSerializer> ne parvient pas à sérialiser ou à désérialiser si le type de l'objet sérialisé est <xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-336"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>  
  
-   <span data-ttu-id="3f2ae-337">Tous les sérialiseurs (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> et <xref:System.Xml.Serialization.XmlSerializer>) ne parviennent pas à générer un code de sérialisation pour un type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> ou pour un type contenant <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-337">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="3f2ae-338">Ils affichent des erreurs de génération à la place.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-338">They display build-time errors instead.</span></span>  
  
-   <span data-ttu-id="3f2ae-339">Les constructeurs suivants des types de sérialisation ne fonctionnent pas nécessairement comme prévu :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-339">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29?displayProperty=nameWithType>  
  
-   <span data-ttu-id="3f2ae-340"><xref:System.Xml.Serialization.XmlSerializer> ne parvient pas à générer le code pour un type dont les méthodes possèdent un des attributs suivants :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-340"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <span data-ttu-id="3f2ae-341"><xref:System.Xml.Serialization.XmlSerializer> ne traite pas l'interface de sérialisation personnalisée <xref:System.Xml.Serialization.IXmlSerializable> .</span><span class="sxs-lookup"><span data-stu-id="3f2ae-341"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="3f2ae-342">Si vous avez une classe qui implémente cette interface, <xref:System.Xml.Serialization.XmlSerializer> considère le type comme un ancien objet CLR simple et sérialise uniquement ses propriétés publiques.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-342">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>  
  
-   <span data-ttu-id="3f2ae-343">La sérialisation d'un objet <xref:System.Exception> simple, tel que l'objet suivant, ne fonctionne pas bien avec <xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span><span class="sxs-lookup"><span data-stu-id="3f2ae-343">Serializing a plain <xref:System.Exception> object, such as the following, doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span></span>  
  
  
  
<a name="VS"></a>   
## <a name="visual-studio-differences"></a><span data-ttu-id="3f2ae-344">Différences concernant Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3f2ae-344">Visual Studio differences</span></span>  
 <span data-ttu-id="3f2ae-345">**Exceptions et débogage**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-345">**Exceptions and debugging**</span></span>  
  
 <span data-ttu-id="3f2ae-346">Quand vous exécutez des applications compilées à l'aide de [!INCLUDE[net_native](../../../includes/net-native-md.md)] dans le débogueur, les exceptions de première chance sont activées pour les types d'exception suivants :</span><span class="sxs-lookup"><span data-stu-id="3f2ae-346">When you're running apps compiled by using [!INCLUDE[net_native](../../../includes/net-native-md.md)] in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 <span data-ttu-id="3f2ae-347">**Génération d'applications**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-347">**Building apps**</span></span>  
  
 <span data-ttu-id="3f2ae-348">Recourez aux outils de génération x86 qui sont utilisés par défaut par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-348">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="3f2ae-349">Nous vous déconseillons d'utiliser les outils MSBuild AMD64, qui se trouvent dans C:\Program Files (x86)\MSBuild\12.0\bin\amd64, car ils peuvent créer des problèmes de génération.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-349">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>  
  
 <span data-ttu-id="3f2ae-350">**Profileurs**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-350">**Profilers**</span></span>  
  
-   <span data-ttu-id="3f2ae-351">Le profileur d'UC Visual Studio et le profileur de mémoire XAML n'affichent pas Uniquement mon code correctement.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-351">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>  
  
-   <span data-ttu-id="3f2ae-352">Le profileur de mémoire XAML n'affiche pas avec précision les données du tas managé.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-352">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>  
  
-   <span data-ttu-id="3f2ae-353">Le profileur d'UC ne peut pas identifier correctement les modules, et affiche les noms de fonction avec préfixe.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-353">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>  
  
 <span data-ttu-id="3f2ae-354">**Projets de bibliothèque de tests unitaires**</span><span class="sxs-lookup"><span data-stu-id="3f2ae-354">**Unit Test Library projects**</span></span>  
  
 <span data-ttu-id="3f2ae-355">L'activation de [!INCLUDE[net_native](../../../includes/net-native-md.md)] sur une bibliothèque de tests unitaires pour un projet d'application du Windows Store n'est pas prise en charge et entraîne l'échec de la génération du projet.</span><span class="sxs-lookup"><span data-stu-id="3f2ae-355">Enabling [!INCLUDE[net_native](../../../includes/net-native-md.md)] on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f2ae-356">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f2ae-356">See Also</span></span>  
 [<span data-ttu-id="3f2ae-357">Prise en main</span><span class="sxs-lookup"><span data-stu-id="3f2ae-357">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [<span data-ttu-id="3f2ae-358">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="3f2ae-358">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="3f2ae-359">Vue d’ensemble des applications .NET pour le Windows Store</span><span class="sxs-lookup"><span data-stu-id="3f2ae-359">.NET For Windows Store apps overview</span></span>](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 [<span data-ttu-id="3f2ae-360">Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="3f2ae-360">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
