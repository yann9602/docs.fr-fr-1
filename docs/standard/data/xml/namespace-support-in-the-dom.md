---
title: Prise en charge des espaces de noms dans le DOM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3145df6517df9db580bfcc5d67edd9d1a61f290b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="namespace-support-in-the-dom"></a>Prise en charge des espaces de noms dans le DOM
Le DOM (Document Object Model ) XML gère parfaitement les espaces de noms. Seuls les documents XML reconnaissant les espaces de noms sont pris en charge. Le World Wide Web Consortium (W3C) établit que les applications DOM implémentant le niveau 1 peuvent ne pas prendre en charge des espaces de noms, alors que les fonctionnalités du DOM de niveau 2 gèrent parfaitement les espaces de noms. Cependant, toutes les fonctionnalités du DOM XML tiennent compte des espaces de noms, peu importe si la méthode émane de la recommandation Document Object Model (DOM) de niveau 1 ou de niveau 2.  
  
 Par exemple, dans un environnement ne prenant pas en charge les espaces de noms, l'appel de `setAttribute("A:b", "123")` conformément à la recommandation Document Object Model (DOM) de niveau 1 ne donne pas pour résultat un attribut doté du préfixe `A` et du nom local `b`. Il produit un attribut dont la valeur est `A:b`.  
  
 Dans un environnement prenant en charge les espaces de noms, par contre, l'appel à `setAttribute("A:b", "123")` de la recommandation Document Object Model (DOM) de niveau 2 génère un attribut dont le préfixe est `A` et le nom local, `b`. Voici comment Microsoft .NET Framework DOM fonctionne.  
  
 C'est pourquoi, toutes les méthodes qui prennent un paramètre de nom prennent également un préfixe destiné à qualifier ce nom. Le paramètre de nom, tel que le `A:b` dans les **setAttribute** DOM Level 1 (méthode), est analysé comme suit :  
  
-   En l'absence de caractère deux-points (:), le nom local correspond à la valeur du paramètre `name`, le préfixe et NamespaceURI étant des chaînes vides.  
  
-   En présence d'un caractère deux-points, le nom est scindé en deux parties au niveau de la position du premier caractère deux-points. Le préfixe a la valeur de la chaîne se trouvant avant le deux-points, et le nom local est la chaîne située après ce caractère. Pour les méthodes ne prenant pas de valeur NamespaceURI, NamespaceURI n'est pas résolu et garde comme valeur une chaîne vide. Sinon, NamespaceURI a pour valeur la chaîne passée à la méthode. Si le préfixe n’est pas défini, le **enregistrer** (méthode) et **InnerXml** et **OuterXml** propriétés échouent.  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
