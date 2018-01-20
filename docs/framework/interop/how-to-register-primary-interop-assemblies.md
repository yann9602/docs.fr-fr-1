---
title: "Comment : enregistrer des assemblys PIA"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registering primary interop assemblies
- primary interop assemblies, registering
ms.assetid: 4b2fcf8a-429d-43ce-8334-e026040be8bb
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 40414f39a1b84e7d07086d0634898de5171db590
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-register-primary-interop-assemblies"></a><span data-ttu-id="be1d6-102">Comment : enregistrer des assemblys PIA</span><span class="sxs-lookup"><span data-stu-id="be1d6-102">How to: Register Primary Interop Assemblies</span></span>
<span data-ttu-id="be1d6-103">Les classes ne peuvent être marshalées que par COM Interop et sont toujours marshalées en tant qu’interfaces.</span><span class="sxs-lookup"><span data-stu-id="be1d6-103">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="be1d6-104">Dans certains cas, l’interface utilisée pour marshaler la classe est appelée interface de classe.</span><span class="sxs-lookup"><span data-stu-id="be1d6-104">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="be1d6-105">Pour plus d’informations sur la substitution de l’interface de classe par une interface de votre choix, consultez [Wrapper CCW (COM Callable Wrapper)](../../../docs/framework/interop/com-callable-wrapper.md).</span><span class="sxs-lookup"><span data-stu-id="be1d6-105">For information about overriding the class interface with an interface of your choice, see [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md).</span></span>  
  
 <span data-ttu-id="be1d6-106">Même s'il est possible d'utiliser des types COM à partir d'une application .NET Framework pour générer un assembly d'interopérabilité, une telle utilisation pose problème.</span><span class="sxs-lookup"><span data-stu-id="be1d6-106">Although any developer who wants to use COM types from a .NET Framework application can generate an interop assembly, doing so creates a problem.</span></span> <span data-ttu-id="be1d6-107">Chaque fois qu'un développeur importe et signe une bibliothèque de types COM, il crée un ensemble de types uniques qui sont incompatibles avec ceux importés et signés par un autre développeur.</span><span class="sxs-lookup"><span data-stu-id="be1d6-107">Each time a developer imports and signs a COM type library, that developer creates a set of unique types that are incompatible with those imported and signed by another developer.</span></span> <span data-ttu-id="be1d6-108">La solution à ce problème d'incompatibilité de type est, pour chaque développeur, d'obtenir l'assembly PIA signé et fourni par le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="be1d6-108">The solution to this type incompatibility problem is for each developer to obtain the vendor-supplied and signed primary interop assembly.</span></span>  
  
 <span data-ttu-id="be1d6-109">Si vous envisagez d'exposer des types COM tiers à d'autres applications, utilisez toujours l'assembly PIA fourni par le même éditeur que la bibliothèque de types qu'il définit.</span><span class="sxs-lookup"><span data-stu-id="be1d6-109">If you plan to expose third-party COM types to other applications, always use the primary interop assembly provided by the same publisher as the type library it defines.</span></span> <span data-ttu-id="be1d6-110">En plus de garantir la compatibilité des types, les assemblys PIA sont souvent personnalisés par le fournisseur pour améliorer l'interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="be1d6-110">In addition to providing guaranteed type compatibility, primary interop assemblies are often customized by the vendor to enhance interoperability.</span></span>  
  
 <span data-ttu-id="be1d6-111">Même si vous ne souhaitez pas exposer des types COM tiers, l'utilisation d'un assembly PIA peut faciliter l'interopérabilité avec les composants COM.</span><span class="sxs-lookup"><span data-stu-id="be1d6-111">Even if you do not plan to expose third-party COM types, using the primary interop assembly can ease the task of interoperating with COM components.</span></span> <span data-ttu-id="be1d6-112">Toutefois, cette stratégie ne protège pas des modifications qu'un fournisseur peut apporter aux types définis dans un assembly PIA.</span><span class="sxs-lookup"><span data-stu-id="be1d6-112">However, this strategy provides no insulation from changes a vendor might make to types defined in a primary interop assembly.</span></span> <span data-ttu-id="be1d6-113">Si votre application nécessite une telle protection, générez votre propre assembly d'interopérabilité au lieu d'utiliser un assembly PIA.</span><span class="sxs-lookup"><span data-stu-id="be1d6-113">When your application requires such insulation, generate your own interop assembly instead of using the primary interop assembly.</span></span>  
  
 <span data-ttu-id="be1d6-114">Vous devez inscrire tous les assemblys PIA acquis sur votre ordinateur de développement avant de pouvoir les référencer avec [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="be1d6-114">You must register all acquired primary interop assemblies on your development computer before you can reference them with [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)].</span></span> <span data-ttu-id="be1d6-115">Visual Studio recherche et utilise un assembly PIA la première fois que vous référencez un type à partir d'une bibliothèque de types COM.</span><span class="sxs-lookup"><span data-stu-id="be1d6-115">Visual Studio looks for and uses a primary interop assembly the first time that you reference a type from a COM type library.</span></span> <span data-ttu-id="be1d6-116">Si Visual Studio ne peut pas localiser l'assembly PIA associé à la bibliothèque de types, il vous invite à l'acquérir ou vous propose de créer un assembly d'interopérabilité .</span><span class="sxs-lookup"><span data-stu-id="be1d6-116">If Visual Studio cannot locate the primary interop assembly associated with the type library, it prompts you to acquire it or offers to create an interop assembly instead.</span></span> <span data-ttu-id="be1d6-117">De même, l’outil [Tlbimp.exe (importateur de bibliothèques de types)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) utilise également le Registre pour rechercher des assemblys PIA.</span><span class="sxs-lookup"><span data-stu-id="be1d6-117">Likewise, the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) also uses the registry to locate primary interop assemblies.</span></span>  
  
 <span data-ttu-id="be1d6-118">Même s'il n'est pas nécessaire d'inscrire les assemblys PIA si vous ne prévoyez pas d'utiliser Visual Studio, l'inscription offre deux avantages :</span><span class="sxs-lookup"><span data-stu-id="be1d6-118">Although it is not necessary to register primary interop assemblies unless you plan to use Visual Studio, registration provides two advantages:</span></span>  
  
