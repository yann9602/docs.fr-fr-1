---
title: -linkresource (Options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /linkresource
dev_langs:
- CSharp
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
caps.latest.revision: 17
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
ms.openlocfilehash: 022d6c1a53eab98fc033c902f903e7bc66e6da3f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="linkresource-c-compiler-options"></a><span data-ttu-id="df93a-102">/linkresource (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="df93a-102">/linkresource (C# Compiler Options)</span></span>
<span data-ttu-id="df93a-103">Crée un lien vers une ressource .NET Framework dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="df93a-103">Creates a link to a .NET Framework resource in the output file.</span></span> <span data-ttu-id="df93a-104">Le fichier de ressources n’est pas ajouté au fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="df93a-104">The resource file is not added to the output file.</span></span> <span data-ttu-id="df93a-105">Cette option diffère de l’option [/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) qui incorpore un fichier de ressources dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="df93a-105">This differs from the [/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df93a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df93a-106">Syntax</span></span>  
  
```console  
/linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="df93a-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="df93a-107">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="df93a-108">Fichier de ressources .NET Framework que vous voulez lier à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="df93a-108">The .NET Framework resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="df93a-109">`identifier`(facultatif)</span><span class="sxs-lookup"><span data-stu-id="df93a-109">`identifier` (optional)</span></span>  
 <span data-ttu-id="df93a-110">Nom logique de la ressource. Il s’agit du nom utilisé pour charger la ressource.</span><span class="sxs-lookup"><span data-stu-id="df93a-110">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="df93a-111">La valeur par défaut est le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="df93a-111">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="df93a-112">`accessibility-modifier`(facultatif)</span><span class="sxs-lookup"><span data-stu-id="df93a-112">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="df93a-113">Accessibilité de la ressource : publique ou privée.</span><span class="sxs-lookup"><span data-stu-id="df93a-113">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="df93a-114">La valeur par défaut est « public ».</span><span class="sxs-lookup"><span data-stu-id="df93a-114">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df93a-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="df93a-115">Remarks</span></span>  
 <span data-ttu-id="df93a-116">Par défaut, les ressources liées sont publiques dans l’assembly quand elles sont créées avec le compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="df93a-116">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="df93a-117">Pour rendre les ressources privées, spécifiez le modificateur d’accessibilité `private`.</span><span class="sxs-lookup"><span data-stu-id="df93a-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="df93a-118">Aucun autre modificateur que `public` ou `private` n’est autorisé.</span><span class="sxs-lookup"><span data-stu-id="df93a-118">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="df93a-119">**/linkresource** nécessite une option [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) autre que **/target:module**.</span><span class="sxs-lookup"><span data-stu-id="df93a-119">**/linkresource** requires one of the [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) options other than **/target:module**.</span></span>  
  
 <span data-ttu-id="df93a-120">Si `filename` est un fichier de ressources .NET Framework créé, par exemple, par [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou dans l'environnement de développement, il est accessible à l'aide des membres de l'espace de noms <xref:System.Resources>.</span><span class="sxs-lookup"><span data-stu-id="df93a-120">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="df93a-121">Pour plus d'informations, consultez <xref:System.Resources.ResourceManager?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="df93a-121">For more information, see <xref:System.Resources.ResourceManager?displayProperty=fullName>.</span></span> <span data-ttu-id="df93a-122">Pour toutes les autres ressources, utilisez les méthodes `GetManifestResource`* dans la classe <xref:System.Reflection.Assembly> pour accéder à la ressource au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="df93a-122">For all other resources, use the `GetManifestResource`* methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="df93a-123">Le fichier spécifié dans `filename` peut avoir n’importe quel format.</span><span class="sxs-lookup"><span data-stu-id="df93a-123">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="df93a-124">C’est le cas, par exemple, si vous voulez qu’une DLL native fasse partie de l'assembly pour qu’elle puisse être installée dans le Global Assembly Cache et accessible à partir du code managé dans l'assembly.</span><span class="sxs-lookup"><span data-stu-id="df93a-124">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="df93a-125">Le deuxième des exemples suivants montre comment effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="df93a-125">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="df93a-126">Vous pouvez effectuer la même opération dans Assembly Linker.</span><span class="sxs-lookup"><span data-stu-id="df93a-126">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="df93a-127">Le troisième des exemples suivants montre comment effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="df93a-127">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="df93a-128">Pour plus d’informations, consultez [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) et [Utilisation d’assemblys et du Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="df93a-128">For more information, see [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="df93a-129">**/linkres** est la forme abrégée de **/linkresource**.</span><span class="sxs-lookup"><span data-stu-id="df93a-129">**/linkres** is the short form of **/linkresource**.</span></span>  
  
 <span data-ttu-id="df93a-130">Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.</span><span class="sxs-lookup"><span data-stu-id="df93a-130">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df93a-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="df93a-131">Example</span></span>  
 <span data-ttu-id="df93a-132">Compiler `in.cs` et créer un lien vers le fichier de ressources `rf.resource` :</span><span class="sxs-lookup"><span data-stu-id="df93a-132">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc /linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="df93a-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="df93a-133">Example</span></span>  
 <span data-ttu-id="df93a-134">Compiler `A.cs` dans une DLL, créer un lien vers une DLL native N.dll et placer la sortie dans le Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="df93a-134">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="df93a-135">Dans cet exemple, A.dll et N.dll résident dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="df93a-135">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc /linkresource:N.dll /t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="df93a-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="df93a-136">Example</span></span>  
 <span data-ttu-id="df93a-137">Cet exemple obtient le même résultat, mais en utilisant des options Assembly Linker.</span><span class="sxs-lookup"><span data-stu-id="df93a-137">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc /t:module A.cs  
al /out:A.dll A.netmodule /link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="df93a-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df93a-138">See Also</span></span>  
 <span data-ttu-id="df93a-139">[Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="df93a-139">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 <span data-ttu-id="df93a-140">[Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) </span><span class="sxs-lookup"><span data-stu-id="df93a-140">[Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) </span></span>  
 <span data-ttu-id="df93a-141">[Utilisation d’assemblys et du Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md) </span><span class="sxs-lookup"><span data-stu-id="df93a-141">[Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md) </span></span>  
 [<span data-ttu-id="df93a-142">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="df93a-142">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

