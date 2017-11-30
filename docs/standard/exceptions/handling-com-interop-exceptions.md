---
title: "Gestion des exceptions COM Interop"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: error-reference
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bc3e01bc8ca463460ede9544d1d5c095c39a59d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="handling-com-interop-exceptions"></a><span data-ttu-id="fecec-102">Gestion des exceptions COM Interop</span><span class="sxs-lookup"><span data-stu-id="fecec-102">Handling COM Interop Exceptions</span></span>
<span data-ttu-id="fecec-103">Le code managé et le code non managé peuvent collaborer pour gérer les exceptions.</span><span class="sxs-lookup"><span data-stu-id="fecec-103">Managed and unmanaged code can work together to handle exceptions.</span></span> <span data-ttu-id="fecec-104">Si une méthode lève une exception dans du code managé, le common language runtime peut passer HRESULT à un objet COM.</span><span class="sxs-lookup"><span data-stu-id="fecec-104">If a method throws an exception in managed code, the common language runtime can pass an HRESULT to a COM object.</span></span> <span data-ttu-id="fecec-105">Si une méthode échoue dans du code non managé en retournant un échec HRESULT, le runtime lève une exception qui peut être interceptée par du code managé.</span><span class="sxs-lookup"><span data-stu-id="fecec-105">If a method fails in unmanaged code by returning a failure HRESULT, the runtime throws an exception that can be caught by managed code.</span></span>  
  
 <span data-ttu-id="fecec-106">Le runtime mappe automatiquement la valeur HRESULT de COM Interop à des exceptions plus spécifiques.</span><span class="sxs-lookup"><span data-stu-id="fecec-106">The runtime automatically maps the HRESULT from COM interop to more specific exceptions.</span></span> <span data-ttu-id="fecec-107">Par exemple, E_ACCESSDENIED devient <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY devient <xref:System.OutOfMemoryException>, etc.</span><span class="sxs-lookup"><span data-stu-id="fecec-107">For example, E_ACCESSDENIED becomes <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY becomes <xref:System.OutOfMemoryException>, and so on.</span></span>  
  
 <span data-ttu-id="fecec-108">Si la valeur HRESULT est un résultat personnalisé ou si elle est inconnue du runtime, le runtime passe une exception générique <xref:System.Runtime.InteropServices.COMException> au client.</span><span class="sxs-lookup"><span data-stu-id="fecec-108">If the HRESULT is a custom result or if it is unknown to the runtime, the runtime passes a generic <xref:System.Runtime.InteropServices.COMException> to the client.</span></span> <span data-ttu-id="fecec-109">Le **ErrorCode** propriété de la **COMException** contient la valeur HRESULT.</span><span class="sxs-lookup"><span data-stu-id="fecec-109">The **ErrorCode** property of the **COMException** contains the HRESULT value.</span></span>  
  
## <a name="working-with-ierrorinfo"></a><span data-ttu-id="fecec-110">Utilisation d'IErrorInfo</span><span class="sxs-lookup"><span data-stu-id="fecec-110">Working with IErrorInfo</span></span>  
 <span data-ttu-id="fecec-111">Quand une erreur est passée de COM à du code managé, le runtime renseigne l'objet exception avec les informations de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="fecec-111">When an error is passed from COM to managed code, the runtime populates the exception object with error information.</span></span> <span data-ttu-id="fecec-112">Les objets COM qui prennent en charge IErrorInfo et qui retournent des valeurs HRESULT fournissent ces informations aux exceptions du code managé.</span><span class="sxs-lookup"><span data-stu-id="fecec-112">COM objects that support IErrorInfo and return HRESULTS provide this information to managed code exceptions.</span></span> <span data-ttu-id="fecec-113">Par exemple, le runtime mappe la description de l'erreur COM à la propriété <xref:System.Exception.Message%2A> de l'exception.</span><span class="sxs-lookup"><span data-stu-id="fecec-113">For example, the runtime maps the Description from the COM error to the exception's <xref:System.Exception.Message%2A> property.</span></span> <span data-ttu-id="fecec-114">Si la valeur HRESULT ne fournit pas d'informations d'erreur supplémentaires, le runtime renseigne un grand nombre de propriétés de l'exception avec des valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="fecec-114">If the HRESULT provides no additional error information, the runtime fills many of the exception's properties with default values.</span></span>  
  
 <span data-ttu-id="fecec-115">Si une méthode échoue dans du code non managé, une exception peut être passée à un segment de code managé.</span><span class="sxs-lookup"><span data-stu-id="fecec-115">If a method fails in unmanaged code, an exception can be passed to a managed code segment.</span></span> <span data-ttu-id="fecec-116">La rubrique [HRESULT et des Exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) contient un tableau montrant le mappage entre les objets d’exception runtime.</span><span class="sxs-lookup"><span data-stu-id="fecec-116">The topic [HRESULTS and Exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) contains a table showing how HRESULTS map to runtime exception objects.</span></span>  

## <a name="see-also"></a><span data-ttu-id="fecec-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fecec-117">See Also</span></span>
[<span data-ttu-id="fecec-118">Exceptions</span><span class="sxs-lookup"><span data-stu-id="fecec-118">Exceptions</span></span>](index.md) 
