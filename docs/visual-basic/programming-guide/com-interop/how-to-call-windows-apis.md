---
title: "Comment : appeler des API Windows (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a219e031cdd36c713db8dcee6cc1da3849c9cf93
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="e2ec0-102">Comment : appeler des API Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2ec0-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="e2ec0-103">Cet exemple définit et appelle la `MessageBox` fonction dans user32.dll et lui passe une chaîne.</span><span class="sxs-lookup"><span data-stu-id="e2ec0-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2ec0-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="e2ec0-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e2ec0-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="e2ec0-105">Compiling the Code</span></span>  
 <span data-ttu-id="e2ec0-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="e2ec0-106">This example requires:</span></span>  
  
-   <span data-ttu-id="e2ec0-107">une référence à l'espace de noms <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="e2ec0-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e2ec0-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="e2ec0-108">Robust Programming</span></span>  
 <span data-ttu-id="e2ec0-109">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="e2ec0-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="e2ec0-110">La méthode n’est pas statique, est abstraite ou a été définie précédemment.</span><span class="sxs-lookup"><span data-stu-id="e2ec0-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="e2ec0-111">Le type parent est une interface, ou la longueur de *nom* ou *dllName* est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="e2ec0-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="e2ec0-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="e2ec0-112">(<xref:System.ArgumentException>)</span></span>  
  
-   <span data-ttu-id="e2ec0-113">Le *nom* ou *dllName* est `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="e2ec0-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="e2ec0-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="e2ec0-114">(<xref:System.ArgumentNullException>)</span></span>  
  
-   <span data-ttu-id="e2ec0-115">Le type conteneur a déjà été créé à l’aide de `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="e2ec0-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="e2ec0-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="e2ec0-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2ec0-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2ec0-117">See Also</span></span>  
 [<span data-ttu-id="e2ec0-118">L’appel de plateforme plus approfondie</span><span class="sxs-lookup"><span data-stu-id="e2ec0-118">A Closer Look at Platform Invoke</span></span>](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [<span data-ttu-id="e2ec0-119">Exemples d'appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="e2ec0-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="e2ec0-120">Consommation de fonctions DLL non managées</span><span class="sxs-lookup"><span data-stu-id="e2ec0-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="e2ec0-121">Émission de la définition d’une méthode avec la réflexion</span><span class="sxs-lookup"><span data-stu-id="e2ec0-121">Defining a Method with Reflection Emit</span></span>](http://msdn.microsoft.com/en-us/84fd3bf6-628f-41aa-83d9-b990cf926e81)  
 [<span data-ttu-id="e2ec0-122">Procédure pas à pas : appel des API Windows</span><span class="sxs-lookup"><span data-stu-id="e2ec0-122">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [<span data-ttu-id="e2ec0-123">COM Interop</span><span class="sxs-lookup"><span data-stu-id="e2ec0-123">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
