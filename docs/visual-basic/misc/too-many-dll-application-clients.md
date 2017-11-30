---
title: Trop de clients pour cette DLL
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID47
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d4b9278134e937ac8bf4626237954432d727ac0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="too-many-dll-application-clients"></a><span data-ttu-id="35c01-102">Trop de clients pour cette DLL</span><span class="sxs-lookup"><span data-stu-id="35c01-102">Too many DLL application clients</span></span>
<span data-ttu-id="35c01-103">La bibliothèque de liens dynamiques (DLL) de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] autorise uniquement l’accès à un nombre limité d’applications hôtes.</span><span class="sxs-lookup"><span data-stu-id="35c01-103">The dynamic-link library (DLL) for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can only accommodate access by a limited number of host applications.</span></span> <span data-ttu-id="35c01-104">Votre application et les autres applications qui sont des hôtes [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] (dont certaines sont accessibles par votre application) tentent toutes d’accéder à la DLL [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] en même temps.</span><span class="sxs-lookup"><span data-stu-id="35c01-104">Your application and other applications that are [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] hosts (some of which may be accessed by your application) are all attempting to access the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] DLL at the same time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="35c01-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="35c01-105">To correct this error</span></span>  
  
-   <span data-ttu-id="35c01-106">Réduisez le nombre d’applications ouvertes accédant à [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="35c01-106">Reduce the number of open applications accessing [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35c01-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35c01-107">See Also</span></span>  
 [<span data-ttu-id="35c01-108">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="35c01-108">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
