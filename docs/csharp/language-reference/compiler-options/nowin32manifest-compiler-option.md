---
title: -nowin32manifest (Options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /nowin32manifest
dev_langs:
- CSharp
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
caps.latest.revision: 15
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
ms.openlocfilehash: 8314fd661ccce968238b480b54847abf7cbece74
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="nowin32manifest-c-compiler-options"></a><span data-ttu-id="107d0-102">/nowin32manifest (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="107d0-102">/nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="107d0-103">Utilisez l’option **/nowin32manifest** pour indiquer au compilateur de ne pas incorporer le manifeste de l’application dans le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="107d0-103">Use the **/nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="107d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="107d0-104">Syntax</span></span>  
  
```console  
/nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="107d0-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="107d0-105">Remarks</span></span>  
 <span data-ttu-id="107d0-106">Quand cette option est utilisée, l’application est soumise à la virtualisation sur Windows Vista, sauf si vous fournissez un manifeste de l’application dans un fichier de ressources Win32 ou au cours d’une étape de génération ultérieure.</span><span class="sxs-lookup"><span data-stu-id="107d0-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="107d0-107">Dans Visual Studio, définissez cette option dans la page de propriétés **Application** en sélectionnant l’option **Créer une application sans fichier manifeste** dans la zone de liste déroulante **Manifeste**.</span><span class="sxs-lookup"><span data-stu-id="107d0-107">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="107d0-108">Pour plus d’informations, consultez [Application, page du Concepteur de projet (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="107d0-108">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="107d0-109">Pour plus d’informations sur la création d’un manifeste, consultez [/win32manifest (options du compilateur C#)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="107d0-109">For more information about manifest creation, see [/win32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="107d0-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="107d0-110">See Also</span></span>  
 <span data-ttu-id="107d0-111">[Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="107d0-111">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="107d0-112">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="107d0-112">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

