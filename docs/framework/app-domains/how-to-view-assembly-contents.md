---
title: 'Comment : afficher le contenu d''un assembly'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9c12c4811e8b23e86fca3960acdb4da06e38fbe
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="73c20-102">Comment : afficher le contenu d'un assembly</span><span class="sxs-lookup"><span data-stu-id="73c20-102">How to: View Assembly Contents</span></span>
<span data-ttu-id="73c20-103">Vous pouvez utiliser [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pour visualiser les informations de langage MSIL (Microsoft Intermediate Language) dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="73c20-103">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="73c20-104">Si le fichier examiné est un assembly, ces informations peuvent inclure les attributs de l’assembly, ainsi que des références à d’autres modules et assemblys.</span><span class="sxs-lookup"><span data-stu-id="73c20-104">If the file being examined is an assembly, this information can include the assembly's attributes, as well as references to other modules and assemblies.</span></span> <span data-ttu-id="73c20-105">Ces informations peuvent être utiles pour déterminer si un fichier est un assembly ou fait partie d’un assembly, et s’il a des références à d’autres modules ou assemblys.</span><span class="sxs-lookup"><span data-stu-id="73c20-105">This information can be helpful in determining whether a file is an assembly or part of an assembly, and whether the file has references to other modules or assemblies.</span></span>  
  
### <a name="to-display-the-contents-of-an-assembly-using-ildasmexe"></a><span data-ttu-id="73c20-106">Pour afficher le contenu d’un assembly à l’aide d’Ildasm.exe</span><span class="sxs-lookup"><span data-stu-id="73c20-106">To display the contents of an assembly using Ildasm.exe</span></span>  
  
1.  <span data-ttu-id="73c20-107">Tapez **ildasm** \<*nom_assembly*> à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="73c20-107">Type **ildasm** \<*assembly name*> at the command prompt.</span></span> <span data-ttu-id="73c20-108">Par exemple, la commande suivante désassemble l’assembly `Hello.exe`.</span><span class="sxs-lookup"><span data-stu-id="73c20-108">For example, the following command disassembles the `Hello.exe` assembly.</span></span>  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### <a name="to-view-assembly-manifest-information"></a><span data-ttu-id="73c20-109">Pour afficher les informations de manifeste d’assembly</span><span class="sxs-lookup"><span data-stu-id="73c20-109">To view assembly manifest information</span></span>  
  
1.  <span data-ttu-id="73c20-110">Double-cliquez sur l’icône du manifeste dans la fenêtre du désassembleur MSIL.</span><span class="sxs-lookup"><span data-stu-id="73c20-110">Double-click the MANIFEST icon in the MSIL Disassembler window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73c20-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="73c20-111">Example</span></span>  
 <span data-ttu-id="73c20-112">L’exemple suivant débute avec un programme de base « Hello, World ».</span><span class="sxs-lookup"><span data-stu-id="73c20-112">The following example starts with a basic "Hello, World" program.</span></span> <span data-ttu-id="73c20-113">Après avoir compilé le programme, utilisez Ildasm.exe pour désassembler l’assembly Hello.exe et consulter le manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="73c20-113">After compiling the program, use Ildasm.exe to disassemble the Hello.exe assembly and view the assembly manifest.</span></span>  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 <span data-ttu-id="73c20-114">L’exécution de la commande ildasm.exe sur l’assembly Hello.exe et le double-clic sur l’icône du manifeste dans la fenêtre IL DASM produisent la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="73c20-114">Running the command ildasm.exe on the Hello.exe assembly and double-clicking the MANIFEST icon in the IL DASM window produces the following output:</span></span>  
  
```  
// Metadata version: v4.0.30319  
.assembly extern mscorlib  
{  
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..  
  .ver 4:0:0:0  
}  
.assembly Hello  
{  
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )   
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx  
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.  
  .hash algorithm 0x00008004  
  .ver 0:0:0:0  
}  
.module Hello.exe  
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}  
.imagebase 0x00400000  
.file alignment 0x00000200  
.stackreserve 0x00100000  
.subsystem 0x0003       // WINDOWS_CUI  
.corflags 0x00000001    //  ILONLY  
// Image base: 0x00600000  
```  
  
 <span data-ttu-id="73c20-115">Le tableau suivant décrit chaque directive du manifeste d’assembly de l’assembly Hello.exe utilisé dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="73c20-115">The following table describes each directive in the assembly manifest of the Hello.exe assembly used in the example.</span></span>  
  
|<span data-ttu-id="73c20-116">Directive</span><span class="sxs-lookup"><span data-stu-id="73c20-116">Directive</span></span>|<span data-ttu-id="73c20-117">Description</span><span class="sxs-lookup"><span data-stu-id="73c20-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73c20-118">**.assembly extern \<** *nom_assembly* **>**</span><span class="sxs-lookup"><span data-stu-id="73c20-118">**.assembly extern \<** *assembly name* **>**</span></span>|<span data-ttu-id="73c20-119">Spécifie un autre assembly qui contient des éléments référencés par le module actuel (dans cet exemple, `mscorlib`).</span><span class="sxs-lookup"><span data-stu-id="73c20-119">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|  
|<span data-ttu-id="73c20-120">**.publickeytoken \<** *jeton* **>**</span><span class="sxs-lookup"><span data-stu-id="73c20-120">**.publickeytoken \<** *token* **>**</span></span>|<span data-ttu-id="73c20-121">Spécifie le jeton de la clé réelle de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="73c20-121">Specifies the token of the actual key of the referenced assembly.</span></span>|  
|<span data-ttu-id="73c20-122">**.ver \<** *numéro_version* **>**</span><span class="sxs-lookup"><span data-stu-id="73c20-122">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="73c20-123">Spécifie le numéro de version de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="73c20-123">Specifies the version number of the referenced assembly.</span></span>|  
|<span data-ttu-id="73c20-124">**.assembly \<** *nom_assembly* **>**</span><span class="sxs-lookup"><span data-stu-id="73c20-124">**.assembly \<** *assembly name* **>**</span></span>|<span data-ttu-id="73c20-125">Spécifie le nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="73c20-125">Specifies the assembly name.</span></span>|  
|<span data-ttu-id="73c20-126">**.hash algorithm \<** *valeur_int32* **>**</span><span class="sxs-lookup"><span data-stu-id="73c20-126">**.hash algorithm \<** *int32 value* **>**</span></span>|<span data-ttu-id="73c20-127">Spécifie l’algorithme de hachage utilisé.</span><span class="sxs-lookup"><span data-stu-id="73c20-127">Specifies the hash algorithm used.</span></span>|  
|<span data-ttu-id="73c20-128">**.ver \<** *numéro_version* **>**</span><span class="sxs-lookup"><span data-stu-id="73c20-128">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="73c20-129">Spécifie le numéro de version de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="73c20-129">Specifies the version number of the assembly.</span></span>|  
|<span data-ttu-id="73c20-130">**.module \<** *nom_fichier* **>**</span><span class="sxs-lookup"><span data-stu-id="73c20-130">**.module \<** *file name* **>**</span></span>|<span data-ttu-id="73c20-131">Spécifie le nom des modules qui composent l’assembly.</span><span class="sxs-lookup"><span data-stu-id="73c20-131">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="73c20-132">Dans cet exemple, l’assembly se compose d’un seul fichier.</span><span class="sxs-lookup"><span data-stu-id="73c20-132">In this example, the assembly consists of only one file.</span></span>|  
|<span data-ttu-id="73c20-133">**.subsystem \<** *valeur* **>**</span><span class="sxs-lookup"><span data-stu-id="73c20-133">**.subsystem \<** *value* **>**</span></span>|<span data-ttu-id="73c20-134">Spécifie l’environnement d’application nécessaire pour le programme.</span><span class="sxs-lookup"><span data-stu-id="73c20-134">Specifies the application environment required for the program.</span></span> <span data-ttu-id="73c20-135">Dans cet exemple, la valeur 3 indique que cet exécutable est exécuté à partir d’une console.</span><span class="sxs-lookup"><span data-stu-id="73c20-135">In this example, the value 3 indicates that this executable is run from a console.</span></span>|  
|<span data-ttu-id="73c20-136">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="73c20-136">**.corflags**</span></span>|<span data-ttu-id="73c20-137">Actuellement un champ réservé dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="73c20-137">Currently a reserved field in the metadata.</span></span>|  
  
 <span data-ttu-id="73c20-138">Un manifeste d’assembly peut contenir plusieurs directives différentes, en fonction du contenu de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="73c20-138">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="73c20-139">Pour obtenir une liste complète des directives dans le manifeste d’assembly, consultez la documentation ECMA, en particulier « Partition II: Metadata Definition and Semantics » et « Partition III: CIL Instruction Set ».</span><span class="sxs-lookup"><span data-stu-id="73c20-139">For an extensive list of the directives in the assembly manifest, see the ECMA documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="73c20-140">La documentation est disponible en ligne. Consultez [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) sur MSDN et [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) sur le site web d’Ecma International.</span><span class="sxs-lookup"><span data-stu-id="73c20-140">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73c20-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73c20-141">See Also</span></span>  
 [<span data-ttu-id="73c20-142">Domaines d'application et assemblys</span><span class="sxs-lookup"><span data-stu-id="73c20-142">Application Domains and Assemblies</span></span>](http://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)  
 [<span data-ttu-id="73c20-143">Rubriques Guide pratique relatives aux domaines d'application et aux assemblys</span><span class="sxs-lookup"><span data-stu-id="73c20-143">Application Domains and Assemblies How-to Topics</span></span>](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 [<span data-ttu-id="73c20-144">Ildasm.exe (désassembleur IL)</span><span class="sxs-lookup"><span data-stu-id="73c20-144">Ildasm.exe (IL Disassembler)</span></span>](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
