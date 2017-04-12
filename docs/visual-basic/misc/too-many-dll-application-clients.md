---
title: Trop de clients application DLL | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID47
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1abc9ce574de00db42a33cde478ca80be74e61ff
ms.lasthandoff: 03/13/2017

---
# <a name="too-many-dll-application-clients"></a>Trop de clients pour cette DLL
La bibliothèque de liens dynamiques (DLL) pour [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] autorise uniquement l’accès à un nombre limité d’applications hôtes. Votre application et autres applications qui sont [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] hôtes (certains d'entre eux sont accessibles par votre application) tentent d’accéder à la [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] DLL en même temps.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Réduire le nombre d’applications ouvertes accédant à [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Types d’erreurs](../../visual-basic/programming-guide/language-features/error-types.md)
