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
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a><span data-ttu-id="27411-102">Gestion des espaces blancs significatifs ou non lors du chargement du DOM</span><span class="sxs-lookup"><span data-stu-id="27411-102">White Space and Significant White Space Handling when Loading the DOM</span></span>
<span data-ttu-id="27411-103">Lors du chargement du document, vous pouvez définir l’option pour conserver l’espace blanc et créer **XmlWhitespace** nœuds dans l’arborescence du document.</span><span class="sxs-lookup"><span data-stu-id="27411-103">When loading the document, you can set the option to preserve white space and create **XmlWhitespace** nodes in the document tree.</span></span> <span data-ttu-id="27411-104">Pour créer des nœuds d’espaces blancs, attribuez le **PreserveWhitespace** true à la propriété.</span><span class="sxs-lookup"><span data-stu-id="27411-104">To create white space nodes, set the **PreserveWhitespace** property to true.</span></span> <span data-ttu-id="27411-105">Si la propriété est définie **false**, qui est la valeur par défaut, les nœuds d’espace blanc ne sont pas créés.</span><span class="sxs-lookup"><span data-stu-id="27411-105">If the property is set to **false**, which is the default, white space nodes are not created.</span></span> <span data-ttu-id="27411-106">Nœuds d’espaces blancs significatifs sont toujours préservés et **XmlSignificantWhitespace** sont toujours créés en mémoire pour représenter ces données, quel que soit le paramètre de la **PreserveWhitespace** indicateur.</span><span class="sxs-lookup"><span data-stu-id="27411-106">Significant white spaces nodes are always preserved, and **XmlSignificantWhitespace** nodes are always created in memory to represent this data, regardless of the setting of the **PreserveWhitespace** flag.</span></span>  
  
 <span data-ttu-id="27411-107">Si le document est chargé à partir d’un lecteur, la définition de la **PreserveWhitespace** indicateur de propriété sur le **XmlDocument** classe affecte la création de **XmlWhitespace** nœuds uniquement lorsque le **WhitespaceHandling** propriété sur le **XmlTextReader** n’est pas définie **WhitespaceHandling.None**.</span><span class="sxs-lookup"><span data-stu-id="27411-107">If the document is loaded from a reader, then setting of the **PreserveWhitespace** flag property on the **XmlDocument** class affects the creation of **XmlWhitespace** nodes only when the **WhitespaceHandling** property on the **XmlTextReader** is not set to **WhitespaceHandling.None**.</span></span> <span data-ttu-id="27411-108">Il s’agit de la valeur de la **WhitespaceHandling** propriété sur le lecteur qui est prioritaire sur le paramètre de cet indicateur sur le **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="27411-108">It is the value of the **WhitespaceHandling** property on the reader that takes precedence over the setting of that flag on the **XmlDocument**.</span></span> <span data-ttu-id="27411-109">Pour plus d’informations sur **XmlSignificantWhitespace**, consultez <xref:System.Xml.XmlSignificantWhitespace>.</span><span class="sxs-lookup"><span data-stu-id="27411-109">For more information on **XmlSignificantWhitespace**, see <xref:System.Xml.XmlSignificantWhitespace>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27411-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27411-110">See Also</span></span>  
 [<span data-ttu-id="27411-111">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="27411-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
