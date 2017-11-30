---
title: ISymENCUnmanagedMethod, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod
helpviewer_keywords: ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 68929dc30b029133c73f18c3749f39f014359c0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="01eb3-102">ISymENCUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="01eb3-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="01eb3-103">Fournit des informations pour la fonctionnalité Modifier & Continuer.</span><span class="sxs-lookup"><span data-stu-id="01eb3-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01eb3-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="01eb3-104">Methods</span></span>  
  
|<span data-ttu-id="01eb3-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="01eb3-105">Method</span></span>|<span data-ttu-id="01eb3-106">Description</span><span class="sxs-lookup"><span data-stu-id="01eb3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01eb3-107">GetDocumentsForMethod (méthode)</span><span class="sxs-lookup"><span data-stu-id="01eb3-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="01eb3-108">Obtient les documents que cette méthode a des lignes.</span><span class="sxs-lookup"><span data-stu-id="01eb3-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="01eb3-109">GetDocumentsForMethodCount (méthode)</span><span class="sxs-lookup"><span data-stu-id="01eb3-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="01eb3-110">Obtient le nombre de documents que cette méthode a des lignes.</span><span class="sxs-lookup"><span data-stu-id="01eb3-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="01eb3-111">GetFileNameFromOffset (méthode)</span><span class="sxs-lookup"><span data-stu-id="01eb3-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="01eb3-112">Obtient le nom de fichier pour la ligne associée à un offset.</span><span class="sxs-lookup"><span data-stu-id="01eb3-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="01eb3-113">GetLineFromOffset (méthode)</span><span class="sxs-lookup"><span data-stu-id="01eb3-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="01eb3-114">Obtient les informations de ligne associées à un offset.</span><span class="sxs-lookup"><span data-stu-id="01eb3-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="01eb3-115">GetSourceExtentInDocument (méthode)</span><span class="sxs-lookup"><span data-stu-id="01eb3-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="01eb3-116">Obtient le plus petit de début ligne et la plus grande ligne de fin de la méthode dans un document spécifique.</span><span class="sxs-lookup"><span data-stu-id="01eb3-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="01eb3-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="01eb3-117">Requirements</span></span>  
 <span data-ttu-id="01eb3-118">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="01eb3-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01eb3-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01eb3-119">See Also</span></span>  
 [<span data-ttu-id="01eb3-120">Interfaces du magasin de symboles de Diagnostics</span><span class="sxs-lookup"><span data-stu-id="01eb3-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
