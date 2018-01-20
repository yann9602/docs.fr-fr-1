---
title: "Marshaling d’un délégué comme méthode de rappel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 894445657c938d381a8585c5e9c7440c694aa5b1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="36c6b-102">Marshaling d’un délégué comme méthode de rappel</span><span class="sxs-lookup"><span data-stu-id="36c6b-102">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="36c6b-103">Cet exemple montre comment passer des délégués à une fonction non managée qui attend des pointeurs de fonction.</span><span class="sxs-lookup"><span data-stu-id="36c6b-103">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="36c6b-104">Un délégué est une classe qui peut contenir une référence à une méthode, et qui équivaut à un pointeur de fonction de type sécurisé ou à une fonction de rappel.</span><span class="sxs-lookup"><span data-stu-id="36c6b-104">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36c6b-105">Quand vous utilisez un délégué à l’intérieur d’un appel, le common language runtime protège le délégué d’une garbage collection pendant la durée de cet appel.</span><span class="sxs-lookup"><span data-stu-id="36c6b-105">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="36c6b-106">Cependant, si la fonction non managée stocke le délégué pour l’utiliser une fois l’appel terminé, vous devez empêcher manuellement la garbage collection jusqu’à ce que la fonction non managée en termine avec le délégué.</span><span class="sxs-lookup"><span data-stu-id="36c6b-106">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="36c6b-107">Pour plus d’informations, consultez [HandleRef, exemple](http://msdn.microsoft.com/library/ab23b04e-1d53-4ec7-b27a-e892d9298959) et [GCHandle, exemple](http://msdn.microsoft.com/library/6acce798-0385-4ded-a790-77da842c113f).</span><span class="sxs-lookup"><span data-stu-id="36c6b-107">For more information, see the [HandleRef Sample](http://msdn.microsoft.com/library/ab23b04e-1d53-4ec7-b27a-e892d9298959) and [GCHandle Sample](http://msdn.microsoft.com/library/6acce798-0385-4ded-a790-77da842c113f).</span></span>  
  
 <span data-ttu-id="36c6b-108">L’exemple de rappel utilise les fonctions non managées suivantes, qui sont montrées avec leur déclaration de fonction d’origine :</span><span class="sxs-lookup"><span data-stu-id="36c6b-108">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="36c6b-109">**TestCallBack** exportée depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="36c6b-109">**TestCallBack** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   <span data-ttu-id="36c6b-110">**TestCallBack2** exportée depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="36c6b-110">**TestCallBack2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 <span data-ttu-id="36c6b-111">[PinvokeLib.dll](http://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614) est une bibliothèque non managée personnalisée qui contient une implémentation des fonctions précédemment répertoriées.</span><span class="sxs-lookup"><span data-stu-id="36c6b-111">[PinvokeLib.dll](http://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>  
  
 <span data-ttu-id="36c6b-112">Dans cet exemple, la classe `LibWrap` contient des prototypes managés pour les méthodes `TestCallBack` et `TestCallBack2`.</span><span class="sxs-lookup"><span data-stu-id="36c6b-112">In this sample, the `LibWrap` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="36c6b-113">Ces deux méthodes passent un délégué comme paramètre à une fonction de rappel.</span><span class="sxs-lookup"><span data-stu-id="36c6b-113">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="36c6b-114">La signature du délégué doit correspondre à la signature de la méthode qu’il référence.</span><span class="sxs-lookup"><span data-stu-id="36c6b-114">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="36c6b-115">Par exemple, les délégués `FPtr` et `FPtr2` ont des signatures qui sont identiques à celles des méthodes `DoSomething` et `DoSomething2`.</span><span class="sxs-lookup"><span data-stu-id="36c6b-115">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="36c6b-116">Déclaration de prototypes</span><span class="sxs-lookup"><span data-stu-id="36c6b-116">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## <a name="calling-functions"></a><span data-ttu-id="36c6b-117">Appel de fonctions</span><span class="sxs-lookup"><span data-stu-id="36c6b-117">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="36c6b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36c6b-118">See Also</span></span>  
 [<span data-ttu-id="36c6b-119">Exemples divers de marshaling</span><span class="sxs-lookup"><span data-stu-id="36c6b-119">Miscellaneous Marshaling Samples</span></span>](http://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70)  
 [<span data-ttu-id="36c6b-120">Types de données d’appel de plateforme</span><span class="sxs-lookup"><span data-stu-id="36c6b-120">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="36c6b-121">Création de prototypes dans du code managé</span><span class="sxs-lookup"><span data-stu-id="36c6b-121">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
