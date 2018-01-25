---
title: -target:winexe (Options du compilateur C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b13af4e665a2bf5a75472bc8f4a501e90c59281a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="e821c-102">-target:winexe (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="e821c-102">-target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="e821c-103">L’option **-target:winexe** indique au compilateur de créer un programme Windows exécutable (EXE).</span><span class="sxs-lookup"><span data-stu-id="e821c-103">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e821c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e821c-104">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="e821c-105">Notes</span><span class="sxs-lookup"><span data-stu-id="e821c-105">Remarks</span></span>  
 <span data-ttu-id="e821c-106">Le fichier exécutable est créé avec l’extension .exe.</span><span class="sxs-lookup"><span data-stu-id="e821c-106">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="e821c-107">Un programme Windows est un programme qui fournit une interface utilisateur à partir de la bibliothèque .NET Framework ou avec les API Win32.</span><span class="sxs-lookup"><span data-stu-id="e821c-107">A Windows program is one that provides a user interface from either the .NET Framework library or with the Win32 APIs.</span></span>  
  
 <span data-ttu-id="e821c-108">Utilisez [-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) pour créer une application console.</span><span class="sxs-lookup"><span data-stu-id="e821c-108">Use [-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="e821c-109">À moins que l’option [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) spécifie autre chose, le fichier de sortie prend le nom du fichier d’entrée qui contient la méthode [Main](../../../csharp/programming-guide/main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="e821c-109">Unless otherwise specified with the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="e821c-110">Quand ils sont spécifiés dans la ligne de commande, tous les fichiers jusqu’à l’option **-out** ou [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) suivante sont utilisés pour créer le programme Windows.</span><span class="sxs-lookup"><span data-stu-id="e821c-110">When specified at the command line, all files until the next **-out** or [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="e821c-111">Une seule et unique méthode **Main** est requise dans les fichiers de code source qui sont compilés dans un fichier .exe.</span><span class="sxs-lookup"><span data-stu-id="e821c-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="e821c-112">L’option [-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) vous permet de spécifier la classe contenant la méthode **Main**, au cas où votre code possède plusieurs classes avec une méthode **Main**.</span><span class="sxs-lookup"><span data-stu-id="e821c-112">The [-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="e821c-113">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e821c-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="e821c-114">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="e821c-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="e821c-115">Cliquez sur la page de propriétés **Application**.</span><span class="sxs-lookup"><span data-stu-id="e821c-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="e821c-116">Modifiez la propriété **Type de sortie**.</span><span class="sxs-lookup"><span data-stu-id="e821c-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="e821c-117">Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="e821c-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e821c-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="e821c-118">Example</span></span>  
 <span data-ttu-id="e821c-119">Compilez `in.cs` en un programme Windows :</span><span class="sxs-lookup"><span data-stu-id="e821c-119">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="e821c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e821c-120">See Also</span></span>  
 [<span data-ttu-id="e821c-121">-target (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="e821c-121">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="e821c-122">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="e821c-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
