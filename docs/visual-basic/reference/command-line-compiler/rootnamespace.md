---
title: /RootNamespace | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
dev_langs:
- VB
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9a7a26407e981d3aea58d970d88bf25025e6bba6
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="rootnamespace"></a><span data-ttu-id="1e382-102">/rootnamespace</span><span class="sxs-lookup"><span data-stu-id="1e382-102">/rootnamespace</span></span>
<span data-ttu-id="1e382-103">Spécifie un espace de noms pour toutes les déclarations de type.</span><span class="sxs-lookup"><span data-stu-id="1e382-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e382-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e382-104">Syntax</span></span>  
  
```  
/rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="1e382-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1e382-105">Arguments</span></span>  
  
|<span data-ttu-id="1e382-106">Terme</span><span class="sxs-lookup"><span data-stu-id="1e382-106">Term</span></span>|<span data-ttu-id="1e382-107">Définition</span><span class="sxs-lookup"><span data-stu-id="1e382-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="1e382-108">Le nom de l’espace de noms dans lequel placer toutes les déclarations de type pour le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="1e382-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e382-109">Notes</span><span class="sxs-lookup"><span data-stu-id="1e382-109">Remarks</span></span>  
 <span data-ttu-id="1e382-110">Si vous utilisez le fichier exécutable Visual Studio (Devenv.exe) pour compiler un projet créé dans l’environnement de développement intégré Visual Studio, utilisez `/rootnamespace` pour spécifier la valeur de la <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>propriété.</xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="1e382-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `/rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="1e382-111">Consultez la page [commutateurs de ligne de commande Devenv](https://docs.microsoft.com/visualstudio/ide/reference/devenv-command-line-switches) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="1e382-111">See [Devenv Command Line Switches](https://docs.microsoft.com/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="1e382-112">Utilisez le désassembleur MSIL du common language runtime (je`ldasm.exe`) pour afficher les noms d’espace de noms dans votre fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="1e382-112">Use the common language runtime MSIL Disassembler (I`ldasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="1e382-113">Pour définir/référencer dans Visual Studio environnement de développement intégré</span><span class="sxs-lookup"><span data-stu-id="1e382-113">To set /rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1e382-114">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="1e382-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1e382-115">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="1e382-115">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="1e382-116">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="1e382-116">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="1e382-117">2.  Cliquez sur l’onglet **Application** .</span><span class="sxs-lookup"><span data-stu-id="1e382-117">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="1e382-118">3.  Modifiez la valeur dans la **racine Namespace** boîte.</span><span class="sxs-lookup"><span data-stu-id="1e382-118">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1e382-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="1e382-119">Example</span></span>  
 <span data-ttu-id="1e382-120">Le code suivant compile `In.vb` et englobe toutes les déclarations de type dans l’espace de noms `mynamespace`.</span><span class="sxs-lookup"><span data-stu-id="1e382-120">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e382-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e382-121">See Also</span></span>  
 <span data-ttu-id="1e382-122">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="1e382-122">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="1e382-123"> [Ildasm.exe (désassembleur IL)](https://msdn.microsoft.com/library/f7dy01k1) </span><span class="sxs-lookup"><span data-stu-id="1e382-123"> [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1) </span></span>  
<span data-ttu-id="1e382-124"> [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="1e382-124"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
