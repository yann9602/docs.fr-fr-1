---
title: "Comment : référencer des types .NET à partir de COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f58225e41d7e09471685395dd6e2194ee5de123c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="aac69-102">Comment : référencer des types .NET à partir de COM</span><span class="sxs-lookup"><span data-stu-id="aac69-102">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="aac69-103">Du point de vue du code client et serveur, les différences entre COM et le .NET Framework sont largement invisibles.</span><span class="sxs-lookup"><span data-stu-id="aac69-103">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="aac69-104">Les clients Microsoft Visual Basic peuvent afficher un objet .NET dans l’Explorateur d’objets, qui expose la syntaxe et les méthodes de l’objet, les propriétés et les champs exactement comme s’il s’agissait de tout autre objet COM.</span><span class="sxs-lookup"><span data-stu-id="aac69-104">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="aac69-105">Le processus d’importation d’une bibliothèque de types est légèrement plus compliqué pour les clients C++, même si vous utilisez les mêmes outils pour exporter des métadonnées vers une bibliothèque de types COM.</span><span class="sxs-lookup"><span data-stu-id="aac69-105">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="aac69-106">Pour référencer des membres d’objet .NET à partir d’un client C++ non managé, référencez le fichier TLB (produit à l’aide de Tlbexp.exe) avec la directive **#import**.</span><span class="sxs-lookup"><span data-stu-id="aac69-106">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="aac69-107">Lors du référencement d’une bibliothèque de types à partir de C++, vous devez soit spécifier l’option **raw_interfaces_only**, soit importer les définitions dans la bibliothèque de classes de base Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="aac69-107">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="aac69-108">Pour importer une bibliothèque</span><span class="sxs-lookup"><span data-stu-id="aac69-108">To import a library</span></span>  
  
-   <span data-ttu-id="aac69-109">Spécifiez l’option **raw_interfaces_only** dans la directive **#import**.</span><span class="sxs-lookup"><span data-stu-id="aac69-109">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="aac69-110">Exemple :</span><span class="sxs-lookup"><span data-stu-id="aac69-110">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="aac69-111">ou</span><span class="sxs-lookup"><span data-stu-id="aac69-111">-or-</span></span>  
  
-   <span data-ttu-id="aac69-112">Ajoutez une directive #import pour Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="aac69-112">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="aac69-113">Exemple :</span><span class="sxs-lookup"><span data-stu-id="aac69-113">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="aac69-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aac69-114">See Also</span></span>  
 [<span data-ttu-id="aac69-115">Exposition de composants .NET Framework à COM</span><span class="sxs-lookup"><span data-stu-id="aac69-115">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="aac69-116">Inscription d’assemblys dans COM</span><span class="sxs-lookup"><span data-stu-id="aac69-116">Registering Assemblies with COM</span></span>](../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [<span data-ttu-id="aac69-117">Appel d’un objet .NET</span><span class="sxs-lookup"><span data-stu-id="aac69-117">Calling a .NET Object</span></span>](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33)  
 [<span data-ttu-id="aac69-118">Déploiement d’une application pour accéder à COM</span><span class="sxs-lookup"><span data-stu-id="aac69-118">Deploying an Application for COM Access</span></span>](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce)
