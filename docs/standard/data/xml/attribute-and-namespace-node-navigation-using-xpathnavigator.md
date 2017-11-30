---
title: "Navigation entre les nœuds d’attribut et d’espace de noms à l’aide de XPathNavigator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 45e94954641e935597394b7cf04818c6c78ea675
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a>Navigation entre les nœuds d’attribut et d’espace de noms à l’aide de XPathNavigator
Le <xref:System.Xml.XPath.XPathNavigator> classe fournit deux ensembles de méthodes de navigation, le premier jeu, trouvé dans le [Node Set Navigation à l’aide de XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) rubrique, sont utilisées pour naviguer *les collections de nœuds* dans un <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> objet. Le deuxième jeu, décrit dans cette rubrique, sont utilisées pour naviguer *nœuds d’attribut et d’espace de noms* dans un <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> objet.  
  
## <a name="attribute-node-navigation"></a>Navigation entre les nœuds d'attribut  
 Les attributs sont des propriétés d'un élément, pas des enfants d'un élément. La distinction est importante étant donné que les méthodes de la classe <xref:System.Xml.XPath.XPathNavigator> permettent de naviguer entre les nœuds frères, parents et enfants.  
  
 Par exemple, les méthodes <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> et <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> ne permettent pas de naviguer d'un élément à un attribut ou entre des attributs. Par contre, les attributs possèdent des méthodes de navigation distinctes.  
  
 Voici les méthodes de navigation entre attributs de la classe <xref:System.Xml.XPath.XPathNavigator>.  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 Si le nœud actuel est un élément, vous pouvez utiliser la propriété <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> pour vérifier si des attributs sont associés à l'élément. Une fois que vous savez qu'un élément possède des attributs, il existe plusieurs méthodes permettant d'accéder à ces attributs. Pour extraire un seul attribut de l'élément, utilisez la méthode <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A>. Pour déplacer <xref:System.Xml.XPath.XPathNavigator> vers un attribut particulier, utilisez la méthode <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>. Vous pouvez également itérer sur chaque attribut d'un élément à l'aide de la méthode <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>, suivie par plusieurs appels à la méthode <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>.  
  
> [!NOTE]
>  Lorsque <xref:System.Xml.XPath.XPathNavigator> se trouve sur un nœud d'attribut ou d'espace de noms, les méthodes <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> et <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> retournent toujours `false` et n'ont pas d'effet sur la position de <xref:System.Xml.XPath.XPathNavigator>. Les méthodes <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A> et <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> font office d'exceptions.  
  
## <a name="namespace-node-navigation"></a>Navigation entre les nœuds d'espace de noms  
 Chaque élément est associé à une collection de nœuds d'espace de noms, un pour chaque préfixe d'espace de noms lié à un URI d'espace de noms dans la portée de l'élément (notamment le préfixe XML lié à l'espace de noms `http://www.w3.org/XML/1998/namespace`, qui est déclaré de manière implicite dans chaque document XML) et un pour l'espace de noms par défaut s'il en existe un dans la portée de l'élément. L'élément est le parent de chacun de ces nœuds d'espace de noms ; toutefois, un nœud d'espace de noms n'est pas un enfant de ses éléments parents.  
  
 Comme pour les attributs, les méthodes <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> et <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> ne permettent pas de naviguer d'un nœud d'élément à un nœuds d'espace de noms ou entre des nœuds d'espace de noms. Par contre, les nœuds d'espace de noms possèdent des méthodes de navigation distinctes.  
  
 Voici les méthodes de navigation entre espaces de noms de la classe <xref:System.Xml.XPath.XPathNavigator>.  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 Il existe toujours au moins un nœud d'espace de noms dans la portée d'un élément dans un document XML. Il s'agit du nœud d'espace de noms avec le préfixe `xml` et l'URI d'espace de noms `http://www.w3.org/XML/1998/namespace`. Pour extraire un URI d'espace de noms dans la portée d'un préfixe donné, utilisez la méthode <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A>. Pour déplacer l'objet <xref:System.Xml.XPath.XPathNavigator> vers un nœud d'espace de noms particulier, utilisez la méthode <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>. Vous pouvez également itérer sur chaque nœud d'espace de noms dans la portée d'un élément à l'aide de la méthode <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>, suivie par plusieurs appels à la méthode <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>.  
  
> [!NOTE]
>  Lorsque <xref:System.Xml.XPath.XPathNavigator> se trouve sur un nœud d'attribut ou d'espace de noms, les méthodes <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> et <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> retournent toujours `false` et n'ont pas d'effet sur la position de <xref:System.Xml.XPath.XPathNavigator>. Les méthodes <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A> et <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> font office d'exceptions.  
  
### <a name="the-xpathnamespacescope-enumeration"></a>Énumération XPathNamespaceScope  
 Lors de la navigation entre les nœuds d'espace de noms, il est possible d'appeler les méthodes <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> et <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> à l'aide d'un paramètre <xref:System.Xml.XPath.XPathNamespaceScope>. Ces méthodes se comportent différemment de leurs équivalents appelés sans paramètre. L'énumération <xref:System.Xml.XPath.XPathNamespaceScope> a des valeurs de <xref:System.Xml.XPath.XPathNamespaceScope.All>, <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml> ou <xref:System.Xml.XPath.XPathNamespaceScope.Local>.  
  
 Les exemples suivants indiquent les espaces de noms qui sont retournés par les méthodes <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> et <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> dans différentes portées d'un document XML.  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 La séquence d'espaces de noms (l'espace de noms sur lequel l'objet <xref:System.Xml.XPath.XPathNavigator> est positionné après un appel à la méthode <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>, suivi d'une série d'appels à la méthode <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>) est la suivante.  
  
-   Lorsqu'il est positionné sur `element2` : `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"` et `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
-   Lorsqu'il est positionné sur `element1` : `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"` et `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
-   Lorsqu'il est positionné sur `root` : `xmlns:xml="http://www.w3.org/XML/1998/namespace".`  
  
> [!NOTE]
>  la classe <xref:System.Xml.XPath.XPathNavigator> retourne des nœuds d'espace de noms dans l'ordre inverse du document. Par conséquent, la méthode <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> se déplace essentiellement vers le dernier nœud d'espace de noms de la portée actuelle.  
  
 Les exemples suivants indiquent les espaces de noms qui sont retournés par les méthodes <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> et <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> avec l'énumération <xref:System.Xml.XPath.XPathNamespaceScope> spécifiée dans différentes portées d'un document XML.  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 Lorsqu'elle se trouve sur `child2`, la séquence d'espaces de noms (l'espace de noms sur lequel l'objet <xref:System.Xml.XPath.XPathNavigator> est positionné après un appel à la méthode <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>, suivi d'une série d'appels à la méthode <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>) est la suivante.  
  
-   <xref:System.Xml.XPath.XPathNamespaceScope.All> : `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, `xmlns="http://www.contoso.com"` et `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
-   <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml> : `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"` et `xmlns="http://www.contoso.com"`.  
  
-   <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
>  la classe <xref:System.Xml.XPath.XPathNavigator> retourne des nœuds d'espace de noms dans l'ordre inverse du document. Par conséquent, la méthode <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> se déplace essentiellement vers le dernier nœud d'espace de noms de la portée actuelle.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Traitement des données XML à l’aide du modèle de données XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Navigation de jeu de nœud à l’aide de XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 [Extraire des données XML à l’aide de XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 [L’accès à fortement typée des données XML à l’aide de XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
