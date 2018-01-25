---
title: "-resource (Options du compilateur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c20de499ae0fd5f8869c9b6e78a308fde9787ef9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="afadc-102">-resource (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="afadc-102">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="afadc-103">Incorpore la ressource spécifiée dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="afadc-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afadc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afadc-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="afadc-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="afadc-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="afadc-106">Fichier de ressources .NET Framework que vous voulez incorporer dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="afadc-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="afadc-107">`identifier`(facultatif)</span><span class="sxs-lookup"><span data-stu-id="afadc-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="afadc-108">Nom logique de la ressource. Il s’agit du nom utilisé pour charger la ressource.</span><span class="sxs-lookup"><span data-stu-id="afadc-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="afadc-109">La valeur par défaut est le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="afadc-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="afadc-110">`accessibility-modifier`(facultatif)</span><span class="sxs-lookup"><span data-stu-id="afadc-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="afadc-111">Accessibilité de la ressource : publique ou privée.</span><span class="sxs-lookup"><span data-stu-id="afadc-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="afadc-112">La valeur par défaut est « public ».</span><span class="sxs-lookup"><span data-stu-id="afadc-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afadc-113">Notes</span><span class="sxs-lookup"><span data-stu-id="afadc-113">Remarks</span></span>  
 <span data-ttu-id="afadc-114">Utilisez [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) pour lier une ressource à un assembly sans ajouter le fichier de ressources au fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="afadc-114">Use [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="afadc-115">Par défaut, les ressources sont publiques dans l’assembly quand elles sont créées à l’aide du compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="afadc-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="afadc-116">Pour rendre les ressources privées, spécifiez le modificateur d’accessibilité `private`.</span><span class="sxs-lookup"><span data-stu-id="afadc-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="afadc-117">Aucune accessibilité autre `public` ou `private` n’est autorisée.</span><span class="sxs-lookup"><span data-stu-id="afadc-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="afadc-118">Si `filename` est un fichier de ressources .NET Framework créé, par exemple, par [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) ou dans l'environnement de développement, il est accessible à l'aide des membres de l'espace de noms <xref:System.Resources>.</span><span class="sxs-lookup"><span data-stu-id="afadc-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="afadc-119">Pour plus d'informations, consultez <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="afadc-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="afadc-120">Pour toutes les autres ressources, utilisez les méthodes `GetManifestResource` dans la classe <xref:System.Reflection.Assembly> pour accéder à la ressource au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="afadc-120">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="afadc-121">**-res** est la forme abrégée de **-resource**.</span><span class="sxs-lookup"><span data-stu-id="afadc-121">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="afadc-122">L’ordre des ressources dans le fichier de sortie est déterminé par l’ordre spécifié sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="afadc-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="afadc-123">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="afadc-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="afadc-124">Ajoutez un fichier de ressources à votre projet.</span><span class="sxs-lookup"><span data-stu-id="afadc-124">Add a resource file to your project.</span></span>  
  
2.  <span data-ttu-id="afadc-125">Sélectionnez le fichier que vous souhaitez incorporer dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="afadc-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3.  <span data-ttu-id="afadc-126">Sélectionnez **Action de génération** pour le fichier dans la fenêtre **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="afadc-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="afadc-127">Définissez **Action de génération**  sur **Ressource incorporée**.</span><span class="sxs-lookup"><span data-stu-id="afadc-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="afadc-128">Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span><span class="sxs-lookup"><span data-stu-id="afadc-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afadc-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="afadc-129">Example</span></span>  
 <span data-ttu-id="afadc-130">Compilez `in.cs` et attachez le fichier de ressources `rf.resource` :</span><span class="sxs-lookup"><span data-stu-id="afadc-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="afadc-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afadc-131">See Also</span></span>  
 [<span data-ttu-id="afadc-132">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="afadc-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="afadc-133">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="afadc-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
