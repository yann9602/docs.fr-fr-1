---
title: "Contenu valide de XElement et objets du Répertoire2 XDocument | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f752ae346167709b95e758d15c1785ba7b6fcc5f
ms.lasthandoff: 03/13/2017

---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a>Contenu valide des objets XElement et XDocument
Cette rubrique décrit les arguments valides qui peuvent être passés aux constructeurs et méthodes utilisés pour ajouter du contenu aux éléments et aux documents.  
  
## <a name="valid-content"></a>Contenu valide  
 Les requêtes sont souvent évaluent à <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>ou <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> Vous pouvez passer des collections de <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XAttribute>des objets dans le <xref:System.Xml.Linq.XElement>constructeur.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> Par conséquent, il est commode de passer les résultats d'une requête en tant que contenu dans des méthodes et des constructeurs que vous utilisez pour remplir des arborescences XML.  
  
 Lors de l'ajout de contenu simple, divers types peuvent être passés à cette méthode. Les types valides sont les suivants :  
  
-   <xref:System.String></xref:System.String>  
  
-   <xref:System.Double></xref:System.Double>  
  
-   <xref:System.Single></xref:System.Single>  
  
-   <xref:System.Decimal></xref:System.Decimal>  
  
-   <xref:System.Boolean></xref:System.Boolean>  
  
-   <xref:System.DateTime></xref:System.DateTime>  
  
-   <xref:System.TimeSpan></xref:System.TimeSpan>  
  
-   <xref:System.DateTimeOffset></xref:System.DateTimeOffset>  
  
-   Tout type qui implémente `Object.ToString`.  
  
-   Tout type qui implémente <xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601>  
  
 Lors de l'ajout de contenu complexe, divers types peuvent être passés à cette méthode :  
  
-   <xref:System.Xml.Linq.XObject></xref:System.Xml.Linq.XObject>  
  
-   <xref:System.Xml.Linq.XNode></xref:System.Xml.Linq.XNode>  
  
-   <xref:System.Xml.Linq.XAttribute>  
  
-   Tout type qui implémente<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>  
  
 Si un objet implémente <xref:System.Collections.Generic.IEnumerable%601>, la collection dans l’objet est énumérée et tous les éléments dans la collection sont ajoutés.</xref:System.Collections.Generic.IEnumerable%601> Si la collection contient <xref:System.Xml.Linq.XNode>ou <xref:System.Xml.Linq.XAttribute>des objets, chaque élément de la collection est ajouté séparément.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XNode> Si la collection contient du texte (ou des objets convertis en texte), le texte dans la collection est concaténé et ajouté en tant que nœud de texte simple.  
  
 Si le contenu est `null`, rien n'est ajouté. Lors du passage d'une collection, des éléments de cette collection peuvent avoir la valeur `null`. Un élément `null` dans la collection n'a aucun effet sur l'arborescence.  
  
 Un attribut ajouté doit avoir un nom unique dans son élément conteneur.  
  
 Lorsque vous ajoutez des <xref:System.Xml.Linq.XNode>ou <xref:System.Xml.Linq.XAttribute>des objets, si le contenu n’a pas de parent, puis les objets sont simplement attachés à l’arborescence XML.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XNode> Si le nouveau contenu a déjà un parent et fait partie d'une autre arborescence XML, il est cloné et le nouveau contenu cloné est attaché à l'arborescence XML.  
  
## <a name="valid-content-for-documents"></a>Contenu valide pour les documents  
 Les attributs et le contenu simple ne peuvent pas être ajoutés à un document.  
  
 Il n’existe pas beaucoup de scénarios qui vous oblige à créer un <xref:System.Xml.Linq.XDocument>.</xref:System.Xml.Linq.XDocument> Au lieu de cela, vous pouvez généralement créer vos arborescences XML avec un <xref:System.Xml.Linq.XElement>nœud racine.</xref:System.Xml.Linq.XElement> À moins que vous ayez un besoin spécifique de créer un document (par exemple, étant donné que vous devez créer des instructions de traitement et des commentaires au niveau supérieur, ou vous devez prendre en charge les types de documents), il est souvent plus commode d’utiliser <xref:System.Xml.Linq.XElement>comme nœud racine.</xref:System.Xml.Linq.XElement>  
  
 Le contenu valide pour un document inclut les éléments suivants :  
  
-   Zéro ou un <xref:System.Xml.Linq.XDocumentType>objets.</xref:System.Xml.Linq.XDocumentType> Les types de documents doivent figurer avant l'élément.  
  
-   Zéro ou un élément.  
  
-   Zéro ou plusieurs commentaires.  
  
-   Zéro ou plusieurs instructions de traitement.  
  
-   Zéro ou plusieurs nœuds de texte qui contiennent uniquement des espaces blancs.  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a>Constructeurs et fonctions qui autorisent l'ajout de contenu  
 Les méthodes suivantes permettent d’ajouter du contenu enfant à un <xref:System.Xml.Linq.XElement>ou un <xref:System.Xml.Linq.XDocument>:</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement>  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A></xref:System.Xml.Linq.XElement.%23ctor%2A>|Construit un <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A></xref:System.Xml.Linq.XDocument.%23ctor%2A>|Construit un <xref:System.Xml.Linq.XDocument>.</xref:System.Xml.Linq.XDocument>|  
|<xref:System.Xml.Linq.XContainer.Add%2A></xref:System.Xml.Linq.XContainer.Add%2A>|Ajoute à la fin du contenu enfant de l' <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A></xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Ajoute du contenu après le <xref:System.Xml.Linq.XNode>.</xref:System.Xml.Linq.XNode>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Ajoute du contenu avant le <xref:System.Xml.Linq.XNode>.</xref:System.Xml.Linq.XNode>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A></xref:System.Xml.Linq.XContainer.AddFirst%2A>|Ajoute du contenu au début du contenu enfant de l’élément <xref:System.Xml.Linq.XContainer>.</xref:System.Xml.Linq.XContainer>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A></xref:System.Xml.Linq.XElement.ReplaceAll%2A>|Remplace tout le contenu (nœuds enfants et attributs) d’un <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A></xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|Remplace les attributs d’un <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A></xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|Remplace les nœuds enfants par du nouveau contenu.|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A></xref:System.Xml.Linq.XNode.ReplaceWith%2A>|Remplace un nœud par du nouveau contenu.|  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’arborescences XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
