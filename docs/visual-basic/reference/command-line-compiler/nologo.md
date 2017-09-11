---
title: /nologo (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners, suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
caps.latest.revision: 16
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
ms.openlocfilehash: fe03c36f46717248269c9aaec13b40569161b0e0
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="nologo-visual-basic"></a><span data-ttu-id="638d5-102">/nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="638d5-102">/nologo (Visual Basic)</span></span>
<span data-ttu-id="638d5-103">Supprime l’affichage de la bannière de copyright et les messages d’information pendant la compilation.</span><span class="sxs-lookup"><span data-stu-id="638d5-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="638d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="638d5-104">Syntax</span></span>  
  
```  
/nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="638d5-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="638d5-105">Remarks</span></span>  
 <span data-ttu-id="638d5-106">Si vous spécifiez `/nologo`, le compilateur n’affiche pas une bannière de copyright.</span><span class="sxs-lookup"><span data-stu-id="638d5-106">If you specify `/nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="638d5-107">Par défaut, l'option `/nologo` n'est pas activée.</span><span class="sxs-lookup"><span data-stu-id="638d5-107">By default, `/nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="638d5-108">La `/nologo` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="638d5-108">The `/nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="638d5-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="638d5-109">Example</span></span>  
 <span data-ttu-id="638d5-110">Le code suivant compile `T2.vb` et n’affiche pas une bannière de copyright.</span><span class="sxs-lookup"><span data-stu-id="638d5-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```  
vbc /nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="638d5-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="638d5-111">See Also</span></span>  
 <span data-ttu-id="638d5-112">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="638d5-112">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="638d5-113"> [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="638d5-113"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
