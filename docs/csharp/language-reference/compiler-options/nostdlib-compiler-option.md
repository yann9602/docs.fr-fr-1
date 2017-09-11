---
title: -nostdlib (Options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /nostdlib
dev_langs:
- CSharp
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1d500e2e55ab3117aa674e11d6cdd25703035879
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="nostdlib-c-compiler-options"></a><span data-ttu-id="3b6f1-102">/nostdlib (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="3b6f1-102">/nostdlib (C# Compiler Options)</span></span>
<span data-ttu-id="3b6f1-103">**/nostdlib** empêche l’importation du fichier mscorlib.dll, qui définit l’espace de noms System tout entier.</span><span class="sxs-lookup"><span data-stu-id="3b6f1-103">**/nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b6f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b6f1-104">Syntax</span></span>  
  
```console  
/nostdlib[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="3b6f1-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="3b6f1-105">Remarks</span></span>  
 <span data-ttu-id="3b6f1-106">Utilisez cette option si vous souhaitez définir ou créer vos propres objets et espace de noms System.</span><span class="sxs-lookup"><span data-stu-id="3b6f1-106">Use this option if you want to define or create your own System namespace and objects.</span></span>  
  
 <span data-ttu-id="3b6f1-107">Si vous ne spécifiez pas **/nostdlib**, mscorlib.dll est importé dans votre programme (ce qui équivaut à spécifier **/nostdlib-**).</span><span class="sxs-lookup"><span data-stu-id="3b6f1-107">If you do not specify **/nostdlib**, mscorlib.dll will be imported into your program (same as specifying **/nostdlib-**).</span></span> <span data-ttu-id="3b6f1-108">Les options **/nostdlib** et **/nostdlib+**sont équivalentes.</span><span class="sxs-lookup"><span data-stu-id="3b6f1-108">Specifying **/nostdlib** is the same as specifying **/nostdlib+**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3b6f1-109">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b6f1-109">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="3b6f1-110">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="3b6f1-110">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="3b6f1-111">Cliquez sur la page de propriétés **Générer** .</span><span class="sxs-lookup"><span data-stu-id="3b6f1-111">Click the **Build** properties page.</span></span>  
  
3.  <span data-ttu-id="3b6f1-112">Cliquez sur le bouton **Avancées** .</span><span class="sxs-lookup"><span data-stu-id="3b6f1-112">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="3b6f1-113">Modifiez la propriété **Ne pas référencer mscorlib.dll** .</span><span class="sxs-lookup"><span data-stu-id="3b6f1-113">Modify the **Do not reference mscorlib.dll** property.</span></span>  
  
 <span data-ttu-id="3b6f1-114">Pour plus d’informations sur la définition de cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="3b6f1-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b6f1-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b6f1-115">See Also</span></span>  
 [<span data-ttu-id="3b6f1-116">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="3b6f1-116">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

