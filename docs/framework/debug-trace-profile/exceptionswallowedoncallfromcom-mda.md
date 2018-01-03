---
title: "Assistant Débogage managé exceptionSwallowedOnCallFromCom"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c20c4e0b6c1c711b2044bc3ba32d00447220cb8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="303a8-102">Assistant Débogage managé exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="303a8-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="303a8-103">L'Assistant Débogage managé `exceptionSwallowedOnCallFromCOM` est activé quand une exception est levée à partir d'un code CLR (Common Language Runtime) appelé depuis COM via une méthode dépourvue de type de retour HRESULT non managé.</span><span class="sxs-lookup"><span data-stu-id="303a8-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="303a8-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="303a8-104">Symptoms</span></span>  
 <span data-ttu-id="303a8-105">Un appel à un composant managé depuis COM retourne la valeur FALSE ou 0.</span><span class="sxs-lookup"><span data-stu-id="303a8-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="303a8-106">Par ailleurs, si la méthode possède un type de retour void, la levée d'une exception pendant l'exécution de la méthode peut passer inaperçue.</span><span class="sxs-lookup"><span data-stu-id="303a8-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="303a8-107">Dans ce cas, l'exception est interceptée discrètement et l'appelant COM reprend la main.</span><span class="sxs-lookup"><span data-stu-id="303a8-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="303a8-108">Cause</span><span class="sxs-lookup"><span data-stu-id="303a8-108">Cause</span></span>  
 <span data-ttu-id="303a8-109">Une exception a été levée, mais aucune procédure valide ne permet de la signaler.</span><span class="sxs-lookup"><span data-stu-id="303a8-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="303a8-110">Solution</span><span class="sxs-lookup"><span data-stu-id="303a8-110">Resolution</span></span>  
 <span data-ttu-id="303a8-111">Le message est purement informatif, et n'indique pas nécessairement la présence d'un bogue.</span><span class="sxs-lookup"><span data-stu-id="303a8-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="303a8-112">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="303a8-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="303a8-113">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="303a8-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="303a8-114">Il indique uniquement des informations sur les exceptions interceptées discrètement.</span><span class="sxs-lookup"><span data-stu-id="303a8-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="303a8-115">Sortie</span><span class="sxs-lookup"><span data-stu-id="303a8-115">Output</span></span>  
 <span data-ttu-id="303a8-116">Message d'information contenant le nom de la méthode, le nom du type et le message de l'exception.</span><span class="sxs-lookup"><span data-stu-id="303a8-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="303a8-117">Configuration</span><span class="sxs-lookup"><span data-stu-id="303a8-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="303a8-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="303a8-118">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="303a8-119">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="303a8-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="303a8-120">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="303a8-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
