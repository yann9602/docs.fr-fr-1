---
title: "comportement de marshaling par défaut"
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
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e66caf800fd49b4822ee22326b8a5cf712d99bb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="default-marshaling-behavior"></a><span data-ttu-id="30b65-102">comportement de marshaling par défaut</span><span class="sxs-lookup"><span data-stu-id="30b65-102">Default Marshaling Behavior</span></span>
<span data-ttu-id="30b65-103">Le marshaling d’interopérabilité agit sur les règles qui définissent le comportement des données associées aux paramètres de méthode quand elles sont passées de la mémoire managée à la mémoire non managée.</span><span class="sxs-lookup"><span data-stu-id="30b65-103">Interop marshaling operates on rules that dictate how data associated with method parameters behaves as it passes between managed and unmanaged memory.</span></span> <span data-ttu-id="30b65-104">Ces règles intégrées contrôlent les activités de marshaling telles que les transformations de types de données, le fait qu'un appelant puisse modifier les données transmises et renvoyer ces modifications à l'appelant, ainsi que les circonstances dans lesquelles le marshaleur fournit des optimisations de performances.</span><span class="sxs-lookup"><span data-stu-id="30b65-104">These built-in rules control such marshaling activities as data type transformations, whether a callee can change data passed to it and return those changes to the caller, and under which circumstances the marshaler provides performance optimizations.</span></span>  
  
 <span data-ttu-id="30b65-105">Cette section aborde les caractéristiques de comportement par défaut du service de marshaling d'interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="30b65-105">This section identifies the default behavioral characteristics of the interop marshaling service.</span></span> <span data-ttu-id="30b65-106">Elle présente des informations détaillées sur le marshaling des tableaux, des types booléens, des types char, des délégués, des classes, des objets, des chaînes et des structures.</span><span class="sxs-lookup"><span data-stu-id="30b65-106">It presents detailed information on marshaling arrays, Boolean types, char types, delegates, classes, objects, strings, and structures.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30b65-107">Le marshaling des types génériques n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="30b65-107">Marshaling of generic types is not supported.</span></span> <span data-ttu-id="30b65-108">Pour plus d’informations, consultez [Interopérabilité à l’aide de types génériques](http://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58).</span><span class="sxs-lookup"><span data-stu-id="30b65-108">For more information see, [Interoperating Using Generic Types](http://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58).</span></span>  
  
## <a name="memory-management-with-the-interop-marshaler"></a><span data-ttu-id="30b65-109">Gestion de la mémoire avec le marshaleur d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="30b65-109">Memory management with the interop marshaler</span></span>  
 <span data-ttu-id="30b65-110">Le marshaleur d'interopérabilité tente toujours de libérer de la mémoire allouée par du code non managé.</span><span class="sxs-lookup"><span data-stu-id="30b65-110">The interop marshaler always attempts to free memory allocated by unmanaged code.</span></span> <span data-ttu-id="30b65-111">Ce comportement est conforme aux règles de gestion de mémoire COM, mais pas à celles qui régissent le code C++ natif.</span><span class="sxs-lookup"><span data-stu-id="30b65-111">This behavior complies with COM memory management rules, but differs from the rules that govern native C++.</span></span>  
  
 <span data-ttu-id="30b65-112">Vous pouvez créer une confusion si vous anticipez le comportement du C++ natif (aucune libération de mémoire) lors d'un appel de code non managé qui libère automatiquement de la mémoire pour les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="30b65-112">Confusion can arise if you anticipate native C++ behavior (no memory freeing) when using platform invoke, which automatically frees memory for pointers.</span></span> <span data-ttu-id="30b65-113">Par exemple, l'appel de la méthode non managée suivante à partir d'une DLL C++ ne libère pas automatiquement de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="30b65-113">For example, calling the following unmanaged method from a C++ DLL does not automatically free any memory.</span></span>  
  
### <a name="unmanaged-signature"></a><span data-ttu-id="30b65-114">Signature non managée</span><span class="sxs-lookup"><span data-stu-id="30b65-114">Unmanaged signature</span></span>  
  
