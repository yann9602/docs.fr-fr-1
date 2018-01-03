---
title: "Énumération AssemblyOptions"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyOptions
api_location: alink.dll
api_type: COM
f1_keywords: AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ad4f9e02ed0d22009fcb8a5ac078231f2cb22e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="81136-102">Énumération AssemblyOptions</span><span class="sxs-lookup"><span data-stu-id="81136-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="81136-103">Énumère les options de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="81136-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81136-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81136-104">Syntax</span></span>  
  
```  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a><span data-ttu-id="81136-105">Champs</span><span class="sxs-lookup"><span data-stu-id="81136-105">Fields</span></span>  
  
|<span data-ttu-id="81136-106">Champ</span><span class="sxs-lookup"><span data-stu-id="81136-106">Field</span></span>|<span data-ttu-id="81136-107">Description</span><span class="sxs-lookup"><span data-stu-id="81136-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="81136-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="81136-108">optAssemTitle</span></span>|<span data-ttu-id="81136-109">Chaîne - représente le titre de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="81136-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="81136-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="81136-110">optAssemDescription</span></span>|<span data-ttu-id="81136-111">Chaîne - contient la description de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="81136-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="81136-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="81136-112">optAssemConfig</span></span>|<span data-ttu-id="81136-113">Chaîne - contient la configuration de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="81136-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="81136-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="81136-114">optAssemOS</span></span>|<span data-ttu-id="81136-115">Chaîne - encodée comme : « dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion ».</span><span class="sxs-lookup"><span data-stu-id="81136-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="81136-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="81136-116">optAssemProcessor</span></span>|<span data-ttu-id="81136-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="81136-117">ULONG</span></span>|  
|<span data-ttu-id="81136-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="81136-118">optAssemLocale</span></span>|<span data-ttu-id="81136-119">Chaîne - contient les paramètres régionaux d’assembly.</span><span class="sxs-lookup"><span data-stu-id="81136-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="81136-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="81136-120">optAssemVersion</span></span>|<span data-ttu-id="81136-121">Chaîne - encodée comme : « Major.Minor.Build.Revision ».</span><span class="sxs-lookup"><span data-stu-id="81136-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="81136-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="81136-122">optAssemCompany</span></span>|<span data-ttu-id="81136-123">Chaîne - contient la société.</span><span class="sxs-lookup"><span data-stu-id="81136-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="81136-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="81136-124">optAssemProduct</span></span>|<span data-ttu-id="81136-125">Chaîne - contient le nom du produit.</span><span class="sxs-lookup"><span data-stu-id="81136-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="81136-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="81136-126">optAssemProductVersion</span></span>|<span data-ttu-id="81136-127">Chaîne (également appelé InformationalVersion).</span><span class="sxs-lookup"><span data-stu-id="81136-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="81136-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="81136-128">optAssemCopyright</span></span>|<span data-ttu-id="81136-129">Chaîne - contient les informations de copyright.</span><span class="sxs-lookup"><span data-stu-id="81136-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="81136-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="81136-130">optAssemTrademark</span></span>|<span data-ttu-id="81136-131">Chaîne - contient les informations de marque.</span><span class="sxs-lookup"><span data-stu-id="81136-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="81136-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="81136-132">optAssemKeyFile</span></span>|<span data-ttu-id="81136-133">String (nom de fichier).</span><span class="sxs-lookup"><span data-stu-id="81136-133">String (file name).</span></span>|  
|<span data-ttu-id="81136-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="81136-134">optAssemKeyName</span></span>|<span data-ttu-id="81136-135">Chaîne (le nom de clé).</span><span class="sxs-lookup"><span data-stu-id="81136-135">String (The key name).</span></span>|  
|<span data-ttu-id="81136-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="81136-136">optAssemAlgID</span></span>|<span data-ttu-id="81136-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="81136-137">ULONG</span></span>|  
|<span data-ttu-id="81136-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="81136-138">optAssemFlags</span></span>|<span data-ttu-id="81136-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="81136-139">ULONG</span></span>|  
|<span data-ttu-id="81136-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="81136-140">optAssemHalfSign</span></span>|<span data-ttu-id="81136-141">Bool (également appelé DelaySign).</span><span class="sxs-lookup"><span data-stu-id="81136-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="81136-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="81136-142">optAssemFileVersion</span></span>|<span data-ttu-id="81136-143">Chaîne - encodée comme « Major.Minor.Build.Revision » - identique à ProductVersion.</span><span class="sxs-lookup"><span data-stu-id="81136-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="81136-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="81136-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="81136-145">Chaîne - encodée sous la forme « Major.Minor.Build.Revision ».</span><span class="sxs-lookup"><span data-stu-id="81136-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="81136-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="81136-146">optLastAssemOption</span></span>|<span data-ttu-id="81136-147">Un compteur du nombre d’éléments.</span><span class="sxs-lookup"><span data-stu-id="81136-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="81136-148">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="81136-148">Requirements</span></span>  
 <span data-ttu-id="81136-149">**En-tête :** alink.h</span><span class="sxs-lookup"><span data-stu-id="81136-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="81136-150">**Bibliothèque**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="81136-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81136-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81136-151">See Also</span></span>  
 [<span data-ttu-id="81136-152">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="81136-152">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
