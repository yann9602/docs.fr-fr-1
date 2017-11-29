---
title: "Peut &#39; t créer le fichier temporaire nécessaire"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID322
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dbb1c65318f954249da097b026583b09ad340e20
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="can39t-create-necessary-temporary-file"></a><span data-ttu-id="ec093-102">Peut &#39; t créer le fichier temporaire nécessaire</span><span class="sxs-lookup"><span data-stu-id="ec093-102">Can&#39;t create necessary temporary file</span></span>
<span data-ttu-id="ec093-103">Le lecteur est complète qui contient le répertoire spécifié par la variable d’environnement TEMP ou la variable d’environnement TEMP spécifie un lecteur non valide ou en lecture seule ou un répertoire.</span><span class="sxs-lookup"><span data-stu-id="ec093-103">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ec093-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ec093-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="ec093-105">Supprimez les fichiers à partir du lecteur, si celui-ci est plein.</span><span class="sxs-lookup"><span data-stu-id="ec093-105">Delete files from the drive, if full.</span></span>  
  
2.  <span data-ttu-id="ec093-106">Spécifiez un autre lecteur dans la variable d’environnement TEMP.</span><span class="sxs-lookup"><span data-stu-id="ec093-106">Specify a different drive in the TEMP environment variable.</span></span>  
  
3.  <span data-ttu-id="ec093-107">Spécifiez un lecteur valide pour la variable d’environnement TEMP.</span><span class="sxs-lookup"><span data-stu-id="ec093-107">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4.  <span data-ttu-id="ec093-108">Supprimez la restriction en lecture seule du lecteur actuellement spécifié ou du répertoire.</span><span class="sxs-lookup"><span data-stu-id="ec093-108">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec093-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec093-109">See Also</span></span>  
 [<span data-ttu-id="ec093-110">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="ec093-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