```  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 <span data-ttu-id="30b65-115">Toutefois, si vous définissez la méthode comme un prototype d’appel de code non managé, puis remplacez chaque type **BSTR** par un type <xref:System.String> et appelez `MethodOne`, le common language runtime tentera de libérer `b` deux fois.</span><span class="sxs-lookup"><span data-stu-id="30b65-115">However, if you define the method as a platform invoke prototype, replace each **BSTR** type with a <xref:System.String> type, and call `MethodOne`, the common language runtime attempts to free `b` twice.</span></span> <span data-ttu-id="30b65-116">Vous pouvez modifier le comportement de marshaling en utilisant les types <xref:System.IntPtr> plutôt que les types **String**.</span><span class="sxs-lookup"><span data-stu-id="30b65-116">You can change the marshaling behavior by using <xref:System.IntPtr> types rather than **String** types.</span></span>  
  
 <span data-ttu-id="30b65-117">Le runtime utilise toujours la méthode **CoTaskMemFree** pour libérer de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="30b65-117">The runtime always uses the **CoTaskMemFree** method to free memory.</span></span> <span data-ttu-id="30b65-118">Si la mémoire que vous utilisez n’a pas été allouée avec la méthode **CoTaskMemAlloc**, vous devez utiliser un **IntPtr** et libérer la mémoire manuellement à l’aide de la méthode appropriée.</span><span class="sxs-lookup"><span data-stu-id="30b65-118">If the memory you are working with was not allocated with the **CoTaskMemAlloc** method, you must use an **IntPtr** and free the memory manually using the appropriate method.</span></span> <span data-ttu-id="30b65-119">De même, vous pouvez éviter la libération automatique de mémoire dans les cas où celle-ci ne doit jamais être libérée, par exemple quand vous utilisez la fonction **GetCommandLine** depuis Kernel32.dll qui retourne un pointeur à la mémoire du noyau.</span><span class="sxs-lookup"><span data-stu-id="30b65-119">Similarly, you can avoid automatic memory freeing in situations where memory should never be freed, such as when using the **GetCommandLine** function from Kernel32.dll, which returns a pointer to kernel memory.</span></span> <span data-ttu-id="30b65-120">Pour plus d’informations sur la libération manuelle de mémoire, consultez [Mémoires tampons, exemple](http://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5).</span><span class="sxs-lookup"><span data-stu-id="30b65-120">For details on manually freeing memory, see the [Buffers Sample](http://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5).</span></span>  
  
## <a name="default-marshaling-for-classes"></a><span data-ttu-id="30b65-121">Marshaling par défaut pour les classes</span><span class="sxs-lookup"><span data-stu-id="30b65-121">Default marshaling for classes</span></span>  
 <span data-ttu-id="30b65-122">Les classes ne peuvent être marshalées que par COM Interop et sont toujours marshalées en tant qu'interfaces.</span><span class="sxs-lookup"><span data-stu-id="30b65-122">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="30b65-123">Dans certains cas, l’interface utilisée pour marshaler la classe est appelée interface de classe.</span><span class="sxs-lookup"><span data-stu-id="30b65-123">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="30b65-124">Pour plus d’informations sur la substitution de l’interface de classe par une interface de votre choix, consultez [Présentation de l’interface de classe](http://msdn.microsoft.com/library/733c0dd2-12e5-46e6-8de1-39d5b25df024).</span><span class="sxs-lookup"><span data-stu-id="30b65-124">For information about overriding the class interface with an interface of your choice, see [Introducing the Class Interface](http://msdn.microsoft.com/library/733c0dd2-12e5-46e6-8de1-39d5b25df024).</span></span>  
  
### <a name="passing-classes-to-com"></a><span data-ttu-id="30b65-125">Passage de classes à COM</span><span class="sxs-lookup"><span data-stu-id="30b65-125">Passing Classes to COM</span></span>  
 <span data-ttu-id="30b65-126">Quand une classe managée est passée à COM, le marshaleur d'interopérabilité encapsule automatiquement la classe avec un proxy COM et passe l'interface de classe produite par le proxy à l'appel de méthode COM.</span><span class="sxs-lookup"><span data-stu-id="30b65-126">When a managed class is passed to COM, the interop marshaler automatically wraps the class with a COM proxy and passes the class interface produced by the proxy to the COM method call.</span></span> <span data-ttu-id="30b65-127">Le proxy délègue ensuite tous les appels sur l'interface de classe vers l'objet managé.</span><span class="sxs-lookup"><span data-stu-id="30b65-127">The proxy then delegates all calls on the class interface back to the managed object.</span></span> <span data-ttu-id="30b65-128">Le proxy expose également d'autres interfaces qui ne sont pas explicitement implémentées par la classe.</span><span class="sxs-lookup"><span data-stu-id="30b65-128">The proxy also exposes other interfaces that are not explicitly implemented by the class.</span></span> <span data-ttu-id="30b65-129">Le proxy implémente automatiquement les interfaces telles que **IUnknown** et **IDispatch** pour le compte de la classe.</span><span class="sxs-lookup"><span data-stu-id="30b65-129">The proxy automatically implements interfaces such as **IUnknown** and **IDispatch** on behalf of the class.</span></span>  
  
### <a name="passing-classes-to-net-code"></a><span data-ttu-id="30b65-130">Passage de classes à du code .NET</span><span class="sxs-lookup"><span data-stu-id="30b65-130">Passing Classes to .NET Code</span></span>  
 <span data-ttu-id="30b65-131">Les coclasses ne sont généralement pas utilisées en tant qu'arguments de méthode dans COM.</span><span class="sxs-lookup"><span data-stu-id="30b65-131">Coclasses are not typically used as method arguments in COM.</span></span> <span data-ttu-id="30b65-132">Au lieu d'une coclasse, c'est une interface par défaut qui est généralement passée.</span><span class="sxs-lookup"><span data-stu-id="30b65-132">Instead, a default interface is usually passed in place of the coclass.</span></span>  
  
 <span data-ttu-id="30b65-133">Quand une interface est passée dans du code managé, le marshaleur d'interopérabilité est responsable de l'encapsulation de l'interface avec le wrapper approprié et du passage du wrapper à la méthode managée.</span><span class="sxs-lookup"><span data-stu-id="30b65-133">When an interface is passed into managed code, the interop marshaler is responsible for wrapping the interface with the proper wrapper and passing the wrapper to the managed method.</span></span> <span data-ttu-id="30b65-134">Savoir quel wrapper utiliser peut s'avérer difficile.</span><span class="sxs-lookup"><span data-stu-id="30b65-134">Determining which wrapper to use can be difficult.</span></span> <span data-ttu-id="30b65-135">Chaque instance d'un objet COM possède un seul et unique wrapper, quel que soit le nombre d'interfaces qu'implémente l'objet.</span><span class="sxs-lookup"><span data-stu-id="30b65-135">Every instance of a COM object has a single, unique wrapper, no matter how many interfaces the object implements.</span></span> <span data-ttu-id="30b65-136">Par exemple, un objet COM qui implémente cinq interfaces différentes n'a qu'un seul wrapper.</span><span class="sxs-lookup"><span data-stu-id="30b65-136">For example, a single COM object that implements five distinct interfaces has only one wrapper.</span></span> <span data-ttu-id="30b65-137">Le même wrapper expose les cinq interfaces.</span><span class="sxs-lookup"><span data-stu-id="30b65-137">The same wrapper exposes all five interfaces.</span></span> <span data-ttu-id="30b65-138">Si deux instances de l'objet COM sont créées, deux instances du wrapper sont créées.</span><span class="sxs-lookup"><span data-stu-id="30b65-138">If two instances of the COM object are created, then two instances of the wrapper are created.</span></span>  
  
 <span data-ttu-id="30b65-139">Pour que le wrapper conserve le même type durant toute sa durée de vie, le marshaleur d'interopérabilité doit identifier le bon wrapper la première fois qu'une interface exposée par l'objet est passée via le marshaleur.</span><span class="sxs-lookup"><span data-stu-id="30b65-139">For the wrapper to maintain the same type throughout its lifetime, the interop marshaler must identify the correct wrapper the first time an interface exposed by the object is passed through the marshaler.</span></span> <span data-ttu-id="30b65-140">Le marshaleur identifie l'objet en examinant l'une des interfaces implémentées par l'objet.</span><span class="sxs-lookup"><span data-stu-id="30b65-140">The marshaler identifies the object by looking at one of the interfaces the object implements.</span></span>  
  
 <span data-ttu-id="30b65-141">Par exemple, le marshaleur détermine que le wrapper de classe doit être utilisé pour encapsuler l'interface qui a été passée dans le code managé.</span><span class="sxs-lookup"><span data-stu-id="30b65-141">For example, the marshaler determines that the class wrapper should be used to wrap the interface that was passed into managed code.</span></span> <span data-ttu-id="30b65-142">Quand l'interface est initialement passée via le marshaleur, celui-ci vérifie si l'interface provient d'un objet connu.</span><span class="sxs-lookup"><span data-stu-id="30b65-142">When the interface is first passed through the marshaler, the marshaler checks whether the interface is coming from a known object.</span></span> <span data-ttu-id="30b65-143">Cette vérification se produit dans deux situations :</span><span class="sxs-lookup"><span data-stu-id="30b65-143">This check occurs in two situations:</span></span>  
  
-   <span data-ttu-id="30b65-144">Une interface est implémentée par un autre objet managé qui a été passé à COM à un autre endroit.</span><span class="sxs-lookup"><span data-stu-id="30b65-144">An interface is being implemented by another managed object that was passed to COM elsewhere.</span></span> <span data-ttu-id="30b65-145">Le marshaleur peut facilement identifier les interfaces exposées par les objets managés. De plus, il est capable de faire correspondre l'interface avec l'objet managé qui fournit l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="30b65-145">The marshaler can readily identify interfaces exposed by managed objects and is able to match the interface with the managed object that provides the implementation.</span></span> <span data-ttu-id="30b65-146">L'objet managé est ensuite passé à la méthode sans qu'aucun wrapper ne soit nécessaire.</span><span class="sxs-lookup"><span data-stu-id="30b65-146">The managed object is then passed to the method and no wrapper is needed.</span></span>  
  
-   <span data-ttu-id="30b65-147">Un objet qui a déjà été encapsulé implémente l'interface.</span><span class="sxs-lookup"><span data-stu-id="30b65-147">An object that has already been wrapped is implementing the interface.</span></span> <span data-ttu-id="30b65-148">Afin de déterminer si tel est le cas, le marshaleur interroge l’objet au sujet de son interface **IUnknown** et compare l’interface retournée aux interfaces des autres objets déjà enveloppés.</span><span class="sxs-lookup"><span data-stu-id="30b65-148">To determine whether this is the case, the marshaler queries the object for its **IUnknown** interface and compares the returned interface to the interfaces of other objects that are already wrapped.</span></span> <span data-ttu-id="30b65-149">Si l'interface est identique à celle d'un autre wrapper, les objets ont la même identité et le wrapper existant est passé à la méthode.</span><span class="sxs-lookup"><span data-stu-id="30b65-149">If the interface is the same as that of another wrapper, the objects have the same identity and the existing wrapper is passed to the method.</span></span>  
  
 <span data-ttu-id="30b65-150">Si une interface n’est pas d’un objet connu, le marshaleur effectue ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="30b65-150">If an interface is not from a known object, the marshaler does the following:</span></span>  
  
1.  <span data-ttu-id="30b65-151">Le marshaleur interroge l’objet au sujet de l’interface **IProvideClassInfo2**.</span><span class="sxs-lookup"><span data-stu-id="30b65-151">The marshaler queries the object for the **IProvideClassInfo2** interface.</span></span> <span data-ttu-id="30b65-152">Si celle-ci est fournie, le marshaleur utilise le CLSID retourné à partir d’**IProvideClassInfo2.GetGUID** pour identifier la coclasse fournissant l’interface.</span><span class="sxs-lookup"><span data-stu-id="30b65-152">If provided, the marshaler uses the CLSID returned from **IProvideClassInfo2.GetGUID** to identify the coclass providing the interface.</span></span> <span data-ttu-id="30b65-153">Grâce au CLSID, le marshaleur peut localiser le wrapper à partir du Registre si l’assembly a déjà été inscrit.</span><span class="sxs-lookup"><span data-stu-id="30b65-153">With the CLSID, the marshaler can locate the wrapper from the registry if the assembly has previously been registered.</span></span>  
  
2.  <span data-ttu-id="30b65-154">Le marshaleur interroge l’interface au sujet de l’interface **IProvideClassInfo**.</span><span class="sxs-lookup"><span data-stu-id="30b65-154">The marshaler queries the interface for the **IProvideClassInfo** interface.</span></span> <span data-ttu-id="30b65-155">Si celle-ci est fournie, le marshaleur utilise l’**ITypeInfo** retourné à partir d’**IProvideClassInfo.GetClassinfo** pour déterminer le CLSID de la classe exposant l’interface.</span><span class="sxs-lookup"><span data-stu-id="30b65-155">If provided, the marshaler uses the **ITypeInfo** returned from **IProvideClassInfo.GetClassinfo** to determine the CLSID of the class exposing the interface.</span></span> <span data-ttu-id="30b65-156">Le marshaleur peut utiliser le CLSID pour localiser les métadonnées du wrapper.</span><span class="sxs-lookup"><span data-stu-id="30b65-156">The marshaler can use the CLSID to locate the metadata for the wrapper.</span></span>  
  
3.  <span data-ttu-id="30b65-157">Si le marshaleur ne peut toujours pas identifier la classe, il enveloppe l’interface avec une classe wrapper générique appelée **System.__ComObject**.</span><span class="sxs-lookup"><span data-stu-id="30b65-157">If the marshaler still cannot identify the class, it wraps the interface with a generic wrapper class called **System.__ComObject**.</span></span>  
  
## <a name="default-marshaling-for-delegates"></a><span data-ttu-id="30b65-158">Marshaling par défaut pour les délégués</span><span class="sxs-lookup"><span data-stu-id="30b65-158">Default marshaling for delegates</span></span>  
 <span data-ttu-id="30b65-159">Un délégué managé est marshalé comme une interface COM ou comme un pointeur fonction, en fonction du mécanisme d'appel :</span><span class="sxs-lookup"><span data-stu-id="30b65-159">A managed delegate is marshaled as a COM interface or as a function pointer, based on the calling mechanism:</span></span>  
  
-   <span data-ttu-id="30b65-160">Pour un appel de code non managé, un délégué est marshalé en tant que pointeur fonction non managé par défaut.</span><span class="sxs-lookup"><span data-stu-id="30b65-160">For platform invoke, a delegate is marshaled as an unmanaged function pointer by default.</span></span>  
  
-   <span data-ttu-id="30b65-161">Pour COM Interop, un délégué est marshalé comme une interface COM de type **_Delegate** par défaut.</span><span class="sxs-lookup"><span data-stu-id="30b65-161">For COM interop, a delegate is marshaled as a COM interface of type **_Delegate** by default.</span></span> <span data-ttu-id="30b65-162">L’interface **_Delegate** est définie dans la bibliothèque de types Mscorlib.tlb et contient la méthode <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> qui permet d’appeler la méthode que le délégué référence.</span><span class="sxs-lookup"><span data-stu-id="30b65-162">The **_Delegate** interface is defined in the Mscorlib.tlb type library and contains the <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> method, which enables you to call the method that the delegate references.</span></span>  
  
 <span data-ttu-id="30b65-163">Le tableau suivant montre les options de marshaling pour le type de données délégué managé.</span><span class="sxs-lookup"><span data-stu-id="30b65-163">The following table shows the marshaling options for the managed delegate data type.</span></span> <span data-ttu-id="30b65-164">L'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> fournit plusieurs valeurs d'énumération <xref:System.Runtime.InteropServices.UnmanagedType> pour marshaler les délégués.</span><span class="sxs-lookup"><span data-stu-id="30b65-164">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal delegates.</span></span>  
  
|<span data-ttu-id="30b65-165">Type d'énumération</span><span class="sxs-lookup"><span data-stu-id="30b65-165">Enumeration type</span></span>|<span data-ttu-id="30b65-166">Description du format non managé</span><span class="sxs-lookup"><span data-stu-id="30b65-166">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="30b65-167">**UnmanagedType.FunctionPtr**</span><span class="sxs-lookup"><span data-stu-id="30b65-167">**UnmanagedType.FunctionPtr**</span></span>|<span data-ttu-id="30b65-168">Pointeur fonction non managé.</span><span class="sxs-lookup"><span data-stu-id="30b65-168">An unmanaged function pointer.</span></span>|  
|<span data-ttu-id="30b65-169">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="30b65-169">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="30b65-170">Interface de type **_Delegate**, comme défini dans Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="30b65-170">An interface of type **_Delegate**, as defined in Mscorlib.tlb.</span></span>|  
  
 <span data-ttu-id="30b65-171">Examinez l'exemple de code suivant dans lequel les méthodes de `DelegateTestInterface` sont exportées vers une bibliothèque de types COM.</span><span class="sxs-lookup"><span data-stu-id="30b65-171">Consider the following example code in which the methods of `DelegateTestInterface` are exported to a COM type library.</span></span> <span data-ttu-id="30b65-172">Remarquez que seuls les délégués marqués à l’aide du mot clé **ref** (ou **ByRef**) sont passés en tant que paramètres en entrée/sortie.</span><span class="sxs-lookup"><span data-stu-id="30b65-172">Notice that only delegates marked with the **ref** (or **ByRef**) keyword are passed as In/Out parameters.</span></span>  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public interface DelegateTest {  
void m1(Delegate d);  
void m2([MarshalAs(UnmanagedType.Interface)] Delegate d);     
void m3([MarshalAs(UnmanagedType.Interface)] ref Delegate d);    
void m4([MarshalAs(UnmanagedType.FunctionPtr)] Delegate d);   
void m5([MarshalAs(UnmanagedType.FunctionPtr)] ref Delegate d);     
}  
```  
  
