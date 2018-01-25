---
title: -keycontainer (Options du compilateur C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 944a9b4dbbed76f388642d67be9518343f750de5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="3544b-102">-keycontainer (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="3544b-102">-keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="3544b-103">Spécifie le nom du conteneur de la clé de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="3544b-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3544b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3544b-104">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="3544b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3544b-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="3544b-106">Nom du conteneur de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="3544b-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3544b-107">Notes</span><span class="sxs-lookup"><span data-stu-id="3544b-107">Remarks</span></span>  
 <span data-ttu-id="3544b-108">Quand l’option **-keycontainer** est utilisée, le compilateur crée un composant partageable en insérant une clé publique provenant du conteneur spécifié dans le manifeste d’assembly et en signant l’assembly final avec la clé privée.</span><span class="sxs-lookup"><span data-stu-id="3544b-108">When the **-keycontainer** option is used, the compiler creates a sharable component by inserting a public key from the specified container into the assembly manifest and signing the final assembly with the private key.</span></span> <span data-ttu-id="3544b-109">Pour générer un fichier de clé, tapez sn -k `file` sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="3544b-109">To generate a key file, type sn -k `file` at the command line.</span></span> <span data-ttu-id="3544b-110">sn -i installe la paire de clés dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="3544b-110">sn -i installs the key pair into a container.</span></span>  
  
 <span data-ttu-id="3544b-111">Si vous compilez avec [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), le nom du fichier de clé est conservé dans le module et incorporé dans l’assembly quand vous compilez ce module dans un assembly avec [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="3544b-111">If you compile with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="3544b-112">Vous pouvez également spécifier cette option comme attribut personnalisé (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) dans le code source de n'importe quel module MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="3544b-112">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="3544b-113">Vous pouvez également passer vos informations de chiffrement au compilateur avec [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="3544b-113">You can also pass your encryption information to the compiler with [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span></span> <span data-ttu-id="3544b-114">Utilisez [-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) si vous voulez ajouter la clé publique au manifeste d’assembly, mais que vous voulez différer la signature de l’assembly tant qu’il n’a pas été testé.</span><span class="sxs-lookup"><span data-stu-id="3544b-114">Use [-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="3544b-115">Pour plus d’informations, consultez [Création et utilisation d’assemblys avec nom fort](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) et [Différer la signature d’un assembly](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="3544b-115">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3544b-116">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3544b-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="3544b-117">Cette option de compilateur n’est pas disponible dans l'environnement de développement Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3544b-117">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="3544b-118">Vous pouvez accéder par programmation à cette option de compilateur avec <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span><span class="sxs-lookup"><span data-stu-id="3544b-118">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3544b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3544b-119">See Also</span></span>  
 [<span data-ttu-id="3544b-120">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="3544b-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="3544b-121">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="3544b-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
