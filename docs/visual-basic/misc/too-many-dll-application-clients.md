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
# <a name="too-many-dll-application-clients"></a>Trop de clients pour cette DLL
La bibliothèque de liens dynamiques (DLL) de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] autorise uniquement l’accès à un nombre limité d’applications hôtes. Votre application et les autres applications qui sont des hôtes [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] (dont certaines sont accessibles par votre application) tentent toutes d’accéder à la DLL [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] en même temps.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Réduisez le nombre d’applications ouvertes accédant à [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Types d’erreurs](../../visual-basic/programming-guide/language-features/error-types.md)
