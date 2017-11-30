---
title: "Implémentation de comportements discrétionnaires dans la classe XslTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2758ea1-03f6-47bd-88d2-0fb7ccdb2fab
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7b6c81a5737b879b7c1356c4b9c2ab68fbbc4688
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="implementation-of-discretionary-behaviors-in-the-xsltransform-class"></a>Implémentation de comportements discrétionnaires dans la classe XslTransform
> [!NOTE]
>  La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans le [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Consultez [à l’aide de la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) et [migration depuis la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) pour plus d’informations.  
  
 Les comportements discrétionnaires sont décrits comme des comportements, répertoriés dans la recommandation du World Wide Web Consortium (W3C) sur XSLT (XSL Transformations) Version 1.0 (www.w3.org/TR/xslt), où le fournisseur d’implémentation choisit une option parmi plusieurs possibles pour gérer une situation. Par exemple, dans la section 7.3 sur la création d'instructions de traitement, la recommandation du W3C précise que la création de nœuds autres que des nœuds de texte lors d'une instanciation du contenu de `xsl:processing-instruction` correspond à une erreur. Pour certains problèmes, le W3C indique la décision à prendre si le processeur décide de récupérer l'erreur. Pour le problème donné dans la section 7.3, le W3C indique que l'implémentation peut récupérer cette erreur en ignorant les nœuds et leur contenu.  
  
 Donc, pour chacun des comportements discrétionnaires autorisés par le W3C, le tableau suivant répertorie les comportements discrétionnaires implémentés pour l'implémentation [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] de la classe <xref:System.Xml.Xsl.XslTransform>, et la section de la recommandation du W3C sur XSLT 1.0 traitant de ce problème.  
  
|Problème|Comportement|Section|  
|-------------|--------------|-------------|  
|Un nœud de texte correspond à la fois à `xsl:strip-space` et à `xsl:preserve-space`.|Récupération|3.4|  
|Un nœud source correspond à plusieurs règles de modèle.|Récupération|5.5|  
|Un URI (Uniform Resource Identifier) d'espace de noms est déclaré comme étant un alias pour plusieurs URI d'espaces de noms dont la priorité d'importation est identique.|Récupération|7.1.1|  
|L'attribut de nom dans `xsl:attribute` et `xsl:element` généré à partir d'un modèle de valeur d'attribut n'est pas un nom qualifié (QName) valide.|Exception levée|7.1.2 et 7.1.3|  
|L'ajout d'un attribut à un élément après l'ajout de nœuds enfants au nœud élément.|Récupération|7.1.3|  
|Ajout d'un attribut à autre chose qu'à un nœud d'élément.|Récupération|7.1.3|  
|L'instanciation du contenu de l'élément `xsl:attribute` n'est pas un nœud de texte.|Récupération|7.1.3|  
|Deux ensembles d'attributs ont la même priorité d'importation et le même nom développé. Les deux ont le même attribut et il n'y a pas d'autre ensemble d'attributs contenant l'attribut commun avec le même nom et une importance supérieure.|Récupération|7.1.4|  
|L'attribut de nom `xsl:processing-instruction` ne produit pas un NCName et une cible d'instruction de traitement.|Récupération|7.3|  
|L'instanciation du contenu de `xsl:processing-instruction` crée des nœuds autres que des nœuds de texte.|Récupération|7.3|  
|Les résultats de l'instanciation du contenu de `xsl:processing-instruction` contiennent la chaîne « `?>` ».|Récupération|7.3|  
|Résultats de l’instanciation du contenu de la `xsl:comment` contient la chaîne «-- », ou se termine par «- ».|Récupération|7.4|  
|Les résultats de l'instanciation du contenu de `xsl:comment` créent des nœuds autres que des nœuds de texte.|Récupération|7.4|  
|Le modèle d'un élément de liaison de variables retourne un nœud d'attribut ou un nœud d'espace de noms.|Récupération|11.2|  
|Une erreur se produit lors de l'extraction de la ressource à partir de l'URI passé dans la fonction de document.|Exception levée|12.1|  
|La référence URI de la fonction de document contient un identificateur de fragment, et une erreur se produit lors du traitement de ce dernier.|Exception levée|12.1|  
|Il existe plusieurs attributs portant le même nom qui ne sont pas intitulés `cdata-section-elements` dans `xls:output`, et ces attributs ont la même priorité d'importation.|Récupération|16|  
|Le processeur ne prend pas en charge la valeur d'encodage de caractères octroyée dans l'attribut `encoding` de l'élément `xsl:output`.|Récupération|16.1|  
|`disable-output-escaping` s'utilise pour un nœud de texte et ce nœud est utilisé pour créer autre chose qu'un nœud de texte dans l'arborescence résultat.|L'attribut `disable-output-escaping` est ignoré.|16.4|  
|Conversion d'un fragment d'arborescence résultat en un nombre ou une chaîne si le fragment d'arborescence résultat contient un nœud de texte dont la production littérale des caractères en sortie est activée.|Ignoré|16.4|  
|La production littérale des caractères en sortie est désactivée pour les caractères qui ne peuvent pas être représentés dans l'encodage utilisé par le processeur XSLT pour la sortie.|Ignoré|16.4|  
|Ajout d'un nœud d'espace de noms à un élément après que les enfants ou les attributs ont été ajoutés à ce dernier.|Récupération|Errata e25|  
|`xsl:number` est une valeur NaN, infinie ou inférieure à 0,5.|Récupération|Errata e24|  
|La collection de nœuds du second argument de la fonction de document est vide et la référence URI est relative.|Récupération|Errata e14|  
  
 Des sections de l'errata se trouvent dans le document du World Wide Web Consortium (W3C) sur les erreurs de spécifications XSLT (XSL Transformations) Version 1.0, à l'adresse http://www.w3.org/1999/11/REC-xslt-19991116-errata.  
  
## <a name="custom-defined-implementation-behaviors"></a>Comportements d'implémentation personnalisés  
 Certains comportements sont spécifiques à l'implémentation de la classe <xref:System.Xml.Xsl.XslTransform>. Cette section présente l'implémentation propre au fournisseur de `xsl:sort` et les fonctionnalités facultatives prises en charge par la classe <xref:System.Xml.Xsl.XslTransform>.  
  
## <a name="xslsort"></a>xsl:sort  
 Lors de l'utilisation d'une transformation à trier, la recommandation du W3C sur XSLT 1.0 établit des observations. Il s'agit des éléments suivants :  
  
-   Deux processeurs XSLT peuvent être des processeurs conformes, mais ils peuvent effectuer un tri différent.  
  
-   Tous les processeurs XSLT ne prennent pas en charge les mêmes langages.  
  
-   En ce qui concerne les langages, le tri effectué par des processeurs distincts peut varier sur un langage spécifique, non spécifié dans le `xsl:sort.`.  
  
 Le tableau suivant montre le comportement de tri implémenté pour chaque type de données dans l’implémentation .NET Framework d’une transformation utilisant le <xref:System.Xml.Xsl.XslTransform>.  
  
|Type de données|Comportement de tri|  
|---------------|----------------------|  
|Texte|Les données sont triées en utilisant la méthode String.Compare du Common Language Runtime (CLR) ainsi que les paramètres régionaux culturels. Lorsque les données sont de type « texte », le tri dans la classe <xref:System.Xml.Xsl.XslTransform> se comporte de la même façon que les comportements de comparaison de chaînes du Common Language Runtime.|  
|Nombre|Les valeurs numériques sont traitées comme des nombres XPath (XML Path Language) et sont triées en fonction des détails présentés dans la recommandation du W3C sur le langage XPath (XML Path Language) Version 1.0, section 3.5 (www.w3.org/TR/xpath.html#numbers).|  
  
## <a name="optional-features-supported"></a>Fonctionnalités facultatives prises en charge  
 Le tableau suivant présente les fonctionnalités facultatives à implémenter pour un processeur XSLT et qui sont implémentées dans la classe <xref:System.Xml.Xsl.XslTransform>.  
  
|Fonctionnalité|Emplacement de référence|Remarques|  
|-------------|------------------------|-----------|  
|Attribut `disable-output-escaping` sur les balises `<xsl:text...>` et `<xsl:value-of...>`.|Recommandation du W3C sur XSLT 1.0, <br /><br /> Section 16.4|L'attribut `disable-output-escaping` est ignoré lorsque l'élément `xsl:text` ou `xsl:value-of` est utilisé dans un élément `xsl:comment`, `xsl:processing-instruction` ou `xsl:attribute`.<br /><br /> Les fragments d'arborescence résultat qui contiennent du texte et la sortie de texte ayant fait l'objet d'un échappement ne sont pas pris en charge.<br /><br /> L'attribut disable-output-escaping est ignoré lors de sa transformation en un objet <xref:System.Xml.XmlReader> ou <xref:System.Xml.XmlWriter>.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Xsl.XslTransform>  
 [XslTransform Class Implements the XSLT Processor](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [Transformations XSLT avec la classe XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [XPathNavigator dans les Transformations](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [XPathNodeIterator dans les Transformations](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Entrée XPathDocument dans XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Entrée XmlDataDocument dans XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [Entrée XmlDocument dans XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
