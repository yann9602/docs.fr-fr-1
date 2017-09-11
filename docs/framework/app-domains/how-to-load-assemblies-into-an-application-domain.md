---
title: "Guide pratique pour charger des assemblys dans un domaine d’application"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 934373d61407c8cc19b7d6424898a582880f9c21
ms.openlocfilehash: c319da0f8e6f3cdfb83e659a778136d668699834
ms.contentlocale: fr-fr
ms.lasthandoff: 08/10/2017

---
# <a name="how-to-load-assemblies-into-an-application-domain"></a><span data-ttu-id="b2019-102">Guide pratique pour charger des assemblys dans un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="b2019-102">How to: Load Assemblies into an Application Domain</span></span>
<span data-ttu-id="b2019-103">Il existe plusieurs façons de charger un assembly dans un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="b2019-103">There are several ways to load an assembly into an application domain.</span></span> <span data-ttu-id="b2019-104">La procédure recommandée consiste à utiliser la méthode `static` (`Shared` en Visual Basic) <xref:System.Reflection.Assembly.Load%2A> de la classe <xref:System.Reflection.Assembly?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="b2019-104">The recommended way is to use the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.Load%2A> method of the <xref:System.Reflection.Assembly?displayProperty=fullName> class.</span></span> <span data-ttu-id="b2019-105">Vous pouvez aussi adopter les approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="b2019-105">Other ways assemblies can be loaded include:</span></span>  
  
-   <span data-ttu-id="b2019-106">La méthode <xref:System.Reflection.Assembly.LoadFrom%2A> de la classe <xref:System.Reflection.Assembly> charge un assembly en fonction de son emplacement de fichier.</span><span class="sxs-lookup"><span data-stu-id="b2019-106">The <xref:System.Reflection.Assembly.LoadFrom%2A> method of the <xref:System.Reflection.Assembly> class loads an assembly given its file location.</span></span> <span data-ttu-id="b2019-107">Le chargement des assemblys avec cette méthode utilise un contexte de chargement différent.</span><span class="sxs-lookup"><span data-stu-id="b2019-107">Loading assemblies with this method uses a different load context.</span></span>  
  
