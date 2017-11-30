---
title: "CorAssemblyFlags, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorAssemblyFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorAssemblyFlags
helpviewer_keywords: CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 67057944705a1cecd1754c3c11da08725c9a93f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corassemblyflags-enumeration"></a><span data-ttu-id="64c64-102">CorAssemblyFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="64c64-102">CorAssemblyFlags Enumeration</span></span>
<span data-ttu-id="64c64-103">Contient des valeurs qui décrivent les métadonnées appliquées à une compilation d'assembly.</span><span class="sxs-lookup"><span data-stu-id="64c64-103">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64c64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64c64-104">Syntax</span></span>  
  
```  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="64c64-105">Membres</span><span class="sxs-lookup"><span data-stu-id="64c64-105">Members</span></span>  
  
|<span data-ttu-id="64c64-106">Membre</span><span class="sxs-lookup"><span data-stu-id="64c64-106">Member</span></span>|<span data-ttu-id="64c64-107">Description</span><span class="sxs-lookup"><span data-stu-id="64c64-107">Description</span></span>|  
|------------|-----------------|  
|`afPublicKey`|<span data-ttu-id="64c64-108">Indique que la référence d’assembly conserve la clé publique complète non hachée.</span><span class="sxs-lookup"><span data-stu-id="64c64-108">Indicates that the assembly reference holds the full, unhashed public key.</span></span>|  
|`afPA_None`|<span data-ttu-id="64c64-109">Indique que l’architecture de processeur n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="64c64-109">Indicates that the processor architecture is unspecified.</span></span>|  
|`afPA_MSIL`|<span data-ttu-id="64c64-110">Indique que l’architecture de processeur est neutre (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="64c64-110">Indicates that the processor architecture is neutral (PE32).</span></span>|  
|`afPA_x86`|<span data-ttu-id="64c64-111">Indique que l’architecture de processeur est x86 (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="64c64-111">Indicates that the processor architecture is x86 (PE32).</span></span>|  
|`afPA_IA64`|<span data-ttu-id="64c64-112">Indique que l’architecture de processeur est Itanium (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="64c64-112">Indicates that the processor architecture is Itanium (PE32+).</span></span>|  
|`afPA_AMD64`|<span data-ttu-id="64c64-113">Indique que l’architecture de processeur est AMD X64 (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="64c64-113">Indicates that the processor architecture is AMD X64 (PE32+).</span></span>|  
|`afPA_ARM`|<span data-ttu-id="64c64-114">Indique que l’architecture de processeur ARM (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="64c64-114">Indicates that the processor architecture is ARM (PE32).</span></span>|  
|`afPA_NoPlatform`|<span data-ttu-id="64c64-115">Indique que l’assembly est un assembly de référence ; Autrement dit, elle s’applique à n’importe quelle architecture mais ne peut pas s’exécuter sur n’importe quelle architecture.</span><span class="sxs-lookup"><span data-stu-id="64c64-115">Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture.</span></span> <span data-ttu-id="64c64-116">Par conséquent, l’indicateur est identique à `afPA_Mask`.</span><span class="sxs-lookup"><span data-stu-id="64c64-116">Thus, the flag is the same as `afPA_Mask`.</span></span>|  
|`afPA_Specified`|<span data-ttu-id="64c64-117">Indique que les indicateurs de l’architecture processeur doivent être propagées vers le `AssemblyRef` enregistrement.</span><span class="sxs-lookup"><span data-stu-id="64c64-117">Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.</span></span>|  
|`afPA_Mask`|<span data-ttu-id="64c64-118">Masque qui décrit l’architecture de processeur.</span><span class="sxs-lookup"><span data-stu-id="64c64-118">A mask that describes the processor architecture.</span></span>|  
|`afPA_FullMask`|<span data-ttu-id="64c64-119">Spécifie que la description d’architecture de processeur est incluse.</span><span class="sxs-lookup"><span data-stu-id="64c64-119">Specifies that the processor architecture description is included.</span></span>|  
|`afPA_Shift`|<span data-ttu-id="64c64-120">Indique un compteur de décalage dans les indicateurs de l’architecture processeur vers et à partir de l’index.</span><span class="sxs-lookup"><span data-stu-id="64c64-120">Indicates a shift count in the processor architecture flags to and from the index.</span></span>|  
|`afEnableJITcompileTracking`|<span data-ttu-id="64c64-121">Indique la valeur correspondante à partir de la <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> de la <xref:System.Diagnostics.DebuggableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="64c64-121">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afDisableJITcompileOptimizer`|<span data-ttu-id="64c64-122">Indique la valeur correspondante à partir de la <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> de la <xref:System.Diagnostics.DebuggableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="64c64-122">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afRetargetable`|<span data-ttu-id="64c64-123">Indique que l’assembly peut être reciblé au moment de l’exécution à un assembly à partir d’un autre serveur de publication.</span><span class="sxs-lookup"><span data-stu-id="64c64-123">Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.</span></span>|  
|`afContentType_Mask`|<span data-ttu-id="64c64-124">Masque qui décrit le type de contenu.</span><span class="sxs-lookup"><span data-stu-id="64c64-124">A mask that describes the content type.</span></span>|  
|`afContentType_Default`|<span data-ttu-id="64c64-125">Indique le type de contenu par défaut.</span><span class="sxs-lookup"><span data-stu-id="64c64-125">Indicates the default content type.</span></span>|  
|`afContentType_WindowsRuntime`|<span data-ttu-id="64c64-126">Indique le [!INCLUDE[wrt](../../../../includes/wrt-md.md)] le type de contenu.</span><span class="sxs-lookup"><span data-stu-id="64c64-126">Indicates the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] content type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="64c64-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="64c64-127">Requirements</span></span>  
 <span data-ttu-id="64c64-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64c64-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64c64-129">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="64c64-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="64c64-130">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64c64-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64c64-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64c64-131">See Also</span></span>  
 [<span data-ttu-id="64c64-132">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="64c64-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
