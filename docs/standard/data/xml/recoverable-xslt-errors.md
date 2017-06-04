---
title: "Erreurs XSLT r&#233;cup&#233;rables | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 484929b0-fefb-4629-87ee-ebdde70ff1f8
caps.latest.revision: 2
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 2
---
# Erreurs XSLT r&#233;cup&#233;rables
La recommandation du W3C sur XSLT \(XSL Transformations\) Version 1.0 comprend des zones dans lesquelles le fournisseur d'implémentation peut décider de la manière de gérer une situation.  Ces zones sont considérées comme discrétionnaires en termes de comportement.  Par exemple, dans la section 7.3 sur la création d'instructions de traitement, la recommandation sur XSLT 1.0 précise que la création de nœuds autres que des nœuds de texte lors d'une instanciation du contenu de `xsl:processing-instruction` génère une erreur.  Pour certains problèmes, la recommandation sur XSLT 1.0 indique la décision à prendre si le processeur décide de récupérer l'erreur.  Pour le problème donné dans la section 7.3, le W3C indique que l'implémentation peut récupérer cette erreur en ignorant les nœuds et leur contenu.  
  
## Comportements discrétionnaires  
 Le tableau suivant répertorie chaque comportement discrétionnaire autorisé par la recommandation sur XSLT 1.0 et la façon dont ces comportements sont gérés par la classe <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
-   La récupération indique que la classe <xref:System.Xml.Xsl.XslCompiledTransform> va récupérer cette erreur.  L'événement <xref:System.Xml.Xsl.XsltArgumentList.XsltMessageEncountered?displayProperty=fullName> peut permettre de signaler tous les événements du processeur XSLT.  
  
-   L'erreur indique qu'une exception est levée pour cette condition.  
  
-   Les références de section se trouvent dans la [recommandation W3C XSL Transformations \(XSLT\) Version 1.0](http://go.microsoft.com/fwlink/?LinkId=49919) et l'[errata de la spécification W3C XSL Transformations \(XSLT\) Version 1.0](http://go.microsoft.com/fwlink/?LinkId=49917).  
  
|Condition XSLT|Section|Comportement XslCompiledTransform|  
|--------------------|-------------|---------------------------------------|  
|Un nœud de texte correspond à la fois à `xsl:strip-space` et à `xsl:preserve-space`.|3.4|Récupération|  
|Un nœud source correspond à plusieurs règles de modèle.|5.5|Récupération|  
|Un URI d'espace de noms est déclaré comme étant un alias pour plusieurs URI d'espace de noms dont la priorité d'importation est identique.|7.1.1|Récupération|  
|L'attribut `name` de `xsl:attribute` et `xsl:element` généré à partir d'une valeur d'attribut n'est pas un nom qualifié.|7.1.2, 7.1.3|Erreur\*|  
|Deux ensembles d'attributs avec le même nom d'importation et le même nom développé ont un attribut en commun et aucun autre ensemble d'attributs contenant l'attribut commun du même nom n'est d'une importance plus élevée.|7.1.4|Récupération|  
|Ajout d'un attribut à un élément après ajout d'enfants.|7.1.3|Erreur\*|  
|Création d'un attribut avec le nom « xmlns »|7.1.3|Erreur\*|  
|Ajout d'un attribut à un nœud que n'est pas un élément.|7.1.3|Erreur\*|  
|Création de nœuds autres que les nœuds de texte lors de l'instanciation du contenu de l'attribut `xsl:attribute`.|7.1.3|Erreur\*|  
|L'attribut `name` d'une `xsl:processing-instruction` ne produit ni un NCName, ni une cible d'instruction de traitement.|7.3|Erreur\*|  
|L'instanciation du contenu de `xsl:processing-instruction` crée des nœuds autres que des nœuds de texte.|7.3|Erreur\*|  
|Le résultat de l'instanciation du contenu de `xsl:processing-instruction` contient la chaîne « ?\> ».|7.3|Récupération|  
|Le résultat de l'instanciation du contenu de `xsl:processing-instruction` contient la chaîne « \-\- » ou se termine par « \- ».|7.4|Récupération|  
|Le résultat de l'instanciation du contenu de `xsl:comment` crée des nœuds autres que des nœuds de texte.|7.4|Erreur\*|  
|Le modèle d'un élément de liaison de variables retourne un nœud d'attribut ou un nœud d'espace de noms.|11.2|Erreur\*|  
|Une erreur se produit lors de l'extraction de la ressource à partir de l'URI passé dans la fonction de document.|12.1|Erreur|  
|La référence URI de la fonction de document contient un identificateur de fragment et une erreur se produit lors du traitement de ce dernier.|12.1|Récupération\*|  
|Il existe plusieurs attributs avec le même nom, mais des valeurs différentes, qui ne sont pas des éléments cdata\-section nommés dans `xsl:output` avec la même priorité d'importation.|16|Récupération|  
|Le processeur ne prend pas en charge l'encodage dans l'attribut d'encodage `xsl:output`.|16.1|Récupération|  
|Désactivation de la production littérale des caractères en sortie pour un nœud de texte qui est utilisé à des fins autres qu'un nœud de texte de l'arborescence résultat.|16.4|Récupération\*|  
|Conversion d'un fragment d'arborescence résultat en un nombre ou une chaîne si le fragment d'arborescence résultat contient un nœud de texte dont la production littérale des caractères en sortie est activée.|16.4|Récupération\*|  
|La production littérale des caractères en sortie est désactivée pour un caractère qui ne peut pas être représenté dans l'encodage utilisé par le processeur XSLT pour la sortie.|16.4|Récupération\*|  
|Ajout d'un nœud d'espace de noms à un élément après que les enfants ou les attributs ont été ajoutés à ce dernier.|errata 25|Erreur\*|  
|L'attribut `value` d'un `xsl:number` est NAN, infini ou inférieur à 0,5.|errata 24|Récupération|  
|La collection de nœuds du second argument de la fonction de document est vide et la référence URI est relative.|errata 14|Récupération|  
  
 <sup>*</sup> Ce comportement diffère de celui de la classe <xref:System.Xml.Xsl.XslTransform>.  Pour plus d'informations, consultez [Implémentation de comportements discrétionnaires dans la classe XslTransform](../../../../docs/standard/data/xml/implementation-of-discretionary-behaviors-in-the-xsltransform-class.md).  
  
## Voir aussi  
 [Transformations XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)