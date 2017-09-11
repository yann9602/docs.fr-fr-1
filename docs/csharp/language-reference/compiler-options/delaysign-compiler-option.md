---
title: -delaysign (Options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /delaysign
dev_langs:
- CSharp
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
caps.latest.revision: 16
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
ms.openlocfilehash: ce4c9fbb14081764985f3b02988dff9ee272c451
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="delaysign-c-compiler-options"></a><span data-ttu-id="a27c3-102">/delaysign (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="a27c3-102">/delaysign (C# Compiler Options)</span></span>
<span data-ttu-id="a27c3-103">Cette option fait en sorte que le compilateur réserve de l’espace dans le fichier de sortie afin qu’une signature numérique puisse être ajoutée ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="a27c3-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a27c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a27c3-104">Syntax</span></span>  
  
```console  
/delaysign[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a27c3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a27c3-105">Arguments</span></span>  
 <span data-ttu-id="a27c3-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="a27c3-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="a27c3-107">Utilisez **/delaysign-** si vous souhaitez obtenir un assembly complètement signé.</span><span class="sxs-lookup"><span data-stu-id="a27c3-107">Use **/delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="a27c3-108">Utilisez **/delaysign+** si vous souhaitez uniquement placer la clé publique dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a27c3-108">Use **/delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="a27c3-109">**/delaysign-** est l’option par défaut.</span><span class="sxs-lookup"><span data-stu-id="a27c3-109">The default is **/delaysign-**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a27c3-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="a27c3-110">Remarks</span></span>  
 <span data-ttu-id="a27c3-111">L’option **/delaysign** est sans effet sauf si elle est utilisée avec [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) ou [/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="a27c3-111">The **/delaysign** option has no effect unless used with [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) or [/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span></span>  
  
 <span data-ttu-id="a27c3-112">Quand vous demandez un assembly totalement signé, le compilateur hache le fichier qui contient le manifeste (métadonnées de l’assembly) et signe ce hachage avec la clé privée.</span><span class="sxs-lookup"><span data-stu-id="a27c3-112">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="a27c3-113">La signature numérique obtenue est stockée dans le fichier qui contient le manifeste.</span><span class="sxs-lookup"><span data-stu-id="a27c3-113">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="a27c3-114">Pour un assembly avec signature différée, le compilateur ne calcule pas, ni ne stocke la signature, mais réserve de l'espace dans le fichier pour que la signature puisse être ajoutée par la suite.</span><span class="sxs-lookup"><span data-stu-id="a27c3-114">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="a27c3-115">Par exemple, l’utilisation de **/delaysign+** permet à un testeur de placer l’assembly dans le cache global.</span><span class="sxs-lookup"><span data-stu-id="a27c3-115">For example, using **/delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="a27c3-116">Après un test, vous pouvez signer complètement l’assembly en plaçant la clé privée dans l’assembly à l’aide de l’utilitaire [Assembly Linker](https://msdn.microsoft.com/library/c405shex).</span><span class="sxs-lookup"><span data-stu-id="a27c3-116">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](https://msdn.microsoft.com/library/c405shex) utility.</span></span>  
  
 <span data-ttu-id="a27c3-117">Pour plus d’informations, consultez [Création et utilisation d’assemblys avec nom fort](https://msdn.microsoft.com/library/xwb8f617) et [Différer la signature d’un assembly](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="a27c3-117">For more information, see [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a27c3-118">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a27c3-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="a27c3-119">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="a27c3-119">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="a27c3-120">Modifiez la propriété **Différer la signature uniquement**.</span><span class="sxs-lookup"><span data-stu-id="a27c3-120">Modify the **Delay sign only** property.</span></span>  
  
 <span data-ttu-id="a27c3-121">Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="a27c3-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a27c3-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a27c3-122">See Also</span></span>  
 <span data-ttu-id="a27c3-123">[Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="a27c3-123">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="a27c3-124">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="a27c3-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

