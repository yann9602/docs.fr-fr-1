---
title: "Comment : créer manuellement des wrappers"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 19f605203a79f8435d414fb3c2eb7041c9824640
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-wrappers-manually"></a><span data-ttu-id="f4950-102">Comment : créer manuellement des wrappers</span><span class="sxs-lookup"><span data-stu-id="f4950-102">How to: Create Wrappers Manually</span></span>
<span data-ttu-id="f4950-103">Si vous décidez de déclarer des types COM manuellement dans du code source managé, il est recommandé de démarrer avec un fichier IDL (Interface Definition Language) existant ou une bibliothèque de types existante.</span><span class="sxs-lookup"><span data-stu-id="f4950-103">If you decide to declare COM types manually in managed source code, the best place to start is with an existing Interface Definition Language (IDL) file or type library.</span></span> <span data-ttu-id="f4950-104">Quand vous ne disposez pas du fichier IDL ou ne pouvez pas générer un fichier de bibliothèque de types, vous pouvez simuler les types COM en créant des déclarations managées et en exportant l'assembly résultant dans une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="f4950-104">When you do not have the IDL file or cannot generate a type library file, you can simulate the COM types by creating managed declarations and exporting the resulting assembly to a type library.</span></span>  
  
### <a name="to-simulate-com-types-from-managed-source"></a><span data-ttu-id="f4950-105">Pour simuler des types COM à partir d’une source managée</span><span class="sxs-lookup"><span data-stu-id="f4950-105">To simulate COM types from managed source</span></span>  
  
1.  <span data-ttu-id="f4950-106">Déclarez les types dans un langage compatible avec la spécification CLS (Common Language Specification) et compilez le fichier.</span><span class="sxs-lookup"><span data-stu-id="f4950-106">Declare the types in a language that is compliant with the Common Language Specification (CLS) and compile the file.</span></span>  
  
