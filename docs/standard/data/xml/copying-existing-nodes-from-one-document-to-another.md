---
title: "Copie de nœuds existants d'un document à un autre"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3caa78c1-3448-4b7b-b83c-228ee857635e
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0f20e5bd595c8eb49360e58f281a8cf6eda89acf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="copying-existing-nodes-from-one-document-to-another"></a>Copie de nœuds existants d'un document à un autre
Le **ImportNode** méthode est le mécanisme par lequel un nœud ou un sous-arbre de nœuds entier est copié à partir d’un **XmlDocument** vers un autre. Le nœud retourné par l'appel est une copie du nœud issu du document source, y compris sur le plan des valeurs d'attribut, du nom du nœud, du type de nœud et de tous les attributs associés à l'espace de noms tels que le préfixe, le nom local et l'URI (Uniform Resource Identifier) d'espace de noms. Le document source n'est pas modifié. À l'issue de l'importation du nœud, il vous reste encore à l'ajouter à l'arborescence à l'aide d'une des méthodes d'insertion de nœuds.  
  
 Dès que le nœud a été joint à son nouveau document, ce dernier en prend possession. En effet, chaque nœud, lors de sa création, possède un document propriétaire, même si les nœuds sont créés dans des fragments de document distincts. Cela est nécessaire de l’objet de modèle DOM (Document XML) et est appliquée par le design de création de paramètres d’usine sur le **XmlDocument** classe. Par exemple, **CreateElement**, est la seule façon de créer de nouveaux nœuds.  
  
 Selon le type de nœud du nœud importé et la valeur de la *approfondie* paramètre, des informations supplémentaires est éventuellement copiée. Cette méthode tente de refléter le comportement attendu si un fragment de code source HTML ou XML était copié d'un document à un autre, en tenant compte du fait que, dans le cas d'un document XML, les deux documents peuvent posséder des définitions de type de document (DTD) différentes.  
  
 Le tableau suivant décrit le comportement spécifique pour chaque type of nœud pouvant être importé.  
  
|Type de nœud|*profondeur* paramètre a la valeur true|*profondeur* paramètre a la valeur false|  
|---------------|------------------------------|-------------------------------|  
|XmlAttribute|Le <xref:System.Xml.XmlAttribute.Specified%2A> a la valeur **true** sur XmlAttribute. Les descendants de la source de **XmlAttribute** sont importés de manière récursive et les nœuds obtenus sont réassemblés pour former le sous-arbre correspondant.|Le *approfondie* paramètre ne s’applique pas aux **XmlAttribute** nœuds, parce qu’ils emportent toujours avec eux leurs nœuds enfants.|  
|XmlCDataSection|Copie le nœud avec ses données.|Copie le nœud avec ses données.|  
|XmlComment|Copie le nœud avec ses données.|Copie le nœud avec ses données.|  
|XmlDocumentFragment|Les descendants du nœud source sont importés de manière récursive et les nœuds obtenus sont réassemblés pour former le sous-arbre correspondant.|Vide **XmlDocumentFragment** est créé.|  
|XmlDocumentType|Copie le nœud avec ses données.*|Copie le nœud avec ses données.*|  
|XmlElement|Les descendants de l'élément source sont importés de façon récursive et les nœuds résultants sont assemblés à nouveau pour former le sous-arbre correspondant. **Remarque :** attributs par défaut ne sont pas copiés. Si le document destinataire de l'importation définit des attributs par défaut pour ce nom d'élément, ces attributs sont assignés.|Spécifié attribut nœuds de l’élément source sont importés et généré **XmlAttribute** sont attachés au nouvel élément. Les nœuds descendants ne sont pas copiés. **Remarque :** attributs par défaut ne sont pas copiés. Si le document destinataire de l'importation définit des attributs par défaut pour ce nom d'élément, ces attributs sont assignés.|  
|XmlEntityReference|Étant donné que les documents de la source et de destination peuvent comporter des entités, cette méthode ne copie que les **XmlEntityReference** nœud. Le texte de remplacement n'est pas inclus. Si l'entité est définie dans le document de destination, sa valeur est assignée.|Étant donné que les documents de la source et de destination peuvent comporter des entités, cette méthode ne copie que les **XmlEntityReference** nœud. Le texte de remplacement n'est pas inclus. Si l'entité est définie dans le document de destination, sa valeur est assignée.|  
|XmlProcessingInstruction|Copie la cible et la valeur de données à partir du nœud importé.|Copie la cible et la valeur de données à partir du nœud importé.|  
|XmlText|Copie le nœud avec ses données.|Copie le nœud avec ses données.|  
|XmlSignificantWhitespace|Copie le nœud avec ses données.|Copie le nœud avec ses données.|  
|XmlWhitespace|Copie le nœud avec ses données.|Copie le nœud avec ses données.|  
|XmlDeclaration|Copie la cible et la valeur de données à partir du nœud importé.|Copie la cible et la valeur de données à partir du nœud importé.|  
|Tous les autres types de nœuds|Ces types de nœuds ne peuvent pas être importés.|Ces types de nœuds ne peuvent pas être importés.|  
  
> [!NOTE]
>  Bien que les nœuds DocumentType puissent être importés, un document ne peut avoir qu'un seul DocumentType. Par conséquent, dès que vous avez importé le type de document, vous devez vous assurer, avant de l’insérer dans l’arborescence, que le document est dépourvu de type de document. Pour plus d’informations sur la suppression de nœuds, consultez [suppression de nœuds, de contenu et de valeurs à partir d’un Document XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
