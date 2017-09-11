---
title: /nowin32manifest (Visual Basic) | Documents Microsoft
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
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
caps.latest.revision: 7
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
ms.openlocfilehash: 975711c9ee2e56b3c3c33611dd56eb6dc6082471
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="nowin32manifest-visual-basic"></a><span data-ttu-id="0b1c1-102">/nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b1c1-102">/nowin32manifest (Visual Basic)</span></span>
<span data-ttu-id="0b1c1-103">Indique au compilateur de ne pas incorporer de manifeste d'application dans le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="0b1c1-103">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b1c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b1c1-104">Syntax</span></span>  
  
```  
/nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="0b1c1-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="0b1c1-105">Remarks</span></span>  
 <span data-ttu-id="0b1c1-106">Lorsque cette option est utilisée, l’application sera soumis à la virtualisation sur Windows Vista, sauf si vous fournissez un manifeste d’application dans un fichier de ressources Win32 ou au cours d’une étape de génération ultérieure.</span><span class="sxs-lookup"><span data-stu-id="0b1c1-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="0b1c1-107">Pour plus d’informations sur la virtualisation, consultez [déploiement ClickOnce sur Windows Vista](https://docs.microsoft.com/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="0b1c1-107">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](https://docs.microsoft.com/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="0b1c1-108">Pour plus d’informations sur la création de manifestes, consultez [/win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span><span class="sxs-lookup"><span data-stu-id="0b1c1-108">For more information about manifest creation, see [/win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b1c1-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b1c1-109">See Also</span></span>  
 <span data-ttu-id="0b1c1-110">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="0b1c1-110">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="0b1c1-111"> [Page Application, Concepteur de projet (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="0b1c1-111"> [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)</span></span>