### <a name="type-library-representation"></a><span data-ttu-id="30b65-173">Représentation d'une bibliothèque de types</span><span class="sxs-lookup"><span data-stu-id="30b65-173">Type library representation</span></span>  
  
```  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 <span data-ttu-id="30b65-174">Un pointeur fonction peut être déréférencé, comme n'importe quel autre pointeur fonction non managé.</span><span class="sxs-lookup"><span data-stu-id="30b65-174">A function pointer can be dereferenced, just as any other unmanaged function pointer can be dereferenced.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30b65-175">Une référence au pointeur fonction d'un délégué managé compris dans du code non managé n'empêche pas le common language runtime d'effectuer le garbage collection sur l'objet managé.</span><span class="sxs-lookup"><span data-stu-id="30b65-175">A reference to the function pointer to a managed delegate held by unmanaged code does not prevent the common language runtime from performing garbage collection on the managed object.</span></span>  
  
 <span data-ttu-id="30b65-176">Par exemple, le code suivant est incorrect, car la référence à l'objet `cb` passé à la méthode `SetChangeHandler` ne permet pas à `cb` de rester actif au-delà de la durée de vie de la méthode `Test`.</span><span class="sxs-lookup"><span data-stu-id="30b65-176">For example, the following code is incorrect because the reference to the `cb` object, passed to the `SetChangeHandler` method, does not keep `cb` alive beyond the life of the `Test` method.</span></span> <span data-ttu-id="30b65-177">Une fois l'objet `cb` collecté, le pointeur fonction passé à `SetChangeHandler` n'est plus valide.</span><span class="sxs-lookup"><span data-stu-id="30b65-177">Once the `cb` object is garbage collected, the function pointer passed to `SetChangeHandler` is no longer valid.</span></span>  
  
```csharp  
public class ExternalAPI {  
   [DllImport("External.dll")]  
   public static extern void SetChangeHandler(  
      [MarshalAs(UnmanagedType.FunctionPtr)]ChangeDelegate d);  
}  
public delegate bool ChangeDelegate([MarshalAs(UnmanagedType.LPWStr) string S);  
public class CallBackClass {  
   public bool OnChange(string S){ return true;}  
}  
internal class DelegateTest {  
   public static void Test() {  
      CallBackClass cb = new CallBackClass();  
      // Caution: The following reference on the cb object does not keep the   
      // object from being garbage collected after the Main method   
      // executes.  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));     
   }  
}  
```  
  
 <span data-ttu-id="30b65-178">Pour compenser les garbage collection inattendus, l'appelant doit s'assurer que l'objet `cb` reste actif aussi longtemps que le pointeur fonction non managé est utilisé.</span><span class="sxs-lookup"><span data-stu-id="30b65-178">To compensate for unexpected garbage collection, the caller must ensure that the `cb` object is kept alive as long as the unmanaged function pointer is in use.</span></span> <span data-ttu-id="30b65-179">Si vous le souhaitez, vous pouvez faire en sorte que le code non managé informe le code managé quand le pointeur fonction n'est plus utile, comme dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="30b65-179">Optionally, you can have the unmanaged code notify the managed code when the function pointer is no longer needed, as the following example shows.</span></span>  
  
```csharp  
internal class DelegateTest {  
   CallBackClass cb;  
   // Called before ever using the callback function.  
   public static void SetChangeHandler() {  
      cb = new CallBackClass();  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));  
   }  
   // Called after using the callback function for the last time.  
   public static void RemoveChangeHandler() {  
      // The cb object can be collected now. The unmanaged code is   
      // finished with the callback function.  
      cb = null;  
   }  
}  
```  
  
## <a name="default-marshaling-for-value-types"></a><span data-ttu-id="30b65-180">Marshaling par défaut des types valeur</span><span class="sxs-lookup"><span data-stu-id="30b65-180">Default marshaling for value types</span></span>  
 <span data-ttu-id="30b65-181">La plupart des types valeur, tels que les nombres entiers et à virgule flottante, sont [blittables](../../../docs/framework/interop/blittable-and-non-blittable-types.md) et ne nécessitent pas de marshaling.</span><span class="sxs-lookup"><span data-stu-id="30b65-181">Most value types, such as integers and floating-point numbers, are [blittable](../../../docs/framework/interop/blittable-and-non-blittable-types.md) and do not require marshaling.</span></span> <span data-ttu-id="30b65-182">D’autres types [non blittables](../../../docs/framework/interop/blittable-and-non-blittable-types.md) ont des représentations différentes selon qu’ils sont en mémoire managée et non managée. De plus, ils nécessitent d’être marshalés.</span><span class="sxs-lookup"><span data-stu-id="30b65-182">Other [non-blittable](../../../docs/framework/interop/blittable-and-non-blittable-types.md) types have dissimilar representations in managed and unmanaged memory and do require marshaling.</span></span> <span data-ttu-id="30b65-183">D'autres encore nécessitent une mise en forme explicite au-delà des limites d'interopération.</span><span class="sxs-lookup"><span data-stu-id="30b65-183">Still other types require explicit formatting across the interoperation boundary.</span></span>  
  
 <span data-ttu-id="30b65-184">Cette rubrique fournit des informations sur les types valeur mis en forme :</span><span class="sxs-lookup"><span data-stu-id="30b65-184">This topic provides the follow information on formatted value types:</span></span>  
  
-   [<span data-ttu-id="30b65-185">Types valeur utilisés dans un appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="30b65-185">Value Types Used in Platform Invoke</span></span>](#cpcondefaultmarshalingforvaluetypesanchor2)  
  
-   [<span data-ttu-id="30b65-186">Types valeur utilisés dans COM Interop</span><span class="sxs-lookup"><span data-stu-id="30b65-186">Value Types Used in COM Interop</span></span>](#cpcondefaultmarshalingforvaluetypesanchor3)  
  
 <span data-ttu-id="30b65-187">En plus de décrire les types mis en forme, cette rubrique répertorie les [types valeur système](#cpcondefaultmarshalingforvaluetypesanchor1) qui ont un comportement de marshaling inhabituel.</span><span class="sxs-lookup"><span data-stu-id="30b65-187">In addition to describing formatted types, this topic identifies [System Value Types](#cpcondefaultmarshalingforvaluetypesanchor1) that have unusual marshaling behavior.</span></span>  
  
 <span data-ttu-id="30b65-188">Un type mis en forme est un type complexe qui contient des informations qui contrôlent explicitement la disposition de ses membres dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="30b65-188">A formatted type is a complex type that contains information that explicitly controls the layout of its members in memory.</span></span> <span data-ttu-id="30b65-189">Les informations de disposition des membres sont obtenues à l'aide de l'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute>.</span><span class="sxs-lookup"><span data-stu-id="30b65-189">The member layout information is provided using the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="30b65-190">La disposition peut correspondre à l'une des valeurs d'énumération <xref:System.Runtime.InteropServices.LayoutKind> suivantes :</span><span class="sxs-lookup"><span data-stu-id="30b65-190">The layout can be one of the following <xref:System.Runtime.InteropServices.LayoutKind> enumeration values:</span></span>  
  
-   <span data-ttu-id="30b65-191">**LayoutKind.Automatic**</span><span class="sxs-lookup"><span data-stu-id="30b65-191">**LayoutKind.Automatic**</span></span>  
  
     <span data-ttu-id="30b65-192">Indique que le common language runtime est libre de réorganiser les membres du type pour une plus grande efficacité.</span><span class="sxs-lookup"><span data-stu-id="30b65-192">Indicates that the common language runtime is free to reorder the members of the type for efficiency.</span></span> <span data-ttu-id="30b65-193">Toutefois, quand un type valeur est passé à du code non managé, la disposition des membres est prévisible.</span><span class="sxs-lookup"><span data-stu-id="30b65-193">However, when a value type is passed to unmanaged code, the layout of the members is predictable.</span></span> <span data-ttu-id="30b65-194">Si vous tentez de marshaler une telle structure, une exception sera automatiquement levée.</span><span class="sxs-lookup"><span data-stu-id="30b65-194">An attempt to marshal such a structure automatically causes an exception.</span></span>  
  
-   <span data-ttu-id="30b65-195">**LayoutKind.Sequential**</span><span class="sxs-lookup"><span data-stu-id="30b65-195">**LayoutKind.Sequential**</span></span>  
  
     <span data-ttu-id="30b65-196">Indique que les membres du type doivent être disposés dans la mémoire non managée dans le même ordre que celui de la définition de type managé.</span><span class="sxs-lookup"><span data-stu-id="30b65-196">Indicates that the members of the type are to be laid out in unmanaged memory in the same order in which they appear in the managed type definition.</span></span>  
  
-   <span data-ttu-id="30b65-197">**LayoutKind.Explicit**</span><span class="sxs-lookup"><span data-stu-id="30b65-197">**LayoutKind.Explicit**</span></span>  
  
     <span data-ttu-id="30b65-198">Indique que les membres sont disposés selon le <xref:System.Runtime.InteropServices.FieldOffsetAttribute> fourni avec chaque champ.</span><span class="sxs-lookup"><span data-stu-id="30b65-198">Indicates that the members are laid out according to the <xref:System.Runtime.InteropServices.FieldOffsetAttribute> supplied with each field.</span></span>  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor2"></a>   
### <a name="value-types-used-in-platform-invoke"></a><span data-ttu-id="30b65-199">Types valeur utilisés dans un appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="30b65-199">Value Types Used in Platform Invoke</span></span>  
 <span data-ttu-id="30b65-200">Dans l’exemple suivant, les types `Point` et `Rect` fournissent des informations sur la disposition des membres à l’aide de **StructLayoutAttribute**.</span><span class="sxs-lookup"><span data-stu-id="30b65-200">In the following example the `Point` and `Rect` types provide member layout information using the **StructLayoutAttribute**.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
   Public x As Integer  
   Public y As Integer  
End Structure  
<StructLayout(LayoutKind.Explicit)> Public Structure Rect  
   <FieldOffset(0)> Public left As Integer  
   <FieldOffset(4)> Public top As Integer  
   <FieldOffset(8)> Public right As Integer  
   <FieldOffset(12)> Public bottom As Integer  
End Structure  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
   public int x;  
   public int y;  
}     
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
   [FieldOffset(0)] public int left;  
   [FieldOffset(4)] public int top;  
   [FieldOffset(8)] public int right;  
   [FieldOffset(12)] public int bottom;  
}  
```  
  
 <span data-ttu-id="30b65-201">Quand ils sont marshalés vers du code non managé, ces types mis en forme sont marshalés en tant que structures de style C.</span><span class="sxs-lookup"><span data-stu-id="30b65-201">When marshaled to unmanaged code, these formatted types are marshaled as C-style structures.</span></span> <span data-ttu-id="30b65-202">Ceci facilite les appels d’API non managées qui possèdent des arguments de structure.</span><span class="sxs-lookup"><span data-stu-id="30b65-202">This provides an easy way of calling an unmanaged API that has structure arguments.</span></span> <span data-ttu-id="30b65-203">Par exemple, les structures `POINT` et `RECT` peuvent être passées à la fonction **PtInRect** de l’API Microsoft Win32 de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="30b65-203">For example, the `POINT` and `RECT` structures can be passed to the Microsoft Win32 API **PtInRect** function as follows:</span></span>  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="30b65-204">Vous pouvez passer des structures à l'aide de la définition d'appel de code non managé suivante :</span><span class="sxs-lookup"><span data-stu-id="30b65-204">You can pass structures using the following platform invoke definition:</span></span>  
  
