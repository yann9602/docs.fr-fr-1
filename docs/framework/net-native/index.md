---
title: Compilation d'applications avec .NET Native
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dec4d465b53f939f8fa711950ba6a000bd304e13
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2018
---
# <a name="compiling-apps-with-net-native"></a><span data-ttu-id="84199-102">Compilation d'applications avec .NET Native</span><span class="sxs-lookup"><span data-stu-id="84199-102">Compiling Apps with .NET Native</span></span>
[!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="84199-103">est une technologie de précompilation pour générer et déployer des applications Windows qui est fournie avec Visual Studio 2015 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="84199-103"> is a precompilation technology for building and deploying Windows apps that is included with Visual Studio 2015 and later versions.</span></span> <span data-ttu-id="84199-104">Elle compile automatiquement la version commerciale des applications écrites en code managé (C# ou Visual Basic) et qui ciblent .NET Framework et Windows 10 en code natif.</span><span class="sxs-lookup"><span data-stu-id="84199-104">It automatically compiles the release version of apps that are written in managed code (C# or Visual Basic) and that target the .NET Framework and Windows 10 to native code.</span></span>  
  
 <span data-ttu-id="84199-105">En règle générale, les applications qui ciblent .NET Framework sont compilées en langage intermédiaire (IL).</span><span class="sxs-lookup"><span data-stu-id="84199-105">Typically, apps that target the .NET Framework are compiled to intermediate language (IL).</span></span> <span data-ttu-id="84199-106">Au moment de l'exécution, le compilateur juste-à-temps (JIT) traduit le langage intermédiaire en code natif.</span><span class="sxs-lookup"><span data-stu-id="84199-106">At run time, the just-in-time (JIT) compiler translates the IL to native code.</span></span> <span data-ttu-id="84199-107">En revanche, [!INCLUDE[net_native](../../../includes/net-native-md.md)] compile les applications Windows directement en code natif.</span><span class="sxs-lookup"><span data-stu-id="84199-107">In contrast, [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiles Windows apps directly to native code.</span></span> <span data-ttu-id="84199-108">Pour les développeurs, cela signifie les points suivants :</span><span class="sxs-lookup"><span data-stu-id="84199-108">For developers, this means:</span></span>  
  
-   <span data-ttu-id="84199-109">Les performances du code natif de fonctionnalités de vos applications.</span><span class="sxs-lookup"><span data-stu-id="84199-109">Your apps feature the performance of native code.</span></span> <span data-ttu-id="84199-110">En règle générale, les performances seront supérieur au code qui est tout d’abord compilé en langage IL et ensuite compilé en code natif par le compilateur JIT.</span><span class="sxs-lookup"><span data-stu-id="84199-110">Usually, performance will be superior to code that is first compiled to IL and then compiled to native code by the JIT compiler.</span></span> 
  
-   <span data-ttu-id="84199-111">Vous pouvez continuer à programmer en C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="84199-111">You can continue to program in C# or Visual Basic.</span></span>  
  
-   <span data-ttu-id="84199-112">Vous pouvez continuer à exploiter les ressources fournies par .NET Framework, y compris sa bibliothèque de classes, la gestion automatique de la mémoire, le garbage collection et la gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="84199-112">You can continue to take advantage of the resources provided by the .NET Framework, including its class library, automatic memory management and garbage collection, and exception handling.</span></span>  
  
 <span data-ttu-id="84199-113">Pour les utilisateurs de vos applications, [!INCLUDE[net_native](../../../includes/net-native-md.md)] présente les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="84199-113">For users of your apps, [!INCLUDE[net_native](../../../includes/net-native-md.md)] offers these advantages:</span></span>  
  
-   <span data-ttu-id="84199-114">Temps d’exécution plus rapides pour la majorité des scénarios et des applications.</span><span class="sxs-lookup"><span data-stu-id="84199-114">Faster execution times for the majority of apps and scenarios.</span></span>
  
-   <span data-ttu-id="84199-115">Temps de démarrage plus rapides pour la majorité des scénarios et des applications.</span><span class="sxs-lookup"><span data-stu-id="84199-115">Faster startup times for the majority of apps and scenarios.</span></span> 
  
-   <span data-ttu-id="84199-116">Faibles coûts de déploiement et de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="84199-116">Low deployment and update costs.</span></span>  
  
-   <span data-ttu-id="84199-117">Utilisation de la mémoire optimisée d’application.</span><span class="sxs-lookup"><span data-stu-id="84199-117">Optimized app memory usage.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="84199-118">Pour la plupart des applications et des scénarios, .NET Native offre des temps de démarrage beaucoup plus rapides et des performances supérieures par rapport à une application compilée pour le langage intermédiaire ou à une image NGEN.</span><span class="sxs-lookup"><span data-stu-id="84199-118">For the vast majority of apps and scenarios, .NET Native offers significantly faster startup times and superior performance when compared to an app compiled to IL or to an NGEN image.</span></span> <span data-ttu-id="84199-119">Toutefois, les résultats peuvent varier.</span><span class="sxs-lookup"><span data-stu-id="84199-119">However, your results may vary.</span></span> <span data-ttu-id="84199-120">Pour vous assurer que votre application a bénéficié d’améliorations des performances de .NET Native, vous devez comparer ses performances avec celle de la version non - .NET Native de votre application.</span><span class="sxs-lookup"><span data-stu-id="84199-120">To ensure that your app has benefited from the performance enhancements of .NET Native, you should compare its performance with that of the non-.NET Native version of your app.</span></span> <span data-ttu-id="84199-121">Pour plus d’informations, consultez [vue d’ensemble de la Session de Performance](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span><span class="sxs-lookup"><span data-stu-id="84199-121">For more information, see [Performance Session Overview](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span></span>
 
<span data-ttu-id="84199-122">Toutefois, [!INCLUDE[net_native](../../../includes/net-native-md.md)] va au-delà d'une simple compilation en code natif.</span><span class="sxs-lookup"><span data-stu-id="84199-122">But [!INCLUDE[net_native](../../../includes/net-native-md.md)] involves more than a compilation to native code.</span></span> <span data-ttu-id="84199-123">Il transforme la façon dont les applications .NET Framework sont intégrées et exécutées.</span><span class="sxs-lookup"><span data-stu-id="84199-123">It transforms the way that .NET Framework apps are built and executed.</span></span> <span data-ttu-id="84199-124">En particulier :</span><span class="sxs-lookup"><span data-stu-id="84199-124">In particular:</span></span>  
  
-   <span data-ttu-id="84199-125">Pendant la précompilation, les parties nécessaires de .NET Framework sont liées statiquement dans votre application.</span><span class="sxs-lookup"><span data-stu-id="84199-125">During precompilation, required portions of the .NET Framework are statically linked into your app.</span></span> <span data-ttu-id="84199-126">Cela permet à l'application de s'exécuter avec les bibliothèques app-local de .NET Framework et au compilateur d'effectuer une analyse globale pour procurer des gains de performance.</span><span class="sxs-lookup"><span data-stu-id="84199-126">This allows the app to run with app-local libraries of the .NET Framework, and the compiler to perform global analysis to deliver performance wins.</span></span> <span data-ttu-id="84199-127">Ainsi, les applications se lancent systématiquement plus rapidement même après une mise à jour de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="84199-127">As a result, apps launch consistently faster even after .NET Framework updates.</span></span>  
  
-   <span data-ttu-id="84199-128">Le [!INCLUDE[net_native](../../../includes/net-native-md.md)] runtime est optimisé pour la précompilation statique et offre de meilleures performances dans la grande majorité des cas.</span><span class="sxs-lookup"><span data-stu-id="84199-128">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] runtime is optimized for static precompilation and in the vast majority of cases offers superior performance.</span></span> <span data-ttu-id="84199-129">Dans le même temps, il conserve les fonctionnalités de réflexion principales, si productives au regard des développeurs.</span><span class="sxs-lookup"><span data-stu-id="84199-129">At the same time, it retains the core reflection features that developers find so productive.</span></span>  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="84199-130"> utilise le même système principal que le compilateur C++, qui est optimisé pour les scénarios de précompilation statique.</span><span class="sxs-lookup"><span data-stu-id="84199-130"> uses the same back end as the C++ compiler, which is optimized for static precompilation scenarios.</span></span>  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="84199-131"> peut procurer aux développeurs de code managé les performances de C++, car il s'appuie pratiquement sur les mêmes outils que C++, comme indiqué dans le tableau ci-après.</span><span class="sxs-lookup"><span data-stu-id="84199-131"> is able to bring the performance benefits of C++ to managed code developers because it uses the same or similar tools as C++ under the hood, as shown in this table.</span></span>  
  
||[!INCLUDE[net_native](../../../includes/net-native-md.md)]|<span data-ttu-id="84199-132">C++</span><span class="sxs-lookup"><span data-stu-id="84199-132">C++</span></span>|  
|-|----------------------------------------------------------------|-----------|  
|<span data-ttu-id="84199-133">Bibliothèques</span><span class="sxs-lookup"><span data-stu-id="84199-133">Libraries</span></span>|<span data-ttu-id="84199-134">.NET Framework + Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="84199-134">The .NET Framework + Windows Runtime</span></span>|<span data-ttu-id="84199-135">Win32 + Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="84199-135">Win32 + Windows Runtime</span></span>|  
|<span data-ttu-id="84199-136">Compilateur</span><span class="sxs-lookup"><span data-stu-id="84199-136">Compiler</span></span>|<span data-ttu-id="84199-137">Compilateur d'optimisation UTC</span><span class="sxs-lookup"><span data-stu-id="84199-137">UTC optimizing compiler</span></span>|<span data-ttu-id="84199-138">Compilateur d'optimisation UTC</span><span class="sxs-lookup"><span data-stu-id="84199-138">UTC optimizing compiler</span></span>|  
|<span data-ttu-id="84199-139">Déployé</span><span class="sxs-lookup"><span data-stu-id="84199-139">Deployed</span></span>|<span data-ttu-id="84199-140">Fichiers binaires prêts à être exécutés</span><span class="sxs-lookup"><span data-stu-id="84199-140">Ready-to-run binaries</span></span>|<span data-ttu-id="84199-141">Fichiers binaires prêts à être exécutés (ASM)</span><span class="sxs-lookup"><span data-stu-id="84199-141">Ready-to-run binaries (ASM)</span></span>|  
|<span data-ttu-id="84199-142">Exécution</span><span class="sxs-lookup"><span data-stu-id="84199-142">Runtime</span></span>|<span data-ttu-id="84199-143">MRT.dll (Runtime CLR minimal)</span><span class="sxs-lookup"><span data-stu-id="84199-143">MRT.dll (Minimal CLR Runtime)</span></span>|<span data-ttu-id="84199-144">CRT.dll (Runtime C)</span><span class="sxs-lookup"><span data-stu-id="84199-144">CRT.dll (C Runtime)</span></span>|  
  
 <span data-ttu-id="84199-145">Pour les applications Windows pour Windows 10, vous devez charger les binaires de compilation de code .NET Native contenus dans les packages d’application (fichiers .aspx) vers le Windows Store.</span><span class="sxs-lookup"><span data-stu-id="84199-145">For Windows apps for Windows 10, you upload .NET Native Code Compilation binaries in app packages (.appx files) to the Windows Store.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="84199-146">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="84199-146">In This Section</span></span>  
 <span data-ttu-id="84199-147">Pour plus d'informations sur le développement d'applications avec la compilation de code .NET Native, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="84199-147">For more information about developing apps with .NET Native Code Compilation, see these topics:</span></span>  
  
-   [<span data-ttu-id="84199-148">Prise en main de la compilation de code .NET Native : procédure détaillée pour les développeurs</span><span class="sxs-lookup"><span data-stu-id="84199-148">Getting Started with .NET Native Code Compilation: The Developer Experience Walkthrough</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
-   <span data-ttu-id="84199-149">[.NET Native et compilation :](../../../docs/framework/net-native/net-native-and-compilation.md) Comment .NET Native compile votre projet en code natif.</span><span class="sxs-lookup"><span data-stu-id="84199-149">[.NET Native and Compilation:](../../../docs/framework/net-native/net-native-and-compilation.md) How .NET Native compiles your project to native code.</span></span>  
  
-   [<span data-ttu-id="84199-150">Réflexion et .NET Native</span><span class="sxs-lookup"><span data-stu-id="84199-150">Reflection and .NET Native</span></span>](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    -   [<span data-ttu-id="84199-151">API qui s’appuient sur la réflexion</span><span class="sxs-lookup"><span data-stu-id="84199-151">APIs That Rely on Reflection</span></span>](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    -   [<span data-ttu-id="84199-152">Informations de référence sur les API de réflexion</span><span class="sxs-lookup"><span data-stu-id="84199-152">Reflection API Reference</span></span>](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    -   [<span data-ttu-id="84199-153">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="84199-153">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
-   [<span data-ttu-id="84199-154">Sérialisation et métadonnées</span><span class="sxs-lookup"><span data-stu-id="84199-154">Serialization and Metadata</span></span>](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
-   [<span data-ttu-id="84199-155">Migration de votre application du Windows Store vers .NET Native</span><span class="sxs-lookup"><span data-stu-id="84199-155">Migrating Your Windows Store App to .NET Native</span></span>](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
-   [<span data-ttu-id="84199-156">Résolution des problèmes généraux liés à .NET Native</span><span class="sxs-lookup"><span data-stu-id="84199-156">.NET Native General Troubleshooting</span></span>](../../../docs/framework/net-native/net-native-general-troubleshooting.md)  
  
## <a name="see-also"></a><span data-ttu-id="84199-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84199-157">See Also</span></span>  
 [<span data-ttu-id="84199-158">FAQ sur .NET Native</span><span class="sxs-lookup"><span data-stu-id="84199-158">.NET Native FAQ</span></span>](http://msdn.microsoft.com/vstudio/dn642499.aspx)
