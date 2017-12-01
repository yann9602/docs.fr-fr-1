---
title: DOM (Document Object Model) XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5e52844-4820-47c0-a61d-de2da33e9f54
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ff91e929876ceec8512e962b88795b6a8a29f3d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-document-object-model-dom"></a>DOM (Document Object Model) XML
La classe DOM (Document Object Model) XML fournit une représentation en mémoire d'un document XML. Le DOM vous permet de lire, de manipuler et de modifier un document XML par programme. Le **XmlReader** également classe lit du XML ; Toutefois, il fournit l’accès non mis en cache, avant uniquement, en lecture seule. Cela signifie qu’il n’y a pas de fonction pour modifier les valeurs d’un attribut ou le contenu d’un élément ou la possibilité d’insérer et supprimer des nœuds avec le **XmlReader**. La modification est la fonction principale du DOM. Ce dernier régit la représentation en mémoire commune et structurée des données XML, bien que les données XML véritables soient stockées de façon linéaire lorsqu'elles se trouvent dans un fichier ou qu'elles proviennent d'un autre objet. Voici des données XML :  
  
## <a name="input"></a>Entrée  
  
```xml  
<?xml version="1.0"?>  
  <books>  
    <book>  
        <author>Carson</author>  
        <price format="dollar">31.95</price>  
        <pubdate>05/01/2001</pubdate>  
    </book>  
    <pubinfo>  
        <publisher>MSPress</publisher>  
        <state>WA</state>  
    </pubinfo>  
  </books>   
```  
  
 L'illustration suivante montre comment la mémoire est structurée lorsque ces données XML sont lues dans la structure DOM.  
  
 ![Structure du document XML](../../../../docs/standard/data/xml/media/xml-to-domtree.gif "XML_To_DOMTree")  
Structure d'un document XML  
  
 Dans la structure du document XML, chaque cercle de cette illustration représente un nœud, qui est appelé un **XmlNode** objet. Le **XmlNode** objet est l’objet de base dans l’arborescence DOM. Le **XmlDocument** (classe), qui étend **XmlNode**, prend en charge des méthodes pour effectuer des opérations sur le document dans son ensemble (par exemple, le chargement en mémoire ou enregistrez le document XML dans un fichier. En outre, **XmlDocument** fournit un moyen pour afficher et manipuler les nœuds dans le document XML entier. Les deux **XmlNode** et **XmlDocument** intègrent des améliorations de performances et la facilité d’utilisation et de méthodes et des propriétés pour :  
  
-   d'accéder et de modifier des nœuds spécifiques au DOM, tels que les nœuds d'élément, de référence d'entité, et bien d'autres ;  
  
-   d'extraire des nœuds entiers, en plus des informations qu'ils contiennent, telles que le texte des nœuds d'élément.  
  
    > [!NOTE]
    >  Si une application ne nécessite pas la structure ou la modification des fonctionnalités fournies par le modèle DOM, le **XmlReader** et **XmlWriter** classes fournissent un accès en flux continu non mis en cache et en avant uniquement au format XML. Pour plus d’informations, consultez <xref:System.Xml.XmlReader> et <xref:System.Xml.XmlWriter>.  
  
 **Nœud** objets comportent un ensemble de méthodes et propriétés, ainsi que les caractéristiques de base et bien définies. Voici certaines de ces caractéristiques :  
  
-   Un nœud ne possède qu'un seul nœud parent, qui est le nœud situé juste au-dessus de lui. Le seul nœud qui est dépourvu de parent est la racine du document, puisqu'il s'agit du nœud de premier niveau qui contient le document lui-même et les fragments de document.  
  
-   La plupart des nœuds peuvent comporter plusieurs nœuds enfants, qui sont les nœuds situés directement sous eux. La liste suivante répertorie des types de nœuds pouvant comporter des nœuds enfants :  
  
    -   **Document**  
  
    -   **DocumentFragment**  
  
    -   **EntityReference**  
  
    -   **Élément**  
  
    -   **Attribut**  
  
     Le **XmlDeclaration**, **Notation**, **entité**, **CDATASection**, **texte**,  **Commentaire**, **ProcessingInstruction**, et **DocumentType** nœuds n’ont pas de nœuds enfants.  
  
-   Les nœuds situés au même niveau, représentés dans le diagramme par le **book** et **pubinfo** sont des nœuds frères.  
  
 L'une des caractéristiques du DOM est la manière dont il gère les attributs. Les attributs ne sont pas des nœuds qui font partie des relations parent-enfant et frère. Ils sont considérés comme une propriété du nœud d'élément et sont constitués d'une paire composée d'un nom et d'une valeur. Par exemple, si vous avez des données XML composées de `format="dollar` associées à l'élément `price`, le mot `format` correspond au nom et la valeur de l'attribut `format` est `dollar`. Pour récupérer le `format="dollar"` attribut de la **prix** nœud, vous appelez le **GetAttribute** méthode lorsque le curseur se trouve à la `price` nœud d’élément. Pour plus d’informations, consultez [accès aux attributs dans le DOM](../../../../docs/standard/data/xml/accessing-attributes-in-the-dom.md).  
  
 Lorsque le code XML est lu en mémoire, des nœuds sont créés. Toutefois, tous les nœuds ne sont pas du même type. Un élément, dans XML, possède des règles et une syntaxe différentes de celles d'une instruction de traitement. C'est pourquoi, à mesure que des données diverses sont lues, un type de nœud est assigné à chaque nœud. Ce type de nœud détermine les caractéristiques et la fonctionnalité du nœud.  
  
 Pour plus d’informations sur les types de nœuds générés en mémoire, consultez [Types de nœuds XML](../../../../docs/standard/data/xml/types-of-xml-nodes.md). Pour plus d’informations sur les objets créés dans l’arborescence de nœuds, consultez [mappage de la hiérarchie d’objets à des données XML](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).  
  
 Microsoft a étendu les API disponibles dans les recommandations du World Wide Web Consortium (W3C) DOM Level 1 et Level 2 afin de faciliter la manipulation d’un document XML. En plus d'assurer une prise en charge complète des normes W3C, les classes, méthodes et propriétés supplémentaires ajoutent une fonctionnalité qui dépasse ce que le DOM XML du W3C permet de faire. De nouvelles classes vous permettent d’accéder aux données relationnelles, tout en proposant des méthodes qui permettent de les synchroniser avec des données ADO.NET et d’exposer simultanément des données comme des données XML. Pour plus d’informations, consultez [synchronisation d’un DataSet avec un XmlDataDocument](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
 Le DOM revêt un intérêt tout particulier pour la lecture de données XML et leur chargement en mémoire afin d'en modifier la structure, d'y ajouter ou d'en supprimer des nœuds, ou encore de modifier les données contenues dans un nœud tout comme dans le texte contenu dans un élément. Cependant, d'autres classes sont disponibles et offrent de meilleures performances que le DOM dans d'autres scénarios. Pour un accès rapide, non mis en cache et avant uniquement de flux de données au format XML, utilisez la **XmlReader** et **XmlWriter**. Si vous avez besoin d’un accès aléatoire avec un modèle de curseur et **XPath**, utilisez le **XPathNavigator** classe.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de nœuds XML](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
 [Mappage de la hiérarchie d’objets à des données XML](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)
