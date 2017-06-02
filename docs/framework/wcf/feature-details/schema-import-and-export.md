---
title: "Importation et exportation de sch&#233;mas | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF, importation et exportation de schémas"
  - "classe XsdDataContractExporter"
  - "Classe XsdDataContractImporter"
ms.assetid: 0da32b50-ccd9-463a-844c-7fe803d3bf44
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Importation et exportation de sch&#233;mas
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]inclut un nouveau moteur de sérialisation, le <xref:System.Runtime.Serialization.DataContractSerializer>. Le moteur de sérialisation `DataContractSerializer` traduit des objets [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] en langage XML et inversement. Outre le sérialiseur lui-même, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] intègre un système lui permettant d'importer et d'exporter les schémas afférents. *Schéma* est une description formelle, précise et lisible de la forme de XML par le sérialiseur ou que le désérialiseur peut accéder. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise le langage de définition de schéma XSD, inspiré du langage XML et défini par le consortium World Wide Web Consortium (W3C). Ce format est compatible avec de nombreuses plateformes tierces.  
  
 Le composant d’importation de schéma, <xref:System.Runtime.Serialization.XsdDataContractImporter>, utilise un document de schéma XSD et génère [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (normalement les classes de contrat de données) des classes telles que les formes sérialisées correspondent au schéma donné.  
  
 Par exemple, le fragment de schéma suivant :  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 génère le type suivant (légèrement simplifié pour permettre une meilleure compréhension).  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 Notez que le type généré respecte les meilleures pratiques du contrat de données plusieurs (trouvé dans [meilleures pratiques : contrôle de version de contrat de données](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)) :  
  
-   Le type implémente le <xref:System.Runtime.Serialization.IExtensibleDataObject> interface. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Contrats de données de compatibilité ascendante](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
-   Les membres de données sont implémentés sous forme de propriétés publiques qui encapsulent des champs privés.  
  
-   La classe est une classe partielle et des éléments peuvent y être ajoutés sans modifier le code généré.  
  
 Le <xref:System.Runtime.Serialization.XsdDataContractExporter> vous permet d’effectuer l’opération inverse : utilisent des types sérialisables avec les `DataContractSerializer` et générer un document de schéma XSD.  
  
## <a name="fidelity-is-not-guaranteed"></a>Fidélité non garantie  
 Lors de la conversion, puis reconversion des schémas ou types, la stricte fidélité des informations converties n'est pas garantie. (A *aller-retour* consiste à importer un schéma pour créer un ensemble de classes et exporter le résultat pour recréer le schéma.) Il se peut que le schéma ainsi recréé ne soit pas exactement identique au schéma d'origine. Effectuer à nouveau le processus dans le sens inverse ne garantit pas en effet la fidélité aux informations d'origine. (Exportez un type pour générer son schéma, puis réimportez le type. Il est improbable que le même type soit retourné.)  
  
## <a name="supported-types"></a>Types pris en charge  
 Le modèle de contrat de données prend uniquement en charge un sous-ensemble limité de schémas WC3. Tout schéma ne se conformant pas à ce sous-ensemble provoquera la levée d'une exception lors de l'importation. Par exemple, il n'est pas possible d'indiquer qu'un membre de données d'un contrat de données doit être sérialisé sous forme d'attribut XML. Les schémas nécessitant l'utilisation d'attributs XML ne sont donc pas pris en charge et provoqueront la levée d'exceptions lors de l'importation, le contrat de données ne pouvant être généré à l'aide des attributs XML appropriés.  
  
 Par exemple, il est impossible d'importer le fragment de schéma suivant à l'aide des paramètres d'importation par défaut.  
  
 <!-- TODO: review snippet reference [!code[c_SchemaImportExport#9](../../../../samples/snippets/common/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  -->  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Référence du schéma de contrat de données](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Lorsqu'un schéma ne se conforme pas aux règles des contrats de données, utilisez un autre moteur de sérialisation. Par exemple, le <xref:System.Xml.Serialization.XmlSerializer> utilise son propre mécanisme d’importation de schéma. De plus, il existe un mode spécial d’importation dans lequel la plage du schéma pris en charge est développée. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]la section sur la génération de <xref:System.Xml.Serialization.IXmlSerializable> tape [importation du schéma pour générer des Classes](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 L'exportateur `XsdDataContractExporter` prend en charge tous les types [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] qui peuvent être sérialisés à l'aide du moteur de sérialisation `DataContractSerializer`. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Types pris en charge par le sérialiseur de contrat de données](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Remarque : le schéma généré à l’aide la `XsdDataContractExporter` données normalement valide qui le `XsdDataContractImporter` peut utiliser (sauf si la <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> est utilisé pour personnaliser le schéma).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]à l’aide de la <xref:System.Runtime.Serialization.XsdDataContractImporter>, consultez [importation du schéma pour générer des Classes](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]à l’aide de la <xref:System.Runtime.Serialization.XsdDataContractExporter>, consultez [exportation de schémas à partir des Classes](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 <xref:System.Runtime.Serialization.XsdDataContractImporter>   
 <xref:System.Runtime.Serialization.XsdDataContractExporter>   
 [Importation du schéma pour générer des Classes](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)   
 [Exportation de schémas à partir de Classes](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)