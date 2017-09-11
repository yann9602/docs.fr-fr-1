---
title: "-target (Options du compilateur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /target
dev_langs:
- CSharp
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 22dc86ce0c0a24681d05e54e5f1ba4f36295659a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="target-c-compiler-options"></a><span data-ttu-id="4c022-102">/target (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="4c022-102">/target (C# Compiler Options)</span></span>
<span data-ttu-id="4c022-103">L’option du compilateur **/target** peut être spécifiée sous quatre formes différentes :</span><span class="sxs-lookup"><span data-stu-id="4c022-103">The **/target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="4c022-104">/target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="4c022-104">/target:appcontainerexe</span></span>](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="4c022-105">Pour créer un fichier .exe pour des applications [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4c022-105">To create an .exe file for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [<span data-ttu-id="4c022-106">/target:exe</span><span class="sxs-lookup"><span data-stu-id="4c022-106">/target:exe</span></span>](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 <span data-ttu-id="4c022-107">Pour créer un fichier .exe.</span><span class="sxs-lookup"><span data-stu-id="4c022-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="4c022-108">/target:library</span><span class="sxs-lookup"><span data-stu-id="4c022-108">/target:library</span></span>](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 <span data-ttu-id="4c022-109">Pour créer une bibliothèque de code.</span><span class="sxs-lookup"><span data-stu-id="4c022-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="4c022-110">/target:module</span><span class="sxs-lookup"><span data-stu-id="4c022-110">/target:module</span></span>](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 <span data-ttu-id="4c022-111">Pour créer un module.</span><span class="sxs-lookup"><span data-stu-id="4c022-111">To create a module.</span></span>  
  
 [<span data-ttu-id="4c022-112">/target:winexe</span><span class="sxs-lookup"><span data-stu-id="4c022-112">/target:winexe</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 <span data-ttu-id="4c022-113">Pour créer un programme Windows.</span><span class="sxs-lookup"><span data-stu-id="4c022-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="4c022-114">/target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="4c022-114">/target:winmdobj</span></span>](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 <span data-ttu-id="4c022-115">Pour créer un fichier .winmdobj intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="4c022-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="4c022-116">Sauf si vous spécifiez **/target:module**, **/target** entraîne le placement d’un manifeste de l’assembly .NET Framework dans un fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="4c022-116">Unless you specify **/target:module**, **/target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="4c022-117">Pour plus d’informations, consultez [Assemblys dans le Common Language Runtime](https://msdn.microsoft.com/library/k3677y81) et [Attributs communs](http://msdn.microsoft.com/library/2f48a7ec-9683-4899-a1d2-a08be8fc558b).</span><span class="sxs-lookup"><span data-stu-id="4c022-117">For more information, see [Assemblies in the Common Language Runtime](https://msdn.microsoft.com/library/k3677y81) and [Common Attributes](http://msdn.microsoft.com/library/2f48a7ec-9683-4899-a1d2-a08be8fc558b).</span></span>  
  
 <span data-ttu-id="4c022-118">Le manifeste de l’assembly est placé dans le premier fichier de sortie .exe dans la compilation ou dans le premier fichier DLL, en l’absence de fichier de sortie .exe.</span><span class="sxs-lookup"><span data-stu-id="4c022-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="4c022-119">Par exemple, dans la ligne de commande suivante, le manifeste est placé dans `1.exe` :</span><span class="sxs-lookup"><span data-stu-id="4c022-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc /out:1.exe t1.cs /out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="4c022-120">Le compilateur crée un seul manifeste d’assembly par compilation.</span><span class="sxs-lookup"><span data-stu-id="4c022-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="4c022-121">Les informations sur tous les fichiers d’une compilation sont placées dans le manifeste de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="4c022-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="4c022-122">Tous les fichiers de sortie sauf ceux créés avec **/target:module** peuvent contenir un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="4c022-122">All output files except those created with **/target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="4c022-123">Lorsque vous générez plusieurs fichiers de sortie sur la ligne de commande, un seul manifeste d’assembly peut être créé et il doit aller dans le premier fichier de sortie spécifié sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="4c022-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="4c022-124">Quel que soit le premier fichier de sortie (**/target:exe**, **/target:winexe**, **/target:library** ou **/target:module**), tous les autres fichiers de sortie générés dans la même compilation doivent être des modules (**/target:module**).</span><span class="sxs-lookup"><span data-stu-id="4c022-124">No matter what the first output file is (**/target:exe**, **/target:winexe**, **/target:library** or **/target:module**), any other output files produced in the same compilation must be modules (**/target:module**).</span></span>  
  
 <span data-ttu-id="4c022-125">Si vous créez un assembly, vous pouvez indiquer que tout ou partie de votre code est conforme CLS avec l’attribut <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4c022-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="4c022-126">Pour plus d’informations sur la définition de cette option de compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="4c022-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c022-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c022-127">See Also</span></span>  
 <span data-ttu-id="4c022-128">[Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="4c022-128">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 <span data-ttu-id="4c022-129">[Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties) </span><span class="sxs-lookup"><span data-stu-id="4c022-129">[Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties) </span></span>  
 [<span data-ttu-id="4c022-130">/subsystemversion (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="4c022-130">/subsystemversion (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)

