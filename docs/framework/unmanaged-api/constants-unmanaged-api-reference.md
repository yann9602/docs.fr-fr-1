---
title: "Constantes (référence des API non managées)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- constants for unmanaged API [.NET Framework]
- native API reference [.NET Framework], constants
- unmanaged API reference [.NET Framework], constants
ms.assetid: 77526f65-b71c-4483-9d19-3a3751fd8a45
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e086e856bb7a872b14815825f78d208ff5296899
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="constants-unmanaged-api-reference"></a><span data-ttu-id="517e9-102">Constantes (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="517e9-102">Constants (Unmanaged API Reference)</span></span>
<span data-ttu-id="517e9-103">Cette rubrique décrit le type de langage, fournisseur de langage et les constantes de type de document qui sont définies dans CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="517e9-103">This topic describes the language type, language vendor, and document type constants that are defined in CorSym.idl.</span></span>  
  
## <a name="language-type-constants"></a><span data-ttu-id="517e9-104">Constantes de Type de langage</span><span class="sxs-lookup"><span data-stu-id="517e9-104">Language Type Constants</span></span>  
 <span data-ttu-id="517e9-105">Le tableau suivant affiche des constantes de type, qui représentent les GUID qui identifient les langages de programmation langage.</span><span class="sxs-lookup"><span data-stu-id="517e9-105">The following table shows language type constants, which represent GUIDs that identify programming languages.</span></span>  
  
|<span data-ttu-id="517e9-106">Symbole</span><span class="sxs-lookup"><span data-stu-id="517e9-106">Symbol</span></span>|<span data-ttu-id="517e9-107">Description</span><span class="sxs-lookup"><span data-stu-id="517e9-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="517e9-108">CorSym_LanguageType_C</span><span class="sxs-lookup"><span data-stu-id="517e9-108">CorSym_LanguageType_C</span></span>|<span data-ttu-id="517e9-109">Indique le langage C.</span><span class="sxs-lookup"><span data-stu-id="517e9-109">Indicates the C language.</span></span>|  
|<span data-ttu-id="517e9-110">CorSym_LanguageType_CPlusPlus</span><span class="sxs-lookup"><span data-stu-id="517e9-110">CorSym_LanguageType_CPlusPlus</span></span>|<span data-ttu-id="517e9-111">Indique le langage C++.</span><span class="sxs-lookup"><span data-stu-id="517e9-111">Indicates the C++ language.</span></span>|  
|<span data-ttu-id="517e9-112">CorSym_LanguageType_CSharp</span><span class="sxs-lookup"><span data-stu-id="517e9-112">CorSym_LanguageType_CSharp</span></span>|<span data-ttu-id="517e9-113">Indique le langage c#.</span><span class="sxs-lookup"><span data-stu-id="517e9-113">Indicates the C# language.</span></span>|  
|<span data-ttu-id="517e9-114">CorSym_LanguageType_Basic</span><span class="sxs-lookup"><span data-stu-id="517e9-114">CorSym_LanguageType_Basic</span></span>|<span data-ttu-id="517e9-115">Indique la langue de base.</span><span class="sxs-lookup"><span data-stu-id="517e9-115">Indicates the Basic language.</span></span>|  
|<span data-ttu-id="517e9-116">CorSym_LanguageType_Java</span><span class="sxs-lookup"><span data-stu-id="517e9-116">CorSym_LanguageType_Java</span></span>|<span data-ttu-id="517e9-117">Indique le langage Java.</span><span class="sxs-lookup"><span data-stu-id="517e9-117">Indicates the Java language.</span></span>|  
|<span data-ttu-id="517e9-118">CorSym_LanguageType_Cobol</span><span class="sxs-lookup"><span data-stu-id="517e9-118">CorSym_LanguageType_Cobol</span></span>|<span data-ttu-id="517e9-119">Indique la langue COBOL.</span><span class="sxs-lookup"><span data-stu-id="517e9-119">Indicates the COBOL language.</span></span>|  
|<span data-ttu-id="517e9-120">CorSym_LanguageType_Pascal</span><span class="sxs-lookup"><span data-stu-id="517e9-120">CorSym_LanguageType_Pascal</span></span>|<span data-ttu-id="517e9-121">Indique la langue de la casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="517e9-121">Indicates the Pascal language.</span></span>|  
|<span data-ttu-id="517e9-122">CorSym_LanguageType_ILAssembly</span><span class="sxs-lookup"><span data-stu-id="517e9-122">CorSym_LanguageType_ILAssembly</span></span>|<span data-ttu-id="517e9-123">Indique le code d’assembly de Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="517e9-123">Indicates the Microsoft intermediate language (MSIL) assembly code.</span></span>|  
|<span data-ttu-id="517e9-124">CorSym_LanguageType_JScript</span><span class="sxs-lookup"><span data-stu-id="517e9-124">CorSym_LanguageType_JScript</span></span>|<span data-ttu-id="517e9-125">Indique le langage JScript.</span><span class="sxs-lookup"><span data-stu-id="517e9-125">Indicates the JScript language.</span></span>|  
|<span data-ttu-id="517e9-126">CorSym_LanguageType_SMC</span><span class="sxs-lookup"><span data-stu-id="517e9-126">CorSym_LanguageType_SMC</span></span>|<span data-ttu-id="517e9-127">Indique la langue SMC.</span><span class="sxs-lookup"><span data-stu-id="517e9-127">Indicates the SMC language.</span></span>|  
|<span data-ttu-id="517e9-128">CorSym_LanguageType_MCPlusPlus</span><span class="sxs-lookup"><span data-stu-id="517e9-128">CorSym_LanguageType_MCPlusPlus</span></span>|<span data-ttu-id="517e9-129">Indique le langage C++ activé pour le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="517e9-129">Indicates the C++ language enabled for the .NET Framework.</span></span>|  
  
## <a name="language-vendor-constants"></a><span data-ttu-id="517e9-130">Constantes de fournisseur de langage</span><span class="sxs-lookup"><span data-stu-id="517e9-130">Language Vendor Constants</span></span>  
 <span data-ttu-id="517e9-131">Le tableau suivant affiche des constantes de fournisseur, qui représentent les GUID qui identifient les éditeurs de langage de programmation de langage.</span><span class="sxs-lookup"><span data-stu-id="517e9-131">The following table shows language vendor constants, which represent GUIDs that identify programming language vendors.</span></span>  
  
|<span data-ttu-id="517e9-132">Symbole</span><span class="sxs-lookup"><span data-stu-id="517e9-132">Symbol</span></span>|<span data-ttu-id="517e9-133">Description</span><span class="sxs-lookup"><span data-stu-id="517e9-133">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="517e9-134">CorSym_LanguageVendor_Microsoft</span><span class="sxs-lookup"><span data-stu-id="517e9-134">CorSym_LanguageVendor_Microsoft</span></span>|<span data-ttu-id="517e9-135">Indique à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="517e9-135">Indicates Microsoft.</span></span>|  
  
## <a name="document-type-constants"></a><span data-ttu-id="517e9-136">Constantes de Type de document</span><span class="sxs-lookup"><span data-stu-id="517e9-136">Document Type Constants</span></span>  
 <span data-ttu-id="517e9-137">Le tableau suivant présente des constantes de type, qui représentent les GUID qui identifient les types de document document.</span><span class="sxs-lookup"><span data-stu-id="517e9-137">The following table shows document type constants, which represent GUIDs that identify document types.</span></span>  
  
|<span data-ttu-id="517e9-138">Symbole</span><span class="sxs-lookup"><span data-stu-id="517e9-138">Symbol</span></span>|<span data-ttu-id="517e9-139">Description</span><span class="sxs-lookup"><span data-stu-id="517e9-139">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="517e9-140">CorSym_DocumentType_Text</span><span class="sxs-lookup"><span data-stu-id="517e9-140">CorSym_DocumentType_Text</span></span>|<span data-ttu-id="517e9-141">Indique un document texte.</span><span class="sxs-lookup"><span data-stu-id="517e9-141">Indicates a text document.</span></span>|  
|<span data-ttu-id="517e9-142">CorSym_DocumentType_MC</span><span class="sxs-lookup"><span data-stu-id="517e9-142">CorSym_DocumentType_MC</span></span>|<span data-ttu-id="517e9-143">Indique un document non textuelles.</span><span class="sxs-lookup"><span data-stu-id="517e9-143">Indicates a non-text document.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="517e9-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="517e9-144">See Also</span></span>  
 [<span data-ttu-id="517e9-145">Informations de référence sur les API non managées</span><span class="sxs-lookup"><span data-stu-id="517e9-145">Unmanaged API Reference</span></span>](../../../docs/framework/unmanaged-api/index.md)