-   <span data-ttu-id="be1d6-119">Un assembly PIA inscrit est clairement marqué sous la clé de Registre de la bibliothèque de types d'origine.</span><span class="sxs-lookup"><span data-stu-id="be1d6-119">A registered primary interop assembly is clearly marked under the registry key of the original type library.</span></span> <span data-ttu-id="be1d6-120">L'inscription est le meilleur moyen de rechercher un assembly PIA sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="be1d6-120">Registration is the best way for you to locate a primary interop assembly on your computer.</span></span>  
  
-   <span data-ttu-id="be1d6-121">Vous pouvez éviter de générer et d'utiliser par erreur un nouvel assembly d'interopérabilité si, à un moment donné, vous utilisez Visual Studio pour référencer un type pour lequel vous avez un assembly PIA non inscrit.</span><span class="sxs-lookup"><span data-stu-id="be1d6-121">You can avoid accidentally generating and using a new interop assembly if, at some time in the future, you do use Visual Studio to reference a type for which you have an unregistered primary interop assembly.</span></span>  
  
 <span data-ttu-id="be1d6-122">Utilisez l’outil [Regasm.exe (outil d’inscription d’assemblys)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) pour inscrire un assembly PIA.</span><span class="sxs-lookup"><span data-stu-id="be1d6-122">Use the [Assembly Registration Tool (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) to register a primary interop assembly.</span></span>  
  
### <a name="to-register-a-primary-interop-assembly"></a><span data-ttu-id="be1d6-123">Pour inscrire un assembly PIA</span><span class="sxs-lookup"><span data-stu-id="be1d6-123">To register a primary interop assembly</span></span>  
  
1.  <span data-ttu-id="be1d6-124">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="be1d6-124">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="be1d6-125">**regasm** *nomassembly*</span><span class="sxs-lookup"><span data-stu-id="be1d6-125">**regasm** *assemblyname*</span></span>  
  
     <span data-ttu-id="be1d6-126">Dans cette commande, *nomassembly* est le nom de fichier de l’assembly inscrit.</span><span class="sxs-lookup"><span data-stu-id="be1d6-126">In this command, *assemblyname* is the file name of the assembly that is registered.</span></span> <span data-ttu-id="be1d6-127">Regasm.exe ajoute une entrée pour l'assembly PIA sous la même clé de Registre que la bibliothèque de types d'origine.</span><span class="sxs-lookup"><span data-stu-id="be1d6-127">Regasm.exe adds an entry for the primary interop assembly under the same registry key as the original type library.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be1d6-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="be1d6-128">Example</span></span>  
 <span data-ttu-id="be1d6-129">L'exemple suivant inscrit l'assembly PIA `CompanyA.UtilLib.dll`.</span><span class="sxs-lookup"><span data-stu-id="be1d6-129">The following example registers the `CompanyA.UtilLib.dll` primary interop assembly.</span></span>  
  
```  
regasm CompanyA.UtilLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="be1d6-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be1d6-130">See Also</span></span>  
 [<span data-ttu-id="be1d6-131">Programmation avec des assemblys PIA</span><span class="sxs-lookup"><span data-stu-id="be1d6-131">Programming with Primary Interop Assemblies</span></span>](http://msdn.microsoft.com/library/306fa1d6-0703-4004-9e93-d0a57f1be81e)  
 [<span data-ttu-id="be1d6-132">Recherche d’assemblys PIA</span><span class="sxs-lookup"><span data-stu-id="be1d6-132">Locating Primary Interop Assemblies</span></span>](http://msdn.microsoft.com/library/d6768e4b-cd80-414d-a4f8-05d979eb393b)  
 [<span data-ttu-id="be1d6-133">Redistribution d’assemblys PIA</span><span class="sxs-lookup"><span data-stu-id="be1d6-133">Redistributing Primary Interop Assemblies</span></span>](http://msdn.microsoft.com/library/e76384f0-d631-474c-bdbd-13884cba0265)