```vb  
Class Win32API      
   Declare Auto Function PtInRect Lib "User32.dll" _  
    (ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
class Win32API {  
   [DllImport("User32.dll")]  
   public static extern Bool PtInRect(ref Rect r, Point p);  
}  
```  
  
 <span data-ttu-id="30b65-205">Le type valeur `Rect` doit être passé par référence, car l'API non managée s'attend à ce qu'un pointeur vers un `RECT` soit passé à la fonction.</span><span class="sxs-lookup"><span data-stu-id="30b65-205">The `Rect` value type must be passed by reference because the unmanaged API is expecting a pointer to a `RECT` to be passed to the function.</span></span> <span data-ttu-id="30b65-206">Le type valeur `Point` est passé par valeur, car l'API non managée s'attend à ce que le `POINT` soit passé à la pile.</span><span class="sxs-lookup"><span data-stu-id="30b65-206">The `Point` value type is passed by value because the unmanaged API expects the `POINT` to be passed on the stack.</span></span> <span data-ttu-id="30b65-207">Cette différence subtile est très importante.</span><span class="sxs-lookup"><span data-stu-id="30b65-207">This subtle difference is very important.</span></span> <span data-ttu-id="30b65-208">Les références sont passées au code non managé comme des pointeurs.</span><span class="sxs-lookup"><span data-stu-id="30b65-208">References are passed to unmanaged code as pointers.</span></span> <span data-ttu-id="30b65-209">Les valeurs sont passées au code non managé sur la pile.</span><span class="sxs-lookup"><span data-stu-id="30b65-209">Values are passed to unmanaged code on the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30b65-210">Quand un type mis en forme est marshalé en tant que structure, seuls les champs du type sont accessibles.</span><span class="sxs-lookup"><span data-stu-id="30b65-210">When a formatted type is marshaled as a structure, only the fields within the type are accessible.</span></span> <span data-ttu-id="30b65-211">Si le type possède des méthodes, des propriétés ou des événements, ceux-ci sont inaccessibles depuis le code non managé.</span><span class="sxs-lookup"><span data-stu-id="30b65-211">If the type has methods, properties, or events, they are inaccessible from unmanaged code.</span></span>  
  
 <span data-ttu-id="30b65-212">Les classes peuvent également être marshalées vers du code non managé en tant que structures de style C, du moment que la disposition des membres est fixe.</span><span class="sxs-lookup"><span data-stu-id="30b65-212">Classes can also be marshaled to unmanaged code as C-style structures, provided they have fixed member layout.</span></span> <span data-ttu-id="30b65-213">Les informations de disposition des membres des classes sont également fournies avec l'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute>.</span><span class="sxs-lookup"><span data-stu-id="30b65-213">The member layout information for a class is also provided with the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="30b65-214">La principale différence entre les types valeur à disposition fixe et les classes à disposition fixe est la manière dont ils sont marshalés vers le code non managé.</span><span class="sxs-lookup"><span data-stu-id="30b65-214">The main difference between value types with fixed layout and classes with fixed layout is the way in which they are marshaled to unmanaged code.</span></span> <span data-ttu-id="30b65-215">Les types valeur sont passés par valeur (dans la pile). Toutes les modifications apportées par l'appelé aux membres du type ne sont donc pas vues par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="30b65-215">Value types are passed by value (on the stack) and consequently any changes made to the members of the type by the callee are not seen by the caller.</span></span> <span data-ttu-id="30b65-216">Les types référence sont passés par référence (une référence au type est passée sur la pile). Toutes les modifications apportées par l'appelé aux membres d'un type blittable sont donc vues par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="30b65-216">Reference types are passed by reference (a reference to the type is passed on the stack); consequently, all changes made to blittable-type members of a type by the callee are seen by the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30b65-217">Si un type référence possède des membres de type non blittable, la conversion est requise deux fois : la première fois quand un argument est passé du côté non managé, la seconde fois lors du retour de l'appel.</span><span class="sxs-lookup"><span data-stu-id="30b65-217">If a reference type has members of non-blittable types, conversion is required twice: the first time when an argument is passed to the unmanaged side and the second time on return from the call.</span></span> <span data-ttu-id="30b65-218">En raison de cette charge mémoire supplémentaire, les paramètres In/Out doivent être explicitement appliqués à un argument si l’appelant veut voir les modifications apportées par l’appelé.</span><span class="sxs-lookup"><span data-stu-id="30b65-218">Due to this added overhead, In/Out parameters must be explicitly applied to an argument if the caller wants to see changes made by the callee.</span></span>  
  
 <span data-ttu-id="30b65-219">Dans l’exemple suivant, la classe `SystemTime` a une disposition séquentielle des membres et peut être passée à la fonction **GetSystemTime** de l’API Win32.</span><span class="sxs-lookup"><span data-stu-id="30b65-219">In the following example, the `SystemTime` class has sequential member layout and can be passed to the Win32 API **GetSystemTime** function.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class SystemTime  
   Public wYear As System.UInt16  
   Public wMonth As System.UInt16  
   Public wDayOfWeek As System.UInt16  
   Public wDay As System.UInt16  
   Public wHour As System.UInt16  
   Public wMinute As System.UInt16  
   Public wSecond As System.UInt16  
   Public wMilliseconds As System.UInt16  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
   public class SystemTime {  
   public ushort wYear;   
   public ushort wMonth;  
   public ushort wDayOfWeek;   
   public ushort wDay;   
   public ushort wHour;   
   public ushort wMinute;   
   public ushort wSecond;   
   public ushort wMilliseconds;   
}  
```  
  
 <span data-ttu-id="30b65-220">La fonction **GetSystemTime** est définie comme suit :</span><span class="sxs-lookup"><span data-stu-id="30b65-220">The **GetSystemTime** function is defined as follows:</span></span>  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="30b65-221">La définition d’appel de code non managé équivalente à **GetSystemTime** se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="30b65-221">The equivalent platform invoke definition for **GetSystemTime** is as follows:</span></span>  
  
```vb  
Public Class Win32  
   Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (ByVal sysTime _  
   As SystemTime)  
