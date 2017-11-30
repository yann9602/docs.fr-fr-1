---
title: "marshaler des données avec COM Interop"
ms.custom: 
ms.date: 09/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2def27790a1727bda524b8c14a93f7b78127a569
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="425e5-102">marshaler des données avec COM Interop</span><span class="sxs-lookup"><span data-stu-id="425e5-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="425e5-103">COM Interop prend en charge l'utilisation des objets COM à partir de code managé, ainsi que l'exposition des objets managés à COM.</span><span class="sxs-lookup"><span data-stu-id="425e5-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="425e5-104">La prise en charge du marshaling des données vers et depuis COM est complète et fournit quasiment toujours le comportement de marshaling approprié.</span><span class="sxs-lookup"><span data-stu-id="425e5-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="425e5-105">Le [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] comprend les outils COM Interop suivants :</span><span class="sxs-lookup"><span data-stu-id="425e5-105">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] includes the following COM interop tools:</span></span>  
  
-   <span data-ttu-id="425e5-106">[Importateur de bibliothèques de types (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), qui convertit une bibliothèque de types COM en un assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="425e5-106">[Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="425e5-107">À partir de cet assembly, le service de marshaling d’interopérabilité génère des wrappers qui effectuent le marshaling des données entre la mémoire managée et non managée.</span><span class="sxs-lookup"><span data-stu-id="425e5-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
-   <span data-ttu-id="425e5-108">[Exportateur de bibliothèques de types (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), qui produit une bibliothèque de types COM à partir d’un assembly et génère un wrapper qui effectue le marshaling lors des appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="425e5-108">[Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="425e5-109">Les sections suivantes lien vers les rubriques qui décrivent les processus de personnalisation des wrappers d’interopérabilité lorsque vous pouvez (ou devez) fournir au marshaleur des informations de type supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="425e5-109">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="425e5-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="425e5-110">In This Section</span></span>  
<span data-ttu-id="425e5-111">[Comment : créer manuellement des Wrappers](how-to-create-wrappers-manually.md) </span><span class="sxs-lookup"><span data-stu-id="425e5-111">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) </span></span>  
<span data-ttu-id="425e5-112">Décrit comment créer un wrapper COM manuellement dans du code source managé.</span><span class="sxs-lookup"><span data-stu-id="425e5-112">Describes how to create a COM wrapper manually in managed source code.</span></span> 
 
 [<span data-ttu-id="425e5-113">Guide pratique pour migrer le modèle DCOM de code managé vers WCF</span><span class="sxs-lookup"><span data-stu-id="425e5-113">How to: Migrate Managed-Code DCOM to WCF</span></span>](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="425e5-114">Décrit comment migrer du code DCOM managé vers WCF pour la solution la plus sécurisée.</span><span class="sxs-lookup"><span data-stu-id="425e5-114">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="425e5-115">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="425e5-115">Related Sections</span></span>  
 <span data-ttu-id="425e5-116">[Types de données COM](https://msdn.microsoft.com/en-us/library/sak564ww(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="425e5-116">[COM Data Types](https://msdn.microsoft.com/en-us/library/sak564ww(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="425e5-117">Fournit les types de données managés et non managés correspondants.</span><span class="sxs-lookup"><span data-stu-id="425e5-117">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="425e5-118">[Personnalisation des wrappers CCW (COM Callable Wrapper)](https://msdn.microsoft.com/en-us/library/3bwc828w(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="425e5-118">[Customizing COM Callable Wrappers](https://msdn.microsoft.com/en-us/library/3bwc828w(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="425e5-119">Décrit comment marshaler explicitement des types de données à l’aide de la <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribut au moment du design.</span><span class="sxs-lookup"><span data-stu-id="425e5-119">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="425e5-120">[Personnalisation des wrappers RCW (Runtime Callable Wrapper)](https://msdn.microsoft.com/en-us/library/e753eftz(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="425e5-120">[Customizing Runtime Callable Wrappers](https://msdn.microsoft.com/en-us/library/e753eftz(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="425e5-121">Décrit comment ajuster le comportement de marshaling des types dans un assembly d’interopérabilité et comment définir des types COM manuellement.</span><span class="sxs-lookup"><span data-stu-id="425e5-121">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="425e5-122">[Interopérabilité COM avancée](https://msdn.microsoft.com/en-us/library/bd9cdfyx(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="425e5-122">[Advanced COM Interoperability](https://msdn.microsoft.com/en-us/library/bd9cdfyx(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="425e5-123">Fournit des liens vers des informations sur l'incorporation de composants COM dans une application .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="425e5-123">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="425e5-124">[Récapitulatif de la conversion d’un assembly en bibliothèque de types](https://msdn.microsoft.com/en-us/library/xk1120c3(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="425e5-124">[Assembly to Type Library Conversion Summary](https://msdn.microsoft.com/en-us/library/xk1120c3(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="425e5-125">Décrit le processus d'exportation et de conversion d'un assembly en une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="425e5-125">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="425e5-126">[Récapitulatif de la conversion d’une bibliothèque de types en assembly](https://msdn.microsoft.com/en-us/library/k83zzh38(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="425e5-126">[Type Library to Assembly Conversion Summary](https://msdn.microsoft.com/en-us/library/k83zzh38(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="425e5-127">Décrit le processus d'importation et de conversion d'une bibliothèque de types en un assembly.</span><span class="sxs-lookup"><span data-stu-id="425e5-127">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="425e5-128">[Interopérabilité à l’aide de types génériques](https://msdn.microsoft.com/en-us/library/ms229590(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="425e5-128">[Interoperating Using Generic Types](https://msdn.microsoft.com/en-us/library/ms229590(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="425e5-129">Décrit les actions prises en charge lors de l'utilisation de types génériques pour l'interopérabilité COM.</span><span class="sxs-lookup"><span data-stu-id="425e5-129">Describes which actions are supported when using generic types for COM interoperability.</span></span>