2.  <span data-ttu-id="f4950-107">Exportez l’assembly contenant les types à l’aide de l’outil [Tlbexp.exe (exportateur de bibliothèques de types)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="f4950-107">Export the assembly containing the types with the [Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
3.  <span data-ttu-id="f4950-108">Utilisez la bibliothèque de types COM exportée comme base pour déclarer des types managés orientés COM.</span><span class="sxs-lookup"><span data-stu-id="f4950-108">Use the exported COM type library as a basis for declaring COM-oriented managed types.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a><span data-ttu-id="f4950-109">Pour créer un wrapper RCW (Runtime Callable Wrapper)</span><span class="sxs-lookup"><span data-stu-id="f4950-109">To create a runtime callable wrapper (RCW)</span></span>  
  
1.  <span data-ttu-id="f4950-110">En supposant que vous disposez d’un fichier IDL ou d’un fichier de bibliothèque de types, choisissez les classes et les interfaces que vous souhaitez inclure dans le wrapper RCW personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f4950-110">Assuming that you have an IDL file or type library file, decide which classes and interfaces you want to include in the custom RCW.</span></span> <span data-ttu-id="f4950-111">Vous pouvez exclure tous les types que vous ne souhaitez pas utiliser directement ou indirectement dans votre application.</span><span class="sxs-lookup"><span data-stu-id="f4950-111">You can exclude any types that you do not intend to use directly or indirectly in your application.</span></span>  
  
2.  <span data-ttu-id="f4950-112">Créez un fichier source dans un langage conforme à la spécification CLS et déclarez les types.</span><span class="sxs-lookup"><span data-stu-id="f4950-112">Create a source file in a CLS-compliant language and declare the types.</span></span> <span data-ttu-id="f4950-113">Consultez [Résumé de la conversion d’une bibliothèque de types en assembly](http://msdn.microsoft.com/en-us/bf3f90c5-4770-4ab8-895c-3ba1055cc958) pour obtenir une description complète du processus de conversion à l’importation.</span><span class="sxs-lookup"><span data-stu-id="f4950-113">See [Type Library to Assembly Conversion Summary](http://msdn.microsoft.com/en-us/bf3f90c5-4770-4ab8-895c-3ba1055cc958) for a complete description of the import conversion process.</span></span> <span data-ttu-id="f4950-114">En effet, quand vous créez un wrapper RCW personnalisé, vous effectuez manuellement l’activité de conversion de type fournie par l’outil [Tlbimp.exe (importateur de bibliothèques de types)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="f4950-114">Effectively, when you create a custom RCW, you are manually performing the type conversion activity provided by the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="f4950-115">L’exemple fourni dans la section suivante montre les types dans un fichier IDL ou un fichier de bibliothèque de types, et les types correspondants en code C#.</span><span class="sxs-lookup"><span data-stu-id="f4950-115">The example in the next section shows types in an IDL or type library file and their corresponding types in C# code.</span></span>  
  
3.  <span data-ttu-id="f4950-116">Lorsque les déclarations sont terminées, compilez le fichier comme tout autre code source managé.</span><span class="sxs-lookup"><span data-stu-id="f4950-116">When the declarations are complete, compile the file as you compile any other managed source code.</span></span>  
  
4.  <span data-ttu-id="f4950-117">Quant aux types importés avec Tlbimp.exe, certains nécessitent des informations supplémentaires, que vous pouvez ajouter directement dans le code.</span><span class="sxs-lookup"><span data-stu-id="f4950-117">As with the types imported with Tlbimp.exe, some require additional information, which you can add directly to your code.</span></span> <span data-ttu-id="f4950-118">Pour plus d’informations, consultez [Guide pratique pour modifier des assemblys d’interopérabilité](http://msdn.microsoft.com/en-us/16aacb20-2269-42bf-a812-b6a7df17e277).</span><span class="sxs-lookup"><span data-stu-id="f4950-118">For details, see [How to: Edit Interop Assemblies](http://msdn.microsoft.com/en-us/16aacb20-2269-42bf-a812-b6a7df17e277).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4950-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="f4950-119">Example</span></span>  
 <span data-ttu-id="f4950-120">Le code suivant montre un exemple de l’interface `ISATest` et de la classe `SATest` dans IDL, et les types correspondants dans le code source C#.</span><span class="sxs-lookup"><span data-stu-id="f4950-120">The following code shows an example of the `ISATest` interface and `SATest` class in IDL and the corresponding types in C# source code.</span></span>  
  
 <span data-ttu-id="f4950-121">**Fichier IDL ou de bibliothèque de types**</span><span class="sxs-lookup"><span data-stu-id="f4950-121">**IDL or type library file**</span></span>  
  
```  
 [  
object,  
uuid(40A8C65D-2448-447A-B786-64682CBEF133),  
dual,  
helpstring("ISATest Interface"),  
pointer_default(unique)  
 ]  
interface ISATest : IDispatch  
 {  
[id(1), helpstring("method InSArray")]   
HRESULT InSArray([in] SAFEARRAY(int) *ppsa, [out,retval] int *pSum);  
 };  
 [  
uuid(116CCA1E-7E39-4515-9849-90790DA6431E),  
helpstring("SATest Class")  
 ]  
coclass SATest  
 {  
  [default] interface ISATest;  
 };  
```  
  
 <span data-ttu-id="f4950-122">**Wrapper dans le code source managé**</span><span class="sxs-lookup"><span data-stu-id="f4950-122">**Wrapper in managed source code**</span></span>  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
using System.Runtime.CompilerServices;  
  
[assembly:Guid("E4A992B8-6F5C-442C-96E7-C4778924C753")]  
[assembly:ImportedFromTypeLib("SAServerLib")]  
namespace SAServer  
{  
 [ComImport]  
 [Guid("40A8C65D-2448-447A-B786-64682CBEF133")]  
 [TypeLibType(TypeLibTypeFlags.FLicensed)]  
 public interface ISATest  
 {  
  [DispId(1)]  
  //[MethodImpl(MethodImplOptions.InternalCall,  
  // MethodCodeType=MethodCodeType.Runtime)]  
  int InSArray( [MarshalAs(UnmanagedType.SafeArray,  
      SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }   
 [ComImport]  
 [Guid("116CCA1E-7E39-4515-9849-90790DA6431E")]  
 [ClassInterface(ClassInterfaceType.None)]  
 [TypeLibType(TypeLibTypeFlags.FCanCreate)]  
 public class SATest : ISATest  
 {  
  [DispId(1)]  
  [MethodImpl(MethodImplOptions.InternalCall,   
  MethodCodeType=MethodCodeType.Runtime)]  
  extern int ISATest.InSArray( [MarshalAs(UnmanagedType.SafeArray,   
  SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4950-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4950-123">See Also</span></span>  
 [<span data-ttu-id="f4950-124">Personnalisation des wrappers RCW (Runtime Callable Wrapper)</span><span class="sxs-lookup"><span data-stu-id="f4950-124">Customizing Runtime Callable Wrappers</span></span>](http://msdn.microsoft.com/en-us/4652beaf-77d0-4f37-9687-ca193288c0be)  
 [<span data-ttu-id="f4950-125">Types de données COM</span><span class="sxs-lookup"><span data-stu-id="f4950-125">COM Data Types</span></span>](http://msdn.microsoft.com/en-us/f93ae35d-a416-4218-8700-c8218cc90061)  
 [<span data-ttu-id="f4950-126">Comment : modifier des assemblys d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="f4950-126">How to: Edit Interop Assemblies</span></span>](http://msdn.microsoft.com/en-us/16aacb20-2269-42bf-a812-b6a7df17e277)  
 [<span data-ttu-id="f4950-127">Récapitulatif de la conversion d’une bibliothèque de types en assembly</span><span class="sxs-lookup"><span data-stu-id="f4950-127">Type Library to Assembly Conversion Summary</span></span>](http://msdn.microsoft.com/en-us/bf3f90c5-4770-4ab8-895c-3ba1055cc958)  
 [<span data-ttu-id="f4950-128">Tlbimp.exe (importateur de bibliothèques de types)</span><span class="sxs-lookup"><span data-stu-id="f4950-128">Tlbimp.exe (Type Library Importer)</span></span>](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 [<span data-ttu-id="f4950-129">Tlbexp.exe (exportateur de bibliothèques de types)</span><span class="sxs-lookup"><span data-stu-id="f4950-129">Tlbexp.exe (Type Library Exporter)</span></span>](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)
