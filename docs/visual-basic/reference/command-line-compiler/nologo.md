---
title: /nologo (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c2c7e7a111a3763d7463f67c2d984955da33bbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="nologo-visual-basic"></a><span data-ttu-id="febca-102">/nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="febca-102">/nologo (Visual Basic)</span></span>
<span data-ttu-id="febca-103">Supprime l’affichage de la bannière de copyright et de messages d’information pendant la compilation.</span><span class="sxs-lookup"><span data-stu-id="febca-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="febca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="febca-104">Syntax</span></span>  
  
```  
/nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="febca-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="febca-105">Remarks</span></span>  
 <span data-ttu-id="febca-106">Si vous spécifiez `/nologo`, le compilateur n’affiche pas d’une bannière de copyright.</span><span class="sxs-lookup"><span data-stu-id="febca-106">If you specify `/nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="febca-107">Par défaut, l'option `/nologo` n'est pas activée.</span><span class="sxs-lookup"><span data-stu-id="febca-107">By default, `/nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="febca-108">Le `/nologo` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="febca-108">The `/nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="febca-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="febca-109">Example</span></span>  
 <span data-ttu-id="febca-110">Le code suivant compile `T2.vb` et n’affiche pas d’une bannière de copyright.</span><span class="sxs-lookup"><span data-stu-id="febca-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```  
vbc /nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="febca-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="febca-111">See Also</span></span>  
 [<span data-ttu-id="febca-112">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="febca-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="febca-113">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="febca-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
