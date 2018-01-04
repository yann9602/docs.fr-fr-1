---
title: Gestion de xml:space en XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], whitespace processing
- xml:space attribute [XAML Services]
- whitespace processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
caps.latest.revision: "15"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b8356cdb47b6b834e8d9a6bb84b26445af6d865
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xmlspace-handling-in-xaml"></a>Gestion de xml:space en XAML
Le `xml:space` attribut est un attribut XML qui déclare le comportement de traitement des espaces blancs significatifs dans un élément objet. Ce comportement ne s’applique à tout le contenu (texte interne) contenu dans l’élément où `xml:space` est déclarée et s’étend également aux éléments enfants.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \- ou -  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>Notes  
 La définition de la `xml:space` attribut en XAML, y compris ses deux valeurs possibles est dérivée de `xml:space` , défini comme un « attribut spécial » par les spécifications W3C pour XML.  
  
 La valeur par défaut de la `xml:space` attribut est la valeur littérale `"default"`. Pour la valeur `"default"`, ou si `xml:space` n’est pas indiqué, le comportement de l’analyse d’un espace blanc significatif est la gestion par défaut, tel que défini dans la rubrique [traitement des espaces blancs en XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
 Pour conserver l’espace blanc dans le contenu d’élément objet, spécifiez `xml:space="preserve"` sur cet élément objet.  
  
 Dans la plupart des interprétations le `xml:space` effets et la valeur de l’attribut sont limitées aux éléments enfants.  
  
 Pour obtenir une description complète des espaces blancs en XAML de traitement, consultez [traitement des espaces blancs en XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des espaces blancs en XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)  
 [Vue d’ensemble du langage XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