End Class  
```  
  
```csharp  
class Win32API {  
   [DllImport("Kernel32.dll", CharSet=CharSet.Auto)]  
   public static extern void GetSystemTime(SystemTime st);  
}  
```  
  
 <span data-ttu-id="30b65-222">Notez que l'argument `SystemTime` n'est pas typé comme un argument de référence, car `SystemTime` est une classe et non un type valeur.</span><span class="sxs-lookup"><span data-stu-id="30b65-222">Notice that the `SystemTime` argument is not typed as a reference argument because `SystemTime` is a class, not a value type.</span></span> <span data-ttu-id="30b65-223">Contrairement aux types valeur, les classes sont toujours passées par référence.</span><span class="sxs-lookup"><span data-stu-id="30b65-223">Unlike value types, classes are always passed by reference.</span></span>  
  
 <span data-ttu-id="30b65-224">L'exemple de code suivant montre une autre classe `Point` qui possède une méthode appelée `SetXY`.</span><span class="sxs-lookup"><span data-stu-id="30b65-224">The following code example shows a different `Point` class that has a method called `SetXY`.</span></span> <span data-ttu-id="30b65-225">Étant donné que le type a une disposition séquentielle, il peut être passé au code non managé et marshalé comme une structure.</span><span class="sxs-lookup"><span data-stu-id="30b65-225">Because the type has sequential layout, it can be passed to unmanaged code and marshaled as a structure.</span></span> <span data-ttu-id="30b65-226">Toutefois, le membre `SetXY` ne peut pas être appelé depuis du code non managé, même si l'objet est passé par référence.</span><span class="sxs-lookup"><span data-stu-id="30b65-226">However, the `SetXY` member is not callable from unmanaged code, even though the object is passed by reference.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class Point  
   Private x, y As Integer  
   Public Sub SetXY(x As Integer, y As Integer)  
      Me.x = x  
      Me.y = y  
   End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class Point {  
   int x, y;  
   public void SetXY(int x, int y){   
      this.x = x;  
      this.y = y;  
   }  
}  
```  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor3"></a>   
### <a name="value-types-used-in-com-interop"></a><span data-ttu-id="30b65-227">Types valeur utilisés dans COM Interop</span><span class="sxs-lookup"><span data-stu-id="30b65-227">Value Types Used in COM Interop</span></span>  
 <span data-ttu-id="30b65-228">Les types mis en forme peuvent également être passés aux appels de méthode d'interopérabilité COM.</span><span class="sxs-lookup"><span data-stu-id="30b65-228">Formatted types can also be passed to COM interop method calls.</span></span> <span data-ttu-id="30b65-229">En effet, quand ils sont exportés vers une bibliothèque de types, les types valeur sont convertis automatiquement en structures.</span><span class="sxs-lookup"><span data-stu-id="30b65-229">In fact, when exported to a type library, value types are automatically converted to structures.</span></span> <span data-ttu-id="30b65-230">Comme dans l'exemple suivant, le type valeur `Point` devient une définition de type (typedef) portant le nom `Point`.</span><span class="sxs-lookup"><span data-stu-id="30b65-230">As the following example shows, the `Point` value type becomes a type definition (typedef) with the name `Point`.</span></span> <span data-ttu-id="30b65-231">Toutes les références au type valeur `Point` situées ailleurs que dans la bibliothèque de types sont remplacées par le typedef `Point`.</span><span class="sxs-lookup"><span data-stu-id="30b65-231">All references to the `Point` value type elsewhere in the type library are replaced with the `Point` typedef.</span></span>  
  
 <span data-ttu-id="30b65-232">**Représentation d’une bibliothèque de types**</span><span class="sxs-lookup"><span data-stu-id="30b65-232">**Type library representation**</span></span>  
  
