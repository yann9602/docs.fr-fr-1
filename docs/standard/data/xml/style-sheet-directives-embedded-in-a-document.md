---
title: "Directives de feuille de style incorporées dans un document"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8c5cfcc9f35e4a07e9426a4dd24c1e2f04985f16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="92cbd-102">Directives de feuille de style incorporées dans un document</span><span class="sxs-lookup"><span data-stu-id="92cbd-102">Style Sheet Directives Embedded in a Document</span></span>
<span data-ttu-id="92cbd-103">Il arrive parfois que des données XML existantes contiennent la directive de feuille de style de `<?xml:stylesheet?>`.</span><span class="sxs-lookup"><span data-stu-id="92cbd-103">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="92cbd-104">Microsoft Internet Explorer accepte cette directive comme une alternative à le `<?xml-stylesheet?>` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="92cbd-104">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="92cbd-105">Quand les données XML contiennent une directive `<?xml:stylesheet?>`, comme le montrent les données suivantes, une tentative de chargement de ces données dans le DOM (Document Object Model) XML entraîne la levée d'une exception.</span><span class="sxs-lookup"><span data-stu-id="92cbd-105">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>  
  
```xml  
<?xml version="1.0" ?>  
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>  
<root>  
    <test>Node 1</test>  
    <test>Node 2</test>  
</root>  
```  
  
 <span data-ttu-id="92cbd-106">Cela se produit car le `<?xml:stylesheet?>` est considéré comme non valide **ProcessingInstruction** au DOM.</span><span class="sxs-lookup"><span data-stu-id="92cbd-106">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="92cbd-107">N’importe quel **ProcessingInstruction**, selon les espaces de noms dans la spécification XML peut uniquement comporter non-(noms sans deux-points), par opposition à qualifiés (QNames) des noms.</span><span class="sxs-lookup"><span data-stu-id="92cbd-107">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>  
  
 <span data-ttu-id="92cbd-108">À partir de la Section 6 de la spécification XML, l’effet de ces espaces de noms du **charge** et **LoadXml** méthodes sont conformes à la spécification qui est dans un document :</span><span class="sxs-lookup"><span data-stu-id="92cbd-108">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>  
  
-   <span data-ttu-id="92cbd-109">tous les types d'éléments et noms d'attributs contiennent un deux-points ou n'en contiennent pas ;</span><span class="sxs-lookup"><span data-stu-id="92cbd-109">All element types and attribute names contain either zero or one colon.</span></span>  
  
-   <span data-ttu-id="92cbd-110">aucun nom d'entité, aucune cible ProcessingInstruction et aucun nom de notation ne contient de deux-points.</span><span class="sxs-lookup"><span data-stu-id="92cbd-110">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>  
  
 <span data-ttu-id="92cbd-111">La présence d'un signe deux-points dans `<?xml:stylesheet?>` provoque la violation de la règle décrite au second point.</span><span class="sxs-lookup"><span data-stu-id="92cbd-111">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>  
  
 <span data-ttu-id="92cbd-112">Conformément à la recommandation du W3C (World Wide Web Consortium) sur l'association de feuilles de style à des documents XML version 1.0, disponible à l'adresse www.w3.org/TR/xml-stylesheet, l'instruction de traitement destinée à associer une feuille de style XSLT à un document XML est `<?xml-stylesheet?>`, où un trait d'union remplace le signe deux-points.</span><span class="sxs-lookup"><span data-stu-id="92cbd-112">According to the World Wide Web Consortium (W3C) Associating Style Sheets with XML documents Version 1.0 Recommendation, located at www.w3.org/TR/xml-stylesheet, the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92cbd-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92cbd-113">See Also</span></span>  
 [<span data-ttu-id="92cbd-114">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="92cbd-114">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
