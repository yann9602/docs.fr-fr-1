---
title: ICeeGen, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen
helpviewer_keywords: ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73af58ac55fd22e5b4f19f715cb0b1a137a640a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iceegen-interface"></a><span data-ttu-id="b5e94-102">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="b5e94-102">ICeeGen Interface</span></span>
<span data-ttu-id="b5e94-103">Fournit des méthodes pour la compilation de code dynamique.</span><span class="sxs-lookup"><span data-stu-id="b5e94-103">Provides methods for dynamic code compilation.</span></span>  
  
 <span data-ttu-id="b5e94-104">Cette interface est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="b5e94-104">This interface is obsolete and should not be used.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b5e94-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b5e94-105">Methods</span></span>  
  
|<span data-ttu-id="b5e94-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="b5e94-106">Method</span></span>|<span data-ttu-id="b5e94-107">Description</span><span class="sxs-lookup"><span data-stu-id="b5e94-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b5e94-108">AddSectionReloc, méthode</span><span class="sxs-lookup"><span data-stu-id="b5e94-108">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|<span data-ttu-id="b5e94-109">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="b5e94-109">Obsolete.</span></span> <span data-ttu-id="b5e94-110">Ajoute une instruction .reloc au code base.</span><span class="sxs-lookup"><span data-stu-id="b5e94-110">Adds a .reloc instruction to the code base.</span></span>|  
|[<span data-ttu-id="b5e94-111">AllocateMethodBuffer, méthode</span><span class="sxs-lookup"><span data-stu-id="b5e94-111">AllocateMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|<span data-ttu-id="b5e94-112">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="b5e94-112">Obsolete.</span></span> <span data-ttu-id="b5e94-113">Crée une mémoire tampon de la taille spécifiée pour une méthode et obtient l’adresse virtuelle relative de la méthode.</span><span class="sxs-lookup"><span data-stu-id="b5e94-113">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>|  
|[<span data-ttu-id="b5e94-114">ComputePointer, méthode</span><span class="sxs-lookup"><span data-stu-id="b5e94-114">ComputePointer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|<span data-ttu-id="b5e94-115">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="b5e94-115">Obsolete.</span></span> <span data-ttu-id="b5e94-116">Détermine la mémoire tampon pour la section de code spécifié.</span><span class="sxs-lookup"><span data-stu-id="b5e94-116">Determines the buffer for the specified code section.</span></span>|  
|[<span data-ttu-id="b5e94-117">EmitString, méthode</span><span class="sxs-lookup"><span data-stu-id="b5e94-117">EmitString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|<span data-ttu-id="b5e94-118">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="b5e94-118">Obsolete.</span></span> <span data-ttu-id="b5e94-119">Émet la chaîne spécifiée dans la base de code.</span><span class="sxs-lookup"><span data-stu-id="b5e94-119">Emits the specified string into the code base.</span></span>|  
|[<span data-ttu-id="b5e94-120">GenerateCeeFile, méthode</span><span class="sxs-lookup"><span data-stu-id="b5e94-120">GenerateCeeFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|<span data-ttu-id="b5e94-121">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="b5e94-121">Obsolete.</span></span> <span data-ttu-id="b5e94-122">Génère un fichier de base de code qui contient le code base chargé actuellement dans cet `ICeeGen`.</span><span class="sxs-lookup"><span data-stu-id="b5e94-122">Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.</span></span>|  
|[<span data-ttu-id="b5e94-123">GenerateCeeMemoryImage, méthode</span><span class="sxs-lookup"><span data-stu-id="b5e94-123">GenerateCeeMemoryImage Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|<span data-ttu-id="b5e94-124">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="b5e94-124">Obsolete.</span></span> <span data-ttu-id="b5e94-125">Génère une image dans la mémoire pour la base de code.</span><span class="sxs-lookup"><span data-stu-id="b5e94-125">Generates an image in memory for the code base.</span></span>|  
|[<span data-ttu-id="b5e94-126">GetIlSection, méthode</span><span class="sxs-lookup"><span data-stu-id="b5e94-126">GetIlSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|<span data-ttu-id="b5e94-127">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="b5e94-127">Obsolete.</span></span> <span data-ttu-id="b5e94-128">Obtient la section de la base de code de langage intermédiaire référencée par le handle spécifié.</span><span class="sxs-lookup"><span data-stu-id="b5e94-128">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="b5e94-129">GetIMapTokenIface, méthode</span><span class="sxs-lookup"><span data-stu-id="b5e94-129">GetIMapTokenIface Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|<span data-ttu-id="b5e94-130">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="b5e94-130">Obsolete.</span></span> <span data-ttu-id="b5e94-131">Obtient l’interface référencée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="b5e94-131">Gets the interface referenced by the specified token.</span></span>|  
|[<span data-ttu-id="b5e94-132">GetMethodBuffer, méthode</span><span class="sxs-lookup"><span data-stu-id="b5e94-132">GetMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|<span data-ttu-id="b5e94-133">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="b5e94-133">Obsolete.</span></span> <span data-ttu-id="b5e94-134">Obtient une mémoire tampon de la taille appropriée de la méthode à l’adresse virtuelle relative spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b5e94-134">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="b5e94-135">GetSectionBlock, méthode</span><span class="sxs-lookup"><span data-stu-id="b5e94-135">GetSectionBlock Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|<span data-ttu-id="b5e94-136">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="b5e94-136">Obsolete.</span></span> <span data-ttu-id="b5e94-137">Obtient un bloc de section de la base de code.</span><span class="sxs-lookup"><span data-stu-id="b5e94-137">Gets a section block of the code base.</span></span>|  
|[<span data-ttu-id="b5e94-138">GetSectionCreate, méthode</span><span class="sxs-lookup"><span data-stu-id="b5e94-138">GetSectionCreate Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|<span data-ttu-id="b5e94-139">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="b5e94-139">Obsolete.</span></span> <span data-ttu-id="b5e94-140">Génère et obtient une section de code utilisant le nom spécifié et les valeurs d’indicateur.</span><span class="sxs-lookup"><span data-stu-id="b5e94-140">Generates and gets a code section using the specified name and flag values.</span></span>|  
|[<span data-ttu-id="b5e94-141">GetSectionDataLen, méthode</span><span class="sxs-lookup"><span data-stu-id="b5e94-141">GetSectionDataLen Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|<span data-ttu-id="b5e94-142">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="b5e94-142">Obsolete.</span></span> <span data-ttu-id="b5e94-143">Obtient la longueur de la section spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b5e94-143">Gets the length of the specified section.</span></span>|  
|[<span data-ttu-id="b5e94-144">GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="b5e94-144">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|<span data-ttu-id="b5e94-145">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="b5e94-145">Obsolete.</span></span> <span data-ttu-id="b5e94-146">Obtient la chaîne stockée à l’adresse virtuelle relative spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b5e94-146">Gets the string stored at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="b5e94-147">GetStringSection, méthode</span><span class="sxs-lookup"><span data-stu-id="b5e94-147">GetStringSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|<span data-ttu-id="b5e94-148">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="b5e94-148">Obsolete.</span></span> <span data-ttu-id="b5e94-149">Obtient une représentation sous forme de chaîne de la section de code référencée par le handle spécifié.</span><span class="sxs-lookup"><span data-stu-id="b5e94-149">Gets a string representation of the code section referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="b5e94-150">TruncateSection, méthode</span><span class="sxs-lookup"><span data-stu-id="b5e94-150">TruncateSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|<span data-ttu-id="b5e94-151">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="b5e94-151">Obsolete.</span></span> <span data-ttu-id="b5e94-152">Tronque la section de code spécifié par la longueur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b5e94-152">Truncates the specified code section by the specified length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5e94-153">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b5e94-153">Requirements</span></span>  
 <span data-ttu-id="b5e94-154">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5e94-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5e94-155">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b5e94-155">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b5e94-156">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b5e94-156">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b5e94-157">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5e94-157">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5e94-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5e94-158">See Also</span></span>  
 [<span data-ttu-id="b5e94-159">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="b5e94-159">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
