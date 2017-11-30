---
title: "Compilation de schéma XmlSchemaCollection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 901c3fdc8fdc80cc7c3bf13170646de857a5e009
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xmlschemacollection-schema-compilation"></a>Compilation de schéma XmlSchemaCollection
Le **XmlSchemaCollection** est un cache ou une bibliothèque où les schémas de langage (XSD XML) de définition XML-Data Reduced (XDR) et de schéma XML peuvent être stockés et validés. **XmlSchemaCollection** améliore les performances en mettant en cache des schémas en mémoire au lieu d’y accéder à partir d’un fichier ou une URL.  
  
> [!NOTE]
>  Bien que le **XmlSchemaCollection** classe stocke les schémas XDR et schémas XML, toute méthode ou propriété qui prend ou retourne un **XmlSchema** objet prend uniquement en charge les schémas XML.  
  
> [!IMPORTANT]
>  La classe <xref:System.Xml.Schema.XmlSchemaCollection> est désormais obsolète et a été remplacée par la classe <xref:System.Xml.Schema.XmlSchemaSet>. Pour plus d’informations sur la <xref:System.Xml.Schema.XmlSchemaSet> , consultez classe [XmlSchemaSet pour la Compilation du schéma](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).  
  
## <a name="add-schemas-to-the-collection"></a>Ajout de schémas à la collection  
 Les schémas sont chargés dans la collection à l’aide du **ajouter** méthode **XmlSchemaCollection**, à ce moment-là que le schéma est associé à un URI d’espace de noms. Pour les schémas XML, l'URI d'espace de noms correspond généralement à l'espace de noms cible du schéma. Pour les schémas XDR, l'URI d'espace de noms correspond à l'espace de noms spécifié lors de l'ajout du schéma à la collection.  
  
## <a name="check-for-a-schema-in-the-collection"></a>Recherche d’un schéma dans la collection  
 Vous pouvez vérifier si un schéma se trouve dans la collection à l’aide de la **contient** (méthode). Le **contient** méthode prend soit un **XmlSchema** objet (pour les schémas XML uniquement) ou une chaîne qui représente l’URI d’espace de noms associé au schéma (schémas XDR et schémas XML).  
  
## <a name="retrieve-a-schema-from-the-collection"></a>Extraction d’un schéma à partir de la collection  
 Vous pouvez extraire un schéma à partir de la collection à l’aide de la **élément** propriété. Le **élément** propriété accepte une chaîne représentant l’espace de noms URI associé au schéma, généralement son espace de noms cible et retourne un **XmlSchema** objet. Le **élément** propriété s’applique uniquement aux schémas XML. La valeur de retour est toujours une référence null pour les schémas XDR car ils n'ont pas de modèle objet disponible.  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a>Validation des documents XML à l'aide de XmlSchemaCollection  
 Vous pouvez valider un document d’instance XML à l’aide un **XmlSchemaCollection** en créant le **XmlSchemaCollection** objet, en ajoutant vos schémas à la collection et en définissant le **schémas**  propriété sur le **XmlValidatingReader** pour assigner le nouvel **XmlSchemaCollection** à la **XmlValidatingReader**.  
  
### <a name="improved-performance"></a>Performances améliorées  
 Il est recommandé, si vous validez plusieurs documents sur le même schéma que vous utilisez le **XmlSchemaCollection** , car il offre de meilleures performances en mettant en cache des schémas en mémoire.  
  
 L’exemple de code suivant crée la **XmlSchemaCollection** objet, ajoute des schémas à la collection et définit la **schémas** propriété.  
  
```vb  
Dim tr as XmlTextReader = new XmlTextReader("Books.xml")  
Dim vr as XmlValidatingReader = new XmlValidatingReader(tr)  
Dim xsc as XmlSchemaCollection = new XmlSchemaCollection  
xsc.Add("urn:bookstore-schema", "Books.xsd")  
vr.Schemas.Add(xsc)  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("Books.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
xsc.Add("urn:bookstore-schema", "Books.xsd");    
vr.Schemas.Add(xsc);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Validation XDR avec XmlSchemaCollection](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
 [Validation XML Schema (XSD) avec XmlSchemaCollection](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
