---
title: "Le fichier est déjà ouvert."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3305831e840510e3f0b5bcb8bf847e39ea3ee4ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="file-already-open"></a><span data-ttu-id="37525-102">Le fichier est déjà ouvert.</span><span class="sxs-lookup"><span data-stu-id="37525-102">File already open</span></span>
<span data-ttu-id="37525-103">Un fichier doit parfois être fermé avant un autre `FileOpen` ou autre opération ne peut se produire.</span><span class="sxs-lookup"><span data-stu-id="37525-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="37525-104">Cette erreur peut avoir plusieurs causes, dont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="37525-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="37525-105">Un mode de sortie séquentielle `FileOpen` opération a été exécutée pour un fichier qui est déjà ouvert</span><span class="sxs-lookup"><span data-stu-id="37525-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="37525-106">Une instruction fait référence à un fichier ouvert.</span><span class="sxs-lookup"><span data-stu-id="37525-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="37525-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="37525-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="37525-108">Fermez le fichier avant d’exécuter l’instruction.</span><span class="sxs-lookup"><span data-stu-id="37525-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37525-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37525-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
