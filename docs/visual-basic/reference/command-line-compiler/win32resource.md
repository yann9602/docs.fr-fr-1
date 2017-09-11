---
title: /win32resource | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /win32resource
- win32resource
dev_langs:
- VB
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
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
ms.openlocfilehash: dc6bbb5948a5dd505f0fc4d1c8a86650214d657a
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="win32resource"></a><span data-ttu-id="12c94-102">/win32resource</span><span class="sxs-lookup"><span data-stu-id="12c94-102">/win32resource</span></span>
<span data-ttu-id="12c94-103">Insère un fichier de ressources Win32 dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="12c94-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12c94-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12c94-104">Syntax</span></span>  
  
```  
/win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="12c94-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="12c94-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="12c94-106">Le nom du fichier de ressources à ajouter à votre fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="12c94-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="12c94-107">Placez le nom de fichier entre guillemets (« ») s’il contient un espace.</span><span class="sxs-lookup"><span data-stu-id="12c94-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12c94-108">Notes</span><span class="sxs-lookup"><span data-stu-id="12c94-108">Remarks</span></span>  
 <span data-ttu-id="12c94-109">Vous pouvez créer un fichier de ressources Win32 avec le compilateur de ressource Windows (RC) Microsoft.</span><span class="sxs-lookup"><span data-stu-id="12c94-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="12c94-110">Une ressource Win32 peut contenir de version ou des informations d’image bitmap (icône) qui vous aide à identifier votre application dans **Explorateur de fichiers**.</span><span class="sxs-lookup"><span data-stu-id="12c94-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="12c94-111">Si vous ne spécifiez pas `/win32resource`, le compilateur génère des informations de version en fonction de la version d’assembly.</span><span class="sxs-lookup"><span data-stu-id="12c94-111">If you do not specify `/win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="12c94-112">Le `/win32resource` et `/win32icon` options s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="12c94-112">The `/win32resource` and `/win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="12c94-113">Consultez [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) pour référencer un [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] fichier de ressources, ou [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) pour attacher un [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="12c94-113">See [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file, or [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12c94-114">La `/win32resource` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="12c94-114">The `/win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12c94-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="12c94-115">Example</span></span>  
 <span data-ttu-id="12c94-116">Le code suivant compile `In.vb` et attache un fichier de ressources Win32 `Rf.res`:</span><span class="sxs-lookup"><span data-stu-id="12c94-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```  
vbc /win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="12c94-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12c94-117">See Also</span></span>  
 <span data-ttu-id="12c94-118">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="12c94-118">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="12c94-119"> [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="12c94-119"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
