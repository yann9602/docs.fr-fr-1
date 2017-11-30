---
title: "Utilisation de contrats de données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataContractAttribute class
- WCF, data
- data contracts [WCF]
ms.assetid: a3ae7b21-c15c-4c05-abd8-f483bcbf31af
caps.latest.revision: "38"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 258e7fd0235ffa67ee8c293831cb8230d48a894c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-data-contracts"></a>Utilisation de contrats de données
Un *contrat de données* est un accord en bonne et due forme entre un service et un client qui décrit de manière abstraite les données à échanger. Autrement dit, pour communiquer, le client et le service n'ont pas besoin de partager les mêmes types, mais uniquement les mêmes contrats de données. Un contrat de données définit précisément, pour chaque type de paramètre ou de retour, les données qui doivent être sérialisées (converties en données XML) pour être échangées.  
  
## <a name="data-contract-basics"></a>Principes de base des contrats de données  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utilise un moteur de sérialisation appelé par défaut Sérialiseur de contrat de données pour sérialiser et désérialiser des données (les convertir vers ou à partir de code XML). Tous les types primitifs du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] , tels que les entiers et les chaînes, ainsi que certains types considérés comme primitifs, tels que <xref:System.DateTime> et <xref:System.Xml.XmlElement>, peuvent être sérialisés sans autre préparation et sont considérés comme ayant des contrats de données par défaut. De nombreux types du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ont également des contrats de données existants. Pour obtenir la liste complète des types sérialisables, consultez [Types Supported by the Data Contract Serializer](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
 Vous devez définir un contrat de données pour les nouveaux types complexes que vous créez afin que ces derniers soient sérialisables. Par défaut, le <xref:System.Runtime.Serialization.DataContractSerializer> déduit le contrat de données et sérialise tous les types visibles publiquement. Toutes les propriétés et tous les champs publics en lecture/écriture du type sont sérialisés. Vous pouvez supprimer des membres de la sérialisation en utilisant <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>. Vous pouvez également créer explicitement un contrat de données à l'aide des attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> . Pour cela, il faut normalement appliquer l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> au type. Cet attribut peut être appliqué à des classes, des structures et des énumérations. Puis, l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> doit être appliqué à chaque membre du type de contrat de données pour indiquer qu'il s'agit d'un *membre de données*, c'est-à-dire qu'il doit être sérialisé. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Types sérialisables](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
### <a name="example"></a>Exemple  
 L'exemple suivant présente un contrat de service (une interface) auquel les attributs <xref:System.ServiceModel.ServiceContractAttribute> et <xref:System.ServiceModel.OperationContractAttribute> ont été explicitement appliqués. L'exemple montre que les types primitifs ne requièrent pas de contrat de données, contrairement au type complexe.  
  
 [!code-csharp[C_DataContract#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#1)]
 [!code-vb[C_DataContract#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#1)]  
  
 L'exemple suivant montre comment créer un contrat de données pour le type `MyTypes.PurchaseOrder` en appliquant les attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> à la classe et à ses membres.  
  
 [!code-csharp[C_DataContract#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#2)]
 [!code-vb[C_DataContract#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#2)]  
  
### <a name="notes"></a>Notes  
 Les remarques suivantes fournissent des éléments à prendre en compte lors de la création de contrats de données :  
  
-   L'attribut <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> est honoré uniquement lorsqu'il est utilisé avec des types non marqués. Cela inclut les types qui ne sont pas marqués avec l'un des attributs <xref:System.Runtime.Serialization.DataContractAttribute>, <xref:System.SerializableAttribute>, <xref:System.Runtime.Serialization.CollectionDataContractAttribute>ou <xref:System.Runtime.Serialization.EnumMemberAttribute> , ou qui sont marqués comme sérialisables par tout autre moyen (par exemple, objet <xref:System.Xml.Serialization.IXmlSerializable>).  
  
-   Vous pouvez appliquer l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> à des champs et à des propriétés.  
  
-   Les niveaux d'accessibilité des membres (interne, privé, protégé ou public) n'affectent en aucune façon le contrat de données.  
  
-   L'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> est ignoré s'il est appliqué à des membres statiques.  
  
-   Pendant la sérialisation, le code de propriété get est appelé pour que les membres de données de propriété obtiennent la valeur des propriétés à sérialiser.  
  
-   Pendant la désérialisation, un objet non initialisé est d'abord créé, sans appeler de constructeur sur le type. Puis, tous les membres de données sont désérialisés.  
  
-   Pendant la désérialisation, le code de propriété set est appelé pour que les membres de données de propriété attribuent aux propriétés la valeur désérialisée.  
  
-   Pour qu'un contrat de données soit valide, il doit être possible de sérialiser tous ses membres de données. Pour obtenir la liste complète des types sérialisables, consultez [Types Supported by the Data Contract Serializer](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
     Les types génériques sont gérés exactement de la même façon que les types non génériques. Les paramètres génériques n'ont pas d'exigences particulières. Considérons par exemple le type suivant.  
  
 [!code-csharp[C_DataContract#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#3)]
 [!code-vb[C_DataContract#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#3)]  
  
 Ce type est sérialisable, que le type utilisé pour le paramètre de type générique (`T`) le soit ou non. Comme il doit être possible de sérialiser tous les membres de données, le type suivant est sérialisable uniquement si le paramètre de type générique l'est également, tel qu'indiqué dans le code suivant.  
  
 [!code-csharp[C_DataContract#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#4)]
 [!code-vb[C_DataContract#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#4)]  
  
 Pour obtenir un exemple de code complet d’un service WCF qui définit un contrat de données, consultez l’exemple [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md) .  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 [Types sérialisables](../../../../docs/framework/wcf/feature-details/serializable-types.md)  
 [Noms de contrat de données](../../../../docs/framework/wcf/feature-details/data-contract-names.md)  
 [Équivalence des contrats de données](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Ordre des membres de données](../../../../docs/framework/wcf/feature-details/data-member-order.md)  
 [Types connus de contrat de données](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [Contrats de données à compatibilité ascendante](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)  
 [Version des contrats de données](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [Rappels de sérialisation avec tolérance de version](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)  
 [Valeurs de données membre par défaut](../../../../docs/framework/wcf/feature-details/data-member-default-values.md)  
 [Types pris en charge par le sérialiseur de contrat de données](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)  
 [Comment : créer un contrat de données de base pour une classe ou Structure](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