```  
typedef struct tagPoint {  
   int x;  
   int y;  
} Point;  
interface _Graphics {  
   …  
   HRESULT SetPoint ([in] Point p)  
   HRESULT SetPointRef ([in,out] Point *p)  
   HRESULT GetPoint ([out,retval] Point *p)  
}  
```  
  
 <span data-ttu-id="30b65-233">Les règles utilisées pour marshaler des valeurs et des références aux appels de code non managé sont également utilisées lors du marshaling via les interfaces COM.</span><span class="sxs-lookup"><span data-stu-id="30b65-233">The same rules used to marshal values and references to platform invoke calls are used when marshaling through COM interfaces.</span></span> <span data-ttu-id="30b65-234">Par exemple, quand une instance du type valeur `Point` est passée de .NET Framework à COM, le `Point` est passé par valeur.</span><span class="sxs-lookup"><span data-stu-id="30b65-234">For example, when an instance of the `Point` value type is passed from the .NET Framework to COM, the `Point` is passed by value.</span></span> <span data-ttu-id="30b65-235">Si le type valeur `Point` est passé par référence, un pointeur vers un `Point` est passé sur la pile.</span><span class="sxs-lookup"><span data-stu-id="30b65-235">If the `Point` value type is passed by reference, a pointer to a `Point` is passed on the stack.</span></span> <span data-ttu-id="30b65-236">Le marshaleur d’interopérabilité ne prend pas en charge les niveaux élevés d’indirection (**Point \*\***) dans les deux directions.</span><span class="sxs-lookup"><span data-stu-id="30b65-236">The interop marshaler does not support higher levels of indirection (**Point \*\***) in either direction.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30b65-237">Les structures dont la valeur d’énumération <xref:System.Runtime.InteropServices.LayoutKind> est définie sur **Explicit** ne peuvent pas être utilisées dans COM Interop, car la bibliothèque de types exportée ne peut pas exprimer une disposition explicite.</span><span class="sxs-lookup"><span data-stu-id="30b65-237">Structures having the <xref:System.Runtime.InteropServices.LayoutKind> enumeration value set to **Explicit** cannot be used in COM interop because the exported type library cannot express an explicit layout.</span></span>  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor1"></a>   
