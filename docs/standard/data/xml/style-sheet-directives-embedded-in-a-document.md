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
# <a name="style-sheet-directives-embedded-in-a-document"></a>Directives de feuille de style incorporées dans un document
Il arrive parfois que des données XML existantes contiennent la directive de feuille de style de `<?xml:stylesheet?>`. Microsoft Internet Explorer accepte cette directive comme une alternative à le `<?xml-stylesheet?>` syntaxe. Quand les données XML contiennent une directive `<?xml:stylesheet?>`, comme le montrent les données suivantes, une tentative de chargement de ces données dans le DOM (Document Object Model) XML entraîne la levée d'une exception.  
  
```xml  
<?xml version="1.0" ?>  
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>  
<root>  
    <test>Node 1</test>  
    <test>Node 2</test>  
</root>  
```  
  
 Cela se produit car le `<?xml:stylesheet?>` est considéré comme non valide **ProcessingInstruction** au DOM. N’importe quel **ProcessingInstruction**, selon les espaces de noms dans la spécification XML peut uniquement comporter non-(noms sans deux-points), par opposition à qualifiés (QNames) des noms.  
  
 À partir de la Section 6 de la spécification XML, l’effet de ces espaces de noms du **charge** et **LoadXml** méthodes sont conformes à la spécification qui est dans un document :  
  
-   tous les types d'éléments et noms d'attributs contiennent un deux-points ou n'en contiennent pas ;  
  
-   aucun nom d'entité, aucune cible ProcessingInstruction et aucun nom de notation ne contient de deux-points.  
  
 La présence d'un signe deux-points dans `<?xml:stylesheet?>` provoque la violation de la règle décrite au second point.  
  
 Conformément à la recommandation du W3C (World Wide Web Consortium) sur l'association de feuilles de style à des documents XML version 1.0, disponible à l'adresse www.w3.org/TR/xml-stylesheet, l'instruction de traitement destinée à associer une feuille de style XSLT à un document XML est `<?xml-stylesheet?>`, où un trait d'union remplace le signe deux-points.  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
