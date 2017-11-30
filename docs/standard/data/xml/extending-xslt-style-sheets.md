---
title: Extension de feuilles de style XSLT
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df4ba2bf-a99e-4d22-bbf3-04fc67669dbc
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8ccd1a95586bc92bcc712639eded135a69da1a36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="extending-xslt-style-sheets"></a><span data-ttu-id="c6b34-102">Extension de feuilles de style XSLT</span><span class="sxs-lookup"><span data-stu-id="c6b34-102">Extending XSLT Style Sheets</span></span>
<span data-ttu-id="c6b34-103">Cette section décrit les différentes méthodes d'extension de la fonctionnalité XSLT.</span><span class="sxs-lookup"><span data-stu-id="c6b34-103">This section describes the different methods of extending the XSLT functionality.</span></span> <span data-ttu-id="c6b34-104">Vous pouvez ajouter des paramètres ou des objets d'extension à l'aide de la classe <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="c6b34-104">You can add extension objects or parameters using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="c6b34-105">Ces paramètres ou objets d'extension peuvent alors être appelés depuis la feuille de style.</span><span class="sxs-lookup"><span data-stu-id="c6b34-105">The extension objects or parameters can then be called from the style sheet.</span></span> <span data-ttu-id="c6b34-106">Vous pouvez en outre incorporer des blocs de script dans la feuille de style avec l'élément `msxsl:script`.</span><span class="sxs-lookup"><span data-stu-id="c6b34-106">In addition, you can also embed script blocks into the style sheet by using the `msxsl:script` element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c6b34-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c6b34-107">In This Section</span></span>  
 [<span data-ttu-id="c6b34-108">Objets d’Extension XSLT</span><span class="sxs-lookup"><span data-stu-id="c6b34-108">XSLT Extension Objects</span></span>](../../../../docs/standard/data/xml/xslt-extension-objects.md)  
 <span data-ttu-id="c6b34-109">Présente l'utilisation de la classe <xref:System.Xml.Xsl.XsltArgumentList> pour le traitement des objets d'extension XML.</span><span class="sxs-lookup"><span data-stu-id="c6b34-109">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT extension objects.</span></span>  
  
 [<span data-ttu-id="c6b34-110">Paramètres XSLT</span><span class="sxs-lookup"><span data-stu-id="c6b34-110">XSLT Parameters</span></span>](../../../../docs/standard/data/xml/xslt-parameters.md)  
 <span data-ttu-id="c6b34-111">Présente l'utilisation de la classe <xref:System.Xml.Xsl.XsltArgumentList> pour le traitement des paramètres XSLT.</span><span class="sxs-lookup"><span data-stu-id="c6b34-111">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT parameters.</span></span>  
  
 [<span data-ttu-id="c6b34-112">Msxsl : script de script à l’aide des blocs</span><span class="sxs-lookup"><span data-stu-id="c6b34-112">Script Blocks Using msxsl:script</span></span>](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md)  
 <span data-ttu-id="c6b34-113">Explique l'utilisation de l'élément `msxsl:script`.</span><span class="sxs-lookup"><span data-stu-id="c6b34-113">Discusses using the `msxsl:script` element.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c6b34-114">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="c6b34-114">Related Sections</span></span>  
 [<span data-ttu-id="c6b34-115">Transformations XSLT</span><span class="sxs-lookup"><span data-stu-id="c6b34-115">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