### <a name="system-value-types"></a><span data-ttu-id="30b65-238">Types de valeur système</span><span class="sxs-lookup"><span data-stu-id="30b65-238">System Value Types</span></span>  
 <span data-ttu-id="30b65-239">L'espace de noms <xref:System> possède plusieurs types valeur qui représentent la forme boxed de types primitifs de runtime.</span><span class="sxs-lookup"><span data-stu-id="30b65-239">The <xref:System> namespace has several value types that represent the boxed form of the runtime primitive types.</span></span> <span data-ttu-id="30b65-240">Par exemple, la structure de type valeur <xref:System.Int32?displayProperty=nameWithType> représente la forme boxed d’**ELEMENT_TYPE_I4**.</span><span class="sxs-lookup"><span data-stu-id="30b65-240">For example, the value type <xref:System.Int32?displayProperty=nameWithType> structure represents the boxed form of **ELEMENT_TYPE_I4**.</span></span> <span data-ttu-id="30b65-241">Au lieu de marshaler ces types en tant que structures, comme le sont les autres types mis en forme, vous les marshalez de la même façon que les types primitifs boxed.</span><span class="sxs-lookup"><span data-stu-id="30b65-241">Instead of marshaling these types as structures, as other formatted types are, you marshal them in the same way as the primitive types they box.</span></span> <span data-ttu-id="30b65-242">**System.Int32** est donc marshalé en tant qu’**ELEMENT_TYPE_I4** et non en tant que structure contenant un seul membre de type **long**.</span><span class="sxs-lookup"><span data-stu-id="30b65-242">**System.Int32** is therefore marshaled as **ELEMENT_TYPE_I4** instead of as a structure containing a single member of type **long**.</span></span> <span data-ttu-id="30b65-243">Le tableau suivant répertorie les types valeur de l’espace de noms **System** qui sont des représentations boxed de types primitifs.</span><span class="sxs-lookup"><span data-stu-id="30b65-243">The following table contains a list of the value types in the **System** namespace that are boxed representations of primitive types.</span></span>  
  
