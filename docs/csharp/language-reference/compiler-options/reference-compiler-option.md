---
title: "-reference (Options du compilateur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /reference
helpviewer_keywords:
- /r compiler option [C#]
- reference compiler option [C#]
- r compiler option [C#]
- /reference compiler option [C#]
- -r compiler option [C#]
- metadata import [C#]
- public type information [C#]
- -reference compiler option [C#]
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 60a00b1cd088a051e1a58d245c455b9678a74988
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="-reference-c-compiler-options"></a><span data-ttu-id="12ab1-102">-reference (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="12ab1-102">-reference (C# Compiler Options)</span></span>
<span data-ttu-id="12ab1-103">L’option **-reference** indique au compilateur d’importer des informations de type [public](../../../csharp/language-reference/keywords/public.md) dans le fichier spécifié du projet actuel, ce qui vous permet de référencer les métadonnées des fichiers d’assembly spécifiés.</span><span class="sxs-lookup"><span data-stu-id="12ab1-103">The **-reference** option causes the compiler to import [public](../../../csharp/language-reference/keywords/public.md) type information in the specified file into the current project, thus enabling you to reference metadata from the specified assembly files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12ab1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12ab1-104">Syntax</span></span>  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="12ab1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="12ab1-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="12ab1-106">Nom d'un fichier comportant un manifeste d'assembly.</span><span class="sxs-lookup"><span data-stu-id="12ab1-106">The name of a file that contains an assembly manifest.</span></span> <span data-ttu-id="12ab1-107">Pour importer plusieurs fichiers, incluez une option **-reference** distincte pour chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="12ab1-107">To import more than one file, include a separate **-reference** option for each file.</span></span>  
  
 `alias`  
 <span data-ttu-id="12ab1-108">Un identificateur C# valide représentant un espace de noms racine qui contient tous les espaces de noms dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="12ab1-108">A valid C# identifier that will represent a root namespace that will contain all namespaces in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12ab1-109">Notes</span><span class="sxs-lookup"><span data-stu-id="12ab1-109">Remarks</span></span>  
 <span data-ttu-id="12ab1-110">Pour importer à partir de plusieurs fichiers, incluez une option **-reference** pour chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="12ab1-110">To import from more than one file, include a **-reference** option for each file.</span></span>  
  
 <span data-ttu-id="12ab1-111">Les fichiers que vous importez doivent contenir un manifeste ; le fichier de sortie doit être compilé avec une option [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) autre que [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="12ab1-111">The files you import must contain a manifest; the output file must have been compiled with one of the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) options other than [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="12ab1-112">**-r** est la forme abrégée de **-reference**.</span><span class="sxs-lookup"><span data-stu-id="12ab1-112">**-r** is the short form of **-reference**.</span></span>  
  
 <span data-ttu-id="12ab1-113">Utilisez [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) pour importer les métadonnées d’un fichier de sortie qui ne contient pas de manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="12ab1-113">Use [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) to import metadata from an output file that does not contain an assembly manifest.</span></span>  
  
 <span data-ttu-id="12ab1-114">Si vous référencez un assembly (Assembly A) qui référence un autre assembly (Assembly B), vous devez référencer l’Assembly B si :</span><span class="sxs-lookup"><span data-stu-id="12ab1-114">If you reference an assembly (Assembly A) that references another assembly (Assembly B), you will need to reference Assembly B if:</span></span>  
  
-   <span data-ttu-id="12ab1-115">Un type que vous utilisez de l’Assembly A hérite d’un type ou implémente une interface de l’Assembly B.</span><span class="sxs-lookup"><span data-stu-id="12ab1-115">A type you use from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="12ab1-116">Vous appelez un champ, une propriété, un événement ou une méthode qui a un type de retour ou un type de paramètre de l’Assembly B.</span><span class="sxs-lookup"><span data-stu-id="12ab1-116">You invoke a field, property, event, or method that has a return type or parameter type from Assembly B.</span></span>  
  
 <span data-ttu-id="12ab1-117">Utilisez [-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) pour spécifier le répertoire dans lequel se trouvent une ou plusieurs références d’assembly.</span><span class="sxs-lookup"><span data-stu-id="12ab1-117">Use [-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) to specify the directory in which one or more of your assembly references is located.</span></span> <span data-ttu-id="12ab1-118">La rubrique **-lib** décrit également les répertoires dans lesquels le compilateur recherche les assemblys.</span><span class="sxs-lookup"><span data-stu-id="12ab1-118">The **-lib** topic also discusses the directories in which the compiler searches for assemblies.</span></span>  
  
 <span data-ttu-id="12ab1-119">Pour que le compilateur reconnaisse un type dans un assembly, et non dans un module, il doit être forcé à résoudre le type, ce que vous pouvez faire en définissant une instance du type.</span><span class="sxs-lookup"><span data-stu-id="12ab1-119">In order for the compiler to recognize a type in an assembly, and not in a module, it needs to be forced to resolve the type, which you can do by defining an instance of the type.</span></span> <span data-ttu-id="12ab1-120">Il existe d’autres moyens de résoudre les noms de types dans un assembly pour le compilateur : par exemple, si vous héritez d’un type dans un assembly, le nom du type est ensuite reconnu par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="12ab1-120">There are other ways to resolve type names in an assembly for the compiler: for example, if you inherit from a type in an assembly, the type name will then be recognized by the compiler.</span></span>  
  
 <span data-ttu-id="12ab1-121">Il est parfois nécessaire de référencer deux versions différentes du même composant dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="12ab1-121">Sometimes it is necessary to reference two different versions of the same component from within one assembly.</span></span> <span data-ttu-id="12ab1-122">Pour ce faire, utilisez la sous-option d’alias du commutateur **-reference** pour chaque fichier afin de faire la différence entre les deux fichiers.</span><span class="sxs-lookup"><span data-stu-id="12ab1-122">To do this, use the alias suboption on the **-reference** switch for each file to distinguish between the two files.</span></span> <span data-ttu-id="12ab1-123">Cet alias est utilisé comme qualificateur pour le nom du composant et se traduit par le composant dans l’un des fichiers.</span><span class="sxs-lookup"><span data-stu-id="12ab1-123">This alias will be used as a qualifier for the component name, and will resolve to the component in one of the files.</span></span>  
  
 <span data-ttu-id="12ab1-124">Le fichier de réponse csc (.rsp), qui référence les assemblys .NET Framework couramment utilisés, est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="12ab1-124">The csc response (.rsp) file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="12ab1-125">Utilisez [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) si vous ne voulez pas que le compilateur utilise csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="12ab1-125">Use [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) if you do not want the compiler to use csc.rsp.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12ab1-126">Dans Visual Studio, utilisez la boîte de dialogue **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="12ab1-126">In Visual Studio, use the **Add Reference** dialog box.</span></span> <span data-ttu-id="12ab1-127">Pour plus d’informations, consultez [Guide pratique pour ajouter ou supprimer des références à l’aide du gestionnaire de références](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span><span class="sxs-lookup"><span data-stu-id="12ab1-127">For more information, see [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span></span> <span data-ttu-id="12ab1-128">Pour garantir un comportement équivalent selon que vous ajoutez des références à l’aide de `-reference` ou à l’aide de la boîte de dialogue **Ajouter une référence**, définissez la propriété **Incorporer les types interop** sur **False** pour l’assembly que vous ajoutez.</span><span class="sxs-lookup"><span data-stu-id="12ab1-128">To ensure equivalent behavior between adding references by using `-reference` and adding references by using the **Add Reference** dialog box, set the **Embed Interop Types** property to **False** for the assembly that you're adding.</span></span> <span data-ttu-id="12ab1-129">La valeur par défaut de la propriété est **True**.</span><span class="sxs-lookup"><span data-stu-id="12ab1-129">**True** is the default value for the property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12ab1-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="12ab1-130">Example</span></span>  
 <span data-ttu-id="12ab1-131">Cet exemple montre comment utiliser la fonctionnalité de l’[alias extern](../../../csharp/language-reference/keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="12ab1-131">This example shows how to use the [extern alias](../../../csharp/language-reference/keywords/extern-alias.md) feature.</span></span>  
  
 <span data-ttu-id="12ab1-132">Vous compilez le fichier source et importez les métadonnées à partir de `grid.dll` et `grid20.dll`, qui ont été compilés précédemment.</span><span class="sxs-lookup"><span data-stu-id="12ab1-132">You compile the source file and import metadata from `grid.dll` and `grid20.dll`,which have been compiled previously.</span></span> <span data-ttu-id="12ab1-133">Les deux DLL contiennent des versions séparées du même composant et vous devez utiliser deux **-reference** avec des options d’alias pour compiler le fichier source.</span><span class="sxs-lookup"><span data-stu-id="12ab1-133">The two DLLs contain separate versions of the same component, and you use two **-reference** with alias options to compile the source file.</span></span> <span data-ttu-id="12ab1-134">Les options ressemblent à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="12ab1-134">The options look like this:</span></span>  
  
 <span data-ttu-id="12ab1-135">-reference:GridV1=grid.dll et -reference:GridV2=grid20.dll</span><span class="sxs-lookup"><span data-stu-id="12ab1-135">-reference:GridV1=grid.dll and -reference:GridV2=grid20.dll</span></span>  
  
 <span data-ttu-id="12ab1-136">Cela configure les alias externes « GridV1 » et « GridV2 » que vous utilisez dans votre programme au moyen d’une instruction extern :</span><span class="sxs-lookup"><span data-stu-id="12ab1-136">This sets up the external aliases "GridV1" and "GridV2," which you use in your program by means of an extern statement:</span></span>  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 <span data-ttu-id="12ab1-137">Une fois cette opération effectuée, vous pouvez référencer le contrôle de grille de grid.dll en ajoutant un préfixe au nom du contrôle GridV1, comme suit :</span><span class="sxs-lookup"><span data-stu-id="12ab1-137">Once this is done, you can refer to the grid control from grid.dll by prefixing the control name with GridV1, like this:</span></span>  
  
```csharp  
GridV1::Grid  
```  
  
 <span data-ttu-id="12ab1-138">Par ailleurs, vous pouvez référencer le contrôle de grille de grid20.dll en ajoutant un préfixe au nom du contrôle GridV2, comme suit :</span><span class="sxs-lookup"><span data-stu-id="12ab1-138">In addition, you can refer to the grid control from grid20.dll by prefixing the control name with GridV2 like this:</span></span>  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a><span data-ttu-id="12ab1-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12ab1-139">See Also</span></span>  
 [<span data-ttu-id="12ab1-140">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="12ab1-140">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="12ab1-141">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="12ab1-141">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
