---
title: Gestion des espaces blancs significatifs ou non lors du chargement du DOM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 82401a18132801f9aa5368832b96be3cb67a8642
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>Gestion des espaces blancs significatifs ou non lors du chargement du DOM
Lors du chargement du document, vous pouvez définir l’option pour conserver l’espace blanc et créer **XmlWhitespace** nœuds dans l’arborescence du document. Pour créer des nœuds d’espaces blancs, attribuez le **PreserveWhitespace** true à la propriété. Si la propriété est définie **false**, qui est la valeur par défaut, les nœuds d’espace blanc ne sont pas créés. Nœuds d’espaces blancs significatifs sont toujours préservés et **XmlSignificantWhitespace** sont toujours créés en mémoire pour représenter ces données, quel que soit le paramètre de la **PreserveWhitespace** indicateur.  
  
 Si le document est chargé à partir d’un lecteur, la définition de la **PreserveWhitespace** indicateur de propriété sur le **XmlDocument** classe affecte la création de **XmlWhitespace** nœuds uniquement lorsque le **WhitespaceHandling** propriété sur le **XmlTextReader** n’est pas définie **WhitespaceHandling.None**. Il s’agit de la valeur de la **WhitespaceHandling** propriété sur le lecteur qui est prioritaire sur le paramètre de cet indicateur sur le **XmlDocument**. Pour plus d’informations sur **XmlSignificantWhitespace**, consultez <xref:System.Xml.XmlSignificantWhitespace>.  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