|<span data-ttu-id="30b65-244">Type de valeur système</span><span class="sxs-lookup"><span data-stu-id="30b65-244">System value type</span></span>|<span data-ttu-id="30b65-245">Type d'élément</span><span class="sxs-lookup"><span data-stu-id="30b65-245">Element type</span></span>|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="30b65-246">**ELEMENT_TYPE_BOOLEAN**</span><span class="sxs-lookup"><span data-stu-id="30b65-246">**ELEMENT_TYPE_BOOLEAN**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="30b65-247">**ELEMENT_TYPE_I1**</span><span class="sxs-lookup"><span data-stu-id="30b65-247">**ELEMENT_TYPE_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="30b65-248">**ELEMENT_TYPE_UI1**</span><span class="sxs-lookup"><span data-stu-id="30b65-248">**ELEMENT_TYPE_UI1**</span></span>|  
|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="30b65-249">**ELEMENT_TYPE_CHAR**</span><span class="sxs-lookup"><span data-stu-id="30b65-249">**ELEMENT_TYPE_CHAR**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="30b65-250">**ELEMENT_TYPE_I2**</span><span class="sxs-lookup"><span data-stu-id="30b65-250">**ELEMENT_TYPE_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="30b65-251">**ELEMENT_TYPE_U2**</span><span class="sxs-lookup"><span data-stu-id="30b65-251">**ELEMENT_TYPE_U2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="30b65-252">**ELEMENT_TYPE_I4**</span><span class="sxs-lookup"><span data-stu-id="30b65-252">**ELEMENT_TYPE_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="30b65-253">**ELEMENT_TYPE_U4**</span><span class="sxs-lookup"><span data-stu-id="30b65-253">**ELEMENT_TYPE_U4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="30b65-254">**ELEMENT_TYPE_I8**</span><span class="sxs-lookup"><span data-stu-id="30b65-254">**ELEMENT_TYPE_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="30b65-255">**ELEMENT_TYPE_U8**</span><span class="sxs-lookup"><span data-stu-id="30b65-255">**ELEMENT_TYPE_U8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="30b65-256">**ELEMENT_TYPE_R4**</span><span class="sxs-lookup"><span data-stu-id="30b65-256">**ELEMENT_TYPE_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="30b65-257">**ELEMENT_TYPE_R8**</span><span class="sxs-lookup"><span data-stu-id="30b65-257">**ELEMENT_TYPE_R8**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="30b65-258">**ELEMENT_TYPE_STRING**</span><span class="sxs-lookup"><span data-stu-id="30b65-258">**ELEMENT_TYPE_STRING**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="30b65-259">**ELEMENT_TYPE_I**</span><span class="sxs-lookup"><span data-stu-id="30b65-259">**ELEMENT_TYPE_I**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="30b65-260">**ELEMENT_TYPE_U**</span><span class="sxs-lookup"><span data-stu-id="30b65-260">**ELEMENT_TYPE_U**</span></span>|  
  
 <span data-ttu-id="30b65-261">Certains autres types valeur de l’espace de noms **System** sont gérés différemment.</span><span class="sxs-lookup"><span data-stu-id="30b65-261">Some other value types in the **System** namespace are handled differently.</span></span> <span data-ttu-id="30b65-262">Étant donné que le code non managé possède déjà des formats bien établis pour ces types, le marshaleur possède des règles spéciales pour les marshaler.</span><span class="sxs-lookup"><span data-stu-id="30b65-262">Because the unmanaged code already has well-established formats for these types, the marshaler has special rules for marshaling them.</span></span> <span data-ttu-id="30b65-263">Le tableau suivant répertorie les types valeur spéciaux de l’espace de noms **System**, ainsi que le type non managé vers lequel ils sont marshalés.</span><span class="sxs-lookup"><span data-stu-id="30b65-263">The following table lists the special value types in the **System** namespace, as well as the unmanaged type they are marshaled to.</span></span>  
  
|<span data-ttu-id="30b65-264">Type de valeur système</span><span class="sxs-lookup"><span data-stu-id="30b65-264">System value type</span></span>|<span data-ttu-id="30b65-265">Type IDL</span><span class="sxs-lookup"><span data-stu-id="30b65-265">IDL type</span></span>|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="30b65-266">**DATE**</span><span class="sxs-lookup"><span data-stu-id="30b65-266">**DATE**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="30b65-267">**DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="30b65-267">**DECIMAL**</span></span>|  
|<xref:System.Guid?displayProperty=nameWithType>|<span data-ttu-id="30b65-268">**GUID**</span><span class="sxs-lookup"><span data-stu-id="30b65-268">**GUID**</span></span>|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|<span data-ttu-id="30b65-269">**OLE_COLOR**</span><span class="sxs-lookup"><span data-stu-id="30b65-269">**OLE_COLOR**</span></span>|  
  
 <span data-ttu-id="30b65-270">Le code suivant montre la définition des types non managés **DATE**, **GUID**, **DECIMAL** et **OLE_COLOR** dans la bibliothèque de types Stdole2.</span><span class="sxs-lookup"><span data-stu-id="30b65-270">The following code shows the definition of the unmanaged types **DATE**, **GUID**, **DECIMAL**, and **OLE_COLOR** in the Stdole2 type library.</span></span>  
  
#### <a name="type-library-representation"></a><span data-ttu-id="30b65-271">Représentation d'une bibliothèque de types</span><span class="sxs-lookup"><span data-stu-id="30b65-271">Type library representation</span></span>  
  
```  
typedef double DATE;  
typedef DWORD OLE_COLOR;  
  
typedef struct tagDEC {  
    USHORT    wReserved;  
    BYTE      scale;  
    BYTE      sign;  
    ULONG     Hi32;  
    ULONGLONG Lo64;  
} DECIMAL;  
  
typedef struct tagGUID {  
    DWORD Data1;  
    WORD  Data2;  
    WORD  Data3;  
    BYTE  Data4[ 8 ];  
} GUID;  
```  
  
 <span data-ttu-id="30b65-272">Le code suivant montre les définitions correspondantes dans l'interface `IValueTypes`.</span><span class="sxs-lookup"><span data-stu-id="30b65-272">The following code shows the corresponding definitions in the managed `IValueTypes` interface.</span></span>  
  
```vb  
Public Interface IValueTypes  
   Sub M1(d As System.DateTime)  
   Sub M2(d As System.Guid)  
   Sub M3(d As System.Decimal)  
   Sub M4(d As System.Drawing.Color)  
End Interface  
```  
  
```csharp  
public interface IValueTypes {  
   void M1(System.DateTime d);  
   void M2(System.Guid d);  
   void M3(System.Decimal d);  
   void M4(System.Drawing.Color d);  
}  
```  
  
#### <a name="type-library-representation"></a><span data-ttu-id="30b65-273">Représentation d'une bibliothèque de types</span><span class="sxs-lookup"><span data-stu-id="30b65-273">Type library representation</span></span>  
  
```  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="30b65-274">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30b65-274">See Also</span></span>  
 [<span data-ttu-id="30b65-275">Types blittable et non blittable</span><span class="sxs-lookup"><span data-stu-id="30b65-275">Blittable and Non-Blittable Types</span></span>](../../../docs/framework/interop/blittable-and-non-blittable-types.md)  
 [<span data-ttu-id="30b65-276">Copie et épinglage</span><span class="sxs-lookup"><span data-stu-id="30b65-276">Copying and Pinning</span></span>](../../../docs/framework/interop/copying-and-pinning.md)  
 [<span data-ttu-id="30b65-277">Marshaling par défaut pour les tableaux</span><span class="sxs-lookup"><span data-stu-id="30b65-277">Default Marshaling for Arrays</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)  
 [<span data-ttu-id="30b65-278">Marshaling par défaut pour les objets</span><span class="sxs-lookup"><span data-stu-id="30b65-278">Default Marshaling for Objects</span></span>](../../../docs/framework/interop/default-marshaling-for-objects.md)  
 [<span data-ttu-id="30b65-279">Marshaling par défaut pour les chaînes</span><span class="sxs-lookup"><span data-stu-id="30b65-279">Default Marshaling for Strings</span></span>](../../../docs/framework/interop/default-marshaling-for-strings.md)
