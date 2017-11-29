---
title: ASSEMBLY_INFO, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASSEMBLY_INFO
api_location: fusion.dll
api_type: COM
f1_keywords: ASSEMBLY_INFO
helpviewer_keywords: ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d532bbd2d338f942c09c4213620468a3361db5f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="assemblyinfo-structure"></a><span data-ttu-id="43901-102">ASSEMBLY_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="43901-102">ASSEMBLY_INFO Structure</span></span>
<span data-ttu-id="43901-103">Contient des informations sur un assembly qui est enregistré dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="43901-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43901-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43901-104">Syntax</span></span>  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="43901-105">Membres</span><span class="sxs-lookup"><span data-stu-id="43901-105">Members</span></span>  
  
|<span data-ttu-id="43901-106">Membre</span><span class="sxs-lookup"><span data-stu-id="43901-106">Member</span></span>|<span data-ttu-id="43901-107">Description</span><span class="sxs-lookup"><span data-stu-id="43901-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="43901-108">La taille, en octets, de la structure.</span><span class="sxs-lookup"><span data-stu-id="43901-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="43901-109">Ce champ est réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="43901-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="43901-110">Indicateurs qui indiquent les détails de l’installation sur l’assembly.</span><span class="sxs-lookup"><span data-stu-id="43901-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="43901-111">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="43901-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="43901-112">-La valeur ASSEMBLYINFO_FLAG_INSTALLED, ce qui indique que l’assembly est installé.</span><span class="sxs-lookup"><span data-stu-id="43901-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="43901-113">La version actuelle du .NET Framework définit toujours `dwAssemblyFlags` à cette valeur.</span><span class="sxs-lookup"><span data-stu-id="43901-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="43901-114">-La valeur ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, ce qui indique que l’assembly est un résident de charge utile.</span><span class="sxs-lookup"><span data-stu-id="43901-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="43901-115">La version actuelle du .NET Framework n’affecte jamais `dwAssemblyFlags` à cette valeur.</span><span class="sxs-lookup"><span data-stu-id="43901-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="43901-116">La taille totale, en kilo-octets, des fichiers contenant l’assembly.</span><span class="sxs-lookup"><span data-stu-id="43901-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="43901-117">Pointeur vers une mémoire tampon de chaîne qui contient le chemin d’accès actuel dans le fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="43901-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="43901-118">Le chemin d’accès doit se terminer par un caractère null.</span><span class="sxs-lookup"><span data-stu-id="43901-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="43901-119">Le nombre de caractères larges, y compris la marque de fin null, qui `pszCurrentAssemblyPathBuf` contient.</span><span class="sxs-lookup"><span data-stu-id="43901-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="43901-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="43901-120">Requirements</span></span>  
 <span data-ttu-id="43901-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43901-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43901-122">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="43901-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="43901-123">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43901-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43901-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43901-124">See Also</span></span>  
 [<span data-ttu-id="43901-125">Structures de fusion</span><span class="sxs-lookup"><span data-stu-id="43901-125">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [<span data-ttu-id="43901-126">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="43901-126">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