-   <span data-ttu-id="b2019-108">Les méthodes <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> et <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> chargent un assembly dans le contexte de réflexion uniquement.</span><span class="sxs-lookup"><span data-stu-id="b2019-108">The <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> and <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> methods load an assembly into the reflection-only context.</span></span> <span data-ttu-id="b2019-109">Les assemblys chargés dans ce contexte peuvent être examinés mais pas exécutés, ce qui permet d’examiner des assemblys qui ciblent d’autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="b2019-109">Assemblies loaded into this context can be examined but not executed, allowing the examination of assemblies that target other platforms.</span></span> <span data-ttu-id="b2019-110">Voir [Guide pratique pour charger des assemblys dans le contexte de réflexion uniquement](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="b2019-110">See [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2019-111">Le contexte de réflexion uniquement est une nouveauté du .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="b2019-111">The reflection-only context is new in the .NET Framework version 2.0.</span></span>  
  
-   <span data-ttu-id="b2019-112">Les méthodes telles que <xref:System.AppDomain.CreateInstance%2A> et <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> de la classe <xref:System.AppDomain> peuvent charger des assemblys dans un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="b2019-112">Methods such as <xref:System.AppDomain.CreateInstance%2A> and <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> of the <xref:System.AppDomain> class can load assemblies into an application domain.</span></span>  
  
-   <span data-ttu-id="b2019-113">La méthode <xref:System.Type.GetType%2A> de la classe <xref:System.Type> peut charger des assemblys.</span><span class="sxs-lookup"><span data-stu-id="b2019-113">The <xref:System.Type.GetType%2A> method of the <xref:System.Type> class can load assemblies.</span></span>  
  
-   <span data-ttu-id="b2019-114">La méthode <xref:System.AppDomain.Load%2A> de la classe <xref:System.AppDomain?displayProperty=fullName> peut charger des assemblys, mais est utilisée principalement pour l’interopérabilité COM.</span><span class="sxs-lookup"><span data-stu-id="b2019-114">The <xref:System.AppDomain.Load%2A> method of the <xref:System.AppDomain?displayProperty=fullName> class can load assemblies, but is primarily used for COM interoperability.</span></span> <span data-ttu-id="b2019-115">Vous ne devez pas l’utiliser pour charger des assemblys dans un domaine d’application autre que celui à partir duquel elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="b2019-115">It should not be used to load assemblies into an application domain other than the application domain from which it is called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2019-116">À compter du .NET Framework version 2.0, le runtime ne charge pas un assembly qui a été compilé avec une version du .NET Framework dont le numéro de version est supérieur au runtime chargé actuellement.</span><span class="sxs-lookup"><span data-stu-id="b2019-116">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="b2019-117">Cela s’applique à la combinaison des composants majeurs et mineurs du numéro de version.</span><span class="sxs-lookup"><span data-stu-id="b2019-117">This applies to the combination of the major and minor components of the version number.</span></span>  
  
 <span data-ttu-id="b2019-118">Vous pouvez spécifier la façon dont le code compilé juste-à-temps (JIT) des assemblys chargés est partagé entre les domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="b2019-118">You can specify the way the just-in-time (JIT) compiled code from loaded assemblies is shared between application domains.</span></span> <span data-ttu-id="b2019-119">Pour plus d’informations, consultez [Domaines d’application et assemblys](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346).</span><span class="sxs-lookup"><span data-stu-id="b2019-119">For more information, see [Application Domains and Assemblies](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2019-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="b2019-120">Example</span></span>  
 <span data-ttu-id="b2019-121">Le code suivant charge un assembly nommé « example.exe » ou « example.dll » dans le domaine d’application actuel, obtient un type nommé `Example` à partir de l’assembly, obtient une méthode sans paramètre nommée `MethodA` pour ce type, et exécute la méthode.</span><span class="sxs-lookup"><span data-stu-id="b2019-121">The following code loads an assembly named "example.exe" or "example.dll" into the current application domain, gets a type named `Example` from the assembly, gets a parameterless method named `MethodA` for that type, and executes the method.</span></span> <span data-ttu-id="b2019-122">Pour obtenir une description complète de l’obtention d’informations à partir d’un assembly chargé, consultez [Chargement et utilisation dynamiques des types](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="b2019-122">For a complete discussion on obtaining information from a loaded assembly, see [Dynamically Loading and Using Types](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
 <span data-ttu-id="b2019-123">[!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)] [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)] [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="b2019-123">[!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)] [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)] [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2019-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2019-124">See Also</span></span>  
 <span data-ttu-id="b2019-125"><xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A></span><span class="sxs-lookup"><span data-stu-id="b2019-125"><xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A></span></span>   
 <span data-ttu-id="b2019-126">[Programmation avec des domaines d’application](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131) </span><span class="sxs-lookup"><span data-stu-id="b2019-126">[Programming with Application Domains](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131) </span></span>  
 <span data-ttu-id="b2019-127">[Réflexion](../../../docs/framework/reflection-and-codedom/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="b2019-127">[Reflection](../../../docs/framework/reflection-and-codedom/reflection.md) </span></span>  
 <span data-ttu-id="b2019-128">[Utilisation des domaines d’application](../../../docs/framework/app-domains/use.md) </span><span class="sxs-lookup"><span data-stu-id="b2019-128">[Using Application Domains](../../../docs/framework/app-domains/use.md) </span></span>  
 <span data-ttu-id="b2019-129">[Guide pratique pour charger des assemblys dans le contexte de réflexion uniquement](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md) </span><span class="sxs-lookup"><span data-stu-id="b2019-129">[How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md) </span></span>  
 [<span data-ttu-id="b2019-130">Domaines d'application et assemblys</span><span class="sxs-lookup"><span data-stu-id="b2019-130">Application Domains and Assemblies</span></span>](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346)

