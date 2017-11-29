---
title: "Vs de base zéro. Accès d’une chaîne de base en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 911f063d6ca9a3f5d88a1f50d9df7f908a488f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Vs de base zéro. Accès d’une chaîne de base en Visual Basic
Cette rubrique compare comment [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] et [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] fournissent l’accès aux caractères dans une chaîne. Le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] fournit toujours un accès de base zéro pour les caractères dans une chaîne, tandis que [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] fournit un accès de base zéro et basé sur un, selon la fonction.  
  
## <a name="one-based"></a>Basé sur un  
 Pour obtenir un exemple d’une base d’un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] , prenez le `Mid` (fonction). Il prend un argument qui indique la position de caractère à laquelle la sous-chaîne démarrera, en commençant à la position 1. Le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> méthode prend un index du caractère dans la chaîne à laquelle la sous-chaîne doit démarrer, en commençant à la position 0. Par conséquent, si vous avez une chaîne « ABCDE », les caractères sont numérotés 1,2,3,4,5 pour la `Mid` (fonction), mais 0,1,2,3,4 pour une utilisation avec le <xref:System.String.Substring%2A?displayProperty=nameWithType> (méthode).  
  
## <a name="zero-based"></a>Base zéro  
 Pour obtenir un exemple de base zéro [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] , prenez le `Split` (fonction). Il fractionne une chaîne et retourne un tableau contenant les sous-chaînes. Le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> méthode également fractionne une chaîne et retourne un tableau contenant les sous-chaînes. Étant donné que la `Split` (fonction) et <xref:System.String.Split%2A> retour de la méthode [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] tableaux, ils doivent être de base zéro.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [Introduction aux chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
