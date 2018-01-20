---
title: Inscription d'assemblys dans COM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 39466115e3835361c76361d3cfc04f76161e7dd5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="registering-assemblies-with-com"></a><span data-ttu-id="738a5-102">Inscription d'assemblys dans COM</span><span class="sxs-lookup"><span data-stu-id="738a5-102">Registering Assemblies with COM</span></span>
<span data-ttu-id="738a5-103">Vous pouvez exécuter l’outil en ligne de commande [Assembly Registration Tool (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) pour inscrire ou désinscrire un assembly à utiliser avec COM.</span><span class="sxs-lookup"><span data-stu-id="738a5-103">You can run a command-line tool called the [Assembly Registration Tool (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) to register or unregister an assembly for use with COM.</span></span> <span data-ttu-id="738a5-104">Regasm.exe ajoute des informations sur la classe au Registre système pour que les clients COM puissent utiliser la classe .NET Framework en toute transparence.</span><span class="sxs-lookup"><span data-stu-id="738a5-104">Regasm.exe adds information about the class to the system registry so COM clients can use the .NET Framework class transparently.</span></span> <span data-ttu-id="738a5-105">La classe <xref:System.Runtime.InteropServices.RegistrationServices> fournit des fonctionnalités équivalentes.</span><span class="sxs-lookup"><span data-stu-id="738a5-105">The <xref:System.Runtime.InteropServices.RegistrationServices> class provides the equivalent functionality.</span></span>  
  
 <span data-ttu-id="738a5-106">Pour activer un composant managé à partir d’un client COM, vous devez d’abord l’inscrire dans le Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="738a5-106">A managed component must be registered in the Windows registry before it can be activated from a COM client.</span></span> <span data-ttu-id="738a5-107">Le tableau suivant montre les clés que Regasm.exe ajoute généralement au Registre Windows</span><span class="sxs-lookup"><span data-stu-id="738a5-107">The following table shows the keys that Regasm.exe typically adds to the Windows registry.</span></span> <span data-ttu-id="738a5-108">(000000 indique la valeur GUID).</span><span class="sxs-lookup"><span data-stu-id="738a5-108">(000000 indicates the actual GUID value.)</span></span>  
  
|<span data-ttu-id="738a5-109">GUID</span><span class="sxs-lookup"><span data-stu-id="738a5-109">GUID</span></span>|<span data-ttu-id="738a5-110">Description</span><span class="sxs-lookup"><span data-stu-id="738a5-110">Description</span></span>|<span data-ttu-id="738a5-111">Clé du Registre</span><span class="sxs-lookup"><span data-stu-id="738a5-111">Registry key</span></span>|  
|----------|-----------------|------------------|  
|<span data-ttu-id="738a5-112">CLSID</span><span class="sxs-lookup"><span data-stu-id="738a5-112">CLSID</span></span>|<span data-ttu-id="738a5-113">Identificateur de classe</span><span class="sxs-lookup"><span data-stu-id="738a5-113">Class identifier</span></span>|<span data-ttu-id="738a5-114">HKEY_CLASSES_ROOT\CLSID\\{000…000}</span><span class="sxs-lookup"><span data-stu-id="738a5-114">HKEY_CLASSES_ROOT\CLSID\\{000…000}</span></span>|  
|<span data-ttu-id="738a5-115">IID</span><span class="sxs-lookup"><span data-stu-id="738a5-115">IID</span></span>|<span data-ttu-id="738a5-116">Identificateur d’interface</span><span class="sxs-lookup"><span data-stu-id="738a5-116">Interface identifier</span></span>|<span data-ttu-id="738a5-117">HKEY_CLASSES_ROOT\Interface\\{000…000}</span><span class="sxs-lookup"><span data-stu-id="738a5-117">HKEY_CLASSES_ROOT\Interface\\{000…000}</span></span>|  
|<span data-ttu-id="738a5-118">LIBID</span><span class="sxs-lookup"><span data-stu-id="738a5-118">LIBID</span></span>|<span data-ttu-id="738a5-119">Identificateur de bibliothèque</span><span class="sxs-lookup"><span data-stu-id="738a5-119">Library identifier</span></span>|<span data-ttu-id="738a5-120">HKEY_CLASSES_ROOT\TypeLib\\{000…000}</span><span class="sxs-lookup"><span data-stu-id="738a5-120">HKEY_CLASSES_ROOT\TypeLib\\{000…000}</span></span>|  
|<span data-ttu-id="738a5-121">ProgID</span><span class="sxs-lookup"><span data-stu-id="738a5-121">ProgID</span></span>|<span data-ttu-id="738a5-122">Identificateur programmatique</span><span class="sxs-lookup"><span data-stu-id="738a5-122">Programmatic identifier</span></span>|<span data-ttu-id="738a5-123">HKEY_CLASSES_ROOT\000…000</span><span class="sxs-lookup"><span data-stu-id="738a5-123">HKEY_CLASSES_ROOT\000…000</span></span>|  
  
 <span data-ttu-id="738a5-124">Sous la clé HKCR\CLSID\\{0000…0000}, la valeur par défaut est définie sur le ProgID de la classe, et deux nouvelles valeurs nommées, Class et Assembly, sont ajoutées.</span><span class="sxs-lookup"><span data-stu-id="738a5-124">Under the HKCR\CLSID\\{0000…0000} key, the default value is set to the ProgID of the class, and two new named values, Class and Assembly, are added.</span></span> <span data-ttu-id="738a5-125">Le runtime lit la valeur Assembly à partir du Registre et la passe au service de résolution d’assembly du runtime.</span><span class="sxs-lookup"><span data-stu-id="738a5-125">The runtime reads the Assembly value from the registry and passes it on to the runtime assembly resolver.</span></span> <span data-ttu-id="738a5-126">Le service de résolution d’assembly tente de localiser l’assembly, en se basant sur son nom et son numéro de version.</span><span class="sxs-lookup"><span data-stu-id="738a5-126">The assembly resolver attempts to locate the assembly, based on assembly information such as the name and version number.</span></span> <span data-ttu-id="738a5-127">Pour que le service de résolution d’assembly puisse localiser un assembly, celui-ci doit se trouver dans l’un des emplacements suivants :</span><span class="sxs-lookup"><span data-stu-id="738a5-127">For the assembly resolver to locate an assembly, the assembly has to be in one of the following locations:</span></span>  
  
-   <span data-ttu-id="738a5-128">Le Global Assembly Cache (il doit s’agir d’un assembly avec un nom fort)</span><span class="sxs-lookup"><span data-stu-id="738a5-128">The global assembly cache (must be a strong-named assembly).</span></span>  
  
-   <span data-ttu-id="738a5-129">Le répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="738a5-129">In the application directory.</span></span> <span data-ttu-id="738a5-130">Les assemblys chargés à partir du chemin d’une application ne sont accessibles qu’à partir de cette application.</span><span class="sxs-lookup"><span data-stu-id="738a5-130">Assemblies loaded from the application path are only accessible from that application.</span></span>  
  
-   <span data-ttu-id="738a5-131">Sur un chemin de fichier spécifié avec l’option **/codebase** définie sur Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="738a5-131">Along an file path specified with the **/codebase** option to Regasm.exe.</span></span>  
  
 <span data-ttu-id="738a5-132">Regasm.exe crée également la clé InProcServer32 sous la clé HKCR\CLSID\\{0000…0000}.</span><span class="sxs-lookup"><span data-stu-id="738a5-132">Regasm.exe also creates the InProcServer32 key under the HKCR\CLSID\\{0000…0000} key.</span></span> <span data-ttu-id="738a5-133">La valeur par défaut de la clé est définie sur le nom de la DLL qui initialise le common language runtime (Mscoree.dll).</span><span class="sxs-lookup"><span data-stu-id="738a5-133">The default value for the key is set to the name of the DLL that initializes the common language runtime (Mscoree.dll).</span></span>  
  
## <a name="examining-registry-entries"></a><span data-ttu-id="738a5-134">Examen des entrées du Registre</span><span class="sxs-lookup"><span data-stu-id="738a5-134">Examining Registry Entries</span></span>  
 <span data-ttu-id="738a5-135">COM Interop fournit une implémentation de fabrique de classe standard permettant de créer une instance de n’importe quelle classe .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="738a5-135">COM interop provides a standard class factory implementation to create an instance of any .NET Framework class.</span></span> <span data-ttu-id="738a5-136">Les clients peuvent appeler **DllGetClassObject** dans la DLL managée pour obtenir une fabrique de classe et créer des objets, comme ils le feraient avec tout autre composant COM.</span><span class="sxs-lookup"><span data-stu-id="738a5-136">Clients can call **DllGetClassObject** on the managed DLL to get a class factory and create objects, just as they would with any other COM component.</span></span>  
  
 <span data-ttu-id="738a5-137">Pour la sous-clé `InprocServer32`, une référence à Mscoree.dll s’affiche (au lieu d’une bibliothèque de types COM traditionnelle) pour indiquer que le common language runtime crée l’objet managé.</span><span class="sxs-lookup"><span data-stu-id="738a5-137">For the `InprocServer32` subkey, a reference to Mscoree.dll appears in place of a traditional COM type library to indicate that the common language runtime creates the managed object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="738a5-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="738a5-138">See Also</span></span>  
 [<span data-ttu-id="738a5-139">Exposition de composants .NET Framework à COM</span><span class="sxs-lookup"><span data-stu-id="738a5-139">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="738a5-140">Comment : référencer des types .NET à partir de COM</span><span class="sxs-lookup"><span data-stu-id="738a5-140">How to: Reference .NET Types from COM</span></span>](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)  
 [<span data-ttu-id="738a5-141">Appel d’un objet .NET</span><span class="sxs-lookup"><span data-stu-id="738a5-141">Calling a .NET Object</span></span>](http://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33)  
 [<span data-ttu-id="738a5-142">Déploiement d’une application pour accéder à COM</span><span class="sxs-lookup"><span data-stu-id="738a5-142">Deploying an Application for COM Access</span></span>](http://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce)
