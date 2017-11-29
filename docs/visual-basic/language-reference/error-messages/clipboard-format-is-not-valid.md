---
title: Format de Presse-papiers non valide
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7adc417d962de35272319d7dc976b237c7e2b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="8c154-102">Format de Presse-papiers non valide</span><span class="sxs-lookup"><span data-stu-id="8c154-102">Clipboard format is not valid</span></span>
<span data-ttu-id="8c154-103">Le format de Presse-papiers spécifié n’est pas compatible avec la méthode en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8c154-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="8c154-104">Parmi les causes possibles de cette erreur sont :</span><span class="sxs-lookup"><span data-stu-id="8c154-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="8c154-105">À l’aide du Presse-papiers `GetText` ou `SetText` méthode avec un format de Presse-papiers autre que `vbCFText` ou `vbCFLink`.</span><span class="sxs-lookup"><span data-stu-id="8c154-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
-   <span data-ttu-id="8c154-106">À l’aide du Presse-papiers `GetData` ou `SetData` méthode avec un format de Presse-papiers autre que `vbCFBitmap`, `vbCFDIB`, ou `vbCFMetafile`.</span><span class="sxs-lookup"><span data-stu-id="8c154-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
-   <span data-ttu-id="8c154-107">À l’aide de la `DataObject``GetData` méthode ou `SetData` méthode avec un format de Presse-papiers dans la plage réservée par Microsoft Windows pour des formats (& HC000 - & HFFFF), lorsque ce format de Presse-papiers n’a pas été inscrit auprès de Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="8c154-107">Using the `DataObject``GetData` method or `SetData` method with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8c154-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="8c154-108">To correct this error</span></span>  
  
-   <span data-ttu-id="8c154-109">Supprimez le format incorrect et spécifier une valide.</span><span class="sxs-lookup"><span data-stu-id="8c154-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c154-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c154-110">See Also</span></span>  
 [<span data-ttu-id="8c154-111">Presse-papiers : ajout d’autres formats</span><span class="sxs-lookup"><span data-stu-id="8c154-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
